---
title: "A novice's sad experience with Karmic..."
date: 2010-02-18
forum: Testimonials &amp; Experiences
---

### Post by hst19 on 2010-02-18
Hi all Ubuntu lovers!

I'm a novice Ubuntu user and started with Karmic. I really like the spirit of ubuntu and after years of using Win XP I was bored with windows and its vulnerability to viruses and that's why I want to try ubuntu. I had high hopes but...after several attempts I'm tired with Karmic.

Ubuntu 9.10 irritated me from the beginning. I downloaded an iso image using utorrent and made a bootable USB stick with UNetBootin. I wanted to have a Ubuntu/XP dual boot system so I made some unallocated space (about 10 GB) in my hard disk and installed ubuntu in this space. Installation was quick, smooth and impressive. The first boot went smoothly. The second didn't. After selecting ubuntu from the GRUB 2 menu, the ububtu icon came on and then the screen went blank. This happened several more times. Sometimes ubuntu loaded, sometimes it didn't. I thought this was a problem with the ISO integrity and md5 sums, so I uninstalled ubuntu and requested a free CD using ShipIt. It arrived today. 

Again installation was no problem. First boot was fine too. Then I tried to configure wvdial to connect to internet using my USB modem (a Huawei fixed wireless terminal using CDMA). I had downloaded all dependencies and wvdial packages from windows and installed them in ubuntu. No problems there. 

Then I tried to see if ubuntu recognized my modem using command dmesg in terminal (I learned this from an old guide on the net). The terminal output showed it was connected. But when I ran wvdial, it didn't recognize any modem! So I was stumped, but I'm probably missing something, as I have absolutely no prior linux experience.

And then...Ubuntu froze. Crashed. The keyboard stopped responding (no buttons worked, not even Num Lock). I cut the power and tried again. What happened was this: grub 2 menu, then ubuntu icon, the nothing (blank screen like before)! This happened several times in succession as I tried rebooting again and again. 
I decided Ubuntu karmic simply wasn't my game. So I uninstalled it again and returned to good old, virus-prone XP. 

How do I feel now? Very, very disappointed. Ubuntu must be pretty good;otherwise it wouldn't be so popular. And yet...the ubuntu community and Canonical are content to distribute buggy, malfunctioning software to people. I've done a fair amount of research online, and problems with Karmic are affecting other people also. Others are also having problems with crashes, blank screens at startup, and difficulties in setting-up dialup connections. Ubuntu is supposed to be user-friendly, and yet problems like these are very rude shocks to linux novices. How How does that fit in with the meaning, spirit and purpose of Ubuntu?

I still like ubuntu. I haven't given up yet. Windows has given me worse trouble before. And I'm waiting for Lucid Lynx...and praying it won't be so impossibly buggy like its predecessor.
Please, Ubuntu community, please Canonical, please give people like me a good Ubuntu release this time. We trust you and have high expectations of you...please, please don't disappoint us.

---

### Post by mörgæs on 2010-02-18
I agree - it is unfortunate that only 9.10 and 8.04 are promoted on [www.ubuntu.com](www.ubuntu.com). 

I always recommend people to begin with 9.04 (supported through most of 2010), and if that for some reason does not work one could try 9.10.

9.10 has many innovations, but it is not the best choice for a beginner.

How does you machine behave with a 9.04 live CD?
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by hortstu on 2010-02-18
I too am a novice... from what you seemed to have accomplished on your own I think I'm more of a novice than you.

Don't worry about lucid yet... when that comes out it will be ready to go but bugs will be getting found by users and updates will be coming out regularly.  Go to the last LTS version of Ubuntu and get a feel for that.

Hardy heron... I believe it is 8.04, is about as bug free as you're going to get.  It's still supported and it has been out for a while and tested by users.  I use it.  I love it.  At the same time it, and these forums, have taught me a great deal.  

Another suggestion, if you run into multiple problems on your next install come in here and start a separate thread for each problem.  Start with the most serious and work your way out.  It may take a little time but someone(s) in here will get you up and running.

No one asks worse questions than me in here.  Don't be afraid to look stupid.  No one knows who you are anyway and someone else has been there before and someone else will be there again.

I started with a dual boot with XP on a desktop, and since I'm not a gamer, I've dropped xp entirely from my laptop.  I never miss it.

Also I would probably set aside more than 10gb for the install but I guess that depends on the size of your drive and what you've got going on in there with xp.

