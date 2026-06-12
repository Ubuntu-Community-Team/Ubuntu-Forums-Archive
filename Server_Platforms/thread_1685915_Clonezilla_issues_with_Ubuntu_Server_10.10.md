---
title: "Clonezilla issues with Ubuntu Server 10.10"
date: 2011-02-11
forum: Server Platforms
---

### Post by kestrel_ on 2011-02-11
Hi, i'm a beginner with linux and Ubuntu but not sure the absolute beginners forum is the right place for this.

I recently installed 64bit 10.10 server.  I got it configured to my liking and decided to create an image with Clonezilla.  After running Clonezilla and restoring the image I made to another identical drive, both now boot to a blinking cursor slightly offset from the top left of my screen.  I can press enter and log in normally.  There is also some 640x480 console text that flashes briefly right after grub but before the black screen/cursor.  

I have no idea what might have been modified by Clonezilla or why considering i only imaged the original drive, yet both now exhibit this odd behavior.  I junked my first server install (grub actually) using Clonezilla, but i think that was user error.  This time I feel I followed proper procedure and still ended up with a modified source drive.  Can anyone confirm similar issues or possibly diagnose mine?  Thanks.

kestrel

---

### Post by kestrel_ on 2011-02-11
I'll post this in the Clonezilla forums but i'm still interested to hear if anyone else has this issue

---

### Post by CharlesA on 2011-02-11
It probably reinstalled GRUB2. To prevent it from doing so, you need to use expert mode and untick the box that says "install grub" or some such thing.

---

### Post by kestrel_ on 2011-02-12
Ok, sounds like a plan.  Thanks.

---

