---
title: "Gwibber is really cool."
date: 2010-04-30
forum: The Cafe
---

### Post by swoll1980 on 2010-04-30
I don't really use Facebook very much, but Gwibber is great. I can check messages, and publish with one click. Great job Gwibber!

---

### Post by TheNerdAL on 2010-04-30
I love Gwibber, I just wish they had MySpace support because I use that mostly.

---

### Post by markp1989 on 2010-04-30
agreed , it rocks. 

only complaint i have with it is that when i tried to install it on my arch+openbox machine it wanted to install pretty much all of gnome along with it.

---

### Post by Foster Grant on 2010-04-30
I'd like to see Twitter's lists feature supported, along with the ability to block and report Twitter spammers.

---

### Post by chriswyatt on 2010-04-30
Gwibber rocks my socks off.

:guitar:

---

### Post by tica vun on 2010-04-30
Thank you for pointing out this wonderful application, announcing my bowel movements to the world on seven networks simultaneously is now much less of an effort. Still waiting for webcam support though, now that would be a real breakthrough in the twitter ****ter movement.

---

### Post by swoll1980 on 2010-04-30
> **tica vun said:**
> Thank you for pointing out this wonderful application, announcing my bowel movements to the world on seven networks simultaneously is now much less of an effort. Still waiting for webcam support though, now that would be a real breakthrough in the twitter ****ter movement.

Is this sarcasm, or no. It's hard to tell.

---

### Post by TheNessus on 2010-04-30
Gwibber is bloat. 

I removed it, and its CouchDesktop dependencies, freed HALF the ram used by Lucid.

---

### Post by mamamia88 on 2010-04-30
facebook doesn't even work on it for me.  twitter works fine though

---

### Post by swoll1980 on 2010-04-30
> **TheNessus said:**
> Gwibber is bloat. 

I removed it, and its CouchDesktop dependencies, freed HALF the ram used by Lucid.

There are plenty of Linux distros that target outdated hardware, luckily Ubuntu isn't one of them.

---

### Post by swoll1980 on 2010-04-30
> **mamamia88 said:**
> facebook doesn't even work on it for me.  twitter works fine though

You have to add, and authorize it.

---

### Post by bash on 2010-04-30
> **Foster Grant said:**
> I'd like to see Twitter's lists feature supported, along with the ability to block and report Twitter spammers.

At least twitter lists are supposed to come with the next version:

> I have already started to assemble a roadmap for Gwibber 3.0. The next version will likely add support for Buzz and Reddit. Some services that were supported in earlier versions will be making a comeback, including Ping.fm, RSS, and BrightKite.

Other significant features on the roadmap include support for new-style retweets, improved direct message handling, Twitter lists, Facebook filters, more comprehensive inline media previews, better scrolling behavior, nickname autocompletion, and unread message notification in the sidebar. Several of these features are already implemented in experimental branches and will arrive in the nightly builds soon.

Source: [http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/](http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/)

---

### Post by mamamia88 on 2010-04-30
> **swoll1980 said:**
> You have to add, and authorize it.

i tried that just freezes up

---

### Post by swoll1980 on 2010-04-30
> **mamamia88 said:**
> i tried that just freezes up

Huh, it works great for me. I wonder what could be wrong. Does Facebook have different servers for different countries? Are you in the US?

---

### Post by mamamia88 on 2010-04-30
yeah i'm from the united states

---

### Post by Foster Grant on 2010-04-30
Another problem I discovered: When Gwibber checks accounts for new posts it absolutely floors the throttle on my dual-core CPU. Raises the processor temperature about 20°F to above 140°F because it's so processor-intensive. It pretty much maxes out my broadband connection, too.

So, to disagree with the thread title, Gwibber's not that cool. In fact, it's kinda hot.

Bug report time.

---

### Post by Foster Grant on 2010-04-30
> **TheNessus said:**
> Gwibber is bloat. 

I removed it, and its CouchDesktop dependencies, freed HALF the ram used by Lucid.

Apparently the problem isn't CouchDB, but rather WebKit:

[quote=Ryan Paul on Launchpad]WebKit is largely responsible for Gwibber's excessive memory consumption right now. The problem is that the default caching behavior used in the GTK+ WebKit port is intended for web browsers and not applications like Gwibber. This is a problem that needs to be addressed upstream. The relevant bug to follow there is this one: [https://bugs.webkit.org/show_bug.cgi?id=24001](https://bugs.webkit.org/show_bug.cgi?id=24001) I'm going to experiment with some of the patches attached to that bug. If those fixes significantly improve Gwibber's memory footprint, I'm going to talk to some people and see if we can get them applied sooner rather than later.

