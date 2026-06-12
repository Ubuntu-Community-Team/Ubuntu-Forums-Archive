---
title: "Keyboard Detection Problem During Install"
date: 2009-03-26
forum: Server Platforms
---

### Post by warchief_ryan on 2009-03-26
When I try to install Ubuntu Server on this old Compaq Presario 5304 it gets to the install menu but the keyboard does not work, I can get into the BIOS but it doesn't work once the CD is loaded.

I also tried Debian Lenny but same thing.

Any idea's to get this installed?


also,
Its a USB keyboard, I don't have a PS/2 keyboard.

There's nothing in the BIOS related to the keyboard or USB that I see.

---

### Post by Yashiro on 2009-03-26
Are you sure? In cases like this it's usually enough to toggle the 'legacy usb' setting or whatever it's called in the bios.

---

### Post by warchief_ryan on 2009-03-26
Yea ive heard that before but there's nothing like that in the BIOS, this is a really old box maybe that's why, its a legacy system itself.

---

### Post by cariboo on 2009-03-26
If you have a usb-->PS/2 adapter give that a try.

Jim

---

### Post by warchief_ryan on 2009-03-26
I have but didn't work.

---

### Post by warchief_ryan on 2009-05-11
To follow up for anyone else in a similar situation, I have to remaster the iso for whatever distro and set a timeout value in isolinux/isolinux.cfg.

Once booting, it detects the keyboard fine.

---

