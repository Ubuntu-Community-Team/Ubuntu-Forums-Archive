---
title: "Rufus versus unetbootin"
date: 2013-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by alphacrucis2 on 2013-08-06
I'm just wondering if anyone has tried Rufus for creating live usb flash images and if it was ok. I have used unetbootin before but Rufus appears to have additional features. The main downside of Rufus I can see is that there doesn't appear to be a Linux version although it will create Linux boot images.

---

### Post by sudodus on 2013-08-07
Rufus is new to me :-)

If you want an overview of tools for creating live usb flash images, you can look at this Ubuntu wiki page

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by cariboo on 2013-08-08
I use dd:

```
sudo dd if=<name of iso> of=sdX bs=1M
```

where sdX = your usb device.

---

### Post by sudodus on 2013-08-08
> **cariboo907 said:**
> I use dd:

```
sudo dd if=<name of iso> of=sdX bs=1M
```

where sdX = your usb device.

Yes ***dd*** is fast and reliable when you get the input and output correctly ... so I made the shell script ***mkusb*** to reduce the 'disk destroyer' risk using dd ;-)[URL="http://ubuntuforums.org/showthread.php?t=1958073"]

Howto make USB boot drives[/URL]

---

### Post by Cheesemill on 2013-08-08
I always use the dd command whenever possible, but it can only be used with hybrid isos.

For everything else I've always had a much better experience with UNetBootin than with Ubuntu's Startup Disk Creator.

---

