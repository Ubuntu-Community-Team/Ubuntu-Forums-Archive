---
title: "IE google translate problem"
date: 2009-05-20
forum: The Cafe
---

### Post by sandyd on 2009-05-20
Im having a weir annoying problem right now.

IN the site that im designing for my school, it has a translator thingy which uses google translator.

I can't really show you the site (because im not alowed to), but ive implemented it on

[http://studenthotspot.co.cc](http://studenthotspot.co.cc)
It currently has the same problem
now heres the problem

i click on one of those flags in firefox, their all loaded ok, but when i click in IE,that where the problem starts.

NONE of the images get loaded. I mean none at all. It translates fine, but I want my images!

I haven't tried at home yet (b/c/ i don't have windows) so can someone comfirm if its an IE issue or my school's issue?

---

### Post by dragos240 on 2009-05-20
> **carlee said:**
> Im having a weir annoying problem right now.

IN the site that im designing for my school, it has a translator thingy which uses google translator.

I can't really show you the site (because im not alowed to), but ive implemented it on

[http://studenthotspot.co.cc](http://studenthotspot.co.cc)
It currently has the same problem
now heres the problem

i click on one of those flags in firefox, their all loaded ok, but when i click in IE,that where the problem starts.

NONE of the images get loaded. I mean none at all. It translates fine, but I want my images!

I haven't tried at home yet (b/c/ i don't have windows) so can someone comfirm if its an IE issue or my school's issue?


Well..... IE really err.... sucks. Just convince your school to get firefox. Say that it won't work.

---

### Post by RiceMonster on 2009-05-20
> **dragos240 said:**
> Well..... IE really err.... sucks. Just convince your school to get firefox. Say that it won't work.

people will still use IE. Firefox is on every computer at my college, yet I still see most people using IE. Not worth the effort, because people will just complain that the website doesn't work and they don't want to use Firefox.

---

### Post by dragos240 on 2009-05-20
> **RiceMonster said:**
> people will still use IE. Firefox is on every computer at my college, yet I still see most people using IE. Not worth the effort, because people will just complain that the website doesn't work and they don't want to use Firefox.
Well if it doesn't work on IE, then what other choice do they have.

---

### Post by sandyd on 2009-05-20
i believe that im just misssing one of the many "IE fix codes" that are supposed to be on my page..

seems that a lot of pages added fixes for IE.:p

any ideas?

---

### Post by dragos240 on 2009-05-20
> **carlee said:**
> i believe that im just misssing one of the many "IE fix codes" that are supposed to be on my page..

seems that a lot of pages added fixes for IE.:p

any ideas?

Well.... it proves my point that IE sucks XD. It's so unstable.

Well.... sorry though, I wish I knew where a fix was :(

---

### Post by sandyd on 2009-05-25
something just hapenned!
looks like IE doesn't play too nicely with frames, so if your wondering.....
adding
```

<script language="javascript" type="text/javascript">
  if (top.location != self.location) {
    top.location.replace(self.location);           // pop to top
  }
</script>

```
to the bottom of the <body> fixed it :)

kills two problems at once. No frames and all pics loading perfectly :) (it was origionally designed only to remove frames... but whatever...)

---

### Post by monsterstack on 2009-05-25
> **carlee said:**
> something just hapenned!
looks like IE doesn't play too nicely with frames, so if your wondering.....
adding
```

<script language="javascript" type="text/javascript">
  if (top.location != self.location) {
    top.location.replace(self.location);           // pop to top
  }
</script>

```
to the bottom of the <body> fixed it :)

kills two problems at once. No frames and all pics loading perfectly :) (it was origionally designed only to remove frames... but whatever...)

Glad you fixed the problem.  [This site]("http://www.positioniseverything.net/articles/multiIE.html") [positioniseverything.net] has some tips and tricks showing you how to have specific html for different browsers, if you ever need to fix IE-specific bugs again. Personally, I'd go with,

```
<!--[if IE 6]> <h1>YOU ARE A MORON.</h1> <![endif]-->
```

But that's a little bit hard on those who have no choice.

---

### Post by sandyd on 2009-05-26
awesome link!

---

