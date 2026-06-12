---
title: "Ubuntu 9.10 as guest OS under VMWare Server 2.0.2 - open-vm-tools Drag'n'Drop"
date: 2010-01-21
forum: Virtualisation
---

### Post by xavierda on 2010-01-21
Hi All,

I have been playing around with setting up Karmic Koala as a guest OS under VMWare Server 2.0.2 running on a Windows 7 x64 host.

I tried the supplied VMWare Tools (failed miserably) but then had somewhat better success installing the open-vm-tools package.

The one bundled in 9.10 got copy and paste working but time sync didn't seem to work. I downloaded the latest tarball from SourceForge and after installing the dependencies can get it to build and install.

Copy and paste works, and I think time synchronisation is sorted. I have to manually load vmware-user though. My main question is - has anyone managed to get drag'n'drop working with this setup?

I can't seem to find any guides for this - it seems to be assumed it will work out of the box.

I've tried loading vmblock (sudo modprobe vmblock) and then "mount -t vmblock none /proc/fs/vmblock/mountPoint" (which is meant to be picked up on by vmware-user) but still no joy ](*,)

Can anyone confirm DnD with Ubuntu 9.10 under VMWare Server 2.0.2? Or point me to a handy guide?

Cheers,

Xav.

---

### Post by xavierda on 2010-02-05
Anyone?

I'm still not sure exactly how to go about setting this up under Ubuntu 9.10.

Today I upgraded the kernel (now: 2.6.31-19-generic) and downloaded, configured and made the latest open-vm-tools release from SourceForge (build 226760).

Still no drag and drop - has this ever worked for anybody?

Regards,

Xav.

---