Good luck

---

### Post by switch10 on 2010-02-18
Some have problems, some don't.  I have installed Karmic (the best release yet in my opinion) on about 10 computers, and I have had no problems.  

I have never tried setting up a dial up connection however.  

Sorry to hear your experience was not so good.  Maybe try again in a year or so...

---

### Post by howefield on 2010-02-18
> **hst19 said:**
> Hi all Ubuntu lovers!

Hi,

You don't appear to be asking for help.

Please ask for this to be moved to Testimonials & Experiences. A section more suited to your posting.

---

### Post by stugi79 on 2010-02-18
I too recently installed 9.10 having never tried Ubuntu before. I had some minor problems with connecting wireless but found help in the forums and have had no problems at all with it since.

I would do what others have suggessted and start a thread for your specific problem and go from there. Once you get it working you'll not regret it!

---

### Post by bapoumba on 2010-02-18
Moved to Ubuntu Testimonials & Experiences.

---

### Post by Swagman on 2010-02-18
It  seems so weird to hear people still trying to use dial-up

---

### Post by QIII on 2010-02-18
If the OP has no broadband available or cannot afford it ...

For the OP:

I empathize with your frustration and the difficulty you have experienced.  The whole community would like to help you resolve any issues you have encountered.  That's why we're here on our own time.

I want to caution you against the assumption that something is bad because you can find others who are having problems with it.  While it is tempting to arrive at that conclusion, it is based on the assumption that the sample you have found represents all users.  People to not come to forums to complain about things that go right.  So for all we know, 95% of users could be experiencing no problems at all.  We can't know, because we have no way to measure that quantity.

That does not diminish the frustration of the 5% who are having legitimate problems.

I would encourage you to try at least one more time.

GRUB issues may sometimes be difficult to pin down -- or they may point rather cryptically to another problem entirely.  But it is often the case that you can enter Ubuntu in recovery mode, get to the terminal as root and issue commands that will give you information that will help others diagnose and solve the issues you are encountering.

You must remember that Linux is a community of developers who work on various parts of a complex OS relatively independently and that independent work has to be packaged in a way that can operate on any of tens of thousands of possible combinations of hardware items.

That is a pretty tall order for a decentralized community without a dedicated staff of thousands of people who do nothing but test every combination of components against every possible hardware combination.

My first suspicion is a video driver issue, but that is a stab in the dark.

A first crack at the problem may be to simply do this:

Install Karmic.

Recreate the issue.

Reboot to Windows and come back here.

Describe what happened.

Also list every detail you know about the hardware configuration of your machine.  The more you can tell us, the better.

Let us help before you flail helplessly on your own and get frustrated.

---

### Post by jdrodrig on 2010-02-18
> **hst19 said:**
> Hi all Ubuntu lovers!

I'm a novice Ubuntu user and started with Karmic. I really like the spirit of ubuntu and after years of using Win XP I was bored with windows and its vulnerability to viruses and that's why I want to try ubuntu. I had high hopes but...after several attempts I'm tired with Karmic.

Ubuntu 9.10 irritated me from the beginning. I downloaded an iso image using utorrent and made a bootable USB stick with UNetBootin. I wanted to have a Ubuntu/XP dual boot system so I made some unallocated space (about 10 GB) in my hard disk and installed ubuntu in this space. Installation was quick, smooth and impressive. The first boot went smoothly. The second didn't. After selecting ubuntu from the GRUB 2 menu, the ububtu icon came on and then the screen went blank. This happened several more times. Sometimes ubuntu loaded, sometimes it didn't. I thought this was a problem with the ISO integrity and md5 sums, so I uninstalled ubuntu and requested a free CD using ShipIt. It arrived today. 

Again installation was no problem. First boot was fine too. Then I tried to configure wvdial to connect to internet using my USB modem (a Huawei fixed wireless terminal using CDMA). I had downloaded all dependencies and wvdial packages from windows and installed them in ubuntu. No problems there. 

Then I tried to see if ubuntu recognized my modem using command dmesg in terminal (I learned this from an old guide on the net). The terminal output showed it was connected. But when I ran wvdial, it didn't recognize any modem! So I was stumped, but I'm probably missing something, as I have absolutely no prior linux experience.

