---
title: "[Virtualbox] Zune software not working"
date: 2008-12-09
forum: Virtualisation
---

### Post by OisinT on 2008-12-09
All seems to be fine when I installed virtualbox.  followed all how-tos and got it going well.  USB is working fine.
HOwever, when I installed the Zune software, i get an error saying that my graphics are incompatible and the zune software just crashes.  I've tried putting the -gdi postfix on the launcher as recommended elsewhere but no luck.
Any and all help is appreciated as I'm heading on a long transatlantic flight on friday and I need some music :(

here is the exact error:

> Your video hardware is not fully compatible with the Zune software. This will keep you from enoying video enhancement, which encludes ornamental on-screen animation. Updating your video drivers at the manufacturer's website might fix this. To re-enable video enhancement, go to Display Settings.

For more info visit the following page:
[http://go.microsoft.com/fwlink/?LinkID=115333&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=115333&clcid=0x409)

then it has a choice to continue, but it always just crashes

---

### Post by Dedoimedo on 2008-12-09
You tried installing it in the virtual machine right?
Well, support for graphics in virtual machines is quite weak today and you won't be able to have 3D acceleration, unfortunately.

Your best bet would be to try VMware Server and an experimental 3D support hack, which might work for some directx 9.0 applications, but it's a big maybe.

Cheers,
Dedoimedo

---

### Post by OisinT on 2008-12-09
come to think of it, honestly I really don't care about the 3D acceleration, I just want to be able to transfer music onto my zune any way possible.  Any idea if there is a way to do it without the 3D stuff?  I didn't think there was but others have gotten it to work so i'm not sure

---

### Post by OisinT on 2008-12-10
bump. anyone?

---

### Post by deputy on 2008-12-17
I was able to install and run Zune software using virtual XP with VMWare Server 2.0. I've been testing it for about 2 weeks now and I am able to update firmware, download music and vids from marketplace, sync to zune, play music and videos. The only thing I haven't tested is the wireless sync. I do believe that VMWare has added hardware acceleration and 3d support so you shouldn't have any problems with that as long as your video card supports it. I used VMWare Server 2.0 because it's free and it supports USB 2.0. I use the Zune software with my 80gb zune and like I said it runs just fine inside virtual XP.

---

