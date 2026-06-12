---
title: "Updates on new Starling"
date: 2009-06-24
forum: System76 Support
---

### Post by Georgesl on 2009-06-24
I'd been on my brand new Starling for about an hour and a pop-up window stated that there are something like 40MB of updates pending.  Is this normal and should I just proceed with them?

(I'm a bit paranoid because it's working so well at this point!)  :)

---

### Post by Derath on 2009-06-24
It's normal, I usually do my updates weekly, and there's usually always something to update.

---

### Post by Georgesl on 2009-06-25
OK, I ran the updates, a11 104 of them!

Everything seems to have gone smoothly except for one message that popped up that asked 

"What would you like to do about menu.lst?"

My options were to either: 

1. Install the package maintainer version 

or 

2. Keep the local version.  

Since "Keep the local version" was highlighted I selected that one. and the update concluded with instructions to reboot the computer.

Is this something I should be concerned about?  Could someone explain what menu.lst does or point me to a reference?  I'm a physics teacher so you can use moderate-sized words, but I know little about Ubuntu.

---

### Post by jdb on 2009-06-25
> **Georgesl said:**
> OK, I ran the updates, a11 104 of them!

Everything seems to have gone smoothly except for one message that popped up that asked 

"What would you like to do about menu.lst?"

My options were to either: 

1. Install the package maintainer version 

or 

2. Keep the local version.  

Since "Keep the local version" was highlighted I selected that one. and the update concluded with instructions to reboot the computer.

Is this something I should be concerned about?  Could someone explain what menu.lst does or point me to a reference?  I'm a physics teacher so you can use moderate-sized words, but I know little about Ubuntu.

/boot/grub/menu.lst is a plain text file that is used by grub to produce a boot menu.

I don't know what he difference is, but since you're probably not interested in maintaining packages I don't think you need the package maintainer version.

When unsure, I always go with a highlighted option :)

jdb

---

