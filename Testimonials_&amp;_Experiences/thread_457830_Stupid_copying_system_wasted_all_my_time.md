---
title: "Stupid copying system wasted all my time"
date: 2007-05-29
forum: Testimonials &amp; Experiences
---

### Post by capdog on 2007-05-29
This just floors me... a friend came round to copy about 10 gigs onto her IPod. Using Kubuntu, I did all the copying which went flawlessly, over the period of about an hour, small files at a time. Then she needed to go, and I went to eject the device.

KDE comes up with a "Progress..." dialog, which just stays at 0%. This just sat like this for 15 mins, not moving, apparently not doing anything. So I clicked "cancel" and then went to eject the device again.

My friend got home and found that half the files hadn't copied! 

How stupid is this behaviour on the part of Kubuntu! 1) The files should copy when IT SAYS "COPYING" and 2) If it does leave the "actual copy" until right before you need to go, THE PROGRESS BAR SHOULD MOVE BEYOND 0%! 

Stupid, moronic system. :(

---

### Post by wolfen69 on 2007-05-29
if it's a stupid, moronic system, the Devil's OS is always there for you.

---

### Post by capdog on 2007-05-30
> **wolfen69 said:**
> if it's a stupid, moronic system, the Devil's OS is always there for you.

The copying system is what is moronic, the system as a whole is fine. Well, most cases anyway. Often I just want to switch back to XP.

---

### Post by wolfen69 on 2007-05-30
go back to xp. its cool, if it wasnt for windows users i wouldnt have a job

---

### Post by wolfen69 on 2007-05-30
ive become somewhate of a linux  evanjelist. i fix windows for a living. i hate it
 linux makes sense.

---

### Post by hellmet on 2007-05-30
Getting back to XP is not the solution!! We wouldn't have been here if we wanted to get back to XP..

---

### Post by wolfen69 on 2007-05-30
i'll never go back to windows

---

### Post by capdog on 2007-05-30
Been using Ubuntu for almost a year now, and I have to split my tasks between XP and Ubuntu. This IPOD thing just irritates me because it's something so simple and trivial - copying files - and now it's another thing that I have to boot into Windows for.

The others are syncing my phone, video editing, iTunes for IPOD updates and now all IPOD related activities I think.

When I have to spend 20 hours getting my widescreen monitor to work at native resolution, for some reason this doesn't bother me.

But when a simple day-to-day operation goes wrong, that makes me furious. It's such a simple requirement to copy files, why is it handled so badly?

---

### Post by anaconda on 2007-05-30
It is possible to use cp so that it will copy things right away and even to get a process "bar" for it.. I just dont remember the reguired options....

EDIT. Just checked man cp, and there wasnt such option! must have been some other terminal program...

---

### Post by 3rdalbum on 2007-05-30
It doesn't "leave the copying until right before you go". It copies in the background. It fills up the memory cache with source data while transmitting to the destination. The copying operation returns when there is no more source data to be placed in the memory cache. If it waited until the copying had completely finished, then you wouldn't be able to eject the source OR the destination until all the data had copied.

I'm not familiar with KDE, but I know that Windows uses a much slower method called "sync". If you had used Windows to copy the files, you would have had less than half the files on the iPod when she left. Windows only uses the Linux way when you have a small amount of data copying again and again to different destinations; I bet few people here knew that, that's how rare it is!

---

