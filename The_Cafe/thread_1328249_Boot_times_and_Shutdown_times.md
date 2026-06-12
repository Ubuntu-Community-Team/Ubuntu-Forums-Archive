---
title: "Boot times and Shutdown times"
date: 2009-11-16
forum: The Cafe
---

### Post by the8thstar on 2009-11-16
Hello all,

I have two computers here.

#1 is a 2003 P4 2.4GHz, 1Gb of RAM, 80Gb of disk space, a 256Mb GeForce 6200 gfx and an additional external HD (500Gb)

#2 is a Core Solo which specs are featured in the signature below.


**_Boot times_**

For both computers, I started counting from the moment I pressed the power button and I stopped after the desktop had loaded AWN fully.

P4: 58s
Core Solo: 45s

I believe these figures are reasonable in this day and age with these somewhat dated computers.


**_Shutdown times_**

For both computers, I started counting from the moment I confirmed the Shutdown dialog box to the end of all activities (no more power).

P4: 6s
Core Solo: 15s

The figure for my old P4 amazed me. I'm wondering why my core solo lappy is slower... a power management issue maybe? SATA vs IDE HDs?


**_Questions_** :

1. Based on the same calculations, what are your boot times and shutdown times?
2. Any ideas why the P4 beats the Core Solo?

---

### Post by the8thstar on 2009-11-16
Is anyone interested?

---

### Post by Tamlynmac on 2009-11-16
Might I suggest this belongs in the Cafe.

It's likely to receive more responses in the Cafe than the T&E. Since it's really neither a testimonial or an experience. But more of a question regarding individual user boot/shutdown times and a request for member feedback.

Just my $0.02

---

### Post by solwic on 2009-11-16
> **Tamlynmac said:**
> Might I suggest this belongs in the Cafe.

It's likely to receive more responses in the Cafe than the T&E. Since it's really neither a testimonial or an experience. But more of a question regarding individual user boot/shutdown times and a request for member feedback.

Just my $0.02

+1.  Super Mod Powers, activate!

---

### Post by the8thstar on 2009-11-17
Alright then. Can any moderator kindly move my thread to the Community Cafe please? Thanks in advance.

---

### Post by Tamlynmac on 2009-11-17
I'd suggest you go [here]("http://ubuntuforums.org/forumdisplay.php?f=48") and ask a member of the staff to move your thread or simply edit it to show the word "Solved" and repost in the Cafe.

Good Luck

---

### Post by HappyFeet on 2009-11-17
I asked mod to move this thread.

---

### Post by armandh on 2009-11-17
power on is not a good starting place as it will include PNP bios searching, rather, when the grub starts the OS loading is a better place to measure the OS without the computer bios PNP work if any

---

### Post by cariboo on 2009-11-17
I would suggest using bootchart, it is in the repositories. The current versions adds 45 seconds to the boot time, but if you subtract that you should get a more accurate reading.

---

