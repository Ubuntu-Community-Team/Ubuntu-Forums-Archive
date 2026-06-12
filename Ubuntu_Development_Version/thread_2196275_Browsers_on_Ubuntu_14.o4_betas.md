---
title: "Browsers on Ubuntu 14.o4 betas"
date: 2013-12-28
forum: Ubuntu Development Version
---

### Post by sam-c on 2013-12-28
This is Opera just now
trying firefox 
chromium
any known issues?

---

### Post by VinDSL on 2013-12-28
I run all three, depending on the situation, and yes, they all have known issues.

By far, my favorite is Chromium.  I mostly run raw trunk builds of Chromium.  Let's see...


Currently (a couple of days old):
```
Chromium	34.0.1762.0 (Developer Build 242590) 
OS	Linux 
Blink	537.36 (@164345)
JavaScript	V8 3.24.7
Flash	11.2 r202
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/34.0.1762.0 Safari/537.36
Command Line	 /home/vindsl/.chrome-linux/chrome --disable-setuid-sandbox --user-data-dir=/home/vindsl/.config/chromium-canary --flag-switches-begin --flag-switches-end
Executable Path	/home/vindsl/.chrome-linux/chrome
Profile Path	/home/vindsl/.config/chromium-canary/Default
Variations [...]
```


If you WANT issues (like I do) this is the buggiest version known to man.  Highly recommended, for trouble!  :D

Download:  [https://download-chromium.appspot.com/](https://download-chromium.appspot.com/)

If you don't want lots of issues, just use the stable version, in the PPA.


Personally, I can't wait for the Maxthon Cloud Browser Alpha to be released for Linux (it won't be long).

