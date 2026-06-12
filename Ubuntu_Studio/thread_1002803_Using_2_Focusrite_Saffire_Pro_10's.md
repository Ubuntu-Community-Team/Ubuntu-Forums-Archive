---
title: "Using 2 Focusrite Saffire Pro 10's"
date: 2008-12-05
forum: Ubuntu Studio
---

### Post by ecullerton on 2008-12-05
Greetings!

I'm using 2 Focusrite Saffire pro 10's, with ffado 2rc1, in Ubuntu Studio 8.04.

Does anyone have any experience with this setup?

I have made excellent progress, but I would like to see if others have made similar progress.  I would also like to fine tune all the settings to get the best out of my system.

To summarize my setup:

Intel DP35DP motherboard (using onboard firewire)
Intel Q6750 Core Duo 2.66GHz CPU
EVGA 8600GTS 512MB
4GB Corair DDR2 800 MHz Memory

Ubuntu Studio 8.04 (64 bit)
FFADO 2.0 rc1
ARDOUR 2.7.1
Jack 0.115.6

If anyone has any suggestions for hardware improvements, I would greatly appreciate it. (Especially on the memory)

I used the ubuntu studio controls to set the raw1394 permission, and the memory allocation to 75%.

I checked /etc/security/limits.conf to see that the rtprio and memlock were there.  I added a nice value of -10


I have been experimenting with latency values, using qjackctl.  I'm running at 96000 Hz.  I found that 64 frames works best.  The periods/buffer is good between 3-14.  I have the realtime box checked.  The Priority is left as (default).

Does anyone know what the Priority value means?

I tried 128 Frames/Period, with between 3-6 Periods/Buffer.  I had a few xruns with this config.

I experienced major jack problems after changing the settings.  I needed to cycle the power for both pro 10's to make it work again.  I found that cycling the power before each settings change had the best results.  I also found that jack completely froze a few times after changing the settings, which required me to kill the jackd process.  Occasionally things got bad enough I had to restart the computer. (Broken pipes errors?)

With the settings at 64 frames/period, 4 periods/buffer, 96000Hz, I was able to record 20 tracks on Ardour simultaneously for 2 hours.  I haven't tested beyond that at this point, but I plan to test with heavier loads in the future.

I feel that the set up is pretty good, but I want to push things further if possible.

Does anyone know of any settings I can use to make thing better? IRQ stuff?

I'd be happy to help anyone configure their setup too!

Thanks,
Ed

---

### Post by kayosiii on 2008-12-06
I have found that the firewire chipset can have a big impact on performance... The TI chipset I have now works a lot better than theVIA chipset I had previously. Sounds like you are getting pretty good results though. (using a single firepod here)

---

### Post by ecullerton on 2008-12-08
Thanks for the info.  It looks like the intel board has a TI chip in it, which is good.

As I do more research, I see that there is a lot of support for 64 studio, and I hear that it is a leaner system geared to audio.  I tried this on my machine, but it lacked some critical software that I want on my machine.

My question is, how can we make Ubuntu Studio as lean as 64 studio, or is this just a myth??? 

Thanks!

---

