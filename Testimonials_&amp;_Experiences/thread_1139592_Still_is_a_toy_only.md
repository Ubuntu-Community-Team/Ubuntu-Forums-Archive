---
title: "Still is a toy only"
date: 2009-04-27
forum: Testimonials &amp; Experiences
---

### Post by mitten on 2009-04-27
Although version 9.04 of Ubuntu has been spreading and covering more and more users on the world. I think it is a toy. It is still a toy only.

Common mistake or must not missing items that are missing. This point makes me no more interest to setup a real workstation that as my secondary important platform besie my Vista PC.

Intel Matrix RAID, common low cost ethernet card, common x86-64bit CPU... Everything surrounding this three area may not makes too much human really want to have a Ubuntu 9.04.

My system is not a top top PC standard. But I have been trying to setup Ubuntu 9.04 x86 64bit. The final result is fail too.

LiveCD installation mode plus extra driver during the Live sesson, fail.
Customize the installation disc by Remastersys includes necessary drivers, fail.
AFter about 8 hours war with the installation story, the ending is no ending... Still fail on something.

Install inside the Windows? x86 64bit system with Matrix RAID seems must be fail.

Up to this time, I think it is not a released. It is just a World Wide Test edition, WWT beta.

Additionally, something must going wrong on large size HDD, such as, 1TB, 1.5TB HDD... many people just got the fail result.

---

### Post by kamitsukai on 2009-04-27
why don't you try the alternate install CD?

> 
Direct Link to ISO

