---
title: "Why webkit and why not gecko ?"
date: 2009-11-03
forum: The Cafe
---

### Post by praveesh on 2009-11-03
Many new browsers like midori,chrome,arora etc are using the open source product of apple and not that of mozilla .now the epiphani has switched to webkit and konqueror is going to switch with the next version of Kde (4.4)  . Why ? What's advantage of webkit over gecko

---

### Post by LookTJ on 2009-11-03
Standards-compliant?

EDIT: I think this is the primary reason, though not sure.

---

### Post by MaxIBoy on 2009-11-03
It's more standards-compliant and it runs faster.

The main thing Gecko has going for it, as far as I can tell, is that Firefox uses it. If Firefox used Webkit, it would be a better browser than it is today. But even without Webkit, Firefox is the best browser in all of existance (in my opinion.) Elinks2 is the second-best.

---

### Post by hoppipolla on 2009-11-03
I agree (about the reasons for webkit's popularity) ! Incidentally though, Im sure I heard that Gecko was somehow tied into the whole workings or UI of Firefox, is this true? Or am I thinking of something else? Sorry, slightly off-topic I know but it does have some impact :)

---

### Post by sertse on 2009-11-03
Also I've heard gecko code while FLOSS is developed in such a way it's yucky to separate it from the Firefox browser. Webkit is much cleaner. Thus easier to browser dev to "just" concentrate on making their browser and then telling to to use the webkit engine.

---

### Post by mivo on 2009-11-03
Webkit browsers render noticeably faster than Gecko-based browsers. No exception, in my experience. I'm currently quite impressed with [Midori]("http://www.twotoasts.de/index.php?/pages/midori_summary.html"). Nice little browser.

---

### Post by praveesh on 2009-11-03
There's a package named wine-gecko and it's the gecko engine for wine . I don't know how they seperate it from firefox

---

### Post by hoppipolla on 2009-11-03
> **sertse said:**
> Also I've heard gecko code while FLOSS is developed in such a way it's yucky to separate it from the Firefox browser. Webkit is much cleaner. Thus easier to browser dev to "just" concentrate on making their browser and then telling to to use the webkit engine.

Yeah thats what I heard too! Im not a coder though so Im not sure.

---

### Post by praveesh on 2009-11-03
Ok the rendering speed makes the difference .

---

### Post by ad_267 on 2009-11-03
Webkit is originally based on khtml. Being a KDE person you should be happy about using Webkit!

---

### Post by MorphingDragon on 2009-11-03
> **praveesh said:**
> There's a package named wine-gecko and it's the gecko engine for wine . I don't know how they seperate it from firefox

With great difficulty. But its needed for some programs to run.

---

### Post by Xbehave on 2009-11-03
[LIST]
[*]It's faster, lighter and easier to plug in to a browser (in part due to it's kpart legacy). 
[*]It's not as good as coping with the web, SVGs are hit/miss.
[*]Plug-ins (such as flash) don't work that well (or at least when chrome was first released that was true)
[*]It is not much more standards compliant. They have a few hacks in there to pass acid3, but generally it's not significantly better with [test-suites]("http://www.w3.org/Style/CSS/Test/CSS2.1/current/html4/by-section.htm")
[/LIST]

There is a lot of anti-gecko FUD, the only one that really sticks is it being slower at rendering.


> The main thing Gecko has going for it, as far as I can tell, is that Firefox uses it.
Well that and Firefox, Netscape, SeaMonkey, Flock, Songbird, Beonex, Lunascape, K-Meleon, Camino, Galeon, Kazehakase, Skipstone&#8224;, Sugar, Picasa (for Linux), wine
> If Firefox used Webkit, it would be a better browser than it is today.
Really? if it dropped its support for most extensions, it would be better? Other than the fact the competition between gecko & webkit is pushing both forwards, there is a lot of support for extensions and real-world webpages (e.g ie6 'only' pages) in gecko that isn't available in webkit yet.

---

### Post by joey-elijah on 2009-11-03
Whether or not gecko is worse than webkit etc Webkit is the future for now. 

Gecko is a dinosaur in comparison.

---

### Post by Xbehave on 2009-11-03
> **joey-elijah said:**
> Whether or not gecko is worse than webkit etc Webkit is the future for now. 

Gecko is a dinosaur in comparison.
Really? last time i checked gecko still had ~4 times as many users, hardly a dinosaur. Just because webkit is the new young whipper-snapper doesn't mean gecko is dying any time soon.

