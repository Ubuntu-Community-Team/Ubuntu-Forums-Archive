---
title: "Really low entropy"
date: 2010-02-14
forum: Security
---

### Post by acidcortex on 2010-02-14
I have a problem with really low entropy on four servers running ubuntu server 8.04.4
Hardware is:
Intel server board s3210shlx, Intel Xeon E3110, 64G SSD drive - servers 1 and 2
Intel server board s3210shlx, Intel Core2Quad Q6600 3x500G IDE drive - servers 3 and 4

First two servers won't get etropy_avail over 100.
Other two hold it between 200 and 300.

Previously, one of these servers had Intel EP45 Extreme mainboard and had the entropy over 2000. I only swapped the board (with intel 3210) and the entropy dropped to 200-300.

Tried rng-tools, but in intel-rng driver says:
FATAL: Error inserting intel_rng (/lib/modules/2.6.24-26-server/kernel/drivers/char/hw_random/intel-rng.ko): No such device

Intel says that this motherboard has embedded RNG device, but doesn't offer any kind of driver or support for linux kernel.

Servers have no keyboards or mice and my guess is that servers 3 and 4 can draw some entropy from ide drives, but SSD doesn't produce any entropy in servers 1 and 2.

Consequently some operations, that use the entropy pool, take a lifetime.

Any help or advice is appreciated.
Thanks

---

### Post by falconindy on 2010-02-14
There's some audio and video related entropy generation daemons. [Randomsound]("http://packages.ubuntu.com/hardy/randomsound") is one of them, and relies on ALSA.

---

### Post by acidcortex on 2010-02-14
> **falconindy said:**
> There's some audio and video related entropy generation daemons. [Randomsound]("http://packages.ubuntu.com/hardy/randomsound") is one of them, and relies on ALSA.

I know that, but 1U cases, no soundcards on server boards, no room for riser cards....
This seems like cheaper and more reliable solution [http://www.entropykey.co.uk/](http://www.entropykey.co.uk/) than soundcard.
But I'm looking for a way to use Intel's embedded RNG or draw more entropy for network jitter or something I have in servers.

Thanks anyway ;)

---

