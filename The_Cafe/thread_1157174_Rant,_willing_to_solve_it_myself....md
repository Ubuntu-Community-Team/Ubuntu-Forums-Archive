---
title: "Rant, willing to solve it myself..."
date: 2009-05-12
forum: The Cafe
---

### Post by moore.bryan on 2009-05-12
RANT:
Is it REALLY that hard to get different wallpapers on different virtual workspaces, particularly in XFCE? It SEEMS almost everyone wants this and I am of the belief developers/programmers usually allow the "public" to drive their development, so why WOULDN'T that function be natively included unless it's as difficult as nuclear cold fusion? True, there are a number of third-party apps to ALMOST do this and KDE, as well as Compiz can do this; however, I don't want to use Compiz and I can't stand KDE.

Solution?
I am WILLING to learn a little bit of code this summer if someone can point me in the right direction to start learning; e.g., which would be the best programming language to use, how could I make it cross-WM compliant, etc.

---

### Post by original_jamingrit on 2009-05-12
There's a lot of C tutorials online, which is probably your best bet: C is a pretty simple language, and if you'll be dealing with GNOME probably the best one to know (AFAIK, GTK and GNOME uses a lot of C).  A google search will turn up a ton of different tutorials, one of them will definitely suit your learning style.

Also, get into touch with the guys shown here: [http://brainstorm.ubuntu.com/idea/93/](http://brainstorm.ubuntu.com/idea/93/)
, as they seem to be interested in the same thing.

Also, UF has a dedicated programming section, so you may have better answers if you probe there for more info.
Good luck.

---

### Post by Bölvaður on 2009-05-12
Your best choice would be to check out how the wallpapers are set in xfce and how workspaces are implemented.

From that you just need to edit some part of the code and/or make a new package to add to the current system.

I would assume xfce is written in C.

---

### Post by BslBryan on 2009-05-12
Hello, moore.bryan. :-)

I've actually come up with a solution.  I've posted it here, but I've found my instructions turn up [here]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/").  Try it out, and it might work out for you.  Worth a look anyway. :-)

I hope I've been of some help, moore.bryan.  

Best to you, and good luck.

---

### Post by moore.bryan on 2009-05-12
> **original_jamingrit said:**
> There's a lot of C tutorials online, which is probably your best bet: C is a pretty simple language, and if you'll be dealing with GNOME probably the best one to know (AFAIK, GTK and GNOME uses a lot of C).  A google search will turn up a ton of different tutorials, one of them will definitely suit your learning style.

Also, get into touch with the guys shown here: [http://brainstorm.ubuntu.com/idea/93/](http://brainstorm.ubuntu.com/idea/93/)
, as they seem to be interested in the same thing.

Also, UF has a dedicated programming section, so you may have better answers if you probe there for more info.
Good luck.
Thanks... C doesn't look impossible; not C++? I thought C++ was the "modernized" version of C. 

Oh, and thank you for the link! 

EDIT: Unfortunately, the GSoC stuff revolves around Gnome and I'm playing with XFCE right now. :-(

> **Bölvaður said:**
> Your best choice would be to check out how the wallpapers are set in xfce and how workspaces are implemented.

From that you just need to edit some part of the code and/or make a new package to add to the current system.

I would assume xfce is written in C.

Why would you assume that? Like I wrote, I'm willing to learn a little programming, but I don't want to learn them all... yet. ;-)

> **BslBryan said:**
> Hello, moore.bryan. :-)

I've actually come up with a solution.  I've posted it here, but I've found my instructions turn up [here]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/").  Try it out, and it might work out for you.  Worth a look anyway. :-)

I hope I've been of some help, moore.bryan.  

Best to you, and good luck.
Unfortunately, your solution involves Compiz and I'm trying to stay away from that.

---

### Post by baseface on 2009-05-12
c++ is NOT a modernized c.
c++ is c with classes... and a lot of other bs that will end up cutting your legs off.

---

