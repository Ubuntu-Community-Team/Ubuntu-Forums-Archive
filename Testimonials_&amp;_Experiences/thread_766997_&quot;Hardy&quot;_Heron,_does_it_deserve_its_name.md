---
title: "&quot;Hardy&quot; Heron, does it deserve its name?"
date: 2008-04-25
forum: Testimonials &amp; Experiences
---

### Post by Jadd on 2008-04-25
Alternate title: So disappointed with Hardy Heron.

**(If you want to skip with my rather long life story with Ubuntu and go straight to the Hardy Heron bit, skip the next five paragraphs and start reading from (And now Hardy Heron))**

Let's start from the beginning of my story with Ubuntu. A few years ago, I came across a blog entry in [my.opera.com](http://my.opera.com) about an icon set for a thing called Ubuntu. I had never heard of Ubuntu before, so I decided to do a search for it. I found it, and I thought, hmm, I've been wanting to retry Linux for some time now, but the CDs I have (OpenSUSE and I think Red Hat desktop) are a few years old. Clicked get Ubuntu, was disappointed to find that it was 690MB big. A few more clicks, and I was wonderfully surprised to find that they would send me a few CDs, even a suggested five, to anywhere in the world, for free! I thought, why not? And ordered some. Some people wonder why Ubuntu is spreading so fast compared to other Linux distros, and for some reason they seem to forget shipit. If Canonical asked for donations I'd donate to shipit.

Ubuntu Dapper Drake was new to me. I was pleasantly surprised by the sheer number of programs that exist for Linux (I'd believed the myth that programs are only really written for Windows), by the live CD, by GNOME (I liked it better than the vague memory of OpenSUSE's KDE) I was *un*pleasantly surprised by the number and the size of the updates, the fact that sound didn't work at all, the fact that couldn't get something called '3D acceleration' to work, and how slow Ubuntu is (as slow as Windows). Running gedit still takes a random amount of time to load, sometimes a whole half-minute. Why? Ubuntu jammed quite frequently as well. Troubleshooting sound gave me a headache (it still does), and I was disappointed to learn that S3 has no decent linux drivers for their graphics and probably never will. I had to compile a driver from source, thankfully there was a guide to step me through that. But I was most impressed by the Ubuntu promise and the Ubuntu philosophy, and decided to keep trying it, because those were causes that I wanted to help, instead of Microsoft's causes.
Edgy Eft came out. I tried to upgrade to it, and was disgusted with the huge amounts of uninterrupted downloads Ubuntu needed, but I did it anyway. Sound still wasn't fixed, compile from source again. It was so frustrating.
Downloaded and burned Feisty Fawn's live CD, only to discover you can't use that to upgrade, so I did a fresh install. Sound now worked (yay!), and I discovered Amarok. Amarok is what made me stay with Ubuntu for over a year, I just loved it. (BTW, Amarok is now planning to make a Windows version of its software, a bad move in my opinion.)
Release after release, Ubuntu fixed one or two hardware issues, and things just got better if I waited. This is how it should be.

