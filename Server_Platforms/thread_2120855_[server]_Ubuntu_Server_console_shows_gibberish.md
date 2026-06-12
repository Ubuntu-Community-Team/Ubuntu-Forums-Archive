---
title: "[server] Ubuntu Server console shows gibberish"
date: 2013-02-27
forum: Server Platforms
---

### Post by conman124 on 2013-02-27
Hi,

I just installed Ubuntu Server 12.04.02 LTS on my server.  The install went fine.

However, now whenever I boot, the console doesn't show English.  I'm not sure if it is showing another language, or is just showing random ASCII characters in place of English.

The login prompt looks like this: [http://img546.imageshack.us/img546/8183/0226132201.jpg](http://img546.imageshack.us/img546/8183/0226132201.jpg)

However, when I boot from Recovery Mode, and tell it to resume normal boot, it works fine.

I can't think of any specialized hardware/video cards that I have.  It is a pretty old machine, so that could be the problem.

Anyone know what to do?  If you need more information, I should be able to ssh in to get it.

Thanks,
Connor

---

### Post by conman124 on 2013-03-02
I discovered something!  Upon examination of dmesg logs from recovery mode which works, and normal mode which doesn't, it seems as though in the normal mode, these is a line which says "[0.42991] efifb: cannot reserve video memory at 0xa6d60".  This line doesn't appear in the recovery mode.  Also, it seems as though in the recovery mode, the video system is not initialized until later in the boot process.  Edit: Upon further examination, I don't see any lines labelled efifb in the working, recovery mode dmesg log.

I think that the video card ( an Intel 82815 815 Chipset ) must need a little bit of time to do its own initialization before it is ready for use, but in the normal mode, the system is trying to initialize it before it is ready.

Is there any way I can tell the kernel to wait before initializing the video system?

Thanks,
--Connor

---

### Post by rockskull on 2013-04-03
Hi,

Did you found a solution for your problem?

I have the exact same problem. Same video chip and ubuntu 12.04, same thing: works in recovery mode and doesn't in normal mode.

---

### Post by conman124 on 2013-04-03
No I never figured it out.  I mostly just SSH into the box, and that works.  And there doesn't seem to be any negative effects of booting through recovery mode, so I'm mostly doing that.

---

