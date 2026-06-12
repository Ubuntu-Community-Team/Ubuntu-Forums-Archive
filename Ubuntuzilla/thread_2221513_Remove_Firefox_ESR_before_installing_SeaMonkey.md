---
title: "Remove Firefox ESR before installing SeaMonkey?"
date: 2014-05-02
forum: Ubuntuzilla
---

### Post by kansasnoob on 2014-05-02
Hi nanotube, long time no see :)

I now maintain 53 individual **buntu PC's for other users (mostly elderly folks like me) and Firefox 29 complaints have my phone ringing off the hook. I first considered changing my identity and going into hiding but then I decided to explore some other options.

I've been playing with Qupzilla for a few months but it still freezes too frequently to be a viable option ATM, so I decided to check out Firefox ESR and installed it using this guide:

[http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html](http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html)

But I don't like the fact that I'd have to manually check for updates and then push them to 53 other end-users.

So I decided to see if Ubuntuzilla was still alive - very glad to see it is :D

So I'm going to try SeaMonkey now. Would there be any need to remove that Firefox ESR first? If so how?

I don't really care if I blow up this installation because I've been using it for SRU testing and it should be replaced anyway.

Thanks in advance.

---

### Post by Previous1 on 2014-05-02
I'm not nanotube but I've played with several iceweasel/ESR installs...

    According to that guide you've unpacked the mozilla tarball to /opt and created a symbolic link in /usr/bin/firefox. What iceweasel does when it finds a file there is make a diversion to /usr/bin/firefox.real (iirc) and "iceweasel" should still work (see man dpkg-divert).

The catch is with ubuntuzilla debs that also create a diversion (firefox.ubuntuzilla), but ubuntuzilla has no ESR debs (unless you make/distribute one yourself).

Note that installing Iceweasel in Ubuntu is a bit tricky - more details here:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=166191](http://forums.linuxmint.com/viewtopic.php?f=42&t=166191)

Also you may get GPG errors from time to time - when Debian messes up.

---

### Post by kansasnoob on 2014-05-02
Arrgh, I goofed :oops:

The past two days have been so taxing that my brain's rattling around like a BB in a tin can.

Everywhere I said Iceweasel I meant SeaMonkey, so I'll edit that.

---

### Post by nanotube on 2014-05-02
Hi kansasnoob, long time no see indeed :)
And hi previous1, thanks for helping out :)

Seamonkey won't conflict with whatever you did with firefox, because it links to /usr/bin/seamonkey, and doesn't touch the firefox link. the seamonkey profile also goes into ~/.mozilla/seamonkey, so doesn't touch firefox either.

So, you should be able to just sudo apt-get install seamonkey-mozilla-build, and will be good to go to use seamonkey and see how it goes.

That said, if you want to remove firefox esr, just undo the steps that you followed at tuxgarage.com. Basically, move the /usr/bin/firefox link back to where it was, and delete it from /opt. 

I installed ff29 myself here a day or two ago. No issues whatsoever. So I'm not sure what all the deal is with ff29. The main thing is to put the menu back (the File, Edit, View, etc. bar). Then it's basically same as it used to be. My guess is that you are getting complaints because your users are used to using the menu bar and it's no longer there. So just enable the menu bar, and /probably/ your problems will be solved. (The way to do it is to click the 'new menu button', click 'customize', then under 'show/hide toolbars' check 'menu bar'.)

Let know how it goes, and if you have any questions.

---

### Post by kansasnoob on 2014-05-03
> **nanotube said:**
> Hi kansasnoob, long time no see indeed :)
And hi previous1, thanks for helping out :)

Seamonkey won't conflict with whatever you did with firefox, because it links to /usr/bin/seamonkey, and doesn't touch the firefox link. the seamonkey profile also goes into ~/.mozilla/seamonkey, so doesn't touch firefox either.

So, you should be able to just sudo apt-get install seamonkey-mozilla-build, and will be good to go to use seamonkey and see how it goes.

