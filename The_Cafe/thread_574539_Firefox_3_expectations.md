---
title: "Firefox 3 expectations"
date: 2007-10-12
forum: The Cafe
---

### Post by vishzilla on 2007-10-12
wht are your expectations on Firefox 3, the features included, features you wish should be there?

I like the Unified Bookmarks/History with the tag feature. Memory leaks is a major concern

---

### Post by -grubby on 2007-10-12
My expectation is that it goes MUCH faster and doesn't crash so much when I open Google videos(is that Adobe's fault?)

---

### Post by Kitsun on 2007-10-12
Less crashes is all I really want.

Going easier on the resources is good too.

---

### Post by FuturePilot on 2007-10-12
> **nathangrubb said:**
> My expectation is that it goes MUCH faster and doesn't crash so much when I open Google videos(is that Adobe's fault?)

Yes, Adobe's fault. That's totally a Flash issue.

---

### Post by mjwood0 on 2007-10-12
1. Less resource usage (or just less memory leaks)
2. Better bookmark support.  Bookmark keywords are so handy and yet so little emphasis is put on them.


Really, that's all I need to be happy.  Other than that, it all works as expected!

---

### Post by Kingsley on 2007-10-12
I expect easier backups, without add-ons.

---

### Post by Kingsley on 2007-10-12
> **mjwood0 said:**
> 1. Less resource usage (or just less memory leaks)
2. Better bookmark support.  Bookmark keywords are so handy and yet so little emphasis is put on them.


Really, that's all I need to be happy.  Other than that, it all works as expected!
I love bookmark keywords too and they're already easy enough to use in Firefox 2. All I did was make a bookmark folder called "Keyword Search' and then placed the search links in there.

---

### Post by starcraft.man on 2007-10-12
Why speculate on expectations? Go try the latest milestone and see for yourself... >.>.

---

### Post by santy_kushwaha on 2007-10-12
ya less crashes that for sure and it support some of the software that will helps to play games online bcoz firefox give a hazal to install those software sometimes

---

### Post by smartboyathome on 2007-10-12
It to actually work with java, ubufox, and apturl.

---

### Post by kadath on 2007-10-13
I'd like Firefox to go back to being the lightweight browser it was in the v1.5 and earlier days, but that's obviously not going to happen.

Anyway, I'm using Minefield alpha 9 right now and it's not bad. Most of the new features are useless for me (bookmark tagging, download window search feature, etc) but I wouldn't say it's worse than FF2.

My main problem is that XUL just seems to slow Firefox down. If I could find a GTK2 browser that had all of the features I get through the few extensions I use (NoScript, Adblock Plus, CS Lite and DownThemAll, for example), I'd switch, but that's unlikely to happen.

---

### Post by yatt on 2007-10-13
> **kadath said:**
> I'd like Firefox to go back to being the lightweight browser it was in the v1.5 and earlier days, but that's obviously not going to happen.

Anyway, I'm using Minefield alpha 9 right now and it's not bad. Most of the new features are useless for me (bookmark tagging, download window search feature, etc) but I wouldn't say it's worse than FF2.

My main problem is that XUL just seems to slow Firefox down. If I could find a GTK2 browser that had all of the features I get through the few extensions I use (NoScript, Adblock Plus, CS Lite and DownThemAll, for example), I'd switch, but that's unlikely to happen.I wish for the same thing, but Firefox seems to be going the way of Mozilla. If Epiphany wasn't the epitome of Gnome's features scare users mentality, I would use it. The only real alternative (IMO) is Konqueror, but I don't want to install all the KDE libs for it.

As for a realist wish: in FF 1.5 and earlier, when you open the addressbar dropdown and select a "I'm feeling lucky" search, it redoes the search. In FF2 it treats the term as a URL and you get a 404.

---

### Post by Polygon on 2007-10-13
> **smartboyathome said:**
> It to actually work with java, ubufox, and apturl.

those are the responsibility of Sun, Ubuntu and ubuntu (respectively). they are just plugins that interface with the browser. Mozilla makes the browser and the plugin API and other companies make their stuff work...if it doesnt work, its most likely the third party companies fault

and my expectations...maybe just make firefox less memory/cpu intensive. Just overall general usability and speed performance and stuff

---

### Post by jrusso2 on 2007-10-13
Fix the memory issues, I have seen it running at 140 mb of ram on Linux.

New java script engine thats less vulnerable.

---

### Post by EdThaSlayer on 2007-10-13
I hope that Firefox 3 will start up faster and crash less. It also would have to look "Next-Gen". :D

---

