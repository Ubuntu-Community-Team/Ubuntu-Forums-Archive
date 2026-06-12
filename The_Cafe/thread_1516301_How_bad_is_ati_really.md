---
title: "How bad is ati really?"
date: 2010-06-23
forum: The Cafe
---

### Post by mamamia88 on 2010-06-23
I am looking to put together a cheap htpc.  i'm in the process of shoppig for deals and came across this.  [http://www.newegg.com/Product/ComboDealDetails.aspx?nm_mc=AFC-SlickDeals&cm_mmc=AFC-SlickDeals-_-NA-_-NA-_-NA&ItemList=Combo.428295](http://www.newegg.com/Product/ComboDealDetails.aspx?nm_mc=AFC-SlickDeals&cm_mmc=AFC-SlickDeals-_-NA-_-NA-_-NA&ItemList=Combo.428295)  it's out of stock right now but i'm hoping it comes back into stock later.   so what do you think will it work decently in ubuntu?  i've only had experience with nvidia in ubuntu

---

### Post by Brent0 on 2010-06-23
My HD5770 works great in Ubuntu. I have had no problems at all. I think most of the anti-ATI talk is from past experiences with the drivers.

---

### Post by Zerocool Djx on 2010-06-23
I use ati and originally got a bare bones kit from tigerdirect.com.. Works fine for me.. I got my whole system, minus monitor, for about $350... works flawless for me..

---

### Post by undecim on 2010-06-23
It's always worked fine for me. Recent driver updates have really improved.

If you don't do a lot of 3d gaming, you can stick with open source drivers, too.

---

### Post by mamamia88 on 2010-06-23
allright cool guys thanks.  one more question will the integrated nvidia card pose any problems mixing with the ati card?

---

### Post by LowSky on 2010-06-23
My HD 4550 works pretty well. Sure ATI doens't have VDPAU suppport but most modern desktop CPU's can handle a video with ease.
> **mamamia88 said:**
> allright cool guys thanks.  one more question will the integrated nvidia card pose any problems mixing with the ati card?
Shouldn't be one problem at all. The PCI express slot will gain control over video. If you even want to you can disable the onboard video from the BIOS, but you really dont have to.

---

### Post by alket on 2010-06-23
I have ATI Readon x700 which is not supported, but the Open Source alternative is good, i can run all games except Glest, Yoo Frankie (OpenGL based) which run slow. For games like Urban Terror, OpenArena 9/10

---

### Post by Penguin Guy on 2010-06-23
I'm using an ATi Radeon 3850 and it's okay for average desktop use, but doesn't work with hibernation or any of my Wine games.

---

### Post by doorknob60 on 2010-06-23
It's not terrible, though a few things can still be problematic sometimes (like Wine). For the most part though, the drivers are pretty good.

---

### Post by Zerocool Djx on 2010-06-23
> **LowSky said:**
> My HD 4550 works pretty well. Sure ATI doens't have VDPAU suppport but most modern desktop CPU's can handle a video with ease.

Shouldn't be one problem at all. The PCI express slot will gain control over video. If you even want to you can disable the onboard video from the BIOS, but you really dont have to.

I got that same card... Mine works fine...

---

### Post by WRDN on 2010-06-23
The ATI drivers have improved significantly over the last few years, for the most part. I am using the latest Catalyst driver (10.6), and it works very well - there was some trouble with the installation, as the first time, I didn't generate a distro specific package from the driver installer, and it caused problems (nothing serious).

Further, the drivers are now mature enough that I am about to do my final year university project using the ATI Stream technology - for those that don't know about this, it is so you can perform GPGPU, or general purpose programming on the graphics card. I will be using OpenCL to write a GPU ray tracer, as opposed to the proposed library to be used for the project, CUDA (NVIDIA GPGPU).

---

### Post by kamaboko on 2010-06-23
My ATI card works great.  Something to consider though.  If you're hooking up to surround sound and your receiver does Dolby True-HD, you may want to hold off for motherboards that will handle that.  Only a few at the moment do, but not great.  Don't know if you've looked into it or it's important to you.

---

### Post by doas777 on 2010-06-23
the driver version in lucid is finally up to snuff for my needs with Lucid. with karmic and prior it has been a real pain, but it appears that they are making some good progress lately.

by the same token, my nvidia card in one (newly lucid) box finally has overscan control for the TV out, so improvements across the board.

---

