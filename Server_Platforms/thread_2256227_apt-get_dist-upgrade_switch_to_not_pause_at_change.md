---
title: "apt-get dist-upgrade switch to not pause at change log screen?"
date: 2014-12-10
forum: Server Platforms
---

### Post by mdlueck on 2014-12-10
Greetings,

Ubuntu Server already emails the admin account the change log when applying updates via:

```
/usr/bin/sudo /usr/bin/apt-get --assume-yes dist-upgrade
```

Is there a command line switch to apt-get which would bypass the "change log less" screen?

I am thankful,

---

### Post by mdlueck on 2015-03-19
Greetings,

I have obtained a work around to this pause behavior:

```
/usr/bin/apt-get --assume-yes dist-upgrade | /bin/cat
```

Does anyone know the correct apt-get switch to do the equivalent, or is really the only way to arrive at such apt-get behavior is to pipe it to cat to digest the pause at the less screen?

I am thankful,

---

