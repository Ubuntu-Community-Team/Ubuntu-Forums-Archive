---
title: "Help!!!! PLEASE!!!!!"
date: 2012-09-07
forum: Security
---

### Post by dan1239 on 2012-09-07
Please help me!!! I accidentally kind of set the other permissions in the File System folder to read write and all that other stuff but now I can't change it back!!! This is the error I get in the terminal when trying to use sudo 

daniel@DanielPC:~$ sudo
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
daniel@DanielPC:~$ 

I tried going back into nautilus and other programs but guess what I found out? You have to be STUPID SUDO TO DO THAT TOO!!! PLEASE HELP ME!!!!!!!!!!](*,)

---

### Post by cariboo on 2012-09-07
Your thread title isn't very helpful, it should t least have some information about your problem. That being said, could you tell us what command you used to create your problem. It would help us greatly in helping you solve your problem.

---

### Post by sandyd on 2012-09-07
Please post the output of
```

ls -l /usr/lib/sudo

```

The permissions on /usr/lib/sudo/sudoers.so should be 644 and owned by root

---

### Post by dan1239 on 2012-09-07
> **sandyd said:**
> Please post the output of
```

ls -l /usr/lib/sudo

```

The permissions on /usr/lib/sudo/sudoers.so should be 644 and owned by root
daniel@DanielPC:~$ ls -l /usr/lib/sudo
total 188
-rw-r--rw- 1 root root 177452 May 31 22:53 sudoers.so
-rw-r--rw- 1 root root   9440 May 31 22:53 sudo_noexec.so

---

### Post by dan1239 on 2012-09-07
> **cariboo907 said:**
> Your thread title isn't very helpful, it should t least have some information about your problem. That being said, could you tell us what command you used to create your problem. It would help us greatly in helping you solve your problem.
Sorry, and I didn't use a command I just was fiddling around and I saw that I could change the permissions for the folder in sudo nautilus and then I kind of had second thoughts and quit it, but unfortunately I didn't stop it in time for those files. Yes I know I shouldn't be messing around with things I don't know about, but I was just tired of having to go to Terminal, cd, sudo, and bladybladyblaahh. Please just help me!! I can't do anything. My Hotspot won't even work anymore!!!

---

### Post by claracc on 2012-09-07
Not knowing exactly what you have done to the folders permissions, please read : [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by dan1239 on 2012-09-07
> **claracc said:**
> Not knowing exactly what you have done to the folders permissions, please read : [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
Thanks, but that didn't work at all.

---

### Post by nothingspecial on 2012-09-07
If you've changed the permissions of every file and folder in your whole system then unfortunately you've broken it. :(

---

### Post by Stonecold1995 on 2012-09-07
Yes, if you changed too much it will be nearly impossible to recover, so you'll probably have to reinstall.  Backup your /home directory first if you have anything you want to keep.

There's nothing wrong with fiddling around if you're curious, but you should never do that on your computer unless you're willing to reinstall everything.  My advice would be to install Ubuntu in VirtualBox, then you can do all the experimenting you'd like.  Best of all, you can create a "snapshot" of the virtualized OS so if you make any mistakes, you can just go to the previous snapshot.  If for some reason you don't want to use VirtualBox, then install Ubuntu to a flash drive and boot from there, that way if you mess something up it won't affect your real install (although be careful because you can still wipe your whole drive or corrupt your filesystem from a USB stick, only VirtualBox can protect you from that).

Bottom line is, you probably fscked up your machine, you'll have to reinstall the OS.  And as always, be sure to keep regular full backups in case this kind of thing happens, which occur easily by mistake (for example, accidentally typing "sudo dd if=/dev/zero of=/ dev/sdb" instead of "sudo dd if=/dev/zero of=/dev/sdb" will erase everything on your computer, rather than erase your external drive like you intended).

Lastly, don't use sudo or su on anything unless you are absolutely sure what it'll do (commands like chmod, chown, mv, rm, dd, fsck, mkfs, etc can be REALLY dangerous if run as root).

*"To err is human... to really fsck up requires the root password."*

---

### Post by Ms. Daisy on 2012-09-08
> **Stonecold1995 said:**
> *"To err is human... to really fsck up requires the root password."*
Love it. So true.

---

