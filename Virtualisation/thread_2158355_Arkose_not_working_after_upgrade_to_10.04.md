---
title: "Arkose not working after upgrade to 10.04"
date: 2013-06-28
forum: Virtualisation
---

### Post by Aisteru on 2013-06-28
Oops, I made a mistake on the title. :/

 I have been using Arkose for opening untrusted web pages for quite some time now with little trouble. However, since I upgraded to Xubuntu 13.04 on Wednesday, I have not been able to run it. I usually use arkose-wrapper-gui with the following profile:

```

[container]
 cmd=firefox
 runas=user
 network=true
 xserver=direct
 dbus=none
 pulseaudio=true
 video=false
 root=/
 mount_bind=/tmp/orbit-$USER
 mount_cow=
 mount_restrict=

```

Now when I attempt to run it, I get this prompt:

```


timmy@ethyl:~$ arkose-wrapper-gui /usr/share/arkose/wrapper-profiles/firefox_scary.conf
reset: unknown terminal type unknown
Terminal type?     


```

After a little research I found something like this can be caused by an incorrect TERM variable. However, when I type either "linux," (as suggested by the post I found) or "xterm," (the actual content of my TERM variable) I get the error:

```
su: System error
```

Unfortunately, I have not found much about this error, or what to do about it.

Any ideas?

Thanks in advance.

---

