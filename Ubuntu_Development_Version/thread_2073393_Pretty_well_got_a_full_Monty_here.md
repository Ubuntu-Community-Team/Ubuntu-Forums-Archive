---
title: "Pretty well got a full Monty here:"
date: 2012-10-19
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-10-19
Just decided to change sources list and upgrade and got all of this:

```

 instead.
ventrical@ventrical-PY028AA-ABA-A1106N:~$ sudo apt-get update
Ign http://security.ubuntu.com raring-security InRelease
Ign http://security.ubuntu.com raring-security Release.gpg                     
Ign http://extras.ubuntu.com raring InRelease                                  
Ign http://security.ubuntu.com raring-security Release         
Ign http://extras.ubuntu.com raring Release.gpg                
Ign http://extras.ubuntu.com raring Release                    
Err http://extras.ubuntu.com raring/main Sources                               
  404  Not Found [IP: 91.189.88.33 80]
Err http://extras.ubuntu.com raring/main i386 Packages                         
  404  Not Found [IP: 91.189.88.33 80]
Ign http://extras.ubuntu.com raring/main Translation-en_CA                     
Ign http://extras.ubuntu.com raring/main Translation-en                        
Ign http://ca.archive.ubuntu.com raring InRelease                              
Ign http://ca.archive.ubuntu.com raring-updates InRelease
Ign http://ca.archive.ubuntu.com raring-backports InRelease
Get:1 http://ca.archive.ubuntu.com raring Release.gpg [933 B]
Get:2 http://ca.archive.ubuntu.com raring-updates Release.gpg [933 B]
Get:3 http://ca.archive.ubuntu.com raring-backports Release.gpg [933 B]
Get:4 http://ca.archive.ubuntu.com raring Release [49.6 kB]                    
Get:5 http://ca.archive.ubuntu.com raring-updates Release [49.6 kB]            
Get:6 http://ca.archive.ubuntu.com raring-backports Release [49.6 kB]          
Get:7 http://ca.archive.ubuntu.com raring/main Sources [873 kB]                
Get:8 http://ca.archive.ubuntu.com raring/restricted Sources [5,646 B]         
Get:9 http://ca.archive.ubuntu.com raring/universe Sources [5,522 kB]          
Err http://security.ubuntu.com raring-security/main Sources                    
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com raring-security/restricted Sources              
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com raring-security/universe Sources                
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com raring-security/multiverse Sources              
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com raring-security/main i386 Packages              
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com raring-security/restricted i386 Packages        
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com raring-security/universe i386 Packages          
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com raring-security/multiverse i386 Packages        
  404  Not Found [IP: 91.189.92.184 80]
Ign http://security.ubuntu.com raring-security/main Translation-en_CA          
Get:10 http://security.ubuntu.com raring-security/main Translation-en          
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_CA    
Get:11 http://security.ubuntu.com raring-security/multiverse Translation-en    
Ign http://security.ubuntu.com raring-security/restricted Translation-en_CA    
Get:12 http://security.ubuntu.com raring-security/restricted Translation-en    
Ign http://security.ubuntu.com raring-security/universe Translation-en_CA      
Get:13 http://security.ubuntu.com raring-security/universe Translation-en      
Err http://ca.archive.ubuntu.com raring/multiverse Sources                     
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/main Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/restricted Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/universe Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/main Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/restricted Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/universe Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/multiverse Sources
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/main i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/universe i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Err http://ca.archive.ubuntu.com raring-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.176 80]
Ign http://ca.archive.ubuntu.com raring/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring/main Translation-en
Ign http://ca.archive.ubuntu.com raring/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring/multiverse Translation-en
Ign http://ca.archive.ubuntu.com raring/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring/restricted Translation-en
Ign http://ca.archive.ubuntu.com raring/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com raring/universe Translation-en
Ign http://ca.archive.ubuntu.com raring-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/main Translation-en
Ign http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com raring-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com raring-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/universe Translation-en
Ign http://ca.archive.ubuntu.com raring-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/main Translation-en
Ign http://ca.archive.ubuntu.com raring-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/multiverse Translation-en
Ign http://ca.archive.ubuntu.com raring-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://ca.archive.ubuntu.com raring-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/universe Translation-en
Fetched 6,552 kB in 1min 20s (81.2 kB/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 91.189.88.33 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.33 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.176 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
ventrical@ventrical-PY028AA-ABA-A1106N:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cpp-4.7 gcc-4.7 gcc-4.7-base libgcc1 libgomp1 libitm1 libquadmath0
  libstdc++6
The following packages will be upgraded:
  apt apt-transport-https apt-utils aptdaemon aptdaemon-data cups cups-bsd
  cups-client cups-common cups-ppdc gnome-icon-theme grub-common grub-pc
  grub-pc-bin grub2-common initramfs-tools initramfs-tools-bin libapt-inst1.5
  libapt-pkg4.12 libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1
  python-aptdaemon python-aptdaemon.gtk3widgets python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-distupgrade
  software-center telepathy-indicator ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk unity-scope-gdocs upstart
36 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 8,645 kB of archives.
After this operation, 66.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring/main libapt-pkg4.12 i386 0.9.7.5ubuntu5 [816 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ raring/main apt i386 0.9.7.5ubuntu5 [1,155 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ raring/main libapt-inst1.5 i386 0.9.7.5ubuntu5 [70.9 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ raring/main cups-common all 1.6.1-0ubuntu11 [138 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ raring/main cups-bsd i386 1.6.1-0ubuntu11 [29.4 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ raring/main libcupsimage2 i386 1.6.1-0ubuntu11 [17.1 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ raring/main cups-client i386 1.6.1-0ubuntu11 [143 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ raring/main libcupsmime1 i386 1.6.1-0ubuntu11 [13.8 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ raring/main cups i386 1.6.1-0ubuntu11 [1,132 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ raring/main libcups2 i386 1.6.1-0ubuntu11 [192 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ raring/main libcupscgi1 i386 1.6.1-0ubuntu11 [30.3 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu/ raring/main libcupsppdc1 i386 1.6.1-0ubuntu11 [53.2 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu/ raring/main upstart i386 1.5-0ubuntu9 [292 kB]
Get:14 http://ca.archive.ubuntu.com/ubuntu/ raring/main cups-ppdc i386 1.6.1-0ubuntu11 [29.2 kB]
Get:15 http://ca.archive.ubuntu.com/ubuntu/ raring/main apt-utils i386 0.9.7.5ubuntu5 [186 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu/ raring/main initramfs-tools all 0.103ubuntu0.2 [49.0 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu/ raring/main initramfs-tools-bin i386 0.103ubuntu0.2 [9,686 B]
Get:18 http://ca.archive.ubuntu.com/ubuntu/ raring/main apt-transport-https i386 0.9.7.5ubuntu5 [15.6 kB]
Get:19 http://ca.archive.ubuntu.com/ubuntu/ raring/main ubuntu-release-upgrader-gtk all 1:0.190.1 [11.0 kB]
Get:20 http://ca.archive.ubuntu.com/ubuntu/ raring/main ubuntu-release-upgrader-core all 1:0.190.1 [27.8 kB]
Get:21 http://ca.archive.ubuntu.com/ubuntu/ raring/main python3-distupgrade all 1:0.190.1 [140 kB]
Get:22 http://ca.archive.ubuntu.com/ubuntu/ raring/main gnome-icon-theme all 3.6.0-0ubuntu2 [662 kB]
Get:23 http://ca.archive.ubuntu.com/ubuntu/ raring/main grub-pc i386 2.00-7ubuntu11 [169 kB]
Get:24 http://ca.archive.ubuntu.com/ubuntu/ raring/main grub-pc-bin i386 2.00-7ubuntu11 [803 kB]
Get:25 http://ca.archive.ubuntu.com/ubuntu/ raring/main grub2-common i386 2.00-7ubuntu11 [116 kB]
Get:26 http://ca.archive.ubuntu.com/ubuntu/ raring/main grub-common i386 2.00-7ubuntu11 [1,286 kB]
Get:27 http://ca.archive.ubuntu.com/ubuntu/ raring/main aptdaemon-data all 0.45+bzr861-0ubuntu9.1 [162 kB]
Get:28 http://ca.archive.ubuntu.com/ubuntu/ raring/main python3-aptdaemon.gtk3widgets all 0.45+bzr861-0ubuntu9.1 [14.6 kB]
Get:29 http://ca.archive.ubuntu.com/ubuntu/ raring/main python3-aptdaemon.pkcompat all 0.45+bzr861-0ubuntu9.1 [34.0 kB]
Get:30 http://ca.archive.ubuntu.com/ubuntu/ raring/main aptdaemon all 0.45+bzr861-0ubuntu9.1 [14.5 kB]
Get:31 http://ca.archive.ubuntu.com/ubuntu/ raring/main python3-aptdaemon all 0.45+bzr861-0ubuntu9.1 [82.9 kB]
Get:32 http://ca.archive.ubuntu.com/ubuntu/ raring/main python-aptdaemon.gtk3widgets all 0.45+bzr861-0ubuntu9.1 [14.9 kB]
Get:33 http://ca.archive.ubuntu.com/ubuntu/ raring/main python-aptdaemon all 0.45+bzr861-0ubuntu9.1 [83.3 kB]
Get:34 http://ca.archive.ubuntu.com/ubuntu/ raring/main software-center all 5.4.1.2 [627 kB]
Get:35 http://ca.archive.ubuntu.com/ubuntu/ raring/main telepathy-indicator i386 0.3.0-0ubuntu3 [15.9 kB]
Get:36 http://ca.archive.ubuntu.com/ubuntu/ raring/main unity-scope-gdocs all 0.7-0ubuntu1 [10.7 kB]
Fetched 8,645 kB in 1min 3s (136 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 151143 files and directories currently installed.)
Preparing to replace libapt-pkg4.12:i386 0.9.7.5ubuntu3 (using .../libapt-pkg4.12_0.9.7.5ubuntu5_i386.deb) ...
Unpacking replacement libapt-pkg4.12:i386 ...
Setting up libapt-pkg4.12:i386 (0.9.7.5ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 151143 files and directories currently installed.)
Preparing to replace apt 0.9.7.5ubuntu3 (using .../apt_0.9.7.5ubuntu5_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.9.7.5ubuntu5) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 151143 files and directories currently installed.)
Preparing to replace libapt-inst1.5:i386 0.9.7.5ubuntu3 (using .../libapt-inst1.5_0.9.7.5ubuntu5_i386.deb) ...
Unpacking replacement libapt-inst1.5:i386 ...
Preparing to replace cups-common 1.6.1-0ubuntu10 (using .../cups-common_1.6.1-0ubuntu11_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.6.1-0ubuntu10 (using .../cups-bsd_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace libcupsimage2:i386 1.6.1-0ubuntu10 (using .../libcupsimage2_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement libcupsimage2:i386 ...
Preparing to replace cups-client 1.6.1-0ubuntu10 (using .../cups-client_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement cups-client ...
Preparing to replace libcupsmime1:i386 1.6.1-0ubuntu10 (using .../libcupsmime1_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement libcupsmime1:i386 ...
Preparing to replace cups 1.6.1-0ubuntu10 (using .../cups_1.6.1-0ubuntu11_i386.deb) ...
cups stop/waiting
Unpacking replacement cups ...
Preparing to replace libcups2:i386 1.6.1-0ubuntu10 (using .../libcups2_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement libcups2:i386 ...
Preparing to replace libcupscgi1:i386 1.6.1-0ubuntu10 (using .../libcupscgi1_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement libcupscgi1:i386 ...
Preparing to replace libcupsppdc1:i386 1.6.1-0ubuntu10 (using .../libcupsppdc1_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement libcupsppdc1:i386 ...
Preparing to replace upstart 1.5-0ubuntu8 (using .../upstart_1.5-0ubuntu9_i386.deb) ...
Unpacking replacement upstart ...
Preparing to replace cups-ppdc 1.6.1-0ubuntu10 (using .../cups-ppdc_1.6.1-0ubuntu11_i386.deb) ...
Unpacking replacement cups-ppdc ...
Preparing to replace apt-utils 0.9.7.5ubuntu3 (using .../apt-utils_0.9.7.5ubuntu5_i386.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace initramfs-tools 0.103ubuntu0.1 (using .../initramfs-tools_0.103ubuntu0.2_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace initramfs-tools-bin 0.103ubuntu0.1 (using .../initramfs-tools-bin_0.103ubuntu0.2_i386.deb) ...
Unpacking replacement initramfs-tools-bin ...
Preparing to replace apt-transport-https 0.9.7.5ubuntu3 (using .../apt-transport-https_0.9.7.5ubuntu5_i386.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace ubuntu-release-upgrader-gtk 1:0.189 (using .../ubuntu-release-upgrader-gtk_1%3a0.190.1_all.deb) ...
Unpacking replacement ubuntu-release-upgrader-gtk ...
Preparing to replace ubuntu-release-upgrader-core 1:0.189 (using .../ubuntu-release-upgrader-core_1%3a0.190.1_all.deb) ...
Unpacking replacement ubuntu-release-upgrader-core ...
Preparing to replace python3-distupgrade 1:0.189 (using .../python3-distupgrade_1%3a0.190.1_all.deb) ...
Unpacking replacement python3-distupgrade ...
Preparing to replace gnome-icon-theme 3.6.0-0ubuntu1 (using .../gnome-icon-theme_3.6.0-0ubuntu2_all.deb) ...
Unpacking replacement gnome-icon-theme ...
Preparing to replace grub-pc 2.00-7ubuntu10 (using .../grub-pc_2.00-7ubuntu11_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-pc-bin 2.00-7ubuntu10 (using .../grub-pc-bin_2.00-7ubuntu11_i386.deb) ...
Unpacking replacement grub-pc-bin ...
Preparing to replace grub2-common 2.00-7ubuntu10 (using .../grub2-common_2.00-7ubuntu11_i386.deb) ...
Unpacking replacement grub2-common ...
Preparing to replace grub-common 2.00-7ubuntu10 (using .../grub-common_2.00-7ubuntu11_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace aptdaemon-data 0.45+bzr861-0ubuntu9 (using .../aptdaemon-data_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement aptdaemon-data ...
Preparing to replace python3-aptdaemon.gtk3widgets 0.45+bzr861-0ubuntu9 (using .../python3-aptdaemon.gtk3widgets_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement python3-aptdaemon.gtk3widgets ...
Preparing to replace python3-aptdaemon.pkcompat 0.45+bzr861-0ubuntu9 (using .../python3-aptdaemon.pkcompat_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement python3-aptdaemon.pkcompat ...
Preparing to replace aptdaemon 0.45+bzr861-0ubuntu9 (using .../aptdaemon_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement aptdaemon ...
Preparing to replace python3-aptdaemon 0.45+bzr861-0ubuntu9 (using .../python3-aptdaemon_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement python3-aptdaemon ...
Preparing to replace python-aptdaemon.gtk3widgets 0.45+bzr861-0ubuntu9 (using .../python-aptdaemon.gtk3widgets_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement python-aptdaemon.gtk3widgets ...
Preparing to replace python-aptdaemon 0.45+bzr861-0ubuntu9 (using .../python-aptdaemon_0.45+bzr861-0ubuntu9.1_all.deb) ...
Unpacking replacement python-aptdaemon ...
Preparing to replace software-center 5.4.1.1 (using .../software-center_5.4.1.2_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace telepathy-indicator 0.3.0-0ubuntu1 (using .../telepathy-indicator_0.3.0-0ubuntu3_i386.deb) ...
Unpacking replacement telepathy-indicator ...
Preparing to replace unity-scope-gdocs 0.6-0ubuntu1 (using .../unity-scope-gdocs_0.7-0ubuntu1_all.deb) ...
Unpacking replacement unity-scope-gdocs ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 33 changed doc-base files...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for install-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up libapt-inst1.5:i386 (0.9.7.5ubuntu5) ...
Setting up cups-common (1.6.1-0ubuntu11) ...
Setting up libcups2:i386 (1.6.1-0ubuntu11) ...
Setting up libcupsimage2:i386 (1.6.1-0ubuntu11) ...
Setting up cups-client (1.6.1-0ubuntu11) ...
Setting up cups-bsd (1.6.1-0ubuntu11) ...
Setting up libcupsmime1:i386 (1.6.1-0ubuntu11) ...
Setting up libcupscgi1:i386 (1.6.1-0ubuntu11) ...
Setting up libcupsppdc1:i386 (1.6.1-0ubuntu11) ...
Setting up upstart (1.5-0ubuntu9) ...
Setting up cups-ppdc (1.6.1-0ubuntu11) ...
Setting up cups (1.6.1-0ubuntu11) ...
cups start/running, process 4703
Updating PPD files for cups ...
Updating PPD files for cups-filters ...
Updating PPD files for foomatic-db-compressed-ppds ...
Updating PPD files for foomatic-db-engine ...
Updating PPD files for ghostscript-cups ...
Updating PPD files for openprinting-ppds ...
Updating PPD files for c2esp ...
Updating PPD files for foo2zjs ...
Updating PPD files for gutenprint ...
Updating PPD files for hpcups ...
Updating PPD files for hpijs ...
Updating PPD files for postscript-hp ...
Updating PPD files for ptouch ...
Updating PPD files for pxljr ...
Updating PPD files for sag-gdi ...
Updating PPD files for splix ...
Setting up apt-utils (0.9.7.5ubuntu5) ...
Setting up initramfs-tools-bin (0.103ubuntu0.2) ...
Setting up initramfs-tools (0.103ubuntu0.2) ...
update-initramfs: deferring update (trigger activated)
Setting up apt-transport-https (0.9.7.5ubuntu5) ...
Setting up python3-distupgrade (1:0.190.1) ...
Setting up ubuntu-release-upgrader-core (1:0.190.1) ...
Setting up ubuntu-release-upgrader-gtk (1:0.190.1) ...
Setting up gnome-icon-theme (3.6.0-0ubuntu2) ...
Setting up grub-common (2.00-7ubuntu11) ...
Setting up grub2-common (2.00-7ubuntu11) ...
Setting up grub-pc-bin (2.00-7ubuntu11) ...
Setting up grub-pc (2.00-7ubuntu11) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up aptdaemon-data (0.45+bzr861-0ubuntu9.1) ...
Setting up python3-aptdaemon (0.45+bzr861-0ubuntu9.1) ...
Setting up python3-aptdaemon.gtk3widgets (0.45+bzr861-0ubuntu9.1) ...
Setting up python3-aptdaemon.pkcompat (0.45+bzr861-0ubuntu9.1) ...
Setting up aptdaemon (0.45+bzr861-0ubuntu9.1) ...
Setting up python-aptdaemon (0.45+bzr861-0ubuntu9.1) ...
Setting up python-aptdaemon.gtk3widgets (0.45+bzr861-0ubuntu9.1) ...
Setting up software-center (5.4.1.2) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Setting up telepathy-indicator (0.3.0-0ubuntu3) ...
Setting up unity-scope-gdocs (0.7-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```

