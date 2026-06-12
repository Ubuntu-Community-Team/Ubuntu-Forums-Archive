---
title: "Can't write to Samba Shares"
date: 2012-03-27
forum: Server Platforms
---

### Post by xtropx on 2012-03-27
[test]
        writeable = yes
        path = /opt/share
        force user = user1
        valid users = user1
        public = yes
        create mode = 0775
        directory mode = 0775

Should probably note that I am using webmin, but I am almost ready to uninstall it because I've ended up working through ssh more anyway.

Error:

[IMG]http://imgur.com/1XRgS[/IMG][IMG]http://i.imgur.com/1XRgS.jpg[/IMG]
[IMG]http://imgur.com/1XRgS[/IMG]

---

### Post by FreeD01 on 2012-03-27
Have you checked permissions on share folder? If you want to write from network (win machine for example) than you need to allow nobody:nogroup. Works for me but consider security issues.

---

### Post by Morbius1 on 2012-03-27
Does the local server user, user1, have permissions to access /opt/share on the server itself?

Have you added the local server user, user1, to the samba password database:
```
sudo smbpasswd -a user1
```

---

