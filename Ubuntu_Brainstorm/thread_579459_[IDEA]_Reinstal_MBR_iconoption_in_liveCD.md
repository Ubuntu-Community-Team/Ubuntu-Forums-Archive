---
title: "[IDEA] Reinstal MBR icon/option in liveCD"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by zolookas on 2007-10-18
[B]Summary:
[/B]A simple gui app to restore grub boot loader.
[B]Scope and Use Cases:
[/B]John have just reinstalled his second operating system and it replaced boot loader, he can't boot into ubuntu.
[B]Implementation Plan:
[/B]Make a gui app (i think even zenity would be sufficient) to restore grub boot loader and include it in a liveCD.

---

### Post by smartboyathome on 2007-10-18
I think that if it installs GRUB on the second operating system, you could just go into the GRUB prompt, and set it that way.

---

### Post by AlexenderReez on 2007-10-18
it can be done/correct easily for most users....if don't know , google.com is your friend...

---

### Post by amano on 2007-10-18
Nope. Googling and writing down commands isn't a nice solution for an intuitiv OS. Above all you cannot enter the internet from the Live CD many times (not without configuring a new connection which can take some time for some providers). And having to google from inside the Windows (which killed your Grub before) doesn't sound nice either.

A little UI or at least script should fix the grub in an intuitiv way. And  this can probably be done easily. Just drop a (live cd-only) link onto the dektop or the menu that calls a script which either restores a backed up grub or - better - looks for the lost ubuntu partition and adds the windows system  (which had perviously killed the grub) to grub.

Just a link and a script. 

No need to google --> intuitiv --> Ubuntu.

---

### Post by Zdravko on 2007-10-18
Nice idea.

---

### Post by zolookas on 2007-10-19
> **AlexenderReez said:**
> it can be done/correct easily for most users....if don't know , google.com is your friend...
Sure, using information found with google help you can build LFS, but ubuntu is meant to be different distro.

---

### Post by Zdravko on 2007-10-19
What do you mean with "different distro"?

---

### Post by carac on 2007-10-19
> **zolookas said:**
> [B]Summary:
[/B]A simple gui app to restore grub boot loader.
[B]Scope and Use Cases:
[/B]John have just reinstalled his second operating system and it replaced boot loader, he can't boot into ubuntu.
[B]Implementation Plan:
[/B]Make a gui app (i think even zenity would be sufficient) to restore grub boot loader and include it in a liveCD.


VERY GOOD IDEA !!!

---

### Post by Zdravko on 2007-10-19
Yes, it is indeed.

---

### Post by AlexenderReez on 2007-10-19
maybe....but for some users...but for other users, we are not using grub....well....i can make it in g.u.i(icon or what so ever as launcher )...

---

### Post by m0eman on 2007-10-19
A great idea!

---

### Post by Zdravko on 2007-10-19
Yes. It is as I already said.

---

### Post by aamukahvi on 2007-10-20
> **AlexenderReez said:**
> maybe....but for some users...but for other users, we are not using grub....well....i can make it in g.u.i(icon or what so ever as launcher )...
If you're not using the default bootloader you're most likely not the type that needs hand holding when it comes to restoring the MBR.

---

### Post by carac on 2007-10-20
> **zolookas said:**
> [B]Summary:
[/B]A simple gui app to restore grub boot loader.
[B]Scope and Use Cases:
[/B]John have just reinstalled his second operating system and it replaced boot loader, he can't boot into ubuntu.
[B]Implementation Plan:
[/B]Make a gui app (i think even zenity would be sufficient) to restore grub boot loader and include it in a liveCD.


I have just seen that there is a package called 'StartUp Manager' (goes to System/Administration in the GUI) which is 99% of that - it should be placed on the LiveCD (and eventually updated to work from CD towards HDD, eventually to detect the HDD installations and previous GRUB configuration). (it should also be eventually called at the end of the normal install, eventually from the final Advanced dialog which controls GRUB ?)

Note that the program above will also fix some problems with the splash boot (which in the 7.10 version seems to be 'invisible' on many systems).

---

### Post by Zdravko on 2007-10-20
I've never heard of it :(

---

### Post by amano on 2007-10-28
Having a script and just an easy starter from the desktop to it would already be sufficient. Maybe it could call some functionality which is already available within ubiquity or something like that.

---

