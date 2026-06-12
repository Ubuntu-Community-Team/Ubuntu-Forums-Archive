---
title: "Problem installing Feisty"
date: 2007-08-06
forum: System76 Support
---

### Post by wj18 on 2007-08-06
I recently tried to make the move from edgy to feisty, and I ran into a couple of problems.  I started by following the normal steps:

[INDENT]
1) Edit the /etc/apt/source.list file, replacing all instances of "edgy" with "feisty"

2) sudo apt-get update

3) sudo apt-get dist-upgrade
[/INDENT]

However, after the update, there were two files missing, I don't remember the file names exactly (they were files 53 and 54).  I thought "meh, maybe it's a fluke and I can update later."  That didn't work, and feisty was not working at all.  So I decided I would download the 7.04 update onto a disk and reinstall feisty from the disk.  I burned the iso image to the disk, and booted up the notebook.  It seemed to start working, the Ubuntu loading screen appeared (this is after I had chosen to boot from the disk); then an error message popped up:

[INDENT]
"BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [this is my terminal]"
[/INDENT]

I couldn't do anything in the built-in shell.  I could browse some files, I couldn't even find /etc/inittab to see what was wrong.

After this happened I thought, "well, I'll just boot normally and see what's up."  Sadly, I couldn't boot normally, it brought up the same error.  It brought up the same error when I tried booting in recovery mode too.  Is there any way I can get feisty on my System76 S62FP Notebook?  Right now I have nothing, I can't do anything, except sit here, of course (I'm writing this on a different computer).

---

### Post by jimrz on 2007-08-06
had the same problem with one of my boxes...have a look at [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474693&highlight=BusyBox+v1.1.1") thread that helped me to get around it.

---

### Post by palintheus on 2007-08-07
What worked for me was:

hitting escape and entering grub, then removing any instance of 'quiet' and 'splash'  then pressing 'b' to boot

when it boots to that prompt type, in order
break=top
modprobe piix
exit

It will then boot without the nice splash screen, but should get you to the login screen and after a reboot your splash screen will return.

---

### Post by thomasaaron on 2007-08-07
You might try installing from the alternate CD.

---

### Post by palintheus on 2007-08-07
> **thomasaaron said:**
> You might try installing from the alternate CD.

This worked for me, but when I rebooted I was stuck at the same screen. and thats when I had to enter the commands in my about post.

---

