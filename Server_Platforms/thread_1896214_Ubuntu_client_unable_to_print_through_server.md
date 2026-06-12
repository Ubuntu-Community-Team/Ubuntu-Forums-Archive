---
title: "Ubuntu client unable to print through server"
date: 2011-12-16
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-12-16
Have added an Epson Stylus Photo R265 printer installed on an Ubuntu 11.04 Server to a Ubuntu 11.10 desktop version.

Everything appears to be correct until you attempt to print a test page.

In 'Policies', 'Enabled' is unchecked. As soon as you check it, and try to print, it unchecks itself and errors out.

The same server printer is fine printing from any Windows client.

Any ideas, please?

TIA

---

### Post by ChrisRChamberlain on 2011-12-16
The Windows path to this printer is:-

[http://servername:631/printers/EPSON-Stylus-Photo-R265](http://servername:631/printers/EPSON-Stylus-Photo-R265)

So, assuming this to be a SMB printer and path incorrect, what would be the equivalent Ubuntu path, please?

---

### Post by ChrisRChamberlain on 2011-12-17
Used 'Find Network Printer' option, 
entered 'http://192.168.0.49:631/printers/EPSON-Stylus-Photo-R265'
and issue resolved!

---

