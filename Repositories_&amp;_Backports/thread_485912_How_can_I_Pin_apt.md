---
title: "How can I Pin apt?"
date: 2007-06-27
forum: Repositories &amp; Backports
---

### Post by bugmenot_user on 2007-06-27
I want to install softwares from backports excliptly by adding -t backports argument to apt-get.(like in Debian). I tried to change priorities but I don't know what value must I set for /etc/apt/apt.conf APT:: Default-Release.  Must it be *release*-updates or *release*-security or just *release*? How can I do this?

---

### Post by smartboyathome on 2007-06-27
You can always set the backports update setting in the Repo tool in Synaptic, couldn't you?

---

### Post by bugmenot_user on 2007-06-27
I think I didn't explain my problem correctly. When you enable backports repository, when you upgrade your system or install something, version on the backports (if any) will be installed. That's not I want. In Debian, if you want to install somethings from backports, you must specify this excliptly. ( [http://www.backports.org/dokuwiki/doku.php?id=instructions](http://www.backports.org/dokuwiki/doku.php?id=instructions) )
Yeah, I want to do apt pinning.

What Repo tool in Synaptic do is, enabling and disabling backports repository. That's not I  want.

Thanks.

---

### Post by smartboyathome on 2007-06-27
I looked in my sources.list and the only way to use backports is to use it like what I explained. You cannot "explicitly" tell it what you want it to install, it will do this automatically to everything.

---

### Post by bugmenot_user on 2007-06-28
How Debian do this? As far as I know, this must be done with apt-pinning. And this can be done in Ubuntu, too.
Apt-pinning is done with some settings in /etc/apt.conf and /etc/apt/preferences. Just sources.list is not enough. 
[(jaqque.sbih.org/kplug/apt-pinning.html)]("http://jaqque.sbih.org/kplug/apt-pinning.html")

Thanks

---

### Post by mlind on 2007-06-28
create **/etc/apt/preferences** and add the following pinning
```

Package: *
Pin: release a=feisty-backports
Pin-Priority: 400

```
now packages from feisty-backports are installed only if you use **-t feisty-backports**
check *man apt_preferences* for the reference.

---

### Post by bugmenot_user on 2007-06-29
> **mlind said:**
> create **/etc/apt/preferences** and add the following pinning
```

Package: *
Pin: release a=feisty-backports
Pin-Priority: 400

```
now packages from feisty-backports are installed only if you use **-t feisty-backports**
check *man apt_preferences* for the reference.
It works. Great. Thank you very much!

---

