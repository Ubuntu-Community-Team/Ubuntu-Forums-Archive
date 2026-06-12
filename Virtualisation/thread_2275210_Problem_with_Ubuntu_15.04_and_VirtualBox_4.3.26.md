---
title: "Problem with Ubuntu 15.04 and VirtualBox 4.3.26"
date: 2015-04-24
forum: Virtualisation
---

### Post by resanders2 on 2015-04-24
During all my past installations of VirtualBox on my Ubuntu machine, I have located the virtual machines on a second drive in the system.  There has never been any problem with that.  With the upgrade to Ubuntu 15.04, my virtual Windows 7 crashes and forces the entire system to have to be cold booted.  I have "solved" this problem by moving my virtual Windows 7 to the same drive where Ubuntu is installed.  Everything works as it should. There are no crashes. I really wish, however, to have all my virtual machines on the second drive rather than the smaller main drive. Does anyone have any idea why this is happening?

---

### Post by jamesmorcos-gmail on 2015-05-28
I have a similar problem. I have a 1TB HDD that I mount as /home. My virtualbox VMs live there. The rest of my file system is on a 128MB SSD. I've been operating just fine in this configuration since Ubuntu 12.04. After installing 15.04, I've noticed a lot more HDD clicking and the IDE indicator in virtualbox is almost always blinking. The tiniest action in my Win7 VM (like clicking on a menu, for instance) leads to a 5-10 second delay before I get a response. I really don't want to move my VM to the SSD, as the .vdi is greater than 50GB in size.

---

