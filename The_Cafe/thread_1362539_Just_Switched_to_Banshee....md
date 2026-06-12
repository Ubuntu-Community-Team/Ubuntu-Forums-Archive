---
title: "Just Switched to Banshee..."
date: 2009-12-23
forum: The Cafe
---

### Post by speedwell68 on 2009-12-23
...from Songbird.  I was getting a bit annoyed with Songbird as it was so bloaty and I was finding the new version (1.4) less than stable.  I was only really using it to manage my iPod Shuffle.  Banshee is so much faster and it supports video playback too.  It is by far the best media player that I have used in Linux.  So glad I have made the switch.

---

### Post by Zoot7 on 2009-12-23
Banshee is the only player I've found that actually has a decent equalizer thus far in Linux.
I've been using it for a while now, the only thing that annoys me is having to route out all the mono build dependencies for stuff like Slackware.

---

### Post by gnomeuser on 2009-12-23
I am happy to see that you enjoy Banshee, it's a pleasure to work on that project and see happy users such as yourself espouse happiness with the end result.

I hope you'll enjoy the upcoming 1.6 release which will add tons of really exciting features.

If you are interested in seeing it up close and personal the the banshee, banshee-unstable and banshee-daily PPAs are a really great tool to make that easy.

The hope is that Banshee can replace Rhythmbox in Lucid+1, we have ironed out most of the issues which were deemed critical when it was examined last as well as adding a bunch of interesting functionality on top.

---

### Post by legolas_w on 2009-12-23
I am also thinking about switching to Banshee but the following issues prevent me so far:

- Can I move my rating from songbird to banshee? I mean which songs has 4 stars and which songs has 5 and so on?

- Does banshee has theme capabilities? I mean can I simply change the theme?

- are there kooooool plugins available for banshee?  something like resume playing last track when it starts? synchronizing some part of the library with a directory? for example synchronizing the top rated tracks with a directory?


Thanks

---

### Post by amazingtaters on 2009-12-23
Congrats on making the switch. I've messed around with Songbird, and maybe I should give it another chance since it's been almost a year since I last tried it, but Banshee has been my old standby since I started using ubuntu about 2 and half years ago and I quickly got sick of rythmbox. Now I'm gonna have to go find out about 1.6.

---

### Post by Tibuda on 2009-12-23
> **legolas_w said:**
> - Does banshee has theme capabilities? I mean can I simply change the theme?

Sure, exactly how themes should work on every app. Change your GTK+ theme settings, and all apps change.

---

### Post by gnomeuser on 2009-12-23
> **legolas_w said:**
> 
- Can I move my rating from songbird to banshee? I mean which songs has 4 stars and which songs has 5 and so on?


Currently Banshee supports import of existing database from Amarok, Rhythmbox and iTunes.

