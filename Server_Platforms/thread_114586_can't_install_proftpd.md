---
title: "can't install proftpd"
date: 2006-01-08
forum: Server Platforms
---

### Post by kasemodz on 2006-01-08
hi, i just started my server. I got tightvnc and apache2 installed. Now I'm trying to install ftp server. I heard proftpd is pretty good. However when I type-

```
sudo apt-get install proftpd
```

I get this error
```
E: Couldn't find package proftpd
```

what is wrong and what should I do?

---

### Post by Susana on 2006-01-08
enable universe repository: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by kasemodz on 2006-01-08
I think there is a problem with my apt-get. When I tried installing flash for firefox by doing- 
```
sudo apt-get install flashplayer-mozilla
```
I get the same error as above. I already tried updating apt-get and it seems to have updated without any problems.

---

### Post by steve_250 on 2006-01-09
As the above poster wrote, go into the package manager settings and select Universe.  That will take care of it for ya.

---

