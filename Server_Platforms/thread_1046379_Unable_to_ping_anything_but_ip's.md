---
title: "Unable to ping anything but ip's"
date: 2009-01-21
forum: Server Platforms
---

### Post by Sir Jake on 2009-01-21
I'm able to ssh into my box, but if I try the command sudo apt-get update I get this.

```
ezzi@PureVoltage:~$ sudo apt-get update
Err http://us.archive.ubuntu.com hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US

```

When I tried to ping another ip on my network it works, so I tried ping [www.google.com](www.google.com)  and it failed. 
When trying it on our other box it worked fine so I pinged the ip for google.com  and it worked great.

Any ideas why this is happening? 

If you need more info please let me know.
 Thanks.

---

### Post by spiderbatdad on 2009-01-21
what do you have in /etc/resolv.conf?

---

### Post by cdenley on 2009-01-21
Also, post this output.
```

dig +short www.google.com
dig +short @208.67.222.222 www.google.com
nc -z -v 74.125.95.103 80

```

---

### Post by buzz57 on 2009-01-21
they look like DNS or routing table errors, you could try checking your network settings

---

### Post by Sir Jake on 2009-01-21
> **spiderbatdad said:**
> what do you have in /etc/resolv.conf?

blah that would be it.
search va.shawcable.net
nameserver 64.59.144.18
nameserver 64.59.144.19

Removed that and ding ding.
seems to be working now.
Thanks

---