---

### Post by hoppipolla on 2009-11-03
> **Xbehave said:**
> Really? last time i checked gecko still had ~4 times as many users, hardly a dinosaur. Just because webkit is the new young whipper-snapper doesn't mean gecko is dying any time soon.
To be fair though I dont see any modern browsers adopting Gecko at the moment. Its all about Webkit in terms of the way things are moving. Gecko will need to improve for this trend to change IMO.

---

### Post by cocopuffz on 2009-11-03
How can you guys tell that Webkit renders soooo much faster? Aren't the differences measured in milliseconds? I've got Chrome and Firefox 3.5 running in Ubuntu and it's barely noticeable to me. In fact, after the latest update my FF3.5 loads up faster than Chrome. I like both but I enjoy the extensions in FF. 

With modern PC's and all that computing & GPU power I seriously don't "feel" any real world difference. Both browsers just pop up instantly and draw my websites blazingly fast.

---

### Post by madnessjack on 2009-11-03
From the looks of things (and I'm no expert), Gecko is better for extending and use as a tool, and Webkit is cleaner and lightweight. That would be fair enough.

---

### Post by samjh on 2009-11-03
Webkit is generally less demanding on resources than Gecko.

Gecko is a very capable HTML renderer.  But it is not just a HTML renderer, but a GUI engine for XUL, which is the GUI toolkit used by Firefox (and Thunderbird).  The consequence is that Gecko is bigger than Webkit.

I really don't think there are any more advantages for Webkit over Gecko other than its size and potential resource requirements.  One non-technical advantage of Webkit is that it has been ported to many different platforms, and is licensed under LGPL and BSD.

---

### Post by mivo on 2009-11-03
> **hoppipolla said:**
> To be fair though I dont see any modern browsers adopting Gecko at the moment.

Looking at the Windows platform, there is really only Chrome that has the chance to get a decent size of the browser market share. Firefox enjoys an excellent reputation (not so much in the Linux community) and I don't see its popularity changing in quite a while. People tend to be unwilling to change a browser they've used for years unless there are pressing reasons). Though, no doubt, Chrome will take off well, simply because it's a Google product (it blazingly fast, too).

---

### Post by Xbehave on 2009-11-03
> **samjh said:**
> One non-technical advantage of Webkit is that it has been ported to many different platforms, and is licensed under LGPL and BSD.
Gecko is available under LGPL or GPL or MPL (you have to release source code for any changes made to the original source files)
webkit is split between LGPL (WebCore) and BSD (for the rest)

So with webkit you have to release changes to webcore, but the rest is just BSD (no need to release code), but with gecko you have to at least use MPL (release changes to original files).

---

### Post by Skripka on 2009-11-03
> **samjh said:**
> Webkit is generally less demanding on resources than Gecko.

Gecko is a very capable HTML renderer.  But it is not just a HTML renderer, but a GUI engine for XUL, which is the GUI toolkit used by Firefox (and Thunderbird).  The consequence is that Gecko is bigger than Webkit.


This.

Firefox is slow and bloated because to do all the things it does, it has a huge complicated code base.  And on a level playing field, small and elegant (Webkit) will stomp on huge and complicated (Gecko) every time in terms of performance.  Gecko IS a dinosaur, and every year or so people stop and ask "WTF aren't we using webkit?  It is 5X faster."

...  I'm reminded of an English idiom about lemmings, regarding user statistics.

As far as why Gecko isn't used in other 3rd party browsers?  What would be the point?  The GUI and the browser are all rendered and integrated together by the same backend.  The only project to ever attempt such as QtFirefox, which last I heard wasn't going anywhere quickly.

Acid3 really isn't that useful for studying and benchmarking web compliance.  All it tests is the browsers ability to handle gawd-awful-coded code.

---

### Post by Xbehave on 2009-11-03
> **Skripka said:**
> As far as why Gecko isn't used in other 3rd party browsers?
What about the fact that IT IS, did you even read my previous post, gecko is used in lots of 3rd party browsers and non-browsers.

Q.What would be the point?
A.The GUI and the browser are all rendered and integrated together by the same backend.

> The only project to ever attempt such as QtFirefox, which last I heard wasn't going anywhere quickly.Have you considerd getting a clue before posting FUD, QtFirefox was a port of xulrunner from GTK to QT, nothing to do with making a new browser, just getting it to run using QT instead of GTK.

