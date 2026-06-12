---
title: "Virtual Box Hardware Mixing"
date: 2008-05-19
forum: Virtualisation
---

### Post by gavshouse on 2008-05-19
hi i have XP on virtual box when using the sound on XP my Host(Ubuntu) doesnt have any sound.

So i found out its because my sound card(on-board) doesnt support hardware mixing so after trying to find a sound card that has hardware mixing and supports linux, i thought 

Can i use 2 Sound cards 1 for Host and 1 for Guest

I know 2 speakers sets or Cable splitter but can i make;

Virtual Box use Sound card 1 
Ubuntu Use sound card 2 

My sound card thread is here if anyone wants to add or help
[http://ubuntuforums.org/showthread.php?p=4989264#post4989264]("http://ubuntuforums.org/showthread.php?p=4989264#post4989264")

---

### Post by bradmkjr on 2008-05-19
Considered a usb sound card?

If you can pass the usb through to the VM then you could have complete control over all the functionality of the the sound device, compared to just the minimal amount with the virtual sound drivers?

[http://www.soundblaster.com/products/product.asp?category=1&subcategory=205&product=9103](http://www.soundblaster.com/products/product.asp?category=1&subcategory=205&product=9103)

PLEASE, do a little more research before buying any audio device to use with virtualization, but the the usb device might be something to consider.

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com](http://x86Virtualization.com)

---

