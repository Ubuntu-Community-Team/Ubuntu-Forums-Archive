---
title: "Why is Ubuntu so good at just... working?"
date: 2013-02-25
forum: The Cafe
---

### Post by James_the_dude on 2013-02-25
I wasn't sure where to post this because I am not really asking for support. I don't need support because I installed xubuntu on my laptop from a usb stick and everything just worked right out of the box!

I tried pure debian. I downloaded an .iso that's over 4 gb, burnt it to a dvd, and installed it on my laptop. Wireless didn't work - naturally. Then I tried again, this time I had a thumb drive with the wireless firmware on it, and when debian said something like "cannot id network hardware, supply firmware if you have it." Still did not work. On top of wireless not working it didn't seem to know what to do with my video card, and I couldn't get the right resolution on my screen. So what exactly did they stuff into that 4+ gigabyte .iso, without being bothered to put in something that would recognize hardware in a year old Asus laptop?

Then I tried fedora. Much smaller .iso. Under 1 gb. Everything kind of worked! I mean, I had wireless working, and my screen resolution worked, but then I rebooted and everything went gray, and xfce kept freezing crashing.

OpenSUSE: similar story, minus the wifi working.

Then I installed xubuntu. I just simply worked! Wireless, video card, no problem. Iso size - I think it was under 800mb. Then I installed it on my 3 year old netbook. Everything worked. Then my girlfriend's 2 year old hp laptop. Everything worked. No problems. Desktop, same story. Some might say "Oh well it is because ubuntu contains non-free code that linux flavors like debian cannot ship with." Okay... but xubuntu is telling me that no proprietary drivers are in use in my system, so I don't think that is the explanation.

I guess I am just curious. Why is it so EASY with x/k/ubuntu? Why does it seem like a battle just to get basic functionality out of other distros?

---

### Post by CharlesA on 2013-02-25
Magic. ;)

---

### Post by MadmanRB on 2013-02-25
Ubuntu works because it offers many things that others dont offer.
It has great hardware detection most of the time.
Plus Ubuntu probably being the most well known linux helps :D

---

### Post by deadflowr on 2013-02-25
It's the shoes.

---

### Post by ACubed10 on 2013-02-25
all the elves working up under the hood.  They are magical! :guitar:

---

### Post by sandyd on 2013-02-25
dude.
Its the robots.
For proof that they run Ubuntu, visit "about:robots" in firefox.

---

### Post by ACubed10 on 2013-02-25
> **sandyd said:**
> dude.
Its the robots.
For proof that they run Ubuntu, visit "about:robots" in firefox.
+1 :p):P

---

### Post by James_the_dude on 2013-02-25
Hah! At this point I'm about ready to believe that it's magic and robots. Maybe even magical robots. ^_-

---

### Post by ACubed10 on 2013-02-25
> **James_the_dude said:**
> Hah! At this point I'm about ready to believe that it's magic and robots. Maybe even magical robots. ^_-
glad you are enjoying it though.  It really is great!

---

### Post by buzzingrobot on 2013-02-25
Different distributions operate by different self-imposed rules and target different audiences.

Ubuntu is based on Debian.  Debian, though, does not target a mainstream audience. Debian targets an audience that wants an extremely stable distribution that they can run for several years, with the confidence that it won't break and that they will receive security updates. This audience is explicitly not interested in staying current with the latest and greatest.

This stable release is, oddly enough, called Debian Stable.  To get there, Debian also uses two quasi-distributions.  One that contains code that has undergone minimal or no testing.  The second code that has a bit of testing, but has not proved itself to be ready for the stable release.

The best way to ensure stability is to test for a long time, fix bugs once something is released, and not add new code into the mix.  Debian Stable often lacks current drivers, programs, etc., for that reason.  Adding those would make it less stable.

The other versions of Debian can include things that don't work for the oppposite reason:  They're very new and have had little or no testing.

