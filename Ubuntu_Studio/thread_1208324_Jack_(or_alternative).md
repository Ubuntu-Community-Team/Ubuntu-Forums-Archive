---
title: "Jack (or alternative)"
date: 2009-07-09
forum: Ubuntu Studio
---

### Post by yasahiro on 2009-07-09
i have a Yamaha DGX-500 keyboard, and would like to hook it up to this computer via a midi - usb cable. for now, i dont have that cable, but i am trying to get sound out of the Jack program. I'm using an optical out (IEC958 on alsamixer) from a turtle beach montego DDL card. I'm not quite sure how to configure Jack for it...

any help would be GREATLY appreciated ^^;

---

### Post by raboofje on 2009-07-09
Jack just 'routes' audio streams, it does not produce sound itself.

A good way to start would be starting jack from qjackctl, zynaddsubfx and vkeybd. Then, in qjackctl, go to 'connections', 'alsa midi': you should see vkeybd (on the left) and zynaddsubfx (on the right) there. Hook them up and bang on the vkeybd keys. The volume bars in zynaddsubfx should light up, and you should hear sound.

Once you get that cable, replace vkeybd with the real thing :).

---

