---
title: "March Madness--Linux not suppported, OSX Is"
date: 2009-03-20
forum: The Cafe
---

### Post by sports fan Matt on 2009-03-20
Interesting just as last year, you need that plugin for silverlight to stream March madness on a linux player.  I never did have success even last year getting it to work, so I watched it on regular tv.

---

### Post by simtaalo on 2009-03-20
[http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight) open-source implmentation of silverlight

---

### Post by sports fan Matt on 2009-03-20
I'll give it a shot...thanks for the link...

---

### Post by sports fan Matt on 2009-03-20
Unsupported platform

Your current platform does not support the video plugins necessary to view NCAA® March Madness® on Demand.

You will need to switch to a supported platform in order to continue.

Standard Video Player Platform Requirements

    * Microsoft Windows XP/Vista
    * Microsoft Internet Explorer 6 or above
    * Microsoft Windows Media Player 9 or above

High Quality Video Player Platform Requirements

    * Microsoft Silverlight 2 (Click here to view system requirements)

Click here to return to the NCAA® March Madness® on Demand home page

I wonder what plugins would be needed...

---

### Post by wolfen69 on 2009-03-20
> **sox fan Matt said:**
> 
I wonder what plugins would be needed...

it won't work without windows media player, and silverlight2. you could always install windows in virtualbox.

---

