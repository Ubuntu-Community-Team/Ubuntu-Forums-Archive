---
title: "Three issues I found with Ubuntu 9.04"
date: 2009-04-26
forum: Testimonials &amp; Experiences
---

### Post by ewz on 2009-04-26
Three issues I found with Ubuntu 9.04

The first Issue was that I found my video card would randomly lock-up requiring a hard reset to get it working again, I have had this problem before, a few years ago with Ubuntu and other Linux distributions the fix for this is to set an Option in  /etc/xorg.conf **Option "NvAGP" "1**"  
works fine now.

The second was my USB hard drive wasn't auto mounted which I thought was a bit strange considering previous versions of Ubuntu it was mounted automaticly.
I found the fix though, add **usb_storage** in /etc/modules reboot and and there it was.

The third issue was I have a duel boot with windows and Ubuntu, well I have XP and Window 7 as well, so Windows 7 handles the XP boot loader. anyway I found that grub had set root to **(hd1,0)** when it should have been **(hd0,0)** maybe because of how my drives are setup, easy to fix though so it is working fine now.

Well apart form those three issues every thing else seems ok.
A bit concerned about that issue with the Nvidia card turning up again after all this time.

Great distribution though, I love it  :-)

---

