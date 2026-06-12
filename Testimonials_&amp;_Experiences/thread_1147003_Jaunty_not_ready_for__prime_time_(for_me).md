---
title: "Jaunty not ready for  prime time (for me)"
date: 2009-05-03
forum: Testimonials &amp; Experiences
---

### Post by oregonbob on 2009-05-03
Jaunty should not have been released. Too many bugs, not enough important issues addressed. This release was absurdly over-hyped by trade press. 

Don't rush to Jaunty unless you want to help debug it. Yeah, it boots faster. I am seeing bugs galore, especially multimedia. Too many to list.

---

### Post by Gremlyn1 on 2009-05-03
I haven't seen too many bugs yet, but ever since upgrading my CPU has been working overtime, running 15-20C hotter than it used to. What's the deal!?

---

### Post by jespdj on 2009-05-03
So, oregonbob, you're frustrated because you've run into some problems trying to use Jaunty.

Ok, count to 10, cool down, relax, and then tell us exactly what went wrong. What hardware do you have, what doesn't work, etc.; let us help you fix the problems.

---

### Post by 3rdalbum on 2009-05-03
I'm not seeing any new bugs. There's still signal strength issues with RTL8187 wireless chipsets, but this might be fixed in the updates that are going up onto the mirrors at the moment. The Aircrack driver still works fine so I'm back using that.

Other than that, no additional bugs that I've seen so far.

Did you help test the betas?

---

### Post by ddrichardson on 2009-05-03
> **oregonbob said:**
> Jaunty should not have been released. Too many bugs, not enough important issues addressed.
I'm sorry to hear you've had problems with Jaunty and understand how frustrating this can be.

For us to improve each release though, we need to know what important issues need to be resolved and if you have encountered bugs what they are so we can fix them.

Unfortunately, supporting such a large amount of hardware with limited manufacturer support and limited testing systems means that there will likely always be bugs which we don't know about unless they are reported.

If there are too many to list - perhaps you would cover the multimedia aspect you cited?

---

### Post by oregonbob on 2009-05-03
I did an upgrade from a well-functioning 8.10 to Jaunty. As you must have heard, the main reason users complain about Linux is all the extensive configuration (by hand) required to get things working right. Usually the biggest problems by my observation are video card, multi-media, and USB devices.

I was quite happy with 8.10 though I had spent months getting things working right. Most stuff worked right. I could play any DVD, I could watch any downloaded video. The biggest annoyance for me on 8.10 is zero support for the USB tuner I bought. Zero support for a Western Digital USB external drive, Zero support for the mic on a very popular USB Logitech quickcam.

It not just me, users want to install the OS and have stuff work, sort of like Windows.

I read some of the hype for 9.04 and hoped it had improved USB device support, so I installed it.

First my ATI Radeon 3650 does not work except in vesa driver. It fliped out trying the correctdriver, garbage when gnome starts up.

My Quickcam still doesn't work: the mic not at all and the video is often flaky or does not work at all with some programs.

I am frustrated by lack of driver support for 64bit, Adobe for example.

Now what really upset me was I could no longer run downloaded videos, AVI's, etc. I remember the config hell I went thru to get them working on 8.10. Redoing all that work is not a warm feeling. 

I am ANGRY after reading hyped up trade press about how good 9.04 was. It isn't that much different than 8.10 to the user. I realize blogs and trade press is largely just standard old ******** hype.

I am dreading days and days of command line config and reading research to get simple stuff working right, again.

I was disappointed in 9.04 in general. No significant UI changes, dull themes and wallpapers. Just...disappointed in Ubuntu for the first time. I get the feeling Ubuntu is burning out. I want to see it "win".

---

### Post by ddrichardson on 2009-05-03
> **oregonbob said:**
> I did an upgrade from a well-functioning 8.10 to Jaunty. As you must have heard, the main reason users complain about Linux is all the extensive configuration (by hand) required to get things working right. Usually the biggest problems by my observation are video card, multi-media, and USB devices.
It is frustrating, by multimedia and your description of diifculties with AVI I'm assuming are linked? Codec support is an irritation for users who just want their files to run, I understand that but it isn't within Ubuntu's control to distribute for legal reasons. I hope changes to gstreamer and our help documentation make this easier to install but recognise there might be room for improvement.