> will stomp on huge and complicated (Gecko) every time in terms of performance.
Define stomp. Webkit is faster but as others have pointed out the difference between gecko and webkit is measure in milliseconds not minutes.

> To be fair though I dont see any modern browsers adopting Gecko at the moment. Its all about Webkit in terms of the way things are moving.
Webkit has a lot more activity on the desktop (possibly because there are already plenty of gecko based browsers) but on mobile devices both [meamo]("http://en.wikipedia.org/wiki/MicroB") and [moblin]("http://en.wikipedia.org/wiki/Moblin") use gecko, while android and iphoneOS use webkit

> But it is not just a HTML renderer, but a GUI engine for XUL, ... The consequence is that Gecko is bigger than Webkit.
While that is partially true, gecko can be compiled without XUL support (meamo does this) to reduce its memory footprint, so if you make a browser that only wants gecko to render html you can compile gecko to do that.

---

### Post by hoppipolla on 2009-11-03
> **Xbehave said:**
> Define stomp. Webkit is faster but as others have pointed out the difference between gecko and webkit is measure in milliseconds not minutes.

I'd be worried if it was minutes though! lol :)

> **Xbehave said:**
> Webkit has a lot more activity on the desktop (possibly because there are already plenty of gecko based browsers) but on mobile devices both [meamo]("http://en.wikipedia.org/wiki/MicroB") and [moblin]("http://en.wikipedia.org/wiki/Moblin") use gecko, while android and iphoneOS use webkit

You mean the two biggest mainstream smartphone OSs in the world?  o.O

---

### Post by Xbehave on 2009-11-03
> **hoppipolla said:**
> You mean the two biggest mainstream smartphone OSs in the world?  o.O
No, 3rd and 5th? maybe, but IMO meamo and moblin are much better even if less popular, that said my point was just that people are still using firefox outside of mozilla.

---

### Post by Mr. Picklesworth on 2009-11-03
As well as the speed thing (which shouldn't be hugely relevant with Firefox 3.6...), Webkit has a smoother API for application developers. Developing with Gecko, from what I have seen, pulls in a crazy heap of dependencies. The library immediately assumes that you are building a web browser and makes things way more complex than they need to be.

A nice example of this insane swamp of dependencies can be found in the old Gecko version of GNOME's Epiphany browser. (Alas, I don't have screenshots, so you'll have to take my word here).
Epiphany has its own download dialog, but every now and then a particular Javascript would trigger the Firefox download dialog to open. Typing a particular URL into the address bar would open up Firefox's entire XUL user interface inside Epiphany.

Now, that's nifty and all, but these things weren't meant to happen and it is *insane* that it would be possible out of the box. Things like that should be opt-in, not opt-out. That is what makes Webkit so nice.

There are some neat apps built with XULRunner, like Pencil, but for casually embedding a web renderer I have never seen Gecko do well.

---

### Post by Mi*6d@# on 2009-11-03
**WebKit**
Pros:
Fast, small, tight and clean codebase.
Easier for developers.
Cons:
Small and clean ~ not as rich.

**Gecko:**
Pros:
Rich codebase, expandable.
Cons:
Dinosaur in comparison to WebKit.
Tied to Firefox.

My choice: **WebKit** (Chromium AMD64 from Launchpad PPA)

---

### Post by Xbehave on 2009-11-03
> **SkyBon said:**
> **WebKit**
Pros:
Fast, small, tight and clean codebase.
Easier for developers.
[B]Cons:
Small and clean ~ not as rich.
[/B]
**Gecko:**
Pros:
Rich codebase, expandable.
Cons:
**Dinosaur in comparison to WebKit.**
**Tied to Firefox.**

My choice: **WebKit** (Chromium AMD64 from Launchpad PPA)
Gecko isn't tied to firefox, microB, miro and many other apps use gecko both with and without XUL.
Gecko also has better support for SVGs and plugins
webkit being lighter and a few ms faster, hardly makes firefox a dinosaur LOL

---

### Post by edin9 on 2009-11-03
> **praveesh said:**
> ......and konqueror is going to switch with the next version of Kde (4.4).....

Source?

---

### Post by praveesh on 2009-11-03
Webkit has a qt port and arora and  midori are qt browsers.

---

### Post by sertse on 2009-11-03
> **Xbehave said:**
> Gecko isn't tied to firefox, microB, miro and many other apps use gecko both with and without XUL.

It's technically true, not practically true. It's easier doing that with Webkit.

Thats perhaps why new browsers since Webkit came out, have been using webkit, or switch to it.

---

