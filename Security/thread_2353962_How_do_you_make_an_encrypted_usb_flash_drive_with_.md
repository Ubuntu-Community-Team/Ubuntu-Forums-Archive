---
title: "How do you make an encrypted usb flash drive with journaling off to save wear?"
date: 2017-02-26
forum: Security
---

### Post by ultragamer2 on 2017-02-26
How can you format a usb flash drive making it encrypted but with journaling off to reduce wear?

---

### Post by HermanAB on 2017-02-27
Well, solid state wear is not a problem any more and the device will likely outlast you, so I would simply use LUKS with ext4 and be done with it.

---

### Post by sudodus on 2017-02-27
You had better ***backup*** your system at regular intervals for two extra reasons,

- encrypted systems are difficult (somethimes impossible) to restore, if they are damaged.

- USB flash drives (at least pendrives) are better but still sensitive to wear and corruption of the internal wear levelling algoritm. (SSDs are quite reliable nowadays.)

See this link, if you still want to turn off journaling,

[UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

but bear in mind that it will be more difficult to repair a damaged file system.

---

### Post by ultragamer2 on 2017-02-27
Ok thanks, btw it's not for a system installed on a usb flash, just portable files on a usb flash.

---

### Post by sudodus on 2017-02-28
When 'only portable files on a usb flash', the risk is rather small, that the drive will be worn out. So I suggest that you keep the journaling, which makes it easier to repair a damaged file system.

It is still a good idea to backup the files on the usb flash drive at regular intervals.

---

### Post by ultragamer2 on 2017-03-01
So does the command
sudo tune2fs -O ^has_journal /dev/sdxy
work with encrypted partitions the same as normal ext4?

---

### Post by sudodus on 2017-03-01
I don't think the encryption makes a difference, but LVM might make a difference. Honestly, I don't know. Let us hope that someone who knows will read this and give you a good answer.

---