And then...Ubuntu froze. Crashed. The keyboard stopped responding (no buttons worked, not even Num Lock). I cut the power and tried again. What happened was this: grub 2 menu, then ubuntu icon, the nothing (blank screen like before)! This happened several times in succession as I tried rebooting again and again. 
I decided Ubuntu karmic simply wasn't my game. So I uninstalled it again and returned to good old, virus-prone XP. 

How do I feel now? Very, very disappointed. Ubuntu must be pretty good;otherwise it wouldn't be so popular. And yet...the ubuntu community and Canonical are content to distribute buggy, malfunctioning software to people. I've done a fair amount of research online, and problems with Karmic are affecting other people also. Others are also having problems with crashes, blank screens at startup, and difficulties in setting-up dialup connections. Ubuntu is supposed to be user-friendly, and yet problems like these are very rude shocks to linux novices. How How does that fit in with the meaning, spirit and purpose of Ubuntu?

I still like ubuntu. I haven't given up yet. Windows has given me worse trouble before. And I'm waiting for Lucid Lynx...and praying it won't be so impossibly buggy like its predecessor.
Please, Ubuntu community, please Canonical, please give people like me a good Ubuntu release this time. We trust you and have high expectations of you...please, please don't disappoint us.


Thanks for sharing. I am sorry Ubuntu failed to you give a perfect out-of-the-box experience. Please dont stop checking back for new releases, they might fit the bill better.

---

### Post by jdrodrig on 2010-02-18
> **QIII said:**
> If the OP has no broadband available or cannot afford it ...

For the OP:

You must remember that Linux is a community of developers who work on various parts of a complex OS relatively independently and that independent work has to be packaged in a way that can operate on any of tens of thousands of possible combinations of hardware items.

That is a pretty tall order for a decentralized community without a dedicated staff of thousands of people who do nothing but test every combination of components against every possible hardware combination.


+1

But if I might add:

To the OP:

I know you might be thinking, "well windows, macos and other OSs are also developed relatively independently and that have to checked against thousands of different configurations"

A big benefit of an open-source community is its proximity to end-users driven by the transparency of the development process and the very open sourcesness of the code. We really appreciate your feedback and it will hopefully (and with a higher probability than in other closed-source OSes) incorporated in the development of the next releases.

---

### Post by howefield on 2010-02-18
> **jdrodrig said:**
> Thanks for sharing. I am sorry Ubuntu failed to you give a perfect out-of-the-box experience. Please dont stop checking back for new releases, they might fit the bill better.

And with the next release (10.04 LTS) coming on 29th April, that isn't long to wait :)

---

### Post by mwcrowley on 2010-02-18
To be fair this is anecdotal evidence, but the previous two releases seemed more stable and trouble free.  I had issues with Karmic that I haven't had with linux in a few years.  DVD burners getting really flaky.  DMA settings getting altered.  USB drives and mp3 players not mounting consistently.  Nautilus not playing nicely with Thunar when mounting my mp3 player.  All these were things that worked on previous releases.  It's still as secure as ever.  Not one virus in ten years.  
Here's what's going to happen, and why you should stay with Ubuntu.  The next release will probably be good enough to keep for a few years, without the need for updating to get new functionality.  Let everyone else be the guinea pig.  I knew Karmic had issues when I updated, but I've solved them all.  What you should do is install the last release or the next one, and only do security updates.

---

### Post by XubuRoxMySox on 2010-02-18
I tested Lucid for a few weeks (ending this week). As a long-term-support version, one might expect it *not* to include the buggy Beta software that has plagued it's predecessor. But, alas, it's still there - the default boot loader, the default sound manager, etc.

It looks like Ubuntu is becoming a high-risk distro that is not to be recommended for newcomers to Linux. Newbies are not lab rats to be used for testing Beta software. They need a widely and thoroughly tested, rock-stable desktop Linux for their first forays into Linux.

Perhaps after they've gotten a little experience and are willing to be used as guinea pigs (and it *is* kinda fun to play with bleeding edge software), they'd be ready for Ubuntu. But it's unconscionable to put Beta software in a "ready" release that purports to be "newbie friendly." I fear for Ubuntu's future unless they change that practice - especially in their LTS versions.

-Robin

---

### Post by leclerc65 on 2010-02-18
Me too, I am not happy with Karmic.
I am using the computer, then 'poof' without a hint it just goes down. Booting using the recovery mode (which takes forever). I don't know what it recovers but I lose so many files that it reminds me the days I got infected in Windows and had to format the hard drive and re-install.
After a few crashes like this my system is now 'downgraded' as follow:

