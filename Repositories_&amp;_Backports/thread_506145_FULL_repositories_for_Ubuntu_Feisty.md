---
title: "FULL repositories for Ubuntu Feisty"
date: 2007-07-21
forum: Repositories &amp; Backports
---

### Post by drsintoma on 2007-07-21
Here  we go!

:arrow: **[Repositories]("http://confiles.com/?op=view&file=1046")**

:arrow: **[GPG Keys]("http://confiles.com/?op=view&file=1047")**

:arrow: **[Download sources.list]("http://confiles.com/download.php/1046/sources.list")**

If you know any more, let me know and I'll add it.

Enjoy! ):P

---

### Post by tcoffeep on 2007-07-21
So, these are safe? I'm still sort of a newb.

I've updated my sources.list with this, and found some more updates, and I've moved from Windows to Ubuntu, so you must forgive my ignorance :)

An added question, is there any repositories for ATI?

---

### Post by drsintoma on 2007-07-21
Let's say are safe enough. Only ubuntu official repositories are 100% safe.
If I'm not wrong ATI drivers are  included in the restricted branch inside ubuntu official repository.

---

### Post by tcoffeep on 2007-07-21
Alrighty. Thanks.

I got a question for you though. I installed everything included, because upgrading is fun :)
But one won't seem to install due to missing dependencies. It's called w3m. :( Something called libc6 is Ubuntu-version, so it can't get updated...i don't think, and so on. Any suggestions?

---

### Post by picpak on 2007-07-21
Why would anyone need so many repos anyway? I only have three extra repos and they cover everything I need.

---

### Post by tcoffeep on 2007-07-21
It's nice to have updates :) I'm addicted to updating :)

---

### Post by drsintoma on 2007-07-21
> **tcoffeep said:**
> Alrighty. Thanks.

I got a question for you though. I installed everything included, because upgrading is fun :)
But one won't seem to install due to missing dependencies. It's called w3m. :( Something called libc6 is Ubuntu-version, so it can't get updated...i don't think, and so on. Any suggestions?

Comment these lines

```
###########
# AUDACIOUS
###########

deb http://vdlinux.sourceforge.jp/ experimental all
deb-src http://vdlinux.sourceforge.jp/ experimental all
```

Those are experimental packages. These things may happen.

Regards.

---

### Post by tcoffeep on 2007-07-22
Thanks. You've been really helpful. :)

---

### Post by ThrobbingBrain66 on 2007-07-22
Using this many unofficial repos really isn't a good idea guys.  Just taking a quick look through all the repos that drsintoma has compiled, I came across three different Beryl repos, Medibuntu and Seveas which offer almost the same packages and various other duplicates. This could potentially lead to all sorts of version mismatches, dependency problems and general unpleasantness.

Keep in mind that troubleshooting any problems you encounter will be more difficult as well.

USE AT YOUR OWN RISK!

---

### Post by Haegin on 2007-07-23
I recommend using this as a list of repositories that you can lookup when you need a particular package and add it when you need a package. Do not enable all of these by default - 99% of people won't need them and you are only asking for more trouble when repositories conflict or when you try to upgrade to a newer version of Ubuntu.

---

### Post by bradmayne on 2007-07-24
i don't see why anyone would want to start updating when they don't need to.  That's going to cause problems later on!  Trust me on that! And to that  d&*k with ears who's quoting a satan worshipper - dude your a straight up tool.

---

### Post by Seisen on 2007-07-25
> **bradmayne said:**
> i don't see why anyone would want to start updating when they don't need to.  That's going to cause problems later on!  Trust me on that! And to that  d&*k with ears who's quoting a satan worshipper - dude your a straight up tool.

If you don't like his sig. don't read it then, plain and simple.

---

### Post by mintcoffee on 2007-07-26
> **bradmayne said:**
> i don't see why anyone would want to start updating when they don't need to.  That's going to cause problems later on!  Trust me on that! And to that  d&*k with ears who's quoting a satan worshipper - dude your a straight up tool.

anyways its his afterlife.:-({|=

---

### Post by tcoffeep on 2007-07-26
Exactly.

Anyways, I followed the advice in this thread, and didn't go with this repositorie, so I used the one off of psychocats.net (or something).

Peace out.

From your local 'tool'.

---

