---
title: "TFTP for Dummies!!!"
date: 2009-04-07
forum: Server Platforms
---

### Post by LimburgerCheese on 2009-04-07
I want to create a TFTP server on my Uby 8.10 so I can manage files from a Cisco router.

I'm busy for about 2 - 3 hours, installed many bits without a positive result... (tftpd, tftp-hpa, tftpgui)

I did prefer a graphical one, but at this moment I'd also be happy with a text-based.

Can somebody help me? Or is this Dummy not the only one in town? ;)

Thanks in advance!

---

### Post by HermanAB on 2009-04-07
The magical bit is that the directory served up by the tftp server must be *read only* else nothing will work.

---

