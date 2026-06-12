---
title: "Manage multiple chroots with rootz"
date: 2008-01-20
forum: Virtualisation
---

### Post by whadar on 2008-01-20
In the past there were few tutorials about chroot, mainly explaining how to create a 32bit chroot environment in a 64bit system, but actually chroot can be useful in more scenarios.
With chroot you can not only create environments of different architectures, but also different releases or different distros.

For example, having side by side Ubuntu Dapper, Ubuntu Gusty, Fedora 8 and Gentoo unstable. Then we can choose from which chroot  we want to launch the command.

The main advantage of chroot compared to other virtualization solutions is that it is very lightweight, and the applications that run integrate with the desktop. The user can't even tell if the application is chrooted or not.

The main disadvantage is that setuping many chroots is quite hard work - this guide - [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) for examle. 
But that's where **[rootz]("http://vamosproject.org/rootz") **comes in and makes life easy. :guitar:

To setup and confugure a chroot with mount binds and everything just do:
> rootz /path/to/chroot1 /mnt/chroot1

Afterwards, to run an application, as a normal user:
> rootz-launcher appname 

Or directly from the browser, by clicking rootz:// links like this: [pidgin]("rootz://pidgin")

rootz even gives more options:

* Create chroots from LiveCD ISO file
* Use a remote ISO from the server without prior download of the whole file.
* Changes are saved separately thanks to unionfs
* Application launcher (rootz-launcher) that can seek the requested application in the chroot and launch it when found.

See homepage: [http://vamosproject.org/rootz](http://vamosproject.org/rootz)

---

### Post by fjgaude on 2008-01-20
Thanks, sounds good. Can you chroot a WinXP OS?

---

### Post by whadar on 2008-01-20
Interesting question :)

Do you mean plain chroot? (to get a shell?)
I don't think you can do standard chroot into WinXP, because chroot will look for a shell, like /bin/sh which of course doesn't exist in XP.

If you want to run win applications, maybe wine can help you do that. Honestly I've never tried that :)

---

### Post by bodhi.zazen on 2008-01-21
This sounds very similar to OpenVZ

---

### Post by whadar on 2008-02-06
With OpenVZ you have all the virtual environments under the same desktop?

---

### Post by bodhi.zazen on 2008-02-06
> **whadar said:**
> With OpenVZ you have all the virtual environments under the same desktop?

I am not following your question.

---

### Post by whadar on 2008-02-12
I ask it differently:
Every openVZ guest has it own desktop enviornment, or all of them use the host's desktop. I assume the answer is desktop per guest.
With rootz you a ***single*** desktop, which is a big advantage when users want to run interactive applications.

---

