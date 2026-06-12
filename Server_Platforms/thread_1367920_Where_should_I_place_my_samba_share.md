---
title: "Where should I place my samba share"
date: 2009-12-30
forum: Server Platforms
---

### Post by dinuzz on 2009-12-30
Dear all

I have Ubuntu Server running on a older hardware. I have one HD installed and the OS installed on it. Where should I store the Samba shares? In the /srv/ directory? Or just simply in the root directory? What is the common practice?

thanks

---

### Post by capscrew on 2009-12-30
> **dinuzz said:**
> Dear all

I have Ubuntu Server running on a older hardware. I have one HD installed and the OS installed on it. Where should I store the Samba shares? In the /srv/ directory? Or just simply in the root directory? What is the common practice?

thanks

The root directory ( /) is definitely NOT the place to store Samba shares.  The directory */root* is also not the place.  The directory */srv* can be used as this is where the Filesystem Hierarchy Standard recommends. See [**_[COLOR="DarkSlateGray"]here   [/COLOR]_**]("http://www.pathname.com/fhs/pub/fhs-2.3.html")for details.

I use a slightly different system.  I use */smb* for my Samba shares file system (i.e. /smb/backup and /smb/pictures etc.).

---

