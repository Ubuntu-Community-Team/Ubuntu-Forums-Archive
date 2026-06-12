---
title: "[SOLVED] named group missing/invalid"
date: 2008-11-23
forum: Server Platforms
---

### Post by devonps on 2008-11-23
Hi,

I'm in the middle of installing Bind9 and was setting the permissions on the rndc.key file, which worked as expected, i.e. 640.

Current permissions are...
```
mailadmin@mail:/etc/bind$ ls -l /etc/rndc.key
-rw-r----- 1 root root 77 2008-11-20 15:40 /etc/rndc.key
```

But when I CHOWN'd the file I got the following error...
```
mailadmin@mail:/etc/bind$ chown root:named /etc/rndc.key
chown: invalid group: `root:named'
```

Should I add the named group myself?

Any help is appreciated,

Thanks,
Steve.

---

### Post by RealPSL on 2008-11-24
The user id and group names used on hardy was **bind** not **named**. Hopefully that clears it up for you.

---

### Post by devonps on 2008-11-24
Worked a treat - thanks :)

Plus as a double bonus I've learned a little more.

Steve.

---

