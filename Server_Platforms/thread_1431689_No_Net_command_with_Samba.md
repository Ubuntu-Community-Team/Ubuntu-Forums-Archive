---
title: "No Net command with Samba"
date: 2010-03-16
forum: Server Platforms
---

### Post by linkspointyears on 2010-03-16
Hi, this is my first post ever, so sorry if i'm not very descriptive.

I just installed Ubuntu Server 9.10 x86 and I cannot use the net command that comes with Samba can anyone help?

---

### Post by KB1JWQ on 2010-03-16
By "Can't use" do you mean it spits out an error?  If so, what?  If no output is returned, how do you know it's not working?

---

### Post by linkspointyears on 2010-03-16
as in

```
administrator@GRASHA:~$ net
-bash: net: command not found
```

as if it was never installed

---

### Post by KB1JWQ on 2010-03-17
Is /usr/bin in your path?

---

### Post by linkspointyears on 2010-03-17
how would i run it from /usr/bin path?

---

### Post by KB1JWQ on 2010-03-17
Please repost the output of "echo $PATH"

And does /usr/bin/net work for you?

---

### Post by linkspointyears on 2010-03-18
```
administrator@GRASHA:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
administrator@GRASHA:~$ /usr/bin/net
-bash: /usr/bin/net: No such file or directory
```

---

### Post by slakkie on 2010-03-18
apt-file search /usr/bin/net

on hardy it is in the package *samba-common*

---

### Post by linkspointyears on 2010-03-18
Reinstalled samba-common package and it worked, Thank you so much!

---

