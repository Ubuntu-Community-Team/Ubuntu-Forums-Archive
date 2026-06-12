---
title: "Upgraded my Lemur from 11.04 to 11.10, stuck on 'Grub loading&quot; with blinking cursor"
date: 2011-11-08
forum: System76 Support
---

### Post by randizzle on 2011-11-08
Cross-posting here since I am getting no love in the 'Installation & Upgrades' forum.

Using the update manager, I attempted to upgrade from 11.04 to 11.10. After completion, I was prompted to restart, which I did. At that point the the machine cycled and when it came back up, I saw the manufacturer splash screen, then a black screen with a blinking cursor. I restarted again, held shift and was greeted with "GRUB loading" at the top and a blinking cursor beneath, it sits in this state indefinitely.

Searching the forums, most people in similar situations seems to be able to book into safe mode. I am unable to get to the GRUB kernel selection screen, so this is not an option.

My machine is a Lemur UltraThin (lemu2)

---

### Post by isantop on 2011-11-08
It sounds like grub was corrupted during the upgrade. You'll want to have a look at this page:

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

It details how to reinstall Grub from a LiveCD.

---

### Post by randizzle on 2011-11-12
Thanks for the response, that was my fear. I am going to try what you suggest today.

---

### Post by isantop on 2011-11-14
The Grub reinstallation is actually rather quick and painless, and can be done without erasing any data on your hard drive.

---

### Post by randizzle on 2011-11-14
Yes, I realize that, thank you. Your analysis was corrent and I was able to fix it with the instructions you provided. (Though its a bit hard to understand how following the normal upgrade path via the update manager caused a corruption in the MBR.)

Thanks again!

---

