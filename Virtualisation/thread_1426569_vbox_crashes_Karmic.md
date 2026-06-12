---
title: "vbox crashes Karmic?"
date: 2010-03-10
forum: Virtualisation
---

### Post by Bill D on 2010-03-10
Hello, 
I am attempting to install/run a Windoze 7 x64 guest from virtualbox PUEL (AMD64) with an Ubuntu 9.10 x64 host. I went to startup the virtual machine for the first time and pressed f12 to select the boot device (64 bit Windows 7 ultimate iso) and the whole computer crashes and shuts down.

---

### Post by Exca on 2010-03-10
Hello, is there some logs for VirtualBox you can show us ? (/var/log/)
I'm not a VirtualBox user, maybe it can allows other people to help you ;-)

---

### Post by Bill D on 2010-03-10
I'm fairly new to the whole Ubuntu concept. How do I go about generating a log file, and how do I save it so I can upload it here as an attachment?

---

### Post by Exca on 2010-03-11
Usually, logs are automaticly generated in /var/log for each daemon or software running on your Ubuntu.

To copy/paste them on this forum:
1. Connect in ssh to your server (if you haven't any graphical access to the website) => ssh user_login@ip_adress
2. Go to your /var/log folder (with the terminal) and find your VirtualBox folder
3. Find the latest log with a ls -al (you'll see the last update time)
4. Type more my_log_name.log, it will show you the content of the file
5. Then, copy/paste it on the forum with two beautifull [ CODE ] and [ / CODE ] tags ;)

Just, analyse it yourself before posting all the log, maybe there is a lot of useless things. Try to find the date and time when your machine have crashed !

---

### Post by Bill D on 2010-03-11
There is no VirtualBox folder inside of /var/log :confused:

---

### Post by Exca on 2010-03-11
Try in **/home/your_user_name/.VirtualBox**, it's an hidden forlder in your home directory.
I've seen on another post that it must be there, but I cannot check that, maybe VirtualBox users can confirm that ? Someone ?

---

### Post by Bill D on 2010-03-12
I found the log file, but it is completely empty

---

### Post by Exca on 2010-03-12
> **Bill D said:**
> I went to startup the virtual machine for the first time and pressed f12 to select the boot device (...)
 
I don't understand this part of your installation step. I've seen this tuto about the Win seven installation on Virtual Box, maybe it can helps;
 
[http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/](http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/)
 
Is there any user interface like this one, where you can select the media source of your virtual CD/DVD drive ?

---

### Post by Bill D on 2010-03-12
There is, I have the .iso on my desktop, it loads the "BIOS" and I press F12 to select boot device, and that is when the computer crashes

---

### Post by alphasoup on 2010-03-13
Assuming you are using Vbox 3.1.2 or 3.1.4 installed from the Virtual Box site.
Why not let the MBR boot directly (without selecting F12), presumably the CD ROM drive is on the bootable device list and will be selected automatically and you can begin installation. Then be patient I find Virtual Box sluggish on Duo 2GHz with 2.5G, I have had to wait a half hour to get a system to come-up the first time :(, then it picks some speed with the Virtual Box tools installed.

add: Device -> CD ROM drive -> x (check mark it so it is available to boot from)

---

