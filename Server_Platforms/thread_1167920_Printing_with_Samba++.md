---
title: "Printing with Samba++"
date: 2009-05-23
forum: Server Platforms
---

### Post by Vegan on 2009-05-23
Since my server's disk fried, I am using a very small disk for the web thing until I get a replacement disk. If you have a ATA 160 GB disk the IBM box would be ecstatic.

I have a HP printer, Deskjet 648C which the manual says is a PCL-3 printer rather than a WinPrinter which is common in the market. The printer even works with DOS.

Attaching the printer is all fine, what I wanted to do was share the printer with Samba as an open resource for Windows users.

If I setup the IBM with a second HD I was wondering if Samba can share based on /dev/sdb rather than /var/www line I have for the web folder share.

My current samba share is very simple, and I leverage my firewall to keep it secure.

Next, how complex is it to have security in a mixed Windows and Linux environment.

---

### Post by HermanAB on 2009-05-23
Well, Windows machines are *always* insecure...

On your firewall, you have to block ports 135-445 to keep Windows safe against the wild wild web.

---

### Post by Vegan on 2009-05-23
I only have port 80 open at present, all the rest are firewalled.

So any thoughts on the printer?

---