- 4G to 2G (one memory stick taken out)
- 9.10 to 9.04
- Root partition from EXT4 to EXT3
- Home partition from EXT3 to EXT2

I don't know , but I have more luck with the April versions (8.04 & 9.04) than the October versions (8.10 & 9.10).

---

### Post by Tamlynmac on 2010-02-18
> [hst19]("http://ubuntuforums.org/member.php?u=1020693")
And yet...the ubuntu community and Canonical are content to distribute buggy, malfunctioning software to people.Thank you for sharing your testimonial and hope you enjoy your forum experience.
Perhaps, one might believe they go out of their way to do it. ;)

My _experience_ has been just the opposite and in hindsight my family has had nothing but positive results. Of course, we adhere to belief that hardware is extremely important and only use Linux compatible hardware. Which IMHO, eliminates many of the issues that impact every OS. Not just Ubuntu.

I won't debate in this section, but will rather wish you the best - Good Luck

---

### Post by robertcoulson on 2010-02-18
Hey ...I have had lots of problems with 9.10...BUT, here I am 7 months later...I WON'T give up on Ubuntu....Keep trying, it's worth the experience and fun.
Robert

---

### Post by juancarlospaco on 2010-02-18
*Maybe you need Canonical Desktop Support for the first times...*

---

### Post by hst19 on 2010-02-19
Thanks a lot for all of your feedback, everyone :). Really appreciate it! And thanks for moving my post to testimonials section. I don't want to cause any cluttter by posting in wrong sections.

I did reinstall ubuntu (just few moments ago actually, even before I checked for responses to my post). I'll check out the installation again and report back here and try to find solutions to some of the problems. Maybe I'll learn something. 

I will also download 8.04 & 9.04 ISO's and see how these versions perform in my machine. It will take some time 'cos I'm on a wireless dial-up connection (can't afford broadband, its too expensive here).

Thanks for your hard work and enthusiasm, ubuntu community. Sorry if I was a little harsh in my previous post...I was in a bad mood with ubuntu crashing and all.

See ya!

---

### Post by DawieS on 2010-02-19
> And then...Ubuntu froze. Crashed. The keyboard stopped responding (no buttons worked, not even Num Lock). I cut the power and tried again. What happened was this: grub 2 menu, then ubuntu icon, the nothing (blank screen like before)! This happened several times in succession as I tried rebooting again and again. 
I decided Ubuntu karmic simply wasn't my game. So I uninstalled it again and returned to good old, virus-prone XP. Have you checked your RAM? I had a similar experience where a machine was working perfectly for 2 years, and then developed problems with one of the memory sticks in the upper address ranges. It worked perfectly when cold, but tested defective after half an hour run-time.

Ubuntu uses ALL your installed memory, thus the problem may not show up in Windows. Memtest is found on the Grub menu. There are 8 tests, run each for about 2 minutes. If any red address bars show up, that is the cause of your problems...:grin:

---

### Post by hst19 on 2010-02-19
> **DawieS said:**
> Have you checked your RAM? I had a similar experience where a machine was working perfectly for 2 years, and then developed problems with one of the memory sticks in the upper address ranges. It worked perfectly when cold, but tested defective after half an hour run-time.

Ubuntu uses ALL your installed memory, thus the problem may not show up in Windows. Memtest is found on the Grub menu. There are 8 tests, run each for about 2 minutes. If any red address bars show up, that is the cause of your problems...:grin:

Thanks, DawieS. I'll try the memory tests and see what happens...

---

### Post by GodLikeCreature on 2010-02-19
> **hst19 said:**
> Thanks a lot for all of your feedback, everyone :). Really appreciate it! And thanks for moving my post to testimonials section. I don't want to cause any cluttter by posting in wrong sections.

I did reinstall ubuntu (just few moments ago actually, even before I checked for responses to my post). I'll check out the installation again and report back here and try to find solutions to some of the problems. Maybe I'll learn something. 

I will also download 8.04 & 9.04 ISO's and see how these versions perform in my machine. It will take some time 'cos I'm on a wireless dial-up connection (can't afford broadband, its too expensive here).

Thanks for your hard work and enthusiasm, ubuntu community. Sorry if I was a little harsh in my previous post...I was in a bad mood with ubuntu crashing and all.

