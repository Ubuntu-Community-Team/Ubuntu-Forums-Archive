---
title: "VB file share; Ubuntu 10.04 64bit as guest on Mac host"
date: 2010-03-27
forum: Virtualisation
---

### Post by GARoss on 2010-03-27
Using VirtualBox 3.1.6 on Mac host (OS X 10.6.2), with Ubuntu 10.04 64bit beta guest.

Previously I was able to connect a shared folder by editing fstab in Kubuntu 9.10-64bit but something is different in Ubuntu 10.04 64bit that prohibits this. So, I'm trying a different method found @ the VB website here: 

[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

My host shared folder is [COLOR="Red"]VB_Mac_Share[/COLOR] & the shared folder in the guest, Ubuntu 10.04 is [COLOR="Blue"]Community[/COLOR]. Typing this in the terminal... 

*sudo mount -t vboxsf [COLOR="Red"]VB_Mac_Share[/COLOR] ~/[COLOR="Blue"]Community[/COLOR]*

...will mount the folder. But, when trying to change the ownership & mount it automatically, as stated in the tutorial, I get Invalid argument errors...

[I]george@george-desktop:~$ sudo mount -t vboxsf -o uid=1000,gid=1000 VB_Mac_Share ~/Community
/sbin/mount.vboxsf: mounting failed with the error: Invalid argument
george@george-desktop:~$ sudo mount -t vboxsf VB_Mac_Share /home/george/Community
/sbin/mount.vboxsf: mounting failed with the error: Invalid argument
george@george-desktop:~$[/I]

How can this be fixed?

---

### Post by GARoss on 2010-03-29
Anyone?

---

### Post by mscf on 2010-04-28
Hey, not sure if you are still having this issue, but I ran into the same thing on a Windows 7 host. 

After playing around a little and doing some reading, I started to think that with the improvements to the boot speeds on 10.04 it might be trying to mount the host folder before the virtualbox drivers are properly loaded.

Anyway, I managed to make it work on my system by following the instrucions at [https://help.ubuntu.com/community/RcLocalHowto]("https://help.ubuntu.com/community/RcLocalHowto") to create a /etc/init.d/local file. then I added this line: mount.vboxsf -w HOST_FOLDER /MOUNT_POINT

Don't know if you got this worked out on your own already, or if this will solve your issues, but it helped me.

---

