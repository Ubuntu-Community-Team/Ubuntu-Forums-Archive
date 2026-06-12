---
title: "libva-intel-vaapi-driver should be installed on newer System76es"
date: 2012-07-05
forum: System76 Support
---

### Post by jakobcreutzfeldt on 2012-07-05
Just a quick heads-up to the System76 guys, I noticed that my gazp7 didn't come with libva-intel-vaapi-driver installed by default. Since all new System76 computers come with Intel HD graphics, I'd say that it should be installed! Actually, I think almost any recent system which uses Intel graphics should have it installed, since it provides hardware video decode/encode:

[quote=Synaptic Package Manager]The VA-API (Video Acceleration API) enables hardware accelerated video decode/encode at various entry-points (VLD, IDCT, Motion Compensation etc.) for the prevailing coding standards today (MPEG-2, MPEG-4 ASP/H.263, MPEG-4 AVC/H.264, and VC-1/VMW3). It provides an interface to fully expose the video decode capabilities in today's GPUs.

This package contains the video decode & encode driver backend for the Intel G45 chipsets and Intel HD Graphics for Intel Core processor family.[/quote]

Or is there a certain incompatibility or complication that I should know about....?

---

### Post by jakobcreutzfeldt on 2012-07-05
Hmm...there should be a "?" in that title. Nobody likes a know-it-all :P

---

### Post by brdmn on 2012-07-05
> **jakobcreutzfeldt said:**
> Just a quick heads-up to the System76 guys, I noticed that my gazp7 didn't come with libva-intel-vaapi-driver installed by default. Since all new System76 computers come with Intel HD graphics, I'd say that it should be installed! Actually, I think almost any recent system which uses Intel graphics should have it installed, since it provides hardware video decode/encode:



Or is there a certain incompatibility or complication that I should know about....?

Have you installed it?  Curious to hear about any possible improvements you've seen on your system.  My lemU4 seems to be fine, but if there were a noticeable benefit, I'd consider installing this driver.

---

### Post by jakobcreutzfeldt on 2012-07-05
I just installed it this morning. I'll give it a try tonight.

As I understand it, you need to use a player that supports it to derive the benefits. I know that VLC Player and Mplayer both support VAAPI. It'll probably mostly make a difference with HD video and possibly Flash video.

re: Flash, from the Arch Linux wiki on [Intel video](https://wiki.archlinux.org/index.php/Intel#Hardware_video_acceleration):
 > To enable hardware video decoding in flash, add EnableLinuxHWVideoDecode=1 to /etc/adobe/mms.cfg. If hardware video decoding is still not working, you can also try adding OverrideGPUValidation = 1.

---

