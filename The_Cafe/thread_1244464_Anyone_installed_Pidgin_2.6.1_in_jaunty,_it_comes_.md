---
title: "Anyone installed Pidgin 2.6.1 in jaunty, it comes with voice and video support..."
date: 2009-08-19
forum: The Cafe
---

### Post by legolas_w on 2009-08-19
Hi
It looks like that pidgin developers included the voice and video support into pidgin but based on a comment at [http://www.getdeb.net/comment/2028](http://www.getdeb.net/comment/2028) it does not work in 9.04.


 Does anyone successfully used voice/video support of pidgin in 9.04?

Thanks

---

### Post by perce on 2009-08-19
According to [the official page]("http://planet.pidgin.im/") they started adding video and voice support.

---

### Post by Tibuda on 2009-08-19
It won't work on Jaunty, and the only protocol that supports vv is XMPP/Jabber/Google. But now that the libpurple framework is ready, we can hope it will support the other networks soon.

---

### Post by mrgnash on 2009-08-19
I have installed it, but haven't had a chance to test voice support yet.. If it did work, that's all I'd use it for because I do love my Centerim :)

---

### Post by khc on 2009-08-20
> **legolas_w said:**
> Hi
It looks like that pidgin developers included the voice and video support into pidgin but based on a comment at [http://www.getdeb.net/comment/2028](http://www.getdeb.net/comment/2028) it does not work in 9.04.


 Does anyone successfully used voice/video support of pidgin in 9.04?

Thanks

Grab libgstfarsight and libnice from karmic, don't forget the -dev packages as well.

---

### Post by kevinpet on 2009-08-20
> **khc said:**
> Grab libgstfarsight and libnice from karmic, don't forget the -dev packages as well.

I've tried installing libgstfarsight0.10-0_0.14-2ubuntu1_i386.deb and libgstfarsight0.10-0_0.0.12ubuntu2_i386.deb but both of these have dependencies, which have dependencies, which have dependencies, and I'd pretty soon end up upgrading to karmic entirely.

What packages exactly should I install?

---

### Post by kpkeerthi on 2009-08-20
[Ubuntu Pidgin PPA]("http://www.google.com/search?q=ubuntu%2C+pidgin+ppa")

---

### Post by khc on 2009-08-20
> **kevinpet said:**
> I've tried installing libgstfarsight0.10-0_0.14-2ubuntu1_i386.deb and libgstfarsight0.10-0_0.0.12ubuntu2_i386.deb but both of these have dependencies, which have dependencies, which have dependencies, and I'd pretty soon end up upgrading to karmic entirely.

What packages exactly should I install?

It's been a while since I did this, but I think you need gstreamer0.10-nice and libnice in addition to libgstfarsight.

---

### Post by fcastillo on 2009-09-16
> **khc said:**
> It's been a while since I did this, but I think you need gstreamer0.10-nice and libnice in addition to libgstfarsight.

I have both of them installed, but I still see the voice and video gray and not enabled. Do I really need the Karmic files? Jaunty doesn't work at all?
It's impossible that pidgin says in the main webpage that there's video and voice support and then under the Ubuntu installation they mention there's support only for Jaunty, but there isn't!!!
I can't believe this!!!

---

### Post by Ric_NYC on 2009-09-16
Voice and video support in 2009?
I can't believe it.

---

