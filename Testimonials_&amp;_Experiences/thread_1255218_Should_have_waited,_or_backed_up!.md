---
title: "Should have waited, or backed up!"
date: 2009-09-01
forum: Testimonials &amp; Experiences
---

### Post by 3rdalbum on 2009-09-01
Hmm. Last night I decided to dist-upgrade to Karmic Koala, and it didn't go well.

Firstly, dpkg became a zombie process near the beginning when installing libthai0; after a bit of Googling and asking for help from #ubuntu, I managed to get the upgrade to continue. Every five minutes it would run into problems, and I had to do a bit of hacking around to find out the precise problem each time and fix it.

My computer froze completely at one point, and I thought "That's it, the system is ruined" but to my surprise after rebooting it actually came up, and displayed the new GDM login screen. After finishing the upgrade process, I tried logging into Gnome, and it simply didn't start.

I have Openbox too, and could start up a sort of Gnome by launching "gnome-panel", "nautilus" and "dbus --session", but there's a LOT that doesn't work, including the Update Manager.

I installed KDE and it's working moderately well. Some problems with plasma widgets, but otherwise it's fine.

So, basically, I have a semi-broken system, and I don't know if it's due to the haphazard update or just the fact that it's currently in alpha. (hey, what happened to the cute names for alpha versions, like Flight and Tribe?).

My testimonial is good and bad:

1. Good: the underlying system seems pretty stable
2. Good: Apart from some plasma widgets not working, KDE is working fine
3. Good: The new GDM looks great
4. Bad: Gnome seems to be broken, assuming it's not just a problem at my end
5. Bad: This is the first time for me that a dist-upgrade has been such a lot of trouble.
6. Bad: Pulseaudio had my sound card set to "mute" by default, a problem I could only fix in KDE
7. Good: Some of the new stuff like Palimpsest is pretty cool
8. Bad: Palimpsest is a really difficult name to remember :-D
9. Good: Ubuntu is one tough distro - after the crash, when it was still partly Karmic and partly Jaunty, it still booted up to the login screen. Impressive.

So, if you're thinking of upgrading early, you should make a backup of your current operating system FIRST. Because, to be honest, I'd probably go back. Let's hope Gnome starts working properly again in later updates. And if you're thinking of upgrading early, you'd better brush up on these commands:

```
apt-get install -f
dpkg --configure -a
dpkg --audit
```

---

### Post by armandh on 2009-09-01
let me get this right....
you are putting a pre release OS on a mission critical machine?

and now you know why such is called bleeding edge!

operating system and car comparison aside   .....   CRASH
tell us where to send the flowers.

---

### Post by 3rdalbum on 2009-09-01
> **armandh said:**
> let me get this right....
you are putting a pre release OS on a mission critical machine?

Oh god no. It's my home desktop, but if anything happened to it I could survive by using my netbook or home server. The home server I regard as my "mission critical" machine.

Yeah I know it's "bleeding edge" and "alpha" for a reason, but I remembered the Hardy beta being rock solid and thought the last alpha would be acceptably alright. And when I'm using KDE, it's perfectly fine - in fact, I'm rather liking KDE again now :-)

---

### Post by lancest on 2009-09-01
They are doing real nice things with Karmic (I have it on an extra pc). Runs ok but you can see its not near enough to being finished. 
I like it alot but it's not replacing Jaunty on my main for around 60 days. It's worth having a look at the various nice improvements though.

---

### Post by slakkie on 2009-09-01
> **armandh said:**
> let me get this right....
you are putting a pre release OS on a mission critical machine?

and now you know why such is called bleeding edge!

operating system and car comparison aside   .....   CRASH
tell us where to send the flowers.


I am :popcorn:

You can send flowers to 
Online Breedband BV tav Wesley
Muiderstraat 1
1011PZ Amsterdam, NL

---

### Post by Sidewinder1 on 2009-09-01
Many times, experience can be the best teacher; she can also be very expensive.
:-)

---

### Post by HappyFeet on 2009-09-01
Are you new? Anyone who does a dist upgrade 2 months before release deserves what they get. 

Good luck with that.