I'm tackling other resource consumption problems, too. The JavaScript method used to push messages into the content area in trunk is really ridiculously processor intensive. The new template-theme-engine branch almost entirely eliminates that problem.[/quote]

[https://bugs.launchpad.net/gwibber/+bug/306497/comments/10](https://bugs.launchpad.net/gwibber/+bug/306497/comments/10)

When it's idle and not checking accounts, it takes up just under 13 MiB of memory on my system. When it is checking accounts, I start getting ridiculous top stats like this:

>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
19012 ***       20   0  152m  16m 2500 S   17  0.9   0:01.86 gwibber-service    
19007 ***       20   0  128m  16m 2572 S   15  0.9   0:02.55 gwibber-service    
19003 ***       20   0  104m  16m 2572 S   13  0.9   0:02.74 gwibber-service    
18997 ***       20   0  104m  16m 2576 S   12  0.9   0:04.57 gwibber-service    
19013 ***       20   0  152m  16m 2612 S   11  0.9   0:01.27 gwibber-service    
19002 ***       20   0  104m  17m 2760 S   11  0.9   0:02.05 gwibber-service    
19017 ***       20   0  176m  16m 2500 S   11  0.9   0:01.06 gwibber-service    
19018 ***       20   0  176m  16m 2484 S   10  0.9   0:01.05 gwibber-service    


>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
19040 ***       20   0  202m  88m  25m R   64  4.7   0:16.24 gwibber            
 2073 ***       20   0 74220  16m 3144 S   47  0.9  23:37.28 beam.smp           
19157 ***       20   0  200m  16m 2572 S   17  0.9   0:03.12 gwibber-service    
19158 ***       20   0  200m  16m 2612 S   14  0.9   0:02.15 gwibber-service    


So it's Gwibber, Webkit and something called beam.smp that acts up whenever Gwibber is checking feeds.

---

### Post by mikkyd on 2010-05-01
> **swoll1980 said:**
> There are plenty of Linux distros that target outdated hardware, luckily Ubuntu isn't one of them.
Buying new hardware is not the answer to all problems. The problem here is that Gwibber kicks off lots of instances (19 in my case) of beam.smp, which use all the CPU.

This is also kicked off by Ubuntu One Prefs...
[http://ubuntuforums.org/showthread.php?t=1466931](http://ubuntuforums.org/showthread.php?t=1466931)

...and Evolution...
[http://ubuntuforums.org/showthread.php?t=1442925](http://ubuntuforums.org/showthread.php?t=1442925)

It seems that the solution is to kill Couch DB and sync your address book with another service. Or buy a new processor, obviously.

---

### Post by legolas_w on 2010-05-01
Does it use HTTPs to connect to twitter and facebook or it is plain http?

thanks

---

### Post by swoll1980 on 2010-05-01
> **mikkyd said:**
> Buying new hardware is not the answer to all problems. The problem here is that Gwibber kicks off lots of instances (19 in my case) of beam.smp, which use all the CPU.

This is also kicked off by Ubuntu One Prefs...
[http://ubuntuforums.org/showthread.php?t=1466931](http://ubuntuforums.org/showthread.php?t=1466931)

...and Evolution...
[http://ubuntuforums.org/showthread.php?t=1442925](http://ubuntuforums.org/showthread.php?t=1442925)

It seems that the solution is to kill Couch DB and sync your address book with another service. Or buy a new processor, obviously.

A bug maybe? There is a difference between bloat, and bugs.

---

### Post by arnab_das on 2010-05-01
gwibber forever sucked for me. never ever could read a single tweet from my twitter account (although pino does the job fabulously well). but for facebook (for me) gwibber is a #win

---

### Post by quinnten83 on 2010-05-01
> **swoll1980 said:**
> I don't really use Facebook very much, but Gwibber is great. I can check messages, and publish with one click. Great job Gwibber!
 It probably is, if it works....

---

### Post by toupeiro on 2010-05-01
To me, gwibber had/has a lot of potential, but today, its a failure for a few reasons IMO:

1) poor desktop couch integration.  I've reported multiple times on bugs on how poorly gwibber integrates with desktop couch and how bad of a job it does cleaning up after itself.

2) Limited functionality.  It seems when using the facebook plugin, for example, it only shows responses of other people, up to the point you try to respond to a post using gwibber.  It never shows your response, or any response after it.  You have to go to the page to see it, which sort of defeats the purpose of having a tool like this.

3) OMG its bloated..  It's a horrific memory hog.

---

### Post by arnab_das on 2010-05-01
gwibber will never clear up this mess. have been using gwibber for almost 2 ubuntu releases now and there has been absolutely NO improvement in the 'pulling the tweets' thing. whats the use of a twitter client which works for most and not for all! gwibber imo had been given a huge opportunity this time around by canonical. they messed it up. from now on, first thing i do after i install an ubuntu release (if the future releases carry gwibber that is) will be *sudo apt-get remove gwibber*.

---

### Post by Foster Grant on 2010-05-01
> **arnab_das said:**
> gwibber will never clear up this mess. have been using gwibber for almost 2 ubuntu releases now and there has been absolutely NO improvement in the 'pulling the tweets' thing. whats the use of a twitter client which works for most and not for all! gwibber imo had been given a huge opportunity this time around by canonical. they messed it up. from now on, first thing i do after i install an ubuntu release (if the future releases carry gwibber that is) will be *sudo apt-get remove gwibber*.

As much as I was looking forward to the Social From The Start features like gwibber, I can't disagree.

Unfortunately, there seems to be some serious bugs in the CouchDB structure underlying Gwibber and a few other things in Lucid.

---

### Post by Mr. Picklesworth on 2010-05-01
> **toupeiro said:**
> To me, gwibber had/has a lot of potential, but today, its a failure for a few reasons IMO:

1) poor desktop couch integration.  I've reported multiple times on bugs on how poorly gwibber integrates with desktop couch and how bad of a job it does cleaning up after itself.

2) Limited functionality.  It seems when using the facebook plugin, for example, it only shows responses of other people, up to the point you try to respond to a post using gwibber.  It never shows your response, or any response after it.  You have to go to the page to see it, which sort of defeats the purpose of having a tool like this.

