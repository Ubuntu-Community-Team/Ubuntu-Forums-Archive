---
title: "Confused on how to change authorities."
date: 2009-03-11
forum: Security
---

### Post by joemilx on 2009-03-11
I am running 8.10 64-bit with current updates.  A week or so ago, I changed from a wired to a wireless environment using a D-Link DWA-1320 adapter.   All went well or so I thought.  

From that point forward, I always get a request to enter my password before the wireless will connect.  Also, I cannot get the GEDIT editor to work any more.  For example, if I request ""gksudo gedit /boot/grub/menu.lst", I get a two minute pause followed by an error that suggests I don't have authority to access that data.  

I suspect my authorities have been altered, but I'm not sure where to start to correct this.

---

### Post by hacker07.gbh on 2009-03-11
Okay I Might be able to help you. Try this: open up your root terminal. then type gedit /boot/grub/menu.lst or press alt F2 then type gksu gedit /boot/grub/menu.lst if none of that helps you can reply back or email me at [email]hacker07@greenbookhackers.com[/email]

---

### Post by joemilx on 2009-03-12
Tried your suggestions before I started this thread.  Then tried again after your response.  I get an error popup that says "menu.lst(boot/grub) is not responding".

---

### Post by hacker07.gbh on 2009-03-12
Okay try this:

Open a shell (Terminal)

Type the following to re-configure GRUB

sudo grub 

Type the following followed by the TAB key

root (hd

This will provide you with a list of possible physical drives eg:

hd0 or hd1

Type the number of the drive you installed ubuntu on, not to worry if you unsure, the next step with tell you if you on the right path. Add a ‘,‘ after the number and press the TAB key again:

root (hd0, 

You will see something similar to the following:

grub> root (hd0,
Possible partitions are:
Partition num: 0, Filesystem type unknown, partition type 0×7
Partition num: 2, Filesystem type is ext2fs, partition type 0×83
Partition num: 4, Filesystem type unknown, partition type 0×7
Partition num: 5, Filesystem type is fat, partition type 0xb
Partition num: 6, Filesystem type is fat, partition type 0xb
Partition num: 7, Filesystem type unknown, partition type 0×82


Notice the ext2fs partition, this is the one Ubuntu is installed for the above example. I would therefore type:

root (hd0,2)

Now type the following, replacing hd0 with the physical drive Ubuntu is installed

setup (hd0)

Close the terminal, reboot and enjoy your restored GRUB loader. Please respond back and tell me how it goes. :):popcorn:

---

### Post by joemilx on 2009-03-14
Let's start this over.  My problem is not with grub per se.  I cannot get GEDIT to work properly when I sign on as root.  I have the the same problem if I try to edit /etc/X11/xorg.conf.  I can list the text files using GEDIT, but I get the error message whenever I use GEDIT as root.  I can look, but I cannot update the files.

---

### Post by hacker07.gbh on 2009-03-19
> **joemilx said:**
> Let's start this over.  My problem is not with grub per se.  I cannot get GEDIT to work properly when I sign on as root.  I have the the same problem if I try to edit /etc/X11/xorg.conf.  I can list the text files using GEDIT, but I get the error message whenever I use GEDIT as root.  I can look, but I cannot update the files.
Okay man first of all you could try to reboot ubuntu if dont have any important data. Or you just might have rootkit. input this in your terminal sudo apt-get install rkhunter

---

### Post by joemilx on 2009-03-28
Resolved after finding a fix on another thread. The system had automatically required password entrys after the 8.10 install.  I turned it off in Applications,Accesories, Passwords and Encryption Keys.

---