> **oregonbob said:**
> I was quite happy with 8.10 though I had spent months getting things working right. Most stuff worked right. I could play any DVD, I could watch any downloaded video. The biggest annoyance for me on 8.10 is zero support for the USB tuner I bought. Zero support for a Western Digital USB external drive, Zero support for the mic on a very popular USB Logitech quickcam.I think it's always prudent on upgrade to have a good backup and perhaps we should strongly consider a change to ubiquity to allow some form of rollback to the previous release. Because of the rapid development pace there are often conflicts on upgrade. If I raise a specification would you be willing to contribute to it?

> **oregonbob said:**
> It not just me, users want to install the OS and have stuff work, sort of like Windows.
I agree but it needs to be remembered that a clean install of Windows is fraught with driver issues too - for the same reason, there's so much hardware to support.

> **oregonbob said:**
> I read some of the hype for 9.04 and hoped it had improved USB device support, so I installed it.

First my ATI Radeon 3650 does not work except in vesa driver. It fliped out trying the correctdriver, garbage when gnome starts up.

My Quickcam still doesn't work: the mic not at all and the video is often flaky or does not work at all with some programs.

I am frustrated by lack of driver support for 64bit, Adobe for example.

Now what really upset me was I could no longer run downloaded videos, AVI's, etc. I remember the config hell I went thru to get them working on 8.10. Redoing all that work is not a warm feeling. 

I am ANGRY after reading hyped up trade press about how good 9.04 was. It isn't that much different than 8.10 to the user. I realize blogs and trade press is largely just standard old ******** hype.

I am dreading days and days of command line config and reading research to get simple stuff working right, again.All these issues while frustrating would be addressed if there was an easy way to roll back to 8.10 and by submitting accurate bug reports as we discussed earlier.

> **oregonbob said:**
> I was disappointed in 9.04 in general. No significant UI changes, dull themes and wallpapers. Just...disappointed in Ubuntu for the first time. I get the feeling Ubuntu is burning out. I want to see it "win".
There are some significant interface changes being discussed for the next release so I hope you'll stick with us!

---

### Post by caravel on 2009-05-03
> **3rdalbum said:**
> I'm not seeing any new bugs. There's still signal strength issues with RTL8187 wireless chipsets, but this might be fixed in the updates that are going up onto the mirrors at the moment.
Ndiswrapper is the better option for Realtek wireless chipsets.

---

### Post by Mark76 on 2009-05-03
You do know it's not Canonical's (or Red Hat's, or Novell's, or....) fault that the driver and device support you need doesn't exist, right?  If you want to lay the blame at the right door it needs to be laid at the feet of ATI, Adobe and whoever built your mic and webcam.  The Linux developers can only do so much with reverse engineering.

Personally I'd suggest you get in touch with these companies and make your feelings known to them. Perhaps if enough of us do that they might start changing their attitude.

---

### Post by stalkingwolf on 2009-05-03
ok i will address the "ease" of a windows install.
if i do a fresh install of xp on my desktop the first thing i run into is that none of the on board stuff works. no drivers.  It used to be that I could just go to the board mfgs site and download the drivers.  Any more
virtually all links to drivers go to a driver detective site where you first pay for the software then pay pay for the drivers.   I can install
a newer version of xp ( full install instead of upgrade) but then all the 
software i own does not work.

So i have choices,
1 clone an old install and not use newer devices
2  install newer full version and not be able to use the software i have already purchased
3  purchase and learn all new software
4  install the Ubuntu release of my choice use the equivilant software
learn to use new software, boot into the old xp system for the occasional
application that has no equivilant and convert the documents and such to
a compatible format.

guess which i chose.

The only issue i have with 9.04 is the same one i had with 8.10 none of my wifi adapters work.  I believe this to be a network manager issue, as when i did a fresh install of 8.04 i had to install wifi radar to get the wireless to work again.

---

### Post by Linux&amp;Gsus on 2009-05-03
First of all, let me say that I do understand your frustration. It's plain and simple always frustrating when things are not working the way one wants them to.
Still, in all that, I must say, honor where honor is due and (constructive!) criticism where (constructive!) criticism is due (and only there!).

