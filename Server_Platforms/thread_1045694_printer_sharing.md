---
title: "printer sharing"
date: 2009-01-20
forum: Server Platforms
---

### Post by wlraider70 on 2009-01-20
I am currently trying to get a small school network up.
I am using ubuntu desktop (i needed the GUI)  for the server.
All other boxes are XP.

the printer i have is a HP Business Inkjet 1100 it is connected to the router.

I have samba runing for file sharing, but im not sure how to cong the printer?

Do i need to install it locally first since the Linux box will be the print sever?
If so where would i get the drivers?

thanks.

---

### Post by Thirtysixway on 2009-01-20
You can set it up on CUPS.  Then add the printer by its network address which would be like

[http://ipofserver:631/printername](http://ipofserver:631/printername)

---

### Post by wlraider70 on 2009-01-20
I assuming CUPS will play nice with samba.

is there a aptitude or apt-get command for CUPS?

---

### Post by dmizer on 2009-01-20
> **wlraider70 said:**
> I assuming CUPS will play nice with samba.

is there a aptitude or apt-get command for CUPS?

Cups and samba are two different protocols. Neither will interfere with the other.

You already have cups installed. Just configure your printer sharing from system > administration > printing

---

### Post by dmizer on 2009-01-20
> **Thirtysixway said:**
> You can set it up on CUPS.  Then add the printer by its network address which would be like

[http://ipofserver:631/printername](http://ipofserver:631/printername)

I believe this is incorrect, I think it should be [noparse]http://ipofserver:631/printers/printername[/noparse]. You should be able to browse for the printer from Windows though.

---