Debian, like Fedora and others, has a strict policy of not including non-FOSS code.  So, if your wireless chip needs a proprietary driver to work, then it's up to you to go out and find it.  Ubuntu plays by the same rules, but makes it easier for its users by maintaining some of these files in its repos as "restricted" packages or as "Additional Drivers".  Some other distros do not wish to do that.

Meanwhile, Fedora's purpose in life is to serve as a testbed for Red Hat Enterprise Linux.  As such, it's full of new things and is released every 6 months. Red Hat Enterprise Linux, on the other hand, tries strenuously to avoid adding new versions, instead, fixing bugs and backporting features. 

Ubuntu, as a product supported by Canonical, also has considerably more personnel working on it than some other distributions, which are often the efforts of one or a very few people. It's also used by people who are not FOSS fanatics and who expect it to "just work", being unwilling to trade functionality for ideological rigidity.

---

### Post by kevdog on 2013-02-25
Ubuntu only works until.....it doesn't and then you actually have to put your thinking cap on.  In some ways its really great for new users since most things work out of the box and hardware detection is great.  You could thank the Canonical software engineers for this great feat.

The negative however is that the default user probably doesn't have a clue of what's going on behind the scenes and then gets frustrated really easily when things don't work.  This wouldn't be an issue for example if they had set their system up in the first place with more of a manual rather than automatic method.  

A big difference in the various distributions other than desktops or window managers and stable vs cutting edge packages, is how much "hand holding" they do for new users.  Ubuntu and Mint are two very popular distributions that attempt to do most things automatically.  Gentoo on the other hand does nothing -- everything has to be configured manually.  

In my opinion,once your fairly comfortable with Ubuntu, its always a good idea if you have another computer laying around or with use of VmWare, to try other distributions.  I recently installed Arch on a spare laptop someone gave to me -- it was a used 4 year-old laptop a big corporation thought had no more use.  Arch really doesn't offer me anything more or less than Ubuntu, but I've really grown in my knowledge of Linux in general about troubleshooting problems, since Arch requires a lot of user interaction and configuration during installation.  It's actually helped me learn Ubuntu a lot better in terms of troubleshooting various problems and with kernel tweaking.

---

### Post by CharlesA on 2013-02-25
> **kevdog said:**
> Ubuntu only works until.....it doesn't and then you actually have to put your thinking cap on.

Been there, done that. Most of the time the problem was due to a third party drive/kernel module (thanks RocketRaid!), or a messed up conf file (thanks Match directive in sshd_config). :D

---

### Post by mamamia88 on 2013-02-26
Ubuntu is so good at just working because for the longest time the linux development community has been more worried about making a technically sound product than making it user friendly.  Well once all the technical loose ends are worked out someone else (Canonical) comes along and makes a few minor tweaks here and there to make it more friendly to newcomers and voila. All the really hard work was already done long before Canonical decided to get in the game.  They just decided that they where going to add a layer of polish to make it easier for newcomers.

---

### Post by JDShu on 2013-02-26
> **mamamia88 said:**
> Ubuntu is so good at just working because for the longest time the linux development community has been more worried about making a technically sound product than making it user friendly.  Well once all the technical loose ends are worked out someone else (Canonical) comes along and makes a few minor tweaks here and there to make it more friendly to newcomers and voila. All the really hard work was already done long before Canonical decided to get in the game.  They just decided that they where going to add a layer of polish to make it easier for newcomers.

This, pretty much. What Canonical did was valuable and brought to focus the need for usability, but the "Just Works" part is probably more due to GNU, Linux, and various other open source projects. Personally, every distribution in my experience has "Just Worked" these days.

---

### Post by buzzingrobot on 2013-02-26
Most people have no interest in learning how software really works.  Nor should they.  One of the reasons for the success of Ubuntu is Canonical's recognition of that. Ditto Windows and Apple. People will happily trade openness and flexibility for usefulness and reliability. We have about 30 years of personal computing history buttressing that assertion.

