---
title: "Playback While Recording"
date: 2009-01-17
forum: Ubuntu Studio
---

### Post by cinajohn on 2009-01-17
OK so, I have been quite successful (with help from the community) in getting my sound working properly for my M-Audio Audiophile 192.  

The last frontier is that I cannot seem to get "play through" from the input.  The only time it has working is under jack and making a connection in patchage.  

To be honest I do not want to use jack, as the only 'studio' type function I need is to be able to record simple .wav's from an input, and I think that getting all my other programs jack aware would be more of an issue.  

alsamixer just gives me two controls, one master and one capture, which are both up, and the gnome ALSA mixer doesn't really give me any options.

Any help or suggestions would be greatly appreciated.:)

Also, I can't seem to arecord any 24 bit format.  16 and 32 bit are fine but any 24 bit setting returns 'set_params:954 Sample format not available'

---

### Post by kamlapati on 2009-01-20
Sorry I can't help, but at least I can bump your request.

I had the same problem a month ago. In the course of my research I found that ALSA does not even claim full support for the card. See here:

[URL="http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio"]


I finally opted for a different card, but would love to hear from anyone that got full functionality out of the AP192.

---

### Post by cinajohn on 2009-01-25
Thanks.

I would be curious to know what sound card you ended up with and how you fared with it.

---

