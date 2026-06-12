---
title: "Does it make a difference if you use sudo or gksudo?"
date: 2008-03-20
forum: The Cafe
---

### Post by billgoldberg on 2008-03-20
> **aysiu said:**
> Or ```
gksudo gedit /etc/apt/sources.list
``` Probably makes no difference in this particular case, but it's a good idea to associate *gksudo* with graphical apps and *sudo* with terminal apps.

It doesn't make a difference, I use sudo for everything and it always works.

---

### Post by aysiu on 2008-03-20
> **billgoldberg said:**
> It doesn't make a difference, I use sudo for everything and it always works.
I'm sure you also are able to cross the street without looking both ways and you somehow manage not to get hit by a car. Doesn't mean I'd recommend it.

*gksudo* and *sudo* work differently. Yes, if you use *sudo* for only Nautilus and Gedit, you probably won't experience any problems, but as I said before, it's a good habit to get into and reinforce for new users to use *gksudo* for graphical applications and *sudo* for terminal applications, because sometimes it does matter.

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by billgoldberg on 2008-03-20
> **aysiu said:**
> I'm sure you also are able to cross the street without looking both ways and you somehow manage not to get hit by a car. Doesn't mean I'd recommend it.

*gksudo* and *sudo* work differently. Yes, if you use *sudo* for only Nautilus and Gedit, you probably won't experience any problems, but as I said before, it's a good habit to get into and reinforce for new users to use *gksudo* for graphical applications and *sudo* for terminal applications, because sometimes it does matter.

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The only reason I prefer sudo to gksudo is because it's easier to type.

After reading about it on your site, I'll try to make a habit out of it.

---

### Post by LaRoza on 2008-03-20
> **billgoldberg said:**
> The only reason I prefer sudo to gksudo is because it's easier to type.

After reading about it on your site, I'll try to make a habit out of it.

Make an alias for gksudo then, maybe "gsu" or something.

Add to .bashrc:

```

alias gsu="gksudo"

```

---

### Post by billgoldberg on 2008-03-20
> **LaRoza said:**
> Make an alias for gksudo then, maybe "gsu" or something.

Add to .bashrc:

```

alias gsu="gksudo"

```

That would just complicate things :p

---

### Post by 23meg on 2008-03-20
gksu functions the same way as gksudo in Ubuntu by default; you may want to use it.

---

### Post by mrsudo on 2008-03-20
> **23meg said:**
> gksu functions the same way as gksudo in Ubuntu.

i definately did not know that.  thanks !!

---

### Post by aysiu on 2008-03-20
I believe ```
gksudo
``` may, in fact, just be a symlink to ```
gksu
``` Can anyone confirm this?

---

### Post by jpkotta on 2008-03-20
> **aysiu said:**
> I believe ```
gksudo
``` may, in fact, just be a symlink to ```
gksu
``` Can anyone confirm this?

```
[jpkotta@gauss w](0)$ readlink -f $(which gksudo)
/usr/bin/gksu

```

I didn't really know the difference until now.  gksudo, being a symlink to gksu, works just like su.  Most of the time I like the fact that sudo uses my config files though.

---

### Post by p_quarles on 2008-03-20
> **aysiu said:**
> I believe ```
gksudo
``` may, in fact, just be a symlink to ```
gksu
``` Can anyone confirm this?
Yes:
```
lee@Rimbaud:~$ ls /usr/bin/gk* -l
-rwxr-xr-x 1 root root 24696 2007-11-23 04:46 /usr/bin/gksu*
lrwxrwxrwx 1 root root     4 2008-02-26 22:52 /usr/bin/gksudo -> gksu*
-rwxr-xr-x 1 root root 11240 2007-12-31 14:42 /usr/bin/gksu-properties*
```
Except, well, it's apparently the other way around.

EDIT: The above is on Debian Testing. It should be the same in Ubuntu, but the same command certainly be used to confirm/deny this.

---

### Post by FuturePilot on 2008-03-20
Pretty much the same
```
nick@GutsyGibbon:~$ ls /usr/bin/gk* -l
lrwxrwxrwx 1 root root    12 2007-12-09 12:06 /usr/bin/gkeytool -> gkeytool-4.2
-rwxr-xr-x 1 root root  3212 2007-09-29 20:34 /usr/bin/gkeytool-4.2
-rwxr-xr-x 1 root root 23080 2007-09-12 18:21 /usr/bin/gksu
lrwxrwxrwx 1 root root     4 2007-12-09 12:06 /usr/bin/gksudo -> gksu
-rwxr-xr-x 1 root root  8748 2007-09-14 06:26 /usr/bin/gksu-properties

```

---

### Post by p_quarles on 2008-03-20
Exactly the same, actually. I just deleted the gkeytool lines for easy reading. 

So, yes, gksudo is simply a symlink pointing to gksu.

---

### Post by Gina on 2008-03-21
Very useful :)  I can save typing two chars by using **gksu** instead of **gksudo**.  So anyone using **sudo** because **gksudo** takes more typing can use **gksu** and "do it right" :)

---

