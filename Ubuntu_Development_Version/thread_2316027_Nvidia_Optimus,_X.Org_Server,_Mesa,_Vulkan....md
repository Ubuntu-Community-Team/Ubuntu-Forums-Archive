---
title: "Nvidia Optimus, X.Org Server, Mesa, Vulkan..."
date: 2016-03-04
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2016-03-04
Hi all,
does anyone know what can we expect in Ubuntu 16.04 (expected to be released on 21 April 2016) related to:

**-*** X.Org Server 1.18 released in November 2015 / X.Org Server 1.18.1 released 8 February 2016

**-*** Nvidia 352.79 released on 2016.1.25

**-*** **NVIDIA Sends Out Latest PRIME Synchronization Patches**
4 March 2016: **PRIME synchronization should fix tearing for those using a multi-GPU solution like Optimus with an Intel integrated graphics processor and NVIDIA discrete GPU in their laptop or desktop**.
[http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-PRIME-Sync-V4](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-PRIME-Sync-V4)

**-*** Mesa 11.2 Launches March 11, 2016

**-*** 3 March 2016: The Vulkan 1.0 specification is less than one month old and NVIDIA has already released their third Linux driver beta.
[http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Third-Vulkan-Beta](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Third-Vulkan-Beta)

**-*** NetworkManager 1.0.10 released 23 Dec 2015


Thanks in advance for any info :)

---

### Post by grahammechanical on 2016-03-04
You are asking about the future. In this section of the forum we deal with the present. The stuff that has actually made it into the development release at this point of the development cycle.

There are always plans. Implementation is something else.

Vulkan

[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Mir-Vulkan](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Mir-Vulkan)

Do not expect beta video drivers to come into a Long Term Support Release. Do expect stuff like X.Org & Mesa to be upgraded over time. If not before the release date then in a point release 6 months or there abouts later. There is a PPA where we can get later, more edgy Nvidia drivers before they go into the stable update channel. It is already showing Nvidia 361.

I do not have a video card that is supported by Nvidia 352 or 361. So, I cannot say if either is available through Additional Drivers. But I do notice that Nvidia settings is at 361 and Nvidia settings usually parallels the Nvidia driver version.

Regards.

---

### Post by grahammechanical on 2016-03-09
A MIr & Vulkan demo

[http://kdubois.net/?p=2056](http://kdubois.net/?p=2056)

The developer says

> If you&#8217;re wondering when this will appear in a repository near you,  probably right after the Ubuntu Y series opens up (we&#8217;re in a feature  freeze for xenial/16.04 LTS at the moment).

Regards.

---

### Post by grahammechanical on 2016-03-12
A blog post that indicates that Ubuntu 16.04 will get X server 1.18. It also shows that what we might think of a something simple to bring about is actually much more difficult to do.

> In case someone [hasn&#8217;t]("https://www.reddit.com/r/Ubuntu/comments/49g4ck/catalyst_will_not_be_included_into_the_next_lts/") [noticed]("http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx") [yet]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016312.html"),  fglrx has been removed from Xenial. There are a couple of reasons for  this. First of all, the driver did not support XServer 1.18 which we  wanted to get in for 16.04.

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

Regards.

---

### Post by aljosa2 on 2016-03-12
My Ubuntu 16.04 current details:

- Nvidia 361.28
- X.Org server 1.18.1 (by the way, X.Org server 1.18.2 was released a few hours ago)

---

### Post by grahammechanical on 2016-03-12
> (by the way, X.Org server 1.18.2 was released a few hours ago)

:) :) No rest for the weary devs.

---

### Post by aljosa2 on 2016-03-21
*21 March 2016*
**NVIDIA 364.12 Arrives With Wayland & Mir Support**
[http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-364.12-Linux](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-364.12-Linux)

The NVIDIA 364.12 driver adds a Wayland platform library to support Wayland composittors, adds new EGL extensions for Wayland, adds initial DRM KMS support, now uses GLVND GLX client libraries by default, adds in Vulkan 1.0 support to mainline, adds new RandR properties, **and now provides proper PRIME support too**.

---

