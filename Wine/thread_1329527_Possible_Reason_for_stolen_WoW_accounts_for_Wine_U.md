---
title: "Possible Reason for stolen WoW accounts for Wine Users?"
date: 2009-11-17
forum: Wine
---

### Post by Alatar1 on 2009-11-17
So my wow account got hacked into the other day, I got the password back and logged in to find my account stripped of all the items and gold etc...
But they only way they could've of gotten my password is by keylogging, which some research tells is next to impossible in linux, somehting to do with keylogging requiring sudo permissions.
        But I thought long on hard on the issue and may have come up with an answer for it, bear in mind i'm not exactly a linux genius but it kinda made sense to me...so whenever I install something new or run pretty much any file operations through wine(like a patch or install of a new game/windows app) it never asks for the root password, which it asks for to do pretty much anything without using wine or windows apps. 

So my theory is that something ran through wine already has the permissions it needs to run properly (I can't remember if i set it that way or if it just does it) in order to prevent issues with ubuntu asking for a password every step of the way, which I'm guessing could cause some serious problems in windows applications like crashing and so forth since it completely stops and disallows said program to run until sudo password is given.

        So if this is the case, would it be possible to be keylogged if the malicious file is in the /.wine/c_drive directory somewhere (more than likely downloaded with a WoW add-on) for your password to be stolen??

Then again I could be wrong and just being a crazy idiot noob? but i dont know how else to explain it, chkrootkit tells me everything is fine rootkit wise, I've scanned for every known virus for ubuntu/linux (which like what? maybe 20? which i also hear are very ineffective) so I'm pretty stumped and worried if my theory isn't right...

---

### Post by beastrace91 on 2009-11-17
It is not impossible or unheard of for Windows viruses to get caught on Wine (although it is uncommon). There are a few different antivirus programs out there that install on Linux (personally I use [avast!](http://avast.com/)) If you think you might have picked something like this up be sure to download something and scan your system.

Also note that anything like this that might have gotten installed is also easily solved by wiping out your Wine install and simply reinstalling everything. 

Regarding your question about root password to install things - Wine does not need your password to install applications because all it's data is stored in your /home directory (**~/.wine** to be exact) and thusly your normal user has full permission to write to this directory.

Regards,
~Jeff

---

### Post by realzippy on 2009-11-17
There will not be so many WoW users using Wine/Linux that it
is worth it to write a keylogging addon for it.What about the strength of your password?

---

### Post by Alatar1 on 2009-11-17
Thank you for the reply i appreciate the input, and I did exactly that I completely wiped wine and wow and all the apps i had with wine and reinstalled wine fresh, it seems to have helped. 
thanks a ton.

*edit*
as for the strength of my password, i thought it was good, but maybe not...The possibility of a brute force type program stealing it is very real as well..but i ordered a blizzard authenticator which works pretty much like a VPN card when tied to your battle.net/WoW account, it makes it impossible to login to the account without having this card physically in your posession, with code on that changes every 30 sec or so

---

### Post by joeelmex on 2009-11-17
Thanks Alatar, had no idea about the fob.  There is an App for it too for the iphone going to use that.

---

### Post by Alatar1 on 2009-11-17
Why you're welcome good sir :) (or Maam :P) , And it's actually free on the iphone/itouch 6.50USD for the keychain card, used to be 10 though

---