3) OMG its bloated..  It's a horrific memory hog.

I, unfortunately, have the exact same experience. It also takes up 16MB in DesktopCouch, currently, which really makes no sense given that this is an app which displays 140 character messages with pictures. Even if it was storing every message ever in the database it shouldn't need that much space!

Lots of cleaning up to be done. On the bright side, Gwibber *was* once pretty light and cool, so it could return to that with some focus.

For now, though, I'm rooting for [Pino]("http://pino-app.appspot.com/"). It's written in Vala, to boot :)

---

### Post by arnab_das on 2010-05-01
> **Mr. Picklesworth said:**
> I, unfortunately, have the exact same experience. It also takes up 16MB in DesktopCouch, currently, which really makes no sense given that this is an app which displays 140 character messages with pictures. Even if it was storing every message ever in the database it shouldn't need that much space!

Lots of cleaning up to be done. On the bright side, Gwibber *was* once pretty light and cool, so it could return to that with some focus.

For now, though, I'm rooting for [Pino]("http://pino-app.appspot.com/"). It's written in Vala, to boot :)

i'm a huge huge pino fan. its awesome, its sleek and its not a memory hog. hope they would include a facebook feature as well though.

---

### Post by Foster Grant on 2010-05-01
Just told Gwibber to stop checking my Twitter and Identi.ca feeds. :( Still have it set to post to them so I can use the text box on the Me menu.

But for reading ... Pino? Buzzbird? Eh, who knows?

---

### Post by mikkyd on 2010-05-01
> **swoll1980 said:**
> A bug maybe? There is a difference between bloat, and bugs.
That's why I said nothing about bloat.

As for bugs though...

o It doesn't remove twitter messages from the stream in Gwibber, only from the twitter server.
o It sometimes doesn't let me unselect the Facebook or Twitter accounts when I send a message.
o It's very slow (no, that's not hardware).
o Yesterday it couldn't show my Facebook account in the "accounts" window, even though FB messages appeared in the stream.
o Today it doesn't show either my Twitter or FB account, there's nothing in the stream, when I add my Twitter account again it doesn't appear in the list on the left, and the entry does not appear in CouchDB.
o It takes too long to open, even after all that "beam.smp" stuff has calmed down and moved out of "top".

When something's this much of a failure I can't even be bothered logging the bugs.

Simple solution: open Twitter in Chromium, select "Create Application Shortcuts..." from the menu. Chromium makes things so easy, you could build a whole O/S from it.

---

