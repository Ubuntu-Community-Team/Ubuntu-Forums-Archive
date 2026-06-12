---
title: "Performing a base/minimal install from a livecd?"
date: 2012-04-24
forum: The Cafe
---

### Post by mips on 2012-04-24
This is not really a installation related query, more fishing for information one.

I have not downloaded a livecd in ages, always use the alternate images. I read here [https://help.ubuntu.com/community/LiveCD#Text-Mode_Installation](https://help.ubuntu.com/community/LiveCD#Text-Mode_Installation) that the livecd offers a text-mode installation.

Would it be possible to perform a minimal base install via this installation mode?

Secondly, lets assume for a second the above is not possibly will performing a full install followed by removing & purging the ubuntu-desktop package leave me with  something resembling a minimal base install or would there be extra stuff left over? (I'm not worried about stuff in the apt cache but installed apps). Just wondering if I did a plain xfce4 install after this it would be the same as a base install + xfce.

---

### Post by forrestcupp on 2012-04-24
Ubuntu Desktop is just a dummy package that refers to a boatload of other packages to simplify updating. If you remove and purge the Ubuntu Desktop package, it will still leave all of the packages that it points to, so it probably wouldn't do you much good.

---

### Post by &lt;¡&gt; on 2012-04-24
> **mips said:**
> 
Secondly, lets assume for a second the above is not possibly will performing a full install followed by removing & purging the ubuntu-desktop package leave me with  something resembling a minimal base install or would there be extra stuff left over? (I'm not worried about stuff in the apt cache but installed apps). Just wondering if I did a plain xfce4 install after this it would be the same as a base install + xfce.

Psychocats has a tutorial on how to remove all the ubuntu default desktop

[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

---

### Post by mips on 2012-04-25
> **forrestcupp said:**
> Ubuntu Desktop is just a dummy package that refers to a boatload of other packages to simplify updating. If you remove and purge the Ubuntu Desktop package, it will still leave all of the packages that it points to, so it probably wouldn't do you much good.

What I suspected :sad:

> **<¡> said:**
> Psychocats has a tutorial on how to remove all the ubuntu default desktop

[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

Thanks, I was actually looking at that very page last week or the week before and totally forgot about it, getting old :redface:

Wonder if if leaves you with an identical setup to that of a base install...

---