**_PC (Intel x86) alternate install CD_**
[http://noncdn.releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso](http://noncdn.releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso)

**_64-bit PC (AMD64) alternate install CD_**
[http://noncdn.releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso](http://noncdn.releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso)


> _Alternate install CD_

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

In the event that you encounter a bug using the alternate installer, please file a bug on the debian-installer package.

There are two images available, each for a different type of computer:



PS: I'd also refrain from calling Ubuntu a toy and such as this only creates flame wars

---

### Post by Sef on 2009-04-27
Moved to Testimonials and Experiences since it is the latter.

---

### Post by mitten on 2009-04-27
Thanks for remind and comment on my bad wordings of my post.

Right, I have been using Linux for many years. Since RedHat, fedora, CentOS, and Ubuntu (start from 8.04). Ubuntu is a great product of OS that contains much power to catch the tails of others mega size OS, such as, Mac OS X, Windows XP/Vista/7 beta. The supporting and rich of software compatibility are better than others Linux (RedHat Enterprise excluded here, it is not free).

I have a set of Ubuntu donation items at home too. Hat, cup, card holder, T-shirt, ...

But something are being widely in uses on the PC nowaday, I just got a bad feeling while I have try and try to deploying the 9.04. Something are still count in the not important list (maybe). Smoothly deployment is not my friend in this two days.

The only one almost perfect deployment is setup 9.04 on my VAIO TZ notebook... upgrade from 8.10.

The Alternate edition of 9.04 x64 were tried before. It just OK on deteting my Matrix RAID volumes. But it was fail finally. Just saying disc error or bad HDD... Burn and burn, RW to R disc.... also fail on somewhere.

A little bit idea may be make me install Windows Server 2008 on the new PC for VMware Workstation 6.5. This action may be the final answer for my way. Why it is my final way? My boss may not happy to see me spent too much time to prepare the virtualization env....

---

### Post by beren.olvar on 2009-04-27
Funny you say something like this... To me is way more serious than other OS. In fact is the only OS I use, for fun and for work. I would not trust my computer nor my information, to "the" other OS, which still seems like a lousy piece of software, at least to me.

It may have some problems with hardware, but that only means you should be careful at buying. Other than that, to use GNU+Linux shows only benefits to me.

cheers

---

### Post by mitten on 2009-04-27
For reducing the cost, my purchasing list may near null... It means everything come from the cheap mainboard (but best for long run). Display, RAID... all provided by the north/south bridge, and on-board PHY...

All of them are common on around HK$1000 mainboard. I think they are widely in use too. Just want to see Ubuntu installation would become smooth while touching those of simple hardware.

Anyway, at least I am using Ubuntu on my notebook. This notebook is my outdoor activities friend on Sat. and Sun.. Mon. To Fri., it is my friend on daily consult work too.

My new activity management web site would be opening soon. XOOPS on Ubuntu... Yeah! This project has no dead line. Perfect.

---

### Post by 3rdalbum on 2009-04-27
I'm not sure you can call Ubuntu a "toy" just because it doesn't recognise your particular piece of exotic hardware. The vast majority of people don't use RAID, and most of the people who do have supported chips.

Having said that, it's obvious that you haven't read any Ubuntu documentation before posting your gripe - for shame.

> Installation - LVMOnRaid

In order to perform this install you will need the Alternate ISO image and have to use the text based installer.


([https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid))

> According to the latest FakeRAID spec, Intrepid users can now install directly to SATA RAID with no additional setup or configuration required. This is is not yet supported in the Ubiquity graphical installer so you must use the Alternate Install CD.

([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto))

> Requirements

    * The "Alternate" install CD for *buntu if you're building a desktop system. If you're building a server, the server install CD includes the necessary options.

([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID))

In short: DON'T USE THE LIVE CD IF YOU WANT TO INSTALL TO A RAID.

---

### Post by Methuselah on 2009-04-27
> **3rdalbum said:**
> I'm not sure you can call Ubuntu a "toy" just because it doesn't recognise your particular piece of exotic hardware. The vast majority of people don't use RAID, and most of the people who do have supported chips.

Having said that, it's obvious that you haven't read any Ubuntu documentation before posting your gripe - for shame.



([https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid))



([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto))



([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID))

In short: DON'T USE THE LIVE CD IF YOU WANT TO INSTALL TO A RAID.


Thanks 3rdalbum, I was about to say the same thing minus all the marvelous links.

---

### Post by mitten on 2009-04-27
"Toy", the wording may attacking some Ubuntu die hard fans. I can say sorry to those of people.

But on the other side, people should pay more rationality to see anything.

Put down all technical things in this stage. Since latest 2006 (Vista released), let take a look on user point of view. Matrix RAID platform OS installation on M$ story:

1. Setup BIOS to enable Matrix RAID.
2. Press Ctrl-I to setup RAID logical group across all disks.
3. Setup Windows Vista/Windows 7/Server 2008
4. The petty Intel RAID manager must not persent at this moment, but you must able to see the prepared volumes during the OS installation.
5. OS installation completed. 
6. Optional: Setup chipset driver and petty RAID manager, etc...

The main point is the point 6. Assume you forgot the drivers issues or you do not feel the system is not operating with normal speed (May be your old machine is too old), the OS is still working fine! The RAID volumes would be keep going with you.

Basic support of those common devices is very important. Compare with ICH10R or ICH10, ICH9R or ICH 9... The price different is only HK$100 usually. Don't think you do not need to use RAID is equal to nobody use RAID/just a little bit people use it. The common way for ICH##R users are building a RAID 0 volumes for VM/fast gaming/fast photo editing/etc.

User need to do too much extra things during the installation is not a good assumption on user acceptable level of the feeling - easy to use.

Be honestly speaking, "little bit improvement on user experience"(On technical man point of view may almost not a problem need to be improve) have done, Ubuntu must become a super star.

My boss usually says, "Don't think the small issue is not a issue. User just feels that it is a problem still exist..."

---

### Post by mitten on 2009-04-27
Actually, as I mentioned before. The Alternate Ubuntu 9.04 x64 installation disc is still make me crazy.

Before I leave to my office and write the first post about the "toy" here, the installation result is LILO installation fail!

I don't know why LILO come out with me. I am never mind to use any type of boot loader. The important thing is "work properly". It is very claar that the installation is fail, even all process has been completed. But no bootloader is not a complete job actually. May be I can manually deploy the boot loader on next time I see the machine and say good morning. It is still make me crazy enough.

My boss may just push me to install the Windows Server 2008 and create Virtual Hosts as soon as possible for others workmates testing software.

---

### Post by mitten on 2009-04-27
Before I really too tired and want to sleep, I found many and many issues reported on the Internet now. Many users started to complain the Matrix RAID supports issues!

As my previous reply state, Matrix RAID is really an important thing that Ubuntu normal installation disc should be supported. It is a MUST requested basic feature. Rather than any others high-tech disk volume management or new file system push to user. The first thing is very simple, where is my RAID volume? Don't concern it is REAL or FAKE RAID, user just want to use their volumes.

Alternate Installation Disc, Installation Document, FakeRAID... research... I think all of them should not push to any user just want setup the OS with RAID, a simple RAID come with Intel ICH chipset. Too much technical documentation need to be read and did many research before installation? Too crazy! User may want to build a fast HDD I/O platform for their video/photo editing jobs. They will care the Ubuntu RAID backend technique? Some body may want to build a platform for fast virtual machine hosting purpose. They also need to read the document and perform a one day research on the little bit task - OS installation?

In fact, back to the Windows Server is a good choice for me, and for users I have mentioned above. Less than two hours for installation and start my actual work! OS setup is not my major, you know?

HDD price is cheap, simple RAID is almost no extra cost nowaday. I am really hope to see all installation disc of Ubuntu or other Linux distributions would be include the MUST support of that common thing.

What next on my trouble? Just the users/project manager/boss election. They will tell me Windows or Linux in seconds while I just step in to the working room. They are really do not concern the technical issues... Just understanding the dead line pushing me stop to "playing" and be a good workmate to make more time for others finishing works. My prediction is 90% towards to Windows.

Die hard fans also should be stop angry with me too. I am still using Ubuntu on HomeServer and my notebook. Non critical and important areas still good for Ubuntu in this stage.

Just a little bit concept/idea are still missing. While the missing puzzle found, I must push more and more Linux solution to the valued customer/users.

Production machine may able to count the cost for buying Debian Linux/RedHat Linux/... any commercial Linux. Customer may care about the image and supporting. Before it would happening, development/testing environment should make the cost lower and lower... Free Linux distributions is our friends. Similar to MSDN Subscription, we can free to use/test/deploy/try migration on many many instance. It is the real world, Workable/not workable. Choice is simple and clear.

---

### Post by Wiebelhaus on 2009-04-27
For being such a "toy" It sure does fulfill my requirements at work and home and also in a friends Law office , but whatever it's a toy right?

I need an Internet air compressor so I can blow these fools dusty hind quarters off our message board.

---

### Post by karellen on 2009-04-27
from my point of view, I never felt the need for RAID. and, speaking in terms of actual hardware support out of the box, Ubuntu (as any major Linux distro) surpasses Windows (not speaking of Mac OS) anytime

---

### Post by Methuselah on 2009-04-27
:popcorn:> **mitten said:**
> Before I really too tired and want to sleep, I found many and many issues reported on the Internet now. Many users started to complain the Matrix RAID supports issues!

As my previous reply state, Matrix RAID is really an important thing that Ubuntu normal installation disc should be supported. It is a MUST requested basic feature. Rather than any others high-tech disk volume management or new file system push to user. The first thing is very simple, where is my RAID volume? Don't concern it is REAL or FAKE RAID, user just want to use their volumes.

Alternate Installation Disc, Installation Document, FakeRAID... research... I think all of them should not push to any user just want setup the OS with RAID, a simple RAID come with Intel ICH chipset. Too much technical documentation need to be read and did many research before installation? Too crazy! User may want to build a fast HDD I/O platform for their video/photo editing jobs. They will care the Ubuntu RAID backend technique? Some body may want to build a platform for fast virtual machine hosting purpose. They also need to read the document and perform a one day research on the little bit task - OS installation?

In fact, back to the Windows Server is a good choice for me, and for users I have mentioned above. Less than two hours for installation and start my actual work! OS setup is not my major, you know?

HDD price is cheap, simple RAID is almost no extra cost nowaday. I am really hope to see all installation disc of Ubuntu or other Linux distributions would be include the MUST support of that common thing.

What next on my trouble? Just the users/project manager/boss election. They will tell me Windows or Linux in seconds while I just step in to the working room. They are really do not concern the technical issues... Just understanding the dead line pushing me stop to "playing" and be a good workmate to make more time for others finishing works. My prediction is 90% towards to Windows.

Die hard fans also should be stop angry with me too. I am still using Ubuntu on HomeServer and my notebook. Non critical and important areas still good for Ubuntu in this stage.

Just a little bit concept/idea are still missing. While the missing puzzle found, I must push more and more Linux solution to the valued customer/users.

Production machine may able to count the cost for buying Debian Linux/RedHat Linux/... any commercial Linux. Customer may care about the image and supporting. Before it would happening, development/testing environment should make the cost lower and lower... Free Linux distributions is our friends. Similar to MSDN Subscription, we can free to use/test/deploy/try migration on many many instance. It is the real world, Workable/not workable. Choice is simple and clear.

Wow, this is a really long diatribe and TBH, I kind of skimmed through.
Most of it seems dedicated to proving Ubuntu is a toy based on your lack of the necessary knowledge to install it properly on your hardware.
This despite abundant testimony to the contrary from many people here; we use Ubuntu for real stuff!

Have you ever installed Windows on a machine with hardware or semi-hardware RAID?
Isn't there a point where the installer flashes a question about third party RAID hardware and you have to press a function key?
At this point, didn't you have to insert A FLOPPY that contains drivers for RAID devices so that windows can even install?
On my harwdare, if you do not do this, windows will not see any disks; is windows a toy too?

The extremely lengthy attempt at justification was not really necessary.
This is the point in a thread where one humbly acknowledges that he made a mistake and should have asked for help.
In fact, if you had asked for help you probably would have been pointed in the right direction very quickly.

---

### Post by Bios Element on 2009-04-27
Good for you, Go use windows. But remember, if you ever have a problem with it (by your logic.) then windows must be a toy too! ;)

---

### Post by wolfen69 on 2009-04-27
> **Bios Element said:**
> Good for you, Go use windows. But remember, if you ever have a problem with it (by your logic.) then windows must be a toy too! ;)

