---
title: "Ubuntu 8.04 LTS and PHP"
date: 2009-09-10
forum: Server Platforms
---

### Post by gac816 on 2009-09-10
Hello Everyone. I am trying to get v.8.04LTS w/PHP5 to connect to MSSQL 2005. From reading other posts, I am beginning to think that PHP5 v5.2.4 and FreeTDS v.0.63 that is part of 8.04 does not support MSSQL 2005. I can connect to MSSQL 2000. I had a test server with 9.04 and had no issues. Any suggestions on how to make this work without compiling new versions? I would like to keep with published packages to make future updates easier and to stay with the LTS version as this will be a production server.
 
Thanks in advance for our suggestions.

---

### Post by Bachstelze on 2009-09-10
You can either:

1) Install the PHP packages from a later version of Ubuntu, while leaving all other packages as they are. It would work, but with the downside that you would get no automatic updates.

2) Ask someone to build a Hardy package of your desired version of PHP for you (or do it yourself). Once again, no automatic updates.

3) Upgrade.

---

### Post by gac816 on 2009-09-11
Thanks for your response.  How do I install packages from a different version?  I tried running apt-get install... and spedifying a newer version, however the message came back saying it couldn't find that version.
 
Thanks again,

---

### Post by Bachstelze on 2009-09-11
You either:

1) Temporarily add the repository for that version and remove it when you're done, or

2) Download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them manually.

---

### Post by gac816 on 2009-09-11
Thanks for the info.  I got the newer versions installed, but it didn't fix my problem.... back to the drawing board.
 
Thanks again.

---

### Post by Wim Sturkenboom on 2009-09-12
I would use what works for now (9.04). At the moment that the next LTS comes out (10.04) upgrade or re-install (not sure what is the better option)

The only reason I'm aware of to use LTS server is the 5yr support (a very valid reason and the 3yr support on the desktop is why I use LTS on the desktop).

---