### Post by Foster Grant on 2010-05-02
Well, this is good news: There's an available SQlite backend.

[https://code.edge.launchpad.net/~segphault/gwibber/230-sqlite-backend](https://code.edge.launchpad.net/~segphault/gwibber/230-sqlite-backend)

No idea how to install it.

And the developer is planning to migrate Gwibber from CouchDB to SQlite in future versions, according to the 2.30 announcement.

[http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/](http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/)

---

### Post by arnab_das on 2010-05-02
> **Foster Grant said:**
> Well, this is good news: There's an available SQlite backend.

[https://code.edge.launchpad.net/~segphault/gwibber/230-sqlite-backend](https://code.edge.launchpad.net/~segphault/gwibber/230-sqlite-backend)

No idea how to install it.

And the developer is planning to migrate Gwibber from CouchDB to SQlite in future versions, according to the 2.30 announcement.

[http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/](http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/)

honestly why work so hard to make gwibber work? adobe air apps seem more tolerable to me than the gwibber crap.

---

### Post by Primefalcon on 2010-05-02
I am loving gwibber

---

### Post by arnab_das on 2010-05-02
> **Primefalcon said:**
> I am loving gwibber

well thats the problem sir. only few people enjoy it. for an application to work or be accepted it should work for EVERYONE without any exceptions. i love the fact that canonical is experimenting with new softwares, but gwibber is one app where canonical has got it all wrong. the developers of gwibber are simply SILENT on bug reports and issues. i have filed countless bug reports and commented on many on the gwibber page. nothing, i repeat nothing has been done to resolve a single one of those bugs in more than 6 months. i appreciate all the hard work open source developers are doing but whats the use of a software whose developers chose to remain silent on bug reports? utterly irritating. imo gwibber should be removed in the next release. being cutting edge doesnt really mean including 'brainstorms' (thats what gwibber is right now, its an 'in-the-future' project) rather than working projects.

---

### Post by Primefalcon on 2010-05-02
TBH I have seen far more people praising it that dissing it... so did a lot of other people I've talked to, not to mention review sites, zdnet absolutely loved it!

---

### Post by arnab_das on 2010-05-02
> **Primefalcon said:**
> TBH I have seen far more people praising it that dissing it... so did a lot of other people I've talked to, not to mention review sites, zdnet absolutely loved it!

again, it gotta WORK for EVERYONE. liking and disliking it is something completely different. for many people, (if u check the bug reports page), it simply fails to pull the tweets. i havent read a single tweet on gwibber till date.

hence its crap. i dont care if it works for X no of people. but the fact is, it doesnt work for Y no of people. and that not how softwares included in a major release of Ubuntu should work.

---

### Post by Primefalcon on 2010-05-02
No matter how great it is, not everyone will love it

---

### Post by arnab_das on 2010-05-02
> **Primefalcon said:**
> No matter how great it is, not everyone will love it

again, its not a matter of liking/loving but simply getting it to work. eg. i hate brasero but it works. hence im completely okay with it. hope i was able to clear my point. :)

---

### Post by Primefalcon on 2010-05-02
> **arnab_das said:**
> again, its not a matter of liking/loving but simply getting it to work. eg. i hate brasero but it works. hence im completely okay with it. hope i was able to clear my point. :)

That's a bug... there seems to be plenty of them each release.... at least this release was nowhere near as bad as Karmic... I ended up having to go back to Jaunty for a while...

I had no usb mikes working (which I need), this is why I generally recommend waiting up to a month after every release before you upgrade, if bugs are something you can't really afford to have

---

### Post by arnab_das on 2010-05-02
> **Primefalcon said:**
> That's a bug... there seems to be plenty of them each release.... at least this release was nowhere near as bad as Karmic... I ended up having to go back to Jaunty for a while...

I had no usb mikes working (which I need), this is why I generally recommend waiting up to a month after every release before you upgrade, if bugs are something you can't really afford to have

i really hope gwibber devs fix this thing now that most ubuntu users are using it (since they havent even responded to bug reports on this issue in the past). not really canonical's fault this. agree that this one's better than karmic when it came out, way way better.

---

### Post by toupeiro on 2010-05-02
I think what kills me the most is.. we lost gimp off the install CD to be replaced by things like this flaky piece of software?  priorities, much?

---

### Post by swoll1980 on 2010-05-02
> **mikkyd said:**
> That's why I said nothing about bloat.

As for bugs though...

