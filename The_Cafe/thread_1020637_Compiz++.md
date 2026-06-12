---
title: "Compiz++"
date: 2008-12-24
forum: The Cafe
---

### Post by FuturePilot on 2008-12-24
This sounds rather interesting.
[http://www.phoronix.com/scan.php?page=news_item&px=Njk1Ng]("http://www.phoronix.com/scan.php?page=news_item&px=Njk1Ng")

Discuss.

---

### Post by Joeb454 on 2008-12-24
Sounds interesting.

Ultimately, I think if Compiz++ gives better memory management/performance/stability, it'll win without question...time will tell :)

---

### Post by Mr. Picklesworth on 2008-12-24
Does it manage windows properly or succeed at not breaking Fitt's law? If so, this sounds like a nice idea!

---

### Post by artir on 2008-12-24
Seems promising, but it says they gave up on the multi-screen support :(
It will end merging with the main compiz, like beryl..

---

### Post by Chame_Wizard on 2008-12-24
Looks nice to me .

---

### Post by artir on 2008-12-24
Seems promising, but it says they gave up on the multi-screen support :(
It will end merging with the main compiz, like beryl..

---

### Post by igknighted on 2008-12-24
> **artir said:**
> Seems promising, but it says they gave up on the multi-screen support :(
It will end merging with the main compiz, like beryl..

It's now written in c++, so merging back would require a rewrite (and it sounds like a loss of features), so I doubt that will happen.

Also, you can still use multiple screens.  You just can't stretch one cube across them.  This never really worked right in compiz anyways, so you aren't really losing anything.

---

### Post by billgoldberg on 2008-12-24
Sounds good to me.

Bring it on.

---

### Post by MasterNetra on 2008-12-24
Sounds promising indeed.

---

### Post by Nepherte on 2008-12-24
It sounds good for those who want eye candy.

---

### Post by klange on 2008-12-24
Just when I thought I could leave for a little while and work on my own stuff... And now I need to actually learn C++?

---

### Post by MaxIBoy on 2008-12-24
I see no reason why old C Compiz plugins won't work on Compiz++, as a lot of programming projects mix languages all the time. 

One thing I'm looking for is a compositing WM that won't fight games for control of the graphics card. Running games+compiz has resulted in terrible performance and system instability for me on two different computers. A fix for that would be cool, but given OpenGL's state-machine design, that would require some fancy coding work.


(By the way, C++ is very similar to C. I know C++, not C, but I can understand, and even modify C code without too many problems. I wouldn't worry, WindowsSucks.)

---

### Post by oedipuss on 2008-12-25
I'm kind of worried that compiz will eventually degenerate into elaborate but useless animation plugin addons without any real advancement. 
For instance, there still isn't a way other than keyboard shortcuts and screen edges to activate or use plugins, and that can become very confusing very fast (especially when defaults sometimes conflict with other apps, like the gimp). Window decorations could expose more than minimize and maximize actions, for example. 

I hope this renews the whole thing, if the devs choose to work with it.

---

### Post by plun on 2008-12-25
> **WindowsSucks said:**
> 

And now I need to actually learn C++?

No I don't think so after reading comments about this proposal...
but perhaps for other reasons...:-k

---

### Post by klange on 2008-12-25
> **plun said:**
> No I don't think so after reading comments about this proposal...
but perhaps for other reasons...:-k

Heh? Why does everyone seem to think I can sit back and do nothing? My comment was a joke anyway: Just when I thought I could settle down for a few months, I now have good reason to actually take the time to really learn C++ and get back into things.

@oedipuss: But you can do that, it just requires writing a decorator that can send DBus events (it's not Compiz's job to draw window decorations, so it's not technically our job to add this functionality to what we have, but don't worry: If and when b0le's new decorator is finished, it'll definitely have this and more)

---

### Post by plun on 2008-12-25
> **WindowsSucks said:**
> Heh? Why does everyone seem to think I can sit back and do nothing? My comment was a joke anyway: Just when I thought I could settle down for a few months, I now have good reason to actually take the time to really learn C++ and get back into things.




Ok... my comment was more about the need for learning C++ for Compiz. :wink:

(after reading a few "upstream" discussions)

---

### Post by MaxIBoy on 2008-12-25
> **WindowsSucks said:**
> @oedipuss: But you can do that, it just requires writing a decorator that can send DBus events (it's not Compiz's job to draw window decorations, so it's not technically our job to add this functionality to what we have, but don't worry: If and when b0le's new decorator is finished, it'll definitely have this and more)

Hopefully this functionality will be themable? (So you could apply a theme, and new buttons with new functions will appear.)

---

### Post by Twitch6000 on 2008-12-25
Now this is some great news :D.

It is even able to be a full windows manager =].

Anyone got a download of it yet lol?

---

### Post by Starks on 2008-12-31
Yeah.

[http://gitweb.compiz-fusion.org/?p=compiz;a=shortlog;h=refs/heads/compiz%2B%2B](http://gitweb.compiz-fusion.org/?p=compiz;a=shortlog;h=refs/heads/compiz%2B%2B)

---

### Post by CShadowRun on 2009-01-23
> **igknighted said:**
> It's now written in c++, so merging back would require a rewrite (and it sounds like a loss of features), so I doubt that will happen.

Also, you can still use multiple screens.  You just can't stretch one cube across them.  This never really worked right in compiz anyways, so you aren't really losing anything.

I don't think this is what was meant by dropping multiple screen support.
There are a few diffrent types of "multi screen" in linux

multi head - Having more than one physical monitor, with the screen spanned across all of them with xinerama/twinview/xrandr. Support for this is **NOT** being dropped

multi display - Having multiple X servers running. Support for this is being dropped

multi screen - Having multiple X screens (usually seperate graphics cards not connected by xinerama/twinview/xrandr. Support for this is being dropped.

Ultimately, this is a good thing. Compiz current support for multi display/screen is near unusable. Having a setup like this will allow you to run one instance of compiz per display/screen, and everything should "Just work".

So in short, Twinview/Xinrama/Xrandr users have nothing to worry about, and people with multi screen/display are going to be happy. So it's all good :)

---

### Post by kdub432 on 2009-01-29
It sends the project back to alpha. its a bad thing

---

### Post by MadAGu on 2009-08-28
At least this is some news... i thought the hole project was dead...

---

