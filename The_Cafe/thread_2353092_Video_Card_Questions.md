---
title: "Video Card Questions"
date: 2017-02-18
forum: The Cafe
---

### Post by eddiefiggie on 2017-02-18
So,

Something I've not tinkered with and something I know very little about.  Video Cards!!

Does UBUNTU run well with Vulcan(API)?  I'm debating between purchasing an NVIDIA card and an AMD card.  Do you have thoughts or recommendations on how these technologies will work with Ubuntu 16.04?  Issues, successes, etc?  Any insight would be helpful.

It's a _**generalist**_ machine...  Work, school, with some gaming as well...  minor video stuff...etc.

---

### Post by wildmanne39 on 2017-02-18
*Thread moved to **The Cafe**.*

---

### Post by QIII on 2017-02-18
I have an AMD card (R9 380X) running AMDGPU-PRO with Vulkan support.  It is working very well.

However:  I am running 16.10 with a supporting kernel and my GPU is GCN 1.2.  This means AMDGPU-PRO will work.  It is problematic in 16.04 and fglrx is not available for 16.04.

To get AMDGPU-PRO to work on 16.04, I had to first upgrade the kernel and then mess around a bit before installing the experimental driver (support was "experimental" for 16.04).  It can be done, but if you are not fairly familiar with such things, you may have trouble.

Right now, the AMD GPU world is under a lot of construction and change.  We, the Linux community, are getting what we have been asking for (warning: be careful what you ask for!), but getting there is a bumpy road for AMD and for Linux.  In the end, AMD support will far outshine anyone else's - but it is going to be a rough trip.

All this is to say:  Unless you have a lot of money to spend on a newer AMD GPU and the desire to mess with your OS in ways that may break it if you are not careful, don't go with AMD just now.  And that is from a long-time AMD user who contributes to wikis and has a lot of blog articles about AMD.

---

### Post by Perfect Storm on 2017-02-19
I would go with nvidia card. If you want to game on Linux it have the best support and performance.

---

### Post by SeijiSensei on 2017-02-19
I've always used NVIDIA when the choice mattered.

---

### Post by uNoubu8a on 2017-02-19
It is sad that AMD has always been more open and collaborative with Linux yet to get anything near gaming performance from your hardware you need to use NVidia proprietary drivers (with a Nvdia gfx card obviously).

---

### Post by mastablasta on 2017-02-20
i think with 17.04 the AMD Will become a better choice (for new GPU cards). most stuff should be supported by then. if not on release then on .1 for sure.

but at the moment nVidia still leads.

---

### Post by gordintoronto on 2017-02-20
Generally, beware of running hardware which was introduced since the operating system you are using. For example, I would not try the latest and greatest Nvidia or AMD with 16.04. If you install 17.04 (a beta will arrive this week) you will only have to do two upgrades before the next LTS.

---

