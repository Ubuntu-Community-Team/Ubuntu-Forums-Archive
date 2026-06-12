---
title: "Firefox destroying my computer, Chromium is fine"
date: 2015-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by vperaino on 2015-11-03
Here is a screenshot of Conky running on my computer. The first half of the activity graphs are with both Chromium and Firefox running at the same time. Nothing special on either of them, just a few rudimentary web pages. 

The second half of the activity graphs show my computer with Firefox closed, but Chromium still running (nothing else changed). 

 Hardware acceleration is turned off for both browsers. 

[IMG]http://i.imgur.com/hZr3H9H.png[/IMG]

Firefox version: 41.0.2

Xubuntu version: 14.04.3

The hell, Mozilla?

EDIT: I might also mention that this is happening on two completely different hardware sets. This issue occurred on one machine, then I took the hard drive out, ported it to another machine entirely, same problem.

---

### Post by tgalati4 on 2015-11-05
Firefox is a hog.  Especially if you have some plug-ins or synchronization running.  What plug-ins are you running?  You need to turn on all the experimental hardware acceleration features to free up CPU cycles.

---

### Post by frank18 on 2015-11-05
> **tgalati4 said:**
> Firefox is a hog.  Especially if you have some plug-ins or synchronization running.  What plug-ins are you running?  You need to turn on all the experimental hardware acceleration features to free up CPU cycles.



That's why i use google  Chrome in xubuntu 14.04 on my old P4 and it's  3 times faster then Ffox

---

### Post by s9032g@comcast.net on 2015-11-05
One of the top ten steps after getting Xubuntu is to get rid of Firefox and install Chromium. The latter is simple, fast, and much more in line with Linux thinking (in my opinion).
Be sure that you use something like Synaptic to get rid of Firefox completely or you will always see Firefox updates offered for things like language packs. 

I think that I read that Firefox will no longer be the standard on 16.04.

---

### Post by Sweet_Baby_Jamie on 2015-11-06
If you like Firefox, you might consider the Qupzilla browser or Seamonkey (my favorite!), both Mozilla projects that aren't nearly as resource-hungry as Firefox.

---

### Post by veggie2 on 2015-11-06
I add another alternative which is Pale Moon Browser. A fork of Firefox with the old style  and extremely light .

---

### Post by vperaino on 2015-11-06
This doesn't seem like Firefox being so much a "resource hog" (which I'm sure it is regardless) as much is something just being flat out broken. Technically I don't need to use Firefox, so it doesn't matter much anyway, but it's just killing me why this is happening. 

Flash is the only plugin that is active in my Firefox, besides some x264 thing.

---

### Post by Linuxisfast on 2015-11-07
Google Chrome uses less memory here than Firefox and after a while is way more responsive with multiple tabs open compared to FF which starts to hang.

---

### Post by Mike_Walsh on 2015-11-07
> **frank18 said:**
> That's why i use google  Chrome in xubuntu 14.04 on my old P4 and it's  3 times faster then Ffox

^^^ +1! Couldn't agree more. I have an old Dell lappie, running Xubuntu 14.04.3; like you, a P4 ...and 1 GB RAM. I use the CPU graph in the panel. When Firefox is running, it's solid green. With Chromium running, barely a quarter of the activity.

> **Sweet_Baby_Jamie said:**
> If you like Firefox, you might consider the Qupzilla browser or Seamonkey (my favorite!), both Mozilla projects that aren't nearly as resource-hungry as Firefox.

I will, however agree with Jamie. If you like Mozilla, SeaMonkey is far lighter. Or,  as veggie2 says, there's PaleMoon; somewhat derided, but very good, nonetheless. It's a fork of FireFox, for those who prefer the way FF used to look, pre-Australis (round about FF29, if memory serves). The rest of it is very much up-to-date, however; it still uses the Gecko rendering engine, and everything else is on a par with the latest releases of FF. The developers have concentrated on achieving a small footprint....and have succeeded very well. It's light.....and fast.

Or, if you want an even lighter version of Chromium, there's Slimjet.


Regards,

Mike. ;)

---

### Post by vasa1 on 2015-11-07
Firefox running very smoothly for me :)

---

### Post by pqwoerituytrueiwoq on 2015-11-07
on my laptop i noticed a slam of cpu usage with ff i don't get on my desktop
i installed todays updates and the 4.3 kernel (+xorg edgers)
it appears to be acting more normal (have not used it long enough to verify)
before the upgrade i turned hardware acceleration OFF and that seemed to help, so i guess it may be a bug with that feature
*laptop has intel gpu, desktop has nvidia gpu
i turned it back on after the updates and have not seen it spike and hold like it had been

---

### Post by monkeybrain20122 on 2015-11-07
Firefox works very well for me. Have 200 tabs and it is still fast. Can't say same about Chrome. But on my netbook I notice that with Firefox you need to clean the cache and other junks sometimes, it boosts performance immensely (Not sure if you need to do that with Chrome since I rarely use it)

---

### Post by sgage on 2015-11-07
> **vasa1 said:**
> Firefox running very smoothly for me :)

Same here - I just don't see a problem. I will not use Chromium, or any other Google product, if I can help it.

---

### Post by vasa1 on 2015-11-07
> **sgage said:**
> Same here - I just don't see a problem. I will not use Chromium, or any other Google product, if I can help it.
I use Google services a lot but Firefox is still my preferred browser.

---

### Post by bapoumba on 2015-11-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by night_sky2 on 2015-11-08
Seems like one of those Firefox hatefest thread.

The truth is, Chrome eats up more RAM than Firefox the more open tabs you have. Folks should look up the latest benchmarks on the internet. Firefox is running as fast ( if not more when some features are disabled) than Chrome on all my computers. The power fo customization and user control makes this browser* way *more flexible than Chromium and co.

