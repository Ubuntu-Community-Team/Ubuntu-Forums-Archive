---
title: "Which sound card to buy"
date: 2010-02-03
forum: System76 Support
---

### Post by dabrowsa on 2010-02-03
Ubuntu 9.10
Wild Dog

I'm giving up trying to get all the jacks on my current sound card working properly.  What new sound card should I buy?  

To repeat: it is essential that _all_ the jacks function under Ubuntu.  I don't care which flavor, [KX]*ubuntu, I can deal.  I can install or uninstall pulseaudio, as long as the hardware works properly.

---

### Post by jdb on 2010-02-03
> **dabrowsa said:**
> Ubuntu 9.10
Wild Dog

I'm giving up trying to get all the jacks on my current sound card working properly.  What new sound card should I buy?  

To repeat: it is essential that _all_ the jacks function under Ubuntu.  I don't care which flavor, [KX]*ubuntu, I can deal.  I can install or uninstall pulseaudio, as long as the hardware works properly.

I've just done some testing on a desktop with an MSI G31M3 motherboard
which has onboard Realtek ALC888 audio.

Audio coming in the line-in comes out of line-out uninterrupted.
When I record using Audacity, the recording freezes up after a short
while in Ubuntu using pulse audio.
In Arch Linux using alsa it records longer but eventually freezes.

I know there was a time when recording worked flawlessly on this computer,
but I'm not sure if it was before or after this motherboard.

jdb

---

### Post by thomasaaron on 2010-02-03
I just posted this here...
[http://ubuntuforums.org/showthread.php?t=1394368&page=2](http://ubuntuforums.org/showthread.php?t=1394368&page=2)

...but for the sake of completion...

> OK, I just spoke called up Intel and asked them about this. Here's what they said...

1. speaker out to mic jack -- this will definitely NOT work.
2. speaker output to line in jack -- in theory, this should work, but (and this surprised me) they do not test it and could not guarantee it would work.

So, as we move forward with this, please realize that it may or may not even be possible on the Wild Dog's motherboard.

(I saw another post where you are looking for a sound card. Do you want me to continue?)

We do not have a list of sound cards that work with Ubuntu. This thread...
[http://ubuntuforums.org/showthread.php?t=589692](http://ubuntuforums.org/showthread.php?t=589692)
...points to...
[http://www.m-audio.com/products/en_gb/Audiophile2496.html](http://www.m-audio.com/products/en_gb/Audiophile2496.html)

Here is another list of cards to investigate...
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

---

