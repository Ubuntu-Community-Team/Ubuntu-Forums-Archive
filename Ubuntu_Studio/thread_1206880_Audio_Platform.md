---
title: "Audio Platform"
date: 2009-07-07
forum: Ubuntu Studio
---

### Post by FatChan on 2009-07-07
Hi All,

I am trying to develop an application that controls up to two full duplex sound devices, and have them simultaneously play and record.  RAW files are all that are neccessary.  Can someone give me some key words or hints on how best to accomplish this in Linux?

One of the devices does not have ALSA support.  Is something like PulseAudio what I should be looking at? 

Thanks in advance.

-Brian

---

### Post by kayosiii on 2009-07-07
to use two sound devices simultaneously to record you need to have the synced to a single clock source.... Some professional sound cards have this capability. Your other options would be to physically modify one of the cards... Or I think there is a method that net jack uses.

When you say that one of your cards is not supported by alsa - what is it supported by? Other than that I suggest searching here or the Linux Audio Users mailing list for multicard setups using net jack (or jack2)...

---