---

### Post by Sweet_Baby_Jamie on 2015-11-08
Oh for goodnessakes, no one *hates* Firefox!  And no matter what the numbers on a graph or a web site say, it's the **user experience** that people base their decisions on, and that is totally subjective and probably different for every user, even if they all have the same hardware and OS.

My parents loved and adored the Netscape Internet Suite on Windows "back in the day."  It was still installed on this computer when they handed it down to me.  Believe it or not Netscape is still alive and well, under a new name:  [COLOR=#008080]**Seamonkey**[/COLOR], yaaaaay!!:KS  Mozilla adopted it and keeps it open-source.  Very Firefoxy and Thunderbirdish it seems to me, but very fast and well integrated.  It even has a built-in IRC client but I admit I've never used that.

But there's no browser-bashing going on here.

---

### Post by speedwell68 on 2015-11-08
> **sgage said:**
> Same here - I just don't see a problem. I will not use Chromium, or any other Google product, if I can help it.

I have no bother with FF and Chrome running side by side, either.  For the record Chromium is an Open Source project and not a Google product.  Google Chrome is a browser based on the Chromium Project.

---

### Post by vasa1 on 2015-11-08
> **speedwell68 said:**
> I have no bother with FF and Chrome running side by side, either.  For the record Chromium is an Open Source project and not a Google product.  Google Chrome is a browser based on the Chromium Project.

Most of the Chromium devs are Google employees. I'd say that Chromium is a Google product.

---

### Post by night_sky2 on 2015-11-08
> **Sweet_Baby_Jamie said:**
> Oh for goodnessakes, no one *hates* Firefox!  And no matter what the numbers on a graph or a web site say, it's the **user experience** that people base their decisions on, and that is totally subjective and probably different for every user, even if they all have the same hardware and OS.
I agree but if we want real data, better to look at some objective tests. Just my 2cents.

---

### Post by night_sky2 on 2015-11-08
> **vasa1 said:**
> Most of the Chromium devs are Google employees. I'd say that Chromium is a Google product.
+1

Chromium is an unfinished product.

 The project is funded by Google Inc., developped mostly by Google engineers and intended to serve as a basis for Google Chrome.

---

### Post by Mike_Walsh on 2015-11-08
> **night_sky2 said:**
> +1

Chromium is an unfinished product.

 The project is funded by Google Inc., developped mostly by Google engineers and intended to serve as a basis for Google Chrome.

I would express that in slightly different terms. It would probably be more correct to say that The Chromium Projects are **on-going**.....and a work in progress.

And are we so petty-minded on this Forum, as to express hatred for one browser or another.....simply based on the ethical code of the group of individuals who developed it, and of those who sponsored it?

Really, people...!! I, for one, have nothing to hide. Google will find extremely lean pickings from my digital 'footprint'. For all important stuff, I use Tor anyway. And I'm considering a VPN.....but this warrants further research, I feel.


Regards,

Mike. ;)

---

### Post by night_sky2 on 2015-11-08
> **Mike_Walsh said:**
> I would express that in slightly different terms. It would probably be more correct to say that The Chromium Projects are **on-going**.....and a work in progress.

The fact is, Chromium is lacking features that are added in Google Chrome or other Chromium-based browsers like Opera. It is especially more apparent on Windows and OSX where there is no auto-updater, codecs (AAC, H.264, and MP3 support) and where one needs to hunt for the latest stable build. So no, I wouldn't think Chromium is intended as a fully-featured, finished product at this stage.

---

### Post by monkeybrain20122 on 2015-11-08
So if you are using Chromium why not just use Chrome? I don't get it why one would use "open source" Chromium and then use a third party hack to get the proprietary pepper flash. The tracking in Chrome can be disabled.

Chromium is a perpetual beta and moreover Ubuntu's offer is not even up to date.

I am not a big user of Chrome (mostly Firefox) but I do fire it up occasionally. I don't get the point of Chromium, it is neither here nor there IMHO.

---

### Post by vasa1 on 2015-11-08
> **Mike_Walsh said:**
> I would express that in slightly different terms. It would probably be more correct to say that The Chromium Projects are **on-going**.....and a work in progress.
...
That's about it.

Here are two detailed links:
[https://www.chromium.org/developers/testing/chromium-build-infrastructure/tour-of-the-chromium-buildbot](https://www.chromium.org/developers/testing/chromium-build-infrastructure/tour-of-the-chromium-buildbot)
[http://build.chromium.org/p/chromium/waterfall](http://build.chromium.org/p/chromium/waterfall)

At some point, a particular build is selected for what will ultimately be turned into Google Chrome.

Also found: [https://ftagada.wordpress.com/2011/01/19/chromium-release-management-explained/](https://ftagada.wordpress.com/2011/01/19/chromium-release-management-explained/)

---

### Post by night_sky2 on 2015-11-09
> **monkeybrain20122 said:**
> So if you are using Chromium why not just use Chrome? I don't get it why one would use "open source" Chromium and then use a third party hack to get the proprietary pepper flash. The tracking in Chrome can be disabled.

Chromium is a perpetual beta and moreover Ubuntu's offer is not even up to date.

I am not a big user of Chrome (mostly Firefox) but I do fire it up occasionally. I don't get the point of Chromium, it is neither here nor there IMHO.
The only point I can see for a lambda user to use Chromium instead is because of a mistrust of Google Chrome's proprietary code. The closed bit that we don't know about.

That being said, if I am a big fan of Chromium but don't trust Google, I would probably go the Opera (or Vivaldi in Beta) route.

---

