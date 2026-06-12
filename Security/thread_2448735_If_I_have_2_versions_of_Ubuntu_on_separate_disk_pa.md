---
title: "If I have 2 versions of Ubuntu on separate disk partitions and open malware....."
date: 2020-08-13
forum: Security
---

### Post by jedi123 on 2020-08-13
Hello, if I have 2 separate disk partitions  and  have 2 versions of ubuntu running on each partition, and I open malware on one of the  ubuntu partitions, can  the malware access personal  files on the other ubuntu partition ? 

Thanks.

---

### Post by TheFu on 2020-08-14
Yes, it could, unless the other storage is 
[LIST]
[*]unavailable through permissions from the current userid and you haven't allowed sudo to run on that account
[*]encrypted and not "opened"
[*]read-only storage, like a DVD/CDROM/
[/LIST]

Being "possible" and being "likely" are often very different things.

Anything you can do manually, malware can accomplish if written that way, but if you have a strong encryption passphrase or use 2FA, then the malware would be stopped ... until the encrypted storage gets opened.

---

### Post by jedi123 on 2020-08-14
Ubuntu 16.04lts has full disk encryption 

Ubuntu 20.04 has no password security 

All my important files are on 16.04 Ubuntu partition on the desktop documents and home folder 

The 20.04 is just for downloading star trek etc.

This would keep me safe as long as I keep no personal stuff on the 20.04 partition correct?

---

### Post by TheFu on 2020-08-14
No. it is more complicated than that.  Loopholes don't provide security.

Need daily, versioned, backups and don't allow physical access to anyone untrusted. Every different user should have their own account with their own password. This way, they can only harm themselves. The system won't be harmed by a normal user being hacked, unless it is unpatched or you are a specific target by some organization.

There is a sticky thread in the Security subforum here which explains normal security for Linux systems.

---