While having the skills and knowledge needed to successfully set up something like Arch or Slackware is useful, I don't think it has much purpose beyond that.  I spent several years with Slackware, and I've used Arch.  But, it's now very much a Been There, Done That, Don't Wanna Do It Again thing for me. I have more pressing and more interesting ways to spend my time than building custom kernels, tweaking init scripts, or chasing down the segfaults.

I used to spend hours, if not days, tweaking my system just to get it to work. Patch the kernel, chase down shaky drivers, etc.   Not any more.

The vast majority of users will never have any reason or desire to have a clue what's going on beneath their GUI.  They expect, correctly and justifiably, that their software works, period. 

Typically, things suddenly "don't work" when users install software that isn't meant to be used on their specific system or is sloppily and amateurishly designed and developed.  Open source is still afflicted with too many of the latter, packages developed and released by hobbyist coders who take little or no action to ensure their software runs on anything other than a machine identical to their machine. It's a tradeoff for the freedom to do whatever you wish.

---

### Post by pqwoerituytrueiwoq on 2013-02-26
> **James_the_dude said:**
> Hah! At this point I'm about ready to believe that it's magic and robots. Maybe even magical robots. ^_-
*magical kitten robots

---

### Post by Linuxratty on 2013-02-26
> **JDShu said:**
>  Personally, every distribution in my experience has "Just Worked" these days.

 MIne as well. In my nine years as a Linux user,I've only hit one bad apple and a couple of disappointments.
 Linspire,my first distro, was wonderful,as was basic Mepis,Fedora and all the Ubuntu based distros.

---

### Post by James_the_dude on 2013-02-26
This "handholding" seems to be done really well. 

Back when I first tried linux probably 6+ years ago it was a pain. A friend of mine recommended I try kubuntu because he heard me complaining about vista on my then-new laptop. Wifi, video, sound, even my touchpad all didn't work right or didn't work at all.

Now when I pop in that xubuntu stick and hit install, I have a fully functional operating system in about an hour.

It has gotten to the point where things like hardware recognition work even better than in windows. At least for me. And I would like to stress the point that my current laptop was originally a windows 7 laptop.

When I did a clean windows 7 install because I needed to use SolidWorks, the touchpad was messed up, the wifi didn't work, the video was not properly supported. Even after downloading the drivers from asus and installing them certain things were still buggy. In the end I had spent at least 8 hours, and I had a more buggy, sluggish OS blemishing part of my hard drive. Whats worse is that when I called Asus and said "I am installing windows. This is my laptop model and serial #. You have different versions of drivers available, what ones do I want, or how do I figure out what I want?" The response was "Uhhhhhhhhhhhhhh......... let me ask my supervisor........................... I know not how to fix that. Uhhmm... you can send it in for repair?"

I'd like to stress the fact though that I didn't start this thread just to vent some fanboyism, and say "ubuntu rocks everything else sucks." I hope I haven't given that impression. All the other serious flavors have their merit and I really wish I did know enough about this stuff that I could just pop in debian (or something) and configure it so that everything works. I really really am just curious as to why it is so much easier with ubuntu, and I guess that question has been answered. More developers, non-foss software, popularity, and goal of being functional even for the non-savvy average user.

---

### Post by ShadowGuardian on 2013-03-06
I think (and my knowledge is limited) that since Ubuntu (Canonical) relies on donations and such, they have to crank out a good reliable product.  They cant rely on people's proprietary needs to get money (dual-booters know what I mean). 

Oh and about "when ubuntu breaks":

When Ubuntu doesnt want to work, its a chance to learn and to fix.  (granted there are always exceptions, but they are rare)

But remember when Windows doesnt want to work, its alot of get-nowhere research, a phone call, sitting for hours on hold while microsoft tries to find someone who knows what they're doing, having to install something that you may have to pay for or getting some weird work-around that leaves you thinking "they could have designed that easier".  You then decide to do more research and. . . the gates of heaven open up as you discover the Ubuntu webpage and see the phrase "It's free and it always will be".

But thats just my opinion :)

---

