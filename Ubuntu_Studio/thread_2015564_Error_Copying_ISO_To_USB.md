---
title: "Error Copying ISO To USB"
date: 2012-07-03
forum: Ubuntu Studio
---

### Post by johny why on 2012-07-03
hi, i mounted the iso, and drag-copied it's contents to a USB drive.

The copy completed fine, but there were copy errors:
```
...
Copying /mnt/+mnt+sdc1+ubuntustudio-12.04-dvd-i386.iso/dists as /mnt/sdb1/dists
ERROR: Operation not permitted
ERROR: Operation not permitted
...
Copying /mnt/+mnt+sdc1+ubuntustudio-12.04-dvd-i386.iso/preseed as /mnt/sdb1/preseed
ERROR: Operation not permitted
Done
There were 3 errors.
```

All other files copied ok.

what should i do?

thanks!

---

### Post by sudodus on 2012-07-03
What kind of iso file is it, and how do you want to use it?

If it is an iso file for an install CD or USB drive, there are several ways to make it.

---

### Post by oldfred on 2012-07-03
You cannot just copy an install ISO like that. The new one's will allow a full install with dd but unless you really understand command line using dd can be dangerous.

Most use the procedure from the Ubuntu web site where you download the ISO.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by johny why on 2012-07-03
> **oldfred said:**
> You cannot just copy an install ISO like that. 

You can, if you are creating a usb with the syslinux method, which i've done successfully to create many boot usb's. 

> **sudodus said:**
> What kind of iso file is it, and how do you want to use it? If it is an iso file for an install CD or USB drive, there are several ways to make it.

this is the ubuntu studio CD. Hope i'm posting in the correct forum. I'm using the syslinux method to create a usb drive, which involves copying all files off the ISO onto the USB. 

Perhaps this installer ISO simply cannot be burned to USB? (As i understand, Ubuntu Studio is not a live CD, only an installer.)

Maybe its just a bad ISO-- now re-downloading from ubuntustudio.org

---

### Post by sudodus on 2012-07-03
> **johny why said:**
> You can, if you are creating a usb with the syslinux method, which i've done successfully to create many boot usb's. 



this is the ubuntu studio CD. Hope i'm posting in the correct forum. I'm using the syslinux method to create a usb drive. But, perhaps this installer ISO simply cannot be burned to USB? (As i understand, Ubuntu Studio is not a live CD, only an installer.)

aybe its just a bad ISO-- now re-downloading from ubuntustudio.org

OK, I think you know what you are doing.

I would make a partition on the usb drive, add boot and lba flags and format it to FAT32. Then I would use Unetbootin to make an install USB drive of it

or

try if it would work to use dd directly.

See the following posts
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by gordintoronto on 2012-07-03
+1

---

