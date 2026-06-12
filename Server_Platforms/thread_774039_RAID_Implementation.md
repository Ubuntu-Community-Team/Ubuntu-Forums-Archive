---
title: "RAID Implementation"
date: 2008-04-29
forum: Server Platforms
---

### Post by zosodemon on 2008-04-29
Hello everyone,

I am going to be attempting to use either RAID 5 or 10 on an Ubuntu server that's main purpose is to run postfix with Mailscanner, basically a SPAM Filter.  My questions to anyone with experience with Ubuntu Server and RAID is, what SATA Card would you recommend that would support at least 4-5 hard drives?  I looked at the lists on the forum with hardware that works and doesn't work but I couldn't seem to find much on what people recommend.  Any help and suggestions would be greatly appreciated.

---

### Post by geertn on 2008-04-29
If you go for hardware RAID any SATA Areca card is a great solution. I have bad experience with Adaptec. If you want hardware raid, make sure you buy a _real_ hardware raid solution. A lot of cheap cards are software raid in disguise and have a need for binary only modules. If you don't want to cash out for real HW raid, you'd better go with software raid.

---

### Post by Eddy Gordo from Tekken on 2008-05-16
what was your "bad experience" with Adaptec?

---

### Post by songshu on 2008-05-16
i have nothing bad to say about Hardware RAID cards, because my experience is that i do not need one.

if you have not considered or do not know the option, there is also a thing like Linux software RAID.

if you have a good RAID card you can be very happy with it and its a good choice, if you don't have a good one you are in big problems, there is no way in between.

with Linux RAID you always know what you get.

---

