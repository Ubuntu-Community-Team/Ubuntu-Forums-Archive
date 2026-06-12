---
title: "Can't get more than 16 colors in Win2k guest in Vbox"
date: 2007-11-17
forum: Virtualisation
---

### Post by timzak on 2007-11-17
I'm not sure how to proceed...Win2k installed good in Vbox (Gutsy host) but can't get anthing more than 800x600 16 colors.  I tried installing nvidia drivers but that didn't work.  How do you get more than 16 colors?  I'd be happy with 16bpp and 1024x768.

Thanks

---

### Post by marguz on 2007-11-17
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Look at the user doc and start reading about installing the "Guest Additions". You can not install the NVidia, ATI or any other 3rd party drivers in the guest for the video, you need to use the guest additions.

I hope that either KVM or XEN will sometime in the near future be able to use 3rd party drivers.

---

### Post by timzak on 2007-11-18
Thank you, I did get this sorted out.  Didn't realize that the guest additions were hidden so obviously in the VM dropdown menu.  I spent all this time Googling to find the guest additions and couldn't find anywhere on the web when all I had to do was install from within Virtualbox dropdown menu. :oops:

---

### Post by jonberling on 2007-11-20
Thanks for this post, I had the same problem but was able to solve  it quickly after reading this :)

---

