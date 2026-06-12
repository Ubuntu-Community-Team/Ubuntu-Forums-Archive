---
title: "LynxONE audio card/OSS issues"
date: 2009-03-16
forum: Ubuntu Studio
---

### Post by rayj on 2009-03-16
Has anyone ever gotten the LynxONE audio card to work under Ubuntu Studio 8.04?

While the drivers are not open sourced, an OSS driver was written (it's hosted at opensound.org). I installed the appropriate driver on my 64-bit system, followed the installation instructions, etc. No luck. I tried uninstalling Pulse Audio, to no avail.

Qualifiers: the system doesn't seem to see a soundcard at all...cat /proc/asound/cards doesn't exist now. This is probably complicated by the fact that I had just updated this system after having it shelved for a few months...there was some permissions issue that had kept me from logging in after the updates and LynxONE driver installation. I'm hoping to use the box for softsynth/fx processing, but I don't even know how to diagnose this issue. The driver was successfully installed, according to the terminal output, and OSS is the only driver displayed in system>preferences>sound, but the problem remains.

I'd like to avoid having to do a clean OS install, as there are several file libraries on the box I'd like to keep as is, but will go there as a last resort. However, considering the issues I've had, and the lack of information on the subject, I'm not even sure if that would work. Does anyone have any suggestions? This card seems to be a good one, and I'd like to implement its use if at all possible. Thanks.

---

