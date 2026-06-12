---
title: "ubuntu+windows+bsd=partition table made a mess!!!!"
date: 2005-05-24
forum: The Cafe
---

### Post by T31 on 2005-05-24
ok this is my story xP

I wanted to install bsd but, it does work in a completely different way so I have this: primary partition windows in one extended, gentoo ubuntu and one fat32.

1st problem bsd has to work in a primary partition so I had to using partition magic (yes it is propietary soft, but really cool) take space from the extended and made one more primary in the end of my hd

What do I have now:

hda1 wintendo xPPP
hda5 ubuntu with reiser fs
hda6 ubuntu with ext3, (yes i killed gentoo, fast but when u have to compile whole gnome.....)
hda8 fat32
hda9 swap

prooooooblably my bsd it is in hda3 thats where knoppix locates something but cant read (god bless this live cd)

Im just posting hoping someone knows how to help me

cfdisk and fdisk give errors to me in every time I start them :(

thx in advance 

](*,)

---

### Post by DutchLau on 2005-05-24
This doesn't really belong in the community chat does it?

I really don't understand your problem. Did you try installing Grub again and letting it "autodetect" your OSes?

---

### Post by T31 on 2005-05-25
yeap, and the poor grub detected only linux and windows, anyway I killed bsd and I will make an installation from zero first windows then bsd then linux

xDDD

thx for reply anyway

---

