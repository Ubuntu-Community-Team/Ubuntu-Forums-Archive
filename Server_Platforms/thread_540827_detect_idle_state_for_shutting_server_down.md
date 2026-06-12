---
title: "detect idle state for shutting server down"
date: 2007-09-02
forum: Server Platforms
---

### Post by drsar on 2007-09-02
I am looking for a method to shut down my fileserver (SAMBA, LAMP) when nothing important is happening. Is there a program that detects idleness and could issue a halt? I'd like to do this to save some power since most of the time the box just hangs out in the basement and is needed only a few times. I have sorted the coming-back-to-life with wakeonlan - works like a charm.

A bit of the specs:
It's a 2.6.20-16-server on a dual processor PIII machine ("switched to SMP code" hence AMP is disabled)

The events that I would like to keep the server alive are someone accessing SAMBA shares, apache answering requests or me being logged in via ssh.

Any pointers or help appreciated.

---

### Post by HermanAB on 2007-09-02
No, just set the power settings to turn off the HDDs after 5 minutes of inactivity.  The disk drives are major consumers of power - about 25W when running.  Turn off logging, so that the disk drives don't keep spinning up all the time, with  sudo service syslog stop'.

Then check the processor type.  If the processor can speed step (Pentium M, Core 2 Duo etc) , then you can load the laptop power control features.  The result will be very low power consumption.

Cheers,

Herman

---

