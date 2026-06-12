---
title: "Ltsp server instantly shuts off computer on login after power outage."
date: 2010-08-06
forum: Server Platforms
---

### Post by jeight on 2010-08-06
I have a Edubuntu Ltsp server installed. Just recently there was a power outage and now when I try to login the computer suddenly shuts off. I tried switching the power unit, taking out most of the ram, and even switched the HD over to another computer but the problem still persists. I have a backup on my /home but I can't keep the system on long enough to restore. My next attempt will be to log into the bash shell and try to access the restore file from there. The problem is that my /home is encrypted so...? If anyone knows of a better solution please let me know.

----
Okay..*sigh* ... Couldn't run bash commands cause computer shuts off to soon. I can't mount drive on another computer because it is encrypted with SElinux. Can't mount off of live CD because of the same reason. Is there any way to fix this without reinstalling the server.?

----
Got mounted and into the shell using the rescue on the alternate cd and preformed -
sudo apt-get update
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade

that didn't work so I tried to mount my /home dir to access my backintime restore file but it's encrypted and wouldn't mount. Next try I'm going to apt-get install gnome-deskop.. if that doesn't work I'll try apt-get remove gnome-desktop and then try reinstalling?????

----
deleted /opt/ltsp/i386 and then rebuild the client. Deleted both guvcview and ltsp-controlaula from the chroot and system finally booted up.

---

### Post by Spockers on 2010-08-23
I had the same issue.
My LTSP Edubuntu would shut down straight after login after upgrading the system to 2.6.32-24-generic.  
So tried your solution starting with your last suggestion of removing Controlaula. It was Controlaula.

I got in by selecting recovery mode option in grub bootloader.
then selected lo graphics mode & restart X options.
I removed Controlaula via synaptic package manager & re started the computer.
All works now.
Thanks for your input.  Is this a bug, or just bad circumstance?

---

