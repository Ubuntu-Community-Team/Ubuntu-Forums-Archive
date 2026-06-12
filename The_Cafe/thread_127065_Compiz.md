---
title: "Compiz"
date: 2006-02-08
forum: The Cafe
---

### Post by nocturn on 2006-02-08
Novell has released Xgl publicly.  Next week they will also release their own window manager that uses Xgl and allows true transparency and hardware acceleration.

My question is, will Compiz replace metacity?

---

### Post by nocturn on 2006-02-08
There are some vids up here [http://tirania.org/blog/archive/2006/Feb-07-1.html](http://tirania.org/blog/archive/2006/Feb-07-1.html)

It looks awesome, specially the minimize effect is great.

---

### Post by frodon on 2006-02-08
and also here ;) :
[http://membres.lycos.fr/athome93/MVI_1949_bis.AVI](http://membres.lycos.fr/athome93/MVI_1949_bis.AVI)
[http://membres.lycos.fr/athome93/MVI_1950_bis.AVI](http://membres.lycos.fr/athome93/MVI_1950_bis.AVI)
[http://membres.lycos.fr/athome93/MVI_1951_bis.AVI](http://membres.lycos.fr/athome93/MVI_1951_bis.AVI)
[http://membres.lycos.fr/athome93/MVI_1952_bis.AVI](http://membres.lycos.fr/athome93/MVI_1952_bis.AVI)

---

### Post by bonzodog on 2006-02-08
hrm...compiz certainly does have some cool features to it. The one I really like is the desktop organisation of windows by hitting the TAB key. but that menu is...ugh...too XP-ish to me, and I'm not a fan of fixed menus. I like Xfce's/blackbox/fluxbox/Windowmaker dynamic menu's where you right click on the desktop.
Otherwise, it shows real promise.

---

### Post by nocturn on 2006-02-08
[QUOTE=bonzodog]hrm...compiz certainly does have some cool features to it. The one I really like is the desktop organisation of windows by hitting the TAB key. but that menu is...ugh...too XP-ish to me, and I'm not a fan of fixed menus. I like Xfce's/blackbox/fluxbox/Windowmaker dynamic menu's where you right click on the desktop.
Otherwise, it shows real promise.[/QUOTE]

The menu is not part of compiz.  It's the Gnome menu on Novell desktop.

Compiz would just replace metacity (praying)

---

### Post by RaptorRaider on 2006-02-08
As I said [here]("http://ubuntuforums.org/showthread.php?p=715360#post715360"), Compiz will probably be released in just a few hours from now.

And yes, since Compiz is also a windowmanager, Metacity would be replaced by it.

---

### Post by mstlyevil on 2006-02-08
If it proves to be stable then I will replace kwin on my knome. I already replaced metacity with kwin but I will have to wait for poofy to test it before installing it.

---

### Post by nocturn on 2006-02-08
[QUOTE=RaptorRaider]As I said [here]("http://ubuntuforums.org/showthread.php?p=715360#post715360"), Compiz will probably be released in just a few hours from now.

And yes, since Compiz is also a windowmanager, Metacity would be replaced by it.[/QUOTE]

I'm just wondering if Gnome is going to switch to it officially.  If it is stable, I really hope so.

If not, I hope it makes it to universe in Dapper, then I'll replace it myself.

---

### Post by mstlyevil on 2006-02-08
[QUOTE=nocturn]I'm just wondering if Gnome is going to switch to it officially.  If it is stable, I really hope so.

If not, I hope it makes it to universe in Dapper, then I'll replace it myself.[/QUOTE]

It would be a nice gesture from the Gnome developers but I will not hold my breath.

---

### Post by frodon on 2006-02-08
[QUOTE=nocturn]I'm just wondering if Gnome is going to switch to it officially.  If it is stable, I really hope so.

If not, I hope it makes it to universe in Dapper, then I'll replace it myself.[/QUOTE]I don't think so but replacing metacity by another WM is easy to do so no problem here.

But as far as i know compiz is just a compositor manager not a WM, i'm wrong ?

---

### Post by nocturn on 2006-02-08
[QUOTE=frodon]I don't think so but replacing metacity by another WM is easy to do so no problem here.

But as far as i know compiz is just a compositor manager not a WM, i'm wrong ?[/QUOTE]

As I understood, compiz is a complete window manager.  You can get some effects (like transparancy) with a compmanager, but the minimize effect and the expose clone are compiz' own.

---

### Post by frodon on 2006-02-08
Great glad to learn that, i used skippy-xd till now to get a expose like effects but it's not enough fast, i think i will try it as soon it will be possible and i'm sure that poofy or someone else will write a guide about it.
For the moment i'm stuck with gnome and xfwm4 (the xfce WM) but if compiz is stable ....

---

### Post by ember on 2006-02-08
Hmm ... if I understood [http://en.opensuse.org/Xgl]("http://en.opensuse.org/Xgl") right, compiz is a compositor, not a window manager - yet maybe it can be used both ways.

---

### Post by RaptorRaider on 2006-02-08
No, again, compiz is a combined window/composite manager.

I have no idea how you can conclude that from that link; it is stated there literally multiple times:
> it allows for very nifty effects using OpenGL-enhanced composition / window managers like compiz
[...]
Use compiz as your window manager
[...]
compiz is the first available combined window / composite manager that uses OpenGL.

---

### Post by poofyhairguy on 2006-02-08
[QUOTE=nocturn]
My question is, will Compiz replace metacity?[/QUOTE]

Few ways to answer that.

1. In the default Gnome? Not for a long time.

2. In Dapper? No, sorry folks.

3. On my desktop (and the desktops of people like me)? Yes, later today.

---

### Post by ssam on 2006-02-08
i think you'll need to get xgl running before compiz will work.

this will most likly be a bit more work than replacing metacity with something like openbox.

has anyone spotted any hardware requirements yet? will it need the nvidia proprietry drivers?

---

### Post by Stormy Eyes on 2006-02-08
[QUOTE=ssam]
has anyone spotted any hardware requirements yet? will it need the nvidia proprietry drivers?[/QUOTE]

Yes, it will, unless you can get ATi's proprietary drivers to work.

---

### Post by RaptorRaider on 2006-02-08
[QUOTE=Stormy Eyes]Yes, it will, unless you can get ATi's proprietary drivers to work.[/QUOTE]
Which shouldn't be that hard if installing Xgl [already]("http://ubuntuforums.org/showthread.php?t=127090") works with ATI's drivers, right?

A large "if" that is, since nobody seems to have tested that method yet.

---

### Post by ssam on 2006-02-08
on [http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl) it looks like this will work on a range of graphics cards (soon), even with the open source drives :-)

> **ATI / open source driver "radeon"**
* Driver does not accelerate blits from back buffer to front buffer which makes it very slow. The driver will soon be updated and should then work OK. 

**Intel / open source driver "i810"**
* Driver does not accelerate blits from back buffer to front buffer which makes it very slow. The driver will soon be updated and should then work OK.
* XVideo YV12 surfaces are hardware accelerated, but due to a bug in the driver the video will miss one of the color channels, leading to false greenish/orange colors. This has to be investigated. 



---

### Post by majikstreet on 2006-02-08
now that's cool! I love the cube thingy..

---

### Post by poofyhairguy on 2006-02-08
Just waiting for the actual compiz code........

---

### Post by mstlyevil on 2006-02-08
[QUOTE=poofyhairguy]Just waiting for the actual compiz code........[/QUOTE]

We are holding our breath waiting for your verdict. (Please hurry I am turning purple right now.)

---

### Post by graabein on 2006-02-08
The update on xgl and Compiz is great news! \\:D/ 

Looking forward to seeing these effects on my desktop some time this year perhaps?! ;) [-(  

Let me ask a quick and stupid question here: Can I use xgl and Compiz with Window Maker as well? It already has different zoom animations for iconification, but I'd like to utilise the ones shown in the videos and also have drop shadows. I think it would look great in Window Maker.

I'd also like to have the windows roll down like pull-down projection screens when I do shade/unshade!

---

### Post by Iandefor on 2006-02-08
[quote=poofyhairguy]Just waiting for the actual compiz code........[/quote] I eagely await a howto from you. Better hop to ;)!

---

### Post by granite230 on 2006-02-10
wtf!

I just read this blog:

[http://aseigo.blogspot.com/2005/12/wouldnt-be-it-be-nice.html]("http://aseigo.blogspot.com/2005/12/wouldnt-be-it-be-nice.html")

quote:
[I]
so ... who is this company, you ask, that would take the development of something as potentially important as this out of the community and put it behind closed doors? novell.[/I]

I don't know if I understand this correctly... does it mean that all the cool stuff I saw on those little movies (like the multiple desktops on a 3D cube), the eyecandy Novell developed, will not be available on our Ubuntu desktops?
So I can't install this sweet eyecandy on my home computer next week? 

I'm a bit confused now, so that's why I'm asking.

---

### Post by floam on 2006-02-10
The guy on that blog is a moron. Novell is giving Compiz to the community as a gift.

---

### Post by granite230 on 2006-02-10
thanx! I was hoping for that answer! :D 

now I can sleep tight

---

### Post by andrewsawyer on 2006-02-11
I've noticed the post about the i810 chipset.  I have an Acer TravelMate C110 Tablet PC with onboard Intel i810 graphics.

Does this mean that I will be able to get it working on my laptop with Dapper?  I'e just downloaded todays Daily of Dapper and installed fresh - my laptop is my 'testing' machine.

I followed the [How-to]("http://www.ubuntuforums.org/showthread.php?t=127090&highlight=xgl") on how to get it installed, however not having either an nVidia or ATI chipset I got stuck when making the symbolic links.

Can anyone confirm they have this running on anything other than nVidia or ATI?

Cheers,

Andy

---

