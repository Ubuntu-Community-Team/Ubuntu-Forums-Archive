---
title: "infinite redraw in Klondike"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-03-06
I've just edited /usr/share/aisleriot/games/klondike.scm to have infinite # of redeals in Klondike. Now that file is missing. For the sake of one young lad that loves to play that, where is the new place to change that settings...? Thank You in advance...

---

### Post by ventrical on 2012-03-06
> **zika said:**
> I've just edited /usr/share/aisleriot/games/klondike.scm to have infinite # of redeals in Klondike. Now that file is missing. For the sake of one young lad that loves to play that, where is the new place to change that settings...? Thank You in advance...


I basically got the same thing you got.

(define kings-only #t)  ;only allow kings to be moved to empty slots

(define max-redeal 2)   ;number of redeals, -1 for unlimited

---

### Post by zika on 2012-03-06
> **ventrical said:**
> I basically got the same thing you got.

(define kings-only #t)  ;only allow kings to be moved to empty slots

(define max-redeal 2)   ;number of redeals, -1 for unlimitedIf You're talking about /usr/share/aisleriot/games/klondike.scm, that file (as a matter of fact (I think) whole folder) is irrelevant from a day or so ago... ;)
That is what I'm &#8222;complaining&#8220;... Now I can not make infinite nuber od redeals work...

---

### Post by ventrical on 2012-03-06
> **zika said:**
> If You're talking about /usr/share/aisleriot/games/klondike.scm, that file (as a matter of fact (I think) whole folder) is irrelevant from a day or so ago... ;)
That is what I'm &#8222;complaining&#8220;... Now I can not make infinite nuber od redeals work...


I'll try it here..

Edit :  works here .. deal  from menu and crtl <n> infintely.

---

### Post by ventrical on 2012-03-06
I'll try on a Unity 3D machine..

edit: works beautifully on that machine also..


or am I misunderstanding you?

---

### Post by zika on 2012-03-06
> **ventrical said:**
> or am I misunderstanding you?You are, I'm afraid.
It is not infinite redeal the whole game, just infinite redeal of cards from upper row...

---

### Post by jbicha on 2012-03-06
I believe you're using Aisleriot 3.3.1 from the GNOME 3 PPA. (It helps a lot if you tell us what version of an app you're using or what relevant PPAs you're pulling from.) It looks like Aisleriot is now storing the rules files in /usr/lib/x86_64-linux-gnu/aisleriot/guile/2.0/ but by default they're compiled so it's harder to edit them.

You're welcome to open a bug (on GNOME's bugzilla too if you like) asking for how to customize the games as I'm not sure.

---

### Post by zika on 2012-03-06
> **jbicha said:**
> I believe you're using Aisleriot 3.3.1 from the GNOME 3 PPA. (It helps a lot if you tell us what version of an app you're using or what relevant PPAs you're pulling from.) It looks like Aisleriot is now storing the rules files in /usr/lib/x86_64-linux-gnu/aisleriot/guile/2.0/ but by default they're compiled so it's harder to edit them.

You're welcome to open a bug (on GNOME's bugzilla too if you like) asking for how to customize the games as I'm not sure.
You're totally right... Mea culpa. I'll investigate and report that...

Update: 1:3.3.1-0ubuntu0~precise2 (precise) (You were right it is from Gnome3-PPA...)

---