### Post by sports fan Matt on 2009-03-20
I knew that, its just sad that (since apparently we're like a cousin to the mac, more isnt done both in market share and development towards getting things firstly regonized that people do you a linux box and then take the steps to intregrete a way for content to work..that would be my wish

---

### Post by Playa1313 on 2009-03-20
Yeah, unfortunately Moonlight is version 1.X when the NCAA website requires 2.0.  I can guarantee Microsoft/Apple had a say in this with the NCAA.

---

### Post by sports fan Matt on 2009-03-20
On the other hand I can view audio streams I couldnt before...

---

### Post by directhex on 2009-03-20
The Moonlight team are specifically working on this site. It *will* be supported, the only question is when

---

### Post by Giant Speck on 2009-03-20
*GASP!*

March Madness must hate Linux!

:lolflag:

---

### Post by bakedbeans4life on 2009-03-20
> **directhex said:**
> The Moonlight team are specifically working on this site. It *will* be supported, the only question is when

Adobe is bad enough, but at the very least they provide a native 64bit Flash plugin for Firefox on Linux (beta as it is).

I always remove Mono and all traces from my system (I am very thorough). If it is of no use, why include it? 

The excuse of "....the only question is when" doesn't wash with me, sorry.

Support of Mono on any other platform will always be secondary to pushing the native Windows alternative.

---

### Post by directhex on 2009-03-20
> **bakedbeans4life said:**
> Adobe is bad enough, but at the very least they provide a native 64bit Flash plugin for Firefox on Linux (beta as it is).

How is this comparison sensible? Ubuntu contains Moonlight packages for i386, AMD64, SPARC, PowerPC, IA64, and ARM. The official upstream .xpi has been available for i386 AND AMD64 since day one.

> I always remove Mono and all traces from my system (I am very thorough). If it is of no use, why include it? 

You're changing the topic. Can you understand that Moonlight and Mono are not the same thing? Especially at this moment in time, where Moonlight 1.0 is pure C++? What does Moonlight's extremely short development lifetime have to do with Mono applications like Tomboy or F-Spot? You're removing Mono because you can't access some sporting event website using Moonlight? Know what "non sequitur" means?

> The excuse of "....the only question is when" doesn't wash with me, sorry.

But you're citing ***ADOBE*** as a better option? Look up the history of Flash 8 for Linux, then come back.

> Support of Mono on any other platform will always be secondary to pushing the native Windows alternative.

Support by whom?

---

### Post by directhex on 2009-03-20
```
#moonlight.20.log-20-03-2009 16:53:09 < jackson!~jackson@ip98-183-229-99.hr.hr.cox.net: tethridge, i bet we'll have it working before the tournament is over, but it'll require using svn
```

In case anyone cares

---

### Post by bash on 2009-03-20
On the topic of Moonlight 2: Is there any (more or less detailed) schedule around when it might be ready/done?

And more general: I don't have anything against Mono. I sometimes find the whole hate against it a bit strange. I personally quite enjoy Banshee for example. And as for Moonlight: In the short time that thing has been around it seem a lot greater from a open-source point of view. The Linux client is open-source, available for most architectures and is written by "Linux" people for Linux using "Linux" technology (For example proper GTK+ interface). That in my opinion is a lot more than you can say about Adobe  Flashplayer "What-80%-CPU-usage-are-too-much?!" 10.

---

### Post by geoken on 2009-03-20
> **directhex said:**
> 
But you're citing ***ADOBE*** as a better option? Look up the history of Flash 8 for Linux, then come back.



Is that the best you can do? MS is on Silverlight 3 and Linux is barely on 1. Conversely, flash 8 was a negligible release. It offered little new features and most major sites (ie. YouTube) continued serving Flash 7 content. Also, their lapse is at least excusable as Flash 8 came out only a few months before Macromedia was bought out by Adobe.

> **directhex said:**
> 
Support by whom?


By Microsoft. They're supposedly offering some aid to the Moonlight team so they're obviously aware of the current state of Moonlight. When they send their techs to build these Silverlight powered sites it's well within their means to either support or exclude moonlight.

---

### Post by directhex on 2009-03-20
> **bash said:**
> On the topic of Moonlight 2: Is there any (more or less detailed) schedule around when it might be ready/done?

Officially, Moonlight releases are marked on the Mono roadmap. The first Moon 2.0 alpha release is scheduled alongside Mono 2.6, in September. The beta is marked for release alongside Mono 2.8 (which is still TBA).

September means a reasonable chance of packaging for Karmic (depending on the whims of the MOTU-Release team).

And before anyone asks, the gap between 1.0 and 2.0 is MUCH larger than the gap between 2.0 and 3.0, so once 2.0 support is nailed down, moving to 3.0 won't take as long or be as difficult.

---

### Post by geoken on 2009-03-20
> **directhex said:**
> 

And before anyone asks, the gap between 1.0 and 2.0 is MUCH larger than the gap between 2.0 and 3.0, so once 2.0 support is nailed down, moving to 3.0 won't take as long or be as difficult.

3D support, running out of the browser, an entirely new video codec, hardware acceleration; it seems like the jump from 2 to 3 is a lot more substantial than 1 - 2.

---

### Post by directhex on 2009-03-20
> **geoken said:**
> 3D support, running out of the browser, an entirely new video codec, hardware acceleration; it seems like the jump from 2 to 3 is a lot more substantial than 1 - 2.

3D support could be interesting. Time will tell.

Out-of-the-browser? Already works TODAY in 1.0.1.

New codec? At worst, a new demuxer. NOT a lot of work.

Hardware acceleration? Stubs exist in the right places already.

So no, I'd disagree with your assessment - I think creating a sandboxed JITter and class library from scratch is a bigger task than renaming "mopen1" to "mopen3"

> **geoken said:**
> Is that the best you can do? MS is on Silverlight 3 and Linux is barely on 1. Conversely, flash 8 was a negligible release. It offered little new features and most major sites (ie. YouTube) continued serving Flash 7 content. Also, their lapse is at least excusable as Flash 8 came out only a few months before Macromedia was bought out by Adobe.

Who said anything about "best"? It's an example. Your "excusable" lapse by the way is from between the release of Flash 8 for Windows (which DID cause several sites to become 8-only) in August 2005, to Flash 9 beta on Linux in January 2007. 17 months of gap. If that's "excusable", how about extending the same courtesy to Moonlight, which has only EXISTED for that length of time? The stable release of Silverlight 2.0 was in October 2008 - 5 months ago. Do the Moonlight team get the same courtesies you afford Macradobe when it comes to taking actual time to develop things?


> By Microsoft. They're supposedly offering some aid to the Moonlight team so they're obviously aware of the current state of Moonlight. When they send their techs to build these Silverlight powered sites it's well within their means to either support or exclude moonlight.

Yep. They can say "write your site in Javascript" and it'll work in Moonlight - the way they specifically did for the official Obama Inauguration stream. Or they can say "write your site in whatever .NET language you like" and it'll not work in Moonlight for a few more months. All comes down to how much you like Javascript really.

---

### Post by Glucklich on 2009-03-21
Yesterday and the day before, I could see the matches on Totem. Without sound but no problem. At least, I'm watching it. Today, it appears that Moonlight is required... this is surreal. It's not that they couldn't support Linux, it's that they don't want to. It's that simple. Lot's of televisions use a MMS code that can be viewed on the majority of the players. Some even just stream it with flash (with great quality, might I add).

Edit: By the way, I bet on UNC to go all the way!

---

### Post by geoken on 2009-03-21
> **directhex said:**
> 



Who said anything about "best"? It's an example. Your "excusable" lapse by the way is from between the release of Flash 8 for Windows (which DID cause several sites to become 8-only) in August 2005, to Flash 9 beta on Linux in January 2007. 17 months of gap. If that's "excusable", how about extending the same courtesy to Moonlight, which has only EXISTED for that length of time? The stable release of Silverlight 2.0 was in October 2008 - 5 months ago. Do the Moonlight team get the same courtesies you afford Macradobe when it comes to taking actual time to develop things?

Give me a reason to extend that courtesy. I gave you a pretty valid reason for Flash 8 (the fact that the company who made it was bought out), so give me a reason for the Silverlight/Moonlight lapse. Considering MS is already highly suspect when it comes to creating a standard and ensuring said standard is slightly more advanced in it's Windows implementation, I would need to here some valid reasoning for this.

For the record it was actually October '06 that the public beta was out. Jan was when the final version was released.

---

### Post by Glucklich on 2009-03-21
> **geoken said:**
> Give me a reason to extend that courtesy. I gave you a pretty valid reason for Flash 8 (the fact that the company who made it was bought out), so give me a reason for the Silverlight/Moonlight lapse. Considering MS is already highly suspect when it comes to creating a standard and ensuring said standard is slightly more advanced in it's Windows implementation, I would need to here some valid reasoning for this.

For the record it was actually October '06 that the public beta was out. Jan was when the final version was released.

Look, I like flash. I have no problem at all with flash. Flash actually does it's job, unlike Moonlight. But... the Basketball games aren't being transmitted on Flash. And I really wanted to watch them. Is there any way to go around this? Since Moonlight on the system has the version 2.2, and the Firefox plugin only to 1.0, how can I get the link of the transmission to see if Totem plays it? Or... how can I link Firefox to play it on Totem, without showing me that sticker that says "Silverlight needed"?

---

### Post by Glucklich on 2009-03-21
I got it!

Maryland @ Memphis:
mms://a2047.l6924361996.c69243.g.lm.akamaistream.net/D/2047/69243/v0001/reflector:10017?auth=daEbcabaCaod7aJc7aZaXd9azaTdFdOdJdc-bjXuT9-c0-NK2vDxqei9n

A&E @ Uconn:
mms://a2047.l6924361996.c69243.g.lm.akamaistream.net/D/2047/69243/v0001/reflector:12533?auth=daEardecVbMdsccceajcgdXa7dsaocZaxb8-bjXuVs-c0-SN5xCyuehbk

Select the "Open Location" option on Totem. No sound but better than nothing. Maybe we can get sound on the CBS site.

---

### Post by phaed on 2009-03-21
I've been trying to solve this problem, too.  Installed IEs4Linux (IE 6) since the NCAA site says it's supported, but that didn't work either.

Somebody said the Moonlight develoers are specifically working on this site so it will be supported, the question is when.  When the tournament is over, of course. :)