I filed an enhancement request to add  [support for songbird importing](https://bugzilla.gnome.org/show_bug.cgi?id=605315)

> 
- Does banshee has theme capabilities? I mean can I simply change the theme?


Banshee adopts and uses the session gtk+ theme, in addition you can have multiple interfaces such as the Cubano "netbook" UI (which shares some visual designs with the Zune Marketplace I hear).

> 
- are there kooooool plugins available for banshee?  something like resume playing last track when it starts? synchronizing some part of the library with a directory? for example synchronizing the top rated tracks with a directory?


Banshee (in git as of 9 days ago, upcoming stable release) supports playlist syncing. This means you define am intelligent  playlist and this will be the target for syncing when you insert your portable device. The intelligent playlist support any information in the database such as rating, play count, and so on. This should do _exactly_ what you ask.

[Git changes for this feature](http://git.gnome.org/browse/banshee/log/?qt=grep&q=playlist+sync).

Outside of that we have a coverflow like extension out of the tree currently that uses clutter. There is Mirage which provides playlists based on similarities between songs acquired from spectrum analysis. Someone wrote a moodbar extensions. Banshee has lots of powerful extensions, not all of them are in the banshee package or even the Ubuntu repos though. 

On top of that the entire interface is replaceable and scriptable using the pythonish Boo language.

---

### Post by hoppipolla on 2009-12-23
yeah I've always found Songbird to be a bit slow and bloated, I also don't like the feel of the toolkit it uses... what is it?

Then again, I haven't used it in AGES, so I could be basing my opinions on an old version.

I'm very happy with Amarok other than a few bugs here and there, but yes Banshee is pretty cool too :)

---

### Post by gnomeuser on 2009-12-23
I can't believe I forgot the coolest extension of all [telepathic banshee](http://nlokos.blogspot.com/2009/06/banshee-goiing-telepathic.html)

The demonstration video in the link makes it clear what this does but basically it allows you to stream/share data in your Banshee library with people listed on your buddy list in Empathy. 

Harness the power of Telepathy with Banshee

---

### Post by VastOne on 2009-12-23
I was looking forward to trying out Banshee and using it after reading this thread.

To my surprise, there is no function for Shoutcast Radio...which is OK in itself as I like to use Streamtuner and have it use my player.

All other music players (exaile, songbird etc) work fine doing this but Banshee fails to load the stream and play it...

Any thoughts as to why?

---

### Post by RiceMonster on 2009-12-23
I'll try banshee again at 1.6. It's pretty good, but there's some things that I'd like it to have before I'd use it:
- Select multiple directories for a music library (or at the very least be able to use symlinks)
- Update library without rescanning the whole thing (I believe this is comming)
- Gapless playback (believe this is comming as well)
- Select album artwork myself manually, incase the wrong artwork is downloaded or it is not found.

---

### Post by gnomeuser on 2009-12-23
> **VastOne said:**
> I was looking forward to trying out Banshee and using it after reading this thread.

To my surprise, there is no function for Shoutcast Radio...which is OK in itself as I like to use Streamtuner and have it use my player.

All other music players (exaile, songbird etc) work fine doing this but Banshee fails to load the stream and play it...

Any thoughts as to why?

running banshee-1 --debug might bring some clarity to the general area. Also you can follow the bug filing guide and our helpful developers will be right along to work on the issue[SIZE="1"]*[/SIZE]

[http://banshee-project.org/contribute/file-bugs/](http://banshee-project.org/contribute/file-bugs/)

* developer time is limited, right along might be optimistic. A well thought out bug report though makes all the difference but still time may be limited by more pressing issues. Please be understanding if your problem isn't addressed right away.

---

### Post by boombox1387 on 2009-12-23
> **RiceMonster said:**
> 
- Select album artwork myself manually, incase the wrong artwork is downloaded or it is not found.

This is coming as well.  Actually, it's already merged into the master branch and available to people testing the daily builds.

I started using Banshee about a year and a half ago, and the development has been fun to watch.  My contributions have mostly been limited to triaging bugs at this point, but it's a really fun project to work with.

---

### Post by VastOne on 2009-12-23
> **gnomeuser said:**
> running banshee-1 --debug might bring some clarity to the general area. Also you can follow the bug filing guide and our helpful developers will be right along to work on the issue[SIZE="1"]*[/SIZE]

[http://banshee-project.org/contribute/file-bugs/](http://banshee-project.org/contribute/file-bugs/)

Done and submitted

[https://bugzilla.gnome.org/show_bug.cgi?id=605317](https://bugzilla.gnome.org/show_bug.cgi?id=605317)

So you know it appears to be a gstream codec loading problem

Thank you....

---

### Post by phillychease on 2009-12-23
after i read this thread i downloaded banshee.
VERY GOOD! its faster than songbird however, are there addons or something so i can search for duplicates?

---

### Post by wipeout7823 on 2009-12-23
> **gnomeuser said:**
> 


Banshee adopts and uses the session gtk+ theme, in addition you can have multiple interfaces such as the Cubano "netbook" UI (which shares some visual designs with the Zune Marketplace I hear).


On top of that the entire interface is replaceable and scriptable using the pythonish Boo language.

Are there any currently active builds of banshee with different interfaces. Just saw a preview of Cubano [http://abock.org/blog-images/gcds-cubano.png ]("http://abock.org/blog-images/gcds-cubano.png") but I don't think it will be available until 2.0. I love banshee but the UI leaves something to be desired.

---

### Post by jpeddicord on 2009-12-23
Switched back to Banshee this week and have been loving it. Only thing I dislike is the [broken Replay Gain support]("https://bugs.launchpad.net/banshee/+bug/377354"), but there's a [patch in bugzilla]("https://bugzilla.gnome.org/show_bug.cgi?id=600072") to fix that.

---

### Post by linusr on 2009-12-23
good thing now banshee can import itunes library including ratings

---

### Post by *g!t5^_)*(H on 2009-12-23
Banshee is my favourite music player since some time ago. Congratulations for this great piece of software gnomeuser! I miss it a lot at my job, where I'm only able of running windows.

---

### Post by gnomeuser on 2009-12-23
> **wipeout7823 said:**
> Are there any currently active builds of banshee with different interfaces. Just saw a preview of Cubano [http://abock.org/blog-images/gcds-cubano.png ]("http://abock.org/blog-images/gcds-cubano.png") but I don't think it will be available until 2.0. I love banshee but the UI leaves something to be desired.

There is the Muinshee frontend which is included in the main packages. Cubano has been strangely delayed for a long time, I don't know when we can expect it. However if you run the openSUSE Moblin edition called Goblin then they ship it.

It should be possible to build it for Ubuntu and provide packages.  I don't know if anyone is doing this currently.

---

### Post by gnomeuser on 2009-12-23
> **optimisme said:**
> Banshee is my favourite music player since some time ago. Congratulations for this great piece of software gnomeuser! I miss it a lot at my job, where I'm only able of running windows.

Please don't give me credit for Banshee, I only do bug triaging, testing, translation and such. I don't code, that is left to our capable community of wonderful developers.

I can assure you that your Banshee free Windows experience will soon come to an end, it is a goal that 1.6 will ship on Linux, OS X and Windows.

---

### Post by gnomeuser on 2009-12-23
> **phillychease said:**
> after i read this thread i downloaded banshee.
VERY GOOD! its faster than songbird however, are there addons or something so i can search for duplicates?

unfortunately no, but it would make a great feature request if you run over to bugzilla and file that mother it would be superb.

---

### Post by ufugu on 2009-12-23
Thanks for inspiring me to try Banshee again.  Songbird is actually WORSE than it used to be.  They have lost sight of their "play the web" focus, added almost no new features to the Linux version in a loooong while, and seem to focus their attention on making everything really ugly.  Too bad, it used to be pretty cool and I thought it was the future of media players at one time!

I'm looking forward to seeing what's been up lately with Banshee! Last time I looked there was still no way to browse by genre, which really limited it's usefulness with large, non-playlist based collections. 

It seems like all the players for Linux start off strong and then their focus diffuses into peripheral features instead of getting the basics of managing a media library down first. Still dreaming of a player that's as good as MediaMonkey or iTunes for just plain old managing of music collections. :guitar:

---

### Post by ICDeath on 2010-01-02
Ok some more questions coming:
1. Can Banshee play Apple Lossless files?
2. Can Banshee automatically organize your library the way Itunes does, so you won't have to rename and move everything yourself? (Songbird now has this feature too)
3. Can it sync with the latest Ipod from September 09? (7th Generation)
4. Can it fetch Itunes downloaded (not manually embedded) artwork? (again, Songbird can do that too now)

If not yet available are those features planned and if not, where can I submit my request of them? :) Having an Ipod, Itunes is almost the only application that keeps me using Windows. But I'm planning to switch to Ubuntu in April and hopefully Banshee will be able to do all of this.

---

### Post by gnomeuser on 2010-01-02
> **ICDeath said:**
> Ok some more questions coming:
1. Can Banshee play Apple Lossless files?


It plays anything you have support for in GStreamer

> 
2. Can Banshee automatically organize your library the way Itunes does, so you won't have to rename and move everything yourself? (Songbird now has this feature too)


Yes, go to:

edit->preferences (names might be slightly different I use the danish locale and translate on the spot to english). Now select the update file- og directory setting.

> 
3. Can it sync with the latest Ipod from September 09? (7th Generation)


iPods are tricky, Apple are displaying epic amounts of douchebaggery and suing people who try to figure out how to make their devices work and they also setup specific stumbling blocks that serve no other purpose than to prevent 3rd parties from adding support such as the crypto hash around the database. I am only certain we have support for 5th generation devices and below. 

> 
4. Can it fetch Itunes downloaded (not manually embedded) artwork? (again, Songbird can do that too now)


If it can't do it, it will fetch your artwork from other sources. Banshee will import your existing iTunes database so I imagine it might grab it from there but I haven't tried that.

> 
If not yet available are those features planned and if not, where can I submit my request of them? :) Having an Ipod, Itunes is almost the only application that keeps me using Windows. But I'm planning to switch to Ubuntu in April and hopefully Banshee will be able to do all of this.

You go to the GNOME bugzilla and file a polite bug report as an enhancement (please do check for duplicates first). 

Generally you are requested to follow this guide:
[http://banshee-project.org/contribute/file-bugs/](http://banshee-project.org/contribute/file-bugs/)

---

### Post by docus on 2010-01-02
I switched to Banshee from Rhythmbox in 9.04 and loved it.  But I had to go back to Rhythmbox in 9.10 because Banshee didn't recognise my iPod (6th gen iPod classic).  Will banshee get this functionality back in version 1.6?

---

### Post by gnomeuser on 2010-01-02
> **docus said:**
> I switched to Banshee from Rhythmbox in 9.04 and loved it.  But I had to go back to Rhythmbox in 9.10 because Banshee didn't recognise my iPod (6th gen iPod classic).  Will banshee get this functionality back in version 1.6?

This is caused by the switch from HAL to DeviceKit. This has been fixed in git master for Banshee and using the latest podsleuth/ipod-sharp. You can install these from the banshee-daily ppa if I am not mistaken.

Though the support isn't without problems:
[https://bugzilla.gnome.org/show_bug.cgi?id=605889](https://bugzilla.gnome.org/show_bug.cgi?id=605889)

If this supports the 6th generation iPods I don't know, I only have a 5th generation model to test with.

---

### Post by docus on 2010-01-02
Hey Gnomeuser, thanks for the helpful reply!  

I added the Banshee daily build PPA but it didn't seem to update Banshee and it didn't install a new version of ipod-sharp or podsleuth.  Not sure what I'm doing wrong.  When I look up ipod-sharp in synaptic to check what version I have, it lists libipod-cil, libipod-cil-dev, libipodui-cil, and libipodui-cil-dev - but no "ipod-sharp" and none of those files are installed.  I tried installing them but it made no difference to Banshee (so I uninstalled them again).

Sorry for the noobishness.

Roll on 1.6 - I can't wait to get back to using Banshee.  Any idea when it's coming out?

Also, I'm going to put it on my g/f's mac to wean her off iTunes.

---

### Post by sdowney717 on 2010-01-02
[http://old.nabble.com/Banshee-f33893.html](http://old.nabble.com/Banshee-f33893.html)
read about user experiences here

I originally thought Banshee was great, my trials over the video podcasting changed my mind. banshee cpu usage would climb to 100% and it would either stop responding or simply crash and exit. Then their is the problem where it plays video in a separate minature window.

---

### Post by gnomeuser on 2010-01-02
> **docus said:**
> Hey Gnomeuser, thanks for the helpful reply!  

I added the Banshee daily build PPA but it didn't seem to update Banshee and it didn't install a new version of ipod-sharp or podsleuth.  Not sure what I'm doing wrong.  When I look up ipod-sharp in synaptic to check what version I have, it lists libipod-cil, libipod-cil-dev, libipodui-cil, and libipodui-cil-dev - but no "ipod-sharp" and none of those files are installed.  I tried installing them but it made no difference to Banshee (so I uninstalled them again).

Sorry for the noobishness.

Roll on 1.6 - I can't wait to get back to using Banshee.  Any idea when it's coming out?

Also, I'm going to put it on my g/f's mac to wean her off iTunes.

libipod-cil is the name of the package in Debian, they have a special naming scheme that packages must follow regardless of what the upstream name is.

Did you also enable the banshee and banshee-unstable ppas? (sorry I forgot to mention that you should at least also enable the regular banshee ppa). The problem might also be that hyperair the ppa maintainer is currently busy on personal manners so there isn't much work being done, I believe he will be back on the job soon. This means e.g. that the PPA isn't setup for building against Lucid, the daily builds though should be handled by a script so that should run regardless.

I believe that the target is to follow the GNOME upstream development cycle now at least that was the proposed plan a little while ago. Meaning when the next GNOME comes out you should also get the new stable release. Though git isn't at all unstable at least presently and in memorable history so you can use it with some caution.

---

### Post by gnomeuser on 2010-01-02
> **sdowney717 said:**
> [http://old.nabble.com/Banshee-f33893.html](http://old.nabble.com/Banshee-f33893.html)
read about user experiences here

I originally thought Banshee was great, my trials over the video podcasting changed my mind. banshee cpu usage would climb to 100% and it would either stop responding or simply crash and exit. Then their is the problem where it plays video in a separate minature window.

These are bugs, did you report them?

---

### Post by Regenweald on 2010-01-02
To hell with music management! Audacious FTW!!!
.
..
.
no , I'm not serious :) but audacious does rock ;)

---

### Post by sdowney717 on 2010-01-03
> These are bugs, did you report them?

yes I did!
The one who wrote the video podcasting is coding a new version.

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/488799](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/488799)
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/488832](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/488832)

---

### Post by gnomeuser on 2010-01-03
> **sdowney717 said:**
> yes I did!
The one who wrote the video podcasting is coding a new version.

Mike Urbanski has been writing such a replacement podcast plugin as part of GSoC but I have yet to see proposals for merging it. However I think the problem you are seeing might more related to the video support which somehow seems to have broken.

Regardless can I ask you to CC me to the bugs or otherwise give me the links so that I might track these issues?

---

### Post by sdowney717 on 2010-01-03
I edited my prior posts by added a couple links to show you. I put a lot of detail in there.
but these are still undecided bugs.

---

### Post by gnomeuser on 2010-01-03
> **sdowney717 said:**
> I edited my prior posts by added a couple links to show you. I put a lot of detail in there.
but these are still undecided bugs.

Ah but you filed these in the Ubuntu bugtracker not the upstream tracker. The Banshee developers are not responsible for tracking downstream bugs. To maximize your chances move them to bugzilla.gnome.org. 

[http://banshee-project.org/contribute/file-bugs/](http://banshee-project.org/contribute/file-bugs/)

Currently Ubuntu's Launchpad sadly doesn't provide a means for pushing such bugs automatically upstream so for now you have to do it by hand. 

Additionally to get more data out you can use --debug and --debugsql which might provide more information as to the exact problem.

I think the 100% load bug might be fixed by this check in:
[http://git.gnome.org/browse/banshee/commit/?id=f89c9e094ee90bccd2e6864d226ef319e4a77a32](http://git.gnome.org/browse/banshee/commit/?id=f89c9e094ee90bccd2e6864d226ef319e4a77a32)

As you appear to be using 1.5.1 can I ask you to retest and confirm if this is present in git (the banshee-daily ppa should provide a recent build at low risk).

---

### Post by sdowney717 on 2010-01-03
I just tried version 1.6, It played a video in a small separate window and then crashed when I closed the window.

I will play around with it and If It keeps crashing send it upstream.

---

### Post by Greenwidth on 2010-01-03
I'm having trouble with Banshee as well, (from both repo and ppa): 

Starts quickly and plays first mp3 fine with hardly any CPU usage, on starting the second, CPU jumps to 100% on 2 cores and program is unusable for 5-10 secs then settles down - same happens for all subsequent mp3's.

Seems strange that it will play the first fine but not the second.

---

### Post by gnomeuser on 2010-01-03
> **Greenwidth said:**
> I'm having trouble with Banshee as well, (from both repo and ppa): 

Starts quickly and plays first mp3 fine with hardly any CPU usage, on starting the second, CPU jumps to 100% on 2 cores and program is unusable for 5-10 secs then settles down - same happens for all subsequent mp3's.

Seems strange that it will play the first fine but not the second.

Does this happen with the version from the banshee-daily ppa?

---

### Post by Greenwidth on 2010-01-03
I'll try the daily when I get back.

I was using (I think):
[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

----

That sorted it! Thanks :)

---

### Post by boombox1387 on 2010-01-06
> **sdowney717 said:**
> I just tried version 1.6, It played a video in a small separate window and then crashed when I closed the window.

I will play around with it and If It keeps crashing send it upstream.

The crashing video window is a known issue.  [https://bugzilla.gnome.org/show_bug.cgi?id=548635](https://bugzilla.gnome.org/show_bug.cgi?id=548635) is where you can read about it and follow its progress.

---

### Post by koshatnik on 2010-01-06
I've had several computers with linux installed, on several different versions of ubuntu, and on not one occassion have I ever managed to get banshee to work. All it does is crash incessantly, or freeze up when adding songs to a library.

Guess it just hates me.

---

### Post by sdowney717 on 2010-01-06
look into exaile
[http://www.exaile.org/](http://www.exaile.org/)

---

### Post by GMU_DodgyHodgy on 2010-01-06
> **gnomeuser said:**
> I can't believe I forgot the coolest extension of all [telepathic banshee](http://nlokos.blogspot.com/2009/06/banshee-goiing-telepathic.html)

The demonstration video in the link makes it clear what this does but basically it allows you to stream/share data in your Banshee library with people listed on your buddy list in Empathy. 

Harness the power of Telepathy with Banshee

Banshee is really well done - switched a while ago - never looked back.

---

### Post by rob22941 on 2010-01-19
Are there any, banshee equalizer plugins available?

---

### Post by mamamia88 on 2010-01-19
me too because version of rhythmbox in lucid broke right click functionality in panel for me

---

### Post by boombox1387 on 2010-01-19
> **rob22941 said:**
> Are there any, banshee equalizer plugins available?

Banshee has an equalizer built in, if that's what you want.  The default equalizer doesn't have any pre-set settings, though (like Pop, Rock, Jazz, etc), and I don't know of any third-party add-ons that add equalizer settings, if that's what you're looking for.

But yeah, Banshee's default equalizer is everything you would expect a 10-band equalizer to be.  It's amazing how much better music sounds when you can tweak it.

---

### Post by rob22941 on 2010-01-19
> **boombox1387 said:**
> Banshee has an equalizer built in, if that's what you want.  The default equalizer doesn't have any pre-set settings, though (like Pop, Rock, Jazz, etc), and I don't know of any third-party add-ons that add equalizer settings, if that's what you're looking for.

But yeah, Banshee's default equalizer is everything you would expect a 10-band equalizer to be.  It's amazing how much better music sounds when you can tweak it.

Got any basic guides on how to tweak my settings?

---

### Post by gnomeuser on 2010-01-19
> **rob22941 said:**
> Got any basic guides on how to tweak my settings?

Moving the sliders till ears are full of win?

---

### Post by rob22941 on 2010-01-19
Haha I'll give it a go!:popcorn:

---

### Post by boombox1387 on 2010-01-19
> **gnomeuser said:**
> Moving the sliders till ears are full of win?

I like that advice :)  That's basically what I did.

Personally, I like to bump the high and low, and knock the mid-low down a little.  I think it makes the music (at least my music) sound crisper and punchier.  If you hover over the sliders, it'll tell you what they're set at.  For me, 2 5 0 -3 -3 -1 4 5 0 2 seems to work pretty well.

People who know more than me would probably tell you that there's a science to it - and they would probably right - and if you go to the websites of these people, you'll probably get lots of good advice.

---

### Post by boombox1387 on 2010-02-12
It's worth noting that built-in equalizer presets are now part of the development version of Banshee.  They'll be available to users of the Daily Build soon (I would imagine) and they'll make it into the next release.

---

### Post by nmyrick on 2010-05-18
Gnomeuser,

I am having an issue with Banshee that I hope you can help me with.  I have a second generation IPod Nano, that Banshee has suddenly just stopped recognizing.  I have not used this Nano on any other computer, and the computer mounts the Ipod perfectly.

I went to the following page to try to see what my issue was, and it said that I need to install libipoddevice and ipod-sharp.

[http://download.banshee-project.org/legacy/banshee-official-plugins/banshee-official-plugins-0.11.3.news](http://download.banshee-project.org/legacy/banshee-official-plugins/banshee-official-plugins-0.11.3.news)

So I installed libipoddevice with no issues (however, I don't know why it wasn't already there, since my IPod was syncing fine a couple days ago), and I have downloaded the tar package for ipod-sharp, but I have found that it contains the most useless readme file that I have ever seen!

The readme file only says the following:
 
"ipod-sharp is a library that allows manipulation of the iTunesDB used in
Apple iPod devices.  Currently it supports adding/removing songs and
manipulating playlists."  

To which I say, "Please tell me something I **don't** know, like what I need to do to install the package, since it isn't available through my current synaptic package manager!"  I thought helping people with installation was supposed to be one of the main purposes of readme files, not telling people what they already know! 

Anyway, can you please help me with the installation/extraction of the iPod-sharp package?

Thanks,
nmyrick

---

### Post by nmyrick on 2010-05-18
gnomeuser,

My version of Banshee is 1.6, and I have the IPod support extension enabled, but it still does not recognize my 2nd Gen Ipod Nano that it was recognizing perfectly fine a couple days ago.

---

### Post by nmyrick on 2010-05-18
FYI:  RhthymBox still recognizes my IPod perfectly fine every time, the only drawback to Rhthymbox is that it doesn't synchronize, but obviously the synchronization is useless if Banshee doesn't recognize it.

---

### Post by gnomeuser on 2010-05-18
Most Banshee iPod problems are caused by 2 things.

1) Removal of HAL

udev (formerly devicekit) replaced HAL and the compatibility and featuresety isn't all it was promised. Sadly this means that Banshee currently needs HAL. To fix these issues you need to upgrade to Podsleuth 0.6.7. This release sadly is not yet found in the Banshee PPA to the best of my knowledge and for some reason Lucid was shipped without the package being updated.

I'll request a SRU for this as iPod support is literally broken 6 ways from Sunday without this update.

Alex Luni who is improving our Now Playing screen as a GSoC student is also doing the udev binding and banshee porting work and that is reportedly going well. I'm confident that part will be in 1.8.

2) Newer models

iPhone, iPod Touch and the iPod Classic models aren't supported by podsleuth. The solution here is likely going to be binding libgpod and porting Banshee to that. However this is a lot of work and nobody is currently able to allot the required time. 

It's kind of a pain to not be able to support the newest Apple products but frankly that is Apples fault. They are also making it legally unattractive, to reverse engineer their protocols and formats. 

This I see a lot of excitement around but sadly very little available time/talent to bring the work to production quality worthy of being in Banshee can be found currently. People with C# experience might want to have a look at this task, lots of people would be grateful for some contributions in this area.

The good news in all of this is that Banshee is now the default media player in MeeGo and Moovida selected Banshee as part of their 2.0 stack. Hopefully meaning we will see some more contributors joining in and at least for the Moovida people iPod support would potentially be of interest.

---

### Post by screaminj3sus on 2010-05-18
Banshee is really awesome. Great ui and lots of good features.

I cant use exaile because it freezes when I scan my music library, its done this since like versions 2.x and other people have reported the same issue but they do nothing about it. ](*,)

---

### Post by gnomeuser on 2010-05-18
Oh and if you want my attention for a Banshee issue in this thread please do poke me via PM to grab my attention or I am likely to miss it. If you include a link to the thread in the message chances of cookies vastly increases.

---

### Post by nmyrick on 2010-05-18
Thanks Gnomeuser.  I found a way to make it work.  I had to disable auto-mounting in nautilus.  

Now I start Banshee and then manually mount the IPod and it works almost every time.

---