This is on an HP machine with a fresh install of QQ RC-i386  that had not been updated.

---

### Post by GreenTaurus on 2012-10-19
Looking pretty good there.

---

### Post by ventrical on 2012-10-19
I installed synaptic and got this:

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libept1.4.12 librarian0 libvte-common libvte9 rarian-compat
  sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide perlsgml w3-recs opensp
  libxml2-utils dwww menu deborphan
The following NEW packages will be installed:
  docbook-xml libept1.4.12 librarian0 libvte-common libvte9 rarian-compat
  sgml-data synaptic
0 upgraded, 8 newly installed, 0 to remove and 8 not upgraded.
Need to get 3,749 kB of archives.
After this operation, 13.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring/main sgml-data all 2.0.8 [276 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ raring/main docbook-xml all 4.5-7ubuntu1 [336 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ raring/main libept1.4.12 i386 1.0.9 [136 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ raring/main libvte-common all 1:0.28.2-5ubuntu1 [22.8 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ raring/main libvte9 i386 1:0.28.2-5ubuntu1 [372 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ raring/main librarian0 i386 0.8.1-5build1 [58.4 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ raring/main rarian-compat i386 0.8.1-5build1 [100 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ raring/universe synaptic i386 0.75.12build1 [2,447 kB]
Fetched 3,749 kB in 26s (140 kB/s)                                             
Selecting previously unselected package sgml-data.
(Reading database ... 151148 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.8_all.deb) ...
Selecting previously unselected package docbook-xml.
Unpacking docbook-xml (from .../docbook-xml_4.5-7ubuntu1_all.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.9_i386.deb) ...
Selecting previously unselected package libvte-common.
Unpacking libvte-common (from .../libvte-common_1%3a0.28.2-5ubuntu1_all.deb) ...
Selecting previously unselected package libvte9.
Unpacking libvte9 (from .../libvte9_1%3a0.28.2-5ubuntu1_i386.deb) ...
Selecting previously unselected package librarian0.
Unpacking librarian0 (from .../librarian0_0.8.1-5build1_i386.deb) ...
Selecting previously unselected package rarian-compat.
Unpacking rarian-compat (from .../rarian-compat_0.8.1-5build1_i386.deb) ...
Selecting previously unselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.12build1_i386.deb) ...
Processing triggers for sgml-base ...
Updating the super catalog...
Processing triggers for doc-base ...
Scrollkeeper was installed, forcing re-registration of all documents.
Unregistering 33 doc-base files, re-registering 33 doc-base files...
Registering documents with scrollkeeper...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up sgml-data (2.0.8) ...
Setting up libept1.4.12 (1.0.9) ...
Setting up libvte-common (1:0.28.2-5ubuntu1) ...
Setting up libvte9 (1:0.28.2-5ubuntu1) ...
Setting up librarian0 (0.8.1-5build1) ...
Setting up synaptic (0.75.12build1) ...
Processing triggers for sgml-base ...
Updating the super catalog...
Setting up docbook-xml (4.5-7ubuntu1) ...
update-catalog: Suppressing action on super catalog. Invoking trigger instead.
update-catalog: Please rebuild the package being set up with a version of debhelper fixing #477751.
Processing triggers for sgml-base ...
Updating the super catalog...
Setting up rarian-compat (0.8.1-5build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```

and this screenshot:

---

### Post by ventrical on 2012-10-19
However, I decided to leave the ubuntu security repos unticked just too see what happens :)

---

### Post by ventrical on 2012-10-19
> **GreenTaurus said:**
> Looking pretty good there.

 Looks like the devs decided not to rest or break ...  raring to go !!:)

 Lets get ready to rumble !

lol :)

---

### Post by philinux on 2012-10-19
You'll get a better response come the 25th or thereafter. See the sticky Re release schedule.

---

### Post by ventrical on 2012-10-19
> **philinux said:**
> You'll get a better response come the 25th or thereafter. See the sticky Re release schedule.


Thanks Philinux. I had seen that .. but I'm happy  with even a  few pieces of code  to chomp on  here or there .. Ha! :)

---

### Post by grahammechanical on 2012-10-19
@ventrical

that is all very well but is there anything that says 13.04? System Monitor? Details? lsb_release -a? It ain't Raring Ringtail until it says it is. :) May be you've got some other kind of raccoon by the tail. :)

regards.

---

### Post by ventrical on 2012-10-19
ubuntu-logo-ringtail-sharif-1350551136.jpg

I screen captured the above. Thats the official logo.

 I know .. it's not much .. but its somthing :)

---

### Post by ventrical on 2012-10-19
> **grahammechanical said:**
> @ventrical

 :) May be you've got some other kind of raccoon by the tail. :)

regards.

 Yes . .perhaps a flying racoon with green feathers still.  Dern . :) lol

---

### Post by ventrical on 2012-10-22
I got this now with 'raring' in it.

**Index of /~kernel-ppa/mainline/v3.7-rc2-raring**



so that worked ! :)


Now to try with nvidia graphics.

---

### Post by ventrical on 2012-10-23
Ta Da,

Recent updates and I'm in:

```

dale@dale-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring
dale@dale-desktop:~$ 

```

---

### Post by sparker256 on 2012-10-23
Same here with the latest updates
```

bill@billsim-64-1304:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Raring Ringtail (development branch)
Release:	13.04
Codename:	raring
bill@billsim-64-1304:~$ uname -r
3.7.0-030700rc1-generic
bill@billsim-64-1304:~$ 

```
Still getting a imediate Kernel PANIC when I select 3.7.0-rc2

Bill

---

### Post by cecilpierce on 2012-10-23
@sparker256

I had to purge 3.7.0, I could not get nvidia to install, spent half a day fooling with it...:mad:

---

### Post by Harry33 on 2012-10-23
> **cecilpierce said:**
> @sparker256

I had to purge 3.7.0, I could not get nvidia to install, spent half a day fooling with it...:mad:

The nvidia-current package ought to be patched for kernel 3.7.*.
Did you try the xorg-edgers version 310.14 (quantal series)?
That one is patched for kernel 3.7.*

---

### Post by cecilpierce on 2012-10-23
> **Harry33 said:**
> The nvidia-current package ought to be patched for kernel 3.7.*.
Did you try the xorg-edgers version 310.14 (quantal series)?
That one is patched for kernel 3.7.*

Yea I tried that and everything I could think of but something was screwed up I guess, have too many irons in the fire ! And the fire anit lit :P

---

### Post by jerrylamos on 2012-10-23
Been trying 12.10/QQ installs every day since 10/17 on my netbook notebook tower. 

All kinds of bugs and kinks, different ones on every install/update on each pc except wireless WPA which is a pain on QQ and 12.10 just fine on Precise..  Of course 12.04.1 runs solid as a rock.

Finally got a 12.10 install today's zsync that would actually boot and run right off.   Acer Aspire 5253 2GB amd64 dual processors 1.6 gHz.  

Buggiest release code I can remember going back to Dapper Drake.

Anyway, if this 12.10 will run for a couple more days I'll try the sources.list if this forum looks O.K.  12.04.1 is my backup/recovery.

---

### Post by ventrical on 2012-10-24
> **jerrylamos said:**
> Been trying 12.10/QQ installs every day since 10/17 on my netbook notebook tower. 

All kinds of bugs and kinks, different ones on every install/update on each pc except wireless WPA which is a pain on QQ and 12.10 just fine on Precise..  Of course 12.04.1 runs solid as a rock.

Finally got a 12.10 install today's zsync that would actually boot and run right off.   Acer Aspire 5253 2GB amd64 dual processors 1.6 gHz.  

Buggiest release code I can remember going back to Dapper Drake.

Anyway, if this 12.10 will run for a couple more days I'll try the sources.list if this forum looks O.K.  12.04.1 is my backup/recovery.

I had installed QQ during development on 8 different machines (including 2 laptops) and the bug activity is minimal, in fact non existent. That is not to say that there are none or that I am actively looking for them on QQ . At all my workstations, QQ has been an improvement (with the exception of loosing Unity 2D).

  I have since migrated to the begginings of the Raring toolchain on two different machines so far and that process has went flawlessly with  the new 3.7.xxxRC2 kernel.

  I haven't tried that migration on my laptops yet.

---

### Post by cariboo on 2012-10-24
I'm in too:

> cariboo@alexis:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"

I was going to wait until the weekend, but I got bored. :-D

---

### Post by wheeze on 2012-10-25
I installed a 11.04 mini.iso I had sitting around, then changed sources to raring and did a dist-upgrade. No problem, went very smoothly. I checked which repos were available and only changed those for now. No 404 errors during apt upgrade.

Soooo, I went ahead and installed xubuntu-desktop. Hey! I'm running Xubuntu 13.04 now :)

---

### Post by ventrical on 2012-10-25
> **wheeze said:**
> I installed a 11.04 mini.iso I had sitting around, then changed sources to raring and did a dist-upgrade. No problem, went very smoothly. I checked which repos were available and only changed those for now. No 404 errors during apt upgrade.

Soooo, I went ahead and installed xubuntu-desktop. Hey! I'm running Xubuntu 13.04 now :)


 Actually , when I booted up this morning, the Plymouth screen  displayed "Ubuntu 13.04". I wonder why we are getting all of this so early? Only explanation I have is that Raring is Raring to go !! :)

---

### Post by PaulW2U on 2012-10-25
> **wheeze said:**
> I installed a 11.04 mini.iso I had sitting around, then changed sources to raring and did a dist-upgrade.

11.04 straight to 13.04? That was adventurous. :)

```
paul@G620:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:        13.04
Codename:       raring

```

Running 13.04 of the Kubuntu variety here.

---

### Post by serdotlinecho on 2012-10-25
> Actually , when I booted up this morning, the Plymouth screen  displayed  "Ubuntu 13.04". I wonder why we are getting all of this so early? Only  explanation I have is that Raring is Raring to go !! :smile:

Wow, really? But I didn't see any ubuntu 13.04? At lightdm login manager?

---

### Post by wheeze on 2012-10-25
> **PaulW2U said:**
> 11.04 straight to 13.04? That was adventurous. :smile:

Well, it was a mini install so there wasn't all that much to upgrade :) Took about 18 minutes to download the upgrade via my 1.5 Mb DSL connection. Kept the stock 3.5 kernel for now. Just wanted to see what I could get going already.

> **ventrical said:**
> Actually , when I booted up this morning, the Plymouth screen  displayed "Ubuntu 13.04". I wonder why we are getting all of this so early? Only explanation I have is that Raring is Raring to go !! :)

Yep, before I installed xubuntu-desktop, I had the 13.04 plymouth screen going on. Fun to see the new stuff pop up :)

---

### Post by wheeze on 2012-10-25
:popcorn:

```
steve@ubu-raring:~$ inxi -SxxxGxFr
System:    Host: ubu-raring Kernel: 3.5.0-17-generic x86_64 (64 bit, gcc: 4.7.2) 
           Desktop: Xfce 4.10.0 (Gtk 2.24.10) info: xfce4-panel dm: lightdm Distro: Ubuntu 13.04 raring
Machine:   Mobo: Abit model: AV8 (VIA K8T800P-8237) version: 1.x Bios: Phoenix version: 6.00 PG date: 05/17/2006
CPU:       Single core AMD Athlon 64 3000+ (-UP-) cache: 512 KB flags: (lm nx sse sse2) bmips: 2043.11 clocked at 1000.00 MHz 
Graphics:  Card: NVIDIA NV44A [GeForce 6200] bus-ID: 01:00.0 chip-ID: 10de:0221 
           X.Org: 1.13.0 driver: FAILED: nouveau Resolution: 1280x1024@60.0hz 
           GLX Renderer: Gallium 0.4 on NV4A GLX Version: 2.1 Mesa 9.0 Direct Rendering: Yes
Audio:     Card: VIA VT8233/A/8235/8237 AC97 Audio Controller 
           driver: snd_via82xx port: d800 bus-ID: 00:11.5 chip-ID: 1106:3059 
           Sound: Advanced Linux Sound Architecture ver: 1.0.25
Network:   Card: VIA VT6120/VT6121/VT6122 Gigabit Ethernet Adapter 
           driver: via-velocity port: d000 bus-ID: 00:0e.0 chip-ID: 1106:3119
           IF: eth0 state: unknown speed: 100 Mbps duplex: full mac: 00:50:8d:d1:60:52
Drives:    HDD Total Size: 580.1GB (0.5% used)
           1: id: /dev/sda model: ST3500418AS size: 500.1GB serial: 9VMMCKZY 
           2: id: /dev/sdb model: ST380817AS size: 80.0GB serial: 4MR025E2 
Partition: ID: / size: 17G used: 2.7G (17%) fs: ext4 ID: swap-1 size: 3.00GB used: 0.00GB (0%) fs: swap 
RAID:      System: supported: N/A
           No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 33.0C mobo: N/A gpu: 49.0 
           Fan Speeds (in rpm): cpu: N/A 
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://mirror.hmc.edu/ubuntu/ raring-backports main restricted universe multiverse
           deb http://mirror.hmc.edu/ubuntu/ raring-proposed main restricted multiverse universe
           deb http://mirror.hmc.edu/ubuntu/ raring-security main restricted universe multiverse
           deb http://mirror.hmc.edu/ubuntu/ raring-updates main restricted universe multiverse
           deb http://mirror.hmc.edu/ubuntu/ raring main restricted universe multiverse
           deb http://archive.canonical.com/ubuntu/ raring partner
Info:      Processes: 136 Uptime: 21 min Memory: 481.0/3010.2MB Runlevel: 2 Gcc sys: 4.7.2 Client: Shell inxi: 1.8.20 

```

---

### Post by mc4man on 2012-10-25
ATM (until raring repos open) you'll find newer packages to use/test in quantal-proposed/updates/security.

---

### Post by jerrylamos on 2012-10-25
Replace all quantal with raring in /etc/apt/sources.list, did update dist-upgrade, didn't complain about missing anything 10/25/2012 3 pm EST.

Some updates not too many.

Same raring problems on this amd64 Acer Aspire 5253 as quantal RC and release:

booting with splash specified splash never displays and stops at solid purple screen.  No cursor.  Press Esc, Alt-F1 nothing appears.  
Ctrl-Alt-Del eventually reboots.  Yes there's a bug written.
"Advanced Options" is a real mess, sluggish jerky 1024x768 instead of 1366x768.  Ugh.  Useless.
Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
Usually boots if splash quiet and vt handoff removed from linux line.

Hidden wireless WPA security automatically disconnects. Have to go into systems settings network manager and flail around with the sluggish drop downs eventually connects.  On every boot.  Yes there's a bug written,

Oh, of course, presice 12.04.1 runs like a champ....

Yes I've got 12.04.1 and 12.10 partitions for backup when raring updates clash....

---

### Post by ventrical on 2012-10-25
> **serdotlinecho said:**
> Wow, really? But I didn't see any ubuntu 13.04? At lightdm login manager?

 No . Not at LightDM. It still said 12.10. The screen before that one. The Plymouth screen after GRUB.

---

### Post by jerrylamos on 2012-10-25
This one says:

Distributor ID:	Ubuntu
Description:	Ubuntu Raring Ringtail (development branch)
Release:	13.04
Codename:	raring
Linux version 3.5.0-17-generic (buildd@allspice) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012

---

### Post by serdotlinecho on 2012-10-27
>  No . Not at LightDM. It still said 12.10. The screen before that one. The Plymouth screen after GRUB.

Oh, that one. But i didn't see any 13.04, just magenta blank wall colour. Then ubuntu logo with 5 dots appeared.

---

### Post by ventrical on 2012-10-27
> **serdotlinecho said:**
> Oh, that one. But i didn't see any 13.04, just magenta blank wall colour. Then ubuntu logo with 5 dots appeared.

 I'll take a screen pic with my camera.

---

### Post by ventrical on 2012-10-27
Re: 13.04
Please do not mind the video quality:) lol

[http://www.youtube.com/watch?v=Jhe2pKyNpbk&feature=youtu.be](http://www.youtube.com/watch?v=Jhe2pKyNpbk&feature=youtu.be)

---

### Post by serdotlinecho on 2012-10-28
I only have regular or default ubuntu plymouth.

[IMG]http://www.thefanclub.co.za/sites/default/files/styles/300-wide/public/images/howto/ubuntu-boot-splash.png[/IMG]

---

### Post by Chdslv on 2012-10-28
Bleeding edge!
Ubuntu Gnome Remix 13.04
Couldn't get kernel 3.7-rc2, but would come in time.:)

> chdslv@chdslv:~$ lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring
chdslv@chdslv:~$ uname -a
Linux chdslv 3.6.2-030602-generic #201210121823 SMP Fri Oct 12 22:31:22 UTC 2012 i686 i686 i686 GNU/Linux 

---

### Post by ventrical on 2012-10-28
Nice looking desktop there :)

---

### Post by Chdslv on 2012-10-28
The same Ubuntu Gnome Remix 13.04, but with Unity

---

### Post by Chdslv on 2012-10-28
> **ventrical said:**
> Nice looking desktop there :)

That desktop is from Ubuntu-Tweak's Love Wallpaper :)

---

### Post by wheeze on 2012-10-28
> **Chdslv said:**
> Bleeding edge!
Ubuntu Gnome Remix 13.04
Couldn't get kernel 3.7-rc2, but would come in time.:)

Is there a *-desktop package for the GNOME Remix? I'd like to give that a try, too :)

---

### Post by Chdslv on 2012-10-28
> **wheeze said:**
> Is there a *-desktop package for the GNOME Remix? I'd like to give that a try, too :)

The easy way; go to [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10) and download it. After installing it, change the repos to** raring**, then update and upgrade. You are in 13.04 development release, which is the bleeding edge ditro.

The hard way; download and install 12.10 mini.iso and change the repos to **raring**, update and upgrade, apt-get install gnome-shell. You'd have to install Firefox, Synaptic and anything you like. This is even snappier than the above and you are in bleeding edge.:)

After installing Gnome-shell, you could install Unity too and then you'd have the best of both, plus Gnome-Classic too.

---

### Post by cariboo on 2012-10-29
When upgrading to a development version, I use the following two commands:

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```

Once you've changed the version names use the following command:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by wheeze on 2012-10-29
> **Chdslv said:**
> The hard way; download and install 12.10 mini.iso and change the repos to **raring..**.

This isn't the hard way, it's how I do 99% of my installations! :lol:

---

### Post by Chdslv on 2012-10-29
> **wheeze said:**
> This isn't the hard way, it's how I do 99% of my installations! :lol:

I agree!

That's the best way to install Ubuntu. I have a coffee while waiting and read a book. We get the bleeding edge distro with only those apps we need. I downloaded other Ubuntu variants to have a look. :)

13.04 is really flying in my nearly 4 year old laptop!

---

### Post by wheeze on 2012-10-29
> **Chdslv said:**
> I agree!

That's the best way to install Ubuntu. I have a coffee while waiting and read a book. We get the bleeding edge distro with only those apps we need. I downloaded other Ubuntu variants to have a look. :)

13.04 is really flying in my nearly 4 year old laptop!

Yeah, the only problem with this method is that I rarely have any issues to report :lol:

My PC is an old home-built from around 2004. The last BIOS upgrade available from the motherboard manufacturer was from 2006! I've got a single-core Athlon 64, 3 GB RAM and an old nVidia 6200 AGP video card and it runs anything I throw on it. Raring is performing very nicely on the old warhorse.

---

