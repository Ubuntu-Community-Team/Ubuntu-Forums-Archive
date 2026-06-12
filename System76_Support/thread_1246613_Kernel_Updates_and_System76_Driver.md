---
title: "Kernel Updates and System76 Driver"
date: 2009-08-21
forum: System76 Support
---

### Post by rrenomeron on 2009-08-21
My wife did a kernel update this morning on her Starling netbook with the latest (2.3.7) System76 driver, and when she rebooted, she was unable to see any wireless networks.

After some investigation, I found out that the new wireless driver (r8187) could not be loaded (possibly because it needs to be compiled against each new kernel).  So I hooked the Starling up to a wired network, re-ran the System76 driver app (the "install drivers" tab), and rebooted, and the wireless was back.  Problem solved.

But ...

There has to be a better way.  Is there?  I am trying to make things as un-geeky and "just works" for my wife as possible.  It's annoying for a nontechnical user to have to hook up to a wired network after every ABI-bump kernel upgrade (which seems to happen much too often, but that's for a different rant).

---

### Post by rubbsdecvik on 2009-08-22
I just received my starling and I had the same problem. And same solution. I'm not sure about any other way around it.

Fortunately for me, I am a techi so I don't have much problem with it, but I agree with you that this is still a little hard to deal with for non-techi's

---

### Post by jml on 2009-08-22
A rapid upgrade cycle is one of the prices you pay for running Ubuntu.  Its designed to be a cutting edge distro with an aggressive update cycle.  The main advantage is that it supports some of the newest hardware out there.You could run a distro with a more conservative update/upgrade cycle, but then you loose support for some of the newest hardware.  I am a big fan of Debian but for many reasons, I can't get it to run satisfactorily on my Starling.  Ubuntu just works better.  End of sermon.  :-)

Joe

---

### Post by paulbary on 2009-08-22
I'm fortunate that my office is only a mile or so from System76's office.
I spoke with Carl last week and he expressed concern that this would be the case with kernel updates and that they have been in contact with Ubuntu Developers about including the newer "fixed" wifi driver in the
kernel. Apparently this is not the normal protocol for Ubuntu and he didn't seem overly optimistic that it would happen with 9.04 ... on the plus side, the October release of Ubuntu isn't that far away and the newer driver should be included, so this problem should no longer be an ongoing issue. I suspect that it will be problematic until October and the cheap fix, (at least IMHO), was to disable auto updates to avoid unintended breakage. Not perfect for sure, but it seemed a reasonably prudent risk given my Starling use ... just my thoughts ...

Paul

Paul

---