### Post by chris200x9 on 2010-06-23
I have a mobile 5650 I don't really game but it can run armagetron near 100 fps with the open source drivers :)

---

### Post by BuffaloX on 2010-06-23
I have a Radeon 4770 and use open source driver in Lucid.
I don't do much gaming in Linux, but the Humble Indie Bundle games all work great for me. Even with Compiz enabled.

The bootup animation doesn't work yet, but that's a very small issue IMO.
I think it works with proprietary drivers, but I haven't tried it.

Nvidia supports old cards better with their closed drivers, and AFAIK they work better with Wine, so I guess it depends on what you want.

---

### Post by K.Mandla on 2010-06-23
> **Brent0 said:**
> I think most of the anti-ATI talk is from past experiences with the drivers.
+1. Old rumors die hard.

---

### Post by sixstringmonk on 2010-06-23
The only thing that bothers me about ATI drivers at the moment is that there is a vsync issue in 2d rendering. This means that there is tearing in video playback. There is a work around for this issue if you use mplayer. However, moving windows with desktop effects produces a lot of tearing. I'm sure that some people don't mind it so it depends how picky you are.

Outside of that one issue, I've found the recent ATI drivers to be very stable.

---

### Post by mr clark25 on 2010-06-23
wow, that looks like a good deal.

mind me asking if you plan to overclock and what cpu you plan to put in it?

---

### Post by proggy on 2010-06-23
i have ati hd 4850 i have all the compiz effects (cube and can watch video at the same time with no slowdown) ati drivers are excellent

---

### Post by Paqman on 2010-06-24
> **LowSky said:**
> Sure ATI doens't have VDPAU suppport but most modern desktop CPU's can handle a video with ease.


For an HTPC, which is presumably outputting at 1360x768 or higher, you're going to want VDPAU. I have an HTPC with a 2.5GHz dual-core chip, and playback on 720p or greater video isn't quite smooth enough to be enjoyable without VDPAU switched on.

---

### Post by alexan on 2010-06-24
It is no longer fair say "bad", but you must consider that ATI tend quickly to drop support for older boards: in this way they can "concentrate" the economical effort to justify improvement for linux users.
If you plan ati, I do suggest you consider +HD5xxx or wait for the next generation of ATI

---

### Post by Lucradia on 2010-06-24
I have a Mobility Radeon HD 58xx... and compiz causes the system to slow to unbearable levels.

gtk-recordmydesktop also does the same, only worse, because I can't click on anything to stop the issue for about 2-3 minutes. (it's slightly less if I run recordmydesktop from terminal.)

Windows though, CamStudio works wonders.

---

### Post by doas777 on 2010-06-24
> **Paqman said:**
> For an HTPC, which is presumably outputting at 1360x768 or higher, you're going to want VDPAU. I have an HTPC with a 2.5GHz dual-core chip, and playback on 720p or greater video isn't quite smooth enough to be enjoyable without VDPAU switched on.

has VDPAU finially become a "switch" you can just toggle? last time i checked (a few versions back) it required a special version of the drivers and client apps from PPA's, only worked with the mplayer backend, required manual config, etc.

I just noticed the other day that SMplayer has a simple output driver dropdown that you can select VDPAU from. is it really as simple as selecting it in the client app now? or is smplayer giving me an option I can't use, and failing back to 'XV' under the hood?

---

### Post by rajeev1204 on 2010-06-24
> **Lucradia said:**
> I have a Mobility Radeon HD 58xx... and compiz causes the system to slow to unbearable levels.

gtk-recordmydesktop also does the same, only worse, because I can't click on anything to stop the issue for about 2-3 minutes. (it's slightly less if I run recordmydesktop from terminal.)

Windows though, CamStudio works wonders.


Please try the new catalyst 10.6 . The difference with or without compiz is significant.

---

### Post by KdotJ on 2010-06-24
I have an ATI Radeon HD 3200 in my laptop. It's not great for new games but in ubuntu in works fine.

Desktop effects and 3D acceleration works fine with no problems. Infact, as of 10.04 I have been using the open-source drivers and not needed to use the proprietary ones to use effects

---

### Post by Paqman on 2010-06-24
> **doas777 said:**
> is it really as simple as selecting it in the client app now?

Yep. Latest Nvidia drivers are good-to-go for VDPAU. I think I might have had to install a supporting package from the repos if memory serves, but other than that it was just a matter of switching it on in the app (XBMC in my case).

---