> **oregonbob said:**
> I did an upgrade from a well-functioning 8.10 to Jaunty. As you must have heard, the main reason users complain about Linux is all the extensive configuration (by hand) required to get things working right. Usually the biggest problems by my observation are video card, multi-media, and USB devices.

I was quite happy with 8.10 though I had spent months getting things working right. Most stuff worked right. I could play any DVD, I could watch any downloaded video. The biggest annoyance for me on 8.10 is zero support for the USB tuner I bought. Zero support for a Western Digital USB external drive, Zero support for the mic on a very popular USB Logitech quickcam.
So, if you had a perfectly working setup why did you upgrade? Specifically if it took you months to get it working right??
That just tells me that you had a lot of trouble, why would you through all that out for something that is brand new. Jaunty isn't yet tested widespread and therefor not everything fixed...

I don't know what the exact trouble is you have with the hardware listed. And even more so I don't know when you bought it. But did you check beforehand that it has Linux support? That's a known issue, not only in the Linux world. Many people didn't upgrade, or at least waited for quite a while, to Windows Vista because their hardware (printers, scanners, etc) wasn't or potentially still isn't supported.
Admitting, thou, that I would expect an USB external HDD to work out of the box. Still, did you check first? I, too, had a problem once with such a HDD, asked (friendly!) in the forum and got it sorted out.




> **oregonbob said:**
> It not just me, users want to install the OS and have stuff work, sort of like Windows.
Well, installing and having everything working perfect out of the box is what everybody would prefer, I guess. On every platform. Reality is that it's not like that. Not in Linux, not in Windows, not in OSX, etc.
Funny enough, thou, I had to ask my bro-in-law many times to help me with Windows. Now on Linux I am able to fix things myself with the help of a forum.
After he and a few others showed me Linux and explaining a few basics. I tried it myself. Didn't had nearly as much trouble with it. So, I'm using Linux not for the hype or geekiness of it. I originally came to it for the pure sake of getting things done.
It's as simple as that: Different people have different experience and more over, they have different needs. What you need is the right tool for the right purpose. Period.

You can not say that people across-the-board sort of want it to be like Windows. I know that I don't want it like that. If Linux would be like Windows for me, I for sure would look for something else.





> **oregonbob said:**
> I read some of the hype for 9.04 and hoped it had improved USB device support, so I installed it.
*...[cut]...*
I am ANGRY after reading hyped up trade press about how good 9.04 was. It isn't that much different than 8.10 to the user. I realize blogs and trade press is largely just standard old ******** hype.
If I would believe the press then Windows would be the best and the fastest and most secure OS. And OSX would be the best and the fastest and the most secure OS. And Linux would be the best and fastest and the most secure OS.
Well, depending on who you ask it could as well be that *[enter OS of choice]* is th slowest, most vulnerable, ugliest, buggiest, *[add bad attribute of choice]* ever seen in this solar system.




> **oregonbob said:**
> I am frustrated by lack of driver support for 64bit, Adobe for example.
You can hardly blame Linux for that. That's like blaming MS when a piece of hardware no longer works on a new version of Windows while the hardware vendor should be the one providing the new driver.




> **oregonbob said:**
> Now what really upset me was I could no longer run downloaded videos, AVI's, etc. I remember the config hell I went thru to get them working on 8.10. Redoing all that work is not a warm feeling. 
As I said earlier, if you had so much trouble why did you upgrade. Next time try a LiveCD first or even better take a old HDD to test-run an installation before you through out something that you worked on for months to get it right.
I know that this doesn't help you much now. But for the next time you know better. Put it under the category of "lesson learned".

Unless, of course, you are a bit like myself. I just do it and see what happens. Well, I try to gather some info first and do a backup of the data and might even try the LiveCD first. But I don't do a proper test-run.
However, specifically doing it that way means I can (nicely!!) ask for assistance afterwards if something goes south. But for sure I can't hop on the forum and and blame everyone and the world for things not working and download my frustration. If I would've take the necessary precaution (e.g. make a working duplicate of my current state or have a test install, etc) then I wouldn't even need to be frustrated, because it's all back, in best case, within a matter of minutes.




