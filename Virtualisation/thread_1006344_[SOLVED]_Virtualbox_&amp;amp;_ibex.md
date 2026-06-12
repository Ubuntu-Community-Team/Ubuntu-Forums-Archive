---
title: "[SOLVED] Virtualbox &amp;amp; ibex"
date: 2008-12-09
forum: Virtualisation
---

### Post by celticbhoy on 2008-12-09
how do I :-

1)   Setup Ibex/Virualbox to use USB ports, all howto's I have seen are for Hardy & file is different.

2)   Access files on a drive outside the Virtualbox OS, I have installed guest additions, and set the drives in virtualbox settings, but they dont show when I try to set a network place.

OBTW - Guest OS is XP.

---

### Post by Jeroenix on 2008-12-09
Hi,

1. The VirtualBox that comes with Ubuntu is the Open Source edition (OSE), which doesn't have USB implemented at all. The differences between the closed and open versions are listed here: [http://www.virtualbox.org/wiki/Editions]("http://www.virtualbox.org/wiki/Editions")

2. While your XP guest VM is down, use the Settings on that VM, enter a path and Name in the Shared Folders section. Start your XP guest, and use \\vboxsrv\Name to access the drive on the host (which can be... a mounted USB drive :).

---

### Post by celticbhoy on 2008-12-09
Thanx for the tip on point 1

On point 2, that is the method I am trying, but when I enter \\vboxsvr\Media ( the name setup) in add a network place xp says "the folder entered does not appear to be valid". Am I seting up in the wrong place in XP ???

---

### Post by Jeroenix on 2008-12-09
> **celticbhoy said:**
> Thanx for the tip on point 1

On point 2, that is the method I am trying, but when I enter \\vboxsvr\Media ( the name setup) in add a network place xp says "the folder entered does not appear to be valid". Am I seting up in the wrong place in XP ???

Hi,

To be sure: are you actually typing \\vboxsvr or \\vboxsrv ?  The latter is the correct one: SRV, not svr.

---

### Post by celticbhoy on 2008-12-09
I tried both just to be sure. When I hover my mouse over the folder icon at the bottom of the window it lists the shared folder as \\vboxsvr\Media.
I even tried it with the command :-

net use g: \\vboxsvr\Media

from a command prompt but it gives the error :-

Error 67 network name not found

any more ideas

---

### Post by Jeroenix on 2008-12-09
:)  You learn something everyday. I just tested BOTH notations, and it turns out they both work. I can't explain why it doesn't on your guest though.. Any firewall thingies running on the guest?

Also, a side-note: it seems that when you go back to a previous snapshot, you also lose the shared folder. This is not the case, as you said you see the folder listed when you hover your mouse over the folder icon... It's strange. I have no ideas anymore, but maybe I'll think of something on the way home. :)

---

### Post by celticbhoy on 2008-12-09
Thanx for the time anyway, the only other thing I can think of is that whenI first installed the guest additions, it was an older version, but I have 2.0.4 now. Could it be that I have to re-istall or re-start something becuase of this ??

---

### Post by celticbhoy on 2008-12-09
:redface:The shame !!!!:redface:

I have been using lowercase for the \\vboxsvr\

should have been \\VBOXSVR\

---

### Post by Jeroenix on 2008-12-09
Very odd.. I'm no Microsoft expert, but I was under the impression that upper/lowercase doesn't matter for Windows SMB shares (which is what Vbox seems to present to Windows). It works with both upper and lowercase here in my Vbox 2.0.4 OSE.

Oh well, as long as it works, eh? :) goodluck.

---

