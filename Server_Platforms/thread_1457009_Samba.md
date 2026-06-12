---
title: "Samba"
date: 2010-04-18
forum: Server Platforms
---

### Post by Vegan on 2010-04-18
I was wondering would it be very hard to configure SAMBA to be able to have linux user accounts available to be opened from Windows so that web pages could be updated etc?

each account is created with adduser in linux

suggestions?

---

### Post by SRST Technologies on 2010-04-18
It depends on where the source directory for those users websites are.  Samba on Ubuntu's default smb.conf file includes an example share for each user's home directory.  Uncommenting the relevant lines and restarting samba makes each user's home directory show up.

That seems irrelevant since most user's websites are in /var/www/something by default, but you could make a simple soft link inside each user's home directory to their personal website directory.  Bingo, problem solved.

---