> **oregonbob said:**
> I am dreading days and days of command line config and reading research to get simple stuff working right, again.
I know that this will not give you much comfort either. But see it from that point: At least you *CAN* do something about it. I had multiple occasions where I simply had to give up on Windows because there couldn't be done anything about it. Except, of course, if the vendor would do something specifically for me...
BTW, I have a situation on Linux myself, with my video card. It's not fully supported and I can't get a 2nd screen to work properly. Means, when ever I need to hock up a projector for a presentation I need to boot Windows. That's just how it is.
But then, on the other hand, the newest things from MS wouldn't even run on this computer, so what. I have the choice between old Windows and working dual screen or up-to-date Linux with everything else working.

Now, go figure...




> **oregonbob said:**
> I was disappointed in 9.04 in general. No significant UI changes, dull themes and wallpapers. Just...disappointed in Ubuntu for the first time. I get the feeling Ubuntu is burning out. I want to see it "win".
Who says that there needs to be a significant UI change every 6 months?
I said it in a different thread already. Whether a theme or wallpaper is nice or ugly is a matter of personal preference. That's why you have at least the chance to change it. Linux is about choice, remember?

Just because *YOU* don't like the latest art work doesn't mean that Ubuntu is going to die soon. Next time you might like it again and I don't. Well, I'm not a fan of Gnome anyways, i use KDE 4 and am very happy with it. But hey, as I said, it's my choice, my personal preference.
It simply is NOT possible to make only 1 perfect UI for every person on the planet.


So, next time you know, if it ain't broke don't fix it. Or at least take the necessary precaution. Then you have easy option, if needed.


Nuff said.
L&G

---

### Post by solwic on 2009-05-03
> **oregonbob said:**
> Jaunty should not have been released. Too many bugs, not enough important issues addressed. This release was absurdly over-hyped by trade press. 

Don't rush to Jaunty unless you want to help debug it. Yeah, it boots faster. I am seeing bugs galore, especially multimedia. Too many to list.

Good rule of thumb:  when the release date is April 23rd, don't install until at least May 23rd.  Every OS has issues at release.  Every single one of them.  

It's why I'm still using Intrepid.  Here in a couple weeks, I'll switch to Jaunty and ext4.  

:biggrin:

---

### Post by Mark76 on 2009-05-03
Question.

Did they really need to upgrade the kernel?

That's where most of the trouble starts.

---

### Post by JetskiDude911 on 2009-05-03
I'm actually enjoying this release. The 2008 release were all horrible for me. So far I haven't ran into any problems with 9.04. Today I'm going to be moving to it on my desktop. I've been running it on my laptop for the past week or so. 

The only thing I've had crash on me was one large file transfer from a Windows machine. Not sure what went wrong. Other large file transfers worked perfectly, but this one just quit for some reason.

---

### Post by sandy8925 on 2009-05-03
To the person who started this thread:

Did you ever see the Multimedia section in ubuntuforums ? It has a nice Sticky with detailed instructions for solving Multimedia problems.

A much simpler way to sort out playing multimedia is to just install vlc media player(the linux version from the repos that is).

Mplayer is also really good and can play practically anything you throw at it(or so I have heard).

You can also try Geexbox which is a small (19 MB) distro. It boots fast and can play almost anything (because it uses mplayer) and supports HDTV's and remotes (I've never used remotes though).

And as someone else here already said the bad driver support is NOT Canonical's fault(or the fault of any other person/organisation/etc. making Linux). It's the hardware manufacturers who have consistently and successfully ignored the growing Linux userbase and not made Linux drivers for their product.

---

### Post by ikt on 2009-05-03
> **oregonbob said:**
> Zero support for a Western Digital USB external drive.

what are you having trouble with? Mine is working fine :confused:

---

### Post by ddrichardson on 2009-05-04
> **ikt said:**
> what are you having trouble with? Mine is working fine :confused:
I didn't notice this in the OP but if you're still reading, many people have reported the usb_storage module not loading at boot and needing to be manually added to /etc/modules.

---

### Post by Bios Element on 2009-05-04
> **Mark76 said:**
> Question.

Did they really need to upgrade the kernel?

That's where most of the trouble starts.

Yes, they did. Ubuntu keeps things updated, If you don't want the latest stuff, don't upgrade.

---

### Post by Syirrus on 2009-05-05
> **JetskiDude911 said:**
> I'm actually enjoying this release. The 2008 release were all horrible for me. So far I haven't ran into any problems with 9.04. Today I'm going to be moving to it on my desktop. I've been running it on my laptop for the past week or so. 

