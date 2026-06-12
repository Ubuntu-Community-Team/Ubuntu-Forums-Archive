---
title: "Boxee Users?"
date: 2011-10-11
forum: The Cafe
---

### Post by Roasted on 2011-10-11
I've been considering a Boxee set up for quite some time,  however I have a few questions regarding it.

I've read that Boxee can handle certain TV shows and certain streaming services, but I've never actually seen it in person or successfully gotten certain add-ons to work in conjunction with some of these services.

When you are utilizing Amazon Prime or Netflix, are you supposed to use the browser? Or is there supposed to be a specific add-on for these services directly?

Is anybody running Boxee with decent success? I slapped it on a spare desktop (Core 2 Duo, 2gb RAM) with a lower end Nvidia 6150 graphics card. To the 40" TV, it displayed very thick black bars on each side of the screen, something I couldn't find a fix to.

I'm hoping upgrading the graphics card will do the trick. In the mean time I was curious if anybody had any comments in regard to Boxee and how it operates and integrates with several popular streaming services.

All opinions welcome. Thanks guys!

---

### Post by nickleboyblue on 2011-10-11
I'm running Boxee on a machine a built from parts I got from a second-hand store and a refurbished motherboard and graphics card.  The connection to the television is an s-video cable, as I do not need the audio (I use the computer's 5.1 surround sound instead).  The entire system cost me a total of about $100 USD and works fine on a P3 processor.

As for the picture, does the screen have black bars on the side when the machine is booted but not running Boxee?  You might try adjusting the computer's resolution to match your television set a little better.

Inside of Ubuntu, Boxee does not support Netflix.  I have looked and failed to find any support for Amazon's streaming service either, but at the rate things go for Boxee, I wouldn't be surprised if that part of this comment is already obsolete.  Boxee supports a ton of "apps" that allow you to easily browse YouTube, Funny-or-die, and hundreds of other internet video services, both free and paid, excluding Netflix.  For Netflix to work in Boxee, you would have to purchase a Boxee box.

Overall, I am extremely impressed with the Boxee interface except for one thing: It's not always clear how to adjust volume levels, and sometimes it's not even possible.

I run Mythubuntu with Boxee and Hulu desktop installed as well.  I edited the XML files from which Mythubuntu derives it's main menus, giving me access to both Boxee and Hulu Desktop from the Mythubuntu menu.  I control Mythubuntu and Boxee from my android, but I can't get Hulu to react to it just yet.  Eventually, I will be able to control every system on the computer using a wiimote (Drivers for them can be found easily).

I have not had any success accessing Amazon streaming service in Mythubuntu's browser, but I haven't tried Boxee.  I'll try it, and if it works, that will make the entire system all that much more usable.

Just because each media center out there claims to be complete doesn't mean you have to use it as a complete media center.  I like Boxee for Internet television, MythTV for my media library, and Hulu Desktop for, what else, Hulu.  It's possible to also install other media centers to your heart's content inside of Mythubuntu, allowing you to entirely customize your experience, even down to the point of installing games and placing them in the menus, with or without the Mythubuntu gaming plugin.  The downside is it takes a bit of work to customize things, but it's really rewarding and you get a truly unique system that your friends will envy you for.

---

### Post by Roasted on 2011-10-11
First off, thanks for the detailed response. It was a huge help. 

The bottom line is this. My girlfriend is paying 130 a month for cable/internet when she hardly uses it. Instead she was considering on dropping cable and getting basic DSL. Being a third shifter, she misses out on a lot of shows during regular air time anyway. She just wanted a way to play them back so she considered a streaming service. That being said, with how infrequently she watches TV, coupled with what little she wants to access shows and movies, a basic DSL package/no cable/streaming service is just what she needs.

The problem is, I want to make sure whatever she gets... works...

I set up a system for her with 10.04 on it. Once 11.10 comes out I'll likely bump it to that since Gnome Shell and Unity look very attractive on TVs even though they are desktop environments. 

If I set her up there, she'll obviously have Chromium and Firefox available. I'm curious, with or without Boxee, how likely it'll be that she could utilize streaming services then? I mean, if Boxee works, great. If it doesn't, the trusty old browser is there...

Any additional thoughts?

---

### Post by castrojo on 2011-10-11
The problem with boxee is that unless you have the Boxee Box the software itself hasn't been updated in a really long time (at least a year).

They say they're going to update it this fall: [http://blog.boxee.tv/2011/06/13/boxee-for-pc-mac-ubuntu-getting-fall-update/](http://blog.boxee.tv/2011/06/13/boxee-for-pc-mac-ubuntu-getting-fall-update/)

