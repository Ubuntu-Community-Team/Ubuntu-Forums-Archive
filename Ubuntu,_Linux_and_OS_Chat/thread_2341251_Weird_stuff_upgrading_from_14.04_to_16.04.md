---
title: "Weird stuff upgrading from 14.04 to 16.04"
date: 2016-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by dvisockas on 2016-10-26
Hey,

Few days ago I decided to upgrade to 16.04 but after the install finished my GRUB menu didn't show Ubuntu. After about 8 hours I managed to find a problem which was that the kernel was missing for some reason. I reinstalled the kernel, booted back into my old 14.04 Ubuntu and.... There was no GUI.
So I reinstalled ubuntu-desktop and other packages that could've been responsible for the missing-GUI thingy. 

The problem now is that I am missing some parts of the UI (Shutdown/sys settings menu in the top bar), I can't reenable my old theme since Unity tweak tool throws an exception "The following schema is missing".

I tried running the update again, using sudo do-release-upgrade, but it throws:

An unresolvable problem occurred while calculating the upgrade. 


```
This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

```

Tried searching for solutions, but nothing worked.

```
 grep Broken /var/log/dist-upgrade/apt.log

```
Has 106 lines: [https://gist.github.com/dvisockas/4655494974d92443d54bbc3adb850cc3](https://gist.github.com/dvisockas/4655494974d92443d54bbc3adb850cc3)

It seems like I'm out of Ideas on what to try next. 

Maybe you guys can help? :)

---

### Post by mastablasta on 2016-10-26
since you messed it all up anyway.... install 16.04 and do not format the disk during the install procedure. instead, just overwrite what you have on disk. should default it to 16.04 and keep you stuff from 14.04 intact.

---

