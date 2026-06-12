---
title: "Triple Boot Kali Linux, Windows 8 and OpenElec bootloader querie"
date: 2015-06-04
forum: Ubuntu/Debian BASED
---

### Post by peter196 on 2015-06-04
*edited due to being moved*

i will need some help.

```
menuentry "OpenELEC.tv" {
   set root=(hd0,3)
   linux /KERNEL boot=/dev/sda3 disk=/dev/sda4 quiet
}

menuentry "OpenELEC.tv (Textmode)" {
   set root=(hd0,3)
   linux /KERNEL boot=/dev/sda3 disk=/dev/sda4 textmode quiet
}

menuentry "OpenELEC.tv (Debugmode)" {
   set root=(hd0,3)
   linux /KERNEL boot=/dev/sda3 disk=/dev/sda4 debugging textmode quiet
}

```

i tried the same thing, though I'm trying to get a triple boot system up and running, with Windows 8.1(soon 10) kali linux and openelec, but if i use your code it will simply state "error: file not found"

I'm still rather new at messing with grub and more than two systems on one machine. in my case i edited it so it fitted with my partitions. so it became
```

[COLOR=#000000][FONT=Ubuntu Mono]menuentry "OpenELEC" {[/FONT][/COLOR]   set root=(hd0,7)
   linux /KERNEL boot=/dev/sda7 disk=/dev/sda8 quiet
}

```[COLOR=#222222][FONT=Verdana]

this is most likely wrong, as it does not work, any idea as to why, or any help?[/FONT][/COLOR]

---

### Post by oldos2er on 2015-06-04
Moved to Ubuntu/Debian BASED.

---

