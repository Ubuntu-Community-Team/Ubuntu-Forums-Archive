---
title: "[SOLVED] Permissions In Ubuntu (Root and VirtualBox)"
date: 2007-12-20
forum: Virtualisation
---

### Post by Ian505 on 2007-12-20
I am still relatively new to Ubuntu and the permissions deal has kind of thrown me off...

I want to run XP in innotek VB but whenever I try to boot the .vdi I get a message to execute the following- which does okay.

```
ian@Electron-U:~$ sudo /etc/init.d/vboxdrv start
[sudo] password for ian:
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

```

Then I try again and it says that it doesnt have access to ./dev/vboxdrv which I assume is the emulation driver. I tried to run VB as SUDO for root privlages (because that's what the driver belonged to) but I didn't know where VB was installed!

I would like to know how to eliminate the /etc/init.d/vboxdrv start command and learn how to run a program as a root without having to edit any links in the top panel. (If possible.) I would also like to know what is executed (what the extension is) when you run a program in Ubuntu. (Just for bg info.)

Thanks a bunch!
Ian

---

### Post by wormser on 2007-12-20
Everybody gets this error.  You need to add your user name to the vboxusers group.  System> Administration> Users and Groups> Manage Groups> Highlight vboxusers> Properties> Check your user name.  I believe you will have to reboot for changes to take effect.  You should be able to run Virtualbox from Applications> System Tools> Virtualbox.  There is no need to run as root.

---

### Post by ayenack on 2007-12-20
Do this it should work.

System>Administration>Users and Groups

Once it opens click on Manage Groups and in there, there should be something like Virtual Box click it and add yourself to it. Then reboot and try starting Virtual Box.

To Late wormser beat me to it.

---

### Post by Ian505 on 2007-12-20
Okay I will try that... hang on. (I read your post right away, but I had to finish writing an email before I restarted.)

EDIT: Good news- it worked. And I didn't have to restart- just log out and back in! **THANK YOU BOTH!**

-Ian

---

### Post by ayenack on 2007-12-20
Glad you got it working Ian. Can you mark as solved. Top of page **Thread Tools>Mark as Solved** so others can gain from your experience.

Best of luck. ayenack.

---

