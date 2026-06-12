---
title: "No more Flash Updates for Precise?"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2012-02-23
Just saw this...

SOURCE:  [http://www.computerworld.com/s/article/9224493/Adobe_to_Linux_users_Get_Chrome_or_forget_Flash](http://www.computerworld.com/s/article/9224493/Adobe_to_Linux_users_Get_Chrome_or_forget_Flash)

> **Adobe to Linux users: Get Chrome or forget Flash**

[COLOR="DimGray"]Computerworld[/COLOR] - Adobe today said that it would stop offering direct downloads of Flash Player for Linux, telling users to move to Google's Chrome browser, which bundles Flash with its updates.

Today's demotion of Flash Player on Linux to Chrome-only was the second time in the last three months that Adobe has withdrawn some or all support from a version of the popular media software: In November, Adobe announced it was abandoning development of Flash for mobile browsers, including the new Chrome for Android.[...]

Flash Player 11.2 will be the last version for Linux that Adobe offers as a download from its own website, but it promised to support that edition with security patches for at least the next five years. [...]

Adobe's decision will impact Mozilla's Firefox on Linux, likely locking that browser into Flash Player 11.2: Mozilla has said it was "not interested in or working on Pepper at this time."

Mozilla did not reply to questions on whether it's now reconsidering its position on Pepper, and failing that, what it would recommend Firefox users running Linux do.

Looks like Precise is going to be locked into Flash 11.2 for the next 5 years... unless Canonical switches the default browser to Chrome :confused:

---

### Post by rajeev1204 on 2012-02-23
Most websites ask for the flash 9 version to play anything so i dont think 11.2 is a problem for a few years. Security updates will continue for it though.

In the meantime, HTML 5 development will speed up i believe.

---

### Post by VinDSL on 2012-02-23
Did some checking, and Chromium is developing a Pepper API.

SOURCE: [https://sites.google.com/a/chromium.org/dev/developers/design-documents/pepper-plugin-implementation](https://sites.google.com/a/chromium.org/dev/developers/design-documents/pepper-plugin-implementation)

So, it looks like Precise will be hooked up (experimental feature at present).  ;)

Only thing I use Firefox for is downloading files (DTA plugin), so no matter...

---

### Post by dino99 on 2012-02-23
antitrust law will come :) and google will review its market

---

### Post by exploder on 2012-02-23
It is good that we know about this now because it has an impact on some of the future lenses that may be created for Unity. In some ways Adobe dropping support for Linux serves as a wake up call.

---

### Post by kuvanito on 2012-02-23
i think this will help:

1-sudo apt-get remove flashplugin-*
2-mkdir -p ~/.mozilla/plugins
3-ln -s /opt/google/chrome/libgcflashplayer.so ~/.mozilla/plugins/
4-Finally, open Firefox and select &#8216;Tools &#8211;> Add-ons&#8217;, then disable Shockwave Flash.

You are now using Googles Chrome Built in Flash.

---

### Post by zika on 2012-02-23
> **kuvanito said:**
> i think this will help:

1-sudo apt-get remove flashplugin-*
2-mkdir -p ~/.mozilla/plugins
3-ln -s /opt/google/chrome/libgcflashplayer.so ~/.mozilla/plugins/
4-Finally, open Firefox and select ‘Tools –> Add-ons’, then disable Shockwave Flash.

You are now using Googles Chrome Built in Flash.For quite some time (I think) there is no /opt/google/chrome/libgcflashplayer.so in GC latest 64-bit version...

---

### Post by effenberg0x0 on 2012-02-23
Adobe, YUNO develop working Flash first and get cocky later? :)

Seriously, they messed up with Flash for iPhone and were kicked out. Then they almost messed up Flash for Android (but got lucky) and now they are gonna mess with Flash for Linux and get kicked out. They should just be transparent about it: "Look, we don't wanna do Flash  anymore, we are doing other stuff now and we don't care about it". 

I'm not aware of a version of Flash for Linux that used a normal amount of CPU/GPU and was stable anyway...  

Regards,
Effenberg

---

