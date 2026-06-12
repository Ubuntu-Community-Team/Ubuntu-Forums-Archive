---
title: "Question about persistence as a security technique"
date: 2014-12-12
forum: Security
---

### Post by username931 on 2014-12-12
Two good articles on persistent devices are:
        [http://tuxtweaks.com/2014/03/create-linux-mint-persistent-live-usb](http://tuxtweaks.com/2014/03/create-linux-mint-persistent-live-usb)
and
        [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

The first uses a flash drive.  It is more convenient and faster, especially if a USB 3 drive is used.
The second, however, has potential security advantages.

For example, take the following hypothetical (based on an actual) case.  A taxpayer is paranoid enough to only use a persistent Live CD when dealing with the IRS on the internet.  His IRS account is hacked, his address changed, a return is filed requesting a substantial refund.  Then, after a check for the refund is sent to the new address and cashed, the IRS demands that the taxpayer return the stolen funds, claiming that the loss resulted from the taxpayer's failure to maintain a secure computer system.  The paranoid taxpayer is able to use the log files on the persistent device to close the case in his favor.

My question is:  Can I have the best of both devices?  Can an iso9660 read-only file system from a Live CD be put on a USB 3 flash drive together with a casper-rw partition?  I have tried without success.  Perhaps the initrd and/or the kernal arguments need changing.  Any assistance would be greatly appreciated.

---

### Post by sudodus on 2014-12-12
If you create a persistent live system with Unetbootin or the Startup Disk Creator, you can edit the boot menu to include one entry with persistence and one entry without persistence (use or omit the boot option persistent). So when you boot without persistence, the content of the casper-rw file will not be used, and you have that untouched system from the iso file.

---

### Post by pfeiffep on 2014-12-12
I was successful making a USB 2 stick bootable and persistent using instruction found [here]("https://help.ubuntu.com/community/Installation/FromUSBStick")
I gave up the using because USB 2 was too sluggish for my liking.

---

### Post by Hungry Man on 2014-12-12
If you use a read-only file system you lose the ability to patch the system, making exploitation much much MUCH easier. So it's terrible for security, actually, despite what people will tell you.Ask yoursel f- if you use a LiveCD for banking, and an attackef compromises the system, why would they care about persistence? They've just owned the session they care about. And it was made easier because you can't patch it.If you really want a secure system there are more effective ways.

---

### Post by HermanAB on 2014-12-13
Yup - with a persistent system, you got to be able to make a new one regularly.  Same when you use a special VM for banking.  Make a new one each time there is a major security update, or at least once or twice a year with a new Ubuntu release.

---

### Post by sudodus on 2014-12-13
> **HermanAB said:**
> Yup - with a persistent system, you got to be able to make a new one regularly.  Same when you use a special VM for banking.  Make a new one each time there is a major security update, or at least once or twice a year with a new Ubuntu release.

Also - with a live system without persistence, you got to be able to make a new one regularly.  Same when you use a  special VM for banking.  Make a new one each time there is a major  security update, or at least once or twice a year with a new Ubuntu  release.

Looking outside the Ubuntu family, you can use ***Knoppix***, and download a new iso file as soon as it is released by Knoppix. (Knoppix is made to run live (or persistent live alias poor man's install).) If you want even higher security you can run ***Tails***, and download a new iso file as soon as it is released by Boum, but it is rather inconvenient, and I would say not necessary for private economic tasks to run TOR, which is default in Tails.

-o-

I think that if you boot and only do your banking business, a live system can be rather safe. Avoid browsing to other web sites before or after the banking:

```
Boot
Bank
Reboot
```

---

### Post by C.S.Cameron on 2014-12-13
If you make a Live USB* and add a blank casper-rw or home-rw file after, you can get persistent at banking time by booting and pressing F6 then adding " persistent", (without quotes).
When done, you can save the used -rw  file someplace secure and add a new blank -rw file to the drive.
I am real worried about loosing a Persistent flash drive with banking info on it as casper-rw files are easy to open.

* Without persistence or reserved extra space

---

### Post by open2reason on 2014-12-13
If considering persistence as a way of keeping things safe and secure between sessions then a short time reviewing warnings about persistence [https://tails.boum.org/doc/first_steps/persistence/warnings/index.en.html](https://tails.boum.org/doc/first_steps/persistence/warnings/index.en.html) via Tails OS [https://tails.boum.org/index.en.html](https://tails.boum.org/index.en.html) could be time well spent if one is that way inclined.

---

### Post by username931 on 2014-12-15
First, thanks for the responses.  I was able to create a usb-based system using usb-creator-gtk.  Please understand that my primary concern is the legal responsibility created by accepting a financial site's terms of service.  If a defendant had believable expertise in computer security, a jury would probably believe him, or her.  Otherwise, competent cross-examination and conflicting expert testimony might well convince a jury that there was a screw-up.  A jury will probably have a bias against the user of anything other than the most advertised security software, i.e. what they use.

Physical evidence really influences juries.  That alone favors using a cd, even if it needs replacing from time to time.  Also, note the following output from df, first on a cd with a 500M flash drive and the second on a 4G flash drive with a rofs from the image of the first cd: (Please excuse the lack of formatting.  I can't figure out how to use tabs in this editor)

Filesystem     1K-blocks   Used Available Use% Mounted on
/cow              483044  56536    401576  13% /
udev             1528252      4   1528248   1% /dev
tmpfs             307696   1164    306532   1% /run
/dev/sr0          712704 712704         0 100% /cdrom
/dev/loop0        659328 659328         0 100% /rofs
none                   4      0         4   0% /sys/fs/cgroup
tmpfs            1538468      4   1538464   1% /tmp
none                5120      0      5120   0% /run/lock
none             1538468      0   1538468   0% /run/shm
none              102400     16    102384   1% /run/user
/dev/sdb1         483044  56536    401576  13% /media/lubuntu/casper-rw

Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             3034740   29444   2847808   2% /
udev             1001736       4   1001732   1% /dev
tmpfs             202552    1040    201512   1% /run
/dev/sda1        3903016 3870388     32628 100% /cdrom
/dev/loop0        653568  653568         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1012748       4   1012744   1% /tmp
none                5120       4      5116   1% /run/lock
none             1012748       0   1012748   0% /run/shm
none              102400      20    102380   1% /run/user

Anyway, they are close, but not identical.  Proving their functional identity might be difficult.  So, even here, there is a trade-off between convenience and proof.

Thanks again.

---