o It doesn't remove twitter messages from the stream in Gwibber, only from the twitter server.
o It sometimes doesn't let me unselect the Facebook or Twitter accounts when I send a message.
o It's very slow (no, that's not hardware).
o Yesterday it couldn't show my Facebook account in the "accounts" window, even though FB messages appeared in the stream.
o Today it doesn't show either my Twitter or FB account, there's nothing in the stream, when I add my Twitter account again it doesn't appear in the list on the left, and the entry does not appear in CouchDB.
o It takes too long to open, even after all that "beam.smp" stuff has calmed down and moved out of "top".

When something's this much of a failure I can't even be bothered logging the bugs.

Simple solution: open Twitter in Chromium, select "Create Application Shortcuts..." from the menu. Chromium makes things so easy, you could build a whole O/S from it.
You responded to a commit I made about targeting newer machines, which was a response to a bloat comment. Obvioulsy people don't buy new machines so they can run buggy software, but to be able to use full featured operating system. It drives me nuts when people call new features bloat.

---

### Post by arnab_das on 2010-05-02
> **swoll1980 said:**
> You responded to a commit I made about targeting newer machines, which was a response to a bloat comment. Obvioulsy people don't buy new machines so they can run buggy software, but to be able to use full featured operating system. It drives me nuts when people call new features bloat.

no offence, and plz dont get me wrong. new features in a software which are 'claimed' to work and dont work for a large no of users (ref: gwibber bugs page) should be tagged as bloated. in that gwibber is a big bloated piece of software.

---

### Post by Foster Grant on 2010-05-02
> **arnab_das said:**
> no offence, and plz dont get me wrong. new features in a software which are 'claimed' to work and dont work for a large no of users (ref: gwibber bugs page) should be tagged as bloated. in that gwibber is a big bloated piece of software.

I can't agree with your assessment. Gwibber itself is not bloated. Gwibber's dependency on things like CouchDB, beam.smp and DesktopCouch which we've learned have way too much resource overhead on execution? Yeah, that's a problem.

However, it can be fixed.

---

### Post by arnab_das on 2010-05-02
> **Foster Grant said:**
> I can't agree with your assessment. Gwibber itself is not bloated. Gwibber's dependency on things like CouchDB, beam.smp and DesktopCouch which we've learned have way too much resource overhead on execution? Yeah, that's a problem.

However, it can be fixed.

but honestly arent these things which were supposed to have been thought through MUCH before the lucid lynx release?

---

### Post by zekopeko on 2010-05-02
> **arnab_das said:**
> but honestly arent these things which were supposed to have been thought through MUCH before the lucid lynx release?

You do understand all of those are bugs?
And there are already patches in the cue to fix this in Lucid.

---

### Post by Foster Grant on 2010-05-02
> **arnab_das said:**
> but honestly arent these things which were supposed to have been thought through MUCH before the lucid lynx release?

There's a word you need to remember when dealing with any Linux distribution ... _upstream._

The problem is being worked on upstream by the Gwibber developer. Based on looking over bug reports, he knows about it and it's why he's in the process of moving it to SQLite. That said, it's a hobby for him rather than his job (he's the open-source editor at Ars Technica). Once he finishes moving it over, no more problems; I've been poking around and a couple of distros already have the SQLite option available. They're not having any problems.

The desktopcouch problems are also upstream. Probably best solved by moving to another database that's not so buggy.

---

### Post by swoll1980 on 2010-05-03
Anyway I'm sorry if it doesn't work well for some people. I just built my machine 2 months ago, and it is pretty much over kill for running Ubuntu. I never realized Gwibber was sucking up resources like that.

---

### Post by mikkyd on 2010-05-03
> **swoll1980 said:**
> You responded to a commit I made about targeting newer machines, which was a response to a bloat comment. Obvioulsy people don't buy new machines so they can run buggy software, but to be able to use full featured operating system. It drives me nuts when people call new features bloat.
The problem is not bloat, which is why new hardware is not the solution. Next time you boot up, run "top" in a terminal window. You may soon see a load of "beam.smp" entries taking up all your CPU cycles (you might need to open an app which relies on Couch DB, such as Gwibber  or Ubuntu One Preferences, to kick this off).

On my netbook this all starts within a minute and lasts about 5 minutes. Running other apps during this time is frustratingly slow, opening new apps even more so. This should not happen and it is quite proper to call it bloat if you don't know that it's actually a bug upstream from Couch DB. It drives me nuts when people instinctively think something's a hardware issue. My hardware should easily be able to open an app with Gwibber's 
functionality and not stall for 5 minutes.

