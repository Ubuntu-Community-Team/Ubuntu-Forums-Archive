---
title: "Changing service banners?"
date: 2006-09-16
forum: Server Platforms
---

### Post by breuerp on 2006-09-16
I know that it's possible to change service banners in most *nix distros but I seem to have forgotten where they're kept.  Can anyone help me out?  The point is not to advertise the version of *nix and the service to every script kiddie on the planet who decides to scan my box.

Thanks!

---

### Post by sktx on 2006-09-17
What do you mean by "service banners" ?

---

### Post by skymt on 2006-09-18
It's different for each service. What services are you running?

---

### Post by breuerp on 2006-09-21
I'm running SSH primarily.  I've manage to find the banner for that now.  Too bad that the server daemon and version number are so easily identified by rudimentary scanning.  I'm getting brute-force attacks (albeit very bad ones) at least once a day.

---

### Post by skymt on 2006-09-21
First off, always run SSH on a non-standard port. That will stop almost all of the idiots and deter the smarter crackers.

Anyway, for SSH, put the banner in a file and add a line like this to /etc/ssh/sshd_config:```
Banner /path/to/banner/file
```

EDIT: Whoops, misread your last post. You found SSH. Good. :-\" Anything else?

---

### Post by breuerp on 2006-09-22
> **skymt said:**
> First off, always run SSH on a non-standard port. That will stop almost all of the idiots and deter the smarter crackers.

Anyway, for SSH, put the banner in a file and add a line like this to /etc/ssh/sshd_config:```
Banner /path/to/banner/file
```

EDIT: Whoops, misread your last post. You found SSH. Good. :-\" Anything else?

The problem is that I typically (though not always) am remoting from a site that actually configures their firewall correctly and lets very few ports out.  I also need to allows some others to actually reach my box.  The scans are all low threat right now (most of them try to brute force the "Administrator" and "root" accounts) but it still troubling how quickly they found the service (less than 24 hours since I started sshd).

---

