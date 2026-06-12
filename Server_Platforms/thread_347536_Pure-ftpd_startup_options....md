---
title: "Pure-ftpd startup options...?"
date: 2007-01-27
forum: Server Platforms
---

### Post by sammydee on 2007-01-27
Hi.

I'm setting up a pure-ftpd server on my ubuntu box (normal desktop install) and I've been reading the documentation for pure-ftpd (fairly confusing/complicated). From what I've read I THINK that to enable certain options such as anonymous ftp, you have to run pure-ftpd with these options, for example, after starting and stopping the service this was printed:

```
Running: /usr/sbin/pure-ftpd -l pam -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -E -B
```

From the documentation I have found out what these options all mean. I am really new to servers and stuff, haven't really messed around with this stuff before, but I think that PAM is a way of authenticating user accounts through the standard linux user database (is that the right terminology?).

Pure-ftpd is automatically started everytime I start up ubuntu. I would like to start it up with a different set of options, that doesn't explicitly disable anonymous access (-E disables anon access) for example, something like this:

```
pure-ftpd -l pam -O clf:/var/log/pure-ftpd/transfer.log -b -c 20 -i -u 1000 -B
```

Is there some sort of startup script I can edit to change the command at all? Is there another way I can add anonymous access to the ftp daemon. Sorry if I asked this in the wrong place!

Sam

---

### Post by sammydee on 2007-01-28
Does anybody know how to do this?

Sam

---

### Post by Acyong on 2007-03-05
This is the same question I would like to ask.

---

### Post by Pontiac on 2007-03-12
Check this link out:

[http://ubuntuforums.org/showthread.php?t=213266](http://ubuntuforums.org/showthread.php?t=213266)

---

