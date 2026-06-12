---
title: "Segmentation faults after install"
date: 2009-04-28
forum: System76 Support
---

### Post by Viranh on 2009-04-28
This bug seems to be affecting anything built on the compal fl92 chassis or similar. (ie. the serp4). This was one of the other major bugs I ran into with jaunty. My wireless problem compounded it, because I couldn't download new packages to work on fixing it. 
[http://ubuntuforums.org/showthread.php?t=1137295](http://ubuntuforums.org/showthread.php?t=1137295)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/)

Are other serp4 users affected? 

It appears that I need to package a newer kernel with an installation. Can anyone give me an idea of how to do this? Links to a guide?

---

### Post by thomasaaron on 2009-04-28
We've not seen this on any of our systems, and I've not had any reports of it. If I read the bug report correctly, it looks like it is an ext4 problem. Are you installing ext4?

If so, I'd ditch it and stay with ext3 until they get the bugs worked out.

---

### Post by Viranh on 2009-04-28
No, this was with ext3 and ext4. I tried both. I reinstalled it six times, several with ext3 because I thought ext4 was causing the problem. I'm confused and frustrated that I'm the only one with this problem then. Perhaps I'll download and burn a new disk and hope there was something terribly wrong with my old one, although I did check it for errors. ](*,)

---

### Post by thomasaaron on 2009-04-28
OK. Make sure you are using Jaunty 64-bit, and make sure you reformat your drives. If you're using the "Guided - Use entire disk option," this should happen by default.

If you're manually partitioning, don't forget to check the "format" checkboxes.

---

