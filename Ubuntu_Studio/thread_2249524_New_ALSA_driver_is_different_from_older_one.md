---
title: "New ALSA driver is different from older one?"
date: 2014-10-22
forum: Ubuntu Studio
---

### Post by idaI_akatuY on 2014-10-22
Hello, I am quite new to this forum.

I have used ubuntu Studio 14.04 with mpd.
Help required!

I have updated MSB Technology USB 384 interface firmware from version 1.71 to version 3.30(latest).
Then I have experienced strange phenomena.

Environment: 
PC /  Core i7-3770 / Mem 8GB / HDD 250GB(SATA) / M/B: Asrock H77 MicroATX
OS and ALSA: see below
# uname -a
Linux ubst32x 3.13.0-32-lowlatency #57-Ubuntu SMP PREEMPT Tue Jul 15 04:23:12 UTC 2014 i686 i686 i686 GNU/Linux

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k3.13.0-32-lowlatency.

USB D/A converter:
 MSB Technology The Signature DAC-IV Plus with USB384 interface.
Amanero Combo 384 in LKS Audio ESS9018 dual DAC

Just after installation of ubuntu Studio 14.04:
- Installing mpd/mpc/gmpc and cifs-utils after apt-get update
Both DAC reproduced normally upto 352.8KHz24bit

Then I reboot the system:

After rebooting , 
MSB Technology DAC seemed to be able to  accept upto 352.8Khz...??Wow! but 0bit of data is displayed on MSB DAC display.
And NO SOUND from MSB DAC!
Oh, it might be something wrong I guessed, so I switched connection from MSB DAC to LKS Audio USB interface.
It worked properly!

And more,,,
When I boot from same PC with voyageMPD, which ALSA driver was old,old one ALSA 1.0.24?
MSB Technology DAC worked after problem with ubuntu Studio.

So I get MSB USB384 interface back to firmware version 1.71, then it worked with updated ubuntu Studio.
For Windows 8 or later we have to use version 3.3 firmware on MSB DAC, but with ubuntu Studio 
it cannot work properly yet. So I like to let USB384 version 3.30 work with ubuntu Studio 14.04 and mpd.

From these observation, there was made some critical change between 14.04 distribution verison ALSA modules
and updated ALSA modules.
Especially I suspected probing bit length feature of USB DAC was modified or different timing code , it has.

Please tell me how to treat this problem.

Yutaka IIDA, AEDIO Japan

---

