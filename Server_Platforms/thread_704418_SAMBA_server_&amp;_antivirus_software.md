---
title: "SAMBA server &amp; antivirus software"
date: 2008-02-22
forum: Server Platforms
---

### Post by InfoTech on 2008-02-22
I installed a SAMBA file server on Ubuntu 7.10 server for a small network of 15 users. I would like to provide (at least basic) anti virus support. Can you recommend some good GPL AV software  that is easily installed in Ubuntu? 

Thanks!

---

### Post by freebeer on 2008-02-22
I've never used it, but the most common AV I've seen mentioned on these boards is "clamav".  It's in the repositories.

---

### Post by Brazen on 2008-02-22
"clamav" is pretty much the only option for gpl av software.

---

### Post by InfoTech on 2008-02-24
Thanks guys. I read some about ClamAV. WHat is recommended: using it as daemon, or regular usage? Could not find anything on how to use it with SAMBA? Thanks again.

---

### Post by astrotech226 on 2008-02-24
I don't think running clamav on it's own is what you are looking to do.  If you want samba to scan the files as they are served out, you need to do this out of a vfs module.

Here's a debian "how to" install the samba vscan module.

[http://www.howtoforge.com/forums/showthread.php?t=3706]("http://www.howtoforge.com/forums/showthread.php?t=3706")

Here's a different module that uses a different approach.  I've never used this one, but the ideas look promising.  Scanning from different servers, scan once, etc...

[URL="http://olivier.sessink.nl/scannedonly/"]
http://olivier.sessink.nl/scannedonly/[/URL]

---

