---
title: "What's the difference original ubuntu iso vs. custom ubuntu iso by cubic?"
date: 2020-02-24
forum: Windows
---

### Post by sk1561 on 2020-02-24
I have write ubuntu iso image on usb stick using yumi-uefi([https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)) .
Yumi found ubuntu iso with problem.
But, customized ubuntu using cubic was not detected by yumi.
Of course, options of "see all iso" in yumi find out custom ubuntu iso.
My question is what the difference of original and custom ubuntu iso is.
Name or [B]MD5 or etc?
Thanks.
[/B]

---

### Post by Frogs Hair on 2020-02-25
It appears that an official download source is used by yumi, but what is meant by custom? I don't know how you would verify the download based on the home page information.

This link maybe of use if you created the ISO. The yumi software could be checking for MD5 when an ISO is added.

 [https://lifehacker.com/create-iso-disk-images-and-generate-md5-checksums-268304](https://lifehacker.com/create-iso-disk-images-and-generate-md5-checksums-268304)

---

### Post by ipv on 2020-03-14
> **sk1561 said:**
> Name or **MD5 or etc?**

name.

> **Frogs Hair said:**
> The yumi software could be checking for MD5 when an ISO is added.

an official ubuntu iso downloaded, md5 & sha verified will not be identified neither by uui nor by yumi if you have re-named the iso.

uui & yumi only identify the iso if it has the official / original name, for example ' ubuntu-18.04.4-desktop-amd64 '.

if you change the name to anything other than that uui & yumi will not identify it.

---

