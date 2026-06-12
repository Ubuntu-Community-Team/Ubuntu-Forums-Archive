---
title: "Install GUI on Ubuntu server 9.10 which is run in virtualbox"
date: 2010-01-22
forum: Server Platforms
---

### Post by vishwasahan on 2010-01-22
Hello this is my first post and i'm new to linux.
I installed ubuntu server 9.1 in virtualbox(running on windows 7) and it was successful.
Problem occurred when I try to install a gui.

first i tried using the commands> sudo apt-get update
sudo apt-get install ubuntu-desktop
then my kernel said

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package ubuntu-desktop
(I tried this when my ubuntu server 9.1 iso image mounted to the drive in virtualbox software)

Then i tried to enabled Universe and multiverse repositories using 
> sudo gedit /etc/apt/source.listbut it also failed since the gedit command is not working till i install gnome.

Can anyone help me on this. However i want to install a gui on my server which runs in virtualbox because um not familiar with, simple i cant do nothing with the tui.

Thanks.

---

### Post by chrisinspace on 2010-01-22
To edit your sources, you could use vi from the command line or install gedit using:

```
sudo apt-get install gedit
```

---

### Post by ICEB3AR on 2010-01-22
Is there a connection to the internet?

This is needed, because on the ubuntu-server iso there are not the packages of ubuntu-desktop.

---

### Post by vishwasahan on 2010-01-22
> **chrisinspace said:**
> To edit your sources, you could use vi from the command line or install gedit using:

```
sudo apt-get install gedit
```


Yeah sorry i couldnt mention i tried that too but again it displays 
"E: Couldn't find package ubuntu-desktop" message.

Is there anything wrong with the method i mounting the source disc(ubuntu-9.10-server-i386)? is there anything to do using the kernel to mount the disc?

---

### Post by vishwasahan on 2010-01-22
> **ICEB3AR said:**
> Is there a connection to the internet?

This is needed, because on the ubuntu-server iso there are not the packages of ubuntu-desktop.

yes machine is connected to the internet and i bridged my network adapter using virtualbox. and when i run ifconfig in the kernel it showed a proper ip address. but is there any way that i can make sure that my server running inside the virtualbox can connect to the internet?

---

### Post by ICEB3AR on 2010-01-22
you could try to ping google:

```
ping -c 5 google.de
```

---

### Post by vishwasahan on 2010-01-22
> **ICEB3AR said:**
> you could try to ping google:

```
ping -c 5 google.de
```


It says unknown host google.de... That means i done have access to the internet right?
so how can i configure ma internet access? i mean bridging is not enough?

---

### Post by ICEB3AR on 2010-01-22
right that means that you don't have a connection to the internet.

if i remember right you only should have to install the guest-additions of virtual box. look at the help of virtual box -> guest additions there is a good howto for linux and don't forget to run with sudo.

or have you done that already ?

---

### Post by vishwasahan on 2010-01-22
> **ICEB3AR said:**
> right that means that you don't have a connection to the internet.

if i remember right you only should have to install the guest-additions of virtual box. look at the help of virtual box -> guest additions there is a good howto for linux and don't forget to run with sudo.

or have you done that already ?


No i didnt do it yet.. I'll try and tell you the result. Thanx

---

### Post by vishwasahan on 2010-01-22
ok now i tried to install VBoxGuestAdditions in my linux. 
i tried the code sudo sh VBoxLinuxAdditions-x86.run  and got the reply sh: cant open VBoxLinuxAdditions-x86.run. So then i browsed my cdrom devices shown in the /media directory.[IMG]http://img709.imageshack.us/img709/6593/ubuntuk.jpg[/IMG]
seems to be the cd image dosen't mount properly right?
what can i do now? go like admin and create a niw dir in /media or /mnt and mount the virtual drive from /dev?

---

### Post by ICEB3AR on 2010-01-22
The board search also helps ;)
[http://ubuntuforums.org/showthread.php?t=426365]("http://ubuntuforums.org/showthread.php?t=426365")

To find the VBoxGuestAdditions.iso you could use that:
```
find / -type f -name VBoxGuestAdditions.iso
```

---

### Post by vishwasahan on 2010-01-22
ok now i have access to internet.
i logged in as root and mounted the cdrom using the command 
mount /dev/cdrom1 /media/cdrom
then i could see the cd image content inside of my /media/cdrom path.
i installed VBoxLinuxAdditions, and came and error that it cant find the X.org.
Anyway now i can mount an iso and have access to the internet.
But still no use of the commands "sudo apt-get update" or "apt-get install" commands. :(
it says couldn't find the package.
what can i do now to install a gui on my server runs in virtualbox (windows 7 host)?
thnx.

---

### Post by ICEB3AR on 2010-01-23
> i installed VBoxLinuxAdditions, and came and error that it cant find the X.org.
VIrtualBox expected that you have a gui running and tried to change the config file.

if you did the following with being connected to the internet:
```
sudo apt-get update
```
this command:
```
apt-cache search ubuntu-desktop
```
should give you list like that:
edubuntu-desktop - edubuntu desktop system
edubuntu-desktop-kde - edubuntu desktop system with KDE desktop
kubuntu-desktop - Kubuntu desktop system
ubuntu-desktop - The Ubuntu desktop system
xubuntu-desktop - Xubuntu desktop system

Now you decide for one of the you'ld like to install and type e.g.:
```
sudo apt-get install ubuntu-desktop
```

if the above list does have no entries then you have no internet-connection or maybe a wrong sources-list:
/etc/apt/sources.list

---

### Post by vishwasahan on 2010-01-23
that was the problem, i couldn't edit the sources.list file because there was no gnome and no gedit.
 then i tried using basic vi editor. you wont believe this and i don't know why my sources.list file was empty.then there was a file called sources.list~ (swap file i think) in the same directory and there was the the all content i wanted. First i tried uncommenting the lines in that sources.list~ file it didnt work.then i copy the content of the sources.list~ to source.list and it worked.downloaded 5hrs (512kbps) and installed ubuntu-desktop and just typed startx, now i'm in. anyway what I'm trying to do is to share internet through wifi with my mobile device.all i needed was a host.hope this will work.
 thanks so much ICEBEAR for your help. 
 I wrote all this because someone else might need this too.__

---

