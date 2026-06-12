---
title: "System Restore for Ubuntu/Debian Released"
date: 2008-09-15
forum: The Cafe
---

### Post by LaRoza on 2008-09-15
It is back up, get it here (works this time...): [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0)

A simple click-click installer and an easy interface (It will be in Applications->System Tools)

There is a problem with the GTK interface but it works (although you might get an error, for no reason)

It works with GTK or QT (so whatever you have will probably work)

Hope someone finds it useful!

---

### Post by RedPandaFox on 2008-09-15
Will try it when I get something that can run Ubuntu :(

After selling my PC I now cant run Linux! My laptop I cant find network drivers for so I cant do what I need it for!

---

### Post by wirepuller134 on 2008-09-15
Thanks for your time on this, very self explanatory.

---

### Post by LaRoza on 2008-09-15
> **wirepuller134 said:**
> Thanks for your time on this, very self explanatory.

It wasn't just me (although I started it and wrote the core of it, and the command line interface interfaces).

[http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665) (Program has the details)

---

### Post by conehead77 on 2008-09-15
Ok, here is a first bug report:

I created a file in my home directory, added it to the files list and deleted all the default files from the list.
Then i made a restore point, changed the content of the file and tried to restore it.
The file didnt switch back to the previous content.

The data is stored fine in the .sysres directory, but it just didnt restore my file.

---

### Post by cariboo on 2008-09-16
I don't know why people want linux to be like windows, The trash can is probably the one of the worst, and now system restore. In the next release there will be the choice of last good boot in grub. If you can't operate a computer well enough that you need a safty net why not just run windows.

Jim

---

### Post by LaRoza on 2008-09-16
> **conehead77 said:**
> Ok, here is a first bug report:

I created a file in my home directory, added it to the files list and deleted all the default files from the list.
Then i made a restore point, changed the content of the file and tried to restore it.
The file didnt switch back to the previous content.

The data is stored fine in the .sysres directory, but it just didnt restore my file.

Thanks...

I don't know how that happened. The packaged versions were missing a vital bit of code.

I fixed it, but it will be a day until it can get repackaged...

Sorry for the inconvenience.

For those interested...

You could pull from lp:sysres/1.0 as it is fixed, but if you understood that, you don't need this program.

---

### Post by p_quarles on 2008-09-16
> **cariboo907 said:**
> I don't know why people want linux to be like windows, The trash can is probably the one of the worst, and now system restore. In the next release there will be the choice of last good boot in grub. If you can't operate a computer well enough that you need a safty net why not just run windows.

Jim
It's hardly like Windows: those features are integrated into the built-in shell in Windows. These are just optional add-ons in a *nix environment. 

In any case, operating a computer without a safety net indicates either 1) you aren't doing anything that important, or 2) you don't know how to operate with a safety net.

---

### Post by kevdog on 2008-09-16
Is this package available via svn or cvs?

---

### Post by LaRoza on 2008-09-16
> **kevdog said:**
> Is this package available via svn or cvs?

No, we use bazaar, a distributed version control system.

---

### Post by Polygon on 2008-09-16
> **cariboo907 said:**
> I don't know why people want linux to be like windows, The trash can is probably the one of the worst, and now system restore. In the next release there will be the choice of last good boot in grub. If you can't operate a computer well enough that you need a safty net why not just run windows.

Jim

yeah, cause deleting a file should delete the file right away with no way of recovering it. No one ever accidentally hits the "delete' menu item when trying to go to properties

system restore is useful cause if you install some package that screws up your apt database.....or if a bad update comes through and you have no GUI or internet.....etc

aka, just because window's has it doesn't mean its not a good idea.

---

### Post by fatality_uk on 2008-09-16
Thanks LaRoza. Using something like SysRes would, I think, encourage a lot more people to use/try Linux. Having confidence to try new apps and have the ability "rollback" to a known good setup is of great benefit.

---

