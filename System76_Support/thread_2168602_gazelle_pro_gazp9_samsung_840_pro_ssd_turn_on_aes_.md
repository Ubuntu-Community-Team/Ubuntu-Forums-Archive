---
title: "gazelle pro gazp9 samsung 840 pro ssd turn on aes encryption"
date: 2013-08-18
forum: System76 Support
---

### Post by David_Singh on 2013-08-18
Just got a gazelle pro with Samsung 840 pro ssd. Can't figure out on the bios screen how to set up the Samsung aes hardware encryption. Does anyone know what to do?

---

### Post by isantop on 2013-08-20
Our firmware doesn't support hard drive passwords, which are required for the hardware encryption features. Instead, we recommend using Ubuntu's built-in software-based home-folder encryption. If your company policy requires full-disk encryption, then you should use Ubuntu's software full-disk encryption by reinstalling Ubuntu. 

Hardware encryption offers very little performance difference, and if the password for the drive is lost, the drive is completely unusable. With software-based encryption, you can still format and use the drive, even if you forget the password (your data is inaccessible and irrecoverable in either case).

---

