---
title: "new server install - apt-get not working for anything."
date: 2008-12-13
forum: Server Platforms
---

### Post by Bartee on 2008-12-13
I have tried to sudo apt-get install openssh-server and several other things and I always get a message that it cannnot find the package I am trying to install.

An nslookup for cnn.com returns 157.166.226.25 so I think I am talking to the internet.

Any Ideas ????

---

### Post by cariboo on 2008-12-13
Can you ping anything out on the internet for example:

```
ping google.com
```

If you get an answer back you have an internet connection. I would then run:

```
sudo apt-get update
```

to update /etc/apt/source.list, then try installing the programs you need.

Jim

---

### Post by Bartee on 2008-12-13
Jim,

Thanks...

It was the update that did the magic... 

WOW lots of stuff updated...

Now everything is falling into place.

Installing rudy rubygems merb etc....

Thanks for responding.

---

