---
title: "Mic not working in Ubuntu 12.04 Beta 2 - Lenovo G470"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by caveman7 on 2012-04-15
Hi all. I used a Lenovo G470 laptop (Core i5 2410M processor, AMD Radeon 6370M and 2GB DDR3 RAM) and I installed Ubuntu 12.04 Beta 2.
I can't get the microphone to work. I encountered this type of issue before in my old Acer Aspire One with Ubuntu 10.04/10.10, and installing PulseAudio Volume Control and tweaking a little solves the problem. I tried the same solution to no avail.

cat /proc/asound/card0/codec* | grep Codec gives the following result:
Codec: Conexant CX20590
Codec: Intel CougarPoint HDMI

Does anybody encountered a similar problem? Any help will be greatly appreciated.

---

### Post by caveman7 on 2012-04-15
anybody?:confused::confused:

---

### Post by adamjomha on 2012-04-15
Same here, with a Sony Vaio vpceb27fd from 11.10 to 12.04. Mic worked before, its not muted in alsamixer but when I open sound settings I show no device under input. External speakers work, and headphones do not.

I was hoping these sound issues would have been less of an issue. I know its still beta, but only a few days away from a real release..

---

### Post by treesurf on 2012-04-15
Here is the page describing how to report audio bugs:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

And this one may be useful as well:

[https://wiki.ubuntu.com/Audio](https://wiki.ubuntu.com/Audio)

---

### Post by iniquiTrance on 2012-04-25
Also reporting the same issue on a Dell XPS 14. Everything was working fine in Oneiric.

---

### Post by caveman7 on 2012-04-25
> **iniquiTrance said:**
> Also reporting the same issue on a Dell XPS 14. Everything was working fine in Oneiric.

hopefully this will be fixed in the final release

---

