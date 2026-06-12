---
title: "System capture missing"
date: 2011-08-05
forum: Ubuntu Studio
---

### Post by aeh on 2011-08-05
I have just installed ubuntu studio 11.04 on a new machine. My audio hardware is a mAudio Fasttrack pro USB. When starting Jack for the first time I have to configure it. So I select input and output devices but I cannot get a 'system capture' in the connections window. Playback works tho.
On the previous installation I had no problems at all. I have 2 other machines with Natty, on both I get the system capture as it should be.
Any ideas?

A

---

### Post by sgx on 2011-08-07
Hi, does the periods/buffer setting in qjackctl setup panel have 3? that's needed for a usb device. 

Is the Audio button set to duplex?

Do you have multiple entries in the Device Output >  dropdown to choose from?

Does lsmod output include a typical snd_ICE1712?

It almost sounds like a kernel module is inferior to the
one in your previous setup. You could install that other kernel,
and choose it at boot time.

Cheers

---

