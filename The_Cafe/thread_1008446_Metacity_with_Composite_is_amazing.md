---
title: "Metacity with Composite is amazing"
date: 2008-12-11
forum: The Cafe
---

### Post by LuisAugusto on 2008-12-11
I'm basely a KDE user who also use GNOME (in fact, in the development process of KDE 4.x I used GNOME as my main desktop without any problem) but I never tested Metacity with Composite, now that I did, there's only one thing I can say: WOW

It's so much better than KWin and Compiz, it doesn't have many features yet (application switcher and transparency are the only ones), however, it seems to be a lot smoother, in fact, it's the only accelerated windows manager which is as smooth as Aero when dragging windows around (Kwin is the worst), the previews in the alt + tab are far better looking too (which were also a lot better in Aero). 

Check it out, thumbnails are amazingly better, this is specially visible in the YaST and Firefox previews:

***Compiz:***
[IMG]http://img201.imageshack.us/img201/2379/compizyy3.png[/IMG]

***KWin***
[IMG]http://img81.imageshack.us/img81/7978/kwinxu6.png[/IMG]

***Metacity***
[IMG]http://img143.imageshack.us/img143/1415/metacitysg3.png[/IMG]


Outstanding, I'm really interested in Metacity now :)

---

### Post by LowSky on 2008-12-11
I'm glad you like it. Have you tried using Compiz with less settings being used. I have noticed that the less turned on the smoother it works

---

### Post by LuisAugusto on 2008-12-11
Yes, I had. It does improve, but Metacity and Aero are better, specially when things get "crowdy". And, since the only plugin I truly use is alt + tab and scale (and some minor animations, like minimize), I have never had an overloaded compiz. If metacity implements scale (present windows in KDE language) it would be perfect.

---

### Post by Mr. Picklesworth on 2008-12-11
Indeed, I love Metacity's compositor as well. It's easier on resources, too :)

I like that Metacity doesn't try to do everything under the sun, instead sticking to just what window managers are *supposed* to do. After all, the really important part is that Metacity supports compositing and the rgba colourmap so that applications can achieve neat window effects of their own.

---

### Post by SunnyRabbiera on 2008-12-11
> **LuisAugusto said:**
> Yes, I had. It does improve, but Metacity and Aero are better, specially when things get "crowdy". And, since the only plugin I truly use is alt + tab and scale (and some minor animations, like minimize), I have never had an overloaded compiz. If metacity implements scale (present windows in KDE language) it would be perfect.

For me Compiz is still better then aero for several reasons, one not as resource hoggy and two it can be customized.
But I am glad to see that Metacity is getting into the compositing game, its not as customizable as kwin or compiz but if the effects work then thats a good thing.

---

### Post by forrestcupp on 2008-12-11
> **Mr. Picklesworth said:**
> 
I like that Metacity doesn't try to do everything under the sun, instead sticking to just what window managers are *supposed* to do. 

True.  Why would anyone ever need things like the rain effect?

---

### Post by Mr. Picklesworth on 2008-12-11
> **forrestcupp said:**
> True.  Why would anyone ever need things like the rain effect?

It's not that it's useless that bothers me; it's that it is implemented close to the window manager. Granted, as a dynamically linked plugin, but still too close for sanity.

There's no reason for those things to not be separate applications, and numerous reasons why they should be -- one of which being system stability. Look at xpenguins or xsnow, for example, (there's a really neat panel applet and a Worms theme!). In Compiz land, those would be plugins to a ginormous application, but in Unix land we already *have* a kernel and a window manager to keep these things organized at runtime.

By the way, to really get people excited, you need a screenshot showing Metacity's window switcher with *more than three* windows in it. (Now, wouldn't it be nice if it took mouse input?...)

---

### Post by Wolki on 2008-12-11
> **LuisAugusto said:**
> It's so much better than KWin and Compiz, it doesn't have many features yet (application switcher and transparency are the only ones)

It also does drop shadows. ^^

Yeah, it's pretty cool, I use it (rebuilt to remove an ubuntu patch) on both my desktop and my laptop. It has some issues though:

- occasionally the right-click menu is full of noise for a moment right afer opening it
- you have to disable it to start compiz
- workspace switching feels rather slow (it's difficult to measure - probably it's faster than uncomposited but seems slow because the rest is so smooth...)

I hear some people are working on a clutter based metacity, which sounds great.

