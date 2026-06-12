---
title: "How I solved my video tearing/HDMI/MTS/NLE support"
date: 2009-08-30
forum: Testimonials &amp; Experiences
---

### Post by Geekkit on 2009-08-30
I sold my PC running Linux and bought a Mac. Problem solved. :)

Seriously, my time is worth more than that. Also, launchpad's biggest bug is itself.

---

### Post by 3rdalbum on 2009-08-30
Ha. The Mac OS doesn't even have video playback acceleration on the graphics card. Good luck trying to play any 1080p content on the Mac without video tearing and loss of sync.

I agree about Launchpad, I always struggle with it.

---

### Post by hansdown on 2009-08-30
You sold a PC running gutsy?

You my friend are undoutebly a master merchant.

---

### Post by Geekkit on 2009-08-30
> **3rdalbum said:**
> Ha. The Mac OS doesn't even have video playback acceleration on the graphics card. Good luck trying to play any 1080p content on the Mac without video tearing and loss of sync.

Wrong. My Macbook Pro with the NVIDIA GeForce 9400M supports it fully and doesn't even blink while delivering. It's like a new world. HDMI with my 52" Sony LCD TV also looks amazing (and actually works).

Seriously, I wish Canonical and all the other distro makers the best. But until they and all the OSS developers stop seeing proprietary software and their producers as the enemy, they'll go nowhere and they'll do it fast.

Anyways, as so many in the forums say: use what works ... and that's what I'm doing.

Cheers.

---

### Post by hansdown on 2009-08-30
Go peacefully Geekkit.

Best of luck to you.

---

### Post by 3rdalbum on 2009-08-30
> **Geekkit said:**
> Wrong. My Macbook Pro with the NVIDIA GeForce 9400M supports it fully

I stand corrected as of the release of Snow Leopard. My information was a couple of days out of date. Still, it only handles H.264 (Apple's pet format).

VDPAU handles H.264, VC1 and WMV with acceleration on the card. Most Blu-rays are VC1, which puts Linux at the video playback advantage.

---

### Post by Geekkit on 2009-08-30
> **3rdalbum said:**
> I stand corrected as of the release of Snow Leopard. My information was a couple of days out of date. Still, it only handles H.264 (Apple's pet format).

VDPAU handles H.264, VC1 and WMV with acceleration on the card. Most Blu-rays are VC1, which puts Linux at the video playback advantage.

Sorry to be a pedant but H.264/MPEG-4 AVC is the Motion Picture Expert Group's "pet format" not Apple's. Whoever wishes to adopt it as a standard can do so - and many have (including Apple).

You've said that "Most Blu-rays are VC1" but unless you've got some reference for statistics, that's simply here say and nothing more. In fact, if you visit [http://bluray.highdefdigest.com](http://bluray.highdefdigest.com), you'll come across numbers that appear to be about equal. Out of my Blu-ray collection (couple dozen), about 2/3 of my disks are H.264/AVC MPEG-4.

Also, you've stated that VC-1 "puts Linux at the video playback advantage", which I find being an odd statement to make. Both VC-1 and H.264/AVC MPEG-4 are full of patents, proprietary/corporate support. In fact, VC-1 is Microsoft's "pet format" so I am not sure how Linux winds up at any advantage at all with VC-1.

Lastly, it will be interesting to see where VDPAU goes. After all, it is closed source and only supports NVidia hardware - not very conducive towards OSS (at least from the opinion coming from many of OSS proponents that I've interacted with).

---

### Post by 3rdalbum on 2009-08-31
> **Geekkit said:**
> Sorry to be a pedant but H.264/MPEG-4 AVC is the Motion Picture Expert Group's "pet format" not Apple's. Whoever wishes to adopt it as a standard can do so - and many have (including Apple).

Oh yes, I wasn't trying to say that H.264 was created by Apple. They're just its biggest supporters.

> You've said that "Most Blu-rays are VC1" but unless you've got some reference for statistics, that's simply here say and nothing more. In fact, if you visit [http://bluray.highdefdigest.com](http://bluray.highdefdigest.com), you'll come across numbers that appear to be about equal. Out of my Blu-ray collection (couple dozen), about 2/3 of my disks are H.264/AVC MPEG-4.

Heh, about 2/3 of mine are VC1.

> Also, you've stated that VC-1 "puts Linux at the video playback advantage", which I find being an odd statement to make. Both VC-1 and H.264/AVC MPEG-4 are full of patents, proprietary/corporate support. In fact, VC-1 is Microsoft's "pet format" so I am not sure how Linux winds up at any advantage at all with VC-1.

Because it can play them with GPU acceleration.

> Lastly, it will be interesting to see where VDPAU goes. After all, it is closed source and only supports NVidia hardware - not very conducive towards OSS (at least from the opinion coming from many of OSS proponents that I've interacted with).

Apparently Intel is going to adopt it as well.

---

