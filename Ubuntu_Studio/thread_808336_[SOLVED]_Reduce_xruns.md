---
title: "[SOLVED] Reduce xruns"
date: 2008-05-26
forum: Ubuntu Studio
---

### Post by ezramorris on 2008-05-26
Hi,
I've just installed Ubuntu Studio (I actually had to install Ubuntu first, then upgrade to Ubuntu Studio). How do I reduced/eliminate the number of xruns on Jack? I am using the realtime kernel, and have followed the instructions here [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) .

Thanks in advance.

---

### Post by Stochastic on 2008-05-27
The best method to eliminate xruns is through trial and error.  Try different frames/period settings in qjackctl as well as sampling rates, and periods/buffer.  Also make sure the Realtime option is checked in qjackctl.  Really it's a balance you'll need to find for your computer between latency and xruns (though 1 xrun is too many in most pro circumstances).  The only other factor can be the overall load on your computer.

---

### Post by Drunky on 2008-05-27
Make sure you have upgraded to Ubuntu Studio properly before trying to use Jack in real-time.  I would suggest using the [UbuntuStudio/UpgradingFromHardy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy") web page on Ubuntu Help.

You will need the linux-rt to install the real-time kernel or you can't run Jack in real-time.  This is paramount if you want to reduce latency or x-runs.

---

### Post by ezramorris on 2008-05-27
Thanks for both your replies. I have the realtime kernel installed, and I knew that there were some options to adjust in qjackctl, but wasn't sure which.

Thank you.

---

### Post by robeast on 2008-05-27
I recently switched my window manager to fluxbox from gnome (with compiz-fusion) and have had much improved performance! Once you have things tuned as well as they can be in jack you may try a light weight window manager to free up some more memory and proc power.

---

### Post by Drunky on 2008-05-27
Here is a web page from Ubuntu Help again:
[How to Configure Jack]("https://help.ubuntu.com/community/HowToJACKConfiguration")

If you are having trouble with xruns try increasing Frames/Buffer.   This will increase latency but I believe it will help with xruns.

Also, I believe increasing Periods/Buffer will help with xruns.  Again this may increase latency.

---

### Post by ezramorris on 2008-05-30
> **Drunky said:**
> ... run Jack in real-time.  This is paramount if you want to reduce latency or x-runs.

Aha. I always forget this. I seem to assume that if I have the RT kernel installed, that's it. Problem solved. Thanks

---