I'm all for testing out new releases and bug reporting, but it should be done in a controlled manner. For example, I built a second computer just for testing alpha and beta releases. Can't afford a second computer just for testing? That's OK. Just don't do it, or try it out in virtualbox. Btw, I can afford to install Karmic on my main machine, (even though I won't) because all my stuff is backed up on 3 different drives. Geez, what a novel idea! Have a nice day. ;)

---

### Post by Tamlynmac on 2009-09-01
> HappyFeet
I'm all for testing out new releases and bug reporting, but it should be done in a controlled manner. For example, I built a second computer just for testing alpha and beta releases. Can't afford a second computer just for testing? That's OK. Just don't do it, or try it out in virtualbox.

Don't need a separate computer or virtualbox - why not just a separate HDD? I installed a used inexpensive 32 gig HDD and it works great for testing purposes. Plus, it's simple to install and can be disconnected when not in use.

Just a thought.

---

### Post by Jazzy_Jeff on 2009-09-01
The best thing to do with any new distro or new version of the same distro is to back up everything that is important and do a clean install instead of an upgrade. You will find you have a lot less problems this way.

---

### Post by HappyFeet on 2009-09-01
> **Jazzy_Jeff said:**
> The best thing to do with any new distro or new version of the same distro is to back up everything that is important and do a clean install instead of an upgrade. You will find you have a lot less problems this way.

Have you even tried Karmic? At this point in development, it does not matter much how you install it. The reality is, that it's far from ready no matter how you install it.

@Tamlynmac: Yes, I am well aware of using a separate HD to do installs on. But thanks for pointing that out to the unwashed masses.

---

### Post by MartyBuntu on 2009-09-01
Drive imaging.
Always have a good, recent backup before major changes.

---

### Post by Tamlynmac on 2009-09-01
> HappyFeet
@Tamlynmac: Yes, I am well aware of using a separate HD to do installs on. But thanks for pointing that out to the unwashed masses.

Yeah, it was one of the many things I learned from wolfen69 before he left the forum. I sure miss him as he was a wealth of knowledge.

Oh well, just thought it might help others to test new versions or apps prior to installing, I think you can even do it with a usb stick, I haven't tries this - have you? If so what information on setup can you share. Thanks

---

### Post by 3rdalbum on 2009-09-01
No, I'm not new, I just haven't ever tried dist-upgrading to anything that's less than "beta" stage. I thought that Gnome would actually start up, and I didn't expect Bash to segfault all last night :-)

I guess I expected things to work well enough so I could submit bug reports. But now I don't know if the problems are due to the alpha state of the distro, or the bad dist-upgrade.

As I acknowledged in my first post, I really should have backed up my stable system before. That was rather dumb of me to jump in without that safety net. But in future if I want to play around with development distributions I'll set up a different partition for it.

---

### Post by HappyFeet on 2009-09-02
I suggest the [Karmic daily build ]("http://cdimage.ubuntu.com/daily-live/current/") next time you want to play around. It should work out better for you.

---

### Post by 3rdalbum on 2009-09-02
> **HappyFeet said:**
> I suggest the [Karmic daily build ]("http://cdimage.ubuntu.com/daily-live/current/") next time you want to play around. It should work out better for you.

Thanks for the suggestion. I only have a fairly small monthly download limit (5GiB) so that sort of thing is nearly out of the question; I try to download as much Ubuntu-related stuff from my ISP's mirror so it doesn't count toward my limit!

I reinstalled 9.04 anyway, and next time I want to play around I'll just repartition my HDD or do it in Virtualbox. It really is astonishing how quickly you can get an Ubuntu system running with all the "modcons".

---

### Post by HappyFeet on 2009-09-02
> **3rdalbum said:**
> Thanks for the suggestion. I only have a fairly small monthly download limit (5GiB) so that sort of thing is nearly out of the question; I try to download as much Ubuntu-related stuff from my ISP's mirror so it doesn't count toward my limit!

Yeah, I hear the internet in aus. is less than desirable. Over here in the states, I get 100% no limit net. And it's really fast too. I could not imagine having a cap on usage. I like to seed many iso's on bittorrent 24/7, so having a cap would definitely put an end to that. I just added up what I've uploaded in the last 8 weeks, and it's well over 200gb. Plus you need to include all of my downloads. Needless to say, it's a lot. Anyway, good luck.

