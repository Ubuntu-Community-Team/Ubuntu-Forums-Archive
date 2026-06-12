---
title: "VirtualBox problem-- unable to boot from ISO."
date: 2013-02-07
forum: Virtualisation
---

### Post by arsenalFC on 2013-02-07
Hello members,

I'm using VirtualBox to run the ISO "hacking: the art of exploitation", and I'm having somewhat of a weird problem. The ISO runs correctly, it boots up and the splash screen shows giving me the option to do a memory test, check CD for defects, boot from local disk, run liveCD etc.. The only option that works is memory test but when I try to  it says liveCD it gets stuck at  a black screen. 

I followed the step by step instructions on how to mount an ISO image from the virtualbox website, I don't know what's the problem. The same problem happened when I was running windows 7 and I'm on ubuntu now. 

regards.

---

### Post by CharlesA on 2013-02-07
Sounds like a video driver issue with whatever driver that CD is trying to load inside VBox.

Have you already verified the ISO is good by checking the md5sum or sha1sum that should be available at the place you got it?

---