I'm anxiously waiting for this. Currently I'm using XBMC (which is awesome for local movies and stuff, but doesn't have the nice integration with streaming content that boxee has).

---

### Post by Roasted on 2011-10-11
> **castrojo said:**
> The problem with boxee is that unless you have the Boxee Box the software itself hasn't been updated in a really long time (at least a year).

They say they're going to update it this fall: [http://blog.boxee.tv/2011/06/13/boxee-for-pc-mac-ubuntu-getting-fall-update/](http://blog.boxee.tv/2011/06/13/boxee-for-pc-mac-ubuntu-getting-fall-update/)

I'm anxiously waiting for this.**_ Currently I'm using XBMC (which is awesome for local movies and stuff, but doesn't have the nice integration with streaming content that boxee has)._**

My thoughts exactly. XBMC is beautiful. But limited... That said, it brings up an interesting idea. If Boxee's advantage over XBMC is the integrated streaming services, yet Boxee doesn't have those services integrated (unless you buy an actual Boxee box), at that point Boxee (when installed manually) offers me nothing over XBMC... That brings me back to my previous comment. "XBMC is beautiful. But limited..." Suddenly it doesn't seem so limited vs Boxee, does it?

That said, maybe I'd be better off just using a standard Ubuntu install and setting up XBMC. That way I could fire up to the default Unity or set up Gnome Shell and have a nice desktop environment for basic web browsing tasks (including online streaming right in the browser) or I can just fire up XBMC and be in my localized home theatre. I'm really thinking that would be the best, since I could have a nice interface with a trusty ole web browser to do the streaming legwork and XBMC to wrap things up when I want to show the family some pictures or watch Pink Floyd's Pulse concert...

Hmm... Is anybody else doing this? Am I correct that this idea may be the best and most modular for what I'd like out of a HTPC?

Also - the screen resolution is set properly. I'm not sure what it is. I hooked up my Macbook Pro last night and it did the exact same thing. I'm not sure if it's just the limited power the graphics card has on the Ubuntu desktop (I assume my Macbook Pro isn't a GPU powerhouse either) that's doing it. *shrug*

---

### Post by Roasted on 2011-10-12
So I've been wondering something. Let's say (in conjunction with my previous post) I were to just use a Gnome Shell or Unity environment as my desktop solution for my HTPC. I mean, think about it. If I get a dark theme to resemble a more movie-theatre like setup on G3 or Unity, it could look very presentable. Both desktop environments would likely work terrific.

That said, when we're talking about a TV you'll likely be sitting farther back than a regular monitor. I see G3 has the "large text" option which is a nice bump for Gnome Shell. Are there any other enhances for making Gnome Shell's appearance even larger? Does Unity have anything like this to help out as well?

---

### Post by castrojo on 2011-10-12
I don't really use a desktop with it, I just have it set to auto login to XBMC.

---

### Post by thatguruguy on 2011-10-12
> **Roasted said:**
> So I've been wondering something. Let's say (in conjunction with my previous post) I were to just use a Gnome Shell or Unity environment as my desktop solution for my HTPC. I mean, think about it. If I get a dark theme to resemble a more movie-theatre like setup on G3 or Unity, it could look very presentable. Both desktop environments would likely work terrific.

That said, when we're talking about a TV you'll likely be sitting farther back than a regular monitor. I see G3 has the "large text" option which is a nice bump for Gnome Shell. Are there any other enhances for making Gnome Shell's appearance even larger? Does Unity have anything like this to help out as well?

If you're just setting up an HTPC, there are better options than running a full Unity or Gnome 3 desktop.  As already alluded to, you can set up XBMC to run automatically at login.  I run XBMC on my Mythbuntu box attached to my main television (because there are strengths and weaknesses to both MythTV and XBMC), and I simply added XBMC as an item in my main Mythbuntu menu.

---

### Post by Munk3y on 2011-10-12
I've been a long time Boxee user. It works pretty good and reliably for me. My girlfriend uses it easily. I have run into some problems over time, though.

1. Make sure to stick with a version of Ubuntu that they support. You'll see on their download page, they only go up to 10.10 because they haven't updated their software in so long.

2. I see you have a nVidia video card. Make sure to do: sudo apt-get install libvdpau1

3. DVD Playback is choppy right after install. To fix it, I had to do the following:
A. sudo apt-get install libmpeg2-4
B. ln -s /usr/lib/libmpeg2.so.0.0.0 /opt/boxee/system/players/dvdplayer/libmpeg2-i486-linux.so

4. After installing/upgrading Flash, sometimes Boxee will show a video in the top left corner of the screen really small when streaming almost everything. To fix it, you have to disable hardware acceleration in Flash by opening Firefox and going to a site with flash on it. Then right clicking on the Flash object, going to settings and changing it in there.

5. Some HD videos are choppy, dropping frames apparently because Boxee doesn't like the way they are encoded.

6. If you mount a network share on the file system, Boxee doesn't seem to recognize it's there and instead shows a blank directory.

7. Boxee itself seems to have issues mounting network shares of some Windows computers. However, you can stream from them if they have media sharing on.

Hopefully the update they release in the "fall" will actually resolve some of the mounting issues.

---

### Post by Roasted on 2011-10-12
> **thatguruguy said:**
> If you're just setting up an HTPC, there are better options than running a full Unity or Gnome 3 desktop.  As already alluded to, you can set up XBMC to run automatically at login.  I run XBMC on my Mythbuntu box attached to my main television (because there are strengths and weaknesses to both MythTV and XBMC), and I simply added XBMC as an item in my main Mythbuntu menu.

But, here's my dilemma:

I want streaming.
XBMC does not do integrated streaming.
Boxee does not do integrated streaming.

Sure, XBMC and Boxee seem great for local usage, but if I want streaming... I need to use my web browser... at that point it begs the obvious question, do I REALLY want XBMC to auto login if 80% of my usage on this HTPC will be in a web browser/desktop environment??

---

### Post by ufugu on 2011-10-12
> **Roasted said:**
> 
The problem is, I want to make sure whatever she gets... works...


Same scenario with my wife.  

I've tried a few media center solutions (Boxee, XBMC) and they are fun to play with, but what I've realized is that it's all an elaborate solution for a simple problem.  If you are watching video, you are probably doing it full screen so what's underneath really doesn't matter.

All you need is a minimal OS, a web browser to stream (we use Hulu and Amazon 99% of the time) and a file browser and VLC to play anything else.  She knows how to use these tools already, so it's not frustrating to her if there's any issue.  

Add a wireless mouse and a minimum font size and you're good to go from the couch.

Forget about Netflix on Linux, don't even bother. They don't want your business.

---

### Post by drascus on 2011-10-12
I actually have a boxee box. the desktop app is a few versions behind the one that they sell with the box. much of boxee is accessed through apps. so for instance netflix is an app you don't have to go to the website in the browser. There is a lot of free tv shows up there. Also there is some third part repositories which can add tons of free tv shows and movies to your setup. I personally have ditched cable and get all of my video through the boxee box. That is not an ideal setup for everyone but it works for me.

---

### Post by Roasted on 2011-10-12
> **ufugu said:**
> Same scenario with my wife.  

I've tried a few media center solutions (Boxee, XBMC) and they are fun to play with, but what I've realized is that it's all an elaborate solution for a simple problem.  If you are watching video, you are probably doing it full screen so what's underneath really doesn't matter.

All you need is a minimal OS, a web browser to stream (we use Hulu and Amazon 99% of the time) and a file browser and VLC to play anything else.  She knows how to use these tools already, so it's not frustrating to her if there's any issue.  

Add a wireless mouse and a minimum font size and you're good to go from the couch.

Forget about Netflix on Linux, don't even bother. They don't want your business.

You bring up some valid points. I guess my referencing G3 and Unity is the simple fact that, well... sit back and look at those interfaces. They're beautiful. I mean, Gnome 2.X from Ubuntu 10.04 isn't the most attractive thing to look at if you're wanting to show off some pictures at your family reunion on the big screen. I know that sounds tacky and relatively stupid but G3 and Unity are at least more presentable, eye appealing environments for being on a large screen.

I didn't even realize what I said about Netflix until you posted back here. But yeah, Netflix sure doesn't give a damn about Linux users, or any of their customers for that matter. I sure won't lose any sleep by pretending they don't exist... especially since several other fine alternatives exist. :)

