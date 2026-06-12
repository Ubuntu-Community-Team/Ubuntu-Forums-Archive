---
title: "How do you typically stop printer drivers from phoning home?"
date: 2013-12-06
forum: Security
---

### Post by augustrigmarole on 2013-12-06
How would a security-savvy Linux user stop a printer driver from phoning home? Unfortunately, I don't really have the option of not using the printer.

I read an article here about Lexmark printers phoning home: [http://www.theregister.co.uk/2004/11/15/lexmark_spyware/](http://www.theregister.co.uk/2004/11/15/lexmark_spyware/)

Although Lexmark denied that they gathered personal information, I don't see an explicit denial that they gathered the printer serial number, which could uniquely identify the user.

Since I am using a Lexmark printer myself, I'm worried the same thing could happen to me. Does anyone have any suggestions? If I could deny it Internet access while granting it access to the local network so it can still print, I think I'll be ok.

By the way, the printer itself (hardware) cannot phone home; I blocked the printer from accessing the Internet via router settings. If anything can phone home, it'll be the driver.

---

### Post by cariboo on 2013-12-06
That article you quoted was from 2004, is there anything a little more recent?

---

### Post by augustrigmarole on 2013-12-06
Not that I know of. However, adware in printer drivers is not really something new (e.g. [http://socratesfoot.wordpress.com/2011/06/30/113/](http://socratesfoot.wordpress.com/2011/06/30/113/)). A printer driver is no different from any other piece of software; it can contain malware.

---

### Post by cariboo on 2013-12-07
The article for HP drivers, was for Windows drivers. Does the same thing occur with Linux drivers? The driver for my Brother HL-5250DN uses a GPL license, so the driver can be checked for any unwanted additions.

---