exactly. i guess everyone who brings a windows pc to a repair shop is using a toy also.

---

### Post by mitten on 2009-04-27
RAID platform server machine?

Sure, almost all server has RAID on production server room. They must have a good fit driver disc for OS installation. Process is just less than one hour to complete it.

Knowledge? I just want to say such basic common hardware should not push user to got too much research and document reading, right? Some people just complain me lack of knowledge... OK, you can keep going to say that. But on my point of view, I just setup the OS on a basic RAID hardware platform, why Ubuntu need me to do too much extra things? Nobody answer to this point up to this time!

You all love to play, or having too much time for play. On my situaton, it is not possible to let me play any more. Do you got the point?

If that problem occur in my home, I can play and play...till to the Ubuntu Alternate sucessfully installed. It is a dead line in front of me, you know? Install Windows Server 2008 is no extra knowledge required to prepared just on the simple volumes issues. My work is prepare a VMWare Workstation env., not on the OS backend. It is a office, not my home.

For those guys pay more attention to play with such basic things, fine. But I want to do more business, rather than spent office hour to setup the OS.

Using Windows PC is a toy also. Actually many people like that, but don't count me in. I have never put my computer for repairing almost 6 years. My boss's clients server also. All Windows Server working fine. I think if the protecton work has well prepared, it is not a toy also.

