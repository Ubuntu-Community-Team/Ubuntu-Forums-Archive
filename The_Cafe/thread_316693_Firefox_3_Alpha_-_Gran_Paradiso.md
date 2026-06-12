---
title: "Firefox 3 Alpha - Gran Paradiso"
date: 2006-12-11
forum: The Cafe
---

### Post by _simon_ on 2006-12-11
Firefox 3 Alpha 1, codenamed Gran Paradiso is available to download.

[Download](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/granparadiso/alpha1/linux-i686/en-US/granparadiso-alpha1.tar.bz2)

[Release Notes](http://www.mozilla.org/projects/firefox/3.0a1/releasenotes/)

> 
**Changes in this Development Milestone**

Gecko 1.9 Alpha 1 introduces several new features which can be tested by using Gran Paradiso Alpha 1:

    * Cairo is now being used as the default graphics library, affecting all graphic and text rendering
    * Cocoa Widgets are now used in OS X builds
    * An updated threading model
    * Changes to how DOM events are dispatched (see bug 234455)
    * Changes to how <object> elements are loaded (see bug 1156)
    * Changes to how web pages are painted
    * New SVG elements and filters, and improved SVG specification compliance

Some of the changes in Gecko 1.9 Alpha 1 will affect the web and platform compatibility of Gran Paradiso Alpha 1:

    * Windows 95, Windows 98 and Windows ME are no longer supported platforms
    * OS X 10.2 is no longer supported, and OS X 10.3.9 or higher is recommended
    * Moving DOM nodes between documents now requires a call to importNode or adoptNode as per the DOM specification.


> 
**Known Issues**

This list covers some of the known problems with Gran Paradiso Alpha 1. Please read this before reporting any new bugs, and watch for updates as new bugs are discovered.

**All Systems**

    * The Cairo graphics system has drastically changed the way all text and images are rendered from previous versions of Gecko, so occasional misrenderings of non-latin scripts and fonts may occur.
    * The Phishing Protection notification bubble is hidden by the content area (see bug 341950.)
    * Gecko now sends WHATWG DOM events when going online or offline (see bug 336359.)
    * There have been many bugs fixed by changes to the behavior of nsCaret.

**Linux and Unix systems**

    * Loading any page with Chinese, Japanese or Korean text can hang the browser (see bug 357637).
    * Performance on complex script (ex: Indic) may be slower than previous versions of Gecko.
    * Compatibility issues have been reported when users are not running Xorg 7.0 or better.
    * Users may experience problems when attempting to print complex pages.


---

### Post by DigitalDuality on 2006-12-11
d

---

### Post by _simon_ on 2006-12-11
I have to say, having used it for a few hours that it seems quicker than 2.0.

Addon wise, I only use Adblock plus and Filterset.G and both are compatible.

---

### Post by esaym on 2006-12-11
I have been running the old alpha on my windows box for a few months now.  No difference from 2.0 that I could see.  However this seems to be a newer alpha.

---

### Post by lwr on 2006-12-11
How's the standards compliance? That's the only thing that really annoys me at the moment (more from a web-developers point of view; I've already got IE6 and 7 to contend with, without having to deal with Firefox quirks). Does it pass the [Acid2 test]("http://www.webstandards.org/action/acid2/")?

---

### Post by engla on 2006-12-11
Firefox 1, 1.5 and 2.0 were all built off the same branch of Gecko, the engine. _Finally_ are we moving towards new web technology! I have high hopes for FFX 3 and Gecko 1.9

---

### Post by Ben Sprinkle on 2006-12-11
This looks promising thanks for the link, I will try it out later. :)

---

### Post by _simon_ on 2006-12-11
> **lwr said:**
> How's the standards compliance? That's the only thing that really annoys me at the moment (more from a web-developers point of view; I've already got IE6 and 7 to contend with, without having to deal with Firefox quirks). Does it pass the [Acid2 test]("http://www.webstandards.org/action/acid2/")?

Unfortunately no, it did not pass for me but remember it's still in alpha.

---

### Post by lwr on 2006-12-11
> **_simon_ said:**
> Unfortunately no, it did not pass for me but remember it's still in alpha.

That's a shame, but I'll keep my hopes up. As I understand it, standards compliance is quite high on the to-do list. 
When do you think, realistically, it will be out? The [Mozilla site]("http://wiki.mozilla.org/Firefox3/Schedule") says May 2007, so by their standards I'm guessing August? I suppose it should in Feisty+1.

---

### Post by engla on 2006-12-11
According to Mozilla, the acid2 bug is fixed:
[https://bugzilla.mozilla.org/show_bug.cgi?id=289480](https://bugzilla.mozilla.org/show_bug.cgi?id=289480)

Now, there doesn't seem to be a "perfect" shot of gecko rendering the acid2 test as intended and it doesn't seem like that is their priority.

It is clear though that a lot of rendering bugs are fixed in gecko 1.9, and that the acid2 test is rendered much better.

(Edit: Impressive. Just half a week ago, this bug landed: [https://bugzilla.mozilla.org/show_bug.cgi?id=300030](https://bugzilla.mozilla.org/show_bug.cgi?id=300030) It's the landing of a whole reflow branch, modifying 201 files. And look at the dependiencies on that bug .. :-))

---

### Post by mustang on 2006-12-11
Very cool thanks for the link.

The browser does appear to be noticeably faster.

---

### Post by engla on 2006-12-11
Does anyone have any news on memory and the general resource use of this version and the whole 3.0 yet? I'd love to see mozilla focusing on slimming firefox to be more effective -- we've seen that this is very possible for old applications (gnome and others have slimmed a lot).

---

### Post by ButteBlues on 2006-12-11
Has the general UI changed at all?

---

### Post by maniacmusician on 2006-12-11
> **a simple façade said:**
> Has the general UI changed at all?
right now, not really. but there will probably be more changes later on, I hope.

---

### Post by maniacmusician on 2006-12-11
> **engla said:**
> Does anyone have any news on memory and the general resource use of this version and the whole 3.0 yet? I'd love to see mozilla focusing on slimming firefox to be more effective -- we've seen that this is very possible for old applications (gnome and others have slimmed a lot).
I don't know about future plans, but this alpha release specifically is worse in that department for me. with just 5 tabs open (as opposed to the usual 7 or 8 for me), it has the same amount of memory consumption and actually MORE CPU consumption. I'm actually getting a lagging mouse once in a while (on my 3.6 GhZ, 1.5GB ram PC) which is not fun. in top, cpu consumption stays around 10-20%. sometimes goes up to 50-ish (and thats without any plugins or extensions at all)

---

### Post by Rhapsody on 2006-12-12
I'm trying Gran Paradiso 3.0a1 right now, and it actually seems better than Firefox 2.0 is. 6 out of my 11 extensions work right now, the lower scroll-up button KDE places there isn't just decoration any more, and the infuriating problem I had with two menus popping up for each right-mouse click seems to no longer be present.

I might actually dump Firefox 2.0 and start using Gran Paradiso alphas instead now. That's how bad Firefox 2.0 has been for me.

---

### Post by _simon_ on 2006-12-12
> **engla said:**
> Does anyone have any news on memory and the general resource use of this version and the whole 3.0 yet? I'd love to see mozilla focusing on slimming firefox to be more effective -- we've seen that this is very possible for old applications (gnome and others have slimmed a lot).

I currently have 4 tabs open and 4 extensions installed.


Firefox-bin is using 61.9Mb and between 0 and 2 % CPU.

I've not experienced any lagging like maniacmusician has.

I'm running Athlon 3200+ with 1Gig

---

### Post by maniacmusician on 2006-12-12
> **_simon_ said:**
> I currently have 4 tabs open and 4 extensions installed.


Firefox-bin is using 61.9Mb and between 0 and 2 % CPU.

I've not experienced any lagging like maniacmusician has.

I'm running Athlon 3200+ with 1Gig
Odd...I have an intel celeron 3.6 GHz with 1.5 GBs...

---

### Post by _simon_ on 2006-12-12
Has anyone found a British-English dictionary for this version?

The one that says it's compatible on the website says it isn't when I try and install it.

Edit: Found one on another mozilla page that worked.

This page: [https://addons.mozilla.org/firefox/dictionaries/](https://addons.mozilla.org/firefox/dictionaries/)

---

### Post by BWF89 on 2006-12-12
No support for Windows 95, 98, ME, and MacOSX 10.2. Damn, seems like Firefox 3 is going to be more of a downgrade than anything. What about all the people that aren't using new operating systems?

---

### Post by Hobbes on 2006-12-16
Guess they are stuck with only firefox 2.0....

---

### Post by chickengirl on 2006-12-16
> **BWF89 said:**
> No support for Windows 95, 98, ME, and MacOSX 10.2. Damn, seems like Firefox 3 is going to be more of a downgrade than anything. What about all the people that aren't using new operating systems?

I don't know about MacOS, but users of Win ME and below are a tiny, tiny minority, and MS doesn't even support 95 and 98 anymore, so it's in their best interest to upgrade (to Linux if not XP/Vista ;) )

---

### Post by madmetal on 2007-06-08
firefox 3.0a5 is available...
just a screenshot with gran paradiso at feisty fawn

[[IMG]http://img167.imageshack.us/img167/3237/screenshotjs0.th.png[/IMG]](http://img167.imageshack.us/my.php?image=screenshotjs0.png)

---

### Post by Quillz on 2007-06-08
> **madmetal said:**
> firefox 3.0a5 is available...
just a screenshot with gran paradiso at feisty fawn

[[IMG]http://img167.imageshack.us/img167/3237/screenshotjs0.th.png[/IMG]](http://img167.imageshack.us/my.php?image=screenshotjs0.png)
I want to try this out. How can I get Gran Paradiso installed w/o it messing with my current Firefox 2 profile?

---

### Post by madmetal on 2007-06-09
> **Quillz said:**
> I want to try this out. How can I get Gran Paradiso installed w/o it messing with my current Firefox 2 profile?

i download it , extracted it and then run ./firefox in firefox folder..
my normal firefox wasn't mess... if you close gran paradiso and go to applications >> internet >> firefox it opens firefox 2 ;) 


ps. when gran paradiso opens it asks if you want to make it your preffered browser , choose no ;)

---

### Post by Kosimo on 2007-06-09
> **madmetal said:**
> firefox 3.0a5 is available...
just a screenshot with gran paradiso at feisty fawn

[[IMG]http://img167.imageshack.us/img167/3237/screenshotjs0.th.png[/IMG]](http://img167.imageshack.us/my.php?image=screenshotjs0.png)

How did you make it running? After extract it i can't run the executable... (feisty)

---

### Post by madmetal on 2007-06-10
as shown on site's instructions..
```

Linux/GTK2

Extract the granparadiso-alpha5.tar.bz2 tarball and run ./firefox:

tar -jxvf granparadiso-alpha5.tar.bz2
cd firefox
./firefox
```

you cant have firefox2 and firefox3 working together..
so close firefox and then go to gran paradiso's folder and give ./firefox

---

