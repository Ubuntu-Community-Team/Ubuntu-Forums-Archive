---
title: "Float denormalized operand"
date: 2011-05-16
forum: Wine
---

### Post by natjudnet on 2011-05-16
I was able to run Liberty Basic under Wine in Ubuntu 10.10 but unable in 11.04. I removed and reinstalled Liberty Basic but when I attempt to run it I get a Runtime Error: Float denormalized operand warning. Has something changed? Will Liberty Basic no longer run under Wine?

---

### Post by dacha on 2011-05-17
Yes, Ubuntu 11.04 shipped with a broken libfontconfig which causes that bug with some Wine applications. Please vote for [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/783622](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/783622)

And here is how you downgrade to the working Maverick libfontconfig: [http://ubuntuforums.org/showpost.php?p=10804481&postcount=8](http://ubuntuforums.org/showpost.php?p=10804481&postcount=8)

---

### Post by natjudnet on 2011-05-20
I can't believe all the programs on this forum that working under Wine with 11.04. Surely Ubuntu can create a patch or revision to correct the libfontconfig problem. :(

---

### Post by bobwyajnr on 2011-05-20
> **natjudnet said:**
> I can't believe all the programs on this forum that working under Wine with 11.04. Surely Ubuntu can create a patch or revision to correct the libfontconfig problem. :(

Everyone following the development of Unity knew that a lot of stuff was going to break in Ubuntu - with the 11.04 release...
Don't forget it is an intermediate development release - so you takes your chances!!
A lot of development time was poured into the new Window Manager this cycle. I've heard that quite a lot of bugs are still present in the final release candidate (which is fairly unusual for Canonical).

I'll be sticking with Gnome 2.3.x with Linux-Mint and Zoron-OS myself - I think :) I've nothing against Unity - but I don't want to test out alpha-build stuff!

Bob

---

### Post by natjudnet on 2011-07-10
Well, I finally got my Windows programs running under Wine in 11.04. I just used Synaptics to remove Wine 1.3 and replace it with Wine 1.2. I was considering rolling back to Ubuntu 10.10 but didn't want the hassle. I still don't like the Unity package but am using the classic desktop with 11.04 and have everything running smoothly. With the classic desktop unsupported in 11.10, I will not be upgrading.

---

### Post by bobwyajnr on 2011-07-10
@**natjudnet**

I've been playing about with my laptop and tried installing the latest Linux-Mint 11 Gnome release (based off 11.04). I'll keep an eye out for this problem - useful to know about in advance!

I'm puzzled as to why you don't just follow the fix in that bug report to revert to the 10.10 **libfontconfig1.so** shared library file? I am sure we could give you a hand with that here - if you get stuck! :confused:

I'm not a big fan of using the 1.2.xx release of Wine - you can't submit bugs Upstream and the code is frozen in a state that is many months old (with no bugfix backports). :(

Bob

---

### Post by natjudnet on 2011-07-11
It just appeared that a lot of people were having difficulty after attempting the change but I'm still willing to give it a try. Have you installed libfontconfig1.so on your system?

Claude

---

### Post by natjudnet on 2011-07-14
Bob,

Wine still wasn't working perfectly so I bit the bullet and followed your lead. My distro now has that clean minty flavor. (After verifying that Mint would _not_ be incorporating Unity, I switched to Mint 10.) I like it and Wine works finer than fine wine! :D

---

### Post by bobwyajnr on 2011-07-14
Hi **natjudnet**

Glad to hear your experience of Linux-Mint is positive! I wasn't really suggesting you switch over though!

Of course I suppose the big question is what Clement Lefebvre will do with Linux-Mint 12... Will he go with Gnome 3 (as originally planned for Linux-Mint 11)? :D

Bob

---

### Post by natjudnet on 2011-07-14
I dunno'. But for now, Wine woks and Unity is gone. I'll cross the next bridge when I get to it. :)

Thanks,
Claude

---

