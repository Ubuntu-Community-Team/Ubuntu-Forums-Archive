---
title: "ubuntu/kubuntu installers crash during install"
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by lamb123 on 2013-04-07
Ubuntu 12.04.2 and secure-remix installed fine.

BIOS is set to legacy + UEFI. Latest BIOS version.
[IMG]http://i.imgur.com/E71KLI6.png[/IMG]


Both booted fine though from USB stick when I "Tryed Ubuntu".

---

### Post by ajgreeny on 2013-04-07
Exactly what point does it crash?

There seems to be a problem on some hardware with the ubiquity-slideshow crashing and taking the whole installation with it, just leaving a spinning cursor.  If that is what happens for you try ```
sudo apt-get remove ubiquity-slideshow-kubuntu
``` and then try installing again; it may be just what is needed.

If not I can not think of other suggestions except checking your .iso file against the md5sum hashes [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by lamb123 on 2013-04-08
it crashes during installing language packs when 30% is done

I can just continue using ubuntu from usb when I close the crash window

---

### Post by ajgreeny on 2013-04-08
I think it worth trying my suggestion of removing the slideshow before installing again.

---

### Post by lamb123 on 2013-04-08
same problem remained

---

