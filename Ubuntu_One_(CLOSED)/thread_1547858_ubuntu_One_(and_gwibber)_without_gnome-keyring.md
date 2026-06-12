---
title: "ubuntu One (and gwibber) without gnome-keyring"
date: 2010-08-07
forum: Ubuntu One (CLOSED)
---

### Post by fululian on 2010-08-07
Hi there,

I would like to know if there is the possibility to use ubuntu One and gwibber without having to use gnome-keyring. I do not use the keyring here, but I would like to use u One and gwibber. Thanks

---

### Post by duanedesign on 2010-08-13
As far as Ubuntu One, I know you can put the  oauth token in the syncdaemon config file. Anything listed in 
```
/usr/lib/ubuntuone-client/ubuntuone-syncdaemon --help
```
is also settable via the config (thanks to configglue). So you can pass in the oauth tokens and such.

---

### Post by fululian on 2010-08-13
Thank you, I'ma try that!

Cheers

---

