---
title: "I need the following FTP setup"
date: 2007-05-09
forum: Server Platforms
---

### Post by hagen00 on 2007-05-09
Hello community

This is possibly a simple question. I'm want to run ProFTP and want the following setup. 

Users can log into their account at /home/user1 - they can't move down a directory to /home, only stay in /home/user1. Is this standard?

user1 can however make folders (or I do it on their behalf as root) eg /home/user1/user1.1 and /home/user1/user1.2. etc. These users will then also be given FTP login, but will only be able to see their directories specifically. e.g. /home/user1/user1.1 and won't be able to go up a level to /home/user1

I do however want users1 to be able to go into the directory /home/user1/user1.1.

Easy? Is it just adding these specific users each time, setting their appropriate home directories and way we go?
Would I just have to add user1.1 to the group user1 and set appropriate permissions? Should be easy to do. Anything to look out for?

Any potential security risks besides weak passwords?

Many thanks

H

---

### Post by Wim Sturkenboom on 2007-05-09
No experience with ProFTP, but what you're looking for is called 'jail root' and is pretty standard in FTP server applications. A search with google on *proftpd jail* gave [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html) which might be your starting point.

With regards to directories, this is all standard stuff as far as I know (always worked for me like that with vsftpd).

---

### Post by hagen00 on 2007-05-09
Cool :) thanks

---