I remembered a few more bugs from my short time as a Gwibber user:
o I did a search in Twitter and (after a long wait with no indication that anything was happening in the background) a new entry appeared under the Search icon in the panel on the left. I clicked on the X on the right of the entry, which deleted it. Next time I clicked the Search option it repeated the deleted search (after an agonizingly long period in which it gave no indication anything was happening).
o I clicked on an "@" link in the Twitter feed. Like Search, this created an entry in the panel on the left, with an X to its right. Clicking the X did not delete the entry.

I'm glad this thing works for you, but for me and others it's a big fail.

---

### Post by Merkaba_ZA on 2010-05-06
I've been using Gwibber as my main social client since I first stumbled on it several releases ago but seeing as Twitter is really the only service I post and check on a regular basis I'm tempted to try out [Pino]("http://pino-app.appspot.com/") that was mentioned a few pages back in this thread. If its faster and slicker than Gwibber I'll switch to it immediately.

---

### Post by SDonatas on 2010-05-06
> **Foster Grant said:**
> Well, this is good news: There's an available SQlite backend.

[https://code.edge.launchpad.net/~segphault/gwibber/230-sqlite-backend]("https://code.edge.launchpad.net/%7Esegphault/gwibber/230-sqlite-backend")

No idea how to install it.

And the developer is planning to migrate Gwibber from CouchDB to SQlite in future versions, according to the 2.30 announcement.

[http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/](http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/)


Thats great news, because just few days ago i purged malfunctioning ubuntuone, gwibber and ofcourse desktop couch, which for some reason all the time works in the backgroud, even if you are not using any program which needs it. And anyway what is the point to use Gwibber with desktop counch if you can (at least for 32 bit ubuntu for now) use adobe air and tweetdeck or other alternative. Because each time i use Gwibber its becomming laggy (i'm sure thats becouse desktopcouch) and when you press on the e.g. facebook pictures program directs you to the website. While in tweetdeck you can do almost everything inside client. I just dont like the way it looks, and there is lack of gnome integration, and i dont think there will ever be.  So fingers crossed for SQlite. I hope ubuntuone will also avoid using desktop counch stuff.

---

### Post by Mr. Picklesworth on 2010-05-06
> **SDonatas said:**
> Thats great news, because just few days ago i purged malfunctioning ubuntuone, gwibber and ofcourse desktop couch, which for some reason all the time works in the backgroud, even if you are not using any program which needs it. And anyway what is the point to use Gwibber with desktop counch if you can (at least for 32 bit ubuntu for now) use adobe air and tweetdeck or other alternative. Because each time i use Gwibber its becomming laggy (i'm sure thats becouse desktopcouch) and when you press on the e.g. facebook pictures program directs you to the website. While in tweetdeck you can do almost everything inside client. I just dont like the way it looks, and there is lack of gnome integration, and i dont think there will ever be.  So fingers crossed for SQlite. I hope ubuntuone will also avoid using desktop counch stuff.

Well, there's our dilemma. Ubuntu One (and Quickly, for that matter) is hooked on Desktop Couch. In fairness, the API to access it is pretty slick. You can make data in an application persistent without even thinking about it, and it's very neat and GLiby.

So, I would be quite happy if DesktopCouch behaved particularly beautifully and the rest of the world moved to it.

As it is, there was almost this wonderful thing going where applications, including Gwibber, were all moving to use the XDG data dirs (~/.cache, ~/.local, ~/.config) to logically organize their persistent data… and Desktop Couch makes that beautiful picture hard to follow again.

I don't feel that I've gained anything from that added complexity, although technically a single database could be quite a nice thing. Perhaps, as things evolve, I'll feel better. Maybe a Desktop Couch backend for GSettings would make me happier; that coupled with CouchDB's pairing functionality could be very interesting.

---

### Post by Scarlet_Chantel on 2010-05-07
Gwibber is super cool... I wish it had a picasa plug in though ... *dreams* :)

---

### Post by mikkyd on 2010-05-09
> ...there was almost this wonderful thing going where applications, including Gwibber, were all moving to use the XDG data dirs (~/.cache, ~/.local, ~/.config) to logically organize their persistent data&#8230; and Desktop Couch makes that beautiful picture hard to follow again.

I don't feel that I've gained anything from that added complexity, although technically **a single database** could be quite a nice thing.
That got me thinking...

CouchDB = Windows Registry

?

---

