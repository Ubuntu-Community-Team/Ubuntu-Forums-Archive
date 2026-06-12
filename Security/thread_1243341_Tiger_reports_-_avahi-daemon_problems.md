---
title: "Tiger reports - avahi-daemon problems"
date: 2009-08-18
forum: Security
---

### Post by oygle on 2009-08-18
Tiger runs automatically every day. I'm seeing these messages

> 
# Checking listening processes
OLD: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 50224 (UDP on every interface) is run by avahi.
NEW: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 37175 (UDP on every interface) is run by avahi.


Does anything need changing ? I use Firestarter, possibly something there that needs changing ?

Oygle

---

### Post by cdenley on 2009-08-18
Avahi is installed by default.
[http://en.wikipedia.org/wiki/Avahi_(software](http://en.wikipedia.org/wiki/Avahi_(software))

You can safely disable it if you don't expect its features to be available.
System>Administration>Services
It isn't really a security concern, though. Firestarter is no longer supported or maintained, so I would suggest you use something else, like gufw.

---

### Post by oygle on 2009-08-19
> **cdenley said:**
> 
You can safely disable it if you don't expect its features to be available.
System>Administration>Services
It isn't really a security concern, though.


Okay, thanks, I wouldn't know if it is used or not, so will leave it there, just to play it safe.

> **cdenley said:**
> 
Firestarter is no longer supported or maintained, so I would suggest you use something else, like gufw.

Firestarter gives me problems sometimes, it blocks access 'out', even though it is setup okay in iptables, and as I see gufw does have a gui, I will use that instead.

Thanks,

Oygle

---

### Post by cariboo on 2009-08-19
Make sure you use:

```
sudo apt-get purge firestarter
```

To completely get rid of firestarter and it's configuration files.

---

### Post by oygle on 2009-08-20
Okay, thanks, I will do that.  :)

There are other packages I have 'removed' but there are still files left over, so that's a handy command to know, to clean up completely.

Thanks,

Oygle

---

