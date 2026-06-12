---
title: "odd directories in /usr/share (/usr/share/linda)"
date: 2006-04-21
forum: Server Platforms
---

### Post by egas77 on 2006-04-21
Greets all, while trying to debug a problem with imapd not finding a user's homedirectory based mail store, I discovered a couple of directories in /usr/share that don't make much sense, at least from a naming convention.

These are /usr/share/linda and /usr/share/lintian.
Each of these directories has an 'overrides' subdir, and in these  are several text files, named for packages, eg. exim4-daemon-heavy and php5-common.

Originally I thought I was the victim of some clever root kit on my Breezy Badger server install, but a friend with a totally different system (also running Breezy, server install) has the same ones, though his files in overrides are different from mine.

Anyone have any ideas?

Thanks most muchly

---

### Post by nagilum on 2006-04-22
```

$ dpkg -S /usr/share/linda
cracklib2, login, exim4-daemon-light, php4-common, passwd, gtk-doc-tools: /usr/share/linda

```
Those are the packages which have files in /usr/share/linda on my system.

---

### Post by imagine on 2006-04-22
Linda and Lintian are some Debian package checkers. I don't know exactly what they are good for though.

---

### Post by fdoving on 2006-04-22
To get more info on the packages: 
```

apt-cache show linda
apt-cache show lintian

```

They are certainly not harmful rootkits.

- Frode

---

### Post by egas77 on 2006-04-24
[QUOTE=fdoving]To get more info on the packages: 
```

apt-cache show linda
apt-cache show lintian

```

They are certainly not harmful rootkits.

- Frode[/QUOTE]

Ah ha. Learn something new everyday. As a former RH user, I'm still new to the world of apt, et al, but it certainly is an excellent package manager.

Thanks all for the replies, much appreciated.

---

