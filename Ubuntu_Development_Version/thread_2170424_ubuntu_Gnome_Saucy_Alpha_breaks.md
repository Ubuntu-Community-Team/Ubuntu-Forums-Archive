---
title: "ubuntu Gnome Saucy Alpha breaks"
date: 2013-08-26
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2013-08-26
Hi, I have been trying to get the Alpha 2 of Ubuntu Gnome 'Saucy' to work for two days, failing!
Here's what happens, I install the OS, everything boots up fine...
I try to update, It says there is a 'Partial Update' available, which I do...

After the 'restart' the the system hangs at the first blue screen  and even the log-in screen does not come! Using tty1 and 'startx' doesnt help, ctrl+Alt+F7 gives back the same old blue screen nothing more...

Out of two times I tried, one time Kernel version 3.11.0-something was installed, which didn't happen the second time.

As this is Alpha Version, I am just trying to find out if any1 else has tried succesfully.
Don't really need a support for this right now.

---

### Post by coffeecat on 2013-08-26
Not a Cafe thread.

*Thread moved to **Ubuntu +1**.*

---

### Post by PaulW2U on 2013-08-26
> **bhattabhishek said:**
> I try to update, It says there is a 'Partial Update' available, which I do...

That may have been your problem. What was installed but more importantly what was removed?

---

### Post by grahammechanical on 2013-08-26
If you are going to be using Ubuntu development branch (any flavour) then you should read this Sticky thread at the top of Ubuntu+1 section.

[http://ubuntuforums.org/showthread.php?t=2140142](http://ubuntuforums.org/showthread.php?t=2140142)

Note the link to this

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

To put it simply, never, repeat, never accept a partial upgrade when running the development branch.

> If you use Update Manager to upgrade your packages, and it offers to do a * Partial Upgrade *  do not accept it without thoroughly checking what packages it offers to  remove, upgrade and install. If you do, you will most likely end up  removing packages that shouldn't be removed, and waste time and effort  repairing your testing installation and asking for assistance.  


Most * Partial Upgrade *  situations occur due to package archive inconsistencies, which will  typically be resolved within a few hours. If your package manager is  confused, and so are you, simply wait and hold off the updates until  things settle down.  



There have been several kernel upgrades over the last few days. The developers are tracking the Linux 3.11 and are pushing the upgrades to that kernel onto Saucy Salamander as fast as they can. There are several components to a kernel and often some of the components are ready for downloading and other parts are not. It may take two days for all the bits to be available for installation. A partial upgrade will bring in the bits that are in the archive but without the other bits the system will brake.

Regards.

---

### Post by su:bhatta on 2013-08-26
Thanks a ton for the replies...

coffeecat: Thanks for moving the thread to the right place

PaulW2U: The problem I have faced is this, since I require Fglrx-updates for proper screen resolution, I could not get all the details of the 'partial upgrade', the apps to be deleted went below my screen and never could see it...

Grahammechanical: Thanks a ton, I should have been more careful and read those threads and wiki up before installing. I am using UbuntuStudio Alpha too, that went and installed 3.11 without any hitch!

P.S. Closing the thread!

---