The only thing I've had crash on me was one large file transfer from a Windows machine. Not sure what went wrong. Other large file transfers worked perfectly, but this one just quit for some reason.

I second that statement, 8.04 and 8.10 didn't work for me. In fact I couldn't even boot the CD. Now with 9.04 all is well.

---

### Post by Vorian Grey on 2009-05-05
> **oregonbob said:**
> I did an upgrade from a well-functioning 8.10 to Jaunty. 

There's your #1 problem right there. Upgrading almost always causes some problems in my experience. I always do a fresh install.

---

### Post by ikt on 2009-05-05
> **Vorian Grey said:**
> There's your #1 problem right there. Upgrading almost always causes some problems in my experience. I always do a fresh install.

This is not microsoft land :P If there are issues during upgrading it's best to report the bugs and hope they get fixed before the next release, your voice/input does matter! (to a degree)

---

### Post by stchman on 2009-05-05
> **oregonbob said:**
> Jaunty should not have been released. Too many bugs, not enough important issues addressed. This release was absurdly over-hyped by trade press. 

Don't rush to Jaunty unless you want to help debug it. Yeah, it boots faster. I am seeing bugs galore, especially multimedia. Too many to list.

Jaunty works perfectly on my Aspire One.  I also do research and buy ONLY hardware that is Linux compatible.

---

### Post by Methuselah on 2009-05-05
So I guess the story of the thread is that sweepign generalisation are seldom true.

I haven't had any problems with Jaunty either.

---

### Post by PCHome on 2009-05-05
Compared to other operating systems I've used (OS/2, BeOS and other Linux versions) Ubuntu is just about the best. It seemed to run perfectly as soon as it was installed.

However, I have to agree that 9.04 was released prematurely. I know that certain bugs that I reported were never fixed so it was a surprise to see it was released. In fact, the "Report a problem" bug reporter itself doesn't work! When I click on it, its icon appears for a moment and then goes away. My system crashes from time to time since installing 9.04 yet the crash reporter, after it collects the information, gives an error that it cannot report it. If nothing else these are major issues and 9.04 will never be valid or stable if one cannot even report the bugs. In the past bugs were always fixed quickly but I expect that many are not even getting reported now.

---

### Post by HappyFeet on 2009-05-05
You do not need a graphical app to report bugs. You can go to [Launchpad]("https://launchpad.net/ubuntu") to report bugs. You will need to sign up first. Please do so, and try to make Ubuntu better.

---

### Post by sstewart207 on 2009-05-05
> **oregonbob said:**
> Jaunty should not have been released. Too many bugs, not enough important issues addressed. This release was absurdly over-hyped by trade press. 

Don't rush to Jaunty unless you want to help debug it. Yeah, it boots faster. I am seeing bugs galore, especially multimedia. Too many to list.

i agree. too many packages left out (drivers such as wvdial, etc.)

:guitar:

---

### Post by cariboo on 2009-05-06
If wvdial is missing, create a bug report, the devs were going to drop aptitude from the LiveCD back in Hardy, I reported the bug, after much argument it was put back in.

---

### Post by VoodooLoveDog on 2009-05-06
I just want to chime in and strongly disagree with the OP. I have installed Windows versions on countless pieces of HW with various peripherals attached to them. More often than not, I will spend anywhere from 1-2 hours finding all of the device drivers associated with a given machine. 

Pick up a brand new machine and install XP on it, I will almost guarantee none of the drivers will show up in Device Manager (Chipset, Audio, Video, USB devices, etc.) This is where Ubuntu shines. Out of the box, I noticed that Ubuntu has a driver configured for 80% of peripherals/HW on a given machine. 

Please don't make a statement like it just works in Windows because often times it doesn't. However I will say installing drivers is somewhat easier in Windows than in Ubuntu. 

Secondly, I'd just like echo some of the other comments. Upgrades from major version to major version of any OS is a risky adventure. Sometimes it works flawlessly and sometimes it is an infuriating mess.

---

### Post by growled on 2009-05-06
> **VoodooLoveDog said:**
> I just want to chime in and strongly disagree with the OP. I have installed Windows versions on countless pieces of HW with various peripherals attached to them. More often than not, I will spend anywhere from 1-2 hours finding all of the device drivers associated with a given machine. 


