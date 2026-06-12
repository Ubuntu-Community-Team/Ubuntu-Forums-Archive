---
title: "Retrieve forgotten WinXP(SP2) pass with ubuntu?"
date: 2007-11-15
forum: Windows
---

### Post by dynamethod on 2007-11-15
Hi there ive been using ubuntu so long that ive forgotten my password for my winxp partition :S

is there someway i can retrieve it with ubuntu?

the otherthing is i think i may have disabled the guest account on the xp partition as well, its been ages since ive used windows, and i really need to get back into the OS without formatting, thanks in advance

---

### Post by tombott on 2007-11-15
There are Linux based Windows password reset tools out there.
I use Hiren Boot Cd to do this.
Have a search and download and burn it. PM if you need more info.

---

### Post by dynamethod on 2007-11-15
unfortunatly i dont have a CD/DVD burner :/

---

### Post by tombott on 2007-11-15
Do you have a floppy drive and spare disk?

if so look [here]("http://home.eunet.no/pnordahl/ntpasswd/bootdisk.html")

---

### Post by dynamethod on 2007-11-15
dont have one of those either :/

ive only got a CD/DVD reader, and a couple USB ports

---

### Post by tombott on 2007-11-15
I have just found [this]("http://www.dslreports.com/forum/remark,14828505") article which says it is possible to reset your XP password using your XP install CD.
I never knew you could do that, very handy to know! But it does mean you would have to run through a repair setup on XP. This shouldn't cause any problems as long as you have your product / CD key.
Once booted back into XP you would need to reapply all service packs etc. so I would use this option as a last resort.

---

### Post by dynamethod on 2007-11-15
ahh sweet, ill try that! hey tyvm for this help, much appreciated!

---

### Post by tombott on 2007-11-15
No worries mate.
Let us know how you get on.
In theory it should keep all your XP settings, programs etc in tact, but you never know with Microsoft.

---

### Post by Rhubarb on 2007-11-15
Another way to get your windows password would be to use OPHCrack.
[http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)

The easiest way would be to burn the live CD there and run it, but since you can't do that you would have to compile the program and download the rainbow table off their website.

Great to hear that you haven't needed to use windows in a long time :)

---

### Post by tombott on 2007-11-15
lol, funny that we are helping somebody get into their Windows system on a Ubuntu forum!

As you said nice to know that the OP hasn't had to use Windows for so long though!

---

### Post by dynamethod on 2007-11-16
well ive found i didnt need the data after all, also ive deleted the winxp partition(finally) since i dont use/need it anymore

off topic but, how do i remove the "windows xp" entry in the grub menu list?

---

### Post by lucasrossi on 2007-11-16
Hi,
You need to "sudo gedit /boot/grub/menu.lst"

---

### Post by darksidedude on 2007-11-18
safe mode and log into admin account 8)

---

### Post by CypherHackz on 2007-12-27
you can change your password in safe mode unless you put password to your administrator account.

-cypher.

---