### Post by DougieFresh4U on 2012-02-23
**[http://ubuntuforums.org/showthread.php?t=1929659](http://ubuntuforums.org/showthread.php?t=1929659)**
Was being discussed last night :P

---

### Post by prusswan on 2012-02-23
beginning of the end for flash, hope it is good riddance to those endless flash updates!

---

### Post by kurt18947 on 2012-02-23
> **prusswan said:**
> beginning of the end for flash, hope it is good riddance to those endless flash updates!

Forfeiting the mobile market (growth segment, anyone?), not making nice with Apple.  Growing Flash does not sound like a priority for Adobe.  Hopefully there won't be major functions added that 11.2 doesn't support.  Does Adobe see the writing on the wall with HTML5?

---

### Post by zika on 2012-03-04
> **zika said:**
> For quite some time (I think) there is no /opt/google/chrome/libgcflashplayer.so in GC latest 64-bit version...I was wrong. Today I found it in /opt/google/chrome/PepperFlash/libpepflashplayer.so
... Mea culpa...

---

### Post by screaminj3sus on 2012-03-04
Adobe will be providing security updates to flash 11.2 for FIVE years. You won't be forced to use google chrome anytime soon, and by then html5 should have matured and become more common.

---

### Post by paul_in_london on 2012-03-04
> **zika said:**
> I was wrong. Today I found it in /opt/google/chrome/PepperFlash/libpepflashplayer.so
... Mea culpa...

The built-in flash plugin is the same for me with this version of chrome (also 64 bit):

```
paul@precise-64:~$ apt-cache policy google-chrome-unstable
google-chrome-unstable:
  Installed: 19.0.1055.1-r123982
  Candidate: 19.0.1055.1-r123982
```

but I've disabled it and am using the standard flash plugin at the moment.

Having said that, I still use FF the vast majority of the time. I may need to use chrome more in future though unless mozilla has a change of heart of decides to add support for the pepper plugin api.

---

### Post by zika on 2012-03-04
> **paul_in_london said:**
> The built-in flash plugin is the same for me with this version of chrome (also 64 bit):

```
paul@precise-64:~$ apt-cache policy google-chrome-unstable
google-chrome-unstable:
  Installed: 19.0.1055.1-r123982
  Candidate: 19.0.1055.1-r123982
```but I've disabled it and am using the standard flash plugin at the moment.

Having said that, I still use FF the vast majority of the time. I may need to use chrome more in future though unless mozilla has a change of heart of decides to add support for the pepper plugin api.
A post of Yours ([http://ubuntuforums.org/showpost.php?p=11738095&postcount=6](http://ubuntuforums.org/showpost.php?p=11738095&postcount=6)) made me dig deeper and I'm just stating that I was not diligent enough to search deep enough... ;)

---

### Post by paul_in_london on 2012-03-04
> **zika said:**
> A post of Yours ([http://ubuntuforums.org/showpost.php?p=11738095&postcount=6](http://ubuntuforums.org/showpost.php?p=11738095&postcount=6)) made me dig deeper and I'm just stating that I was not diligent enough to search deep enough... ;)

Thanks. I understand - I was just chipping in! :)

---

### Post by alexcckll on 2012-04-03
Buggers up iPlayer usage if the BBC decide to update their floor to Flash 12 in the future...

---

### Post by philinux on 2012-04-03
> **alexcckll said:**
> Buggers up iPlayer usage if the BBC decide to update their floor to Flash 12 in the future...

See post #1. Chrome will still get updates. It's just firefox that gets the hit.

---

### Post by BigCityCat on 2012-04-03
> **zika said:**
> I was wrong. Today I found it in /opt/google/chrome/PepperFlash/libpepflashplayer.so
... Mea culpa...

I didn't think this was released yet?

---

### Post by alexcckll on 2012-04-03
> **philinux said:**
> See post #1. Chrome will still get updates. It's just firefox that gets the hit.
So is Chrome going to be the fully supported browser going forward? All updates being applied through Update Manager etc etc?  Just that the scuttlebutt suggests that Chromium WON'T be getting Adobe code...

And what about security tools like Noscript and AdBlock?

---

### Post by philinux on 2012-04-03
> **alexcckll said:**
> So is Chrome going to be the fully supported browser going forward? All updates being applied through Update Manager etc etc?  Just that the scuttlebutt suggests that Chromium WON'T be getting Adobe code...

And what about security tools like Noscript and AdBlock?

I don't there's an answer just now. Who knows what Mozilla might do.

---

### Post by alexcckll on 2012-04-04
So will I be able to use BBC iPlayer, We7 etc etc in Ubuntu going forward?  And will everything be available through Software Centre?  Or will i have to go back to Windows?

---

### Post by forrestcupp on 2012-04-04
> **alexcckll said:**
> So will I be able to use BBC iPlayer, We7 etc etc in Ubuntu going forward?  And will everything be available through Software Centre?  Or will i have to go back to Windows?

I doubt if those web sites will change their Flash requirements to be beyond the last one that is supported in Linux. They're not giving us updates, but they're also not intruding into our computers and forcefully uninstalling the versions of Flash that we have installed, either. :)

The world is headed toward html5, and like someone else said early on, most web sites only require Flash 9. We'll probably mostly be safe with what we have.

---

### Post by zika on 2012-04-14
It kind of clarified my vision on all this: [http://www.bbc.com/news/technology-17663669](http://www.bbc.com/news/technology-17663669)

---

### Post by Avaritia on 2012-04-14
I wonder how much money Google 'donated' to Adobe to make Chrome the default browser for watching flash videos.

---

### Post by VinDSL on 2012-04-14
Heh!  Insightful and rather ironic...

Check this out:  ["Oh, my! I'm about to abandon Firefox, in favor of Chrome..."]("http://forums.anandtech.com/showthread.php?t=2073956") (VinDSL thread on Anandtech)

I went on a quest for a Fx replacement, 2 years ago.

99.9% of the time, I use Chromium, these days, i.e. not Chrome.

I'm too paranoid to use Google Chrome... with their connections to NSA!

It's Chromium & DuckDuckGo for me, until further notice...  ;)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-14
> **VinDSL said:**
> 99.9% of the time, I use Chromium, these days, i.e. not Chrome.

From your post over there, I came to a conclusion it's Opera you use most. Why did you go back to Chromium?

---

### Post by VinDSL on 2012-04-14
> **&#1058 said:**
> From your post over there, I came to a conclusion it's Opera you use most. Why did you go back to Chromium?
Well...

I actually prefer Opera-**[COLOR="DarkRed"]Next[/COLOR]** to everything else, but it has issues with Ubu +1

Current problem is -- I run my tabs on the bottom, but lately, if the tabs are on the bottom, the menu button stays on the top, along with a big butt fugly space.

It might be a theming problem...

Anyway, it's stuff like that, which keeps me from using it all the time.  ;)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-14
I also use Opera Next, alongside with stable Opera, with the usage ratio 95% to 5% respectively. But to be fair I've never tried changing position of tab bar.

Personally, what bothers me most with Opera (any version) on Linux is terrible behaviour of Flash plugin :( To make myself clear right here, I really dis-like the Flash plugin and its concept in whole. However, it is a bitter reality that one still can't surf the web without it: from media players to games to banners to page elements, Flash is (sadly) scattered all around our virtual environment.

Issues I encounter in Opera with Flash include obnoxious CPU consumption, awful quality of video when not in full screen, impossible typing of non-english text in Flash (forms and games), terrible crashes of Flash plugin when switching tabs or changing page zoom etc. All this makes my combined Ubuntu+Opera+Flash usage experience miserable :-({|=

On the other side, I can't see myself not using Opera on any plarform because of its mouse guestures, keyboard shortcuts, built in EVERYTHING (mail/rss client, irc client, torrent client), blistering speed, fanatical standards support, super cool design, an infinite list of settings available for fine tuning, plus a couple dozen more less important features.

Having said all this, it actually makes me very happy to see what appears to be a beginning of the final end of one unfortunate technology (in my opinion). I am eagerly looking forward to the day when I won't be forced to struggle with the F plugin in my Opera on my Ubuntu.

---

### Post by VinDSL on 2012-04-14
> **&#1058 said:**
> I also use Opera Next, alongside with stable Opera, with the usage ratio 95% to 5% respectively. But to be fair I've never tried changing position of tab bar.
w00t!  Thanks for bringing this up!  :)

I just got the menu button to go to the bottom, on the first try.

Heh!  I swear, I must have spent 2 hours trying to get it to move to the bottom, the last time I tried...

Anyway, I L-O-V-E having the tabs on the bottom.  But, Opera is the only browser that does it right.  Opera gets copied a LOT (ppl don't realize it), but they never have duplicated the look n' feel of Opera tabs, on the bottom.

Here's how it looks.  See what you think...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-14-apr-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-14-apr-2012-2.png")[/INDENT]

---