Too true. I've done countless Windows and Linux installs and Linux wins easily for being the easiest to install. I have literally spent hours hunting for drivers in Windows. In Ubuntu, if it's not in the repository you can easily find some information about in the forums.

---

### Post by oregonbob on 2009-05-06
I am OP. My problems with 9.04 are:

1) There was to much hype and fake rave for the release. In hindsight, I think some well known bloggers simply read other hyped posts, then did their own hyped post without really trying the product themselves. I had high expectations. All it really does is boot faster. There should be warnings that users will do days of config for faster boot time -- not worth it.

2) None of my popular USB devices work yet.

3) Gnome-mplayer is set as default player. It has issues, if you go full screen, the window does full, but the actual video stays small and duplicates. Other players work after hours of experimentation.

4) It automatically removed some apps it claimed were obsolete, such as Skype, then did not install a replacement, and replacement was same 32bit hack

5) I am burned and frustrated that nothing is totally ready for 64bit yet. You must have been like me and read all the advice that if one has a 64bit CPU, then use 64bit Ubuntu. NOT!

6) Audacity records 1-2 seconds and quits. I saw this reported bug. When I spend an afternoon and go from one broken app to the next, you get frustrated.

Many upgraded apps apparently have problems, I recall flames about Aramok and others. So I wound up upgrading from something that worked to something that did not.

It is amusing to watch twitter search on #ubunut 9.04 and observe a user doing an upgrade every 2 minutes or so. All those headaches.

Don't get me wrong. I love Linux, I love Ubuntu, I appreciate all the hard work done for free to make this wonderful product a reality. If I had not read all the hype first, and maybe read some TRUTH first, I don't think I would be complaining right now.

Thanks for all the comments

P.S. And today I learn that Boxee does NOT work for 64bit----------Damn it! :(

---

### Post by HappyFeet on 2009-05-07
> **oregonbob said:**
> 

5) I am burned and frustrated that nothing is totally ready for 64bit yet. You must have been like me and read all the advice that if one has a 64bit CPU, then use 64bit Ubuntu. NOT!



64 bit has been a great experience for me. I will never go back to 32 bit.

---

### Post by Perfect Storm on 2009-05-07
Thread title changed a bit.


regards
A.I. Dude 
Ubuntu Forum Staff

---

### Post by solwic on 2009-05-07
> **HappyFeet said:**
> 64 bit has been a great experience for me. I will never go back to 32 bit.

No issues with the 64 bit version when I tested it.  Just a little tougher to find certain programs.  :)

---

### Post by jdrodrig on 2009-05-07
> **oregonbob said:**
> Jaunty should not have been released. Too many bugs, not enough important issues addressed. This release was absurdly over-hyped by trade press. 

Don't rush to Jaunty unless you want to help debug it. Yeah, it boots faster. I am seeing bugs galore, especially multimedia. Too many to list.

I disagree, previous releases were even MORE over-hyped by trade press!

---

### Post by oregonbob on 2010-08-07
It is funny to read this post a year later. I didn't even start this thread but somebody (admin?) made it a new thread and moved it. Maybe the craziest, repeated response I got is that I shouldn't have upgraded, which I consider silly.

I guess I didn't mention I've been running unix and linux since 1982. A not-ready release of linux isn't enough to even discourage me. I just keep thinking about those who suggested I shouldn't upgrade, hahaha. I stand by the statement that Jaunty was not ready *when* it was released. Promotion and hype got ahead of reality and may have forever lost some potential users.

But now I am running Lucid 10.04 on my main desktop and my laptop and love it! I finally made the switch from Windows as my main default to Ubuntu. Now I hate it when I have to boot Windows 7. Lucid exceeds Windows 7 in every aspect in my opinion. Like many others in here I want to see Ubuntu become a major player in operating systems worldwide. Microsoft still has a grip on most of the market. When that happens I assume we will see vendors making their hardware work faster and better with linux.

Lucid was great from the first day it was released. All I can say now is *Sweet!*

Now if I could just watch Netflix on Ubuntu! I still have to boot Windows to watch Netflix.

("don't upgrade" ....bwahahahaha....) :D

---

