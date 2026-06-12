---
title: "Ubuntu 10.04 cannot execute binary file"
date: 2010-12-22
forum: Server Platforms
---

### Post by fast_eddie on 2010-12-22
Hi,

Trying to install Parallels Plesk Panel 10 x86_64 onto a completely new installation of Ubuntu 10.04.1 LTS

root@server:~# chmod +x parallels_installer_v3.7.1_build101014.17_os_Ubuntu_10.04_x86_64
root@server:~# ./parallels_installer_v3.7.1_build101014.17_os_Ubuntu_10.04_x86_64
-bash: ./p.arallels_installer_v3.7.1_build101014.17_os_Ubuntu_10.04_x86_64: cannot execute binary file

Any suggestions?

Many thanks, Ed

---

### Post by windependence on 2010-12-22
Take the period out of your command:
 
./[COLOR=red]**p.arallels**[/COLOR]_installer_v3.7.1_build101014.17_os_Ubun tu_10.04_x86_64: cannot execute binary file
 
-Tim

---

### Post by fast_eddie on 2010-12-22
Hi

What you had picked up on was actually the repsonse to the request.
The request was formated:~#  ./parallels_installer-----10.04_x86_64

Are there any parameters that I should check to ensure the file can be executed in root?

Regards, Ed

---

### Post by brettg on 2010-12-22
I would look at the binary file. It sounds to me like it is an incomplete download

---

### Post by fast_eddie on 2010-12-23
Brett

Many thanks for that, it was indeed an incomplete file.  However, its still reporting that the file cannot be executed:
-bash: ./parallels_installer_v3.7.1_build101014.17_os_Ubuntu_10.04_x86_64: [COLOR=Red]cannot execute binary file[/COLOR]

I'm logged in as root, but I thought that it might be that I'm trying to run the file from a wrong directory or that the fstab file had noexec? So I removed the only noexec option listed from /proc and rebooted, but  still no joy!

The binary file is compiled for Ubuntu 10.04 but I noticed that the version that's running is Ubuntu 10.04.1 LTS
Could that be my problem?

---

### Post by fast_eddie on 2010-12-23
Hey

Got it working, when the hosting guys rebuilt the VDS with Ubuntu 10.04 they specified 32-bit instead of the requested 64-bit!!

Thanks for your help with this, I was running out of ideas!

---

