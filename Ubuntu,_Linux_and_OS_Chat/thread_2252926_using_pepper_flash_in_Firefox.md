---
title: "using pepper flash in Firefox"
date: 2014-11-15
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2014-11-15
Hi, this was posted on a thread which is now locked for other reasons, but I think it may be of interest so I take the moderator's suggestion and start a new thread.

In case you guys are not aware, now you can use up to date pepper flash on Firefox with a wrapper. [https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin) I am using it on Fedora 20, all video sites and audio sites I have tested work perfectly. Performance is no difference from 11.2 when  the latter works, but this  works also on sites that no longer work with flash 11.2. I find it smoother  than pipelight flash,--a wine wrapper for Windows flash,-- has less dependencies and easier to update, it is pretty sweet. :smile: 

Regarding security, since this is a wrapper, if you have Chrome  installed flash version would be kept up to date as long as Chrome is up  to date, this is better than using Chromium with pepper because flash  is often outdated in that case (right now Firefox shows flash 15 on my  Fedora install) The only downside is that sandboxing is not implemented,  but I think this is no more insecure that using system flash on Firefox  since there is no sandboxing feature for NAAPI plugins as far as I  understand.

Ubuntu users can install it with ppa [http://www.webupd8.org/2014/05/insta...in-ubuntu.html]("http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html")


*hardware acceleration is not supported atm, but then hw accelaration for flash 11.2 only works on Youtube anyway if it works at all and there are several ways to watch Youtube even without flash. Some features like webcam and access to drmed video stream are not implemented yet, see known issues from the first link above.

---

### Post by argonvegell on 2014-11-15
Have you tried running Flash games on it? Like FarmVille, CityVille, Candy Crush, etc, if so, how does it handle it?

---

### Post by monkeybrain20122 on 2014-11-16
I don't know, I don't play those games. You may want to try it out, if it doesn't work, just remove it and reinstall system flash (and maybe file a bug report) 

Edited: BTW many of the issues reported there have been fixed already.

---

### Post by Tar_Ni on 2014-11-16
Great. But this is still Alpha right? I may wait until all features are enabled, Flash 11.2 though old, still works for the vast majority of flash content.

Since I would prefer to avoid Google Chrome, will it work if I only install pepperflashplugin-nonfree from the software center? I know that the plugin need to be updated manually from the terminal but this is not an issue for me.

Thanks.

---

### Post by monkeybrain20122 on 2014-11-17
> **Tar_Ni said:**
> Great. But this is still Alpha right? I may wait until all features are enabled, Flash 11.2 though old, still works for the vast majority of flash content.

Since I would prefer to avoid Google Chrome, will it work if I only install pepperflashplugin-nonfree from the software center? I know that the plugin need to be updated manually from the terminal but this is not an issue for me.

Thanks.

It says it is alpha on the website but that message may be outdated. :) It is actually very stable and smooth. As far as videos and audio stuffs are concerned I think it is already fully working except maybe for some corner cases.

---

### Post by j0sk on 2014-12-13
Since FF is my choice of browser I will try this approuch.

---

### Post by Tar_Ni on 2014-12-13
The flash player plugin 11.2 for Firefox still play flash content on the vast majority of websites. From personal experience, issues have only been encountered in some Facebook games and a sports website. Besides that it still does the job..

I am glad that devs are looking at solutions though we know that Adobe Flash Player is not the way forward but rather HTML5. That being said, I won't install Google Chrome in my PC I don't trust them and for all I know it's a spyware and I prefer to avoid this method. I am looking for a confirmation if it will work using Chromium + pepperflashplugin-nonfree? If not, then I guess my last hope to use a wrapper will be with Opera which is working on implementing pepperflash and bringing their browser back on Linux.

---

### Post by j0sk on 2014-12-15
> **Tar_Ni said:**
> The flash player plugin 11.2 for Firefox still play flash content on the vast majority of websites. From personal experience, issues have only been encountered in some Facebook games and a sports website. Besides that it still does the job..

I am glad that devs are looking at solutions though we know that Adobe Flash Player is not the way forward but rather HTML5. That being said, I won't install Google Chrome in my PC I don't trust them and for all I know it's a spyware and I prefer to avoid this method. I am looking for a confirmation if it will work using Chromium + pepperflashplugin-nonfree? If not, then I guess my last hope to use a wrapper will be with Opera which is working on implementing pepperflash and bringing their browser back on Linux.

You're right. The existing Flash plugin for FF works on all websites that I use so I wont need the latest version of that plugin. Besides the Flash is dying anyway.

---