Btw, anyone who says transmission is no good, has not used it lately. Sure it may not look fancy, but it has all the basics and more. It just chugs along nicely day after day, week after week, month after month. I don't think I've ever had a problem with it.

---

### Post by mdsmedia on 2009-09-03
> **HappyFeet said:**
> Yeah, I hear the internet in aus. is less than desirable. Over here in the states, I get 100% no limit net. And it's really fast too. I could not imagine having a cap on usage. I like to seed many iso's on bittorrent 24/7, so having a cap would definitely put an end to that. I just added up what I've uploaded in the last 8 weeks, and it's well over 200gb. Plus you need to include all of my downloads. Needless to say, it's a lot. Anyway, good luck.

Btw, anyone who says transmission is no good, has not used it lately. Sure it may not look fancy, but it has all the basics and more. It just chugs along nicely day after day, week after week, month after month. I don't think I've ever had a problem with it.
I'm not sure what 3rdalbum's ISP limits are, but I let Transmission run 24/7 because my 5GB DOWNLOAD limit is not affected by my unlimited upload.

---

### Post by 3rdalbum on 2009-09-04
> **mdsmedia said:**
> I'm not sure what 3rdalbum's ISP limits are, but I let Transmission run 24/7 because my 5GB DOWNLOAD limit is not affected by my unlimited upload.

I used to run Transmission seeding between the hours of 10pm and 7am, but I added a 700mb torrent to download during that time once and ended off going over the 5 gigabyte limit within two days. I don't know if Transmission went wild and downloaded 5 gigs, or if someone got into my poorly-secured wireless network, but I'm not taking any chances. 27 days of slow internet was not fun!

---

### Post by HappyFeet on 2009-09-04
> **3rdalbum said:**
> I used to run Transmission seeding between the hours of 10pm and 7am, but I added a 700mb torrent to download during that time once and ended off going over the 5 gigabyte limit within two days. I don't know if Transmission went wild and downloaded 5 gigs, or if someone got into my poorly-secured wireless network, but I'm not taking any chances. 27 days of slow internet was not fun!

It must suck to have to worry about that. I have unlimited net so.......

---

### Post by SeePU on 2009-09-08
Just try the LiveCD to see how much a POS Karmic really is.  

It won't even work on mainstream hardware (locks up/freezes... all that fun stuff).  It's the only development version distro that does that so far.

---

### Post by HappyFeet on 2009-09-08
> **SeePU said:**
> Just try the LiveCD to see how much a POS Karmic really is.  

You don't have to be so dramatic. Judge it *after* it is released. Geez.

---

### Post by Tamlynmac on 2009-09-08
> HappyFeet
You don't have to be so dramatic. Judge it *after* it is released. Geez. 	

No way dude - it should be perfect "NOW". :rolleyes:

---

### Post by cariboo on 2009-09-08
> **SeePU said:**
> Just try the LiveCD to see how much a POS Karmic really is.  

It won't even work on mainstream hardware (locks up/freezes... all that fun stuff).  It's the only development version distro that does that so far.

Just because Karmic doesn't work for you, doesn't mean that it is a problem for everyone

Please post your problems in the support forums. I'm sure there are a lot of people that would be more than happy to help you solve your problems.

The big problem is the graphics chipset in your system, unfortunately the manufacturer has chosen not to support it any more with closed source drivers.

---

### Post by Bucky Ball on 2009-09-08
Why do people do this??? Karmic is not released yet, how can you expect it to be stable???

There is the current (stable) LTS release Hardy 8.04, the current release which some people say is still pretty unstable and others yell 'Rock Solid' Jaunty 9.04 and then there are the 'testing' versions which haven't been released yet (and I would wait six months after the release date if you want stable).

Accordingly, this should be posted in the appropriate 'testing' forum, not 'testimonials'.

---

### Post by 3rdalbum on 2009-09-08
> **SeePU said:**
> Just try the LiveCD to see how much a POS Karmic really is.  

It won't even work on mainstream hardware (locks up/freezes... all that fun stuff).  It's the only development version distro that does that so far.

When I was on Karmic, the hangs were caused by faulty memory (I was still getting hanging after reinstalling 9.04). I took out the older two RAM sticks and I haven't had a hang since.

---

