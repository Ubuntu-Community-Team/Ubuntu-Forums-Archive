---
title: "Request for Mozilla Firefox 1.0.3"
date: 2005-04-17
forum: Ubuntu Backports
---

### Post by Seatux on 2005-04-17
I seen firefox 1.0.3 out for some time and i had my Windows machine updated to it. As usual, there are no debian packs going around. So there...

---

### Post by NeoChaosX on 2005-04-17
Yeah, I'd love to see a 1.0.3 backport too. Has some security fixes and improved pop-up blocking.

---

### Post by Burgundavia on 2005-04-18
The security fixes will be backported. I don't know about the pop-up blocking. 

Corey

---

### Post by Virtual DarKness on 2005-04-18
I'd like to have this backported too :)

bye,
Giovanni.

---

### Post by Bob D. on 2005-04-18
jdong won't have to backport 1.0.3. The Ubuntu devs will do this since it is a security release. 9 bugs fixed, 3 critical: [http://www.mozilla.org/projects/security/known-vulnerabilities.html](http://www.mozilla.org/projects/security/known-vulnerabilities.html)

Bob

---

### Post by jdong on 2005-04-18
[QUOTE=Bob D.]jdong won't have to backport 1.0.3. The Ubuntu devs will do this since it is a security release. 9 bugs fixed, 3 critical: [http://www.mozilla.org/projects/security/known-vulnerabilities.html]("http://www.mozilla.org/projects/security/known-vulnerabilities.html")
 
Bob[/QUOTE]
 
No bob, not necessarily. Ubuntu **may** or may not backport the security fixes (ONLY), not provide us with 1.0.3...... I will make a 1.0.3 backport ASAP.
 
For example, look at Warty (FF 0.9.3) -- how many security issues does that have? ;)

---

### Post by Bob D. on 2005-04-18
That's interesting...what made me think so was how fast the devs made 1.0.2 available. But, thinking about it, that was *prior* to Hoary being released.

I stand (well, sit) corrected.  :smile:

Bob

---

### Post by wolovids on 2005-04-18
[QUOTE=jdong]For example, look at Warty (FF 0.9.3) -- how many security issues does that have? ;)[/QUOTE]

That is exactly what I was thinking!  They probably should have upgraded Firefox in Warty, however there were numerous changes from 0.9.3 -> 0.10 -> 1.0.  Firefox was still in development and thus such a large upgrade could have introduced many negative outcomes and would have required a lot of testing.  That's probably why they just put the upgrade in Hoary. 

We'll see if Canonical thinks the upgrade from 1.0.2 -> 1.0.3 is minor enough to warrant a security update.  I hope!

---

### Post by jdong on 2005-04-18
[http://ubuntuforums.org/showthread.php?goto=newpost&t=24306](http://ubuntuforums.org/showthread.php?goto=newpost&t=24306)

We were talking about that in this security forum thread.

I'm pro-Fedora when it comes to minor updates, and that's why I started Backports :)

---

### Post by jdong on 2005-04-19
Patching Ubuntu .diff.gz for 1.0.2 against 1.0.3 fails due to a few rejected hunks. I'll have to work at it a bit more....

---

### Post by Deusiah on 2005-04-20
Thanks very much for doing this jdong, it's very much appreciated here. The backports project is great! Why on earth Ubuntu have to copy the Debian stance on upgrades I'll never know :-?

---

### Post by denzilla on 2005-04-21
[QUOTE=Deusiah]Thanks very much for doing this jdong, it's very much appreciated here. The backports project is great! Why on earth Ubuntu have to copy the Debian stance on upgrades I'll never know :-?[/QUOTE]


So damn true!

---

### Post by vassalle on 2005-04-23
any news on the firefox 1.03 ?

---

### Post by Turin Turambar on 2005-04-23
Just wondering, why don't you install (or perform upgrade) Firefox 1.0.3 debian package, available on packages.debian.org?
I don't quite understand this backport project...aside from the fact that you cannot download from packages.debian.org in synaptic/apt-get, what else do you get?

---

### Post by DirtDawg on 2005-04-23
Speaking of Firefox 1.03, on my windoze machine I've noticed it doesn't always stop running when I exit the program. This was never a problem before 1.02 or so. I just wondered if anyone else has noticed this?

---

### Post by Turin Turambar on 2005-04-23
[QUOTE=Turin Turambar]Just wondering, why don't you install (or perform upgrade) Firefox 1.0.3 debian package, available on packages.debian.org?
I don't quite understand this backport project...aside from the fact that you cannot download from packages.debian.org in synaptic/apt-get, what else do you get?[/QUOTE]

Got it. I just tried to install firefox 1.0.3. I did install it with a success, but I entered into dependancy hell, so I had to manually reinstall packages from ubuntu CD as Synaptic didn't want to reinstall it.

---

### Post by Alex4R on 2005-04-23
[QUOTE=jdong]For example, look at Warty (FF 0.9.3) -- how many security issues does that have? ;)[/QUOTE]

You are right, but 0.9.3 doesn't support some of my favorite extensions. This is one of the reasons why I upgraded to Hoary. Also, I think if you go to [http://www.mozilla.org](http://www.mozilla.org), you can download 1.0.3 and install all of the files in a remote directory, then delete everything out of the /usr/lib/mozilla-firefox folder and copy all of the files from the remote directory into /usr/lib/mozilla-firefox it should work. It did for me.

---

### Post by jdong on 2005-04-24
Alright, while I was away on a 4-day vacation (*excuuuuuse* me ;)), it seems like Debian has a Firefox 1.0.3 package.


I'll proceed to make the backport :)

---

### Post by TravisNewman on 2005-04-24
Nice :) Hopefully this one won't have the weird lockup problems (yes I did start experiencing those).

---

### Post by XDevHald on 2005-04-24
When I installed 1.0.3 the .sh in the /usr/lib/mozilla-firefox dir, it installed it but turned it into an xapplication to where if you double click on firefox it'll say display or run in terminal or just run, now I did install this before a few days ago and it worked just fine from the installer-bin but not sure where I went wrong on installing it now compared to then...

---

### Post by Turin Turambar on 2005-04-24
Here's what happened to me: I installed both Firefox 1.0.3 and Gnome FF support, debian packages. However, they needed some lib6, libfont1 or so files... Problem is because on Ubuntu they are older than required...
When I installed new libraries, system reported 4 or so broken packages - because some Ubuntu programs require the exact version of lib6, not newer or older... then I had to install everything again (from Ubuntu CD) with dpkg...

So it's not an easy task as it first seemed.

---

### Post by poofyhairguy on 2005-04-25
Thanks is advance Jdong.

---

