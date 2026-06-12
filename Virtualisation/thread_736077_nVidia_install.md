---
title: "nVidia install"
date: 2008-03-26
forum: Virtualisation
---

### Post by LunaSanctus on 2008-03-26
hi

I'm new in Linux and I wanted to install the nVidia drivers. I downloaded the kit in the desktop folder as nVidia.run and in the terminal window I run sh nVidia.run (after i changed to de destop dir). Here I get a message that I should log in as root and run the program.

Can anyone help me. How can I login as root? what password should I use? I changed the password for the rood user in the users and groups to 123456, after that I restarted and tryed to login as root, but I got another message (administrator can't log here or something like that).

---

### Post by revenant138 on 2008-03-26
I think you can do this a different way - 

Ctrl+Alt+F6 (i think f6 at least) to switch to non-gui mode. Then kill your graphics manager 

GDM:
sudo /etc/init.d/gdm stop

KDE: 
only way i know how to do it is killall -9 X (this is kind of harsh way to stop it, anyone else have a better way?)

then run the script as sudo

---

### Post by Pumalite on 2008-03-26
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
password
sudo sh /path/to/driver/NVIDIA-Linux-xxxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg file
Then: startx
You need build-essential installed:
sudo aptitude install build-essential
(before attempting to install the driver)

---

### Post by revenant138 on 2008-03-26
Won't ctrl+alt+F1 try to make them login as root? i was trying to get around that since they were having problems?

---

### Post by Pumalite on 2008-03-26
Ctrl+Alt+F1 takes him to a virtual Terminal that will ask him to login with his username and password

---

### Post by revenant138 on 2008-03-26
I thought that was as root though, and they dont have a root pwd. 

Im at work so i cant check it ;) no biggie

---

### Post by LunaSanctus on 2008-03-26
I trye Ctrl+Alt+F1 no luck there
I'm running VMWare Workstation under Win Vista, my virtual machine is Ubuntu 7.0 Desktop Edition....

is there another way to disable the graphics manager?

---

### Post by PmDematagoda on 2008-03-26
Unfortunately I do not think you can install the Nvidia driver anyway since, as Ubuntu is being virtualised, the graphics adapter would not be hardware but more software. So this means that the graphics driver is considered to be "generic" by the system being virtualised, this also would mean that the Nvidia driver would not start at all since it requires an Nvidia VGA card to be installed.

This thread is moved to the Virtualisation section.

---

### Post by fjgaude on 2008-03-26
> **LunaSanctus said:**
> I trye Ctrl+Alt+F1 no luck there
I'm running VMWare Workstation under Win Vista, my virtual machine is Ubuntu 7.0 Desktop Edition....

is there another way to disable the graphics manager?

Oh, you cannot install video drivers in virtual Windows, period. One of these days, maybe.

If you have installed the Tools, setup to recognize USBs, etc., the video will be fast as it is in the host, but only 2D, no 3D acceleration.

---

