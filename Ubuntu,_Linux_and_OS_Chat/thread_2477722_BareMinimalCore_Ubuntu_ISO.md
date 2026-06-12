---
title: "Bare/Minimal/Core Ubuntu ISO"
date: 2022-08-04
forum: Ubuntu, Linux and OS Chat
---

### Post by jamesbrown2 on 2022-08-04
Well, the name "Core" now is used for the IoT Ubuntu project...so it is not "appropriate" in this context...

Is there anyone who has just a core/mini iso for Ubuntu?  Is nobody working on that?  Is there a script I can run after installing Server to strip all of the excess packages that I will never use on my netbook (e.g. cloud-init)?

I know that I am not the only one wondering about such a release, because I see tens of thousands of people searching for the Ubuntu mini ISO (in many languages).

Bless you all!

---

### Post by ajgreeny on 2022-08-04
You can still download the ***mini.iso*** for 20.04 from [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso) and I presume you could install that and upgrade to 22.04 when the version upgrade is offered, which I think should be soon.  The 20.04 is the latest version available to download as the previously downloadable minimal.iso is no longer created or available.

That iso will install the very bare minimum OS without any GUI but you will be able to add all the packages you might want that are in the standard repos.
You will, of course, need to install xorg packages, a window manager and for ease of startup a display manager.
Then you can add whatever you want from the available GUI packages normally in Ubuntu or any of the other DE versions, such as an office suite, media player, browser and email application if you want.

EDIT:
You may find the thread discussing this in much more detail at [https://ubuntuforums.org/showthread.php?t=2449474&highlight=minimal.iso](https://ubuntuforums.org/showthread.php?t=2449474&highlight=minimal.iso) more useful than my limited knowledge of the situation.

---

### Post by grahammechanical on 2022-08-04
If I remember correctly the Installation process of Ubuntu 22.04 offers a Normal Installation or a Minimal Installation. In fact it is part of the installation guide for Ubuntu 22.04 Desktop. See the picture. I have never tried this option myself.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)

Regards

---

### Post by TheFu on 2022-08-05
The minimal install for Ubuntu Server really isn't minimal. It is still extremely bloated, just without things like tab-completion included. I think the disk savings are closer to 100MB, not much at all.

---

### Post by mechanic on 2023-01-18
Yes, I've been looking for a minimum install of standard Ubuntu, in the end settling for a mini.iso of the 2012 release, and upgrading twice to the current LTS version (22.04.01 or whatever it's called). I see on the OMGUbuntu blog that new installers offer a minimum install as one of the choices during installation. I was going to check this route until I found that the current download for this LTS is 4GB! This seems to be the case because the idea is to go for a big install and cutback later, rather than trim the download to the minimum at an early stage. I also tried going the net/server offering as a way to get to a text system, but that is quite a complex and time-consuming download process.

4GB - can you believe that in 2018 and with squashed file downloads we need that much file space? It wasn't long ago that we could get working download installers on a CD (700MB or so). Where did it all go wrong?

---

### Post by ian-weisser on 2023-01-21
It goes back to what people want by "Ubuntu" and what they want with "minimal".

A lot of folks seem to use "Ubuntu" as a shorthand ways of saying "a version of Linux that I don't need to re-learn"

A true "minimal" version of Ubuntu has never been supported, as that usually conflicts with some of the features that define Ubuntu. Ubuntu's attraction to many is that it's a popular OS that appeals to both new/unskilled  users (safe and sane defaults, curated general-purpose desktop, testing,  community) and enterprises (Debian-based, consistent release cycles,  security patches).

For true "minimal Ubuntu", go with Debian Netinstall. It's a version of Linux that Ubuntu-familiar folks don't need to re-learn. It's REAL 'minimal'. And participate in the Debian community. Ubuntu benefits directly from a strong Debian community.

---

### Post by tea for one on 2023-01-21
Not strictly Ubuntu but this info may help.
I have used both 20.04 and currently 22.04 from here:-
[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

Also, it seems that Xubuntu want to offer an official version soon.
[https://www.omgubuntu.co.uk/2023/01/xubuntu-23-04-will-come-in-a-cd-rom-size-minimal-image](https://www.omgubuntu.co.uk/2023/01/xubuntu-23-04-will-come-in-a-cd-rom-size-minimal-image)
Comment from the Xubuntu Technical Lead in the discussion.

---

### Post by mechanic on 2023-01-21
Install: min Xubuntu 18.04 (Beaver), root partition 3.9GBytes.

 Updated LTS twice, now 22.04.1 (Jellyfish): root partition - 6.3 GBytes. There's the problem, right there!

Further update - 23.04 core, early download on a VM,
Root partition - 9.3 GBytes.

What? Who voted for this explosion in user space?

Increasing the amount of space needed implies similar increases in the amount of source code for the distros. More source means more bugs! If there were a way to keep the earlier versions up, and expend all this (or most) developer effort in bug hunting and removal we'd have more reliable systems with better performance! Why not? Ubuntu 18.04 was a pretty good base system!

Come to think of it, pretty simple systems got us to the moon!

---

### Post by wunschtaria on 2023-06-09
What? Who approved of this user space explosion?


Expanding the required storage space entails expanding the amount of source code for the distros as well. Bugs multiply as source increases! We'd have more dependable systems with higher performance if there was a method to maintain the older versions and devote all (or most) developer time to finding and fixing bugs. Exactly why not? The basic system, Ubuntu 18.04, was pretty decent.

---

### Post by donald187 on 2023-06-10
> **ian-weisser said:**
> 
For true "minimal Ubuntu", go with Debian Netinstall. It's a version of Linux that Ubuntu-familiar folks don't need to re-learn. It's REAL 'minimal'. And participate in the Debian community. Ubuntu benefits directly from a strong Debian community.

jamesbrown2, if you choose this path I believe that at the install software page (or whatever it's called) you have to uncheck Debian Desktop Environment and Gnome Desktop.  That should give you a prompt after installation where you can install the basic stuff like xorg and other stuff.  Otherwise you will get the Gnome desktop with lots of "extra stuff".  

Disclaimer:  I have not done this but this is what has been advised on forums.debian.net when similar questions are asked.  Ask there before attempting this.  For heaven's sake, don't take my word for it lol.  I have installed from the minimal cd...

[https://www.debian.org/CD/netinst/](https://www.debian.org/CD/netinst/)

...but always have left the Debian Desktop Environment and Gnome Desktop checked (the defaults).

---

