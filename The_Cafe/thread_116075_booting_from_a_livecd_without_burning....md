---
title: "booting from a livecd without burning..."
date: 2006-01-11
forum: The Cafe
---

### Post by Specialsauce on 2006-01-11
i need to figure out if its possible to boot from a livecd without burning it...

---

### Post by erikpiper on 2006-01-11
????????????

Confused...

Is this a joke?

---

### Post by Specialsauce on 2006-01-11
i didnt realize my question was THAT stupid :'(

---

### Post by erikpiper on 2006-01-11
No. I think I am just confuzed.....

I think you can boot into linux under another OS.. See DSL... BUT a live CD is a ISO (Disk image..)

---

### Post by Specialsauce on 2006-01-11
yes, i have an iso, ut no blank CDs. i want to boot from the ISO... is it possible to like mount it or somethin and then boot from the mounted location...?

---

### Post by erikpiper on 2006-01-11
Mabe if you could get the computer to boot from USB or something...

I thought you meant on other computers...... Mabe you can put it on a spare HD and use grub.......... I really dont know how.. :(

---

### Post by BSDFreak on 2006-01-11
You'll need to boot a kernel off of your hard drive (or floppy) and have the mount tools on there so you can mount it as a loopback device. I'd extract it instead and boot it with Grub/Lilo.

---

### Post by Burgundavia on 2006-01-11
This is actually quite simple, provided you know what are you are doing or being flamed. Basically you need Qemu and a whole lot of RAM. Qemu is a disc emulator, similar to VMware but open source. It can be installed out of the ubuntu repos, in universe.

Then head to the command line and type "qemu -cdrom YOURLIVECD.iso"

That should do it.

Corey

---

### Post by Specialsauce on 2006-01-11
[QUOTE=Burgundavia]This is actually quite simple, provided you know what are you are doing or being flamed. Basically you need Qemu and a whole lot of RAM. Qemu is a disc emulator, similar to VMware but open source. It can be installed out of the ubuntu repos, in universe.

Then head to the command line and type "qemu -cdrom YOURLIVECD.iso"

That should do it.

Corey[/QUOTE]
thank you

---

