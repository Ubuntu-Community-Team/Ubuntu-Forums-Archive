---
title: "My 10 Tab Browser Stress Test"
date: 2007-11-14
forum: The Cafe
---

### Post by Onyros on 2007-11-14
I love browsers. If there's one piece of software I really like to test, that's it: browsers.

I was tampering around with one of my favourite browsers - *Kazehakase* - and thought it would be nice to have something like Opera's Speed Dial as a start page.

I created a simple HTML page, mimicking the original stuff, 9 links and all (with opacity for a nice effect and a black background, which I always prefer) and started it up in my adapted Kazehakase_clean script (thanks, K.Mandla! - I also adapted that to Epiphany).

[ATTACH]50173[/ATTACH]

Now, there's one thing about browsers nowadays: I can't live without tabs. I tend to avoid having more than 10 open at a time, because I like to focus. But I can no longer imagine my internet browsing without tabs.

Out of curiosity, I opened the 9 tabs on my improvised Speed Dial HTML page, which left Kazehakase with 10 tabs open. The pages vary in terms of complexity: some are PHP+MySQL pages with no Flash, some have lotsa Flash ([www.nba.com](www.nba.com) - I love that game), etc. Diverse enough to constitute a "sample".

I was pleasantly surprised with memory usage (Resident Memory, that is). I was curious enough to test the same thing with all tab-enabled browsers I have installed.

The lineup:

--> **Opera** 9.24
--> **Kazehakase** 0.4.9
--> **Dillo** 0.8.6
--> **Epiphany** 2.20.1
--> **HV3** (daily build)
--> **Firefox** 2.0.0.7

All GUI browsers, which have native or compiled tab support (in Dillo's case, it's a patch).

Much to my surprise, the so-called lightweight browsers performed the worst. Not only in terms of speed, but also of memory usage. Now, this is, for me, what's closer to the real usage of a browser. If I'm going to use Dillo, I'm going to use it with tabs; and then, I'm going to use it with more or less than 10 tabs open at a time. Looking at the results, that takes away Dillo's lightness of being... in a heartbeat :P

Opera, as much as it's controversial especially among the FOSS crowd, had the best results throughout the test. It opened the 10 tabs faster, and with less memory usage. Taking into account reports regarding *Kestrel* (Opera 9.50 branch now in beta), it should only get better.

And now, for the results, measured in terms of memory usage, on GNOME's System Monitor (confirmed with htop, too), from worst to best:

--> ***HV3** *= **254.1 MB** (!!)
--> ***Dillo*** = **99.1 MB**
--> ***Kazehakase*** = **73.4 MB**
--> ***Firefox*** = **72.0 MB**
--> ***Epiphany*** = **71.8 MB**
--> ***Opera*** = **65.3 MB**

HV3 is still beta, but if having a few tabs open is going to ramp up memory usage like that... wouldn't it be better to drop them, altogether? Regarding Dillo, I still love it, and will keep on using it. Tabs weren't suppose to happen there, so it's not surprising.

The difference between Gecko browsers are negligible, so I'll keep using what serves me best and what seems faster to me - Kazehakase.

As for Opera... It's already the browser I use the most, this just confirmed what I had expected. Its closed-source, but it's one heckuva browser.

Take it for what it's worth! Too bad there still isn't a good, stable WebKit browser to do the same test, I'd be more than interested in those results!

*Tested on a Thinkpad X31, 768MB RAM - on GNOME, Ubuntu Gutsy Gibbon 7.10. No widgets and no extensions installed on any browser whatsoever.*

---

### Post by Bungo Pony on 2007-11-14
There's so many reasons to love Opera, and this is just another one :)

---

### Post by happysmileman on 2007-11-14
> **Onyros said:**
> 
Take it for what it's worth! Too bad there still isn't a good, stable WebKit browser to do the same test, I'd be more than interested in those results!