[b][list][[color=#BF0000]Beckham-style Video[/color]](http://youtu.be/1bEgTjQYx4Y)[/list]

[list][[color=#BF0000]Coming soon to Linux[/color]](http://forum.maxthon.com/thread-6581-1-1.html)[/list]

[list][[color=#BF0000]Extra Credit Reading[/color]](http://www.softpedia.com/reviews/windows/Maxthon-Cloud-Browser-Review-407911.shtml)[/list][/b]

But, you didn't ask about that...  ;)

---

### Post by zika on 2013-12-29
> **VinDSL said:**
> I run all three, depending on the situation, and yes, they all have known issues.

By far, my favorite is Chromium.  I mostly run raw trunk builds of Chromium.  Let's see...


Currently (a couple of days old):
```
Chromium    34.0.1762.0 (Developer Build 242590) 
OS    Linux 
Blink    537.36 (@164345)
JavaScript    V8 3.24.7
Flash    11.2 r202
User Agent    Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/34.0.1762.0 Safari/537.36
Command Line     /home/vindsl/.chrome-linux/chrome --disable-setuid-sandbox --user-data-dir=/home/vindsl/.config/chromium-canary --flag-switches-begin --flag-switches-end
Executable Path    /home/vindsl/.chrome-linux/chrome
Profile Path    /home/vindsl/.config/chromium-canary/Default
Variations [...]
```


If you WANT issues (like I do) this is the buggiest version known to man.  Highly recommended, for trouble!  :D

Download:  [https://download-chromium.appspot.com/](https://download-chromium.appspot.com/)

If you don't want lots of issues, just use the stable version, in the PPA.


Personally, I can't wait for the Maxthon Cloud Browser Alpha to be released for Linux (it won't be long).

[B]
[LIST]
[*][[COLOR=#BF0000]Beckham-style Video[/COLOR]]("http://youtu.be/1bEgTjQYx4Y")
[/LIST]

[LIST]
[*][[COLOR=#BF0000]Coming soon to Linux[/COLOR]]("http://forum.maxthon.com/thread-6581-1-1.html")
[/LIST]

[LIST]
[*][[COLOR=#BF0000]Extra Credit Reading[/COLOR]]("http://www.softpedia.com/reviews/windows/Maxthon-Cloud-Browser-Review-407911.shtml")
[/LIST]
[/B]

But, you didn't ask about that...  ;)
I always wanted to know who is the second guy (beside me) who uses AppSpot Chromium... Now I know... ;)

---

### Post by kansasnoob on 2013-12-29
I've been wondering about Opera. Anyone have the straight story?

---

### Post by VinDSL on 2013-12-29
> **kansasnoob said:**
> I've been wondering about Opera. Anyone have the straight story?
I seriously doubt it.  The devs are 'holding the cards close to their chests'.

It seems like everyone is  forking Chromium, these days, because it works so well across all sorts of different devices.  That way, regardless of what device you're using -- you're met with a familiar UI.  That's what Opera is trying to do too.  

It's the holy grail of browser development, with a pot of gold waiting at the end of the rainbow, for anyone that can figure out how to sway ppl to their honeypot, e.g. sign-up for their Cloud Services, so called.

The thing is, Opera fanbois are used to, and expect,  lots of classic Opera features that simply don't exist in any other browser.  Anything the devs cobble together is going to be measured against Opera 12.

Rumor has it that adding ALL of these classic Opera features to Chromium will be impossible, so the result will be a compromise.

I've also read that 'they' are continuing to develop Opera 12, in case the Chromium product doesn't sell (literally).

Have you heard anything?!?!?  I'm all ears...  :)

---

### Post by VinDSL on 2013-12-29
> **zika said:**
> I always wanted to know who is the second guy (beside me) who uses AppSpot Chromium... Now I know... ;)
Heh!  I wish I could make that 'API' message go away.  Do you get that, at startup?

I actually went over and generated a Chromium Project containing various APIs, generated a key, installed it, and all that nonsense.  And, I'm STILL getting the message at startup.

Oh, the joys of testing...  :D

---

### Post by Cavsfan on 2013-12-29
I have installed Chromium stable and use it a lot. Also installed Opera stable via this page I believe: [http://www.ubuntuupdates.org/ppa/opera](http://www.ubuntuupdates.org/ppa/opera)

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy opera
opera:
  Installed: 12.16.1860
  Candidate: 12.16.1860
  Version table:
 *** 12.16.1860 0
        500 http://deb.opera.com/opera/ stable/non-free amd64 Packages
        100 /var/lib/dpkg/status

```

I use Firefox some; got rid of NoScript as it's a pain most of the time and installed Ghostery and WOT. Same thing on Chromium.

I use Opera with no addons except WOT to see sites that the other 2 won't show due to the addons.

---

### Post by zika on 2013-12-29
> **VinDSL said:**
> Heh!  I wish I could make that 'API' message go away.  Do you get that, at startup?

I actually went over and generated a Chromium Project containing various APIs, generated a key, installed it, and all that nonsense.  And, I'm STILL getting the message at startup.

Oh, the joys of testing...  :DYes, message is there but it does not bother me at all... It does cripples Chromium in certain ways but I do not care...

---

### Post by craig10x on 2013-12-29
I use Chrome myself but i just got into 14.04 development and happened to notice that in the ubuntu software center as well as the synaptic package manager, ubuntu has added the pepperflash plug in for chromium which you can download and it must add it on to Chromium automatically...so, those who run Chromium, but want and easy way to add in the plug in, as of 14.04 you can easily get it now...

Also makes me wonder if they may go ahead after all and make Chromium the default browser...perhaps that is why they added that package on...
For me, i will still use Chrome itself, but this is certainly good for the Chromium users ;)

---

### Post by jerrylamos on 2013-12-29
> **craig10x said:**
> I use Chrome myself but i just got into 14.04 development and happened to notice that in the ubuntu software center as well as the synaptic package manager, ubuntu has added the pepperflash plug in for chromium which you can download and it must add it on to Chromium automatically...so, those who run Chromium, but want and easy way to add in the plug in, as of 14.04 you can easily get it now...

Also makes me wonder if they may go ahead after all and make Chromium the default browser...perhaps that is why they added that package on...
For me, i will still use Chrome itself, but this is certainly good for the Chromium users ;)
Hmmm, don't know anything about pepperflash.  Best video here is from Chromebook Acer 710.  Supposed to be 1.1 gHz dual core but runs video's faster than my faster processors running Ubuntu. 

I typically install Chrome Stable on Ubuntu lately because it automatically picks up added bookmarks from my 3 tablets running Android and my Chromebook whatever version of Google Chrome it shipped with. 

There's supposed to be some way to pick up bookmark changes in Firefox but haven't bothered to find out how.

Now on Chrome I do get "He's dead, Jim" from time to time example when I've got a zsync running too.  No such problem with Firefox.

---

### Post by sam-c on 2014-01-10
Thanx Guys,
Opera Again 14.04
Uncle Sam

---

### Post by inearlygaveup on 2014-01-18
[B]
VinDSL's Avatar
VinDSL    - Just foud this have you tried it yet[/B]  - was posted 7 Jan 2014 on  [http://forum.maxthon.com/thread-7544-1-1.html](http://forum.maxthon.com/thread-7544-1-1.html)

> Hi guys&#65292;

First Linux Beta for 2014 is available for you to download.

In this Beta, we have fixed a few crashes and bugs, and made some minor change.

Couldn't wait for you guys to try it.^_^

Downloads for 32-bit:

[http://dl.maxthon.com/mx_linux/package//maxthon_0.9.0.31_i386.deb](http://dl.maxthon.com/mx_linux/package//maxthon_0.9.0.31_i386.deb)
MD5: ad5d8c266625aae06bc3d53f14cb2e7a

[http://dl.maxthon.com/mx_linux/package//maxthon-0.9.0.31-i386.rpm](http://dl.maxthon.com/mx_linux/package//maxthon-0.9.0.31-i386.rpm)
MD5: 9369266d30c9046aca4eebd8e6bda8db
- See more at: [http://forum.maxthon.com/thread-7544-1-1.html#sthash.2D1TvMP6.dpuf](http://forum.maxthon.com/thread-7544-1-1.html#sthash.2D1TvMP6.dpuf)

---

### Post by VinDSL on 2014-01-18
> **inearlygaveup said:**
> [B]
VinDSL's Avatar
VinDSL    - Just foud this have you tried it yet[/B]  - was posted 7 Jan 2014 on  [http://forum.maxthon.com/thread-7544-1-1.html](http://forum.maxthon.com/thread-7544-1-1.html)
Yes, I've been testing it on Peppermint Four Re-Spin OS (Lubuntu fork).  Works great!

It's just a rough alpha, at this point.

They've made some major changes to the 'Customize & Control' menu, but otherwise it still looks n' feels like Chrome/Chromium.


[indent][[img]http://vindsl.com/images/vindsl-desktop-4-jan-2014-1(650x407).png[/img]](http://vindsl.com/images/vindsl-desktop-4-jan-2014-1.png)[/indent]


The coup d'état is going to be when they install their cloud add-ons:  'Cloud Push'. 'Cloud Sync', 'Cloud Download', 'Split Screen', and so forth.

Haven't installed it in Ubu 14.04 yet.  I need to do a fresh install, but I'm sure it will work... ;)

---

### Post by VinDSL on 2014-01-18
Whoopsie!  Just noticed they released a beta.

Thanks, for publishing that link.  

I'll go upgrade Maxthon right now. :D

---

### Post by VinDSL on 2014-01-18
So far, so good...  ;)


[indent][[img]http://vindsl.com/images/vindsl-desktop-18-jan-2014-1(650x407).png[/img]](http://vindsl.com/images/vindsl-desktop-18-jan-2014-1.png)[/indent]

---

### Post by chenriques on 2014-01-19
Hi :)

I'm testing Ubuntu 14.04 (daily) and it comes with Firefox 25.
I've tried updating Ubuntu but it does not have updates for Firefox. Why does Ubuntu 14.04 not update to Firefox 26 which is stable since December?

---

### Post by inearlygaveup on 2014-01-19
> **VinDSL said:**
> So far, so good...  ;)


[indent][[img]http://vindsl.com/images/vindsl-desktop-18-jan-2014-1(650x407).png[/img]](http://vindsl.com/images/vindsl-desktop-18-jan-2014-1.png)[/indent]

Like your desktop - just going to take another look peppermint

---

### Post by QDR06VV9 on 2014-01-19
> **chenriques said:**
> Hi :)

I'm testing Ubuntu 14.04 (daily) and it comes with Firefox 25.
I've tried updating Ubuntu but it does not have updates for Firefox. Why does Ubuntu 14.04 not update to Firefox 26 which is stable since December?

When ever firefox is not current in testing I always use this PPA [https://launchpad.net/~mozillateam/+archive/firefox-next](https://launchpad.net/~mozillateam/+archive/firefox-next)
You will have to use the saucy repo though obviously, Trusty is not populated yet but work Flawlessly;)

---