See ya!

Hey, I am sorry to hear you are having issues.  Care sharing your system specifications?  

I think you, like many others, are under the idea that Ubuntu will support all kinds of devices and thus work out of the box no matter the hardware in use.  That's really not your fault, and it is an unfortunate result of less than clear information coming from distro builders and the rest of us in the community.

So yeah, that's right, Ubuntu may not work under your particular setup, so that should be within your expectations.  Having said so, some words of advice.

- Most Linux distros support the liveCD(or liveUSB in your case) functionality.  That's the best method to understand if Ubuntu works on your machine without actually changing anything.  In other words, instead of creating the partitions and then trying to install, you would have been better off booting from the liveCD or liveUSB and checking how your system works.  If everything goes smoothly, that's a good sign moving forward.  This is also good practice before updating to a new release.  So many people just mindlessly jump into the last release of their favorite Linux distro and then moan about the consequences, when they could have tested it first this way and save the frustration.

- Even if you are confident that Linux will work in your system, it is a good idea (at least when you are new to it) to use the Wubi installer.  Installing Ubuntu inside Windows will keep things very much under control.  It suffers slightly from a performance stand point, but it will give you a chance to test it safely.  If it does not work or you don't like it, just simply uninstall it as you would with any other windows application.  This approach would give you a pseudo-dual boot setup, only winboot would lead, not Grub.

- It is particularly important with Linux to be sure that you have some way to connect to the internet and download updates (safest  and easiest way is using your ethernet connection).  Believe me, the Karmic you have on that ISO and the current updated version are very different!  That's not to say that the initial image on that ISO is crap, only that the problems you are having may have been logged as defects and already been fixed, so updating could make a big difference!

- As for your USB modem...  I am wondering.  Did you check if the network applet picked it up?  I have a 3G Huawei E172 which was perfectly recognized and worked out of the box, just showing as a separate connection under the network applet menu.  Really, I did nothing for it to work, it was easier than in Windows!  In fact, I have only lost that functionality on those machines I installed Wicd on.  Wicd does not support USB 3G modems yet.

Finally, just want to encourage you to continue trying Linux, even beyond Ubuntu.  I think you would benefit from trying Linux Mint, an Ubuntu based distribution that is particularly good for new users.  Give an RPM distro a chance as well.  Mandriva is particularly good for starters as well, and I have seen it support devices Ubuntu didn't, so it may work better under your setup.

Good Luck!

---

### Post by uRock on 2010-02-19
Karmic is the best OS out there. It is stable and just works well for me.

If the OP had asked for help with his/her problems, they'd probably be fixed by now. May I also suggest trying [9.04]("http://releases.ubuntu.com/9.04/")?

---

### Post by hst19 on 2010-02-19
> **GodLikeCreature said:**
> Hey, I am sorry to hear you are having issues.  Care sharing your system specifications?  

I think you, like many others, are under the idea that Ubuntu will support all kinds of devices and thus work out of the box no matter the hardware in use.  That's really not your fault, and it is an unfortunate result of less than clear information coming from distro builders and the rest of us in the community.

So yeah, that's right, Ubuntu may not work under your particular setup, so that should be within your expectations.  Having said so, some words of advice.

- Most Linux distros support the liveCD(or liveUSB in your case) functionality.  That's the best method to understand if Ubuntu works on your machine without actually changing anything.  In other words, instead of creating the partitions and then trying to install, you would have been better off booting from the liveCD or liveUSB and checking how your system works.  If everything goes smoothly, that's a good sign moving forward.  This is also good practice before updating to a new release.  So many people just mindlessly jump into the last release of their favorite Linux distro and then moan about the consequences, when they could have tested it first this way and save the frustration.

- Even if you are confident that Linux will work in your system, it is a good idea (at least when you are new to it) to use the Wubi installer.  Installing Ubuntu inside Windows will keep things very much under control.  It suffers slightly from a performance stand point, but it will give you a chance to test it safely.  If it does not work or you don't like it, just simply uninstall it as you would with any other windows application.  This approach would give you a pseudo-dual boot setup, only winboot would lead, not Grub.

- It is particularly important with Linux to be sure that you have some way to connect to the internet and download updates (safest  and easiest way is using your ethernet connection).  Believe me, the Karmic you have on that ISO and the current updated version are very different!  That's not to say that the initial image on that ISO is crap, only that the problems you are having may have been logged as defects and already been fixed, so updating could make a big difference!

