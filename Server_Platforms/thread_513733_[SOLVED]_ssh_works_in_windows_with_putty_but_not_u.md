---
title: "[SOLVED] ssh works in windows with putty but not ubuntu."
date: 2007-07-30
forum: Server Platforms
---

### Post by lunaz on 2007-07-30
i installed openssh-server on the other computer, and got it working in windows, but it won't work in ubuntu for some reason.

am i typing things wrong again? :)

```

luna@badassness:~$ ssh luna@192.168.1.100:4245
ssh: 192.168.1.100:4245: Name or service not known
luna@badassness:~$


```

it makes no difference if i use sudo.

---

### Post by scxtt on 2007-07-30
ssh -p 4245 luna@192.168.1.100

---

### Post by lunaz on 2007-07-30
ohh ty :D worked!

---

