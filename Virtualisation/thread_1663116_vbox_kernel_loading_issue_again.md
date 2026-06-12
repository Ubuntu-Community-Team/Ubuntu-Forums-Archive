---
title: "vbox kernel loading issue again"
date: 2011-01-09
forum: Virtualisation
---

### Post by sdowney717 on 2011-01-09
Ok, I forget again but why is it not loaded?
what hoops to run thru?
thanks

---

### Post by sdowney717 on 2011-01-09
solved again
but does this have to be run after every boot?
and they need to fix the error message to use
vboxdrv.dpkg-dist setup


> scott@scott-desktop:~$ sudo /etc/init.d/vboxdrv.dpkg-dist setup
[sudo] password for scott: 
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.
scott@scott-desktop:~$ 


---

### Post by CharlesA on 2011-01-09
Do you have DKMS installed?

It sounds like it's not loading the kernel module automagically.

---

### Post by junkboxy on 2011-01-09
Agreed CharlesA, you gotta make sure DKMS is loading
 
[COLOR=black]apt-get install dkms[/COLOR]
 
then rerun setup for your flavor of Vbox.
 
/etc/init.d/vboxdrv setup

---

### Post by sdowney717 on 2011-01-09
already installed.
so why does this happen to me?

> scott@scott-desktop:~$ sudo apt-get install dkms
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
The following package was automatically installed and is no longer required:
  libenet0debian1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scott@scott-desktop:~$ 


---

### Post by CharlesA on 2011-01-09
Not sure. It's like the vbox kernel modules aren't loading on startup.

---

### Post by sdowney717 on 2011-01-09
some time ago, I recall the kvm module could not load with vm or vbox?
seem to recall having to do something special. one had to be in and the other out, All I do is upgrade Ubuntu versions, could some config file be the cause?

---

### Post by CharlesA on 2011-01-09
Could be, but I don't have any idea where to even look. Maybe check lsmod?

---

### Post by rpete on 2011-02-06
I have tried purging dkms and reinstalling it.  I have made sure build-essential is updated.  For both of those, I cannot complete the update because I get a message that the oss4-dkms and blcr parts of dkms are not working.  

I used changed directory to the init.d and then from init.d$ ran the command sudo ./vboxdrv.dpkg-bak setup   This temporarily fixed the problem but on reboot I got the message that blcr and oss4 are bad. 

Any other ideas?

---