### Post by ticopelp on 2007-10-13
> **Kitsun said:**
> Less crashes is all I really want.

Going easier on the resources is good too.

+1

---

### Post by betweenthetines on 2007-10-13
> **jrusso2 said:**
> Fix the memory issues, I have seen it running at 140 mb of ram on Linux.

I've actually monitored Firefox.bin using over 250MB of ram at one time before on my computer, but that might have something to do with the fact that I set vm.swappiness=0 in my /etc/sysctl.conf file...

I agree with the general opinion so far: faster overall and more streamlined with resources, that's what Firefox 3 should bring.

---

### Post by Darkhack on 2007-10-13
> **yatt said:**
> I wish for the same thing, but Firefox seems to be going the way of Mozilla. If Epiphany wasn't the epitome of Gnome's features scare users mentality, I would use it. The only real alternative (IMO) is Konqueror, but I don't want to install all the KDE libs for it.

I recently started writing patches for Epiphany because I wanted the same thing; a nice, lean, quick, native GTK+ browser.  And thanks to work by Xan Lopez, Epiphany can now be compiled against WebKit.  WebKit is a rendering engine that is currently being used by Safari and is in the processes of becoming the replacement for KHTML in Konqueror [1].  The advantage to WebKit is that it is actually *more* standards compliant than Mozilla's Gecko engine, and it is up to twice as fast.  Epiphany still runs on Gecko in the latest GNOME, but if you download the source code, you can compile it with WebKit.  Do note however that it is basically unusable since the GTK+ port of WebKit is still under development.  When I say unusable, I mean it... no scrollbars for the pages even.

As for Epiphany's "the users are idiots" philosophy that Linus Torvalds famously made fun of, Yes, Epiphany is pretty bad.  Alas, there is hope!  Epiphany does support extensions just like Firefox does.  Ubuntu even has the *epiphany-extensions* package available in the repositories and includes extensions such as Ad-Block and Greasemonkey.  Another strong advantage here is that the extensions are written in C and are thus compiled into binary code.  As more developers become interested in Epiphany, we can get some extensions in there so that more advanced users, such as ourselves, don't feel like we're using Grandma's web browser.  Think about it; Epiphany with WebKit and binary compiled extensions.  You'd have a full featured, yet fast and lean browser that is also simple enough for Grandma and powerful enough for you with the additional extensions.

Konqueror is pretty kick *** too, but I don't want to have to install the KDE libs and run it in GNOME.  If you are a KDE user though, you can't get any better than that.  Konqueror is probably the best program ever written, but I still use GNOME simply because I dislike a lot of other things about KDE.  The one thing that Konqueror lacks is proper extension support.  There are a few tweaks from [KDE-Apps.org]("http://kde-apps.org"), but it's a big jump to even call those extensions.

*[1] - Apple forked KHTML to create WebKit originally and the KDE team had been backporting features but they are now going to be sharing the same codebase.*

---

### Post by LowSky on 2007-10-13
i want it to start up faster,  be more lightweight, search faste, less memory leaks.

What is with every company adding all these extras and making it so hard to turn them off?

All i want is the ability to pick and choose feature with ease, none of this automatic no choice stuff. I miss the old FF that was so customizable that IE had to play catch up. Now I'm thinking that Firefox has to catch up. I wan't the browser that changed the internet back the way it used to be.

---

### Post by phrostbyte on 2007-10-13
Firefox 3 is looking really good, the rendering engine is MUCH improved I've noticed.

---

### Post by Ireclan on 2007-10-13
I want Firefox to block individual elements of a page, WITHOUT the need for extensions. Just like Opera.

---

### Post by stealth17 on 2007-10-17
> **Kitsun said:**
> Less crashes is all I really want.

Going easier on the resources is good too.

QTF.... also better CSS3 support

---

### Post by FredB on 2007-10-17
Just try alpha9 when it will be released (end of this month)... And you'll be greatly surprised.

I am using development builds of mozilla software since year 2000... So I've known phoenix 0.1 in september 2002...

Wow, Firefox is around 5 years old...

---

### Post by the_darkside_986 on 2007-10-17
A usable, properly documented NPAPI would be nice. I'm not sure if they are in the process of changing it or what, but the last time I tried to write a simple do-nothing plugin (not extension) without the mozilla source tree, it was a disaster. The example plugin source code is confusing, and is inconsistent with that the plugin tutorial says, which says that in a plugin dll, the NPP_* functions are the one implemented by the plugin not all these random NS_* ones I see in the example. Also there is no readable makefile for the example plugin. Its makefile depends on another makefile which depends on another makefile, and so on. 

