---
title: "Canno't Install Vmware Workstation 7 on Ubuntu 10.04"
date: 2010-06-11
forum: Virtualisation
---

### Post by bigboidomo on 2010-06-11
Hello.

I have ubuntu 10.04 i have been trying to intall the linux version of vmware workstation 7.1 but i keep getting 

root access is required for the operations you have chosen.

can someone please help me?

---

### Post by rhandsome on 2010-06-11
I'm trying to install it on 10.4 myself  but I'm getting a different error.  For you however, try "sudo sh ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle" or whatever flavor your trying to install. (commandline without quotes.)

---

### Post by bigboidomo on 2010-06-11
does this have to be in a certain location? noob to ubunu

---

### Post by bigboidomo on 2010-06-11
nevemind i got it to work thank you so much

---

### Post by bigboidomo on 2010-06-11
> **rhandsome said:**
> I'm trying to install it on 10.4 myself  but I'm getting a different error.  For you however, try "sudo sh ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle" or whatever flavor your trying to install. (commandline without quotes.)

Ok i have it installed, how do i enable 3d Graphics? so my virtual machine would turn on?

---

### Post by rhandsome on 2010-06-11
There should be a "Accelerate 3D Graphics" checkbox under the Virtual Machine Settings -> Display -> 3D Graphics section of your newly created Virtual Machine.

Question:  Did you install the i386 version or x86_64bit version of Workstation?

---

### Post by rajiv1096 on 2010-06-15
just wondering what you did to solve the problem because im having the same problem. it's giving me "you must have root access" message..

---

### Post by meoconvn38 on 2010-06-17
First can you type the command    "  ls - l " and try install :D

then post the errors here :D then we can try to help :confused:

---

### Post by dominosultan on 2010-07-21
> **rhandsome said:**
> I'm trying to install it on 10.4 myself  but I'm getting a different error.  For you however, try "sudo sh ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle" or whatever flavor your trying to install. (commandline without quotes.)

This solved it for me.  Thank you rhandsome!

---

### Post by morfioso on 2010-07-27
hi im an ubuntu noob and im  trying to install  vmware workstation 7.0.0-203739.i386.bundle and im getting the same root access required message graphically. ive tried all the above suggestions  and i keep getting the same error message
morfioso@ubuntu:~$ sudo sh ./VMware-Workstation-Full-7.0.0-203739.i386.bundle
sh: Can't open ./VMware-Workstation-Full-7.0.0-203739.i386.bundle
im using version 10.04 .pls help

---

### Post by edmac on 2010-08-31
Hello All,
 
I am a new to Ubuntu forum and also new to Ubuntu. I am in the process of installing vmware workstation 7.01 and am getting the same errors. I tried using the same installation options mentioned above. My error is 108: Syntax error: newline expected.  I am trying to install from download directory. Any and all help is greatly appreciated. Thank you in advance.

---

### Post by linh2t on 2010-08-31
You download the newest version in vmware website. It's work fine in ubuntu 10.04. 
Older version vmware can not install in ubuntu 10.04. I tried to install before it appeared the same error....

Good luck!

---

### Post by BenMitchell1979 on 2010-09-05
I'm getting the following error when attempting to install VMWare-Workstation-7.1.1-282343.bundle from Ubuntu 10.04. I'm running the following command "sudo sh "./VMware-Workstation-Full-7.1.1-282343.i386.bundle" and I get the following error message: "./VMware-Workstation-Full-7.1.1-282343.i386.bundle: 110: Syntax error: newline unexpected". 

I'm not sure if this some error in the latest build of VMware Workstation or not - I'm sort of a noob when it comes to *nix based operating system.

---

### Post by dcstar on 2010-09-06
> **BenMitchell1979 said:**
> I'm getting the following error when attempting to install VMWare-Workstation-7.1.1-282343.bundle from Ubuntu 10.04. I'm running the following command "sudo sh "./VMware-Workstation-Full-7.1.1-282343.i386.bundle" and I get the following error message: "./VMware-Workstation-Full-7.1.1-282343.i386.bundle: 110: Syntax error: newline unexpected". 

I'm not sure if this some error in the latest build of VMware Workstation or not - I'm sort of a noob when it comes to *nix based operating system.

Why are you using quotes in the command?

---

### Post by BenMitchell1979 on 2010-09-07
LOL - I didn't :) - The issue was that I was using the "Download Manager" to download the software from VMWare's website. You need to use the direct link vs the download manager.

---

### Post by savastux on 2010-11-22
You can download this patch and run it: [http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash](http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash)

After this, I was able to install VMware Workstation 7.1.2

(if you need a guide, you can use this one: [http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/](http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/) )

Hope this works for you.
Att,
Savastux

---

### Post by Quadunit404 on 2010-11-22
Um... Ubuntu 10.04 uses Linux 2.6.32 (although it is possible to get it running on Linux 2.6.35) :|

Unless the OP compiled Linux 2.6.35 on their Ubuntu 10.04 installation and uses that instead of Linux 2.6.32, that bash script isn't going to help much.

---

### Post by savastux on 2010-11-22
Sorry, my mistake.

I mixed things up here. I thought you were using Ubuntu 10.10

But as you said, you can use kernel 2.6.35

Att,
Savastux

---

