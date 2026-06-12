---
title: "windows vista on vmware"
date: 2006-05-29
forum: The Cafe
---

### Post by brodock on 2006-05-29
is it possible?
i mean... microsoft is trying to make lots of effort to make people who use linux not able to dual boot...
but what about vmware?
can i safe-try with it?
i mean, does any one here tryied to install vista at vmware (i know it consumes thousands of trillions mb o ram lol)

---

### Post by towsonu2003 on 2006-05-29
[QUOTE=brodock]is it possible?
i mean... microsoft is trying to make lots of effort to make people who use linux not able to dual boot...
but what about vmware?
can i safe-try with it?
i mean, does any one here tryied to install vista at vmware (i know it consumes thousands of trillions mb o ram lol)[/QUOTE]
I think you mean Windows eats your bootloader installed to MBR? If so, check out this page if you're willing to do some repartitioning and installing windows AFTER ubuntu. also search the forums for vista bc I know ubuntu's grub has problems setting Vista up correctly (easy to fix, but don't remember how). 

Page was: 
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

Anyway, vmware should be safe to install vista, but you might have problems checking aero (vista 3d effects) in a vmware virtual machine... 

PS. ubuntu's grub isn't that good at recognizing other linux distros either (will file a bug in a minute).

---

### Post by brodock on 2006-05-29
thanks for the info... aero was the only thing i wanted to try... lol

---

### Post by towsonu2003 on 2006-05-29
[QUOTE=brodock]thanks for the info... aero was the only thing i wanted to try... lol[/QUOTE]
heheh

I think you'll need to resize partitions and add a new one (ntfs filesystem) for Vista... Don't forget to check out the recover grub wiki page and search the forum on a fix for grub not being able to boot vista (I guess keywords would be "grub vista" with no quotes)

good luck :)

---