---

### Post by wmcbrine on 2009-03-21
> **Glucklich said:**
> I got it!Can you tell us how to find these URLs? And/or the URLs for the current games now?

I got it to play under VirtualBox, but that leaves something to be desired.

---

### Post by Glucklich on 2009-03-21
Sure. I don't know if you have Adblock on Firefox but if you don't, install it. Even if you're not planing on using. Although, I think it's a cool tool. Then, go to [http://www.atdhe.net/](http://www.atdhe.net/) (it's not illegal since they only pick up streams going on somewhere else like Justin.tv, UStream, etc.) All matches are listed there, plus another sporting events around the globe. Pretty cool, hmm? Right. It will pop up a window, that says pretty much what the CBS Sports site says but... Click on the right button of your mouse and on "Block Frame" (or something like that, I'm using Portuguese). Then on the last box you'll have a personalized adress, copy only the part since "mms" because, that's what you can play on Totem. Then, go on Totem, "Open Location" paste the link you got from Adblock and enjoy. Like I said, no sound... but I actually enjoy listening to music and watching the ball game. North Carolina is being a great match. High-scoring, as always. GO UNC (a.k.a. don't blow my bracket)!!!

---

### Post by coolbrook on 2009-03-21
Maybe next year.

---

### Post by Glucklich on 2009-03-27
"Moonlight developers are specifically working on this site." Riiight. Yesterday, I could watch the games on Totem. Now, even with my workaround we can't watch it. Looks like, they made an auth system for Silverlight. And you want me to believe that Novell employees are working on this? Yeeeah, they even must be loosing their sleep because this. F*ckin' Microsoft, messing with my basketball games.

---

### Post by directhex on 2009-03-28
> **Glucklich said:**
> "Moonlight developers are specifically working on this site." Riiight. Yesterday, I could watch the games on Totem. Now, even with my workaround we can't watch it. Looks like, they made an auth system for Silverlight. And you want me to believe that Novell employees are working on this? Yeeeah, they even must be loosing their sleep because this. F*ckin' Microsoft, messing with my basketball games.

```
root@osc-franzibald:/var/log/bip/directhex/gimpnet/2009-03# grep ncaa \#moonlight.*.log
#moonlight.04.log:04-03-2009 19:10:32 < jackson!~jackson@ip98-183-229-99.hr.hr.cox.net: http://all-access.cbssports.com/player.html?code=ncaa
#moonlight.04.log:04-03-2009 20:23:15 < jackson!~jackson@ip98-183-229-99.hr.hr.cox.net: "System.InvalidOperationException: Element is a child of another element", that's what i get with the ncaa site
#moonlight.09.log:09-03-2009 01:48:12 < kangaroo!~plasma@ns1.sublimeintervention.com: how far is ncaa?
#moonlight.09.log:09-03-2009 05:20:32 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: ncaa
#moonlight.09.log:09-03-2009 05:23:53 < kangaroo!~plasma@ns1.sublimeintervention.com: yeah ncaa is like 1mb of code
#moonlight.10.log:10-03-2009 18:06:34 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: toshok_: can you try http://all-access.cbssports.com/player.html?code=ncaa again
#moonlight.10.log:10-03-2009 18:11:40 < toshok_!~toshok@adsl-75-36-188-121.dsl.pltn13.sbcglobal.net: lewing: ncaa looks the same as it did a couple days ago
#moonlight.13.log:13-03-2009 16:07:32 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: ncaa gets some data now
#moonlight.13.log:13-03-2009 16:10:34 < kangaroo!~plasma@ns1.sublimeintervention.com: oh you meant ncaa?
#moonlight.13.log:13-03-2009 16:10:41 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: ok ncaa was playing but it ran out of memory
#moonlight.13.log:13-03-2009 16:11:52 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: http://all-access.cbssports.com/player.html?code=ncaa
#moonlight.13.log:13-03-2009 16:56:08 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: toshok: ncaa has started to sort of play things and smoohthd is working for kang and olympics is seeming very close
#moonlight.13.log:13-03-2009 16:57:09 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: building now.  is more control content showing up for ncaa?
#moonlight.13.log:13-03-2009 16:57:20 < kangaroo!~plasma@ns1.sublimeintervention.com: ncaa did weird weird things for me
#moonlight.13.log:13-03-2009 16:57:38 < kangaroo!~plasma@ns1.sublimeintervention.com: I think if we combine larry and my laptops into a frankentop we'd have ncaa and smoothhd perfect
#moonlight.13.log:13-03-2009 16:59:12 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: ncaa also takes like 5 minutes to load
#moonlight.13.log:13-03-2009 18:20:04 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: man ncaa spews a lot of ArgumentExceptions
#moonlight.13.log:13-03-2009 18:27:41 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: lewing: yeah, re: ncaa we need to figure out what's throwing those and if it's our fault
#moonlight.13.log:13-03-2009 20:01:39 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: ncaa just throws a **** ton of exceptions
#moonlight.13.log:13-03-2009 20:46:50 < kangaroo!~plasma@sublimeintervention.com: ok ncaa is better, but crashing int he gc now
#moonlight.13.log:13-03-2009 20:52:07 < kangaroo!~plasma@sublimeintervention.com: toshok: ncaa
#moonlight.14.log:14-03-2009 01:42:16 < kangaroo!~plasma@sublimeintervention.com: anyone been working on ncaa?
#moonlight.14.log:14-03-2009 01:42:19 < kangaroo!~plasma@sublimeintervention.com: (the new ncaa?
#moonlight.17.log:17-03-2009 03:03:18 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: i think i have richtextbox to the same point as ncaa (with the parser namescope thing)
#moonlight.17.log:17-03-2009 03:03:39 < kangaroo!~plasma@sublimeintervention.com: wait ncaa has a parser namescope thing too?
#moonlight.18.log:18-03-2009 18:03:54 < kangaroo!~plasma@sublimeintervention.com: firefox http://mmod.ncaa.com/video/hq 
#moonlight.19.log:19-03-2009 00:39:32 < kangaroo!~plasma@sublimeintervention.com: playboy seems to be crashing the same was as ncaa here
#moonlight.19.log:19-03-2009 17:10:48 < rusty!~rhowell@rus.provo.novell.com: I thought ncaa.com was _sort of_ working 
#moonlight.19.log:19-03-2009 17:18:45 < kangaroo!~plasma@sublimeintervention.com: toshok: ncaa? I'm working on it now
#moonlight.19.log:19-03-2009 17:18:52 < toshok!~toshok@66.116.112.2: nah, not ncaa
#moonlight.19.log:19-03-2009 17:21:11 < rusty!~rhowell@rus.provo.novell.com: does ncaa.com work for anyone else?
#moonlight.19.log:19-03-2009 17:21:19 < kangaroo!~plasma@sublimeintervention.com: rusty: thats the problem with ncaa
#moonlight.19.log:19-03-2009 17:32:13 < kangaroo!~plasma@sublimeintervention.com: nah I just realized I have site-specific branches for hardrock, playboy, ncaa, etc
#moonlight.20.log:20-03-2009 16:32:48 < tethridge!~tale@zswa01cs005-da01.atlanta.hp.com: Hello all, I'm trying to view the ncaa games on youtube.  They require silverlight.  I have moonlight installed and I even installed an agent switcher so that firefox would report that I'm on Vista running IE7.  It still won't work.  Can you guys get it to stream?
#moonlight.20.log:20-03-2009 16:58:31 < jackson!~jackson@ip98-183-229-99.hr.hr.cox.net: well it's really just an iframe to ncaa.com
#moonlight.23.log:23-03-2009 19:22:23 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: playboyarchive.com, once it's fixed, hardrock, ncaa
#moonlight.23.log:23-03-2009 19:23:02 < alan!~alan@89.100.117.96: ncaa keeps spinning threads until it dies. It doesn't appear to hit any of the binding issues it used to hit (with the current patch)
#moonlight.24.log:24-03-2009 16:46:39 < kangaroo!~plasma@sublimeintervention.com: for ncaa?
#moonlight.24.log:24-03-2009 16:52:00 < alan!~alan@195.75.240.248: kangaroo, With that applied, ncaa just keeps spinning threads until it dies
#moonlight.24.log:24-03-2009 17:34:11 < kangaroo!~plasma@sublimeintervention.com: so thats (I think) the core problem in ncaa
#moonlight.25.log:25-03-2009 03:16:19 < kangaroo!~plasma@sublimeintervention.com: http://all-access.cbssports.com/player.html?code=ncaa
#moonlight.25.log:25-03-2009 03:22:26 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com:  DownloaderRequest: http://all-access.cbssports.com/DataFeeds/LogEntry.ashx?ApplicationId=ncaa&feedId=0&ExceptionType=System.Reflection.TargetInvocationException&Exception=System.Reflection.TargetInvocationException:%20Exception%20has%20been%20thrown%20by%20the%20target%20of%20an%20invocation.%20---%3E%20System.IndexOutOfRangeException:%20Array%20index%20is%20out%20of%20range.%0A%20%20at%20CBSCS_SilverlightUI.VideoController.CreateRela
#moonlight.25.log:25-03-2009 03:38:21 < kangaroo!~plasma@sublimeintervention.com: 23:16 <@kangaroo> http://all-access.cbssports.com/player.html?code=ncaa
#moonlight.25.log:25-03-2009 03:53:10 < kangaroo!~plasma@sublimeintervention.com: firefox -d gdb http://mmod.ncaa.com/video/hq 
#moonlight.25.log:25-03-2009 03:53:14 < kangaroo!~plasma@sublimeintervention.com: thats the other ncaa site
#moonlight.25.log:25-03-2009 03:53:15 < shana!~zen@worldofcoding.com: <kangaroo> http://all-access.cbssports.com/player.html?code=ncaa
#moonlight.25.log:25-03-2009 03:53:56 < kangaroo!~plasma@sublimeintervention.com: 23:53 <@kangaroo> firefox -d gdb http://mmod.ncaa.com/video/hq 
#moonlight.25.log:25-03-2009 04:02:57 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: also, we are still throwing a jillion NRE's loading ncaa
#moonlight.25.log:25-03-2009 04:05:34 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: oh those CWL's are coming from ncaa?
#moonlight.25.log:25-03-2009 04:06:14 < kangaroo!~plasma@sublimeintervention.com: the ui never comes up on that ncaa
#moonlight.25.log:25-03-2009 05:09:05 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: DownloaderRequest: http://all-access.cbssports.com/DataFeeds/LogEntry.ashx?ApplicationId=ncaa&feedId=0&ExceptionType=System.Reflection.TargetInvocationException&Exception=System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---%3E System.IndexOutOfRangeException: Array index is out of range.
#moonlight.25.log:25-03-2009 10:42:58 < alan!~alan@195.75.240.248: woo! ncaa doesn't spin up 1,000,000 threads anymore, but it locks up on startup :)
#moonlight.25.log:25-03-2009 11:50:05 < alan!~alan@195.75.240.248: Basically ncaa is dying because it's bundling some libs and we're loading the microsoft version of System.Xml.Linq.XDocument and it's going into an infinite loop
#moonlight.25.log:25-03-2009 15:13:59 < alan!~alan@195.75.240.248: Now tell me why ncaa is entering an infinite loop ;)
#moonlight.25.log:25-03-2009 19:05:49 < kangaroo!~plasma@sublimeintervention.com: jeff_: cbssports ncaa shows some text parsing problems
#moonlight.25.log:25-03-2009 19:25:23 < alan!~alan@195.75.240.248: It's quite possible it's the same issue, i managed to narrow it down to Interlocked.CompareExchange not working right for ncaa
#moonlight.26.log:26-03-2009 10:12:29 < alan!~alan@195.75.240.248: i wonder if ncaa works now 
#moonlight.26.log:26-03-2009 10:12:38 < sde!~sde@202.140-245-81.adsl-dyn.isp.belgacom.be: what's ncaa
#moonlight.26.log:26-03-2009 10:13:27 < alan!~alan@195.75.240.248: http://mmod.ncaa.com/video/hq
#moonlight.26.log:26-03-2009 16:44:23 < kangaroo!~plasma@sublimeintervention.com: lewing: which? the vertigo ncaa or cbssports?
#moonlight.26.log:26-03-2009 16:44:33 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: http://mmod.ncaa.com/video/hq?ts=1238085739&t=8148974abc7765739b93ade5e416d914&w=90
#moonlight.26.log:26-03-2009 16:45:24 < kangaroo!~plasma@sublimeintervention.com: you're thinking of firefox http://all-access.cbssports.com/player.html?code=ncaa
#moonlight.26.log:26-03-2009 16:45:43 < kangaroo!~plasma@sublimeintervention.com: we've never rendered anything on http://mmod.ncaa.com/video/hq
#moonlight.26.log:26-03-2009 16:50:41 < kangaroo!~plasma@sublimeintervention.com: lewing: http://mmod.ncaa.com/video/hq is hitting scriptable problems?
#moonlight.26.log:26-03-2009 17:33:33 < kangaroo!~plasma@sublimeintervention.com: can anyone on mcs+mono+moon trunk load ncaa?
#moonlight.26.log:26-03-2009 17:49:51 < kangaroo!~plasma@sublimeintervention.com:  MOON_TRACE="M:System.Windows.Application:set_RootVisual" firefox http://mmod.ncaa.com/video/hq
#moonlight.26.log:26-03-2009 18:01:32 < kangaroo!~plasma@sublimeintervention.com: it works around the issue for ncaa for now tho so people can keep working
#moonlight.26.log:26-03-2009 18:01:41 < shana!~zen@worldofcoding.com: kangaroo: ncaa is the one crashing?
#moonlight.26.log:26-03-2009 18:02:12 < kangaroo!~plasma@sublimeintervention.com: toshok: I think we need to call it there if and only if we're in the case that ncaa is in
#moonlight.26.log:26-03-2009 18:03:01 < alan!~alan@195.75.240.248: ncaa is delaying instantiating its root visual until after it downloads a bunch of stuff
#moonlight.26.log:26-03-2009 18:03:19 < shana!~zen@worldofcoding.com: loading ncaa, right?
#moonlight.26.log:26-03-2009 18:03:21 < kangaroo!~plasma@sublimeintervention.com: toshok: ncaa is delay attaching the root visual
#moonlight.26.log:26-03-2009 18:06:42 < kangaroo!~plasma@sublimeintervention.com: shana: yes loading ncaa
#moonlight.26.log:26-03-2009 18:44:38 < kangaroo!~plasma@sublimeintervention.com: ncaa looks pretty nice once it comes up
#moonlight.26.log:26-03-2009 19:41:18 < shana!~zen@worldofcoding.com: how long does ncaa take to actually blow up?
#moonlight.26.log:26-03-2009 21:38:01 < shana!~zen@worldofcoding.com: kangaroo: http://shana.worldofcoding.com/files/ncaa.png
#moonlight.26.log:26-03-2009 22:00:25 < kangaroo!~plasma@sublimeintervention.com: shana: for ncaa?
#moonlight.26.log:26-03-2009 22:11:13 > directhex: ncaa?
#moonlight.26.log:26-03-2009 22:24:43 < toshok!~toshok@adsl-75-36-187-18.dsl.pltn13.sbcglobal.net: which ncaa site is the one using the funky set_RootVisual behavior?
#moonlight.26.log:26-03-2009 22:26:25 < lewing!~lewing@cpe-24-27-37-14.austin.res.rr.com: toshok: http://mmod.ncaa.com/video/hq?debug=32&ts=1238106372&t=65ae414fd2b5c3a4b60f639696b20374&w=90
#moonlight.26.log:26-03-2009 22:31:21 < kangaroo!~plasma@sublimeintervention.com: http://mmod.ncaa.com/video/hq
#moonlight.26.log:26-03-2009 22:37:52 < shana!~zen@worldofcoding.com: toshok: I see this: http://shana.worldofcoding.com/files/ncaa.png
#moonlight.27.log:27-03-2009 10:19:43 < alan!~alan@195.75.240.248: wow, i saw ncaa for about 0.6312 seconds before it crashed
#moonlight.27.log:27-03-2009 11:05:14 < alan_!~alan@195.75.240.248: the latest moon, comment out line 1248 in plugin.cpp (NPN_ReleaseVariantValue (&npresult);) and then run ncaa
#moonlight.27.log:27-03-2009 11:05:21 < alan_!~alan@195.75.240.248: http://mmod.ncaa.com/video/hq
#moonlight.27.log:27-03-2009 14:16:29 < shana!~zen@worldofcoding.com:  you can drop the ncaa "fix" guys, official fix is in
```

Yes, I want you to believe that Novell employees are working on this.

---

### Post by Glucklich on 2009-03-28
That's some funny stuff. 

> playboy seems to be crashing the same was as ncaa here

Epic!

---

### Post by directhex on 2009-03-28
> **Glucklich said:**
> That's some funny stuff. 



Epic!

Playboy recently uploaded all back-issues here: [http://playboy.covertocover.com/](http://playboy.covertocover.com/)

It's a decent SL2 test site, and uses DeepZoom extensively

---

### Post by Glucklich on 2009-03-28
> **directhex said:**
> Playboy recently uploaded all back-issues here: [http://playboy.covertocover.com/](http://playboy.covertocover.com/)

It's a decent SL2 test site, and uses DeepZoom extensively

Didn't knew about that. But how to get past by the initial page that says that Silverlight is required?

But still, that doesn't explain why the NCAA was viewable with Totem the other day and yesterday wasn't.

---

### Post by MikeTheC on 2009-03-28
Is this "March Madness" thing all that important? What, are you like trying to buy something from a company that snubs your OS platform of choice?

Remember: if you're going to do business with them, you're supporting them, which means you're essentially "casting a vote" for not just what they sell, but how they function as a business. If you feel this strongly, you probably shouldn't support them...

---

### Post by directhex on 2009-03-28
> **Glucklich said:**
> Didn't knew about that. But how to get past by the initial page that says that Silverlight is required?

Well, much like NCAA - you need to be using a browser which identifies itself as having Silverlight 2.0 installed (e.g. Moonlight from SVN). That's the point - the Novell folks are using it as a test site for their current work adding SL2 support to Moonlight.

> But still, that doesn't explain why the NCAA was viewable with Totem the other day and yesterday wasn't.

You'd need to ask the NCAA people about that - nothing to do with Novell or Moonlight

---

### Post by Glucklich on 2009-03-28
> **MikeTheC said:**
> Is this "March Madness" thing all that important? What, are you like trying to buy something from a company that snubs your OS platform of choice?

Remember: if you're going to do business with them, you're supporting them, which means you're essentially "casting a vote" for not just what they sell, but how they function as a business. If you feel this strongly, you probably shouldn't support them...

You have no idea of what "March Madness" is, do you? The question is that it's not a product. It is the college basketball competition. So, obviously, it is important if you are a basketball fan. These are probably, the most intense matches you can watch on television. And supposedly, it's a free broadcast on-demand made by CBS Sports. NCAA has nothing to do with it.

---

### Post by MikeTheC on 2009-03-28
> **Glucklich said:**
> You have no idea of what "March Madness" is, do you? The question is that it's not a product. It is the college basketball competition. So, obviously, it is important if you are a basketball fan. These are probably, the most intense matches you can watch on television. And supposedly, it's a free broadcast on-demand made by CBS Sports. NCAA has nothing to do with it.

Oh. No, I had no idea what it was. Never heard of it before (well, at least, not in *that* context.) Thanks for the clarification.

However, much of what I said still stands. If you go to the trouble to access their content *as provided* then you are as much as voting *for* how it is provided. The most effective way I know to change any organization's behavior, in addition to complaining, is to stop doing business. If they see their traffic level drop (which, at this point, really isn't likely given the OS platforms which *are* supported) they'll want to do something about it.

---

### Post by Glucklich on 2009-03-28
> **MikeTheC said:**
> Oh. No, I had no idea what it was. Never heard of it before (well, at least, not in *that* context.) Thanks for the clarification.

However, much of what I said still stands. If you go to the trouble to access their content *as provided* then you are as much as voting *for* how it is provided. The most effective way I know to change any organization's behavior, in addition to complaining, is to stop doing business. If they see their traffic level drop (which, at this point, really isn't likely given the OS platforms which *are* supported) they'll want to do something about it.

Yeah, that's the thing. Linux users traffic is not big enough to make any kind of affirmation. Most of the people that I talk to about basketball, are not computer enthusiasts. Well, I cannot consider myself one either. Honestly, I just got fed up with Windows. At this point all our hopes lie on the Novell team. Maybe next year... or the next one (judging by the rate of the posts and the few advances made). Hoops fans will have to swallow this one.

---

### Post by MikeTheC on 2009-03-28
Then, with respect, I suggest we need to pick our battles carefully. Be strategic.

Of course, for me, this is easily enough done. I'm not into sports, so *not* watching this March Madness game is essentially a non-event. I was not going to be watching it anyhow (as no doubt you were able to deduce from my initial comments), and so I'll now help show solidarity for your "side," as it were, and *not* watch it even more. Who knows, maybe the suction generated by the void in the universe I'm about to generate (kind of like dividing by zero -- don't try *that* at home!) will help shift them.

You never know. Keep fingers crossed, though! ;)

---

