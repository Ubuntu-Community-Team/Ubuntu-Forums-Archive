---
title: "How to upgrade Wine"
date: 2008-12-05
forum: Wine
---

### Post by Totenglocke on 2008-12-05
How do I upgrade Wine to a newer version?  It's up to 1.1.10 according to Wine's site, yet 1.0.something is the only one available through synaptic package manager.

---

### Post by hikaricore on 2008-12-05
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

The instuctions are right there if you follow the download link.
Please try and look a little further in the future before posting. :)

---

### Post by Totenglocke on 2008-12-05
I mixed up my windows and thought I was looking at WINE when I was looking at a side project of Wine and on that one the last link I found was to an outdated hardy repository.  Sorry.

---

### Post by Sparkypine on 2008-12-23
*Sorry, that document was not found. Please check your URL and try again.*

Please try to verify your links in the future, some of us rely on people asking these seemingly obvious questions. :)

---

### Post by IanW on 2008-12-24
The Ubuntu debs provided on Wine's website & repository are compiled & uploaded by ONE guy.
Follow the instructions [here](http://www.winehq.org/download/deb) to add Wine's repository to your system.

Wine is actually now up to 1.1.11, but 2nd Turkey day is upon us, so cut him a little slack, OK?

---

### Post by cogadh on 2008-12-24
> **Sparkypine said:**
> *Sorry, that document was not found. Please check your URL and try again.*

Please try to verify your links in the future, some of us rely on people asking these seemingly obvious questions. :)
WineHQ recently changed the website, invalidating that link. Two weeks ago (when it was originally posted), the link worked fine. The new link is this:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by redsoxreed on 2008-12-24
If you want the latest version, you could always build from source...

---

### Post by cogadh on 2008-12-25
> **redsoxreed said:**
> If you want the latest version, you could always build from source...
But why bother when there are pre-built packages already available? Unless you need to build from source in order to incorporate an uncommitted patch (or some other customization) or you want to try it for the challenge, there is really no reason to build Wine from source.

---

### Post by redsoxreed on 2008-12-25
> **cogadh said:**
> But why bother when there are pre-built packages already available? Unless you need to build from source in order to incorporate an uncommitted patch (or some other customization) or you want to try it for the challenge, there is really no reason to build Wine from source.

Because you have to wait a few days after the release for the packages to be built.  You can get it much sooner by building from source.

---

### Post by cogadh on 2008-12-25
If you honestly lack the patience to wait a few days for your Wine package to be upgraded (automatically, I might add), then I suppose building from source is the way to go. But seriously, is there really any need to be that impatient? With the exception of Wine releases that have occurred during holidays or during a new Ubuntu release, I don't think it has ever taken YokoZar much more than 36 hours (if that) to produce a new package. Besides, its not like each new Wine release is a revolutionary advance over the previous one. In fact, each new release is very likely to break things that you previously had working in Wine, so waiting up to a few days for the early adopters to find some of the major bugs before you get the updated package is actually a good thing.

---

### Post by redsoxreed on 2008-12-25
I guess I'm an early adopter then. :)

---

### Post by OrbJinzo on 2008-12-25
> **cogadh said:**
> If you honestly lack the patience to wait a few days for your Wine package to be upgraded (automatically, I might add), then I suppose building from source is the way to go. But seriously, is there really any need to be that impatient? With the exception of Wine releases that have occurred during holidays or during a new Ubuntu release, I don't think it has ever taken YokoZar much more than 36 hours (if that) to produce a new package. Besides, its not like each new Wine release is a revolutionary advance over the previous one. In fact, each new release is very likely to break things that you previously had working in Wine, so waiting up to a few days for the early adopters to find some of the major bugs before you get the updated package is actually a good thing.

Quite the buzzkill arent ya? And its been almost 6days since the release. I just compiled from source and it wasnt bad.

---

### Post by poisonkiller on 2008-12-26
Well... it seems that the .deb package is ready for download (probably has been since 21st December). Navigate **[here]("http://ppa.launchpad.net/ubuntu-wine/ubuntu/pool/main/w/wine/")**, scroll to the bottom and download wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb. Then you just have to install it.

---

### Post by OrbJinzo on 2008-12-27
guess there too lazy to update the servers. :P

---

