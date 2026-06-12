---
title: "ubuntu one error in headless mode"
date: 2013-11-07
forum: Ubuntu One (CLOSED)
---

### Post by ddaas.0 on 2013-11-07
I am running Ubuntu 12.04 LTS Server and I followed the instruction from here: [https://wiki.ubuntu.com/UbuntuOne/Headless](https://wiki.ubuntu.com/UbuntuOne/Headless)

Now, when I try using u1sdtool I get the following error:
```
u1@s1:~$ u1sdtool -s

Oops, an error ocurred:
org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1


```

I don't know if it is important but when I followed the instruction from  the guide above there was no file named  ~/.config/ubuntuone/syncdaemon.conf
I created it and now it contains these 2 line:

[__main__]
   oauth=cc:dd

Where cc:dd is account key optained with: python ubuntuone-sso-login.py

There is no process like ubuntuone-syncdaemon running.

What should I do ?

Thanks

---

