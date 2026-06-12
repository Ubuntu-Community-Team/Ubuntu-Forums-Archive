---
title: "Networking - IE can't find sites"
date: 2010-01-19
forum: Wine
---

### Post by eyeteeth on 2010-01-19
I'm sorry, I'm missing something, probably basic.  Everything I've searched seems to suggests there is no network configuration needed as wine uses Linux's networking.

However, I cant load a web site in IE.  In different testing, when I used Play on Linux to install IE, the web site would come up... but I had no tool bars.  Just the window.

Currently I am back to Wine 1.1.36 only, no Play on Linux. Ubuntu 9.10.

Where or what should I start looking at?

If I can get this working, I'd be one ecstatic camper.  My MAIN task with this system involves working with a website that was of course... coded to work only in IE...  I wouldn't have to keep jumping back and forth anymore.

Thanks.

---

### Post by beastrace91 on 2010-01-19
What IE version are you trying to install/use? Does internet/network function for other Wine applications? (Maybe install firefox as a test if you do not have another Wine app to try)

~Jeff

---

### Post by eyeteeth on 2010-01-19
I tried IE6 that came in Wine, and I also installed IE8.  IE8 found the sites via Play on Linux, but it didn't have any tool bars.  IE8 had the tool bars in Wine alone, but the network doesn't appear to be configured?

I'll try an alternate browser.

---

### Post by eyeteeth on 2010-01-20
Well... of course... Firefox installs and works just fine in Wine.  Unfortunately... I NEED IE for this stooooopid website I have to access.

---

### Post by eyeteeth on 2010-01-20
No luck with IE7 either.

---

### Post by beastrace91 on 2010-01-20
Have you tried installing IE6/7 via [Winetricks](http://wiki.winehq.org/winetricks)? It automates the process for you.

~Jeff

---

### Post by eyeteeth on 2010-01-20
I have Winetricks, but have NOT tried installing either version via Winetricks. I'll take a look into that as well.

thanks.

---

### Post by eyeteeth on 2010-01-20
I didn't realize Winetricks included an IE installer.  Thanks for that.

Good news, is it got IE working somewhat.  Bad news, is that the particular site in question apparently was coded with ASP.net and it doesn't work with IE7, winetricks, and wine.  To be honest I couldn't use IE for more than a minute or so without it freezing.

Yet another reason to hate the behemoth.  All the little hooks include and anti-standard stuff they put out...

Thanks for your help, looks like I will be forced to continue to dual boot.  I'm not sure I can call this solved... but concluded.

---

### Post by beastrace91 on 2010-01-20
What are your hardware specs? Running Windows in [VirtualBox](http://virtualbox.org/) is what I do for the few websites that are IE only and those couple applications Wine doesn't run for me.

~Jeff

---

### Post by eyeteeth on 2010-01-28
Finally had a chance to check that out.  Looks like it would work far better than Wine, just unfortunate that it takes up so much more space. I can't fully test it as I made the mistake of installing Ubuntu 'inside' windows as I wasn't sure i'd like it was thought I was just testing.  As I mentioned... I hate going back to windows now...

thanks.

---

### Post by AllRadioisDead on 2010-01-28
I had the same problem. 
Oddly enough, after installing ie6 in winetricks to no success, I tried again and it gave me the option to reinstall and it began working. Kinda weird.

---

