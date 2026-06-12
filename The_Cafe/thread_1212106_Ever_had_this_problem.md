---
title: "Ever had this problem?"
date: 2009-07-13
forum: The Cafe
---

### Post by AoSteve on 2009-07-13
I have an old 80GB IDE drive I use for windows Vista.   Yeah, slow and not powerful but it works.   Well I got my new SATA drive and wanted to reinstall Vista on my older 250GB IDE drive that is quite a bit faster and larger.   So..   

I put the disk in and boot up to install Vista and get to the drive selection...

"No drives that meet the specification are detected..."

I tried everything, reset my entire BIOS!!!!!    Nothing worked..

Come to find out...   IF you have a current installation of Vista on the system it will NOT let you install vista.  I pull out the 80GB and it works....

"Nice way to burst my bubble MS"    Just another reason I love Ubuntu, I've had two different installs of Ubuntu on the same physical disk.   This is rediculous that I can't install Vista on this system with my other install still attached.

[/end pist off rant]

---

### Post by moody_mark on 2009-07-13
As you know you can have a primary and secondary device on an IDE chain. Just a guess here, did both the drives have the "autodetect" jumper selection. Perhaps Vista only wants to install to the primary drive?

---

### Post by AoSteve on 2009-07-14
Nope, not at all.   I tested every theory I had.   And my IDE chain is NEVER to autoselect.   I hate that crap because I've had drives that haven't liked that idea at all.    So my 250GB was a slave and the 80GB was a master.    Well now I got it, took the 80GB totally out and I'm running the 250gb as a master.   Sata is much easier then IDE, but both work, which is what matters.    Also, vista for some reason doesn't like my controller in ACHI mode either...  Odd..    Well at least IDE->SataII  works well.  It suposedly emulates SATAII through the IDE controller to the operating system.   So now windows doesn't have any IDE drivers loaded for the drive!

Either way it just torques me that windows won't nstall when there's another copy on the system.  I never knew this.  But it will come up with that problem if there's any known vista installation.   I even tried rerunning the setup after the install on the 250GB drive and it told me the same thing.  LOL

---

### Post by HappyFeet on 2009-07-14
You could use a live cd and use gparted to format the drive first.

---

### Post by AoSteve on 2009-07-14
Well I got it working.   I wasn't going to mess with the 80GB and was thinking of keeping it around for a "testing" OS drive.   But of course not.  LOL    I didn't feel like formatting it, I wanted to keep what I could from the drive itself.

---

