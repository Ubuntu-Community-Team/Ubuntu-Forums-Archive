---
title: "passwd command doesn't work with root after change to common-password"
date: 2013-02-21
forum: Server Platforms
---

### Post by strictt9 on 2013-02-21
I'm using 10.04.4 Server.  

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

I changed the common-password file from:
password        [success=1 default=ignore]      pam_unix.so obscure sha512

To this:
password        [success=2 default=ignore]      pam_unix.so min=8 obscure sha512

And now whenever I try to change the root password I get the following:

root@vpn1:~# passwd
passwd: Permission denied
passwd: password unchanged

If I change the line in common-passwd back to it's original text it will work again. 

Any ideas or help would be appreciated.

Thanks!

---

### Post by balaroot on 2013-03-18
success = 2 means, control will skip the next 2 lines if successfull, probably you might have a duplicate line, because i got the same problem and fixed this by removing the extra line required by other tools (like samba) and everything seems to be working. I know this is old thread but posted here for any googler having the same probem

---

