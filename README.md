# cuda_11.8_wsl2_ubuntu24.04
# goal was to install cuda 11.8 in a fresh ubuntu 24.04 to run cryosparc and or relion

# first install a batch of build essential package for common libraries needed for many packages to run
sudo apt install build-essential
# check that gcc was included in that library packages
which gcc
# log
/usr/bin/gcc
gcc --version
# log
gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

# cuda toolkit download and installation attempts
# go to https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=runfile_local
# download the Linux > x86_64 > wsl-ubuntu > 2.0 > deb(local) [follow the instruction for debian package installation]
# gives missing dependency error
# log
The following packages have unmet dependencies:
 nsight-systems-2022.4.2 : Depends: libtinfo5 but it is not installable
E: Unable to correct problems, you have held broken packages.
# install libtinfo5
wget http://security.ubuntu.com/ubuntu/pool/universe/n/ncurses/libtinfo5_6.3-2ubuntu0.1_amd64.deb
sudo apt install ./libtinfo5_6.3-2ubuntu0.1_amd64.deb
# then run the install command again
sudo apt-get -y install cuda
sudo apt-get install cuda-toolkit
sudo reboot now

# setup the cuda paths
echo 'export PATH=/usr/local/cuda-11.8/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
sudo ldconfig

# verifying a functioning cuda (follow the instruction here if needed)
https://github.com/nvidia/cuda-samples



