---
title: "KVM Spice performance"
date: 2012-06-09
forum: Virtualisation
---

### Post by Reason NL on 2012-06-09
I've been using KVM for quite some time now, but recently learned of the spice protocol.
I've been using virtualbox for all my desktop VM's because of the dreadful graphical performance of KVM/QEMU, so I got excited about Spice giving me the possibility to switch to KVM for all my visualization needs.
So I ended up testing Spice with virt-manager on both my server and locally, but even though it's better than the VNC solutions it's still way of to be useful for graphical desktops. It doesn't come close to virtualbox. Quite the opposite of what I've seen on the web about spice.

Does anyone out here have experience with Spice?
Anyone some clues on how to speed up things?

(I've seen impressive movies on youtube but that seems to be miles from what I've seen here)

---

### Post by Reason NL on 2012-06-22
Anyone? I've been trying installing agents, but it's still not running smooth at all.

---

### Post by ClientAlive on 2012-07-01
I see you were able to get spice working at all. I've tried changing the  configuration in KVM but get errors; and, ultimately, it won't take.  I've been looking all over the internet for several days for some  instruction how to get it working but have mostly come up empty-handed. I  saw one bug report that seemed relevant but the language used was a  little over my head and left some gaps in information as well.

By any chance can you direct me where to find information or help me any  other way? Also, if you happen to know of any info on setting up dual  monitors with the guest.

---

### Post by Reason NL on 2012-07-06
I just installed the qemu-kvm-spice (available in  12.04) and created a new VM using virt-manager selecting spice as video  output.
Nothing more to it and it worked just fine, besides the performance that is.

Hope you will get it working so you can take a look at this performance issue as well.

---

### Post by babyhuey on 2012-07-17
Make sure you are using the QXL video adapter in virt-manager. Performance will be pretty terrible with any of the others. With QXL 2D performance should be comparable to virtualbox or vmware. However, videos like YouTube and the like will not be as fast as virtualbox and vmware.

The Spice protocol currently uses MJPEG for video which isn't the best. There is work being done to pass the raw video directly to the host where it can be decoded in hardware or FFMPEG, etc.



ClientAlive:
I wasn't able to get it to work until I used this ppa:
[https://launchpad.net/~bderzhavets/+archive/lib-usbredir76](https://launchpad.net/~bderzhavets/+archive/lib-usbredir76)

Stock Ubuntu would always give me a black screen if I booted with anything but the paravirtualized Cirrus vga.

---

### Post by ClientAlive on 2012-07-18
> **Reason NL said:**
> I just installed the qemu-kvm-spice (available in  12.04) and created a new VM using virt-manager selecting spice as video  output.
Nothing more to it and it worked just fine, besides the performance that is.

Hope you will get it working so you can take a look at this performance issue as well.

Right on. I didn't know about that package to install. I'll try it out next time I have a littler time.

Thx

---

### Post by Reason NL on 2012-07-18
Forgot to mention that I had installed python-spice-client-gtk as well (client side). Virt-manager throws an error in the console screen without it.
Although the screen is black for a while, with QXL enabled, it does boot the desktop perfectly fine.
Still though, the performance isn't great and doesn't come close to Virtualbox on the same machine.
Haven't tried video's, Firefox refuses to run in the ISO for some strange reason (Had the same problem running it directly on bare metal so no KVM issue).

Quick summary:

Installed kvm, qemu-kvm, qemu-kvm-spice and python-spice-client-gtk right from the default repo, no PPA whatsoever (12.04 Host).
Created a simple virtual machine running directly from the Ubuntu ISO (12.04).

(Installed it on a raw image prior to this test with the spice-vdagent, but that didn't make a difference performance wise)

I was planning to run all my VM's in KVM, not just the server ones, but the desktop performance has to be on par with Virtualbox  to be a viable alternative.

---

