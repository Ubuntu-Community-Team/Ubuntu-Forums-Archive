---
title: "Display issues in VirtualBox"
date: 2008-04-29
forum: Virtualisation
---

### Post by Jugney on 2008-04-29
Hello,

I recently did a fresh install of Hardy Heron and reinstalled VirtualBox and Windows Vista within it. After a restart, the display doesn't look right - like the number of colors is down to 8 bit or something.

It could be due to installing Guest Additions, or to the first batch of Windows security updates it installed - I'm not sure which. Does anyone have any ideas? I didn't see a way to configure the display in VirtualBox.

I have an nVidia graphics card with 128MB of memory, with 8MB assigned to the VM. 

Thank you for any help,

Jugney

EDIT: Solved. It was as simple as changing color in Windows display properties from 8bit (somehow got set to that) to 24 bit. If I  knew how to delete this post I would!

---

### Post by bnl on 2008-05-04
I just had the same problem with WinXP.  I went to the Control Panel and sure enough, it was set to 8 bit.  I just increased it and all is well again in VirtualBox land.

EDIT:  Haha, i didn't see your edit that just says the same thing.

---

