---
title: "Uh-oh."
date: 2009-10-22
forum: The Cafe
---

### Post by NoaHall on 2009-10-22
Hm, just had a look at my sources.list, and this what was there -

```

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

I get the feeling I've done something stupid recently...

---

### Post by FuturePilot on 2009-10-22
Maybe I'm missing something obvious but I don't see anything wrong? :confused:

---

### Post by RaZe42 on 2009-10-22
Yeah, I don't see anything wrong with it either...

---

### Post by NoaHall on 2009-10-22
Oh. Well, despite the fact it's missing quite a bit, I suppose it's fine.

---

### Post by CharlesA on 2009-10-22
Same here. They look normal to me.

What's it missing?

EDIT: Mine has less then yours:

```
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by howefield on 2009-10-22
> **RaZe42 said:**
> Yeah, I don't see anything wrong with it either...

Noahall didn't say there was anything wrong, just the possibility that he had done something stupid...

:lolflag:

---

### Post by schauerlich on 2009-10-22
> **howefield said:**
> Noahall didn't say there was anything wrong, just the possibility that he had done something stupid...

Which, really, is a possibility we should never discount.

---

### Post by NoaHall on 2009-10-22
It's missing quite a few entries? And comment lines? And I didn't remove them?

---

### Post by CharlesA on 2009-10-22
Interesting, mine had a bunch of comment lines..

Wonder what happened.

---

### Post by juancarlospaco on 2009-10-22
Just a text with links, no problem i see worse problems.

---

### Post by hoppipolla on 2009-10-22
> **NoaHall said:**
> It's missing quite a few entries? And comment lines? And I didn't remove them?

oh yeah! I didn't notice that either!

Oh well, so long as it has the right repos then you're ok :)

---

