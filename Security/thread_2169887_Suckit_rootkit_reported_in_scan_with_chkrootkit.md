---
title: "Suckit rootkit reported in scan with chkrootkit"
date: 2013-08-23
forum: Security
---

### Post by dangillmor on 2013-08-23
I just installed and ran chkrootkit, and got this positive on the line "Searching for Suckit rootkit..." : 

/sbin/init INFECTED

Can anyone help with this? If I'm infected I want to find a way to remove this.

Running 13.04 with latest updates...

Thanks.

---

### Post by coldraven on 2013-08-24
I don't know the answer but try running rkhunter and see if it reports the same thing. (Best run in fullscreen)
```
sudo rkhunter -c
```

---

### Post by unspawn on 2013-08-24
> **dangillmor said:**
> I just installed and ran chkrootkit, and got this positive on the line "Searching for Suckit rootkit..." :   /sbin/init INFECTED  Can anyone help with this? If I'm infected I want to find a way to remove this.  Running 13.04 with latest updates...  Thanks.   Run a Live CD or DVD, mount the "victim" file system and run the specific Chkrootkit v0.49 check manually and on the /sbin/init of the "victim" file system.  First set the MOUNT_POINT variable to where you mounted the "victim" file system and include a trailing slash:  ```
 strings -an4 ${MOUNT_POINT}sbin/init | egrep "HOME" 
``````
 # This specific Chkrootkit check works only on "Live" systems: cat /proc/1/maps | egrep "init."  
``````
# This specific Chkrootkit check works only on "Live" systems: cat /dev/.golf 
```   Additionally run these checks from Rootkit Hunter:   ```
 strings -an4 ${MOUNT_POINT}sbin/init | egrep -ie "(****|backdoor|bin/rcpc|bin/login)" stat -c %h ${MOUNT_POINT}sbin/init
``` Prolly won't find a thing but feel free to post output.    *BTW If you would really have been infected you should collect evidence, mitigate and investigate, not delete stuff. **BTW formatting really s*cks.

---

### Post by dangillmor on 2013-08-24
rkhunter reports no rootkit, but does (apparently a false positive, based on a variety of web reports) report a problem with unhide.rb.

---

### Post by Irihapeti on 2013-08-24
Chances are that it's a false positive. Chkrootkit and rkhunter are notorious for those.

See [https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

It's a long-standing issue. [http://ubuntuforums.org/showthread.php?t=1362074](http://ubuntuforums.org/showthread.php?t=1362074) describes the same problem from nearly 4 years ago.

---

### Post by Frogs Hair on 2013-08-24
> [URL="http://chrisjrob.com/2013/07/04/rkhunter-usrbinunhide-rb-has-been-replaced-by-usrbinunhide-rb/"]
[COLOR=#000000]rkhunter reports no rootkit, but does (apparently a false positive, based on a variety of web reports) report a problem with unhide.rb.[/COLOR]


http://chrisjrob.com/2013/07/04/rkhunter-usrbinunhide-rb-has-been-replaced-by-usrbinunhide-rb/[/URL]

---

### Post by unspawn on 2013-08-24
> **Frogs Hair said:**
> > rkhunter reports no rootkit, but does (apparently a false positive, based on a variety of web reports) report a problem with unhide.rb.  http://chrisjrob.com/2013/07/04/rkhunter-usrbinunhide-rb-has-been-replaced-by-usrbinunhide-rb/[/URL]    That's nice but it's wrong.    Nobody should use "unhide.rb".   Use [unhide](http://www.unhide-forensics.info/) instead.

---

