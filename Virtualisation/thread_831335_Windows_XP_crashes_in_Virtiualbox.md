---
title: "Windows XP crashes in Virtiualbox"
date: 2008-06-16
forum: Virtualisation
---

### Post by ShelJ on 2008-06-16
Since my last update, last week, Windows XP crashes when ever I try to access my shared folder in Virtualbox.  Whenever I try to access my shared folder, I get a bluescreen for a split second and Win XP restarts.  At first I thought that this might be a problem with my permissions, but everything checks out there.  I cannot open my shared network folder, which is my Desktop, but I get this crash.  I've been using Win XP on Virtualbox for a few months now, as I need it for AutoCAD, and this is the first time that this has been a problem, as a result I cannot access any of my AutoCAD files to do any work at home, and I'm facing deadlines.  ](*,)

If you can suggest anything please help.  I'd rather not have to reinstall Win XP on Virtualbox, or I will lose some work.

---

### Post by yaknowwat on 2008-06-16
II suggest if you haven't to update to virtualbox 1.6.x unfortunately it is not in the repo's but this topic helps with that quite nicely.

[http://ubuntuforums.org/showthread.php?t=817523](http://ubuntuforums.org/showthread.php?t=817523)

Then uninstall the virtualbox guest additions in the xp virtual machine reboot the virtual machine and install the newer ones you'll have to reboot the windows virtual machine again after that

---

### Post by ShelJ on 2008-06-17
Thanks for the redirection, however when I try this (I have before as well) I get the following Error:```
 * No suitable module for running kernel found
```

When I look in the /var/log/vbox-install.log I get "Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop."

I tried to correct this on my own, but I think Ill need a walk through to correct this, so that I don't screw up my system.

---

### Post by ShelJ on 2008-06-17
Alright I got it working, however I had to use the following cmd: 
```
 sudo aptitude install linux-headers-$(uname -r)
``` 
then 
```
sudo /etc/init.d/vboxdrv setup
``` (just in case someone else runs into this problem) 

It worked once, but now I get the Windows Error, "\\VBOXSVR\Desktop is not accessible. You might not have permission to use this network resource.  ...  The network location cannot be reached."  However, I have permissions according to the VirtualBox settings (Access: FULL) and Users and Groups settings (vboxusers: ShelJ)

Finally, I just noticed that I misspelled VirtualBox in the title of this thread.  Curse you clumsy fingers!!!

---

### Post by bodhi.zazen on 2008-06-17
IMO it is much much easier to use a "standard' network share protocol.

Samba, FTP, HTTP, ssh (scp) etc.

If you *must* use network shares take a look at re-installing the virtualbox tools.

---

### Post by ShelJ on 2008-06-17
I just need to transfer files to and from my Desktop. Will what you sugg work, and how do I set it up?

---

### Post by bodhi.zazen on 2008-06-17
IMO samba is easiest to set up and is for the most part working "out of the box".

Samba is the same protocol for sharing in windows.

Boot your windows guest, share a directory.

Mount the share on Ubunutu -> you can drag and drop files from the GUI.

[uwiki]SettingUpSamba[/uwiki]

---