Thanks for the insight guys. I'm going to fire up an install of 11.10 and see how things go. :guitar:

---

### Post by thatguruguy on 2011-10-12
You may want to look into NaviX, which is an add-on to XBMC.  It has some good streaming options available.  And Mythbuntu has some streaming ability available, but I use XBMC + NaviX for most of the streaming stuff I do.

Plus, I have Hulu Desktop installed as well on my Mythbox.

As far as streaming from Amazon (or, eventually, Netflix), I'm fairly certain that can be set up within either a MythTV or XBMC session, but I really just haven't gotten around to setting it up, yet.

---

### Post by Roasted on 2011-10-12
> **thatguruguy said:**
> You may want to look into NaviX, which is an add-on to XBMC.  It has some good streaming options available.  And Mythbuntu has some streaming ability available, but I use XBMC + NaviX for most of the streaming stuff I do.

Plus, I have Hulu Desktop installed as well on my Mythbox.

As far as streaming from Amazon (or, eventually, Netflix), I'm fairly certain that can be set up within either a MythTV or XBMC session, but I really just haven't gotten around to setting it up, yet.

Maybe what I'll do is plan on using Gnome Shell with XBMC being an easily launchable option. If add-ons come available to make it happen, then great. If not, it's still a win win. :D

---

### Post by nickleboyblue on 2011-10-14
Boxee DOES do limited streaming, but I use it mainly for youtube and other random video browsing.  For actual entertainment, I use Hulu Desktop, which lets you watch a lot for free but charges for premium content.  It's a cheap fee to pay, especially compared to what your girlfriend pays for cable (she's getting very ripped off).  I would suggest, like it's been said a couple of times here, that you use a mythubuntu installation and simply add buttons into the menu for Hulu Desktop, XBMC, Boxee, and anything else you can think of that she would want to use.  The advantages of Boxee and MythTV are that Android has apps for controlling them through wifi, so she could use an android cell phone to control the system.

