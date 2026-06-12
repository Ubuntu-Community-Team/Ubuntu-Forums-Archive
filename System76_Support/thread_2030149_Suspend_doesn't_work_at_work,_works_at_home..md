---
title: "Suspend doesn't work at work, works at home."
date: 2012-07-20
forum: System76 Support
---

### Post by afilonov on 2012-07-20
Confuses me a lot. I can suspend/resume my laptop at home as many times as I want, works perfectly.
At work I can resume with no problem, but suspend doesn't work. I'm getting huge kernel dumps in syslog, and then getting back. Laptop doesn't hang, just refuses to suspend. Yes, sometimes I have the same problem at home, but second attempt usually works.

Laptop is System76 Gazelle performance black (GAZP2), Ubuntu 10.04, current updates:


uname -a
Linux gazelle 2.6.32-41-generic #91-Ubuntu SMP Wed Jun 13 11:44:43 UTC 2012 i686 GNU/Linux

Kernel dumps look like this (this is only the beginning, hundreds of lines follow):

Jul 17 17:28:23 gazelle kernel: [430110.077156] PM: Preparing system for mem sleep
Jul 17 17:28:23 gazelle kernel: [430110.077162] Freezing user space processes ... 754>] kthread+0x74/0x80
Jul 17 17:28:23 gazelle kernel: [430130.102223]  [<c01686e0>] ? kthread+0x0/0x80
Jul 17 17:28:23 gazelle kernel: [430130.102227]  [<c0104087>] kernel_thread_helper+0x7/0x10
Jul 17 17:28:23 gazelle kernel: [430130.102230] crypto/1      S 00000000     0 17143      2 0x00000000
Jul 17 17:28:23 gazelle kernel: [430130.102236]  d6975f88 00000046 d6976000 00000000 00000000 c0850760 e0361c24 c0850760
Jul 17 17:28:23 gazelle kernel: [430130.102244]  67fe61f8 00016ee1 c0850760 c0850760 e0361c24 c0850760 c0850760 c0777a00
Jul 17 17:28:23 gazelle kernel: [430130.102253]  00000001 00016ee1 e0361980 e0361980 e0361980 c1e0b94c d6975fb8 c0164a75
Ju

---

### Post by 3Miro on 2012-07-23
What is different between home and work?

- different wireless networks, maybe using different encryption which loads different kernel modules.

- external monitor perhaps.

- some program or another that is mostly used at work and is causing the issue with suspend.

---

### Post by afilonov on 2012-07-23
> **3Miro said:**
> What is different between home and work?

- different wireless networks, maybe using different encryption which loads different kernel modules.

- external monitor perhaps.

- some program or another that is mostly used at work and is causing the issue with suspend.

Yes, wireless networks are different. No programs which are used at work but not at home. One subtle difference: at home I sometimes connect to NFS disks. NFS is never used at work.
No external monitor at either location.

---

### Post by isantop on 2012-07-24
> **afilonov said:**
> Yes, wireless networks are different. No programs which are used at work but not at home. One subtle difference: at home I sometimes connect to NFS disks. NFS is never used at work.
No external monitor at either location.

Do you suspend more frequently at work than you do at home? What you're seeing may not actually be a difference.

---

### Post by afilonov on 2012-07-25
Figured it out. It's NFS. I suspended laptop at home, with NFS disks mounted. Then I thought I unmounted them (forced) at work, but one of them still got stuck in mtab. Once I cleared it out, suspend works at work flawlessly.

---

