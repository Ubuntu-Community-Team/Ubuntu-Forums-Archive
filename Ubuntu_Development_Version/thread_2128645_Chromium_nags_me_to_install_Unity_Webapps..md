---
title: "Chromium nags me to install Unity Webapps."
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by The Cog on 2013-03-23
Chromium browser keeps nagging me to install Unity WebApps plugin.
 As far as I can tell, that's something to do with Unity, which I don't use (I use XFCE).
Does anyone know how I can stop it from nagging me, or do I just have to stop using Chromium?

---

### Post by mc4man on 2013-03-23
Don't have chromium but I see it would install 2 webapps related packages - 
unity-chromium-extension
webaccounts-chromium-extension 
Plus this is already installed here - 
webaccounts-extension-common

likely if you remove the 1st. 2 the nag may go. (or just the 1st.

Edit - couldn't resist - it appears here that removing the 1st package should stop this though you may need to do a log out/in after.

---

### Post by pqwoerituytrueiwoq on 2013-03-23
> **mc4man said:**
> Don't have chromium but I see it would install 2 webapps related packages - 
unity-chromium-extension
webaccounts-chromium-extension 
Plus this is already installed here - 
webaccounts-extension-common

likely if you remove the 1st. 2 the nag may go. (or just the 1st.

Edit - couldn't resist - it appears here that removing the 1st package should stop this though you may need to do a log out/in after.

i have removed unity-chromium-extension, webaccounts-chromium-extension, webaccounts-extension-common
the only chromium pachges installed are chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg

this is the thread i made: [http://ubuntuforums.org/showthread.php?t=2128210](http://ubuntuforums.org/showthread.php?t=2128210)

---

### Post by vasa1 on 2013-03-23
> **The Cog said:**
> Chromium browser keeps nagging me to install Unity WebApps plugin.
 As far as I can tell, that's something to do with Unity, **which I don't use (I use XFCE)**.
Does anyone know how I can stop it from nagging me, or do I just have to stop using Chromium?
Is Xfce the only DE or do you also have Unity installed and choose Xfce at the time of logging in?

---

### Post by pqwoerituytrueiwoq on 2013-03-23
i only have xfce installed, only unity stuff i have is a dependency of xchat

---

### Post by The Cog on 2013-03-24
@pc4man, @pqwoerituytrueiwoq: Ah, thank you. 

unity-chromium-extension and webaccounts-chromium-extension are listed as recommended by chromium-browser. 
And webaccounts-chromium-extension depends on webaccounts-extension-common. 

I have removed these three packages and deleted the extensions from chromium (menu tools / extensions). 
Now the nagging has stopped. 

@vasa1: I have only installed Xubuntu, which of course uses XFCE. But as you see, the unity nagware was installed as part of Chromium, not as part of unity.


If I wanted commercial popups, I'd buy a windows box from the high street. Eugh!
Thanks for your help folks. Marking the thread as solved.

---

### Post by zika on 2013-03-24
As far as I can remember (seing them not installed now, even with google-chrome) I did not purge them in near past so I do not think that they came on my machine with any install...

---

### Post by vasa1 on 2013-03-24
> **The Cog said:**
> ...
@vasa1: I have only installed Xubuntu, which of course uses XFCE. But as you see, the unity nagware was installed as part of Chromium, not as part of unity.
...
Thanks! The Lubuntu team will continue to have "Chromium" as the default browser in 13.04. Should be some interesting reactions if these extensions are present.

---

### Post by vasa1 on 2013-03-24
> **zika said:**
> As far as I can remember (seing them not installed now, even with google-chrome) I did not purge them in near past so I do not think that they came on my machine with any install...
Google Chrome isn't modified by Canonical the way Chromium is. So my guess is that users of Chrome (on any DE) won't experience any side-effects other than lack of "integration" with this whole web apps thing.

Edit: I guess the same thing happens with Firefox as well.

---

### Post by zika on 2013-03-24
> **vasa1 said:**
> Google Chrome isn't modified by Canonical **the way Chromium is**. So my guess is that users of Chrome (on any DE) won't experience any side-effects other than lack of "integration" with this whole web apps thing.

Edit: I guess the same thing happens with Firefox as well.You'we got point there, I do dont have Chroium &#8222;installed&#8220; since I'm using Canary and Iron as well as FF-Nightly expanded from tar.gz...

---

### Post by vasa1 on 2013-03-24
> **zika said:**
> You'we got point there, I do dont have Chroium „installed“ since I'm using Canary and Iron as well as FF-Nightly expanded from tar.gz...

At the risk of hijacking this thread, where do you get Canary from? I thought it was only for MS Windows.

---

### Post by stinkeye on 2013-03-24
> **The Cog said:**
> Chromium browser keeps nagging me to install Unity WebApps plugin.
 As far as I can tell, that's something to do with Unity, which I don't use (I use XFCE).
Does anyone know how I can stop it from nagging me, or do I just have to stop using Chromium?
Possibly this dconf setting...
com.canonical.unity.webapps integration-allowed

Get current
```
gsettings get com.canonical.unity.webapps integration-allowed
```

Disable
```
gsettings set com.canonical.unity.webapps integration-allowed false
```

---

### Post by zika on 2013-03-24
> **vasa1 said:**
> At the risk of hijacking this thread, where do you get Canary from? I thought it was only for MS Windows.If get punished, I'll say You made me to do this...
[Canary]("http://download-chromium.appspot.com/")
[Iron](http://www.srware.net/forum/viewtopic.php?f=18&t=6813)

---

### Post by tjeremiah on 2013-03-24
do webapps work well in 13.04? In the beginning of 12.10, they did, but as updates came around the feature became useless.

---

### Post by VinDSL on 2013-03-24
> **vasa1 said:**
> At the risk of hijacking this thread, where do you get Canary from? I thought it was only for MS Windows.

> **zika said:**
> If get punished, I'll say You made me to do this...
[Canary]("http://download-chromium.appspot.com/")
[Iron](http://www.srware.net/forum/viewtopic.php?f=18&t=6813)
I'm running Canary, too.  But, it's still Chromium, no :confused:

Here's my "About Chromium"

[INDENT][ATTACH=CONFIG]240494[/ATTACH][/INDENT]

BTW, Chromium Canary is unstable/untested, so let_the_buyer_beware.  :)

For the most part it works great, but occasionally you'll experience some strange anomalies...

---

### Post by vasa1 on 2013-03-24
> **zika said:**
> If get punished, I'll say You made me to do this...
[Canary]("http://download-chromium.appspot.com/")
...
Okay, thanks! I think this is someone's personal site.

---

### Post by zika on 2013-03-24
> **vasa1 said:**
> Okay, thanks! I think this is someone's personal site.Beware: at least two upgrades are available daily... I do not think that it could be personal. If it is it is one diligent person for sure... ;)

---

### Post by VinDSL on 2013-03-24
> **vasa1 said:**
> Okay, thanks! I think this is someone's personal site.
Yes n' no. ;)

It's hard to read, but...

Site was created by François Beaufort:  [https://plus.google.com/100132233764003563318/posts](https://plus.google.com/100132233764003563318/posts)

Now maintained by the Chrome team: [https://code.google.com/team/index.html?product=chrome](https://code.google.com/team/index.html?product=chrome)

---

### Post by VinDSL on 2013-03-24
> **zika said:**
> Beware: at least two upgrades are available daily...
True!

I usually upgrade Canary about once a week, but...

I could upgrade it when I'm bored; which is also at least two times a day.  LoL!  :D

---

### Post by vasa1 on 2013-03-24
> **VinDSL said:**
> Yes n' no. ;)
It's hard to read, but...
...
That was it :)

---

### Post by VinDSL on 2013-03-24
> **vasa1 said:**
> That was it :)
BTW, I run Chromium Canary as a standalone install, in my home folder. I *think* zika does the same (although we go about it in different ways).

Chromium Canary is straight off the trunk. It "may be tremendously buggy" (quoting the website) and often has more issues than a New York magazine stand (in my experience). But it's still fun, living on the fringe-edge of computing, you know?

If you decide to run Canary, I strongly suggest you don't depend on it for anything important, like placing an online order, doing electronic money transfers, or whatever.  It's likely to put you in the jackpot -- Murphy's Law, and all that stuff...

Personally, I maintain an official PPA install of Chromium too, for use during those times when you just can't take any chances of your browser going janky on you in the middle of a session.  ;)

Just saying...

---

### Post by vasa1 on 2013-03-25
> **VinDSL said:**
> ... But it's still fun, living on the fringe-edge of computing, you know?

If you decide to run Canary, ...
Just saying...

Thanks for the input but I'm one of those boring KISS types who uses Chrome stable :) I was just curious because I hadn't heard of Chromium Canary. I knew of Chrome Canary (for Windows).

---

### Post by zika on 2013-03-25
> **VinDSL said:**
> True!

I usually upgrade Canary about once a week, but...

I could upgrade it when I'm bored; which is also at least two times a day.  LoL!  :DI use Canary to feed my upgrade-addiction so the rest of stuff is less endangered... ;)

---

### Post by zika on 2013-03-25
> **VinDSL said:**
> BTW, I run Chromium Canary as a standalone install, in my home folder. I *think* zika does the same (although we go about it in different ways).

Chromium Canary is straight off the trunk. It "may be tremendously buggy" (quoting the website) and often has more issues than a New York magazine stand (in my experience). But it's still fun, living on the fringe-edge of computing, you know?

If you decide to run Canary, I strongly suggest you don't depend on it for anything important, like placing an online order, doing electronic money transfers, or whatever.  It's likely to put you in the jackpot -- Murphy's Law, and all that stuff...

Personally, I maintain an official PPA install of Chromium too, for use during those times when you just can't take any chances of your browser going janky on you in the middle of a session.  ;)

Just saying...Different is the name of the game... ;)
I (knock-knock-knock-on-the wood) did not have any major issues with Canary... Even though I have it heavily burdened with almost all switches that could be turned on for speed and... I can honestly say I like it... But, yes, most of the time I use IRON... ;) Mainly because I see a lot of &#8222;collision ahead&#8220; in X-logs... Even though, collision does not happen at the end...

---

### Post by zerubbabel on 2013-04-05
> **The Cog said:**
> @pc4man, @pqwoerituytrueiwoq: Ah, thank you. 

unity-chromium-extension and webaccounts-chromium-extension are listed as recommended by chromium-browser. 
And webaccounts-chromium-extension depends on webaccounts-extension-common. 

I have removed these three packages and deleted the extensions from chromium (menu tools / extensions). 
Now the nagging has stopped. 

@vasa1: I have only installed Xubuntu, which of course uses XFCE. But as you see, the unity nagware was installed as part of Chromium, not as part of unity.


If I wanted commercial popups, I'd buy a windows box from the high street. Eugh!
Thanks for your help folks. Marking the thread as solved.

Suddenly, after installing the latest round up updates to Kubuntu 13.04, Chromium is nagging me with this same message, and when I click "install plug-in" it leads to a page about "unity-chromium-extension" version 2.4.4. I currently have version 2.4.6 installed (it was one of the updates installed this morning). Even if I remove all three packages in the above quote, I am still nagged with this same "Unity WebApps plugin" message. I know this thread is marked "Solved" but evidently the problem is not solved. So how can I get rid of this annoying message? It makes using Chromium very distracting.

---

### Post by pfeiffep on 2013-04-05
> [COLOR=#000000]Google Chrome isn't modified by Canonical the way Chromium is. So my guess is that users of Chrome (on any DE) won't experience any side-effects other than lack of "integration" with this whole web apps thing.[/COLOR]

[COLOR=#000000]Edit: I guess the same thing happens with Firefox as well.[/COLOR]

When I attempted using Chrome (DE gnome session fall back) any 'bug' anyplace was associated with Chrome in that apport stated to remove a non-supported app. I then installed Chromium and all future bugs were handled as expected

---

