---
title: "[SOLVED] Help install vmware on i386"
date: 2007-12-23
forum: Virtualisation
---

### Post by rickycodie on 2007-12-23
i  can't install vmware player-it says that i386 computers aren't supported?!!?!!?
something like 80% of computers are i386!! i have done some research on this but no headway seems to have been made since october. here's what i've found,
launchpad
[https://bugs.launchpad.net/ubuntu/gutsy/+source/vmware-player/+bug/151424](https://bugs.launchpad.net/ubuntu/gutsy/+source/vmware-player/+bug/151424)

here
[http://ubuntuforums.org/showthread.php?t=580035](http://ubuntuforums.org/showthread.php?t=580035)

is there any hope for me?

i will try the debian package and repost.
thanks in advance
ricky

---

### Post by rickycodie on 2007-12-23
so here's the update, the debian package was a no-go. it installs but then i can't find or run the program.

---

### Post by rickycodie on 2007-12-24
bump

---

### Post by Comhra on 2007-12-24
I have the same problem.  I get a message saying: ''VMWare cannot be installed on your computer type (i386).  Either the application requires special hardware features or the vendor decided not to support your computer type.''

Tried installing through Synaptic but it did not work properly.  The app wanted to update which I allowed but immediately it wanted to d/l the self same update again and so on.  I removed it after three attempts.  VirtualBox doesn't work for me in Ubuntu.  It keeps freezing even though a Beta version runs seemlessly on my MacBook.

Is there a workaround for this problem?  I'd dearly like a Virtual Machine in Ubuntu, mainly to try out other distros and the Alpha Version of Hardy.

---

### Post by Comhra on 2007-12-24
Looks like the VMWare package in Ubuntu repositories is broken.  No wonder it wouldn't work.  Is there a workaround?

---

### Post by fjgaude on 2007-12-24
Workaround, sure: get the package directly from the source: [http://vmware.com](http://vmware.com) and download and follow instructions to install... it's easy. Mostly automatic once you start.

---

### Post by Comhra on 2007-12-24
Downloading The RPM file.  Hope it works.  It's a bit like a window's .exe file, right?

---

### Post by fjgaude on 2007-12-24
> **Comhra said:**
> Downloading The RPM file.  Hope it works.  It's a bit like a window's .exe file, right?

From the site you get a binary of sorts, no RPM file for Ubuntu. Look at the upper right hand corner for VMware Server. Download that, the 1.0.4 version that is highlighted.

Follow instructions.

---

### Post by criskat777 on 2007-12-24
If it's a Virtual Machine that you want try Virtual box. Just go to it's web page there's a deb for Ubuntu just point and click. Be sure to install Guest additions after installing what ever OS you install.:)

---

### Post by Comhra on 2007-12-24
Couldn't open the .RPM File for VMWare, the Archive Manager doesn't support it.  I'll give VirtualBox a whirl.  Thanks for the help, guys.  Happy Christmas all.

---

### Post by rickycodie on 2007-12-24
i've got virtual box ans i love it, however i am installing osx on the machine and it doesn't work in virual box. so i need vmware. i will try the binary although in the past it hasn't worked for me.

---

### Post by rickycodie on 2007-12-24
ok so the instructions for installation are on the link below and must be followed to a t. 

go to page ten for installation instructions.

[http://www.vmware.com/support/pubs/player_pubs.html](http://www.vmware.com/support/pubs/player_pubs.html)

---

### Post by Shazaam on 2007-12-24
> **Comhra said:**
> Couldn't open the .RPM File for VMWare, the Archive Manager doesn't support it.  I'll give VirtualBox a whirl.  Thanks for the help, guys.  Happy Christmas all.

You need to install "alien" from the repos to open rpms.

---