Technical man has their own future, I am not consider to debate on this point. but on my point of view, technical way is not a good way on my career. I don't want to be a tech. support guys only in front of my boss and other freelance consult work. Spend few days to study how to install a OS... It is not possible for me. The important thins running on the OS is the real valued items.

---

### Post by Saint Angeles on 2009-04-27
> **mitten said:**
> RAID platform server machine?

Sure, almost all server has RAID on production server room. They must have a good fit driver disc for OS installation. Process is just less than one hour to complete it.

Knowledge? I just want to say such basic common hardware should not push user to got too much research and document reading, right? Some people just complain me lack of knowledge... OK, you can keep going to say that. But on my point of view, I just setup the OS on a basic RAID hardware platform, why Ubuntu need me to do too much extra things? Nobody answer to this point up to this time!

You all love to play, or having too much time for play. On my situaton, it is not possible to let me play any more. Do you got the point?

If that problem occur in my home, I can play and play...till to the Ubuntu Alternate sucessfully installed. It is a dead line in front of me, you know? Install Windows Server 2008 is no extra knowledge required to prepared just on the simple volumes issues. My work is prepare a VMWare Workstation env., not on the OS backend. It is a office, not my home.

For those guys pay more attention to play with such basic things, fine. But I want to do more business, rather than spent office hour to setup the OS.

Using Windows PC is a toy also. Actually many people like that, but don't count me in. I have never put my computer for repairing almost 6 years. My boss's clients server also. All Windows Server working fine. I think if the protecton work has well prepared, it is not a toy also.

Technical man has their own future, I am not consider to debate on this point. but on my point of view, technical way is not a good way on my career. I don't want to be a tech. support guys only in front of my boss and other freelance consult work. Spend few days to study how to install a OS... It is not possible for me. The important thins running on the OS is the real valued items.
so 90% of the internet is hosted on a toy OS?

i'm sorry, i dont have time for this. i have to get some serious web work done on my ubuntu machine. some serious PHP programming. also, i'm spending my free time learning c++ and python... i guess it is a toy if you mean its seriously fun and easy to use.

---