All I want from the NPAPI: the ability to implement a firefox plugin .so file simply by writing the NP_ and NPP_ functions (and returning the right string value for the mime-type I want to handle), and a working makefile that is small as a simple gcc project and does not require mozilla source tree or an obscure base plugin example to build on to. And a real tutorial would be nice. When I try to write a simple .so file that does just that, firefox does not see the plugin at all. Currently, there is much more work that has to be done to make a simple plugin than what the tutorial seems to imply.

This probably explains why Adobe's flash plugin crashes so much. The plugin API is so archaic and confusing that we are lucky to have anything from them for the mozilla browser platform. I wonder if Konqueror and KHTML browsers have a better and different plugin system? I know they are compatible with mozilla plugins though. And maybe WebKit will have its own, good plugin API.

(If anyone was wondering what I was trying to do, I was trying to write a simple Lua player plugin. It is just an interesting side project I was trying to do for fun.)

---

### Post by ezphilosophy on 2007-10-17
I would like an easy/convenient way to backup my pull-down search engines.

---

### Post by Tom Mann on 2007-10-17
I would like greasemonkey and adblock plus built in.

---

### Post by aktiwers on 2007-10-17
I hope it will be more lightweight

---

### Post by kadath on 2007-10-17
> **Tom Mann said:**
> I would like greasemonkey and adblock plus built in.

For the love of god, NO. The whole problem with FF is that it's too heavy already. I like Adblock Plus, but it shouldn't be built into the browser. I don't use Greasemonkey at all, so I'd hate if it was thrown in there as well.

I don't even know why spellchecking is a feature in FF. Useful? Yes. Necessary? No. There are a lot of people using FF that still have posts riddled with spelling errors.

Also, is it just me, or is the Linux version of FF almost completely ignored by Mozilla? Every time I see news about FF3, it's always regarding the Windows or OS X versions (despite FF most certainly having more users on Linux than OS X). Frankly, I don't think Mozilla honestly gives a rat's *** about Linux. Windows is where their primary market share is, and they're making oodles of money from it. It seems like all of the improvements to FF on Linux are contributed by the community. For example, a patch has been submitted to offer a thumbnail preview pane (a la GIMP) in the file upload window, to make uploading images more user-friendly. When will we see the patch get accepted and applied? FF4? FF5? Who knows.

I sort of wish the Iceweasel maintainers would make it an official fork and start accepting patches for it. Things would probably get fixed a lot faster.

---

### Post by Rhapsody on 2007-10-17
More speed, improved XHTML support, improved SVG support, new crash reporter. Firefox 3 looks pretty good.

Still, I'm more excited about Firefox 4. I'm hoping for further SVG improvements (animations, a GUI for zooming, and being able to use SVG as a proper image format would be nice), better CSS support (possibly CSS 2.1 compliance, more CSS 3, with text-shadow being what I want most), and deCOMtamination.

---

### Post by happysmileman on 2007-10-17
I expect to try it for a week or so, see if it's any better,, then probably realise it's not and stick with opera

---

### Post by TeaSwigger on 2007-10-18
Progress with regard to eliminating memory leaks and lowering resource usage. Less features for core Firefox, instead focusing on keeping it secure, lean, and as solid a base as possible for the modular extensions etc to add features and do their stuff however the user desires.

---

### Post by undine on 2007-10-18
> **TeaSwigger said:**
> Progress with regard to eliminating memory leaks and lowering resource usage. Less features for core Firefox, instead focusing on keeping it secure, lean, and as solid a base as possible for the modular extensions etc to add features and do their stuff however the user desires.

You just described Epiphany ;)

---

### Post by curuxz on 2007-10-18
I don't know what Firefox 3 will look like, but I will bet money on IE 8 being almost identical ;)

---

### Post by Raval on 2007-10-18
> **curuxz said:**
> I don't know what Firefox 3 will look like, but I will bet money on IE 8 being almost identical ;)

I see this also.

---

### Post by TeaSwigger on 2007-10-19
> **undine said:**
> You just described Epiphany ;)

They should too?

Yeah I've tried it but not much as I've been hanging around in kubuntu most of the time. Konqueror is also interesting if much more "do it all" compared to Epiphany. Didn't want to compare though as the OP only asked about 'fox. :)

> **curuxz said:**
> I don't know what Firefox 3 will look like, but I will bet money on IE 8 being almost identical ;)

And something tells me that the innovators freely contributing the ideas to the free Firefox for non-profit circulation won't be getting any checks back from Microsoft when MS starts offering their "new" features in their for-profit non-free software.

---

