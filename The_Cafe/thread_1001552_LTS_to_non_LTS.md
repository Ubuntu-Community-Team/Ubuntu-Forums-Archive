---
title: "LTS to non LTS"
date: 2008-12-04
forum: The Cafe
---

### Post by inobe on 2008-12-04
personally i would take the plunge for better and faster along with all the new bugs, however i think its inappropriate that new users jump on them' especially without reading or googling for bugs.

some examples: intel onboard graphics, onboard nvidia 8200

helping these people reconfigure xserver seems like a common thing.


i like to question them when they ask for a howto upgrade, i do show them' however i give them something to seriously think about before hand.

heck if its still supported and everything works "why upgrade" they usally do not have a logical reason.

any opinions ?

---

### Post by magmon on 2008-12-04
Cuz you get all the cool new features!

---

### Post by inobe on 2008-12-04
wow, not many opinions ?

---

### Post by inobe on 2008-12-04
[http://ubuntuforums.org/showthread.php?t=1002163](http://ubuntuforums.org/showthread.php?t=1002163)
> 
I had been using compiz effects on 8.04 without any problems. When I upgraded to 8.10, I could no longer use them. The computer won't let me switch from None to Normal under Visual Effects (System->Preferences->Appearance->Visual Effects). Initially, it told me it couldn't do it. After fiddling with compiz-check, it now freezes if I attempt to switch it or type "compiz" in the terminal.

Additional potentially useful information:
Typing "lspci | grep -i graphic" in the terminal yields:
00:02.0 VGA compatible controller: **Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)**

Is my graphics card no longer supported by 8.10 or something? Thanks for any help!
discuss

---

### Post by igknighted on 2008-12-04
That has nothing at all to do with LTS vs. non-LTS.  I think for everyone who is not a business user, LTS means nothing.  By the time the next LTS rolls along, the software will be so old most users wont want it.

And there can be bugs in drivers at any time.  The intel block in compiz-check could be removed in an update later if the bug is fixed, but no one really knows when that could be.  But again, this has nothing to do with LTS or not, as there were many instances of similar issues from 7.10 to 8.04.

---

### Post by inobe on 2008-12-04
one would think 8.10 would be 9.04 LTS ?

edit: of course the bugs will get scrubbed first, also that person is using 8.04

---

### Post by sbooder on 2008-12-05
I not sure I get the point of a non LTS distro, if it is so buggy, and we should stick with 8.04, who the hell is Intrepid aimed at.  

If the powers that be want to  release a version so inadequate no one can use it, why not just call it Vista!

---

### Post by inobe on 2008-12-05
ultimately its community support, i am for it 100% and will always install the latest and greatest regardless of bugs' i do not mind reporting' however i am a advanced user and fully capable of getting out of complicated situations, on the other hand' i think we are going about it the wrong way when a new version is release !

let me elaborate, those that seek to upgrade should be warned of bugs and other issues !

sure' i know, you can eye ball the release notes, the problem is' a novice user won't know where to find these notes !

if we look at the main download page' its not presented the way many would understand.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

a nice link in bold can save a lot of headaches:)

---

### Post by Endolith on 2008-12-05
Is there even a difference between LTS and non-LTS?  They seem equally buggy.

---

### Post by koenn on 2008-12-05
> **Endolith said:**
> Is there even a difference between LTS and non-LTS?  They seem equally buggy.

the bugs in LTS last longer.

---

### Post by inobe on 2008-12-05
sarcasm and seriousness are two different things:p


this is why newer versions are buggy........

newer programs on top of a newer kernel !

example: if you upgrade from 8.04 to 8.10 you get kernel 2.6.27 and xorg 7.4, however in 8.04 you had kernel 2.6.24 and xorg 7.3.....

i am running opensuse 11 with there latest kernel 
```
/home/core-duo # uname -r
2.6.25.18-0.2-pae
```

i am still using xorg in suse 7.3 !

everyone knows what happens when you upgrade, if you visit bugzilla or even search it googling' take a guess what the first os in the list is when i type xorg bugs .

you don't want to a new linux user this kind of responsibility :)

---