Konqueror uses KHTML, which is what Webkit was based on, so you can expect similar results (though not the exact same results since code has changed a good bit AFAIK), however you'd need KDELibs and stuff, so if you're using GNOME the memory usage might be more than it should be.

Webkit should be in QT soon (maybe it already is) so you could expect to see some.

---

### Post by SomeGuyDude on 2007-11-14
I like Opera and all, but unless you only have 512MB of RAM I don't see the reason to give a hoot if it took 65 or 72. At that point it's like buying a car and saying "but this one gets 23.5 miles to the gallon, that other one's only 23.47!"

---

### Post by Onyros on 2007-11-14
> **happysmileman said:**
> Konqueror uses KHTML, which is what Webkit was based on, so you can expect similar results (though not the exact same results since code has changed a good bit AFAIK), however you'd need KDELibs and stuff, so if you're using GNOME the memory usage might be more than it should be.

Webkit should be in QT soon (maybe it already is) so you could expect to see some.I'm not usually a GNOME user, I use it occasionally; my favourite environment is, without a shadow of a doubt, Fluxbox. I think GNOME's bloated for what it offers, and Fluxbox as minimalistic as it is, is far more efficient. And believe me, I understand why Openbox has been garnering fans over time, it's just that Fluxbox has a few killer features of its own (auto-tabbing, I also like the default panel over whichever other panels are available, which keeps memory usage down).

It's just sometimes I need to use the Desktop, drag files around, create new empty docs, etc... and those are the times I'd rather use GNOME. It's something I brought over from my Mac days, using the desktop for those things.

But I really only use GNOME and Fluxbox, no KDE for me, even though it does have incredible apps (K3b comes to mind).

I once had Konqueror installed, but I had some rendering issues which kept me from using it. Also, due to the fact I mainly use GTK apps, its startup time was awful in the environments I use.

I'll give it a try again, though, no harm in trying it out ;)

---

### Post by Onyros on 2007-11-14
> **SomeGuyDude said:**
> I like Opera and all, but unless you only have 512MB of RAM I don't see the reason to give a hoot if it took 65 or 72. At that point it's like buying a car and saying "but this one gets 23.5 miles to the gallon, that other one's only 23.47!"That's not the only point: Opera did so faster than the other browsers in that test (except Dillo, perhaps), with controlled CPU usage. And it's only going to improve, if one is to believe reports regarding the new rendering engine that's coming along quite nicely (Kestrel).

I know the differences are laughable, but choosing between a default Opera vs a default Firefox, for example, is a no-brainer for me, in terms of functionality, speed... and memory usage (hehe).

---

### Post by happysmileman on 2007-11-14
> **SomeGuyDude said:**
> I like Opera and all, but unless you only have 512MB of RAM I don't see the reason to give a hoot if it took 65 or 72. At that point it's like buying a car and saying "but this one gets 23.5 miles to the gallon, that other one's only 23.47!"

Some of us do only have 512MB of RAM(OMFG!!!) and some of us do see the reason for less memory usage.

I'm currently using 100MB of swap space on my ancient PC with only 512MB RAM, (though in fairness I'm compiling QT) but there are times when 7MB means the difference between going into swap or not. So I'll take my Opera (as well as for it's increased speed).

---

### Post by init1 on 2007-11-14
Wow, that was very unexpected. I though hv3 would be on the bottom. Hopefully they'll sort that out in another release.

---

### Post by Whiffle on 2007-11-14
can you post links to those sites?  I'd like to see how konqueror fairs.

---

### Post by bruce89 on 2007-11-14
> **Onyros said:**
> I know the differences are laughable, but choosing between a default Opera vs a default Firefox, for example, is a no-brainer for me, in terms of functionality, speed... and memory usage (hehe).

