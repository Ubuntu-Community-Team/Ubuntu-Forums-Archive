---
title: "Anyone ever actually used the x86 Ubuntu Touch image available for download?"
date: 2016-09-22
forum: Ubuntu Development Version
---

### Post by T2uiYKb7 on 2016-09-22
[SIZE=3][COLOR=#008000]1:

[/COLOR][/SIZE]This is in regard to the i386 32-bit daily version available from here:[ http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/")

What hardware is this compatible with? 

Will it configure its self automatically like a normal Ubuntu install will or is it like an Android ROM where it only works with very specific hardware?

I [COLOR=#008000]think [/COLOR]the link [COLOR=#008000]above [/COLOR]is compatible with a large range of hardware and is different than these ROM style .img's below that are obviously for specific hardware.

[https://developer.ubuntu.com/en/phone/devices/devices/](https://developer.ubuntu.com/en/phone/devices/devices/)

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

[SIZE=3][COLOR=#008000]2:[/COLOR][/SIZE]

I understand how to copy the .img to the internal storage of my tablet (dd or cp to /dev/sda) but my tablet is UEFI (only) and this doesn't have a /efi/boot/bootx32.efi file.

Can I simply copy the bootx32.efi and grubx32.efi from a normal Ubuntu install into a /efi/boot/ directory? The file structure seems the same.

[COLOR=#008000]Has anyone successfully booted the .img in the top link on a UEFI only device?[/COLOR]

Thanks any help would be great.

Edit: My tablet does boot anything with a correctly configured /boot/efi/bootx64.efi automatically even if it's simply dd'd or extracted to a drive. (I realize this is only if it's a bootx64.efi file that's configured correctly with a compatible OS.)

---

### Post by Bucky Ball on 2016-09-22
*Thread moved to **Ubuntu Development Version**.*

---

### Post by ventrical on 2016-09-22
'Can't find server' error for your top link.

---

### Post by ventrical on 2016-09-22
> **Bucky Ball said:**
> *Thread moved to **Ubuntu Development Version**.*

Bucky Ball..

Cannot find server: error @ original   [http://http//cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://http//cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)

I asked the OP about it . No reply.

Regards..

---

### Post by howefield on 2016-09-22
OP link fixed, removed the double "http://".

---

### Post by T2uiYKb7 on 2016-09-22
Sorry just checked back now, apologies for the typo in the URL. Anyone here with experience with this Ubuntu Touch .img file?

---

### Post by T2uiYKb7 on 2016-10-03
Has anyone ever actually used the x86 Ubuntu Touch image available for download?

Surely someone has, it's like it doesn't exist.

---

