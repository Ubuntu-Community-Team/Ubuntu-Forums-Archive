---
title: "Crossover/wine question"
date: 2005-12-21
forum: The Cafe
---

### Post by quietglow on 2005-12-21
Hey crossover/wine gurus, what do you do to get apps installed which require SP1 or 2? Is it possible?

I've been using crossover for months and love it, but I have a couple of apps I'd love to run which require XP SP1.

Thanks!

---

### Post by BSDFreak on 2005-12-21
[QUOTE=quietglow]Hey crossover/wine gurus, what do you do to get apps installed which require SP1 or 2? Is it possible?

I've been using crossover for months and love it, but I have a couple of apps I'd love to run which require XP SP1.

Thanks![/QUOTE]

Which apps are you using that require SP1?

---

### Post by quietglow on 2005-12-21
I'm trying to get Konfabulator going. I'm dying for good widgets :-)

(I know about gdesklets and superkaramba)

---

### Post by BSDFreak on 2005-12-21
[QUOTE=quietglow]I'm trying to get Konfabulator going. I'm dying for good widgets :-)

(I know about gdesklets and superkaramba)[/QUOTE]

It's because of WinHTTP, that much i can figure out, but how to fix it i dunno, i'd ask over at the crossover or wine forums if i were you.

---

### Post by Wallakoala on 2005-12-21
[QUOTE=quietglow]I'm trying to get Konfabulator going. I'm dying for good widgets :-)

(I know about gdesklets and superkaramba)[/QUOTE]

Konfabulator is one of the things i miss most about windows. If there is any way i can get it to work on linux for free, then I would like to know.

---

### Post by xequence on 2005-12-21
I thought wine emulated windows 98...

---

### Post by scole on 2005-12-21
you can config wine to emulate any version of windows. 98 is the standard.

---

### Post by BSDFreak on 2005-12-21
[QUOTE=scole]you can config wine to emulate any version of windows. 98 is the standard.[/QUOTE]

While true i doubt it's going to matter as it needs a specific library included in Sp1 which is not available in wine.

I'm sure there is a hack to this and i'm sure it's an illegal hack so i'm not going to even attempt it.

---

### Post by quietglow on 2005-12-21
Illegal how? Does it end up adding some part of windows into the wine directory? Would it be illegal even if you own a copy of windows? Would you mind giving me a leading clue? :-)

I haven't really messed with wine configuration as of yet--Crossover just works for most everything I need so far.

Being able to run Konfabulator would be really dang cool, though. I owned it for mac before yahoo bought (or apple copied it :-)

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=Wallakoala]Konfabulator is one of the things i miss most about windows. If there is any way i can get it to work on linux for free, then I would like to know.[/QUOTE]

Gdesktlets

Superkaramba

What you are trying to do is not worth the effort I say.

---

### Post by Wallakoala on 2005-12-21
[QUOTE=poofyhairguy]Gdesktlets

Superkaramba

What you are trying to do is not worth the effort I say.[/QUOTE]

I havent tried Superkaramba but Gdesklets isnt the same as Konfabulator. I just think that the konfabulator widgets are more "high quality" in a way. There are plently of nice gdesklets, but they aren't as useful to me. And also gdesklets seems to take up more resources than konfabulator.

I'm not bashing gdesklets, I just agree with the OP that it would be pretty sweet to get konfabulator working on linux.

---

### Post by quietglow on 2005-12-21
> What you are trying to do is not worth the effort I say.

I disagree. I use and love gnome, so unless I want to look at ugly black backgrounds that I get when using superkaramba, I'm left with gdesklets. In my experience, gdesklet sensors are buggy, huge resource hogs and (by far the worst when we're talking eye candy) mostly not very good looking. If there are any offended gdesklet developers here, I'm sorry!

In contrast, Konfabulator widgets are very nice to look at and tend to be fairly lightweight. If I have to do some major reconstruction to get it running, then I'll probably drop the idea. I love crossover, though, and use it for lots of stuff (in addition to Office, which I use for work...can't wait for OO to suport comment bubbles in writer!)

---

### Post by Wallakoala on 2005-12-21
[QUOTE=quietglow]I disagree. I use and love gnome, so unless I want to look at ugly black backgrounds that I get when using superkaramba, I'm left with gdesklets. In my experience, gdesklet sensors are buggy, huge resource hogs and (by far the worst when we're talking eye candy) mostly not very good looking. If there are any offended gdesklet developers here, I'm sorry!

In contrast, Konfabulator widgets are very nice to look at and tend to be fairly lightweight. If I have to do some major reconstruction to get it running, then I'll probably drop the idea. I love crossover, though, and use it for lots of stuff (in addition to Office, which I use for work...can't wait for OO to suport comment bubbles in writer!)[/QUOTE]

100% agree
Also...ive made a few konfabulator widgets myself, so I just feel more comfortable with it in general.

---

### Post by BSDFreak on 2005-12-21
[QUOTE=quietglow]Illegal how? Does it end up adding some part of windows into the wine directory? Would it be illegal even if you own a copy of windows? Would you mind giving me a leading clue? :-)

I haven't really messed with wine configuration as of yet--Crossover just works for most everything I need so far.

Being able to run Konfabulator would be really dang cool, though. I owned it for mac before yahoo bought (or apple copied it :-)[/QUOTE]

You will have to supply what is missing. Now, even if you can successfully link it into your configuration there is no guarantee that it will work since these hacks have a tendency to mess up other things.

And it's illegal, at least in the US for all other use than intended use. (This isn't true everywhere so you may have luck finding a solution on an overseas website, should someone attempt a hack).

---

### Post by quietglow on 2005-12-21
You rock. :-) So the suggestion that it has something to do with winhttp, was that like a "feeling" or was that "look into this if you want this to work."?

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=quietglow]
 If I have to do some major reconstruction to get it running, then I'll probably drop the idea. [/QUOTE]

I figure that has to be the case. If I am wrong about that then it is worth the effort....it just seems that its one of those programs that is HARD to get working in WINE.

---

### Post by quietglow on 2005-12-21
Yeah, after messing with it now for a couple of hours, those gdesklets are starting to look pretty darn nice :-)

I found an older version of it (2.1) which seems to get a bit farther and does kick out the error that it needs the WinHTTP library. The problem is that I've got that dll in the system32 folder and its still giving the error. I'm getting pretty close to not having any other things to try.

---

### Post by quietglow on 2005-12-21
Well, I got it to install...finally. But it doesn't work: it gives a non-specific exception when it starts up and tries to run the default widget. Switching out other widgets for the default one doesn't help so I'm guessing there is a more basic problem.

---

### Post by BSDFreak on 2005-12-22
[QUOTE=quietglow]Yeah, after messing with it now for a couple of hours, those gdesklets are starting to look pretty darn nice :-)

I found an older version of it (2.1) which seems to get a bit farther and does kick out the error that it needs the WinHTTP library. The problem is that I've got that dll in the system32 folder and its still giving the error. I'm getting pretty close to not having any other things to try.[/QUOTE]

You'll need to update the winhttp package manually to make it work.

---

### Post by quietglow on 2005-12-22
To make it work or just to install? I've got it installed but it dies with an undefined exception when I run it. You think that might be an old winhttp issue? It would be helpful if I had some sort of debugging window to see what sort of error it was dying with.

Screenshot attached.

---

