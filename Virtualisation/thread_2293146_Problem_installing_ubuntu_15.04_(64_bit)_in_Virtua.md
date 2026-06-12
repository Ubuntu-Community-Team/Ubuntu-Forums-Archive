---
title: "Problem installing ubuntu 15.04 (64 bit) in Virtualbox 5.0"
date: 2015-09-03
forum: Virtualisation
---

### Post by gaurav.pruthi88 on 2015-09-03
I am trying to install ubuntu 64 bit in virtualbox 5.0.x  as guest OS inside a 32 bit ubuntu 14.04 host. I tried installing 14.10 and 15.04 (both 64 bit) without success. When the tried installing 14.10, after the step "copying file is complete" an error pops up "the installer encounters an unrecoverable error" and then it hangs. When I try with 15.04, after the "copying files" step is completed (starting installtion steps didn't come ), it takes me to login screen where if I enter username as "ubuntu" and blank password it appears like login and password is fine but it comes back to login screen. After starting virtual terminal Ctrl + F1 , I can see crash files in /var/crash/ related to compiz 
I removed ubiquitous-slideshow-ubuntu from virtual terminal (after reading posts on this forum ), but situation is till the same
Any idea how to get rid of this crashes. Also I want to mention when I use option "Try Ubuntu" when virtualbox starts, then I see the background with the unity sidebar and 2 icons on desktop (including the icon to "install ubuntu" )blinking.

---

### Post by QIII on 2015-09-03
Hello!

What are the hardware specs of the host machine?  Under the right circumstances you can install a 64 bit guest on a 32 bit host.

---

### Post by howefield on 2015-09-03
And thread moved to the "*Virtualisation*" forum.

---

