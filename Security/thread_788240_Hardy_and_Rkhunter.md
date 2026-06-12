---
title: "Hardy and Rkhunter"
date: 2008-05-09
forum: Security
---

### Post by aurel on 2008-05-09
Hello,

I'm running hardy up-to-date on my 64bit PC.
After first update, rkhunter shows next warnings:

/bin/dmesg                                        [ Warning ]
 Warning: The file properties have changed:
          File: /bin/dmesg
          Current inode: 2490482    Stored inode: 2490398
          Current file modification time: 1209470318
          Stored file modification time : 1208230576

/bin/more                                         [ Warning ]
 Warning: The file properties have changed:
          File: /bin/more
          Current inode: 2493326    Stored inode: 2490431
          Current file modification time: 1209470318
          Stored file modification time : 1208230576

/bin/mount                                        [ Warning ]
 Warning: The file properties have changed:
          File: /bin/mount
          Current inode: 2493038    Stored inode: 2490432
          Current file modification time: 1209470319
          Stored file modification time : 1208230576

/usr/bin/logger                                   [ Warning ]
 Warning: The file properties have changed:
          File: /usr/bin/logger
          Current inode: 2080793    Stored inode: 2081368
          Current file modification time: 1209470319
          Stored file modification time : 1208230576

/usr/bin/sudo                                     [ Warning ]
 Warning: The file properties have changed:
          File: /usr/bin/sudo
          Current inode: 2081308    Stored inode: 2081771
          Current size: 122688    Stored size: 122560
          Current file modification time: 1209555621
          Stored file modification time : 1203938890

/usr/bin/whereis                                  [ Warning ]
 Warning: The file properties have changed:
          File: /usr/bin/whereis
          Current inode: 2493521    Stored inode: 2081890
          Current file modification time: 1209470319
          Stored file modification time : 1208230576

What that means?

---

### Post by brian_p on 2008-05-09
> **aurel said:**
> Hello,

I'm running hardy up-to-date on my 64bit PC.
After first update, rkhunter shows next warnings:

[snippy snip]

What that means?

You haven't read the man page or googled?

Does

[http://www.mail-archive.com/rkhunter-users@lists.sourceforge.net/msg01063.html](http://www.mail-archive.com/rkhunter-users@lists.sourceforge.net/msg01063.html)

help?

---

