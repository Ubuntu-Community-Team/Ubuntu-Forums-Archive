---
title: "Quark Xpress 8.12 - Won't boot properly"
date: 2010-03-09
forum: Wine
---

### Post by von kluth on 2010-03-09
**'Mornin!**

I've been trying to get this to work by myself but I'm guessing my inexperience with Ubuntu may be the problem there...


[SIZE=3]**Problem**[/SIZE]

I've managed to download the trial for Quark Xpress 8 from the official website.
I've installed it (the PC-version ofc.) through wine.
However as I try to boot I only get the launch-screen (similiar to that of Open Office).
It won't load any further, It just hangs when it gets to the launch-screen.
I've set the version of windows that Wine launches to almost every setting.
I've checked the System Monitoring and it tells me that Quarks CPU-usage is at 90-120%.

When running via the terminal I get this:

```
fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:storage:StgCreateDocfile Storage share mode not implemented.
fixme:ver:RtlGetProductInfo (6,0,0,0,0x32f230): stub
fixme:ver:RtlGetProductInfo (6,0,0,0,0x32f218): stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:advapi:GetEffectiveRightsFromAclA 0x1870b4 0x32dbfc 0x32dbb0 - stub
fixme:ole:OleQueryLinkFromData (0x1df6d0),stub!
fixme:ole:OleUIAddVerbMenuW ((nil), (null), 0x1007a, 13, 16876, 16925, 0, 16926, (nil)): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
```i can't read what it is telling me. What should I do? :confused:

I have a feeling this shouldn't be to hard to fix. However I have yet to hear of someone running Quark Xpress 8 on Ubuntu - everyone seems to be using the older versions.


Help is of course much appreciated.

---

### Post by asdfoo on 2010-03-09
which `wine --version` are you using?  1.1.40 is the most recent, give that a shot if you're using an older version.

---

### Post by von kluth on 2010-03-10
As I was using 1.1.39, I swapped for Wine 1.1.40 but it seems to have made no difference, the problem remains unchanged. :/
When I try to launch Quark the System Monitoring tells me its CPU-usage is at 90-120%.

---

### Post by von kluth on 2010-03-11
Anyone?
I'm really confused on this one. :(

---

