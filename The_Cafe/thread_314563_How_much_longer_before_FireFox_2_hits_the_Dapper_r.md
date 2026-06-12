---
title: "How much longer before FireFox 2 hits the Dapper repos?"
date: 2006-12-07
forum: The Cafe
---

### Post by greggh on 2006-12-07
Anybody have any good guesses?

:confused:

---

### Post by givré on 2006-12-07
IMO, a long long time.
I guess, until firefox release security release of the 1.5 branch.

---

### Post by Kernel Sanders on 2006-12-07
Firefox 2.0 is crap. You're better off with 1.5

---

### Post by dbbolton on 2006-12-07
> ***John* said:**
> Firefox 2.0 is crap. You're better off with 1.5
i'm inclined to agree :/

---

### Post by agurk on 2006-12-07
Firefox 2.0 will never hit any Dapper repo, there are lots of threads about this already and you might also want to checkout the Launchpad discussion [https://launchpad.net/products/dapper-backports/+bug/68158](https://launchpad.net/products/dapper-backports/+bug/68158)

(And yes, 2.0 is a bit rough, but the upcoming 2.0.0.1 looks very solid here; no crashes the past week, running nightly builds)

---

### Post by rfruth on 2006-12-07
The released Firefox 2.0 is darn good !

---

### Post by givré on 2006-12-07
> **agurk said:**
> Firefox 2.0 will never hit any Dapper repo, there are lots of threads about this already and you might also want to checkout the Launchpad discussion [https://launchpad.net/products/dapper-backports/+bug/68158](https://launchpad.net/products/dapper-backports/+bug/68158)

Your bug report refer to a backport, that's something different than an update or a security update.
When ff 1.5 will reach end of life (in April 2007), they will have only too choice to do the regular and important security update :
- backport the change of the 2.0 branch to the 1.5 branch
- update FF to the 2.0 branch
The two options will be a real pain, but since dapper is LTS they will have to do it, and i think they will choose option 2. Backporting security fix from a totaly different branch during at least 2 years would be a real pain.

---

### Post by PatrickMay16 on 2006-12-07
> ***John* said:**
> Firefox 2.0 is crap. You're better off with 1.5

I agree entirely.

---

### Post by yabbadabbadont on 2006-12-07
> **givré said:**
> Your bug report refer to a backport, that's something different than an update or a security update.
When ff 1.5 will reach end of life (in April 2007), they will have only too choice to do the regular and important security update :
- backport the change of the 2.0 branch to the 1.5 branch
- update FF to the 2.0 branch
The two options will be a real pain, but since dapper is LTS they will have to do it, and i think they will choose option 2. Backporting security fix from a totaly different branch during at least 2 years would be a real pain.

I wonder if they will be able to keep the official branding when that happens?  Or maybe they will still keep submitting their patches to the Mozilla Foundation for approval even though the 1.5 series won't be supported.

---

### Post by agurk on 2006-12-07
> **givré said:**
> When ff 1.5 will reach end of life (in April 2007), they will have only too choice to do the regular and important security update :
- backport the change of the 2.0 branch to the 1.5 branch
- update FF to the 2.0 branch

Well, "end of life" just means Mozilla stops providing fixes for a product version, it doesn't mean that they'll stop accepting patches or that you can't patch it yourself, which is what e.g. Debian does and I expect Ubuntu will do as well.

---

### Post by user1397 on 2006-12-07
What do you all mean when saying that firefox 2.0 is crap?  I've never had one crash with it, whether in ubuntu, windows xp, and even mac os x...

am I a minority?

---

### Post by dbott67 on 2006-12-07
The version of FF 2.0 that ships with Edgy freezes like a Canadian lake in January!

Granted, I seem to have found that most of the crashes seem to stem whenever there is a flash advertisement on the web page (so it may not be a FF issue, per se, but rather a plug-in issue). Anyhow, it happens very frequently to me... but not always.

1.5 is far more stable IMO.

-Dave

---

### Post by rfruth on 2006-12-07
I must be holding my mouth just so cause Fx2 (that comes with Edgy) works fine for me be it QT, Flash, streaming audio/video ... I only have 1 extra theme & 3 extensions, that could be the difference :-k

---

### Post by dbott67 on 2006-12-07
Whatever the problem is, I experience very frequent lockups in Firefox.  I used Automatix to install the usual suspects (Flash, Java, et al.) and recently I started to experience 'hard freezes' of Firefox (requiring a kill -9 PID#).

Sometimes I'll use the "kill task" button and I notice a bunch of windows that appear to be in the same position as 'flash ads'.  The windows are about the scattered around the screen, generally 5 or 6 of them, with regular controls on them (min/max, restore, close).  Once I close one of them, they all close.

Very strange stuff.

I have 2 tabbed sites in my "home page", [www.cnn.com](www.cnn.com) and [www.tsn.ca](www.tsn.ca) (as well as a couple of forums - ubuntu, etc.).  It seems to happen whenever I'm popping between CNN & TSN.

---

### Post by esaym on 2006-12-07
No problems using swiftfox 2.0 in drapper.  Even has a quick and easy install script [http://getswiftfox.com/debian.htm](http://getswiftfox.com/debian.htm)

also automatix can install it.

---

### Post by greggh on 2006-12-07
> **esaym said:**
> No problems using swiftfox 2.0 in drapper.  Even has a quick and easy install script [http://getswiftfox.com/debian.htm](http://getswiftfox.com/debian.htm)

also automatix can install it.

I think swiftfox 2.0 is based on FF 1.5

Edit: I was wrong. I was thinking of the latest Iceweasel.

---

### Post by Polygon on 2006-12-07
ive never had any crashes with 2.0 in windows or in dapper ( i manually installed it)

---

### Post by greggh on 2006-12-07
> **Polygon said:**
> ive never had any crashes with 2.0 in windows or in dapper ( i manually installed it)

Where can I find the best instructions for manually installing FF2 in Dapper?

---

### Post by givré on 2006-12-07
For those who have a problem with FF+flash, you may try to launch it with :
```
XLIB_SKIP_ARGB_VISUALS=1 firefox
```
If that solve your problem, you should consider reopenning 
[https://bugs.launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942](https://bugs.launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942)
The problem was solve for me, but probably not for everybody...

---

### Post by aysiu on 2006-12-07
> **greggh said:**
> Where can I find the best instructions for manually installing FF2 in Dapper?
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by SunnyRabbiera on 2006-12-07
Firefox 2.0 works smothly for me, though i use it on dapper and not edgy.

---

### Post by greggh on 2006-12-07
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Thank you

---

### Post by durant1958 on 2006-12-08
> **agurk said:**
> Firefox 2.0 will never hit any Dapper repo, there are lots of threads about this already and you might also want to checkout the Launchpad discussion [https://launchpad.net/products/dapper-backports/+bug/68158](https://launchpad.net/products/dapper-backports/+bug/68158)

(And yes, 2.0 is a bit rough, but the upcoming 2.0.0.1 looks very solid here; no crashes the past week, running nightly builds)

I took the advice offered in bug thread.  I'm posting this from my nice shiny FireFox 2.0 running on openSUSE 10.1.

Sorry folks, but Ubuntu shot itself in the foot over this one.  Sad really, it didn't have to be this way.

Mark Gosdin

---

### Post by givré on 2006-12-08
> **durant1958 said:**
> 
Sorry folks, but Ubuntu shot itself in the foot over this one.  Sad really, it didn't have to be this way.

:confused: 
It was so hard to upgrade to edgy or to install it manually 

:confused: :confused:

---

### Post by greggh on 2006-12-08
> **givré said:**
> :confused: 
It was so hard to upgrade to edgy or to install it manually 

:confused: :confused:

I installed edgy fresh on my second HD and the fonts were so blurry and fat. I installed automatix2 and the fonts package and that didn't help, so I have to stick with Dapper untill they can fix the fonts issue with edgy.

---

### Post by givré on 2006-12-08
> **greggh said:**
> I installed edgy fresh on my second HD and the fonts were so blurry and fat. I installed automatix2 and the fonts package and that didn't help, so I have to stick with Dapper untill they can fix the fonts issue with edgy.
Hum, which font issue, the only potential font problem that i know is when 
you upgrade form dapper : [https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403](https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403)

Did you check that : [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)
```
Fonts
* Problem: Some applications, such as firefox, gedit, and terminal windows may have suboptimal fonts. [WWW] Bug #63403
* Workaround: Remove or replace your ~/.fonts.conf file

```

---

### Post by greggh on 2006-12-08
> **givré said:**
> Hum, which font issue, the only potential font problem that i know is when 
you upgrade form dapper : [https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403](https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403)

Did you check that : [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)
```
Fonts
* Problem: Some applications, such as firefox, gedit, and terminal windows may have suboptimal fonts. [WWW] Bug #63403
* Workaround: Remove or replace your ~/.fonts.conf file

```

I think I found a few others complaining of really bad fonts in FF and OO that did a fesh install. Maybe its not a common problem, but it affects my setup in edgy while the fonts looks perfect in dapper... same machine, just differnet HD. Also, I read a lot of folks that were affected by the fonts peoblem after the upgrade tried all suggested fixes including replacing the ~/.fonts.conf and still couldn't fix the problem.

---

### Post by givré on 2006-12-08
> **greggh said:**
> I think I found a few others complaining of really bad fonts in FF and OO that did a fesh install. Maybe its not a common problem, but it affects my setup in edgy while the fonts looks perfect in dapper... same machine, just differnet HD. Also, I read a lot of folks that were affected by the fonts peoblem after the upgrade tried all suggested fixes including replacing the ~/.fonts.conf and still couldn't fix the problem.
ok, but my point was different, and i still think that the attitude of durant1958 was stupid.
Going to openSUSE because the backport team don't want to backport FF...

---

### Post by greggh on 2006-12-08
> **givré said:**
> ok, but my point was different, and i still think that the attitude of durant1958 was stupid.
Going to openSUSE because the backport team don't want to backport FF...

Well, it does seem a bit unecessary, but that's the beautiful thing about GNU/Linux... freedom.

---

### Post by Brunellus on 2006-12-08
> **givré said:**
> ok, but my point was different, and i still think that the attitude of durant1958 was stupid.
Going to openSUSE because the backport team don't want to backport FF...
seems a bit extreme.  If you *need* FF2.0, then you can untar it to /home and run it from there until they decide to backport.  If not...then not.

---

### Post by aysiu on 2006-12-08
> **Brunellus said:**
> seems a bit extreme.  If you *need* FF2.0, then you can untar it to /home and run it from there until they decide to backport.  If not...then not.
Or run this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by FyreBrand on 2006-12-08
> **givré said:**
> ok, but my point was different, and i still think that the attitude of durant1958 was stupid.
Going to openSUSE because the backport team don't want to backport FF...
It is stupid.  In my opinion it's just a troll flame.  It's the same form of troll flame people use whenever they don't want to figure something out or they want to incite hoopla.  It's bunk.

---

