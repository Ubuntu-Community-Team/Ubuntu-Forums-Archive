---
title: "A rant on 8.10"
date: 2008-12-02
forum: Testimonials &amp; Experiences
---

### Post by borzwazie on 2008-12-02
I've been using Ubuntu since I was introduced to it in 5.04. I like(d) Ubuntu, because it was Linux, but it all just worked after install. I put the CD in, and a working box came out the other end.

This has held true until 8.04. 8.04 shipped with a completely borked wireless package, which remained borked. 

Then, 8.10 shipped. Where do I start?

First of all, why no rescue disk option? Sure, we can futz with the options in F6, but come on, how hard is it really to just include that option? I sure could have used it because of:

Second: mixed PATA/SATA. Something is horribly wrong with the PATA driver implementation on 8.10. No matter what I do, on various machines new and old, I CANNOT install 8.10 to a PATA drive. I end up with Grub error 2 or 5. The install will proceed normally, but upon reboot: no boot. I had this problem on a Core2Duo box, an Athlon64 (939) box, and even an old Pentium III.

Third: wireless, again. This, at least, is in the release notes - the Atheros driver that is used by default just plain does not work correctly for me, and I had to backrev to the older driver. Kudos for the release notes, but no points awarded for QA process.

Lastly: Why does the install process default to the longest-loading X process I've ever seen? This boot process on a modern (Core2Duo) box takes 15 freaking minutes! I appreciate the minimal amount of information collected to get the install process underway, but the forms and partitioning take 30 seconds - why should the boot process take so long?

To be sure, there are workarounds for all or most of these things, but the mere presence of these issues indicates to me that Ubuntu has lost its way somewhere as the easiest-to-use distro.

---

### Post by wolfen69 on 2008-12-02
> **borzwazie said:**
> I CANNOT install 8.10 to a PATA drive. I end up with Grub error 2 or 5. The install will proceed normally, but upon reboot: no boot. I had this problem on a Core2Duo box, an Athlon64 (939) box, and even an old Pentium III.



that would lead me to believe that you have a bad burn/disc. i have installed 8.10 on several pata drives without issue.

if 8.10 irks you so much, don't use it. wait for 8.04.2 to come out on 1/1/09. it will have all updates and support for newer hardware/more hardware.

---

