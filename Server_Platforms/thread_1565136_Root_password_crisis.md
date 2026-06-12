---
title: "Root password crisis"
date: 2010-08-31
forum: Server Platforms
---

### Post by sixstringssteve on 2010-08-31
I have one of those ultra reliable Ubuntu servers in the corner that I never have to logon to becuase it never needs anything.  I needed to check up on it today and my root password would not work.  I am absolutly sure I did not forget my password and because I am the only Linux guy in the office I am sure some nimrod didn't get his fingers in the machine.
 
I attempted to enter GRUB recovery mode but when I hit ESC it says something about no disk and goes into the booting process.  I attempted to use a desktop version live CD, but the filestructure is unreadible, I assume due to the security of the server system.  Before I rebooted it the server worked fine, Apache and PHP were working away.  Now the whole thing is a 50Lb boat anchor.
 
How can I reset the password when I cannot enter GRUB menu or use a live CD?
 
This is getting a bit heavy.

---

### Post by Bachstelze on 2010-08-31
And I guess the person who set it up left the company? What does a

```
fdisk -l
```

on the Live CD give?

---

### Post by sixstringssteve on 2010-08-31
That is what is wierd...I set up the server.  I use the same root passwords for all my Linux boxes, this one just went dumb on me for some reason.
 
fdisk -l lists the partitions on /dev/sda1. The partition that has the filesystem is listed as a Linux LVM. I tried to mount it to a /media/ dir that I created but it says it is an unreadible filesystem, and says that the filesystem is LVM2_member. When I look at the properties of the dive it lists the 80GB drive with a 225MB filesystem.....which is not even close to correct.

---

### Post by sixstringssteve on 2010-08-31
OK, I had to install LVM2 so I could mount the partition. Once I mounted the partition and activated it I was able to access the Shadow file and reset the hash to the administrator password to blank.  This still did not work.  I have no idea why this machine all of a sudden does not want me to log on.

---

### Post by Bachstelze on 2010-08-31
You should never edit /etc/shadow directly. A blank hash does not do what you think. Assuming you mounted the root filesystem at /mnt, you must

```
sudo mount -t proc none /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt /bin/bash
```

And then you can use [font=monospace]passwd[/font] to reset the root password.

---

### Post by Ryan Dwyer on 2010-09-01
Ubuntu has the root account disabled by default, so the username is probably your name or something generic like sysadmin. If you go into a recovery console or boot from a live CD you can cat /etc/passwd and see what user has ID 1000 - that's your user.

---

### Post by sixstringssteve on 2010-09-01
OK, I recoverd the original Shadow file and I can checked the user with the ID 1000.  the user is 'administrator'....which I knew.  I can't seem to let it chroot so I can reset the password.  When I run chroot the respnse is that cannot run command '/bin/bash': No such file or directory.  The bash file is there becase I can see the darn thing.
 
I am not quite a noob, but I obviously don't have the experience you guys do....thank for the help.

---

### Post by Bachstelze on 2010-09-01
You seem to be very confused. You did set up the system, but don't know which account you should use for admin stuff...

For the "no such file or directory" problem, most probably the system is 32-bit and you are running a 64-bit Live CD.

---

### Post by sixstringssteve on 2010-09-02
I know what account to use, I'm not an idiot.  I am running a 32-bit OS and using a 32-bit Live CD.
 
All I need off this machine is a small MySQL database and I can dump the whole thing and reload.

---

### Post by de0xyrib0se on 2010-09-02
runlevel 1

---

### Post by Ryan Dwyer on 2010-09-03
Mount the partition and copy /var/lib/mysql to another drive if you can. When you restore it you'll need to chown it to mysql:mysql and chmod it recursively to 700.

---

### Post by Vishal Agarwal on 2010-09-03
Yesterday I was facing the root password problem. I am the only person accessing the server.
What I found is the right hand shift key has stopped working :p. 

While entered the password one by one characters it worked. Then and there I have changed it to some thing easy. ;)

FYI only.

---

