---
title: "Rkhunter comes with a warning"
date: 2011-07-13
forum: Security
---

### Post by ruliezz on 2011-07-13
Hi All,

Just I install the rkhunter tool via apt-get install rkhunter. When I had run the rkhunter check, rkhunter comes with a warning about "GasKit Rootkit", i dont understand what it is, but maby your can help me.

This server is install new last and maby 1 week old, so i don't understand why this happends.

---

### Post by dFlyer on 2011-07-13
Have you tried a google search on your reply. There seems to be a lot of information on it.

---

### Post by ruliezz on 2011-07-13
Of course, but i dont found any thing, maby you can help me?

---

### Post by unspawn on 2011-07-13
Checking out the current release code you can find file and directories names to check out yourself:
```

  7196          # GasKit Rootkit
  7197          GASKIT_FILES="${RKHROOTDIR}/dev/dev/gaskit/sshd/sshdd"
  7198          GASKIT_DIRS="${RKHROOTDIR}/dev/dev
  7199                       ${RKHROOTDIR}/dev/dev/gaskit
  7200                       ${RKHROOTDIR}/dev/dev/gaskit/sshd"
  7201          GASKIT_KSYMS=
  7202
(..)
  8409  
  8410          # Suspicious startup file strings
  8411          RCLOCAL_STRINGS="/usr/bin/rpc.wall:Linux Rootkit (LRK4)
  8412                           sshdd:GasKit Rootkit
  8413                           hidef:Knark Rootkit
  8414                           /usr/bin/.etc:Dica-Kit Rootkit"
  8415  

```
* RKHROOTDIR usually equals "/" and RCLOCAL_STRINGS means running 'strings' on files and grepping for search terms.


> **ruliezz said:**
> i dont found any thing
...then your search-fu may be low as there AFAIK is one entry only in the rkhunter-users mailing list (*which actually is listed as the preferred first point of contact instead of *any* forum regardless of how friendly, knowledgeable or helpful members are or not*): [http://sourceforge.net/mailarchive/forum.php?thread_name=20080222161213.77CB515803D%40mailserver6.hushmail.com&forum_name=rkhunter-users](http://sourceforge.net/mailarchive/forum.php?thread_name=20080222161213.77CB515803D%40mailserver6.hushmail.com&forum_name=rkhunter-users)

---

### Post by ruliezz on 2011-07-14
Thanks all for the helpfull answers is it maby possible that error the mounted usb disk? On this disk is a ubuntu server os on it. This was my old disk. Maby is that the problem.

I try to find out and do my best :)

Do you have any idea?

---

### Post by ruliezz on 2011-07-14
Yes! I found out what the problem is. My LVM named "Dev" en lvm is in /dev always ;)

---

