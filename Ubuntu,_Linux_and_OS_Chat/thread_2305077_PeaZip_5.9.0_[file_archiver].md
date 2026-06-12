---
title: "PeaZip 5.9.0 [file archiver]"
date: 2015-12-02
forum: Ubuntu, Linux and OS Chat
---

### Post by giorgiotani on 2015-12-02
PeaZip 5.9.0 for Linux was released a few days ago, providing p7zip 15.09 backend in order to support RAR5 format extraction without requiring the additional UNRAR5 plugin based on RarLabs code.


In the new release, in order to reduce dependencies (and provide easier installation), Linux installers contains a minimal set of backend binaries.
Additional backend (*paq, FreeArc, etc) can be added manually from "Optional Formats" external package if needed.
Portable packages are not affected by this change and comes with all backend as in previous releases.


PeaZip for Linux x86 [http://www.peazip.org/peazip-linux.html](http://www.peazip.org/peazip-linux.html)

PeaZip for Linux x86-64 [http://www.peazip.org/peazip-linux-64.html](http://www.peazip.org/peazip-linux-64.html)

---

### Post by yoshii on 2015-12-05
thanks!  where can I get RAR support?  I tried the "Optional Formats" external package, but it didn't include a res for RAR... ?

---

### Post by giorgiotani on 2015-12-05
RAR format is handled through p7zip backend, which was updated to 15.09 version adding support for RAR5 files, the component is Rar.so in PeaZip/res/7z/codecs/.
It is featured in the main installers as well as in portable versions packages, the Optional Formats plugin is not needed to work with RAR files.

---

### Post by yoshii on 2015-12-05
Oh hey, thanks.  That is good news.  The program looks nice too.  I've seen it develop over the years and I like the more simplified settings to some degree.  
I had been using BandiZip via Wine just for RAR files, but this is sort of clumsy.  It will be nice to use something Linux oriented instead.  Thanks.

---

