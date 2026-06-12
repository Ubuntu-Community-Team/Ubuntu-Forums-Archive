---
title: "The mad scientist strikes again...."
date: 2006-01-09
forum: The Cafe
---

### Post by bonzodog on 2006-01-09
ok...
I have a possibly mad, extremely geekish idea, but to me it's my idea of an ideal distro.

Start with an expert install of Ubuntu; 

a) Strip out the current system V derived init tree, and replace it with the slackware BSD derived init system, which is faster and more stable. 

b) Add portage  from gentoo (which is EASY to do),but alter it to build optimised apps from the gentoo mirrors using emerge into .deb packages, which can be seen and used by apt. (i.e get it to adopt dh_make and build proper .deb packages). I am convinced this is actually quite easy.

c) Not bother with X. There is a FAR more powerful GUI engine for linux available. It's called DirectFB, and can handle 3D acceleration and eye candy effects in the Framebuffer. Add to this Qingy as a login manager,  and WindowMaker as the default desktop.

This is to me is an ideal distro. Fast, and lightweight, but with some of the most powerful linux core systems currently available integrated.

The kernel of course would have to be re-built from scratch and unmodified kernel code used.

What do people think? Am I mad? Or am I just a true linux geek who got bored, and decided to work out what he REALLY wanted. A bit from that distro, a bit from this one, and the best of that distro over there.

---

### Post by majikstreet on 2006-01-09
mnhph. you're not insane.. if you can do it, go ahead. I'm sure there would be people who would like it. hell, I'd even try it on a spare computer... :)  Sounds like a good idea, so... do you know how to do what you want to do?

---

### Post by akurashy on 2006-01-09
I could say its a nice idea, but I never seen directfb in action, so I'm not sure how it would run. though this can be tried and post screenshots indeed :D

---

### Post by Lovechild on 2006-01-09
you can already do stuff like b) with apt-get - try reading my bugreporting guide for how to do this.

and yes you are a bit mad

---

### Post by stuporglue on 2006-01-09
> c) Not bother with X. There is a FAR more powerful GUI engine for linux available. It's called DirectFB, and can handle 3D acceleration and eye candy effects in the Framebuffer. Add to this Qingy as a login manager, and WindowMaker as the default desktop.

I haven't really heard much of DirectFB and my experience with the Framebuffer is limited to using Elinks with graphics mode and png/jpg support compiled in on Gentoo. :-)

Are you saying that 3D acceleration is done all in software? Or just that with the right drivers it can do 3d acceleration. I notice that directFB hasn't hit a 1.0 yet, and that Qt support requires the SVN version still. 

One last issue then I'll be quiet. [http://www.directfb.org/index.php?path=Main%2FSupport%2FGraphics](http://www.directfb.org/index.php?path=Main%2FSupport%2FGraphics) Not many drivers yet. :-) 

But, if you make it, I'll try it out.

---

### Post by bonzodog on 2006-01-10
No, not too many drivers. but, I am going to bump this as I want further opinions;
Anyone that REALLY knows the System V init system, and can tell me if it is possible to swap it out for the slackware one?

also, there ought to more info on DirectFB available. It is a really nice front end.

---

### Post by ssam on 2006-01-10
you may want to also look at mac os x's launchd, that is pretty fast at getting a system booted.

see
[http://en.wikipedia.org/wiki/Launchd](http://en.wikipedia.org/wiki/Launchd)
[http://arstechnica.com/reviews/os/macosx-10.4.ars/5](http://arstechnica.com/reviews/os/macosx-10.4.ars/5)

---

