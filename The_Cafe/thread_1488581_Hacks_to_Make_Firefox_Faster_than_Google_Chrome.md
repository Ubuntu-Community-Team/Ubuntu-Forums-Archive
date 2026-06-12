---
title: "Hacks to Make Firefox Faster than Google Chrome"
date: 2010-05-20
forum: The Cafe
---

### Post by ronnielsen1 on 2010-05-20
[http://www.junauza.com/2010/05/hacks-to-make-firefox-faster-than.html](http://www.junauza.com/2010/05/hacks-to-make-firefox-faster-than.html)

> Google Chrome has now eclipsed Mozilla Firefox in the speed category. However, I still use Firefox as my main web browser because it is still better than Chrome in certain areas.

But just recently, I tried a few tweaks that significantly improved the speed of Firefox making it a little bit snappier than the latest version of Google Chrome when loading webpages.


---

### Post by ukripper on 2010-05-20
Need explanation for each tweak made. This link doesn't explain that!

---

### Post by mikewhatever on 2010-05-20
This stuff has been posted a million times, with and without explanations.
[http://lmgtfy.com/?q=speedup+firefox](http://lmgtfy.com/?q=speedup+firefox)

---

### Post by lovinglinux on 2010-05-20
> **ronnielsen1 said:**
> Google Chrome has now eclipsed Mozilla Firefox in the speed category.

I'm not s sure about that. See [this test video](http://lovinglinuxblog.blogspot.com/2010/05/browser-speed-test.html) I did comparing a vanilla Firefox speed with a vanilla Chromium speed. It seems to me that, in the real world (outside benchmarking tools), the difference is not significant. Obviously that if you add tons of extensions like me, then the speed you inevitably go down.

> **ronnielsen1 said:**
> But just recently, I tried a few tweaks that significantly improved the speed of Firefox making it a little bit snappier than the latest version of Google Chrome when loading webpages. 

You should read the preference description on [mozillaZine Knowledge Base](http://kb.mozillazine.org) before applying any tweaks, specially the Caveats:

[content.notify.ontimer](http://kb.mozillazine.org/Content.notify.ontimer#Caveats)
[content.notify.interval](http://kb.mozillazine.org/Content.notify.interval#Caveats)
[content.switch.threshold](http://kb.mozillazine.org/Content.switch.threshold#Caveats)

---

### Post by cpplinux on 2010-05-20
Remove all the themes/extensions/plugins, then you can get a very fast and boring Firefox. Fun or fast, choose one.

---

### Post by Dragonbite on 2010-05-20
Something that makes Firefox faster? I'm all for it!

---

### Post by Shining Arcanine on 2010-05-20
While some of these things certainly help, they definitely do not make Firefox faster than Chromium. Firefox's renderer runs in a single thread (to my knowledge), which bottlenecks. Chromium's multiprocess approach has a different renderer thread in each process, which prevents such bottlenecks. Using these tweaks alleviates about 5% of the bottlenecks. Using Chromium alleviates the other 95% of the bottlenecks. You are not going to make Firefox faster than Chromium by doing these things.

---

### Post by andrewabc on 2010-05-20
Some of those 'hacks' have been around for years. Sometimes they make firefox slower.

The best way to make firefox faster is to put your profile into ram.
[Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475)

---

### Post by Frogs Hair on 2010-05-20
There is likely a reason Firefox was not set up that way to begin with, I would need that explained prior to trying .

---

### Post by mikewhatever on 2010-05-20
I think Firefox is fast enough as far as rendering pages goes. Some browsers are faster, others slower, what does it matter if a page renders in 0.15 or 0.19 seconds, especially if one uses Noscript :idea:? My only real gripe with Firefox is the time it takes to launch it.

---

### Post by Uncle Spellbinder on 2010-05-20
Firefox is already lighting quick for me. 30 plus add-ons and no lags at all. Flash works perfectly as well. So, bottom line: No hacks to speed up Firefox are needed at all. PERIOD

---

### Post by Dragonbite on 2010-05-20
> **Uncle Spellbinder said:**
> Firefox is already lighting quick for me. 30 plus add-ons and no lags at all. Flash works perfectly as well. So, bottom line: No hacks to speed up Firefox are needed at all. PERIOD

It might also depend on the system you're running.

My laptops are Pentium M's at 1.8ghz or less, with either 1GB ram or 512MB Ram. 

I haven't compared on the desktop, but that's only a P4 @ 2.4GHz with 2.5GB Ram.

---

### Post by jbrown96 on 2010-05-20
> **andrewabc said:**
> Some of those 'hacks' have been around for years. Sometimes they make firefox slower.

The best way to make firefox faster is to put your profile into ram.
[Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475)

That does work well, but it's difficult to setup and could cause problems during a crash. A better alternative is to install preload and modify the config to allow it to cache /home. 
I do use Chrome, but my hard drive isn't used at all loading it because preload has learned it's the most important thing to keep in memory.
```
sudo apt-get install preload
```
Then edit the mapprefix line in /etc/preload.conf to be ```
mapprefix = /usr/;/lib;/var/cache/;/home/;!/
``` It doesn't instantly speed Firefox up because it has to learn which files you use, but I've been using it for years and it really helps. 
I've made it more aggressive by increasing the memfree to 70 and decreasing minsize to 200000 (1/10 of default).

---

### Post by Dark Aspect on 2010-05-20
You can speed up Firefox by disabling the status bar and compressing the binary with upx:

```
upx -9 /usr/lib/firefox-3.6/firefox

```

```
user_pref("dom.disable_window_status_change", true);
```

Also see [link]("http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html")

---

### Post by tjeremiah on 2010-05-20
About the two browsers, as I've I said before, Chrome is cool but I cant seem to find a decent ad blocker that actually functions like the ones in FF. As for this tweak, ill try it out.

---

### Post by mamamia88 on 2010-05-20
well it seems to have worked great for me.  that was the only real reason i was using chrome to begin with.  i new some of these tricks but not all of them.  thanks again op

---

### Post by witeshark17 on 2010-05-21
FF will tune the performance soon enough. Anyway, plenty fast here. :popcorn:

---

### Post by XSAlliN on 2010-06-24
> **Shining Arcanine said:**
> While some of these things certainly help, they definitely do not make Firefox faster than Chromium. Firefox's renderer runs in a single thread (to my knowledge), which bottlenecks. Chromium's multiprocess approach has a different renderer thread in each process, which prevents such bottlenecks. Using these tweaks alleviates about 5% of the bottlenecks. Using Chromium alleviates the other 95% of the bottlenecks. You are not going to make Firefox faster than Chromium by doing these things.

It all depends on what you want from a browser, cause the speed of chrome comes with a price:


> As far as I'm concern, Chrome is the spy-ware browser...

But not a spy-ware for a specific type of users, but one for a major company like Google. Which means, you don't have to worry about Credit Card frauds or something like that... There's an old saying: "information is power" - Google being the biggest marketing corporation on the Internet has a very good use for this power. So, they won't harm users in any way, that would be against their "current" interests... They just want to gather data regarding users interests.

As you all know by now, at current times Internet is the best place for that:

-you want to buy something, you browse the Internet
-you're interested in some future gadgets, you browse the Internet
-you're looking for a specific product (from any domain) you browse the Internet
-you're looking for a specific place for a vacation, you browse the Internet.
... and so on.

Until Chrome was released, their search engine (Google) and their mail client (Gmail) was a very good tool for that, yet with Google Chrome they have even more control which obviously, can lead to more accurate results. This will increase their profits significantly, as mentioned above - without hurting those involved.

It's all up to you as user, if you agree with that or not... which is obviously coved by their EULA Yet, I strongly believe 99.9% of all Goggle Chrome users never looked at it (same as they proceed with any EULA).

========

I use Firefox for general usage, yet I also have Chromium installed for YouTube - since under Linux 64 bit flash doesn't work as wanted under Firefox, yet works pretty decent under Chromium. YouTube is also part of Google, so it makes no difference. And yes, I one of those rare people that don't accept their entire policy and also read EULA's.

...some of it is just ethics related, **[but this is something I won't accept]("http://forums.informaction.com/viewtopic.php?f=10&t=1676")**, yet I'm aware it's in Google's interest "to be non-functional". They're already loosing milions of $ with Firefox cause of Adblock and NoScript and only around 30% of FF users have this add-ons installed...

At current time is doesn't have the hardware acceleration of Chrome, but as a browser is fast enough and as far as I know "the most secure browser"... So, that's something worth considering... at least from my point of view.

---

### Post by stmiller on 2010-06-24
[https://developer.mozilla.org/en/Firefox_4_for_developers](https://developer.mozilla.org/en/Firefox_4_for_developers)

Wait for Firefox 4 beta due very soon...

---

### Post by del_diablo on 2010-06-24
> **Shining Arcanine said:**
> While some of these things certainly help, they definitely do not make Firefox faster than Chromium. Firefox's renderer runs in a single thread (to my knowledge), which bottlenecks. Chromium's multiprocess approach has a different renderer thread in each process, which prevents such bottlenecks. Using these tweaks alleviates about 5% of the bottlenecks. Using Chromium alleviates the other 95% of the bottlenecks. You are not going to make Firefox faster than Chromium by doing these things.

Its still slower than Opera, which runs better per thread.

---

