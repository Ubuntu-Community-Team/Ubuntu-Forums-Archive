---
title: "Please Compare Low Latency Image to Regular Image like in Ubuntu Studio"
date: 2014-07-09
forum: Ubuntu Studio
---

### Post by sam-c on 2014-07-09
Please Compare Low Latency Image to Regular Image like in Ubuntu Studio
Thanx
Uncle Sam
For Example When I am running VLC with a DVD Movie Should I run it on Ubuntu Studio or Regular 14.04 Ubuntu or Related Distros?
Thank you Again:popcorn:

---

### Post by jejeman on 2014-07-09
If you have weak PC you should use regular instead of lowlatency.

---

### Post by brianmc on 2014-07-11
> **sam-c said:**
> Please Compare Low Latency Image to Regular Image like in Ubuntu Studio

Err, one is good for time-critical work, such-as realtime audio - the other isn't?

Not really what you were asking, is it?
> For Example When I am running VLC with a DVD Movie Should I run it on Ubuntu Studio or Regular 14.04 Ubuntu or Related Distros?

As the other poster says, that should only matter if you're running on really ancient hardware.

If you have an issue with VLC under Ubuntu Studio, there is nothing to stop you installing the package ***linux-generic*** and booting with that kernel rather than the lowlatency one. The differences between the two are, nowadays, nowhere near as-dramatic as they were a few years ago; most of the code for lowlatency is in the mainline kernel already, and I'd be surprised if you could tell the difference unless you set out to do near-realtime audio work with a generic kernel.

---

