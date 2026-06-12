---
title: "Avast fps"
date: 2012-10-27
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-10-27
I was just doing some housekeeping and found that Avast reports .iso files as decompression bombs :) lol I had not noticed this behaviour in stable releases.

---

### Post by VinDSL on 2012-10-28
I've only run across one (1) virus using avast! and that was back in 2011.  Still, it doesn't hurt to check your rig, from time-to-time.

I'm not worried about Linux et al. but I don't want to send malware to my winders friends -- poor souls.  They have enough problems.


As far as "compression bombs", so called, are concerned...


SOURCE:  [http://forum.avast.com/index.php?topic=32981.0](http://forum.avast.com/index.php?topic=32981.0) (avast! moderator reply)
> 
Compression bomb doesn't mean "this is malware". It says only that the compression ratio of the object is higher than some threshold, and that further decompression would lead to memory exhaustion.

Some time ago, older zlib-based squashfs was quite popular as compressed FS for live distributions. That's why avast! might consider its parts  worth of decompressing (gunzipping) and this warning is issued. It's normal behavior .

Regards,
PC


Not to worry, I judge!  ;)

---

### Post by ventrical on 2012-10-28
I tried the new Comodo AV for Linux, downloaded the EICAR test file and that worked OK. Avast has worked great so far, especially with my IDE to USB converter on used Windows hdds and etc..  The CAV for Linux (Debian) also  provides real time scanning but. of course, that part is not working properly.  I'll try to see if I can get that working with Thunderbird.

---