### Post by Bios Element on 2009-04-27
> **mitten said:**
> Technical man has their own future, I am not consider to debate on this point. but on my point of view, technical way is not a good way on my career. I don't want to be a tech. support guys only in front of my boss and other freelance consult work. Spend few days to study how to install a OS... It is not possible for me. The important thins running on the OS is the real valued items.

Wait...you refuse to even spend a few DAYS learning things? I really feel sorry for your employer... Really dude all I can take from your posts is that your a troll. You never asked for help. You just posted with general flaming commentary. If you refuse to spend some time learning something then it's good you don't expect to use it in the future.

---

### Post by mitten on 2009-04-27
Sorry for something missing. You all assume I am a technical post staff?

Few days for that is means I am doing that side by side... Consult post is work on many and many things that you expected or not expected on every working days. Few days setup OS does not means 8 hours a day. Ok?

---

### Post by mitten on 2009-04-27
Very sad that almost all Ubuntu die hard fans does not consider my point. The basic common hardware support should be improve. Just sit down and selling your IT knowledge... users are all expert on IT? I think it is not ture.

Some guys replay here may not understand what is Matrix RAID also, I think. It is not a extra RAID card with complex RAID standard features...

Somebody also skip the Windows installation story part of my posts. Why Windows can basically support that basic common hardware? And Ubuntu do not want to? Just is a simple point for thinking. Don't keep show off any IT knowledge here. My point of view is user friendly level. Just want Ubuntu can improve something important but Ubuntu assume it is minor or not necessary...

---

### Post by Bios Element on 2009-04-27
> **mitten said:**
> Very sad that almost all Ubuntu die hard fans does not consider my point. The basic common hardware support should be improve. Just sit down and selling your IT knowledge... users are all expert on IT? I think it is not ture.

Some guys replay here may not understand what is Matrix RAID also, I think. It is not a extra RAID card with complex RAID standard features...

Somebody also skip the Windows installation story part of my posts. Why Windows can basically support that basic common hardware? And Ubuntu do not want to? Just is a simple point for thinking. Don't keep show off any IT knowledge here. My point of view is user friendly level. Just want Ubuntu can improve something important but Ubuntu assume it is minor or not necessary...

No, you assume you can be a jerk and get nice responses. Doesn't work that way. Firstly, I'll say right off that the "joe sixpack" doesn't know or care what a Matrix RAID is. Heck, I don't even know although I'll google it in a bit here.

Windows supports hardware because the hardware is made for windows, NOT because windows is made for the hardware. Heck, Windows can't detect my Nvidia 8800 of all things...A common card and it cannot detect it. No doubt it's because windows sucks.

Ubuntu supports TONS of hardware. I've only once had a single hardware issue and that only took about 30 minutes to correct. Ubuntu is improving every release and you saying it's not is flamebait at it's finest.

---

### Post by mitten on 2009-04-28
OK, I have a final response on this topic.

The word "toy" may not suitable in this siutation. Use "child"/"teeagers" may be better on the title.

Hope to see that non-extra card common hardware support is petty good on next release. User want to click next only on installing OS with basic common hardware platform. They know how to create a RAID group in BIOS for fast/protected working environment. Just want to have a better stage to doing their actual work in front of audience(clients/customer/users). They should not going to study how to build the stage for the show. Just want to use it.

Before I am be a consultant, leave to my previous software development career. Many years ago... computer just a tools, should be just a tools to helping people on work, and make fun on off duties (at night, Sat., Sun....) Too much technical thing surrounding human may make us too tired. Many programmers also like me... leave to the technical work and seek for consultant jobs or change the job nature...

You all are love to living with computer, I really feel it. Good, you guys doesn't like me, still have much heart to do so. I am going to back to basic, just let it as my tools...

Thanks all guys here. May be I have another question about Ubuntu in the future. This forum is contains full of power and human actually work hard for posts. I will try to discuss something here too. Bye...

---

### Post by wolfen69 on 2009-04-28
> **Bios Element said:**
> Firstly, I'll say right off that the "joe sixpack" doesn't know or care what a Matrix RAID is. Heck, I don't even know although I'll google it in a bit here.


right on. i'm beginning to like you. :-$

also, i don't see the typical windows user come in here and spout off...because the typical windows user would not come here.

---

### Post by wolfen69 on 2009-04-28
> **Bios Element said:**
> 
Ubuntu supports TONS of hardware. I've only once had a single hardware issue and that only took about 30 minutes to correct. Ubuntu is improving every release and you saying it's not is flamebait at it's finest.

hey BIOS, you look like a poor man's Wesley Crusher.   :lolflag:

---

### Post by karellen on 2009-04-28
this thread is a waste of time. I'm no Linux zealot, but this discussion is pure bashing. The OP can't seem to understand that the only one guilty for his RAID not being supported is the OEM. hardware is made for Windows, not vice versa

---

### Post by juancarlospaco on 2009-04-28
Just pay the Canonical Support if you dont know how to setup your hardware...

---

### Post by Bios Element on 2009-04-28
> **juancarlospaco said:**
> Just pay the Canonical Support if you dont know how to setup your hardware...

Or Hey, I got an idea! Make a post asking for help and see if anyone knows something! >.>

---

### Post by Insane_Homer on 2009-04-28
> **mitten said:**
> Very sad that almost all Ubuntu die hard fans does not consider my point. The basic common hardware support should be improve. Just sit down and selling your IT knowledge... users are all expert on IT? I think it is not ture.

Some guys replay here may not understand what is Matrix RAID also, I think. It is not a extra RAID card with complex RAID standard features...

Somebody also skip the Windows installation story part of my posts. Why Windows can basically support that basic common hardware? And Ubuntu do not want to? Just is a simple point for thinking. Don't keep show off any IT knowledge here. My point of view is user friendly level. Just want Ubuntu can improve something important but Ubuntu assume it is minor or not necessary...

Windows Support for Basic common hardware is good? You are having a laugh. The manufacturer supply an out of date driver on CD does not make windows better. 

I have had far less trouble with Ubuntu finding drivers for devices than I do for Windows (XP, Vista, 7, 2003 server and 2008 server). Not one of those OS's recognised all the hardware out the box... Ubuntu 8.10 and 9.04 did on 4 different machines for me. (GFX, wireless, Sound, printer, screen res et al). 

The only device that don't work on Ubuntu for me is the MS webcam, I wonder why? If you think driver support out the box is better in Winblows then you are delusional.

it's unfortunately that you feel Ubuntu is a toy because you don't feel the need to put in any effort into problem solving.

I've supported Windblows as my day-to-day job for over 12 years. I use Ubuntu by choice at home.

Tell me one thing, all these Windows Installs you have, are they all fully paid up licenses? By all means pay over £1000 for your piece of mind or save £1000 and put a little effort it yourself and contribute rather than bitch.

you bitch that you want server standard raid but want it on the cheap. Cheap hardware is crap on Windows too. I wouldn't buy no name brand bottom of the line equipment and then bitch about the OS. You build cheap you get cheap (probably why they only support winblows to start with).

You don't buy a banger of a car and bitch at Shell that the petrol is the reason it won't start

---

### Post by growled on 2009-04-28
> **mitten said:**
> Although version 9.04 of Ubuntu has been spreading and covering more and more users on the world. I think it is a toy. It is still a toy only.


One OS costs thousands of dollars in license and anti-virus and spyware programs, plus time to keep up with all your updates. The other OS costs nothing and doesn't need any anti-virus or spyware programs, and updates everything for you. Now, which one is the toy again?

---

### Post by Sophont on 2009-04-29
mittern,

sorry that you had trouble installing Ubuntu on your particular hardware.

But you make the common mistake of assuming that if you have trouble installing that there must be a universal problem.

Yet for many many on many hardware combinations an Ubuntu install works out of the box and at that stage already has more software installed and hardware auto-configured than most windows fresh installs.

I have no idea how common your particular RAID controller is but RAIDs are still rare exceptions for desktop systems. So you start of with a very unusual requirement for a desktop system.

On servers of course a RAID is a typical requirement. But if I prepare a server I also research beforehand what I buy and if it is supported by the os that I want to use (just happened a few months ago - prepared a new server for a friends company - looked up whether RAID controller is suppported by Linux - yes - bought, installed - no prob).

The Linux kernel in general and Ubuntu in particular support a very large number of hardware - but not all.
Windows supports a large number of hardware - but not all.
Main difference is that windows is usually sold pre-bundled on the computer - so all drivers issues have already been taken care of by the OEM.

If Windows work better for you - by all means - use it.

But calling Ubuntu/Linux a toy because you had trouble with a particular setup is not a fair judgement. It wpould be fairly easy to find users who had trouble with their hardware and windows drivers.
There were actually vast numbers of users having trouble with Vista when it came out, because they couldn't find working drivers for their hardware. Meanwhile hardware is coming out that doesn't have good drivers for XP anymore.
Does that make Windows a toy too?