---

### Post by CholericKoala on 2008-12-11
it also takes bout 30 less mb of ram for me than compiz

---

### Post by Mr. Picklesworth on 2008-12-11
> **Wolki said:**
> - occasionally the right-click menu is full of noise for a moment right afer opening it

Are you using the NVidia proprietary drivers, by chance? The latest betas of their drivers resolve that issue. Intrepid may be getting an update with them at some point.

---

### Post by SunnyRabbiera on 2008-12-11
> **Mr. Picklesworth said:**
> Are you using the NVidia proprietary drivers, by chance? The latest betas of their drivers resolve that issue. Intrepid may be getting an update with them at some point.

Yeh right there i can see why compiz might look lower in quality then aero, but aero is still a space hog

---

### Post by LuisAugusto on 2008-12-11
> **SunnyRabbiera said:**
> For me Compiz is still better then aero for several reasons, one not as resource hoggy and two it can be customized.
But I am glad to see that Metacity is getting into the compositing game, its not as customizable as kwin or compiz but if the effects work then thats a good thing.

I have a crappy graphic card and I had never experience a slow down with Aero, it's always smooth, every single animation, and it doesn't have glitches, however, I never said it was better than Compiz, I mentioned specific issues. Compiz has more plugins and effects which is good for some.

> **Wolki said:**
> It also does drop shadows. ^^

Yes, I forgot to mention them, they're quite elegant btw, better looking than Kwin shadows.

> **Wolki said:**
> I hear some people are working on a clutter based metacity, which sounds great.

I wouldn't like a clutter Metacity Composite, just add scale, a minimize/open animation and maybe expo, everything else is useless (maybe some minor effects, like desaturated windows when log out, etc.)

No wobbly windows, airplane animation, exploding windows, cubes, spheres and all those things. Compiz is already there as clutter windows manager.


I truly liked that Metacity Composite, I'm sooo impressed with it XD.

---

### Post by loell on 2008-12-11
Metacity uses your CPU instead of your graphics card , if you happen to have a capable graphics card then it would be better utilizing them via compiz for compositing.

---

### Post by LuisAugusto on 2008-12-11
> **loell said:**
> Metacity uses your CPU instead of your graphics card , if you happen to have a capable graphics card then it would be better utilizing them via compiz for compositing.

Oh, I see, so is using XRender instead og OpenGL. Kwin has an option to use XRender too, but is more slower than all other implementations. metacity definitively does it better.