- As for your USB modem...  I am wondering.  Did you check if the network applet picked it up?  I have a 3G Huawei E172 which was perfectly recognized and worked out of the box, just showing as a separate connection under the network applet menu.  Really, I did nothing for it to work, it was easier than in Windows!  In fact, I have only lost that functionality on those machines I installed Wicd on.  Wicd does not support USB 3G modems yet.

Finally, just want to encourage you to continue trying Linux, even beyond Ubuntu.  I think you would benefit from trying Linux Mint, an Ubuntu based distribution that is particularly good for new users.  Give an RPM distro a chance as well.  Mandriva is particularly good for starters as well, and I have seen it support devices Ubuntu didn't, so it may work better under your setup.

Good Luck!

Thanks, GodLikeCreature!
As you said, maybe Karmic isn't working on my PC due to a hardware issue. 
Here are my specs:
Intel pentium 4 2.4 Ghz
512 MB RAM
40 GB hard disk (ubuntu partition 6.6 GB)
integrated graphics (Intel 82845G/GL/GE/PE/GV graphics controller)
Dell OptiPlex GX260 motherboard (bios version A09)
L2 cache 512 KB

I'm not tech-savvy so I just thought ubuntu will work on my system, because Windows does! Maybe I was mistaken. What do you think? Are my specs seriously not ubuntu-friendly? Thanks for yout opinion.

---

### Post by hst19 on 2010-02-19
I followed DawieS' advice and did memory tests, but no errors detected.

---

### Post by jdrodrig on 2010-02-19
> **Tamlynmac said:**
> Which IMHO, eliminates many of the issues that impact every OS. Not just Ubuntu.


Call me crazy but I think you are debating....what good does the OP get from hearing *our* opinions or experiences if we are not willing to stand behind them?

I dont think that an organization that puts out a sign "Please write your experience and deposit them on this drop-out box" and then to every negative experience replies "Hi my name is x, and I had a great experience..but I am not debating" will get many people to actually submit feedback. 

Debate does not have to be violent nor disrespectful. It can be basically about digging-in details about the experiences of "our customers" and offering them the proper channels to address them if they want to. Offering our experiences can be helpful if we use them as comparision tools of what could be driving the differences.

Just my 2 cents.

---

### Post by uRock on 2010-02-19
Why are the same people posting the same things over and over on every thread in this sub-forum?

---

### Post by jdrodrig on 2010-02-19
> **iRock said:**
> Why are the same people posting the same things over and over on every thread in this sub-forum?

OK. Point taken. I will take a break now...:D

wait...were you talking about yourself? I am very bad at rhetorical questions so I had to ask.

---

### Post by GodLikeCreature on 2010-02-19
> **hst19 said:**
> Thanks, GodLikeCreature!
As you said, maybe Karmic isn't working on my PC due to a hardware issue. 
Here are my specs:
Intel pentium 4 2.4 Ghz
512 MB RAM
40 GB hard disk (ubuntu partition 6.6 GB)
integrated graphics (Intel 82845G/GL/GE/PE/GV graphics controller)
Dell OptiPlex GX260 motherboard (bios version A09)
L2 cache 512 KB

I'm not tech-savvy so I just thought ubuntu will work on my system, because Windows does! Maybe I was mistaken. What do you think? Are my specs seriously not ubuntu-friendly? Thanks for yout opinion.

Hey, I don't see anything that would make alarms go off.  :p

Having said so, it'd be interesting if you could post the output you get from some system logs and lshw.  I am not sure about forum policies, perhaps it is not convenient to do that here, being a testimonials section of the forum.  Let's just give it a go, and if the mods think we should take it to other section of the forum, we will:

If you can get a clean boot, open a terminal and type the following:

mkdir logs (this will create a folder named "logs" under your home folder)

sudo cp /var/log/dmesg* logs/ 

(this will copy all entries of dmesg logs into the logs folder you just created, will likely ask you for your password)

sudo cp /var/log/syslog logs/ 

(this will copy the system log in a similar way)

sudo lshw > logs/lshwlog 

(this will create a file listing your hardware)

Now get full ownership and rights over those files (this is a precaution, you may not need it):

sudo chown -R yourusername: logs/
sudo chmod -R 744 logs

