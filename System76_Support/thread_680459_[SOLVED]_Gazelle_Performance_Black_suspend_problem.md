---
title: "[SOLVED] Gazelle Performance Black suspend problem in Gutsy"
date: 2008-01-27
forum: System76 Support
---

### Post by afilonov on 2008-01-27
I have Gazelle Performance Black (order #3785). I didn't have many problems with suspend/resume with Edgy and Feisty (well, there was that annoying screen shift problem, but I had a good workaround). Now, after upgrade to Gutsy, machine hangs in BIOS either on suspend or on resume. Sometimes I can go four or five suspend/resume cycles, but I didn't have more. Is there anything I can do about it?

---

### Post by thomasaaron on 2008-01-28
Multiple suspend/resume cycles have always presented problems. We've been working on that one for a while.  

Please file a bug report on this one (you might search to see if there is already one in there).

[https://launchpad.net/system76](https://launchpad.net/system76)

---

### Post by afilonov on 2008-01-28
I'm going to try couple more things before filing a bug.

Answers to questions in "HELP ME HELP YOU":

1. Ubuntu 32-bit
2. Don't know. It's Gazelle Performance Black bought in November 2006. Probably GAZP2.:
How can I find out?
3. I added acpi_sleep=s3_mode to the kernel string in grub menu, changed SAVE_VBE_STAT and POST_VIDEO to false in /etc/default/acpi-support.

---

### Post by thomasaaron on 2008-01-29
> 2. Don't know. It's Gazelle Performance Black bought in November 2006. Probably GAZP2.:

You can email me with your name/order#, and I can look it up.
Or, look on the bottom of the computer and tell me what the model number is. Probably S62*?

---

### Post by afilonov on 2008-01-29
> **thomasaaron said:**
> Multiple suspend/resume cycles have always presented problems. We've been working on that one for a while.  

Please file a bug report on this one (you might search to see if there is already one in there).

[https://launchpad.net/system76](https://launchpad.net/system76)

> **thomasaaron said:**
> You can email me with your name/order#, and I can look it up.
Or, look on the bottom of the computer and tell me what the model number is. Probably S62*?

It's S62J. I put order number in the initial post of this thread.

---

### Post by tedrampart on 2008-01-29
I've been having this issue as well..  sometimes it sits there with the fan going but doesn't resume fully, or it just turns off when I try to resume it.  

it happened with the gazp3 case I had, and now with my gazp2 case (after warranty on my case)..

---

### Post by thomasaaron on 2008-01-30
OK. Please file a bug report on it, and I'll do some testing in-house.

---

### Post by afilonov on 2008-02-06
Filed bug #187536 on Jan 31. Sorry, looks like duplicate bug #187537 was accidentally filed as well, I marked it as duplicate.

---

### Post by afilonov on 2008-02-28
Bump. Is there any progress? Bug is not getting updated either. I thought that problem is gone with latest kernel update, but no, had laptop hang during suspend two days ago.

---

### Post by thomasaaron on 2008-02-28
I don't understand. Does it hang with every suspend or just occasionally?

---

### Post by afilonov on 2008-02-29
It does not hang on every suspend/resume. But it hangs for sure after several cycles. It's better with the latest kernel updates, but probably can go for 10 cycles max.

---

### Post by tedrampart on 2008-03-01
thats about the same as mine.  Its hard for me to keep track.  Sometimes it either hangs, or just shuts right off when I triy to turn it back on.  but mostly it just hangs.

---

### Post by afilonov on 2008-04-24
After applying the fix proposed in the bug it's working fine now. Strangely enough, it hung right away after fix was applied, then on the fourth suspend, but after that I'm working for about a month already without any problems. Thanks to system76 guys. I'll close the bug tonight.

---

### Post by afilonov on 2008-04-27
> **afilonov said:**
> After applying the fix proposed in the bug it's working fine now. Strangely enough, it hung right away after fix was applied, then on the fourth suspend, but after that I'm working for about a month already without any problems. Thanks to system76 guys. I'll close the bug tonight.

Oh well. Just the next day after I wrote this it hung on suspend again.

---

### Post by afilonov on 2008-07-21
Upgraded to Hardy. Marking this thread as Solved.

---

