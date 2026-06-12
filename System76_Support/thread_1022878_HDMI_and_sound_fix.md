---
title: "HDMI and sound fix"
date: 2008-12-27
forum: System76 Support
---

### Post by Lee_Machine on 2008-12-27
So I was reading about Ubuntu 9.04 and apparently there is a new alsa driver 1.0.18 which adds support for sound with HDMI on nvidia cards. It will be included in the next release.

It's been out since November and at first it pissed my off why S76 has not pushed it out in the S76 drivers or posted a howto.

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

I updated alsa and at first I thought it was going to be easy but there was a lot to it. But I can confirm that HDMI sound does work now. 


Here is the changelog that confirms the added support for alsa and HDMI with nvidia.

[http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18](http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18)

The how to for compiling the new driver is here

[http://alsa.opensrc.org/Quick_Install](http://alsa.opensrc.org/Quick_Install)

So for those that don't want to mess with this, just wait until Ubuntu 9.04 and it will work. 

Hopefully the new version will be pushed but probably not as I read that the Ubuntu team wants to focus on stability and get all the bugs worked out.

Now if I could just get eSATA to work all the time then all the ports that my Pangolin has will work :lolflag:

Hope this helps for someone else. I'm sure glad I can use my laptop on my TV.

Update: Here is the changelog for Jaunty and it confirms the added alsa 1.0.18

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December.txt.gz](https://lists.ubuntu.com/archives/jaunty-changes/2008-December.txt.gz)

---

### Post by val67 on 2008-12-27
I thought all this work should be transparent to us users by running the system76 driver.

I am pretty disappointed that S76 doesn't take care of this and ships computers with hardware not fully functional.

---

### Post by Lee_Machine on 2008-12-27
> **val67 said:**
> I thought all this work should be transparent to us users by running the system76 driver.

I am pretty disappointed that S76 doesn't take care of this and ships computers with hardware not fully functional.

I was pretty shocked when I found out that sound does not work with HMDI. What other use is there for HDMI other than for watching movies on a TV with HDMI? Yes, you can use the headphone port to go to speakers, or use Bluetooth speakers, but I'd just rather use the TV speakers.

I understand that S76 does not control ALSA but why sell a laptop with HMDI if it doesn't work? Knowing that it will in the future is even ok but put a disclaimer on the website. 

In the end it will be fixed in two ways S76 adds it to the driver (and they should) or most users will have to wait until April for Jaunty.

---