Once done, you should be able to close the terminal and transfer all these files into a USB pendrive.  If you can get that done, share your logs (perhaps via dropbox?) and let's see if there is anything outstanding.

If nothing works out, I would recommend you try a different distro.

---

### Post by hst19 on 2010-02-19
> **GodLikeCreature said:**
> Hey, I don't see anything that would make alarms go off.  :p

Having said so, it'd be interesting if you could post the output you get from some system logs and lshw.  I am not sure about forum policies, perhaps it is not convenient to do that here, being a testimonials section of the forum.  Let's just give it a go, and if the mods think we should take it to other section of the forum, we will:

If you can get a clean boot, open a terminal and type the following:

mkdir logs (this will create a folder named "logs" under your home folder)

sudo cp /var/log/dmesg* logs/ 

(this will copy all entries of dmesg logs into the logs folder you just created, will likely ask you for your password)

sudo cp /var/log/syslog logs/ 

(this will copy the system log in a similar way)

sudo lshw > logs/lshwlog 

(this will create a file listing your hardware)

Now get full ownership and rights over those files (this is a precaution, you may not need it):

sudo chown -R yourusername: logs/
sudo chmod -R 744 logs

Once done, you should be able to close the terminal and transfer all these files into a USB pendrive.  If you can get that done, share your logs (perhaps via dropbox?) and let's see if there is anything outstanding.

If nothing works out, I would recommend you try a different distro.