Then I bought a laptop. I really wanted to get a Ubuntu Dell laptop, because I wanted to support Ubuntu and I was fed up with hardware issues, but in the end, a got a Packard Bell laptop with Vista on it, because I couldn't wait for it to arrive in the post. (Long story.) The hardware issues returned to haunt me. I couldn't get the wireless working (in Ubuntu, not Windows of course), despite the 'wonderful' Network Manager that was now included by default in Feisty (or was it Gutsy?). It would only work if I made the wireless security virtually nil. I can't stand Ubuntu without Internet; I need the community, I need to search on the Internet if something goes wrong, I can't just ask friends and family: they only know Windows. The headphones refused to work, and so did the microphone jack, so goodbye Skype, goodbye music, goodbye Amarok :`(. I returned to Windows, even Vista, until I finally discovered Wicd. Wicd fixed the Internet problem, I returned to Ubuntu. Tried a bunch of stuff to fix the sound problem, including installing OSS and pulseaudio, nothing worked.

Gutsy came out, I got to play with a decent Compiz Fusion. I love this stuff, I really do. Subscribed to the [Linux Action Show](http://www.linuxactionshow.com), got into the community, discovered games: Tremulous! Warsow! Spring RTS! These were fun, and they actually worked better than in Vista! (OpenGL drivers aren't functional yet for ATI graphic cards under Vista) Gutsy detected and installed a network printer with ease, Vista still can't print. I was now torn between two systems: Vista for music, Ubuntu for printing and other cool stuff.

The hardware support wasn't perfect, but the wireless worked, and 3D acceleration worked, I was happy. I couldn't hibernate or suspend, the screen sometimes became very dim for no reason, the headphones and mic didn't work, but none of these, except the sound stuff, bothered me very much.

**(And now Hardy Heron!)**

I had high expectations for Hardy Heron. Now that the daring enabling of Compiz Fusion to compete with Aero was over with, I hoped the Ubuntu team would concentrate on hardware issues. My number one hope was that they would fix Network Manager, Ubuntu without the Internet is like an Oasis with no water. It's useless. And I knew it was possible, because the GPL'd Wicd managed it.

I downloaded the beta of Hardy. I was so disappointed. It had problems. Today, I installed the final release of Hardy. It had exactly the same problems, despite so many people having reported the issues! **Unfixed problems:**
[LIST]
[*]Network Manager still wasn't fixed, it was just as bad as before, I had to install Wicd again. Wicd had improved though, GUI-wise. I had reported the bug before 24Aprl, just to be marked along with tons of others as a duplicate of a well known bug. This bug wasn't fixed for the 24th. People, without Internet, Ubuntu is despair. Don't disconnect people from it. A release codenamed, not even, publicly named "Hardy" should make that a priority. No-one can blame the hardware manufacturers, because the open source Wicd managed to do it right.
[*]The headphone and microphone jack still don't work. Reported bugs, nobody seemed to have a clue how to go about troubleshooting this. Taking the trouble to file a bug, just to have ignored, is frustrating.
[/LIST]
So my high hopes for Hardy Heron were dashed. Unfortunately, Hardy Heron seemed determined to upset me even more, because it broke things that worked perfectly in the Gutsy release. **New problems:**
[LIST]
[*]Setting a MS-Workgroup name for your computer renders Ubuntu useless, because it breaks sudo. This bug was reported way in advance by a lot of people, you have the duplicates and the many [forum threads](http://hightechsorcery.com/comment/reply/112) to prove it. Running anything with sudo gives you an 'unable to resolve host-name' error, using the administrator tools of course are even more frustrating, since gksu always fails silently. You just sit there wondering when on earth the app's going to finish loading. There is a work-around, but apparently, the Ubuntu developers would rather people do this manually then do it for them. The workaround is editing  /etc/hosts (as root of course, despite a broken sudo), and removing one word. That's it. Was that so hard?
[*]The text installer's broken. Choosing install or even check CD will just give you a blank screen. You have to add vga=771 to the boot options. How anyone is supposed to figure this out is beyond me. I only knew how because I remember somebody mentioning it in the forums. The F1 help included just isn't friendly enough for a beginner. May I remind you again, that I didn't have this issue with the Gutsy text installer.
[*]Ubuntu Heron freezes randomly. A total crash, nothing moves anymore, and ctrl-alt-F1 to F7, ctrl-alt-backspace have no effect. I reported a bug, this time, I was given assistance on troubleshooting, but it required another computer and on SSH connection, and I couldn't do that. I hoped it would be fixed before the final release, but it wasn't! I've been running Gutsy since before it was released, and I never had this problem. I've had this problem several times with Heron. To be fair, it might be Wicd'- fault, but I can't go without Wicd since Network Manager doesn't work.
[/LIST]

Hardy Heron did fix some hardware issues, for example, hibernate now works, and the screen brightness panel applet actually works now. But I'd rather go without them then go without the Internet and go with constant crashes.

I've always loved Ubuntu. They haven't fixed some problems as fast as I would have liked, but they did fix stuff, slowly but surely. They moved forward. Now I feel almost heart-broken because they actually moved backwards in a release called "Hardy", and what's more, an LTS release, which probably will be distributed on shipit.

I loved Ubuntu, but I did not recommend it to anyone, because of these hardware issues. Despite that, several people have asked me to install Linux on their machines (it *is* gaining momentum), and every single one of them have had deal-breaker hardware issues: X and the networking system. X would refuse to work on an installed Ubuntu despite working great on the live CD, installing a restricted driver would break X (the new bulletproof X never showed its face)... I always had issues getting people's wireless to work, as well as they USB ADSL modems. But at least I didn't recommend this headache to them, I enjoy troubleshooting my own stuff, but I don't want to have to do it for other people's systems just to get the basic necessities (X and a connection to the Internet)

I love the Ubuntu community, more often than not, they help you out with your problems. But no Internet access means no community, no X means no graphical browser. I had to learn how to use lynx, not a user-friendly program.

I dislike the fact that we're encouraged over and over again to file bug reports, only to have them ignored. You don't even get a 'read' flag.

Why did we have to rush Heron? Dapper LTS was released in June, we rushed Heron to April, even if that meant including beta software. Yes, Firefox on Hardy is beta!

I guess for now I'll stick with Gutsy Gibbon. Not that Hardy doesn't have some great features (speedy boot-up, for one), but I would be more than satisfied with a Hardy that is Gutsy minus hardware problems.

---

### Post by hurtstotalktoyou on 2008-04-25
What it comes down to is this:  Hardy Heron appears to have less hardware support than Gutsy Gibbon.  Whatever the reason for this, it is unacceptable.

I have spent several hours, now, wrestling with Hardy, and I *still* can't get it to work.  I too have had trouble with the mic input.  Unfixed problems from Gutsy:

1.  Neither Audacity nor any other application can record the stereo mix computer audio ("what u hear" in Windows).

Additional woes, which are new to Hardy:

1.  My 17" CRT display is unsupported (?????).
2.  Twinview clone displays (displaying the same input on the monitor and TV at the same time) must be manually reconfigured after each reboot.
3.  Neither Audacity nor any other application can record from my mic.

This is absolutely unacceptable.  I understand that Hardy has some new features which some folks wanted to get their hands on, but that's what beta is for.  The final release date should have been pushed back to deal with these issues.  At the very least, Hardy Heron should have been advertised as having reduced hardware compatibility compared to Gutsy.  I am quite irritated at having wasted so much of my time without having resolved any of the above problems

---

### Post by karellen on 2008-04-25
thanks for the quick feedback guys. I was thinking of giving hardy a try, but after a number of people reported having troubles with this (allegedly very stable lts release) I'm not so sure, especially as I have a perfect working system with gutsy and fedora 8...

---

### Post by wirelessmonkey on 2008-04-25
Jadd,  
I'm afraid I don't have any of the problems on my 4 Hardy boxes, which inclines me to think that there may be another factor such as hardware or driver dysfunction.

Hurtstotalk..
1 & 2, I had this problem in gutsy, but assuming you have the nvidia drivers installed, you can fix twinview and resolution by running this from terminal
#~ sudo /usr/bin/nvidia-settings 

You'll get the nvidia display manager.  After configuring and testing your settings, click the 'save to configuration' button.  It will stay this way until you update drivers or reconfigure Xorg.conf

Without running nvidia-settings under sudo, you can set your current display environment, but it will not save it to the configuration.


Best of Luck

---

### Post by hurtstotalktoyou on 2008-04-25
> **wirelessmonkey said:**
> Hurtstotalk..
1 & 2, I had this problem in gutsy, but assuming you have the nvidia drivers installed, you can fix twinview and resolution by running this from terminal
#~ sudo /usr/bin/nvidia-settings 

You'll get the nvidia display manager.  After configuring and testing your settings, click the 'save to configuration' button.  It will stay this way until you update drivers or reconfigure Xorg.conf

Without running nvidia-settings under sudo, you can set your current display environment, but it will not save it to the configuration.

This worked perfectly, thanks!

---

### Post by MNICY on 2008-04-25
In my opinion, Firefox 3 Beta is much more stable then Internet Explorer Stable.

Beta does not necessarily mean it does not work.
If the Ubuntu team thinks Firefox 3 is stable enough to include with Ubuntu, then I am willing to try it out.

---

### Post by la3875 on 2008-04-25
In time it might earn its name...

Wireless broke between Beta and RC and video/desktop effect failed to work. Also a minor quirk on hibernating, when it woke up, Evolution was offline. In my opinion the current release is nothing more than RC2 and has much to be repaired. I'm back to Gutsy until they can resolve the various issues.

---

### Post by xjgnsdof on 2008-04-26
On my main rig (see sig for specs) I get random lock-ups in Hardy, which I got in Gutsy, that are caused by NVIDIA drivers. My two laptops, one from 2002 and the other from 2005, never lock up. Once a better driver appears, this problem should disappear.

I've been using Ubuntu since Feisty Fawn, and I think that Hardy Heron is awesome. My Linksys wireless adapter and video card worked "out-of-the-box," the OS as a whole is noticeably faster, and the new default apps were admirable. I know it has only been a few days (as of this post) since Hardy dropped, but those are my first impressions.

---

### Post by Jadd on 2008-04-26
> **wirelessmonkey said:**
> Jadd,  
I'm afraid I don't have any of the problems on my 4 Hardy boxes, which inclines me to think that there may be another factor such as hardware or driver dysfunction.

Best of Luck

I'm afraid that it can't be the hardware or the driver's fault this time, 'cause some these issues weren't an issue with Gutsy. The Heron introduced these deal-breakers: disfunctional sudo, disfunctional text installer and constant random freezes. :(

---

### Post by karellen on 2008-04-26
I fail to understand why on Earh break something that already works on a particular piece of hardware; if a distro worked well in the past, there's no excuse for not doing so right now

---

### Post by Jammy4041 on 2008-04-26
Give Hardy Heron Time- remember- it's only been out for just two days now as a fully fledged stable release. Soon software developers will release better versions, just for hardy. Hardy has at least three years to prove itself.

---

### Post by BLTicklemonster on 2008-04-26
> **Jammy4041 said:**
> Give Hardy Heron Time- remember- it's only been out for just two days now as a fully fledged stable release. Soon software developers will release better versions, just for hardy. Hardy has at least three years to prove itself.

Remember, Hardly Helion has only been out two days now as a fully fledged WHAT? Stable release? I think they jumped the gun on this one, and it's the black eye that everyone else has been praying for. 

This release needs to be pulled, guys. I love Ubuntu, but Hardy is definitely not ready for public release. It may work on some people's computers with no problem and other's with serious tweaking but the average Joe who comes along, burns a cd, tries to boot from it, and watches in awe as it fails to respond is going to never look back.

Pull the plug on this one now!

---

### Post by karellen on 2008-04-26
> **Jammy4041 said:**
> Give Hardy Heron Time- remember- it's only been out for just two days now as a fully fledged stable release. Soon software developers will release better versions, just for hardy. Hardy has at least three years to prove itself.

why should it be given time for the things that had been already working in gutsy? or feisty

---

### Post by Jadephyre on 2008-04-27
exactly my point... although i'm not using it at the moment, Gutsy has worked for me (apart from the fact that Wireless had to be realized with NDISWRAPPER and that the OpenSource Driver didn't work for my ATI X1100).
I downloaded Hardy Final (32bit & 64Bit) and it just does not boot the Live Environment... at least not without a slew of Boot Parameters added.
The Kernel which is used in the Final is, at least i guess so, the showstopper that is causing all those headaches.
If they do not release 8.04.1 REALLY fast, they are going to alienate a lot of users with all those Problems because the Phrase "It just works" just doesn't work at the moment.

The immense string of Boot Parameters alone have thrown me off of installing Hardy so far.

EDIT: At the Moment i'm using Linux Mint 4

---

### Post by balaji.ramasubramanian on 2008-04-28
The one thing I *hate* about Ubuntu is uncertainty in hardware stuff. i have seen Windows unstable too, but then it comes with support. The problem with Open Source Software as I realize over the time I have used it is that there is **no** (I repeat *no*) support for *your* problems.

I read through the problems that many of you are reporting. I don't have *all* of the problems, but I have some other different problems in Ubuntu. The worst part is that nobody in Canonical seems to care if some people can't use their software. Your bug report is totally ignored. In addition, the smug geeky idiot from Canonical will reply to your bug reports as if you made a mistake buying a PC and that the software is sacrosanct. The attitude **must** change. I'm an engineer too (electrical) and can understand software and C code almost well although I just don't take the trouble to write code. I'm not obliged to do so and I'm not interested in wasting my time reading some documents on Linux kernel. What I care about is: Does my system do what I want it to do?

Since Dapper, I have not done a fresh install of Ubuntu and so I wonder how much that contributes to the slow response Gutsy gives, when compared to my older Dapper machine.

The one thing I can't understand is why can't Linux guys do something to help people use Windows drivers in Linux. Write a software that will enable the drivers to work on Linux. I'm not talking about an installation program for any new hardware, but a driver file that can be extracted from the Windows driver and used in existing Linux applications.

This in fact is precisely what is done for the nVIDIA driver. If that can be done, I'm pretty sure one can find a way to do it for all drivers. It is a matter of writing code to extract useful stuff from Windows drivers and doing the required work. Every hardware comes with a CD and they promise to work with Windows. Why not use that stuff and make it work for Linux. I mean there are only a few interfaces and peripherals. The protocol is in the driver provided by the hardware guy and you should just reuse that. If the whole philosophy of Open source comes from software re-use, we should work on re-using drivers too.

The other thing that Canonical **must** do is to work with a very large base of hardware and peripheral providers. They should invest on this and I will donate for that too. When you work with a **large** (not just the major) peripheral providers and write software that works just out of the box, more and more people will use Linux. Countries like India and China will stop investing in a Microsoft license and instead just get Ubuntu. What that does to your software now is that all hardware providers start writing drivers that work with Ubuntu. The peripheral providers are writing Windows drivers not because Microsoft pays them (I'm sure Microsoft does not pay a penny to the peripheral providers for hardware support.) but because people use Microsoft Windows. If now we change that popularity to Ubuntu, I'm pretty sure Microsoft will have a run for the money and still no peripherals will stop writing software for Ubuntu.

---

### Post by vexorian on 2008-04-28
Just give it time, I heard exactly the same thing about gutsy when it was first released, it is _AWESOME_ to see how people now say hey will stick to gutsy...


> **balaji.ramasubramanian said:**
> The one thing I *hate* about Ubuntu is uncertainty in hardware stuff. i have seen Windows unstable too, but then it comes with support. The problem with Open Source Software as I realize over the time I have used it is that there is **no** (I repeat *no*) support for *your* problems.


Who says it doesn't? If you want support go pay it.

---

### Post by mengtze on 2008-04-28
Well, I am going back to 7.10. In a year maybe I will try heron again.

---

### Post by Bog_Warrior on 2008-04-28
Ubuntu does not offer support... where are we?  THIS is the support for Ubuntu and the strength of the OS.  If this forum can't help for free, you can pay for support.  Microsoft provides help and support??? it's called reboot.  

It seems so easy to make an OS work, but when you think about taking an infinite number of devices, with an infinite number of applications, and try to write an OS to get these components to work with everyone, every time out of the box.... you can't even buy an OS with those specifications.  

I only come to this thread when my system is working, and to the others to get priceless support.

Thanks to Ubuntu.

BW

---

### Post by wirelessmonkey on 2008-04-29
> **Jadd said:**
> I'm afraid that it can't be the hardware or the driver's fault this time, 'cause some these issues weren't an issue with Gutsy. The Heron introduced these deal-breakers: disfunctional sudo, disfunctional text installer and constant random freezes. :(

Due to the number of successful Hardy installs, it is only reasonable to assume that there is a problem on your end.  Perhaps your install media is bad, perhaps one of the drivers has been changed or updated for some piece of hardware, perhaps there is a filesystem or HDD problem.  It is unreasonable to assume the OS is faulty, when there is plenty of evidence for successful installs on a variety of hardware.

I suggest burning new install media, at the slowest possible speed, using the alternate install cd image, so you can watch for potential errors. You may also want to run memtest86 from the liveCD, just to make sure there are no memory problems.  

Most of all, though, I suggest that if you want to run Hardy you should disregard your Feisty/Gutsy experiences, and start from scratch.


Best of Luck

---

### Post by BLTicklemonster on 2008-04-29
> **wirelessmonkey said:**
> Due to the number of successful Hardy installs, it is only reasonable to assume that there is a problem on your end.  Perhaps your install media is bad, perhaps one of the drivers has been changed or updated for some piece of hardware, perhaps there is a filesystem or HDD problem.  It is unreasonable to assume the OS is faulty, when there is plenty of evidence for successful installs on a variety of hardware.

I suggest burning new install media, at the slowest possible speed, using the alternate install cd image, so you can watch for potential errors. You may also want to run memtest86 from the liveCD, just to make sure there are no memory problems.  

Most of all, though, I suggest that if you want to run Hardy you should disregard your Feisty/Gutsy experiences, and start from scratch.


Best of Luck

Due to the number of UNsuccessful Hardy installs, it is only reasonable to assume that there is a problem with Hardy's development. Especially when one considers that so many of these people here (myself included) had no real problems with any release so far up until now. 

Just because everyone on your block dresses like you doesn't mean that you're normal...

Google this:

Hardy Heron 8.04 problems site:ubuntuforums.org

and see how many hits you get.

Something like this?
Results 1 - 10 of about 70,600 from ubuntuforums.org for Hardy Heron 8.04 problems

And it's been out how long?

---

### Post by karellen on 2008-04-29
> **BLTicklemonster said:**
> Due to the number of UNsuccessful Hardy installs, it is only reasonable to assume that there is a problem with Hardy's development. Especially when one considers that so many of these people here (myself included) had no real problems with any release so far up until now. 

Just because everyone on your block dresses like you doesn't mean that you're normal...

Google this:

Hardy Heron 8.04 problems site:ubuntuforums.org

and see how many hits you get.

Something like this?
Results 1 - 10 of about 70,600 from ubuntuforums.org for Hardy Heron 8.04 problems

And it's been out how long?

from what I've read in "testimonials & experience", everyone who says that Hardy's not perfect (or at least ten times better than the previous version) it's either a troll or simply a whiner.
it doesnt' matter that were things that worked in feisty and don't work in Hardy, the final-stable-ready-for-use-version...

---

### Post by JunCTionS on 2008-04-29
I guess every computer has it's own problems, mine had a sort of decreased hardware support with Gutsy (compared to Feisty) and is now almost fully supported on Hardy Heron.
Well, almost, headphone jack doesn't seem to work yet and my webcam (which didn't work at all before) now has video, but not the mic, yet.
My experience has been a better more stable Kubuntu on my Toshiba Sattellite A105-S4677 (if you've got one, I recommend Ubuntu/Kubuntu, I've also tested my girlfriend's A105-S4344 which was completly functional with Gutsy too).
I'm glad it seems that the OS is making good progress although it may not be perfect. To the unlucky ones, have patience, you're getting much more than your money's worth. And keep an eye out on the forums for your model (or post each particular problem and see what you get).

The headphone thing is probably easy to fix and the webcam seems promising (both didn't work at all in Gutsy).

---

### Post by Jadephyre on 2008-04-29
yeah right, just because i could run all Versions of Ubuntu before 8.04 means that NOW after the Release of Hardy my Hardware is defective... as if.

---

### Post by Jadd on 2008-04-29
> **wirelessmonkey said:**
> Due to the number of successful Hardy installs, it is only reasonable to assume that there is a problem on your end.  Perhaps your install media is bad, perhaps one of the drivers has been changed or updated for some piece of hardware, perhaps there is a filesystem or HDD problem.  It is unreasonable to assume the OS is faulty, when there is plenty of evidence for successful installs on a variety of hardware.

I suggest burning new install media, at the slowest possible speed, using the alternate install cd image, so you can watch for potential errors. You may also want to run memtest86 from the liveCD, just to make sure there are no memory problems.  

Most of all, though, I suggest that if you want to run Hardy you should disregard your Feisty/Gutsy experiences, and start from scratch.


Best of Luck
Gutsy worked, Hardy didn't, it must be the hardware's fault?
Did I mention that one of the new problems Hardy Heron introduced was a broken text installer? (I did.) Unfortunately, I forgot to mention that I did an md5sum check on the .iso file, and on all the files on the burnt CD, so that can't be the problem. Memtest shouldn't be necessary, I managed to load a Hardy beta live CD.
And why should I ignore previous Hardy/Feisty experiences? Ignoring Windows experiences I can understand, but ignoring previous better Ubuntu Linux experiences, I cannot.

---

### Post by bigbrovar on 2008-04-29
>  Originally Posted by wirelessmonkey  View Post
Due to the number of successful Hardy installs, it is only reasonable to assume that there is a problem on your end. Perhaps your install media is bad, perhaps one of the drivers has been changed or updated for some piece of hardware, perhaps there is a filesystem or HDD problem. It is unreasonable to assume the OS is faulty, when there is plenty of evidence for successful installs on a variety of hardware.

I suggest burning new install media, at the slowest possible speed, using the alternate install cd image, so you can watch for potential errors. You may also want to run memtest86 from the liveCD, just to make sure there are no memory problems.

Most of all, though, I suggest that if you want to run Hardy you should disregard your Feisty/Gutsy experiences, and start from scratch.


Best of Luck
ur post should be similar to something u would get from a microsoft support  team if u contacted them about a problem with vista .. i started ubuntu with feisty and sine then i have never had the kind of problems am facing with Hardy .. the whole things has this feeling of being rushed .. u need to see the thread here to understand that hardy has a big porblem i dont think any ubuntu release ever caused this much storm.. when i see a post about pple not having problem what so ever with hardy i just wonder what planet their from.. cus my system seem to lock up at the slightest excuse.. now i cant use opera,or firefox cause what i would get is a system freeze.. the fact that 50% of users have no problem with hardy means its not ready for public release ..

---

### Post by Johnathon on 2008-04-30
Ubuntu has had far more successful installs than a 50% failure rate. Trust me, if there was a 50% failure rate, everyone who has an interest in seeing Ubuntu fail would be screaming it as loudly as possible.

If you have a problem **ASK FOR HELP**. You've got here, the mailing lists, the wiki, IRC and the answers system. If someone doesn't know how to help you, I'd be very surprised.

If you have a problem that you think IS A **FAILURE** IN **SOFTWARE** then **REPORT A BUG**. Don't be surprised if your bug doesn't get looked at for a while, we have at the moment, 21,000 new (un-looked at) bug reports. We'll get to you, it just might take a while. **BE PATIENT.**

---

### Post by bilal.17 on 2008-04-30
> **bigbrovar said:**
> ur post should be similar to something u would get from a microsoft support  team if u contacted them about a problem with vista .. i started ubuntu with feisty and sine then i have never had the kind of problems am facing with Hardy .. the whole things has this feeling of being rushed .. u need to see the thread here to understand that hardy has a big porblem i dont think any ubuntu release ever caused this much storm.. when i see a post about pple not having problem what so ever with hardy i just wonder what planet their from.. cus my system seem to lock up at the slightest excuse.. now i cant use opera,or firefox cause what i would get is a system freeze.. the fact that 50% of users have no problem with hardy means its not ready for public release ..

 Its true that Hardy does have this problem of lockup, but if it really hit that many people, then we would see everybody complaining about it. My desktop has yet to freeze in Hardy, and hopefully it wont. Also im not seeing this big storm that Hardy has caused, every single version came out with some bugs, some a bit more than others, but i wouldnt say that Hardy was rushed. I was using it since beta and i havent had any problems with it, on both my desktop and my laptop.

---

### Post by vexorian on 2008-04-30
> **BLTicklemonster said:**
> Google this:

Hardy Heron 8.04 problems site:ubuntuforums.org

and see how many hits you get.

Something like this?
Results 1 - 10 of about 70,600 from ubuntuforums.org for Hardy Heron 8.04 problems

And it's been out how long?
Hmnn, this is a fallacy of authority, I think somebody should create a new fallacy name for the assumption number of hits in google means anything.

But, let me correct you.

[Hardy Heron 8.04 problems site:ubuntuforums.org] 74100

That's the ultimate ambiguous search phrase, a lot of those results are totally unrelated or are advertisements for hardy.

Anyways, judging by the size of this thread, and plenty of blog posts I've read, I gotta say Hardy seems a lot more stable than gutsy in its first week.

[Gutsy Gibbon 7.10 problems site:ubuntuforums.org] 2690000 results!

---

### Post by wirelessmonkey on 2008-04-30
> **bigbrovar said:**
> ur post should be similar to something u would get from a microsoft support  team if u contacted them about a problem with vista .. i started ubuntu with feisty and sine then i have never had the kind of problems am facing with Hardy .. the whole things has this feeling of being rushed .. u need to see the thread here to understand that hardy has a big porblem i dont think any ubuntu release ever caused this much storm.. when i see a post about pple not having problem what so ever with hardy i just wonder what planet their from.. cus my system seem to lock up at the slightest excuse.. now i cant use opera,or firefox cause what i would get is a system freeze.. the fact that 50% of users have no problem with hardy means its not ready for public release ..

Gag me... I'm not telling you anything abnormal.  Between Gutsy and Hardy, there have been a number of changes in core system applications, not to mention peripheral applications.  Some of the new things in Hardy require other packages/apps to be upgraded as well.  If these upgraded apps (i.e. drivers) have issues with other system files, or HARDWARE, you will see, well, exactly what we are seeing.  Problems.   Start from scratch, verify where the problems lay. Submit bug reports if necessary.  Nothing I said,or intend to say, is intended as an insult to you, your intelligence, or your computer.  
The fact that I'm not having problems, and that I'm not using special boxen, nor am I a developer/programmer that could fix said problems, implies that there may be a way to track down and deal with the issues you all are having.  The Best Way (IMHO) is to start from scratch, and not assume that anything works.  Then you can find out where your issues are coming from in a linear, step-by-step process.

Believe it or not, I am trying to help. 

So, as I said before.... Best of Luck.

---

### Post by mscoxoh on 2008-05-04
Not just Ubuntu, but all Linux systems, remind me of owning a John Deere tractor from the 50s or 60s. They're great machines if you like to constantly tinker (and you KNOW HOW). But if you aren't a small-engine mechanic and just want to put in the oil and gas then jump on and start mowing, you're in for many frustrations. I'm OK using Ubuntu as a server, but wouldn't think of making it a desktop (Windows) replacement. For my everyday use, I want a unix system, but a stable, tinker-free environment, too, so I got a Mac.

---

### Post by BLTicklemonster on 2008-05-05
> **vexorian said:**
> Hmnn, this is a fallacy of authority, I think somebody should create a new fallacy name for the assumption number of hits in google means anything.

But, let me correct you.

[Hardy Heron 8.04 problems site:ubuntuforums.org] 74100

That's the ultimate ambiguous search phrase, a lot of those results are totally unrelated or are advertisements for hardy.

Anyways, judging by the size of this thread, and plenty of blog posts I've read, I gotta say Hardy seems a lot more stable than gutsy in its first week.

[Gutsy Gibbon 7.10 problems site:ubuntuforums.org] 2690000 results!

Based on my experience, it's not. I have yet to get a live cd to get past deciding to boot. It just sits there. I downloaded and burned a live cd of gNewSense, and the live cd was faster than any normal ubuntu live cd I've ever used. It was like running the system already installed. So I was tickled that I might get 8.04 running. Not. Once I installed it, everything was the same as what I saw in my original Hardy install. Jumpy, bogging down, etc. What is worse, it messed up my gutsy install. gNewSense is Ubuntu without any proprietary stuff, just all open source, so I don't see how it messed up gutsy so that I could not boot to it any more. It showed up in grub, but wouldn't respond. Sooo, I have a newer version of gutsy now, and my old one has some issues, but will boot. 

And coming to this site, pressing the new posts link, and looking around, I see far more problem posts than I've seen since I started messing with Ubuntu back in 2005.

Anyway, I got my gutsy back, so I'm happy. Hardy will come along sooner or later, and then I'll upgrade. Til then, I'm sticking with 7.10.

---

### Post by chrisneedshelp on 2008-05-05
I can't speak for much being a complete nube, and while giving no opinions, for sound problems that I shared, i found this

[http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147)

and couldn't be happier, ran the script, did NOT MERGE, and restarted, sound works flawlessly!

---

### Post by linuxlizard on 2008-05-05
> Its true that Hardy does have this problem of lockup, but if it really hit that many people, then we would see everybody complaining about it.

Looks like to me there are lots of people complaining about a number of things, and then there are a lot of diehard fans who are telling them to sitdown and shutup cause there's no problem here, move along thank you!

The truth is, it's easy to ignore until it's *your* hardware's turn on a release. That's how it was for me until Hardy- my hardware worked perfectly since breezy. Now lots of little things are screwed up that worked properly before. Not easy to ignore when it's your hardware.

> we have at the moment, 21,000 new (un-looked at) bug reports.

That may be one of the most telling things about Hardy this whole thread...

---

### Post by ibanez on 2008-05-05
I've been using Ubuntu since its release in 2004, I've stuck with it since , I dont call the not affecting me posters "Diehards" , I call them the brown nose brigade, The ones who say I installed it on 10 boxes without a single problem ... Pahh!!! , I installed it on 5 boxes all different hardware, and EVERYONE has experienced problems .. 

I've stuck with Ubuntu but this latest spate of Its not Heron its you has made me feel the need to migrate, This forum has gone from the helpful place it used to be to the typical Unix/Linux board of yesteryear, Full of elitists and Ubuntu brown nosers. 

 Fact is Heron is seriously problematic but there are a handful who deny these problems. 

Time for a new Distro for me, Its a shame though as Ubuntu really USED to have a future. 
Thats the beauty of Linux its free to migrate, & migrate I shall .

---

### Post by sneeks on 2008-05-05
ok chaps time for my 10 pence worth,if you look at some of the sticky s in the forum posts about installing a new version of Ubuntu,you will see it says that you should wait at least a month before d/l it.
this is to iron out the bugs that will effect some/all machines.
some people will be lucky and it will work out of the box,and for some it will not.
for most the only prob will be with video cards and maybe sound,but dont forget your pc's bios will have some control on what goes on so just reset the bugger.
also dont expect it to run prob free on the latest and greatest m/b,vista has the same probs as i see it all the time.
but on the other hand you have a base unit/laptop that is 18 months old you should have very little problems,or none whatsoever.
open source is(in my opinion...)still young and learning and to get over to the mainstream we will have these probs.
do you see bill's users complaining.....no because they no nothing different,they just have to wait like we do,but we have the option to voice it to the developers who listen,where as they dont.
you will find that in a month or so most of your woes will be sorted,(but not all !!! lol).
i will put it another way being a motorcyclist.
buy a ducati 996 and have horrendous service bills and things fall off all the time...or.....
buy yourself a 2 year old Suzuki TLR 1000 s and live life to the max,and accept that sometimes that it is gonna throw you off cause your not man (or woman) enough to handle it..
so to answer your question,yes it will deserve it's name soon..
sneeks.

---

### Post by SunnyRabbiera on 2008-05-05
well for me Hardy has lived up to its name.
For me I have not had a decent experience with Ubuntu in general since Edgy, that is a years worth of distro hopping right there.
Feisty was miserable for me, I could not even use the stupid thing thanks to the ATA issue it had with me.
Gutsy was not that much better, I had monitor issues galore and getting stuff to work was a real pain.
Hardy for me is my best Ubuntu experience since Edgy, sure I have had issues myself... compositing seems to be responsible for the terminal issues I had, plus a few other bugs have popped up especially with firefox 3.
But so far so good on my end, but all ubuntu versions have had their bugs... even Dapper which was my best ubuntu version.

---

### Post by Gatemaze on 2008-05-06
And still is :) I am still running drake and it is dead solid... I think I 2-3 crashes since 2006 that it firstly came out. Unfortunately my experience with heron is like the one of many people, so many freezes... but i can wait a couple of months and hopefully everything will be fixed... hopefully as heron is very nice...

---

### Post by BLTicklemonster on 2008-05-06
> **SunnyRabbiera said:**
> well for me Hardy has lived up to its name.
For me I have not had a decent experience with Ubuntu in general since Edgy, that is a years worth of distro hopping right there.
Feisty was miserable for me, I could not even use the stupid thing thanks to the ATA issue it had with me.
Gutsy was not that much better, I had monitor issues galore and getting stuff to work was a real pain.
Hardy for me is my best Ubuntu experience since Edgy, sure I have had issues myself... compositing seems to be responsible for the terminal issues I had, plus a few other bugs have popped up especially with firefox 3.
But so far so good on my end, but all ubuntu versions have had their bugs... even Dapper which was my best ubuntu version.

LMAO, so they released one for the people who had problems in the earlier releases, that's why I've never had real problems with any releases and now have them? Shoot, that' great. I can live with that! (be cool if it were so)

Ubuntu still rocks. So what if they have one that appears to be not as ready as the previous ones? I can sit back and wait. Gutsy's treating me just fine.

---

### Post by Brickell on 2008-05-06
I'm a 5-day-new Ubuntu user, I have Hardy, and I did have some problems on the first day with the wireless connection. I fiddled around and finally got it to work; not sure how, but I did.
I absolutely cannot hear anything, no music, no Youtube, no nothing.
and I am having the hardest time trying to get my webcam to work. I've tried just about every solution anyone has had to offer, tried all the software, all the compiling, all the set ups you can imagine. Nada, zilch.
I've been relentlessly trying to solve these problems, but I'm seriously thinking about switching back to Windows or something.

---

### Post by ktechman on 2008-05-06
At Least give Gutsy a try. Don't throw the baby out with the bath water.....

---

### Post by BLTicklemonster on 2008-05-06
I agree with ketchman. Load up gutsy, then let it do an update, then start setting it up. Hardy just hit the streets, so while it may work flawlessly on some computers, it still has some wrinkles that may need ironing out. Gutsy has been around long enough that you should be able to get things going in it a lot easier. And use the forums for help. Most likely whatever problem you've had, someone else has had and fixed.

---

### Post by Guilden_NL on 2008-05-08
I have two hand built (by moi) Desktop systems with radically different outcomes with Hardy.  

#1) Phenom AMD 8GB ram, EVGA GeForce 9800 GTX video card  SATA raid of 8 10,000 RPM discs NO WIRELESS
#2) Dual Core 64 AMD 2GB ram, NVidia card (no acceleration, forget what it is at the moment) NO SATA, with Wireless

#1)Couldn't run Gutsy due to a bug with the bios supporting my SATA Raid. Installed Hardy beta, and it ran perfectly. Upgraded to LTS and still perfect
#2)Ran Gutsy perfectly, only had to configure wireless with NDISWrapper and extremely happy.  Couldn't upgrade to Hardy due to a huge step backward with Broadcom chip bug with wireless that was prematurely closed in beta.  I swap out the card, go with a TI chipset card known to run on Hardy and Hardy freezes up due to NVidia bugs.  Am in the middle of using cabled ethernet to pull everything possible into upgrade to make it work.  Otherwise drop back to Gutsy for a couple of years.  I don't have time to fiddle around with steps backwards.

So my experience is a mixture of :guitar: & ](*,)

I will say that the 'tude of those not having problems has gotten to be rather annoying with Hardy.  I didn't see that with Gutsy, even when I was struggling through identifying the SATA Raid bug for several months.
Linux and Ubuntu is at a critical juncture point - having a negative 'tude with those experiencing problems will push people away from Linux right when the door of opportunity is at its most open point due to Vista.

So having this 'tude: [-(  will not result in this 'tude: \\:D/ when newbies are [-o<

Don't we all want this instead? LINUX: =D>

---

### Post by BLTicklemonster on 2008-05-08
Dude, you :guitar:

---

### Post by Guilden_NL on 2008-05-08
BLTicklemonster, you wouldn't happen to be in Tasmania would you?

Have heard people refer to Tazzy as NAntarctica, so wondering.  We just got back from a long vacation there and really enjoyed the state.

8-)

---

### Post by dynamethod on 2008-05-08
> **BLTicklemonster said:**
> Due to the number of UNsuccessful Hardy installs, it is only reasonable to assume that there is a problem with Hardy's development. Especially when one considers that so many of these people here (myself included) had no real problems with any release so far up until now. 

Just because everyone on your block dresses like you doesn't mean that you're normal...

Google this:

Hardy Heron 8.04 problems site:ubuntuforums.org

and see how many hits you get.

Something like this?
Results 1 - 10 of about 70,600 from ubuntuforums.org for Hardy Heron 8.04 problems

And it's been out how long?


Ok so i did:

Results 1 - 10 of about 265,000 from ubuntuforums.org for Hardy Heron 8.04 problems. (0.27 seconds) 

Now try this:

Gutsy Gibbon 7.10 problems site:ubuntuforums.org

which gives:

Results 1 - 10 of about 1,410,000 from ubuntuforums.org for Gutsy Gibbon 7.10 problems. (0.25 seconds) 


So now what?

---

### Post by BLTicklemonster on 2008-05-08
> **dynamethod said:**
> Ok so i did:

Results 1 - 10 of about 265,000 from ubuntuforums.org for Hardy Heron 8.04 problems. (0.27 seconds) 

Now try this:

Gutsy Gibbon 7.10 problems site:ubuntuforums.org

which gives:

Results 1 - 10 of about 1,410,000 from ubuntuforums.org for Gutsy Gibbon 7.10 problems. (0.25 seconds) 


So now what?

Just for yucks, divide the two by how long they have each been out.

Guiden, I'm in Rome, Ga. US. I just wanted a funny location, and seeing as how just about everywhere is north in Antartica... well it seemed like the fun thing to do. (I know you can head east in west there, it's just funny to me. And Tasmanians, I guess.)

---

### Post by Jadd on 2008-05-20
I am pleased to announce that updates for sudo and gksu have been released that fix the dysfunctional sudo issue I complained about. A bit late, but I'm glad they finally got round to it. Thank you. Don't break sudo again!

---

### Post by BLTicklemonster on 2008-05-20
I have been using a 128 meg nvidia card in a pci slot in a machine meant for a pci-e mount video card, but just got a new pci-e card and put it in my machine and tried hardy again.

Either that cured my problems, or there were things done to the downloaded iso file (which something has to have been done, because the first one I downloaded was too big to burn to a cd, but this new one fits) which fixed things. Either way, Hardy is running quicker'n greased lightnin' for me now. Way quicker than earlier versions.

---