I do suggest that for audio, you use an external sound system that has it's own remote or is controlled by a universal remote.  Boxee in Ubuntu doesn't have good controls for volume, and the volume setting inside of mythtv effects the volume in everything else.  Having a separate audio system would let you set the software volume all the way up and control the volume itself from one place.

Just because there is much to choose from doesn't mean you need make only one choice.  You can have a lot of those systems happily coexisting on the same computer for as long as you need them to.

---

### Post by ninjaaron on 2011-10-14
[IMG]http://boards.theflood.us/cb/src/131413477193.jpg[/IMG]

Sorry.  Just had to get it out of my system.  Please continue your discussion about technology.

---

### Post by aeiah on 2011-10-14
if she's paying that much for cable then just buy a boxee box where you have all these nice streaming apps.

or you could use xbmc and a manual/automatic torrent method to acquire tv shows. xbmc does have a few streaming apps, but i think hulu and netflix is an in-browser solution

---

### Post by Roasted on 2011-10-14
> **nickleboyblue said:**
> Boxee DOES do limited streaming, but I use it mainly for youtube and other random video browsing.  For actual entertainment, I use Hulu Desktop, which lets you watch a lot for free but charges for premium content.  It's a cheap fee to pay, especially compared to what your girlfriend pays for cable (she's getting very ripped off).  I would suggest, like it's been said a couple of times here, that you use a mythubuntu installation and simply add buttons into the menu for Hulu Desktop, XBMC, Boxee, and anything else you can think of that she would want to use.  The advantages of Boxee and MythTV are that Android has apps for controlling them through wifi, so she could use an android cell phone to control the system.

I do suggest that for audio, you use an external sound system that has it's own remote or is controlled by a universal remote.  Boxee in Ubuntu doesn't have good controls for volume, and the volume setting inside of mythtv effects the volume in everything else.  Having a separate audio system would let you set the software volume all the way up and control the volume itself from one place.

Just because there is much to choose from doesn't mean you need make only one choice.  You can have a lot of those systems happily coexisting on the same computer for as long as you need them to.

Very good point. Especially if I'm using a standard install of Ubuntu I can dump countless other items on top of that installation too to see what I like most.

I'm just trying to generate as much discussion as possible so I can learn more about it. I mean, I started an Amazon streaming subscription last night (free 1 month trial) but almost everything I found that I would want to watch costs money. I thought this was free unlimited in conjunction with the 79/year cost? Unless I'm just restricted because it's a monthly trial... *shrug*

That being said, does Mythbuntu handle streaming better than say Boxee? I've seen XBMC and I've seen Boxee. I know what they're capable of and I certainly know what they're not capable of in terms of streaming integration. As of now, both XBMC and Boxee aren't on my radar, and I plan to just use a standard installation of 11.10 and use probably Gnome Shell and use the browser to stream through. If Mythbuntu offers more modular integration features for streaming services I'll certainly give it a whirl.

---

### Post by aeiah on 2011-10-14
mythbuntu is an ubuntu distro that uses mythtv. mythtv is really a PVR, and is designed to work with tv signals you receive in a normal way. it may be able to stream but its probably the weaker of the three

boxee is designed with streaming in mind, but is apparently out-dated on everything except the boxeebox. its built upon xbmc

xmbc is really designed for viewing offline content (which could be acquired online...), but there are some plugins for streaming content. i use one for streaming live uk tv. there are hulu and netflicks hacks for it, but i think they involve launching a web browser instance, and as far as i know, this only works in windows.

if you can acquire the tv shows you want, xbmc will do a great job of organising them for you, pulling metadata etc. same goes for movies and music.

oh, there's also some hardware solutions (other than the boxeebox) such as popcorn hour, but that involves extra cost of course (+ probably a subscription).

---

