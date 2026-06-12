---
title: "KVM USB Passthrough of DVB working but is there a better way?"
date: 2014-01-06
forum: Virtualisation
---

### Post by KillerKelvUK on 2014-01-06
So my setup is purely for home uses/experimentation but today I created an Ubuntu Server 12.04 guest and mapped in my Tvii USB DVB-S2 adapter.  After applying the fix for getting USB 2.0 Host Controllers passing through ([http://www.linux-kvm.com/content/virt-manager-adds-support-usb2#comment-5437](http://www.linux-kvm.com/content/virt-manager-adds-support-usb2#comment-5437)) my guest showed the device as intended via lsusb but did not attempt to load any drivers.  So I decided to test my approach in a Win7 guest and this detected the device but complained about the USB 1.1 until I applied the aforementioned fix and then it worked fine, so I guessed my KVM config was okay.

I did a little reading (noobish still) around modules and took a look at lsmod to see what was there...nothing/nadda/zip!  I then recalled that my KVM guest template uses the "virtual" kernel image so I reverted back to normal 3.8.0-35 and after a reboot voila...the modules are loaded, the firmware is grabbed and the device is working.  TVHeadend is currently scanning the muxes as I type...all is good.

My reason for posting is to question whether my solution is indeed the right approach.  I'm still learning my way around so any critique welcome to help me learn?

---

### Post by TheFu on 2014-01-07
I use multiple HDHR tuner devices. Skips the entire "physically connected" limitation of many tuners which means any VM can be used. The HDHR are network-based tuners and highly recommended by almost everyone.  I love mine, but will admit, I don't use them with Linux (7MC under a KVM VM). Any computer on the network can use any tuner on the network, if it isn't already in-use.

So, is there a better way?  Yes.

---

