---
title: "Unable to delete older kernels, no space left on devices"
date: 2019-03-30
forum: Server Platforms
---

### Post by veronica-c on 2019-03-30
Hi, I am new to Ubuntu and I have some difficulties when I install Cuda 10. I am using Windows 10 and Ubuntu 16.04 dual system.  
I installed Cuda to run Caffe successfully before. However,  I am trying to using Caffe again now but it failed. I didn't make any changes to my environment files. 
It showed that "error while loading shared libraries: libcudart.so.8.0: cannot open shared object file: No such file or directory". I am sure I have PATH and Library PATH.

```
#CUDA
export PATH=/usr/local/cuda-10.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.0/lib64
#export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/veronica/.mujoco/mjpro150/bin
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/cuda-10.0/lib64
```

What's worse, I didn't find /usr/local/cuda-10.0 folder this time. Thus I decided to re-install Cuda. And I removed older version. ```
$sudo apt-get purge nvidia-cuda

```
I used this tutorial to install Cuda.  [http://www.rignitc.com/2018/12/29/install-cuda-10-with-ubuntu-16-04](http://www.rignitc.com/2018/12/29/install-cuda-10-with-ubuntu-16-04)

I disabled nouveau drivers. 
**Disable nouveau drivers.**
Create a file at /etc/modprobe.d/blacklist-nouveau.conf with the following contents: 
blacklist nouveau
options nouveau modeset=0

After that, I regenerated the kernel initrd but it failed. 



```
$ sudo /sbin/mkinitramfs
sudo: /sbin/mkinitramfs: command not found


$ sudo /usr/sbin/mkinitramfs


Usage: /usr/sbin/mkinitramfs [OPTION]... -o outfile [version]


Options:
  -c compress    Override COMPRESS setting in initramfs.conf.
  -d confdir    Specify an alternative configuration directory.
  -k        Keep temporary directory used to make the image.
  -o outfile    Write to outfile.
  -r root    Override ROOT setting in initramfs.conf.


See mkinitramfs(8) for further details.

```


In this process, I am trying to install latest Nvidia driver. 

```

$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001B06sv00001028sd00003600bc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-396 - third-party non-free
driver   : nvidia-390 - third-party non-free
driver   : nvidia-410 - third-party non-free
driver   : nvidia-418 - third-party free recommended
driver   : nvidia-415 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-384 - third-party non-free



$ sudo apt install nvidia-418
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not going to be installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```


I also tried 'autoinstall driver'

```
$sudo ubuntu-drivers autoinstallReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not going to be installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
The following NEW packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
59 not fully installed or removed.
Need to get 0 B/546 MB of archives.
After this operation, 1,168 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 file:/var/cuda-repo-10-1-local-10.1.105-418.39  cuda-visual-tools-10-1 10.1.105-1 [398 MB]
Get:2 file:/var/cuda-repo-10-1-local-10.1.105-418.39  cuda-documentation-10-1 10.1.105-1 [50.4 MB]
(Reading database ... 338150 files and directories currently installed.)
Preparing to unpack .../cuda-visual-tools-10-1_10.1.105-1_amd64.deb ...
Unpacking cuda-visual-tools-10-1 (10.1.105-1) ...
dpkg: error processing archive /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-visual-tools-10-1_10.1.105-1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/local/cuda-10.1/libnvvp/plugins/org.eclipse.birt.chart.engine_4.4.1.v201409160530.jar' to '/usr/local/cuda-10.1/libnvvp/plugins/org.eclipse.birt.chart.engine_4.4.1.v201409160530.jar.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../cuda-documentation-10-1_10.1.105-1_amd64.deb ...
Unpacking cuda-documentation-10-1 (10.1.105-1) ...
dpkg: error processing archive /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-documentation-10-1_10.1.105-1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/local/cuda-10.1/doc/html/npp/group__image__filter__border__32f.html' to '/usr/local/cuda-10.1/doc/html/npp/group__image__filter__border__32f.html.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../nvidia-418_418.56-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-418 (418.56-0ubuntu0~gpu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-418_418.56-0ubuntu0~gpu16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/nvidia-418/libnvidia-eglcore.so.418.56' to '/usr/lib/nvidia-418/libnvidia-eglcore.so.418.56.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-visual-tools-10-1_10.1.105-1_amd64.deb
 /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-documentation-10-1_10.1.105-1_amd64.deb
 /var/cache/apt/archives/nvidia-418_418.56-0ubuntu0~gpu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I thought it happened maybe due to "No space left on device'.  I tried the solution which were posted in this link but failed: [https://ubuntuforums.org/showthread.php?t=2254523](https://ubuntuforums.org/showthread.php?t=2254523)

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  122M  6.2G   2% /run
/dev/sda3        21G   21G     0 100% /
tmpfs            32G  191M   32G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/sda5       976M  3.7M  972M   1% /boot/efi
/dev/sda6       1.3T  266G  943G  23% /home
tmpfs           6.3G  152K  6.3G   1% /run/user/1000
/dev/sda2       492G  1.8G  490G   1% /media/veronica/DATA

$ df -l
Filesystem      1K-blocks      Used Available Use% Mounted on
udev             32803592         0  32803592   0% /dev
tmpfs             6567704    124700   6443004   2% /run
/dev/sda3        21690236  21602756         0 100% /
tmpfs            32838504    195472  32643032   1% /dev/shm
tmpfs                5120         4      5116   1% /run/lock
tmpfs            32838504         0  32838504   0% /sys/fs/cgroup
/dev/sda5          998480      3740    994740   1% /boot/efi
/dev/sda6      1335007296 278843040 988326768  23% /home
tmpfs             6567704       152   6567552   1% /run/user/1000
/dev/sda2       515196924   1784364 513412560   1% /media/veronica/DATA

```


And I want to remove those older kernels.

```
$ dpkg -l | grep -G "linux.*image.*"
ii  linux-base                                      4.5ubuntu1~16.04.1                            all          Linux image base package
rc  linux-image-4.15.0-29-generic                   4.15.0-29.31~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-34-generic                   4.15.0-34.37~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-36-generic                   4.15.0-36.39~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-38-generic                   4.15.0-38.41~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-39-generic                   4.15.0-39.42~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-42-generic                   4.15.0-42.45~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-43-generic                   4.15.0-43.46~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-45-generic                   4.15.0-45.48~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-46-generic                   4.15.0-46.49~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-generic-hwe-16.04                   4.15.0.46.67                                  amd64        Generic Linux kernel image

$ sudo dpkg -P linux-headers-4.15.0-{29,34,36,38,39,42,43,45}
dpkg: warning: ignoring request to remove linux-headers-4.15.0-29 which isn't installed
dpkg: dependency problems prevent removal of linux-headers-4.15.0-34:
 linux-headers-4.15.0-34-generic depends on linux-headers-4.15.0-34.


dpkg: error processing package linux-headers-4.15.0-34 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-4.15.0-36:
 linux-headers-4.15.0-36-generic depends on linux-headers-4.15.0-36.


dpkg: error processing package linux-headers-4.15.0-36 (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-headers-4.15.0-38 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.15.0-39 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.15.0-42 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.15.0-43 which isn't installed
dpkg: dependency problems prevent removal of linux-headers-4.15.0-45:
 linux-headers-4.15.0-45-generic depends on linux-headers-4.15.0-45.


dpkg: error processing package linux-headers-4.15.0-45 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-4.15.0-34
 linux-headers-4.15.0-36
 linux-headers-4.15.0-45


$ sudo dpkg -P linux-image-4.15.0-{29,34,36,38,39,42,43}-generic
dpkg: warning: ignoring request to remove linux-image-4.15.0-29-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.15.0-34-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.15.0-36-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.15.0-38-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.15.0-39-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.15.0-42-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.15.0-43-generic which isn't installed


$ sudo dpkg --purge linux-headers-4.15.0-{29,34,36,38,39,42,43}
dpkg: warning: ignoring request to remove linux-headers-4.15.0-29 which isn't installed
dpkg: dependency problems prevent removal of linux-headers-4.15.0-34:
 linux-headers-4.15.0-34-generic depends on linux-headers-4.15.0-34.


dpkg: error processing package linux-headers-4.15.0-34 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-4.15.0-36:
 linux-headers-4.15.0-36-generic depends on linux-headers-4.15.0-36.


dpkg: error processing package linux-headers-4.15.0-36 (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-headers-4.15.0-38 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.15.0-39 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.15.0-42 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.15.0-43 which isn't installed
Errors were encountered while processing:
 linux-headers-4.15.0-34
 linux-headers-4.15.0-36

$ sudo dpkg --remove --force-remove-reinstreq linux-image-extra-4.15.0-46-generic
dpkg: warning: ignoring request to remove linux-image-extra-4.15.0-46-generic which isn't installed

$ for i in /boot/vmlinuz* ; do      dpkg -S $i | egrep -v $(uname -r); done |cut -d- -f3-4
4.15.0-45

$ sudo dpkg --remove --force-remove-reinstreq linux-image-4.15.0-45-generic
dpkg: dependency problems prevent removal of linux-image-4.15.0-45-generic:
 linux-modules-extra-4.15.0-45-generic depends on linux-image-4.15.0-45-generic | linux-image-unsigned-4.15.0-45-generic; however:
  Package linux-image-4.15.0-45-generic is to be removed.
  Package linux-image-unsigned-4.15.0-45-generic is not installed.


dpkg: error processing package linux-image-4.15.0-45-generic (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.15.0-45-generic


$ uname -r && dpkg --get-selections linux4.15.0-46-generic
dpkg: no packages found matching linux

$ sudo apt install linux-generic-hwe-16.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic-hwe-16.04 is already the newest version (4.15.0.46.67).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-drivers : Depends: nvidia-418 (>= 418.40.04) but it is not going to be installed
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not going to be installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not going to be installed
 libcuda1-418 : Depends: nvidia-418 (>= 418.56) but it is not going to be installed
 nvidia-418-dev : Depends: nvidia-418 (>= 418.56) but it is not going to be installed
 nvidia-opencl-icd-418 : Depends: nvidia-418 (>= 418.56) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-36 linux-headers-4.15.0-36-generic
  linux-modules-4.15.0-36-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
The following NEW packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
59 not fully installed or removed.
Need to get 0 B/546 MB of archives.
After this operation, 1,168 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 file:/var/cuda-repo-10-1-local-10.1.105-418.39  cuda-visual-tools-10-1 10.1.105-1 [398 MB]
Get:2 file:/var/cuda-repo-10-1-local-10.1.105-418.39  cuda-documentation-10-1 10.1.105-1 [50.4 MB]
(Reading database ... 338146 files and directories currently installed.)
Preparing to unpack .../cuda-visual-tools-10-1_10.1.105-1_amd64.deb ...
Unpacking cuda-visual-tools-10-1 (10.1.105-1) ...
dpkg: error processing archive /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-visual-tools-10-1_10.1.105-1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/local/cuda-10.1/nsightee_plugins/com.nvidia.cuda.repo-1.0.0-SNAPSHOT.zip' to '/usr/local/cuda-10.1/nsightee_plugins/com.nvidia.cuda.repo-1.0.0-SNAPSHOT.zip.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../cuda-documentation-10-1_10.1.105-1_amd64.deb ...
Unpacking cuda-documentation-10-1 (10.1.105-1) ...
dpkg: error processing archive /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-documentation-10-1_10.1.105-1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/local/cuda-10.1/doc/html/export/npp/group__image__resize__square__pixel.html' to '/usr/local/cuda-10.1/doc/html/export/npp/group__image__resize__square__pixel.html.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../nvidia-418_418.56-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-418 (418.56-0ubuntu0~gpu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-418_418.56-0ubuntu0~gpu16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/nvidia-418/libnvidia-rtcore.so.418.56' to '/usr/lib/nvidia-418/libnvidia-rtcore.so.418.56.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-visual-tools-10-1_10.1.105-1_amd64.deb
 /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-documentation-10-1_10.1.105-1_amd64.deb
 /var/cache/apt/archives/nvidia-418_418.56-0ubuntu0~gpu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cuda-drivers : Depends: nvidia-418 (>= 418.40.04) but it is not installed
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not installed
 libcuda1-418 : Depends: nvidia-418 (>= 418.56) but it is not installed
 nvidia-418-dev : Depends: nvidia-418 (>= 418.56) but it is not installed
 nvidia-opencl-icd-418 : Depends: nvidia-418 (>= 418.56) but it is not installed
E: Unmet dependencies. Try using -f.






$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cuda-drivers : Depends: nvidia-418 (>= 418.40.04) but it is not installed
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not installed
 libcuda1-418 : Depends: nvidia-418 (>= 418.56) but it is not installed
 nvidia-418-dev : Depends: nvidia-418 (>= 418.56) but it is not installed
 nvidia-opencl-icd-418 : Depends: nvidia-418 (>= 418.56) but it is not installed
E: Unmet dependencies. Try using -f.


$ sudo du -sh /var/cache/apt/archives
545M    /var/cache/apt/archives
$ sudo apt-get clean


$ sudo spt-get autoremove --purge
sudo: spt-get: command not found


$ sudo apt-get autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cuda-drivers : Depends: nvidia-418 (>= 418.40.04) but it is not installed
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not installed
 libcuda1-418 : Depends: nvidia-418 (>= 418.56) but it is not installed
 nvidia-418-dev : Depends: nvidia-418 (>= 418.56) but it is not installed
 nvidia-opencl-icd-418 : Depends: nvidia-418 (>= 418.56) but it is not installed
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/teamviewer.list:25 and /etc/apt/sources.list.d/teamviewer.list:30
E: Unmet dependencies. Try using -f.

$ sudo apt-get -f autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
The following packages will be REMOVED:
  linux-headers-4.15.0-36* linux-headers-4.15.0-36-generic*
  linux-modules-4.15.0-36-generic*
The following NEW packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
0 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
59 not fully installed or removed.
Need to get 97.4 MB/546 MB of archives.
After this operation, 1,012 MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.

$ sudo du -sh /var/cache/apt/archives
52K    /var/cache/apt/archives
veronica@veronica-Alienware-Aurora-R7:~$ dpkg --get-selections | grep linux-image
linux-image-4.15.0-45-generic            deinstall
linux-image-4.15.0-46-generic            install
linux-image-generic-hwe-16.04            install





$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not going to be installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

$ sudo apt install nvidia-418
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not going to be installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

$ sudo apt-get -f install
[sudo] password for veronica: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-36 linux-headers-4.15.0-36-generic
  linux-modules-4.15.0-36-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
The following NEW packages will be installed:
  cuda-documentation-10-1 cuda-visual-tools-10-1 nvidia-418
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
59 not fully installed or removed.
Need to get 97.4 MB/546 MB of archives.
After this operation, 1,168 MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.







```



[SIZE=3]Please help me with that. I am really struggled with it for two days.  Thank you in advanced![/SIZE]

---

### Post by VMC on 2019-03-30
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
```
I have always used the above post. Its a "dry run" so you can see what kernel gets deleted.

---

### Post by veronica-c on 2019-03-30
Thanks for your reply! This is what I got by running it:

```
$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-drivers : Depends: nvidia-418 (>= 418.40.04) but it is not going to be installed
 cuda-toolkit-10-1 : Depends: cuda-documentation-10-1 (>= 10.1.105) but it is not going to be installed
 cuda-tools-10-1 : Depends: cuda-visual-tools-10-1 (>= 10.1.105) but it is not going to be installed
 libcuda1-418 : Depends: nvidia-418 (>= 418.56) but it is not going to be installed
 linux-image-4.15.0-45-generic : Depends: linux-modules-4.15.0-45-generic but it is not going to be installed
 nvidia-418-dev : Depends: nvidia-418 (>= 418.56) but it is not going to be installed
 nvidia-opencl-icd-418 : Depends: nvidia-418 (>= 418.56) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And if I run 'apt-get -f install', it will repeat what I originally posted in this thread. Any other solutions?

---

### Post by veronica-c on 2019-03-30
Update: 

I also tried the solutions posted in this link but failed:[ https://ubuntuforums.org/showthread.php?t=2254523]("https://ubuntuforums.org/showthread.php?t=2254523")

Added the command line code to my original post.

---

### Post by VMC on 2019-03-30
You can follow this and its associated links for help:
[https://askubuntu.com/questions/563178/the-following-packages-have-unmet-dependencies](https://askubuntu.com/questions/563178/the-following-packages-have-unmet-dependencies)

---

### Post by veronica-c on 2019-03-30
Appreciate that! I tried the related link [https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)

However, when I run ```
$ sudo apt-get -f install
```. It shows that "You don't have enough free space in /var/cache/apt/archives/.". 

I tried to remove all the .deb files in the /var/cache/apt/archives/ but still got the same error messages. Now I am wondering is there any other way to make more space except resizing it with gparted? I don't want to resize the system as I would like to keep my files and my installations. Thanks again in advanced!



```
$ df -h /var/cache/apt/archives
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        21G   21G     0 100% /


$ sudo du -h /var/cache/apt/archives
4.0K	/var/cache/apt/archives/partial
52K	/var/cache/apt/archives


$ sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

$ sudo apt clean

$ sudo rm -f /var/cache/apt/archives/*.deb

$ df -h /var/cache/apt/archives
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        21G   20G     0 100% /

$ sudo fdisk -l
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F7AADD73-B9CF-40CF-8CD4-B1F6364850A2


Device          Start        End    Sectors   Size Type
/dev/sda1        2048     264191     262144   128M Microsoft reserved
/dev/sda2      264192 1030658047 1030393856 491.3G Microsoft basic data
/dev/sda3  1030658048 1074997247   44339200  21.1G Linux filesystem
/dev/sda4  1074997248 1192183807  117186560  55.9G Linux swap
/dev/sda5  1192183808 1194184703    2000896   977M EFI System
/dev/sda6  1194184704 3907028991 2712844288   1.3T Linux filesystem


$ sudo du -sh /var/log
21M	/var/log

$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0     11:0    1  1024M  0 rom  
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda4   8:4    0  55.9G  0 part [SWAP]
&#9500;&#9472;sda2   8:2    0 491.3G  0 part /media/veronica/DATA
&#9500;&#9472;sda5   8:5    0   977M  0 part /boot/efi
&#9500;&#9472;sda3   8:3    0  21.1G  0 part /
&#9500;&#9472;sda1   8:1    0   128M  0 part 
&#9492;&#9472;sda6   8:6    0   1.3T  0 part /home







```

---

### Post by VMC on 2019-03-30
That's one of the problems. The archives is what is left after an install. Are there any files in archive that match the [COLOR=#000000][FONT=&amp]dependencies above?
edit: Only the debs should be there. Only partial and locked after a clean out.. sudo list and find out what's inside the partial.[/FONT][/COLOR]

---

### Post by veronica-c on 2019-03-30
Here is what's inside the archives (I used "clean" before):

```
$ sudo -i
root@veronica-Alienware-Aurora-R7:~# cd /var/cache/apt/archives
root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives# ls
lock  partial



root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives# cd partial
root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives/partial# ls
root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives/partial#


```

It seems that nothing left in partial. Is it normal?

---

### Post by veronica-c on 2019-03-30
> **VMC said:**
> That's one of the problems. The archives is what is left after an install. Are there any files in archive that match the [COLOR=#000000][FONT=&amp]dependencies above?
edit: Only the debs should be there. Only partial and locked after a clean out.. sudo list and find out what's inside the partial.[/FONT][/COLOR]


I am sorry, new to the forum. I should reply with quote.

Here is what's inside the archives (I used "clean" before):

```
$ sudo -i
root@veronica-Alienware-Aurora-R7:~# cd /var/cache/apt/archives
root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives# ls
lock  partial



root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives# cd partial
root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives/partial# ls
root@veronica-Alienware-Aurora-R7:/var/cache/apt/archives/partial#


```

It seems that nothing left in partial. Is it normal?

---

### Post by VMC on 2019-03-31
using "[FONT=Arial, Helvetica Neue, Helvetica, sans-serif][COLOR=#242729]Disk Usage Analyzer" find the largest file usage inside sda3[/COLOR][/FONT]

---

### Post by veronica-c on 2019-03-31
> **VMC said:**
> using "[FONT=Arial][COLOR=#242729]Disk Usage Analyzer" find the largest file usage inside sda3[/COLOR][/FONT]

It seems that /var/lib/docker/overlay2 is the largest. The disk usage is shown in the following figures.

[ATTACH=CONFIG]282904[/ATTACH]
[ATTACH=CONFIG]282905[/ATTACH]
[ATTACH=CONFIG]282906[/ATTACH]

---

### Post by ajgreeny on 2019-03-31
Just to check the complete system partition usage let's see the output of commands ```
df -h
df -i
```

---

### Post by VMC on 2019-03-31
> **ajgreeny said:**
> Just to check the complete system partition usage let's see the output of commands ```
df -h
df -i
```
The OP supplied that info on the first post. He didn't supply the inodes.

---

### Post by veronica-c on 2019-03-31
Here is the inodes info.

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  130M  6.2G   3% /run
/dev/sda3        21G   21G     0 100% /
tmpfs            32G  228M   32G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/sda5       976M  3.7M  972M   1% /boot/efi
/dev/sda6       1.3T  224G  986G  19% /home
tmpfs           6.3G  156K  6.3G   1% /run/user/1000
/dev/sda2       492G  1.7G  490G   1% /media/veronica/DATA

$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             8200898    590   8200308    1% /dev
tmpfs            8209626    961   8208665    1% /run
/dev/sda3        1387200 465701    921499   34% /
tmpfs            8209626    318   8209308    1% /dev/shm
tmpfs            8209626      6   8209620    1% /run/lock
tmpfs            8209626     17   8209609    1% /sys/fs/cgroup
/dev/sda5              0      0         0     - /boot/efi
/dev/sda6       84779008 548126  84230882    1% /home
tmpfs            8209626     61   8209565    1% /run/user/1000
/dev/sda2      513492624     49 513492575    1% /media/veronica/DATA



```

---

### Post by veronica-c on 2019-03-31
> **VMC said:**
> The OP supplied that info on the first post. He didn't supply the inodes.

After I cleaned out all the files in /var/lib/docker/overlay2, it solved.  Thank you so much!!!

---

### Post by VMC on 2019-03-31
I didn't know what *docker* was, since I don't have one.  Some sort of container. 
Mark topic SOLVED. Thanks.

---

### Post by veronica-c on 2019-04-01
> **VMC said:**
> I didn't know what *docker* was, since I don't have one.  Some sort of container. 
Mark topic SOLVED. Thanks.


Marked it as solved.  

May you take a look at my new thread if you have time? I have trouble with environment variables.  Thank you very much!!!

[https://ubuntuforums.org/showthread.php?t=2415810&p=13848591#post13848591](https://ubuntuforums.org/showthread.php?t=2415810&p=13848591#post13848591)

---