### Post by iamkuriouspurpleoranj on 2013-03-06
Yeah - also had a headache with drivers reinstalling Windows without the recovery partition. I think everyone should have to do this at least once. Then they would understand how we get a very good deal with Linux.

As for Slackware and Arch teaching you about Linux: maybe that's true. On the other hand, I don't see why working your way from cover to cover of an Ubuntu, Fedora or OpenSUSE manual wouldn't also teach you a lot about Linux.

My big fear with Arch is screw-ups/vulnerabilities that I can't see. I can tell if I've not configured sound or wireless correctly because these are easy to check but other more internal aspects, how would I know? I'll wait a couple of years first... while my Gentoo kernel compiles :-/

PS. I do want to learn Slackware and Gentoo but I'm really not ready for them yet. Just like I'm not ready for FreeBSD. I'm almost ready for Arch but something in me says "no, proceed straight to Slackware/Gentoo".

---

### Post by buzzingrobot on 2013-03-06
> **ShadowGuardian said:**
> ...Ubuntu (Canonical) relies on donations and such...

Canonical is a corporation selling services and technical support.  That's much the same line of business that Red Hat and Suse are in.

---

### Post by blatz89 on 2013-03-07
Ubuntu works with Black Magic and the Departed Souls Of The Innocent (tm.)

Nah, just kidding. :3

---

### Post by mamamia88 on 2013-03-07
> **iamkuriouspurpleoranj said:**
> Yeah - also had a headache with drivers reinstalling Windows without the recovery partition. I think everyone should have to do this at least once. Then they would understand how we get a very good deal with Linux.

As for Slackware and Arch teaching you about Linux: maybe that's true. On the other hand, I don't see why working your way from cover to cover of an Ubuntu, Fedora or OpenSUSE manual wouldn't also teach you a lot about Linux.

My big fear with Arch is screw-ups/vulnerabilities that I can't see. I can tell if I've not configured sound or wireless correctly because these are easy to check but other more internal aspects, how would I know? I'll wait a couple of years first... while my Gentoo kernel compiles :-/

PS. I do want to learn Slackware and Gentoo but I'm really not ready for them yet. Just like I'm not ready for FreeBSD. I'm almost ready for Arch but something in me says "no, proceed straight to Slackware/Gentoo". The beauty of arch is that it gives you the exact system you want without really having to understand all of it right away. Arch spells out everything so clearly that even I can understand most of it.    I went straight from Ubuntu to Arch and as long as you are able to use common sense and read for comprehension then you'll be fine. I just don't see the point in Gentoo since it's basically Arch but with compiling everything.  Personally I'd rather give up the little speed advantage that Gentoo may have for the convenience of using binaries.   What you save a few milliseconds here and there but on the other hand you leave your pc on overnight to compile everything and hope something doesn't go wrong in the process?   No thank you.   I'm all for learning linux and stuff but you have to draw a line in the sand somewhere.  Personally my time with arch has taught me skills that will be useful no matter what distro I use in the future.  Will I use it again as my primary distro again anytime soon?  Probably not.  As long as a distro comes with a pretty close to stock xfce setup and isn't noticeably sluggish I'm fine nowadays.

---

### Post by codingman on 2013-03-07
It's always fun to play around in Linux, I first began to use Fedora, and I really liked it, especially after Windows failing on me. Then, I heard about Ubuntu, and decided to try it. I did a live CD and was surprised to find lots of applications pre-installed, for I had to install lots of applications in order for Fedora to be functional for me. I have gone through a lot of distros, most of them ubuntu based, and have found that the original Ubuntu is much better than many others.

---

### Post by blackbird34 on 2013-03-10
Ubuntu just worked its magic again... I thought i was in dependency hell, Synaptic was wagging its little fists at me, then I resigned myself, burned Precise on to a fresh USB stick and rebooted a couple of times, tried one last apt-get install -f ... and presto, it worked! 
This kind of little excitements keeps me going hahaha... I've been taking "Way too much Ubuntu" :D but it works wonders!

---

### Post by pinballwizard on 2013-03-10
Nice FOSS vs Hardware thread.

---