### Post by 23meg on 2009-05-12
[http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

Looks like it's mostly done already, and the patches are awaiting merging. If you want to work on this you'll want to work on refining them (if needed) rather than starting from scratch.

---

### Post by moore.bryan on 2009-05-12
> **baseface said:**
> c++ is NOT a modernized c.
c++ is c with classes... and a lot of other bs that will end up cutting your legs off.
got it... I'll stick with C then...
> **23meg said:**
> [http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

Looks like it's mostly done already, and the patches are awaiting merging. If you want to work on this you'll want to work on refining them (if needed) rather than starting from scratch.
But still focuses on Gnome... XFCE wonderings here. :-)

---

### Post by Rainstride on 2009-05-12
> **23meg said:**
> [http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

Looks like it's mostly done already, and the patches are awaiting merging. If you want to work on this you'll want to work on refining them (if needed) rather than starting from scratch.

i thought this was going to be in 9.04....:confused:

---

### Post by 23meg on 2009-05-12
> **moore.bryan said:**
> got it... I'll stick with C then...

But still focuses on Gnome... XFCE wonderings here. :-)

The patches should still provide at least a good base to work from.

> **Rainstride said:**
> i thought this was going to be in 9.04....:confused:

It seems the patches didn't get merged upstream in time for 9.04.

---

### Post by subdivision on 2009-05-12
Honestly, is this really such a big deal?  How much time do you spend looking at your wallpaper that you need a different one for each workspace?

I understand that freedom to customize is one of the things that Linux is all about.  I tweak my own installation endlessly.  It just seems odd to get so indignant about something like this.

---

### Post by moore.bryan on 2009-05-13
> **23meg said:**
> The patches should still provide at least a good base to work from.
Fair enough... thanks for the suggestion!
> **subdivision said:**
> Honestly, is this really such a big deal?  How much time do you spend looking at your wallpaper that you need a different one for each workspace?

I understand that freedom to customize is one of the things that Linux is all about.  I tweak my own installation endlessly.  It just seems odd to get so indignant about something like this.
I warned you it was a rant, didn't I? ;-)

For me, the background helps me keep track of which workspace I'm on. See, the XFCE pager doesn't work well with Compiz; in fact, I've never been able to get it to behave properly. I try to segregate my work using my workspaces so as to remain a little more organized. As you put it, Linux is all about the customization for personal use and tastes... that's just what this is about.

I suppose my rant could fall under a different title, perhaps: Why do the most common sense computer functions always seem to be lacking and/or nearly impossible in every/a certain WM? Of course, the definition of common sense is highly debateable. 
:-)

---

### Post by RiceMonster on 2009-05-13
> **moore.bryan said:**
> See, the XFCE pager doesn't work well with Compiz; in fact, I've never been able to get it to behave properly.

I assume you're still using 4.4? You're right, it really doesn't work very well. On 4.6 you'll find it will works just like it does with xfwm.

---

### Post by moore.bryan on 2009-05-13
> **RiceMonster said:**
> I assume you're still using 4.4? You're right, it really doesn't work very well. On 4.6 you'll find it will works just like it does with xfwm.
nope, 4.6.1 and it doesn't act any way it's supposed to.

---

### Post by RiceMonster on 2009-05-13
hmmm... I found it worked oddly in 4.4, but I haven't noticed any problems with 4.6. What exactly does it do wrong? I don't really use compiz.

---

### Post by 3rdalbum on 2009-05-13
Different wallpapers for different workspaces seems to be the next essential feature for a week... and then nobody mentions it for six months.

I doubt I'd use different wallpapers, but if you want this feature, you must keep some momentum behind the feature request. Or, of course, write it yourself :-)   Good luck!

---

### Post by moore.bryan on 2009-05-13
> **RiceMonster said:**
> hmmm... I found it worked oddly in 4.4, but I haven't noticed any problems with 4.6. What exactly does it do wrong? I don't really use compiz.
I don't much like Compiz, but it's the only game in-town right now. One, the pager won't shade which workspace I'm on and, two, it will only allow switching between two workspaces and not the four I have set-up.
> **3rdalbum said:**
> Different wallpapers for different workspaces seems to be the next essential feature for a week... and then nobody mentions it for six months.

I doubt I'd use different wallpapers, but if you want this feature, you must keep some momentum behind the feature request. Or, of course, write it yourself :-)   Good luck!
That's exactly what I'm going to do... this is a relatively "fresh" issue for me. Maybe I'll be the difference-maker!
;-)

---

