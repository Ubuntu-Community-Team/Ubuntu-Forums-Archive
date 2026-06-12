---
title: "Hacked through Youtube? Printer port vulnerabilities and access"
date: 2018-12-26
forum: Security
---

### Post by alvinmoneypit on 2018-12-26
Hi,
Just been hacked this AM. During a single page print job, the attacker posted multiple pages of the same doc to my printer; the only difference in the docs is the number printer hacked.  I've attached the document the attacker left.  It claims that Port 631 is open to the internet and vulnerable.  Was this through Firefox?  What other access have they potentially gained through this?

---

### Post by Frogs Hair on 2018-12-26
12.04 is no longer supported so I would backup the files to a removable device or cloud if possible and install a supported release and DE of your choice.


[https://www.ubuntu.com/download/flavours](https://www.ubuntu.com/download/flavours)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by alvinmoneypit on 2018-12-26
Not the question I asked, but thanks anyway - I don't know  what a 'DE' is.

---

### Post by Frogs Hair on 2018-12-26
There are no more security updates for 12.04, so that's I why suggested installing a newer more secure release. A DE is a desktop environment and there are more options since 12.04 was released hence the flavours link I posted.

---

### Post by alvinmoneypit on 2018-12-27
Type "localhost:631" without quotes into a browser address bar.  This should bring up the CUPS page.  Click on the "Administration" tab at the top of the screen.  Uncheck the box in the "Server Settings" "advanced" section column labeled, "Share printers connected to this system" and "Allow printing from the internet".  Also uncheck "Allow remote administration".  Those actions will close Port 631 to the internet. Alternatively, there are many ways to disable access to this port from the internet, the easiest and most effective may be simply including it in your firewall. If you disable port 631 internally by altering CUPS configuration file, be sure to re-start CUPS.

---

### Post by Frogs Hair on 2018-12-27
> **alvinmoneypit said:**
> Type "localhost:631" without quotes into a browser address bar.  This should bring up the CUPS page.  Click on the "Administration" tab at the top of the screen.  Uncheck the box in the "Server Settings" "advanced" section column labeled, "Allow printing from the internet".  Alternatively, there are many ways to disable access to this port from the internet, the easiest and most effective may be simply including it in your firewall. If you disable port 631 internally by altering CUPS configuration file, be sure to re-start CUPS.

Good to know, but you still have an operating system with no supported update/security repositories installed.

---

