---
title: "Svn + apache sending application/octet-stream content-type headers"
date: 2010-02-04
forum: Server Platforms
---

### Post by gaker on 2010-02-04
Hello,

I recently moved to an SVN Server Running Ubuntu Server 9.10 from RHEL, and installed everything via aptitude.  I have setup a few subversion servers in the past on Ubuntu, but this is the first I have done on 9.10.  I have everything working correctly, but for some reason application/octet-stream Content-Type headers are being sent for every file that is viewed in a browser.  I have worked around this for the time being by adding ForceType text/plain in the Apache vhost file, which is something I have never had to do before.

Subversion is not configured to send any overriding content-type headers, and on the configuration end, the configuration is close to identical to what I have done ranging from Ubuntu 6.10 to 9.04.  So long story short, I'm really scratching my head on this.

Any ideas on what I could be missing?  I have failed to really find any answers in a couple of hours of searching, so any ideas would be appreciated.

Kind Regards,

-greg

eta:  I hope this is the appropriate forum. Apologies if it is not.

---

### Post by gaker on 2010-02-10
Sorry to bump this one up, but if anyone has an idea, I'd be grateful.  

Thanks,

-greg

---

### Post by noway2 on 2010-02-10
If by, "application/octet-stream Content-Type headers" you mean those XML pages.. this is an indication that you are close to having things working but something isn't quite right.  The things to check are: the SvnParentPath which sometimes needs or wants a / after it and the permissions and ownership of repository files.  The files should be owned by apache (www-data) read/writable by owner and readable by everyone else.

If you change any of the apache configuration, be sure to restart apache!

---

### Post by gniss on 2010-03-07
Nothing to do with XML pages; just using webdav to browse script files (php). I found the same problem and the same work around.  Anyone else have any clues on this?

---

