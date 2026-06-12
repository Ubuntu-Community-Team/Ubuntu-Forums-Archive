---
title: "Using Waves GTR in Ubuntu Studio 7.10"
date: 2008-05-29
forum: Ubuntu Studio
---

### Post by GuitarOfGold on 2008-05-29
Hi, I'm pretty new to the Linux world, so I don't know a lot of what I'm doing.  What I'm attempting to do is using Waves GTR in Ubuntu Studio 7.10 with as low latency as possible, since I want to use it live, and Windows latency can't go low enough for me not to notice it, though I can get it low enough to keep time with myself.  I'm real thrilled with having to play "in advance" though.  The Waves GTR plugin doesn't add enough latency to be noticeable.  In Windows, I tried running through Sonar 6 PE, Reaper, and a stand-alone app I really like called Plogue Bidule.  Latency was about the same in everything except Bidule, which could override the audio driver.  Close, but not quite.

I'm running my guitar through a Presonus Firepod.  I got that up and running in Ubuntu without X-runs and very low, unnoticeable latency.  My problem now is apparently classic:  How can I get Waves GTR (a dreaded VST) to work in Ubuntu?  Is there a simple host floating around out there that would do this?  I'd really like to use Plogue Bidule (or something similar) because of it's routing abilities, but it's not available for Linux.

I also realize the whole licensing issue with Steinburg would force me to compile something on my own.  I've tried to do this with Ardour, but I get errors, one of which I can't find any information on anywhere.  Most are in the form of "missing blah blah blah" or "can't find yadda yadda."  I don't know anything about this, I just follow tutorials.  Maybe one day, I'll be Linux savvy, but for now, any options & help would be greatly appreciated.

How would latency be running Plogue Bidule under Wine?

---

### Post by Stochastic on 2008-05-30
Well first let me say welcome, it's always nice to see people familiar with audio make the shift to linux - with greater numbers, one day these technical issue you speak of will disappear.

The compilation errors you're getting are most commonly due to not having dev libraries installed.  If I get a message like "can't find SomeThingX" then the first thing I do is open a terminal and do ```
apt-cache search somethingx
``` (this searches your software repositories for somethingx) sometimes the exact match needs to be inferred, other times you need to be a bit trickier and do ```
apt-cache search some | grep x
``` (this searches for the word some, then only shows the results that also contain x).  After that, you'll need to do ```
sudo apt-get install libsomethingx-dev
``` to actually install the package.

As for GTR and VSTs, I've got good news and bad news (then some more good).  The good news is that VSTs can run in linux, but it takes some setup.  There are three main methods [FST]("http://www.joebutton.co.uk/fst/"), [DSSI-VST]("http://dssi.sourceforge.net/"), and [Audacity VST-Enabler]("http://audacityteam.org/vst/").  Be warned that it does take a bit of compiling from source to get this stuff installed.

The bad news is that in the [unofficial linux vst-database]("http://ladspavst.linuxaudio.org/") I can't find any listing for Waves or GTR.  This doesn't mean it won't run, but it does mean it's a shot in the dark.  If you are able to get a vst host up, please file a report, on that site, as to your success/failure with GTR.

The other good news is that Linux has free amp modeling plugins of their own for you to use if GTR won't install.  They're the CAPS amp modelling plugins from the LADSPA set.  To get them just do ```
sudo apt-get install ubuntustudio-audio-plugins jack-rack
``` Then fire up jack-rack (you'll need jack running first) to use them as real-time effects.

As for plogue bidule, I've asked the developers if they will ever port to linux and their polite response was that there were no plans to as of yet.  I don't know if it will run in wine, as the [Wine AppDB]("http://appdb.winehq.org/") doesn't have a listing.  So once again it's a shot in the dark.

However, [Pure Data]("http://puredata.info/") is an open-source modular app that's very similar to bidule.  It is a bit more low-level than Bidule, but that just means more flexibility, right? (okay, maybe it's got a bit steeper learning curve)

Lastly, you mentioned Reaper; and though you hadn't asked if it would run in Linux, many people do run Reaper in Wine.  From what I hear, it's quite stable and reliable.  Thought you'd like to know.

---

### Post by GuitarOfGold on 2008-05-31
OK, I decided to go the Reaper route and install it on Wine.  Problem is now that I can't install wine.  I follow the included instructions, but I get an error that says the compiler couldn't create an executable.

Also, I'm (most of the time) stuck on a 56k connection.  So far, I haven't been able to figure out how to get it to work in Ubuntu.  I have all the parameters set, I just don't know how to actually dial it.  That makes getting things online kinda difficult while I'm in Ubuntu.

---

### Post by Stochastic on 2008-06-01
All you need to do to get wine is make sure you have the universe repository enabled (in System->Administration->Software Sources), and do ```
sudo apt-get install wine
``` no need to install from source.

As for getting things off the internet, I really don't know the first thing about getting a dial-up to work in Ubuntu.  I'd post in the Networking & Wireless section of these forums to figure that one out.

Dependence on the internet is a fairly major crutch for Ubuntu installations, there's just simply too much software in the repositories for it all to fit onto one CD or DVD install.  Back when I was using Debian they had a 6 CD install disc set so that the end user would have a ton of software available to them without needing the net to install.

If you can't get the internet up and running on your box, but are able to transfer files from a different box that's hucked ta tha interweb, it's possible to grab packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (usually right at the bottom of the page).  The downside to this is that all the packages marked with a red circle are mandatory requirements to have installed before the main package you want will install.  This can get quite laborious for major packages.  Take a look at all the packages wine requires for instance: [http://packages.ubuntu.com/gutsy/wine](http://packages.ubuntu.com/gutsy/wine)  In the end, you're better off to go through the learning curve of getting your modem to work for ya, and using the awesome powers of **APT** (this apt has super-cow powers)!

---

### Post by GuitarOfGold on 2008-06-02
OK, I pretty much gave up on my modem (after trying a variety of tutorials).  Instead, I took my laptop somewhere where there was a wireless connection and installed Wine.  I then just ran my already-installed Reaper from my Windows drive instead of reinstalling it.  (That way I don't have to re-find all my plugins.)  It works (well, technically), but I now realize I need to install ASIOwine to get some audio to my Firepod.  Unfortunately, none of the how-to's seem to work for me.  (Story of my life.)

I know Waves makes an outside-the-box version for Windows to dodge the whole latency issue, but I'd rather use Linux, if for nothing else than the coolness factor. :D

---

