---
title: "VirtualBox on 14.04 host Intel Graphics - Fullscreen mode"
date: 2014-09-18
forum: Virtualisation
---

### Post by den_ on 2014-09-18
Since the last update of VirtualBox I am not able to run it in the full screen mode (actually seamless mode is also affected.) any more. 
By that I mean the screen freezes, and it doesn't accept any input, except switching work spaces, but every workspace shows Win7 (guest) desktop, and as I mentioned, no interaction with neither guest nor host is possible.
If I try to activate the seamless mode, a behavior is a bit different. Instead the picture of Win7 desktop I see darkened Ubuntu host desktop, rest is same.

I have to switch to one of emulated ttys, or to log in via ssh and to kill the VirtualBox process. Afterwards is the system usable again.

Relevant system info: Ubuntu 14.04, 64 bit Intel (Sandy Bridge) graphics.

VirtualBox from their repo "http://download.virtualbox.org/virtualbox/debian trusty contrib".

I found it strange I am the only one to report this issue here. There is a smiliar issue reported in VirtualBox forums, but not really the same as mine.

I would be thankful if someone could provide some feedback on this...

Thanks

Denis

---

### Post by TheFu on 2014-09-18
Every time the kernel gets replaced, reinstalling the virtualbox guest additions is necessary.  Add this to your -every time the kernel changes - checklist.

---

### Post by den_ on 2014-09-18
AFAIK, there was a bug, years ago which forced one to do that, and has been fixed since a while.  I'm using Virtualbox on Ubuntu host for 5 years now, and I never had to reinstall guest additions. Sometimes a recompiling the kernel module is necessary, if one doesn't use dkms (like in my case, when one uses their packages.) but reinstalling of guest additions, not really. 
I did reinstall the additions, just to be sure, and it didn't help unfortunately.

---

### Post by den_ on 2014-10-05
I have marked this thread as solved, although that's not 100% the case. The thing is, VirtualBox 4.3.10 from Ubuntu repository works in full screen mode, as usual without issues. 

If one wants the latest 4.3.16 from Oracle's repo, in my case the only option is to give up on full screen / seamless mode.

---