I have installed windows on a number of servers - every time I had to do extra steps to install the RAID driver. Never worked out of the box - unlike the server I recently installed Ubuntu server on.

At the end of the day your milage will very depending on your particular combination of hardware - regardless of windows or Linux.
But the trend is already in Linux favor. A few years ago hardware support with Linux was way behind windows. Now it's close to parity. If the current trend continues we'll soon have windows trailing Linux in hardware support. In the long run the many individual closed source drivers can't compete with the open model and it's centralized repos. And the number of manufacturers supporting Linux or at least supplying better infos is rising - due to so many governments and big corps using Linux nowadays that they want a market share of.

Again - if windows work better for *your* purposes - no problem - use it. Remember to replace Notepad, Paint, IE, install a ton of software, defrag, de-malware and keep your preferred AV app up-to-date. And hunt for your drivers via Google - avoiding suspicious sites in the process.

p.s. I guess big corporations considered Vista a toy - they mostly skipped it.

---

### Post by ukripper on 2009-04-29
I  agree with you, ubuntu is certainly a toy when looked at it via perspective of a 10 year old, i guess that is pretty good to keep your kids busy with something constructive!:popcorn:

I guess on that above little note this thread should be closed!

---

### Post by Arup on 2009-04-29
If your mindset is such, a serious OS which is among the most transparent looks like a toy to you and OTOH, the OS whose only sustenance today is because gamers use it is serious, there is absolutely nothing to say. Hardware issues are nothing new in world of IT, there have been horrid drivers made for Windows by Creative which have caused BSODs, instability in general etc. antivirus, HIPS, firewalls make Windows crash or slow down, we have nothing like that to deal with on Ubuntu, all apps are patched for critical bugs, all you do is boot your Ubuntu daily and do what you origially intended to with your PC. Enjoy your Window, get Pwned and may the Conflicker be with you.

---

### Post by mitten on 2009-04-29
Somebody want this tread to be closed. Right, but those people were still written...

My original idea is just talking about the common onboard cheaper stuff support and friendly installation with that fake RAID. But people were almost all turned to KO somebody just say something may made fans disagreed or dislike to heard. The key point is the word "Toy".

Somebody may not read it all and just catch the word "Toy", then send me back to Widows world. Very disappointed for those of people. In fact, I am using Ubuntu at HomeServer and my own notebook.

Somebody put the common display card or "True" RAID on well OEM packing server machine and say something with me. Just stand on fans angle to speak to me. No need to answer this comparsion. I don't think common display card or TRUE RAID card are really common, widely appears than onboard Matrix RAID. On Windows, no display card driver must able to display the desktop as well. Just lost some features or very very high resolution options. It is a truth.

Just want to comment something Ubuntu can do better. But people just shouting here with the word "Toy". And do not want to consider on the improvement idea. OK, fine. Ubuntu fans are right, Ubuntu fans are win forever. This post posted here is not a right location. Because there is a fans club forum. People using RAID for fast desktop experience with low cost FAKE RAID is not a correct human being in this U World. People just want to use an OS as a tool also is not a correct human being. User must study the OS structure, OS concept, founders ideas, and everything surrounding the technical level document. 

My new knowledge got here is, people must pay attention, time, and efforts to got to know how to create/maintain a car, than you can  sit on and start to drive it  go got the destination.

My behavior has not changed at this moment. For fast finish task for client's user, just choose the best way I should not got too much trouble. Maintain duties is not my business. They have their own IT department or IT staff (at least one). At home, or on now critical urgent project, I am still happy to play with (or use "face to" here for safe) Linux.

My working story ending is the new PC machine sent back to the vendor (just a PC shop in this case). Something I was dislike to use. Before the new one arrive, I am still love to use different method to got Matrix RAID work on Ubuntu. Compare with commercial Linux and M$ Windows, they are trusted by most clients. Ubuntu Linux? They are really not wanna to use. Supporting cost too high, especially in SME that does not have a IT department. It is the real world. Don't think all companies must strong on IT sector. Windows may got more problems, but they can handling well in most of cases without any technical man or stand on OS expert.

My country may not same as your home town, technical man is not valuable. That's why I was not want to be a software development guys few years ago. Be a technical man here, just wait for be a poor man and work with 12-16 hours per day. And workmates just asking to helping them to fix or check anything that needs plug in power cord. e.g. something going down in the toilet, the LCD monitor color going worst...