That said, if you want to remove firefox esr, just undo the steps that you followed at tuxgarage.com. Basically, move the /usr/bin/firefox link back to where it was, and delete it from /opt. 

I installed ff29 myself here a day or two ago. No issues whatsoever. So I'm not sure what all the deal is with ff29. The main thing is to put the menu back (the File, Edit, View, etc. bar). Then it's basically same as it used to be. My guess is that you are getting complaints because your users are used to using the menu bar and it's no longer there. So just enable the menu bar, and /probably/ your problems will be solved. (The way to do it is to click the 'new menu button', click 'customize', then under 'show/hide toolbars' check 'menu bar'.)

Let know how it goes, and if you have any questions.

Thanks nanotube, I see where SeaMonkey ends up now:

```
lance@lance-desktop:~$ ls /opt
firefox  seamonkey

```

I was a bit shocked at how upset my end-users were with the change. I was able to get this far with the [Classic Theme Restorer]("https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/") add-on:

[ATTACH=CONFIG]252768[/ATTACH]

The only thing I haven't been able to do is restore color to the back/forward, stop, and home icons which I consider minor - but some of these old folks can be downright brutal in their criticism.

I shouldn't be surprised though, I have most using [this Precise classic setup]("http://ubuntuforums.org/showthread.php?t=1966370") and I still get complaints about the need to hold Alt to edit panels.

It's not like I get paid for this, it started in 2007 with helping one person move to Ubuntu from a borked Win ME box, then another, and another .............

Anyway I'm putting together different options and I'll put on a little show at the senior center on Sunday afternoon.

I do rather hope Chris Coulson get's the [Firefox ESR PPA]("https://launchpad.net/~team-esr/+archive/firefox-esr") up and running soon.

That would make life easier for me.

---

### Post by nanotube on 2014-05-03
> **kansasnoob said:**
> 
I was a bit shocked at how upset my end-users were with the change. I was able to get this far with the [Classic Theme Restorer]("https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/") add-on:

Yea i saw that one, but for me all i really care about is the menu. doesn't matter that there's an extra couple buttons to the right of the search box :)

> 
The only thing I haven't been able to do is restore color to the back/forward, stop, and home icons which I consider minor - but some of these old folks can be downright brutal in their criticism.

Heh, have you made it clear to them that you don't make firefox, so you are not to blame for firefox deciding to change some things around?

> 
It's not like I get paid for this, it started in 2007 with helping one person move to Ubuntu from a borked Win ME box, then another, and another .............

haha yea i know how that goes. now i try to avoid helping people >_> (jk)

> 
Anyway I'm putting together different options and I'll put on a little show at the senior center on Sunday afternoon.

nice! hope they appreciate it :)

> 
I do rather hope Chris Coulson get's the [Firefox ESR PPA]("https://launchpad.net/~team-esr/+archive/firefox-esr") up and running soon.
That would make life easier for me.

What are you going to do after 24ESR turns into 31ESR a few months later (currently 24ESR scheduled to go out of support in Oct 2014) ?
That's one of the reasons I'm not dealing with ESR in ubuntuzilla, even though with a bit of coding, I could add a firefox-mozilla-build-esr. Because it seems most complaints are cosmetic, and people will have to give it up in October anyway. So i figure, rather than put off the inevitable, best to just rip off the bandaid quickly and make the best of it. :)

I mean, if you can convince me that it's worth it for more than cosmetic reasons, i'll do it...

---

### Post by kansasnoob on 2014-05-08
Sorry for the long delay, I have the major unrest calmed to a slight grumble using the Classic Theme Restorer:

[ATTACH=CONFIG]253008[/ATTACH]

I've sent each user a copy of these screenshots:

[ATTACH=CONFIG]253009[/ATTACH]   [ATTACH=CONFIG]253013[/ATTACH]   [ATTACH=CONFIG]253011[/ATTACH]  [ATTACH=CONFIG]253012[/ATTACH]

I still have some interest in ESR but I need to do some more homework :)

Many thanks.

---

