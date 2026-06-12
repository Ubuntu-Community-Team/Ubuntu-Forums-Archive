---
title: "Problems with virtualization after upgrade to 10.04"
date: 2010-05-08
forum: Virtualisation
---

### Post by mrwawa on 2010-05-08
Hi all,

I run Ubuntu using VirtualBox 3.16 with XP as a host.  I recently updgraded to 10.04 and I received the message that some third party software was being disabled and/or couldn't be updated.  Now when I try to boot Ubuntu 10.04 within VirtualBox /sbin/vboxsf is gone so I can't mount my shared folder.  In addition Ubuntu has low be run in low graphics mode.  Messages are "failed to load /usr/lib/ . . /drivers/vboxvideo.drv.so.  Also seemless mode is impossible and I can't rerun the guest addition.  On top of that, mouse usage is spotty (i.e. being trapped inside the window, and then only of limited use.  As if unseen windows are blocking it).

It seems that some of the VirtualBox files etc. were deleted.  What is the best way to remedy this situation.  Can I reload the .vdi file image.  Will I lose files that I have saved?

On a more general note.  What is the best way to update Ubuntu within a virtual machine.  Minor glitches have occurred each time I have upgraded, but nothing to this extent.  I am basically getting scared to upgrade, but no one should live in fear.

Thanks for any information,

Wade

---

### Post by jbrown96 on 2010-05-08
You probably just need to reinstall the Virtualbox guest additions in Ubuntu.

---

### Post by mrwawa on 2010-05-09
Thanks a lot.  I didn't know I needed to do that, but everything is fine now.

---