That would make many freedom people very annoyed. (me being one of them, I think it's bad enough that Firefox is default)

> **Onyros said:**
> I once had Konqueror installed, but I had some rendering issues which kept me from using it. Also, due to the fact I mainly use GTK apps, its startup time was awful in the environments I use.


> **happysmileman said:**
> Webkit should be in QT soon (maybe it already is) so you could expect to see some.

WebKit has now got a GTK+ port which is progressing well. [http://trac.webkit.org/projects/webkit/wiki/BuildingGtk](http://trac.webkit.org/projects/webkit/wiki/BuildingGtk)

Gutsy has a fairly old SVN snapshot available. [http://packages.ubuntu.com/gutsy/libs/libwebkitgdk0d](http://packages.ubuntu.com/gutsy/libs/libwebkitgdk0d)

---

### Post by urukrama on 2007-11-14
> **Onyros said:**
> I created a simple HTML page, mimicking the original stuff, 9 links and all (with opacity for a nice effect and a black background, which I always prefer) and started it up in my adapted Kazehakase_clean script (thanks, K.Mandla! - I also adapted that to Epiphany).

Will you make that html page available? It'd be nice to use it with Epiphany.

---

### Post by Onyros on 2007-11-14
> **urukrama said:**
> Will you make that html page available? It'd be nice to use it with Epiphany.Sure thing, I'll hook you up in a few minutes.

I have it optimized for my Thinkpad's resolution (1024x768 - thumbnails are 150 x 113 px), but you'll easily be able to change everything to your liking (as well as change the default links I have there, now, obviously).

---

### Post by Onyros on 2007-11-14
Here you go, mate!

With Kazehakase, as I'm using a startup script (which cleans cookies and a few other things I like to keep tidy - once again, credit goes to K. Mandla), I launch it with "kazehakase path/to/speed_dial/menu.html".

Also changed the "New" bookmark from "about:blank" to the Speed Dial html file.

In Epiphany, all you have to do is change the start page.

---

### Post by Whiffle on 2007-11-14
Heres a couple for Konqueror

---

### Post by rliegh on 2007-11-14
> **SomeGuyDude said:**
> I like Opera and all, but unless you only have 512MB of RAM I don't see the reason to give a hoot if it took 65 or 72.
You say that as if it's at all unusual to 'only' have 512mb of ram. Most low-end computers sold brand-new these days come with 512 by default. Hell, I'm the only one I know who has >1gb of ram.

---

### Post by Onyros on 2007-11-14
> **Whiffle said:**
> Heres a couple for KonquerorAh, Whiffle, sorry about that... The set of links I uploaded were slightly different from those I used in the original test. (I had a few links there which were kinda personal, so I changed them around a bit).

Even so, it's a very interesting result for Konqueror. With these links, I have Opera using 55.3 MB, though ;)

---

### Post by Whiffle on 2007-11-14
Meh, I was just curious anyway.  I didn't untar the file either, i just opened it in konqueror :-P

---

### Post by urukrama on 2007-11-15
> **Onyros said:**
> Here you go, mate!

Cheers! This is neat.

---

### Post by Darkhack on 2007-11-15
I've been working on my own web browser since the beginning of November and I decided to perform the same test with the speed dial page that was offered.  Memory usage for my browser was at 51.6 MB.  That's using the Gecko rendering engine.  I'm sure I could easily get it down to 45 MB or less if I was using WebKit, but unfortunately, the GTK+ port of WebKit is very immature and lacks a lot of features.  WebKit is vastly superior to Gecko so I will be switching once the GTK+ port gets more features implemented.

---

### Post by Nevon on 2007-11-15
> **rliegh said:**
> You say that as if it's at all unusual to 'only' have 512mb of ram. Most low-end computers sold brand-new these days come with 512 by default. Hell, I'm the only one I know who has >1gb of ram.
Lol, I have 196mb on this baby :P Currently I am using Fluxbuntu with Firefox, and even if it takes a couple of seconds to start up, it works pretty well once you've got it up and running.

---

### Post by Onyros on 2007-11-15
> **Darkhack said:**
> I've been working on my own web browser since the beginning of November and I decided to perform the same test with the speed dial page that was offered.  Memory usage for my browser was at 51.6 MB.  That's using the Gecko rendering engine.  I'm sure I could easily get it down to 45 MB or less if I was using WebKit, but unfortunately, the GTK+ port of WebKit is very immature and lacks a lot of features.  WebKit is vastly superior to Gecko so I will be switching once the GTK+ port gets more features implemented.Ooooh, nice! When's an alpha or beta ready for testing?? :D

WebKit may even get you better results. I tried Midori once, with an SVN WebKit and apart from crashing with Flash, it was looking really cool as it were.

---

### Post by Darkhack on 2007-11-15
> **Onyros said:**
> Ooooh, nice! When's an alpha or beta ready for testing?? :D

WebKit may even get you better results. I tried Midori once, with an SVN WebKit and apart from crashing with Flash, it was looking really cool as it were.

I've looked at Midori and it was very nice.  If it ever catches on then I'll probably just point people in that direction and keep my project as a hobby for myself.  I'm not a very fork happy person and I wanted to help with Epiphany but its codebase is terrible and bloated.  Epiphany is around 86,000 lines of code while Midori sits at a lean 5,360.  So far, I'm at 155 lines of code but thats because it doesn't do anything.  Location bar, back/forward navigation, and tabbed browsing support are all I have which is also why it uses such little memory too.  Midori came in at 51.5 MB and also has a lot more features.

One of my pet peeves though is code readability, organization, and documentation.  I shouldn't have to spend more than five minutes finding out where something is located in code.  Midori is excellent in this aspect, though it could still use a bit of improvement of course.  Epiphany is just awful at this.  Good browser, just not easy to develop for.  Developer Manuals are basically dead in the open source world.  Apparently "go look at the code" has become the new RTFM for newbie developers to a project since there is no manual.

To answer your question though, I probably won't release it, at least not for a long time.  I have a "target" release date in my head of April 3, 2008 (My best friend's 18th birthday!) to get something that is stable and usable for basic browsing.

---

### Post by chameleonkid on 2007-11-15
Is there a way to set the home page on opera so it opens up all nine of your speed dial pages as the home page? I think that feature would be pretty awesome.

I will assume you "opened" each speed dial page manually, unless this is capable...

---

### Post by Onyros on 2007-11-15
> **chameleonkid said:**
> Is there a way to set the home page on opera so it opens up all nine of your speed dial pages as the home page? I think that feature would be pretty awesome.

I will assume you "opened" each speed dial page manually, unless this is capable...Firefox handles that well: you can put several start pages on tabs, by separating them like this

"http://ubuntuforums.org | [http://slashdot.org](http://slashdot.org) | http://distrowatch.com" in the start page option, I believe on General Preferences, and I think there's no limit to that.

With Opera, I just middle clicked on each image so that each link would load on a different tab. Same goes for Kazehakase and Epiphany... It's just that I used a fake Speed dial on these two, while Opera has the real thing.

Also, @ Darkhack: keep it up, mate! Try something a little different, like Kazehakase's developer did. It has a few nice features OOTB. But I gotta give it to you: Midori looks really promising, and it's good to know they're keeping it organized: makes for better development in the future.

---

### Post by cocopops on 2007-12-10
Hi,

I did some more testing using this speeddial page with Hv3. The numbers I got on mac osx are a long way from impressive, but better than those that you report. In case anybody is interested:

  [http://tkhtml.tcl.tk/cvstrac/tktview?tn=246](http://tkhtml.tcl.tk/cvstrac/tktview?tn=246)

I'm seeing Hv3 consuming a shade under 110MB vs Firefox2 at around 77. With javascript disabled, Hv3's memory usage is much more acceptable.

If you (or anybody else) does any more testing of this sort, it would be really helpful if you could let the authors of the minor browser projects know about it. Firefox, Opera etc. are probably drowning in feedback, but the little guys like Hv3, Dillo, Netsurf would really benefit from being told when they have problems like this.

Regards,
Dan.

---

### Post by Onyros on 2007-12-14
> **cocopops said:**
> Hi,

I did some more testing using this speeddial page with Hv3. The numbers I got on mac osx are a long way from impressive, but better than those that you report. In case anybody is interested:

  [http://tkhtml.tcl.tk/cvstrac/tktview?tn=246](http://tkhtml.tcl.tk/cvstrac/tktview?tn=246)

I'm seeing Hv3 consuming a shade under 110MB vs Firefox2 at around 77. With javascript disabled, Hv3's memory usage is much more acceptable.

If you (or anybody else) does any more testing of this sort, it would be really helpful if you could let the authors of the minor browser projects know about it. Firefox, Opera etc. are probably drowning in feedback, but the little guys like Hv3, Dillo, Netsurf would really benefit from being told when they have problems like this.

Regards,
Dan.Hi, Dan :)

I actually did the testing with Javascript disabled (which is HV3's default, btw), but I'll have to look further into it, and then I'll surely drop them a line or file a bug report. And I do second that appeal of yours, regarding the "little guys".

Also, my bad for not reporting this to them before! Thanks for taking care of that for *lazy* me ;)

---

### Post by daynah on 2007-12-14
> **SomeGuyDude said:**
> I like Opera and all, but unless you only have 512MB of RAM I don't see the reason to give a hoot if it took 65 or 72. At that point it's like buying a car and saying "but this one gets 23.5 miles to the gallon, that other one's only 23.47!"

This test had FF's memory to begin with, but FF has a documented "feature" that is a memory leak. It may only be a bit of a difference to start with, but it will grow and grow till you restart FF, just like it's recommended you restart Windows once a day.

Opera also has all of the same features that FF has, and manages to have many of those features (email, torrenting, IRC) without "adding on" anything, which does add on time and strain to FF.

Currently, Opera has features that FF does not have. It's speed dial does things that none of the add-on speed dials touch. The Opera Beta also has built in syncing of favorites and other settings without compromising the brower's basic integrity. If you get a FF syncing mechanism, FF will only get worse.

Opera, though proprietary, works hard to support its linux folk. Gnash currently doesn't work in it, but I read on the Opera forum that they're working on that for the next version. Everything else works gceat though, and there is easy to read opera-on-linux documentation because they want to support us.

Most of the other broswers suffer from a lack of features. FF and Opera have cool add ons and widgets, and other browsers don't have that. Opera has great things built in, and really only Konqueror can do anything more than surf the web. Though you, reader, may like a certain "other" browser, the numbers say it's a fight between FF and...maybe Opera has a chance.

---

### Post by Onyros on 2007-12-14
Opera has become better through time, and I really can't say the same about Firefox, personally. In that good ol'frenzy of updating just to shove in new features, there's a lot of things that are left unattended. Memory leaks (and yep, Opera has "them" too, but they're really a feature... which can easily be disabled through *opera:config*), the fact that the browser has become slower through time, etc.

I know Firefox is (or was) a landmark for the growth and recognition of FOSS, but in my view it's unmistakable: Opera is the superior browser. I've become "disenchanted" with Firefox ever since that controversy vs. Debianl; disenchanted with the Mozilla Corporation for dropping Thunderbird (even though I stopped using it long ago). Even so, I am not militant about those matters: that's not the reason why I don't use Firefox. I really prefer Kazehakase as a Gecko-based alternative.

I do admire people's respect for the project, but only while they stray from blind zealotry. At the end of the day, if Firefox was indeed superior to Opera, it would be a no-brainer for me. If they were somewhat similar in terms of performance and features, maybe the fact that Firefox is a FOSS project would tilt me that way.

As it is, Opera is my favourite browser. And this is my opinion, but a cold-headed rational approach would probably lead me the same way.

And now, to finish it off, brilliantly enough, the flashplugin-nonfree update pushed today through the gutsy-proposed repo doesn't work with Opera.

That and considering most people's reports that the latest version is no improvement whatsoever, I believe it's time for a downgrade. :D

---

