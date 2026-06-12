---
title: "Tried to run sudo apt update in Ubuntu 22.04"
date: 2022-03-12
forum: Ubuntu Development Version
---

### Post by Joe_Linux on 2022-03-12
Tried to run sudo apt update in Ubuntu 22.04 the following was my result.
```
buntu@ubuntu:~$ sudo apt update
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220228) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220228) jammy Release
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease         
Get:5 http://archive.ubuntu.com/ubuntu jammy InRelease [270 kB]          
Hit:6 https://ppa.launchpadcontent.net/mkusb/unstable/ubuntu jammy InRelease   
Hit:7 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                 
Get:8 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages [1404 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy/main amd64 DEP-11 Metadata [428 kB]
Get:10 http://archive.ubuntu.com/ubuntu jammy/main amd64 c-n-f Metadata [30.0 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [14.2 MB]
Get:12 http://archive.ubuntu.com/ubuntu jammy/universe Translation-en [5642 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy/universe amd64 DEP-11 Metadata [3583 kB]
Get:14 http://archive.ubuntu.com/ubuntu jammy/universe DEP-11 48x48 Icons [3425 kB]
Get:15 http://archive.ubuntu.com/ubuntu jammy/universe DEP-11 64x64 Icons [7613 kB]
Get:16 http://archive.ubuntu.com/ubuntu jammy/universe amd64 c-n-f Metadata [286 kB]
Fetched 36.8 MB in 34s (1077 kB/s)                                             
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ubuntu:~$ apt list --upgradable
Listing... Done
libexpat1/jammy 2.4.7-1 amd64 [upgradable from: 2.4.6-1]
python3-renderpm/jammy 3.6.8-1 amd64 [upgradable from: 3.6.7-1ubuntu1]
python3-reportlab-accel/jammy 3.6.8-1 amd64 [upgradable from: 3.6.7-1ubuntu1]
python3-reportlab/jammy 3.6.8-1 all [upgradable from: 3.6.7-1ubuntu1]
ubuntu@ubuntu:~$ sudo apt update libexpat1/jammy 2.4.7-1 amd64 
E: The update command takes no arguments
ubuntu@ubuntu:~$ sudo apt update jammy 2.4.7-1 amd64
E: The update command takes no arguments
ubuntu@ubuntu:~$ sudo apt update jammy 2.4.7-1
E: The update command takes no arguments
ubuntu@ubuntu:~$ sudo apt update
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220228) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220228) jammy Release
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                 
Hit:7 https://ppa.launchpadcontent.net/mkusb/unstable/ubuntu jammy InRelease   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ubuntu:~$ 

```
How would I update using sudo apt update ?
Thank you in advance.
PS already used the software updater on 03/11/12

---

### Post by corradoventu on 2022-03-12
after apt update you must run ```
sudo apt upgrade
```

---

### Post by Joe_Linux on 2022-03-12
Thank you 
```
ubuntu@ubuntu:~$ sudo apt update
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220228) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220228) jammy Release
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:5 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                 
Hit:7 https://ppa.launchpadcontent.net/mkusb/unstable/ubuntu jammy InRelease   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ubuntu:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gnome-screenshot libcmis-0.5-5v5 libicu67 libmozjs-78-0 libneon27-gnutls
  libpoppler115 libpython3.9 libwebp6
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libexpat1 python3-renderpm python3-reportlab python3-reportlab-accel
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 735 kB of archives.
After this operation, 1024 B disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 libexpat1 amd64 2.4.7-1 [90.7 kB]
Get:2 http://archive.ubuntu.com/ubuntu jammy/main amd64 python3-renderpm amd64 3.6.8-1 [64.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu jammy/main amd64 python3-reportlab-accel amd64 3.6.8-1 [20.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 python3-reportlab all 3.6.8-1 [559 kB]
Fetched 735 kB in 10s (71.7 kB/s)                                              
(Reading database ... 248005 files and directories currently installed.)
Preparing to unpack .../libexpat1_2.4.7-1_amd64.deb ...
Unpacking libexpat1:amd64 (2.4.7-1) over (2.4.6-1) ...
Preparing to unpack .../python3-renderpm_3.6.8-1_amd64.deb ...
Unpacking python3-renderpm:amd64 (3.6.8-1) over (3.6.7-1ubuntu1) ...
Preparing to unpack .../python3-reportlab-accel_3.6.8-1_amd64.deb ...
Unpacking python3-reportlab-accel:amd64 (3.6.8-1) over (3.6.7-1ubuntu1) ...
Preparing to unpack .../python3-reportlab_3.6.8-1_all.deb ...
Unpacking python3-reportlab (3.6.8-1) over (3.6.7-1ubuntu1) ...
Setting up libexpat1:amd64 (2.4.7-1) ...
Setting up python3-renderpm:amd64 (3.6.8-1) ...
Setting up python3-reportlab-accel:amd64 (3.6.8-1) ...
Setting up python3-reportlab (3.6.8-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
ubuntu@ubuntu:~$
```

---

### Post by Joe_Linux on 2022-03-12
How do I mark this thread as solved ?

---