P.S: Interesting, I just tested Kwin using XRender against OpenGL, it's slower in everything... but moving windows. Tough it doesn't feature the beautiful thumbnails metacity does (and it isn't as smooth at moving windows).

---

### Post by igknighted on 2008-12-12
I've never tried metacity's composite, but kwin's has always been smooth as ice for me (intel graphics).  Much better than compiz.

---

### Post by LuisAugusto on 2008-12-12
> **igknighted said:**
> I've never tried metacity's composite, but kwin's has always been smooth as ice for me (intel graphics).  Much better than compiz.

I don't use Compiz, I prefer Kwin, but Compiz feels smoother here, and I use an intel graphic card too :/
Tough Kwin only feels less smoother when things get "crowdy", but for example, the un-minimize  effect looks better on Kwin.

---

### Post by kpkeerthi on 2008-12-12
Tried Metacity once but it hogged my CPU and also had some sporadic rendering artifacts (nvidia, its you!). 

I find Compiz much smoother and ligher on CPU. I just have minimal effects turned on that I find non-intrusive. Compiz might use a little more RAM but I have them plenty.

---

### Post by Wolki on 2008-12-12
> **Mr. Picklesworth said:**
> Are you using the NVidia proprietary drivers, by chance? The latest betas of their drivers resolve that issue.

No, I'm using the open-source ATI drivers. Good to know it's fixed for some people, though.

It doesn't seem as bad as it used to be, but I have to try it on my laptop which has less vram.

> **LuisAugusto said:**
> I wouldn't like a clutter Metacity Composite, just add scale, a minimize/open animation and maybe expo, everything else is useless (maybe some minor effects, like desaturated windows when log out, etc.)

No wobbly windows, airplane animation, exploding windows, cubes, spheres and all those things. Compiz is already there as clutter windows manager.

Compiz isn't based on clutter though (probably a misunderstanding, I mean the clutter library [http://www.clutter-project.org/](http://www.clutter-project.org/) ) And I feel an OpenGL metacity might good, not only will it allow a bit more bling but also hardware acceleration. I'd trust the metacity devlopers to not go overboard with effects.

[QUOTE=loell]Metacity uses your CPU instead of your graphics card , if you happen to have a capable graphics card then it would be better utilizing them via compiz for compositing.[/QUOTE]

If you're going for performance, probably. Some people don't like the way compiz handles windows though, which to me is still the main task of a window manager, and composited metacity gives us some of the smoothness.

---

### Post by FuturePilot on 2008-12-12
The major deal breaker for me with the Metacity compositor is that it does no syncing whatsoever, which causes terribly tearing when you move a window around, watch a video, or do any other fast motion.

---

### Post by SupaSonic on 2008-12-12
Hm, if Metacity's compositing uses CPU, then the compositing effect on opengl games shouldn't be as devastating as Compiz. Am I wrong here?

---

### Post by FuturePilot on 2008-12-12
Metacity's compositor does in fact use hardware acceleration, just Xrender instead of OpenGL

---

### Post by Metallion on 2008-12-12
I just want to say I seriously disagree with people calling compiz or certain plugins of it pointless. Fun is not pointless!! If it was we might as well stop watching movies or playing games.

Another would be that a more attractive, prettier desktop is more fun to work on and with that improves the users mood and therefore most likely his performance too. Not to mention how much it impresses non linux users. I'm not really trying to convert people to our os of choise but I know many people here are and believe me, compiz is THE number 1 way to catch people's attention.

Finally there's many plugins that I actually find really useful to work with. Just to name a few, opacity is great if you quickly need to see what's below your window. The cube or sphere is awesome for seeing what is on which workspace and annotate is very useful to mark certain things in a presentation.

---

### Post by LuisAugusto on 2008-12-12
> **Wolki said:**
> Compiz isn't based on clutter though (probably a misunderstanding, I mean the clutter library [http://www.clutter-project.org/](http://www.clutter-project.org/) ) And I feel an OpenGL metacity might good, not only will it allow a bit more bling but also hardware acceleration. I'd trust the metacity devlopers to not go overboard with effects.

Oh, yes, I knew the library, but the idea never crossed my mind XD.

> **Metallion said:**
> I just want to say I seriously disagree with people calling compiz or certain plugins of it pointless. Fun is not pointless!! If it was we might as well stop watching movies or playing games.

Another would be that a more attractive, prettier desktop is more fun to work on and with that improves the users mood and therefore most likely his performance too. Not to mention how much it impresses non linux users. I'm not really trying to convert people to our os of choise but I know many people here are and believe me, compiz is THE number 1 way to catch people's attention.

Finally there's many plugins that I actually find really useful to work with. Just to name a few, opacity is great if you quickly need to see what's below your window. The cube or sphere is awesome for seeing what is on which workspace and annotate is very useful to mark certain things in a presentation.

Snow on your desktop, flying airplanes windows, etc. Are not just useless, but get in your way too. I'm not against the development of those, use them if you want to, but they are useless in fact.

---

### Post by Metallion on 2008-12-12
> **LuisAugusto said:**
> Snow on your desktop, flying airplanes windows, etc. Are not just useless, but get in your way too. I'm not against the development of those, use them if you want to, but they are useless in fact.

So that means that you disagree with me that these things can increase the joy of working with the computer and with that the performance? And is it really any more useless than having a desktop background, a pretty gtk/qt style or a window decorator? You say it's useless but you don't really say why.

Since text doesn't show body language or any emotion I want to point out that there's no hostility whatsoever in this post. Just friendly discussion. :)

---

### Post by geoken on 2008-12-12
> **LuisAugusto said:**
> Oh, yes, I knew the library, but the idea never crossed my mind XD.



Snow on your desktop, flying airplanes windows, etc. Are not just useless, but get in your way too. I'm not against the development of those, use them if you want to, but they are useless in fact.

They don't get in my way. They also provide enjoyment to me and make it more pleasant for me to use my computer.

There is absolutely 0 difference in the amount of time it takes me to close a window and begin interacting with another window when I use the explode closing animation vs no closing animation.

---

### Post by LuisAugusto on 2008-12-12
Joymen =/= Use

I said it was good to develop them, but they're useless, some times we like useless things, that's another subject.

---

