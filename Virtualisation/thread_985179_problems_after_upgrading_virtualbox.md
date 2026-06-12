---
title: "problems after upgrading virtualbox"
date: 2008-11-17
forum: Virtualisation
---

### Post by kaston on 2008-11-17
i recently just upgraded to hardy from gutsy and today i installed a virtualbox upgrade, which was something that gave me errors the last few times i tried.

after upgrading, i tried to run vbox and got the following error:

```
The VirtualBox support driver which is running is from a different
version of VirtualBox. You can correct this by stopping all running
instances of VirtualBox and reinstalling the software..
VBox status code: -11 (VERR_VERSION_MISMATCH).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

i reinstalled vbox using synaptic as recommended, but i still get the same error.  how can i fix this?

---

### Post by prshah on 2008-11-17
> **kaston said:**
> 
after upgrading, i tried to run vbox and got the following error:
```

VBox status code: -11 (VERR_VERSION_MISMATCH).
```

i reinstalled vbox using synaptic as recommended, but i still get the same error. 

a) Are you fully updated? ```
sudo apt-get update && sudo apt-get upgrade
``` will update information on available software and carry out upgrades to each if available.

b) Have you enabled any custom repositories for VirtualBox? Post your /etc/apt/sources.list file if you are uncertain.

c) Did you try stopping all VirtualBox services as suggested, before trying to re-install VirtualBox?

---

### Post by kaston on 2008-12-07
> **prshah said:**
> a) Are you fully updated? ```
sudo apt-get update && sudo apt-get upgrade
``` will update information on available software and carry out upgrades to each if available.

i ran your code but it did not upgrade anything so i assume i am fully upgraded.  by the way, i am running hardy heron.

> **prshah said:**
> 
b) Have you enabled any custom repositories for VirtualBox? Post your /etc/apt/sources.list file if you are uncertain.

i'm not sure.  here is my /etc/apt/sources.list file

```
## Uncomment the following two lines to fetch updated software from the network
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy restricted main universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-security restricted main universe #Added by software-properties

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-security universe


deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe #Added by software-properties

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-security main #Added by software-properties
deb http://packages.medibuntu.org/ gutsy free non-free
deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
```

> **prshah said:**
> c) Did you try stopping all VirtualBox services as suggested, before trying to re-install VirtualBox?

yes

---

### Post by kaston on 2008-12-08
can anyone help with this?  i really need to get vbox working so i can run autocad on it

---

### Post by roadmouse on 2008-12-08
I also had problems with VirtualBox after upgrading. Different errors, but ViertualBox would not start anymore.

After completely removing all VirtualBox components with synaptic (including preference files), and reinstalling them again, I could start VirtualBox again. But now it gives errors on a kernel driver.

You might wanty to backup your hidden VirtualBox folder from your home directory before removing your installation, since it also stores the virtual-drive images there. You don't want to loose those... ;)

---

### Post by kaston on 2008-12-08
there must be a fix to this.  i don't want kernel problems either.  ubuntu gurus?

---

### Post by spcwingo on 2008-12-08
Try installing the dkms package through synaptic and then reinstalling virtualbox.  After that reboot.  I can't guarantee that it will work for you, but it did for me.

---

### Post by kaston on 2008-12-09
> **spcwingo said:**
> Try installing the dkms package through synaptic and then reinstalling virtualbox.  After that reboot.  I can't guarantee that it will work for you, but it did for me.

didn't work.  any other suggestions?  this is getting pretty annoying...a mac is looking like a better alternative each day

---

### Post by kaston on 2008-12-10
tried posting this in the general help forum but didn't get any answers:

i recently just upgraded to hardy from gutsy and i installed a virtualbox upgrade, which was something that gave me errors the last few times i tried.

after upgrading, i tried to run vbox and got the following error:

```
The VirtualBox support driver which is running is from a different
version of VirtualBox. You can correct this by stopping all running
instances of VirtualBox and reinstalling the software..
VBox status code: -11 (VERR_VERSION_MISMATCH).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

i reinstalled vbox using synaptic as recommended, but i still get the same error.  i have also installed the dkms package through synaptic and then reinstalled virtualbox as recommended by someone, but that didn't work either.  how can i fix this?  i need to run vbox so i can run autocad for school, so this is pretty important

---

### Post by nhasian on 2008-12-10
may i suggest uninstalling the version you have now and then getting the latest deb file from

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Dedoimedo on 2008-12-10
Hello,
First, backup your configurations. Then, instead of reinstalling, remove (and purge) VirtualBox. Reboot for the safe measure and then install again.
Dedoimedo

---

### Post by kaston on 2008-12-10
if i uninstall my current vbox and then install the latest .deb from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) will i lose all of my data on my vbox drive?

---

### Post by kaston on 2008-12-10
anyone?

---

### Post by clb137 on 2008-12-10
HI,

yes you will lose ur data unless you back it up

clint

---

### Post by kaston on 2008-12-10
what directory do i need to backup to save my data?

---

### Post by iKonaK on 2008-12-10
Your settings along with the virtual volumes are in .VirtualBox in youre home directory.
All thou i'm pretty sure your settings will remain if you reinstall and install the latest .deb from their website you can backup for just in case; simply rename the folder and after the fun with instalation is over you can copy the settings and the volums back to the new .VirtualBox folder.
:p

---

### Post by kaston on 2008-12-10
seems to work but i had to reboot before i could find my new vbox in the applications menu.  why don't they tell you you have to reboot before running?  anyhoo, thanks for the help

---

### Post by iKonaK on 2008-12-10
For some reason the icon dosen't appear in the menu but if you choose to edit th menu you'll see, even before rebooting, that the icon is there, and checked, you just have to uncheck it and check it back....the application is working before the reboot :)

---

### Post by Dedoimedo on 2008-12-10
Whenever you install something that has drivers, it's not a bad practice to reboot, for meticulousness' sake.
Dedoimedo

---

### Post by kaston on 2008-12-10
interesting.  seems like a small bug that could be easily fixed.

---

### Post by bodhi.zazen on 2008-12-10
> **kaston said:**
> tried posting this in the general help forum but didn't get any answers:

First, please do not start multiple threads on the same topic, it causes confusion.

Second, please use the apropriate sub-forum. We have a forums specializing in virtualization.

Threads merged and moved.

---

### Post by kaston on 2008-12-10
so what do i do if i start a thread somewhere and noone answers it?  i guess i just shouldn't ever bring it up again?

sorry, i couldn't find the virtualization thread out of the 99 subforums available so i thought it was reasonable that it go under general help

---

### Post by bodhi.zazen on 2008-12-10
We have an unanswered posts team to address unanswered threads.

If you bump your thread, however, it is no longer unanswered.

If you start multiple threads it causes duplication of effort and confusion.

The general etiquette is to wait at least 24 hours before bumping your posts. Please keep in mind, this is a volunteer forum, and some questions are more difficult then others.

While you are waiting, may I suggest the search function or google ?

---