Thanks a lot, GodLikeCreature, I will try to do that. I have some good news...after reinstalling ubuntu, first boot went fine, didn't crash, and I somehow managed to connect to the internet with my usb modem! AS usual, wvdial didn't recognize it when run form terminal, but I tweaked some settings in wvdial.cfg and ran wvdial, and it worked. This was the how-to guide that helped me.
[http://sanjibmukherjee.info/2010/01/reliance-netconnect-ubuntu-910]("http://sanjibmukherjee.info/2010/01/reliance-netconnect-ubuntu-910")
I haven't booted ubuntu after that but let's hope it won't give me trouble again...

Could you please tell me how to share my logs? I'm very new to this sort of thing and will appreciate your instructions. I have an account with SugarSync but not Dropbox, but I can make one if necessary.

---

### Post by Radioman991 on 2010-02-19
> **Swagman said:**
> It  seems so weird to hear people still trying to use dial-up

My 81 y.o. father-in-law still uses dialup.  He gets on the net like 3 times a year.  I am however working to get him on a cable connection.

That said, to the OP.  My luck using dialup is a nightmare if you are trying to use a "slot" type modem board, that is usually designed for Windows.  An external US Robotics, connected to a serial port will be a LOT less of a hassle.   Fought my father-in-law's one whole weekend.  Since I bought him an external modem, no issues at all.  YMMV

---

### Post by uRock on 2010-02-20
> **Radioman991 said:**
> My 81 y.o. father-in-law still uses dialup.  He gets on the net like 3 times a year.  I am however working to get him on a cable connection.

That said, to the OP.  My luck using dialup is a nightmare if you are trying to use a "slot" type modem board, that is usually designed for Windows.  An external US Robotics, connected to a serial port will be a LOT less of a hassle.   Fought my father-in-law's one whole weekend.  Since I bought him an external modem, no issues at all.  YMMV

It would almost be worth it to give a neighbor 5 bucks a month to connect to their wireless. When I lived in an apartment one of my neighbors paid for the highest service, then charged people 5 bucks a month to connect. Their broadcast name had the apartment number and $5 by it. You had to get them to add your MAC before you could connect.

---

### Post by hst19 on 2010-02-20
> **Radioman991 said:**
> My 81 y.o. father-in-law still uses dialup.  He gets on the net like 3 times a year.  I am however working to get him on a cable connection.

That said, to the OP.  My luck using dialup is a nightmare if you are trying to use a "slot" type modem board, that is usually designed for Windows.  An external US Robotics, connected to a serial port will be a LOT less of a hassle.   Fought my father-in-law's one whole weekend.  Since I bought him an external modem, no issues at all.  YMMV

I agree. At first, I had trouble with my external USB modem but after changing the wvdial.cfg file the problem was solved. 
I haven't tried using an internal modem though. Fortunately I don't have to, so it's a relief.

---

### Post by GodLikeCreature on 2010-02-20
> **hst19 said:**
> Could you please tell me how to share my logs? I'm very new to this sort of thing and will appreciate your instructions. I have an account with SugarSync but not Dropbox, but I can make one if necessary.

Hey, congrats on getting that to work!  

As for logs, have you updated already?  You will probably have in excess of 100 updates waiting for you, so that will take time.  A Kernel upgrade will take place, as well as many other updates of all kinds.  Complete that update and boot again, I think you have good chances that your problems will end with that update.

If that is the case and you have a solid installation, I would recommend you backup your installation to an ISO, so you can restore straight to a configuration you know works for you.  Check out this entry from my blog for instructions.  [http://cristalinux.blogspot.com/2010/01/things-to-do-after-installing-ubuntu.html](http://cristalinux.blogspot.com/2010/01/things-to-do-after-installing-ubuntu.html)

Also, there are lots of them, but you may want to check my own "things to do after installing Ubuntu" list.  Find it here:  [http://cristalinux.blogspot.com/2010/01/things-to-do-after-installing-ubuntu.html](http://cristalinux.blogspot.com/2010/01/things-to-do-after-installing-ubuntu.html)

Good Luck!  

[http://cristalinux.blogspot.com/2010/01/things-to-do-after-installing-ubuntu.html](http://cristalinux.blogspot.com/2010/01/things-to-do-after-installing-ubuntu.html)

Good Luck!

---

### Post by J_Stanton on 2010-02-20
> **robertcoulson said:**
> Hey ...I have had lots of problems with 9.10...BUT, here I am 7 months later...I WON'T give up on Ubuntu....Keep trying, it's worth the experience and fun.
Robert

i agree.

---

### Post by 3rdalbum on 2010-02-21
> **hst19 said:**
> And I'm waiting for Lucid Lynx...and praying it won't be so impossibly buggy like its predecessor.
Please, Ubuntu community, please Canonical, please give people like me a good Ubuntu release this time. We trust you and have high expectations of you...please, please don't disappoint us.

Two things:

1. You don't need to wait for Lucid. It's here now, in alpha form (alpha 3 is due in a week). There are bugs, but I haven't come across any showstoppers yet, and some of Karmic's problems with mobile broadband are no longer present in Lucid.

2. You can help the testing effort for Lucid, by downloading the alpha and keeping it up to date every day. File bug reports against every problem you see. Karmic was considered to be a pretty good version for the people who were testing it before the release, because the people who tested Karmic got their bugs sorted out (mostly) before the thing actually shipped.

---

### Post by XubuRoxMySox on 2010-02-21
It *will* be buggy as long as they continue to insist upon Beta software by default. You would think that they wouldn't do that in a LTS version, but...

As long as you *know* it's Beta (even after it's final "ready" release) and are *willing* to take that kind of risk, it's fine. But I wouldn't offer it to a newbie.

-Robin

---

### Post by aklo on 2010-02-21
I'm sorry ubuntu 9.10 don't work for you.

My first ubuntu 9.10 works perfectly without any tweaks needed, it just works.

---

### Post by craig10x on 2010-02-21
I can tell you that Toshiba Laptops seem to get along fabulously with Ubuntu...I've used 8.10 9.04 and now 9.10 on one and they all worked 100% out of the box...no problems at all...

My Toshiba is about a year old...but all 3 of those Ubuntu's also worked on my friend's Toshiba, which he bought from me...and that is about 3 or 4 years old...

Mine had AMD and  ATI graphics and his (which was my old one) has just a basic Intel Celeron chip and Intel graphics i believe...

A little tip for those shopping for new laptops :)

---

### Post by GodLikeCreature on 2010-02-21
> **craig10x said:**
> I can tell you that Toshiba Laptops seem to get along fabulously with Ubuntu...I've used 8.10 9.04 and now 9.10 on one and they all worked 100% out of the box...no problems at all...

My Toshiba is about a year old...but all 3 of those Ubuntu's also worked on my friend's Toshiba, which he bought from me...and that is about 3 or 4 years old...

Mine had AMD and  ATI graphics and his (which was my old one) has just a basic Intel Celeron chip and Intel graphics i believe...

A little tip for those shopping for new laptops :)

I have experienced the same flawless experience with HP hardware.  I have installed Ubuntu with no issues on the following laptop/tablet models:

NX7400
6910p
6930p
TC4400
TC2710
TC2730

I have also installed it on desktop models, but those I don't remember!  :D

---