May be you all living on the place that people are not look down on everybody that doing technical work. Enjoy... My real world is , if client user take a look on OS setup time and step, they must phone to my boss and request it must be changed to install Windows and all necessary things they need to see(the result, the things needed to be test on the VM) before lunch. And I must sit down and listen to my boss for one hour about working efficient.

---

### Post by kamitsukai on 2009-04-29
> **HappyFeet said:**
> Your reply confirms this.  ](*,)

There was no need for that.

I was using language befitting the previous replies to this thread

---

### Post by Bios Element on 2009-04-29
> **kamitsukai said:**
> I was using language befitting the previous replies to this thread

No, you were trolling and flaming while not providing any actual help/suggestions/constructive commentary.

---

### Post by kamitsukai on 2009-04-30
> **Bios Element said:**
> No, you were trolling and flaming while not providing any actual help/suggestions/constructive commentary.

excuse me? why don't you go check the first post made on this thread coincidently I was actually refering to one of your posts in the first place when you called mitten a ****

and considering your posts so far maybe you should rethink who the troll is?

> **Bios Element said:**
> No, you assume you can be a jerk and get nice responses. Doesn't work that way. Firstly, I'll say right off that the "joe sixpack" doesn't know or care what a Matrix RAID is. Heck, I don't even know although I'll google it in a bit here.

Windows supports hardware because the hardware is made for windows, NOT because windows is made for the hardware. Heck, Windows can't detect my Nvidia 8800 of all things...A common card and it cannot detect it. No doubt it's because windows sucks.

Ubuntu supports TONS of hardware. I've only once had a single hardware issue and that only took about 30 minutes to correct. Ubuntu is improving every release and you saying it's not is flamebait at it's finest.

> **Bios Element said:**
> Or Hey, I got an idea! Make a post asking for help and see if anyone knows something! >.>

I'm not posting on here again so if you want insult me with your posts id prefer it if you PM'ed me as none of this has helped mitten with his original problem

---

### Post by starcannon on 2009-04-30
> **mitten said:**
> Although version 9.04 of Ubuntu has been spreading and covering more and more users on the world. I think it is a toy. It is still a toy only.

Hmm, mine works great, I use it for real life, indeed it does all of my daily chores, including college and work; so, I'd have to disagree, its not only a toy, its also a great tool.

> 
Common mistake or must not missing items that are missing. This point makes me no more interest to setup a real workstation that as my secondary important platform besie my Vista PC.

No worries, use what works for you, thats what I do.

> 
Intel Matrix RAID, common low cost ethernet card, common x86-64bit CPU... Everything surrounding this three area may not makes too much human really want to have a Ubuntu 9.04.

Much of this is really dependent on tech ability, most people do not install operating systems; indeed, most people buy computers with operating systems already installed. I drive a car, I can not rebuild a transmission, retrofit drive train, or customize my paint; this however does not mean that my car is not reliable and useful, it just means that I occasionally have to pay someone to do car related tasks for me.

> 
My system is not a top top PC standard. But I have been trying to setup Ubuntu 9.04 x86 64bit. The final result is fail too.

"Standard" is a broad term, I would need to see lshw output before I would know whether you had equipment that I would consider "standard"; and not only is it a broad term, its really an objective term; what is standard to me may be exotic to you, and turn about. I build my systems with Linux in mind, I know going into it that my gear is Linux supported.

> 
LiveCD installation mode plus extra driver during the Live sesson, fail.
Customize the installation disc by Remastersys includes necessary drivers, fail.
AFter about 8 hours war with the installation story, the ending is no ending... Still fail on something.

You may need to reconsider some hardware, or just stick with the OS that works, and then if your still interested in Linux be sure to research your next computer purchase and buy something that has all Linux supported hardware in it. Dell, System 76, and Zareason are just a few places you can go to buy computers that ship with Ubuntu preinstalled, everything just works, turn it on and go.

> 
Install inside the Windows? x86 64bit system with Matrix RAID seems must be fail.

Not sure what you mean here, was that a Wubi install?

> 
Up to this time, I think it is not a released. It is just a World Wide Test edition, WWT beta.

Well thats one opinion, and if true, at least I'm not paying to be a test pilot.

> 
Additionally, something must going wrong on large size HDD, such as, 1TB, 1.5TB HDD... many people just got the fail result.

Never had any problems like that myself /shrug. Again, use what works, and if still interested make sure the next build or purchase is based around linux compatability and I think you'll have a smooth experience.

GL and have fun regardless of which OS you choose. As for me, I'll keep on :guitar: in the free world.

---

