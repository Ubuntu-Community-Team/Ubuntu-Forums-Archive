---
title: "Linux has long way to go"
date: 2008-09-16
forum: Testimonials &amp; Experiences
---

### Post by bobwalters on 2008-09-16
I have just downloaded the latest distro of Ubuntu and I am trying to install a video driver.  I'm sure I will figure it out eventually but compared to the OS a lot of people hate it is a PAIN IN THE BUTT! I think many people who bash the boys in Redmond tend to forget what is really necessary to make an OS accessible to the general public and how much effort it takes.

Bob

---

### Post by hansdown on 2008-09-16
What video card are You using bobwalters ?

---

### Post by karlr42 on 2008-09-16
Video drivers for nVidia and ATI are easy with [Envy](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by tuxxy on 2008-09-16
Enable your driver at system > admin > hardware drivers, if no luck download envyng and use that to install nvidia/ati drivers.

Heres a [video driver guide ]("https://help.ubuntu.com/community/Video")if you need more information

---

### Post by bobwalters on 2008-09-16
I am using an NVIDIA 8600GT. And no offense but it is not easy.  What is easy is double clicking on an exe and running the install and having the system take care of everything. Even installing from Computer|Manage is easy but having to type stuff on a commnad line is never easy. I have not had to do that in years. I will figure it out it is just a matter of dusting off some old skills.  I just want to point out that if the Linux community ever wants this to go truly mainstream the whole process needs to be automated. 

Bob

---

### Post by tuxxy on 2008-09-16
> **bobwalters said:**
> I am using an NVIDIA 8600GT. And no offense but it is not easy.  What is easy is double clicking on an exe and running the install and having the system take care of everything. Even installing from Computer|Manage is easy but having to type stuff on a commnad line is never easy. I have not had to do that in years. I will figure it out it is just a matter of dusting off some old skills.  I just want to point out that if the Linux community ever wants this to go truly mainstream the whole process needs to be automated. 

Bob

So you have the same model graphics card as me, most likely a GT? 

A 8600GT should run out of the box, the driver for your card can be installed very easily, like 3 mouse clicks, the most you will have to do is download the program envyng to select the correct driver and install it automatically for you, even in windows you will have to download the driver.

Why would you have to use the terminal, to download envyng open synaptic and search for it, then run it from your menu as you would any other app.

---

### Post by bobwalters on 2008-09-16
I downloaded the latest driver from NVIDIA for Linux and I am trying to install it.  I will no doubt do the same for ATI.

Bob

---

### Post by Bios Element on 2008-09-16
> **bobwalters said:**
> I downloaded the latest driver from NVIDIA for Linux and I am trying to install it.  I will no doubt do the same for ATI.

Bob

Just get them from the package manger. Ubuntu will handle them just fine. Your going to way to much work. Use the solution tuxxy posted. It'll work just fine.

---

### Post by cardinals_fan on 2008-09-16
> **tuxxy said:**
> Enable your driver at system > admin > hardware drivers, if no luck download envyng and use that to install nvidia/ati drivers.

Heres a [video driver guide ]("https://help.ubuntu.com/community/Video")if you need more information

> **bobwalters said:**
> I am using an NVIDIA 8600GT. And no offense but it is not easy.  What is easy is double clicking on an exe and running the install and having the system take care of everything. Even installing from Computer|Manage is easy but having to type stuff on a commnad line is never easy. I have not had to do that in years. I will figure it out it is just a matter of dusting off some old skills.  I just want to point out that if the Linux community ever wants this to go truly mainstream the whole process needs to be automated. 

Bob
I've quoted tuxxy's helpful post (above) for emphasis.  If it doesn't work, post a thread in Absolute Beginner Talk for help.

Remember, "easy" is subjective.  I personally consider typing a couple commands much easier than blindly clicking through a wizard.

---

### Post by ronnielsen1 on 2008-09-16
> I have just downloaded the latest distro of Ubuntu and I am trying to install a video driver. I'm sure I will figure it out eventually but compared to the OS a lot of people hate it is a PAIN IN THE BUTT!
Um, Yes, I've been completely frustrated with linux but I've also had terrible installs with windows looking for days to find drivers and having to restart the computer for every stupid little thing.

---

### Post by eye208 on 2008-09-17
> **bobwalters said:**
> I am using an NVIDIA 8600GT. And no offense but it is not easy.  What is easy is double clicking on an exe and running the install and having the system take care of everything. Even installing from Computer|Manage is easy but having to type stuff on a commnad line is never easy. I have not had to do that in years. I will figure it out it is just a matter of dusting off some old skills.  I just want to point out that if the Linux community ever wants this to go truly mainstream the whole process needs to be automated.
The process is automated. It just doesn't involve double-clicking an exe, and that's why you are confused. You are applying Windows knowledge to Linux because you think the Windows way is the right way. Sorry, but it's not.

Installing a video driver in Ubuntu is a piece of cake. The system even automatically picks the correct driver for you. No need to know the type of video card. No need to know the download location. All you need to do is mark a checkbox in the driver manager and confirm the installation. It's so simple, a three year old child could do it.

---

### Post by ukripper on 2008-09-17
> **karlr42 said:**
> video drivers for nvidia and ati are easy with [envy](http://albertomilone.com/nvidia_scripts1.html)

+1

---

### Post by ukripper on 2008-09-17
> **tuxxy said:**
> enable your driver at system > admin > hardware drivers, if no luck download envyng and use that to install nvidia/ati drivers.

Heres a [video driver guide ]("https://help.ubuntu.com/community/video")if you need more information

+1..

---

### Post by Shippou on 2008-09-17
> **eye208 said:**
> The process is automated. It just doesn't involve double-clicking an exe, and that's why you are confused. You are applying Windows knowledge to Linux because you think the Windows way is the right way. Sorry, but it's not.

Installing a video driver in Ubuntu is a piece of cake. The system even automatically picks the correct driver for you. No need to know the type of video card. No need to know the download location. All you need to do is mark a checkbox in the driver manager and confirm the installation. It's so simple, a three year old child could do it.

+2. +1 for the 1st paragraph and +2 for the second paragraph.

Nice analysis.

---

### Post by Teamgeist on 2008-09-17
> **bobwalters said:**
> I downloaded the latest driver from NVIDIA for Linux and I am trying to install it.  I will no doubt do the same for ATI.

Bob

This is not neccessary!
Ubuntu provides the driver via the package manager and will set everything up for you automatically.
Just go to System--> Administration --> Hardware Drivers

In case this does not work go to System--> Administration--> Synaptic Package Manager and from there search for envyng-gtk and install it.

You have to understand that installing software on a Ubuntu (or Linux in general) System works differently than in the Windows world.

Through the package managaer you are able to download and install thousands of Programs from the Repositories provided by Ubuntu.

Once you have used Synaptic (package manager) you will not want to use anything else anymore and will find it anoying to install software the "Windows way" since you don't have to go to houndreds of different websites to get the software you want/need.

This has been my experienceat least.

Accept that Linux/Ubuntu is NOT Windows and does not want to be.
Things work differently but they work very well.

Give it a shot.

/edit: Damn. Shippou was slightly faster. ;-)

---

### Post by starcannon on 2008-09-17
Installing a video driver is generally as simple as 4 clicks and a reboot in Ubuntu. Occasionally its more involved, but then again, the same can be said of that redmond system your talking about; and at the end of the week it all works out nicely when I'm not scouring a registry in safemode trying to outwhit the latest virus.

Linux has arrived.

> **bobwalters said:**
> I have just downloaded the latest distro of Ubuntu and I am trying to install a video driver.  I'm sure I will figure it out eventually but compared to the OS a lot of people hate it is a PAIN IN THE BUTT! I think many people who bash the boys in Redmond tend to forget what is really necessary to make an OS accessible to the general public and how much effort it takes.

Bob

---

### Post by jaqie on 2008-09-17
> **starcannon said:**
> Installing a video driver is generally as simple as 4 clicks and a reboot in Ubuntu. Occasionally its more involved, but then again, the same can be said of that redmond system your talking about;
That's (when more is involved) is not the fault of windows, it's the fault of the video card maker, when in windows.  When in linux and it's not simple, it's more hazy where the "blame" is depending on many factors like if it is an OEM binary (like the nvidia driver) or a user-contributed file, or... But I digress.
> and at the end of the week it all works out nicely when I'm not scouring a registry in safemode trying to outwhit the latest virus.
That is not the fault if windows. The only thing that is the fault of windows is it's default security mode, default open.  Change that, and things work swimmingly on windows. I have not had a virus on my main pc (xp pro) in... four? five years? and I am on it about ten to sixteen hours a day nearly every day.  As someone just said in another post, downloading and running an exe to install a driver is the way things work in windows, in ubuntu things do not work like that. Same thing here, it's just done different. The root of the problem here with windows is the default security model - default open - which is changeable with a bit of knowledge.

To each their own, neither is better or worse, just very different then eachother.

In my opinion, this is where things stand at the moment: for mom and pop, grandmas, et cetra, those type of users: ubuntu is hands down the best os, all the way up to power users and heavy PC gamers. Those are where windows is still a very viable and often necessary OS.  Windows is not the best choice anymore for end users.

---

### Post by starcannon on 2008-09-17
jaqie, 

>  To each their own, neither is better or worse, just very different then eachother.     Agreed; and granted, if one behaves and doesn't allow windows to catch a virus it can stay healthy. However, I do like not having to be looking over my shoulder, or running windows in tinfoil hat mode. I hear you, truly I do, and I agree that for certain projects windows is still the best choice, and in those situations I have Virtual Box; I can keep windows safe from itself in there. 

Anyway, I still think that Linux has arrived, and that Windows is now truly the OS that needs to play catch up; this is not a "religious" perspective, it is truly an objective observation. If I were at this moment going to go out and buy a non-linux OEM computer, it would be a Mac, not because I have any fond feelings for Apple, but because it is just stable, predictable, and** relatively** safe. Anyway, I think that Windows can come back, but I think it's going to take concentrating on Operating Systems, and not worrying themselves with DRM, Xboxes, and Xunes; its going to take not getting involved in decade long trials, and its definately going to take innovation as opposed to litigation and lobbying. 

Have fun, and I really enjoy your views, nice to see someone who isn't just coming from a fan-boy mentality.
Rob

---

### Post by jaqie on 2008-09-17
> **starcannon said:**
> jaqie, 

Agreed; and granted, if one behaves and doesn't allow windows to catch a virus it can stay healthy. However, I do like not having to be looking over my shoulder, or running windows in tinfoil hat mode.
That's just my point. With some reconfiguration and different app choices, you don't have to worry in windows. I sure don't.  I don't run in "tinfoil hat mode" on windows, quite far from it as a matter of fact. Ive found many very good freeware programs ive never heard of before, and tried them, and loved them. A few ive found malware in, not by the antivirus but by trying to modify things they have no permission to, getting permission denied, and doing things from crashing to giving an error to what have you.
> I hear you, truly I do, and I agree that for certain projects windows is still the best choice, and in those situations I have Virtual Box; I can keep windows safe from itself in there.
See, there is still that view you seem to have that windows itself is the issue, where it is not - it is the default settings, and app choices that are the heart of the issue.  the best example (of many) is IE.  Windows' included apps, and their default security settings are the problem, the os is quite capable of being a very secure, robust, stable OS, and my system and many others proves that. So many end user's systems prove the other side of that, as well, that in default settings with default apps windows has serious problems.
> Anyway, I still think that Linux has arrived, and that Windows is now truly the OS that needs to play catch up; this is not a "religious" perspective, it is truly an objective observation.
I totally agree, and they are trying. If nothing else, microsoft has proven many times in their past that they try something new to them, flub it up badly, and keep trying until they get it to work, and work well. Now they are finally trying to get security as default mode to work and they flubbed it up, give 'em time. They got reliability to work quite well when switching from 9x kernel to NT kernel. They will *eventually* get this right, too. In the mean time, there is a free OS out there that is doing much better, and that is the one I recommend to end users hands down... Ubuntu.
> If I were at this moment going to go out and buy a non-linux OEM computer, it would be a Mac, not because I have any fond feelings for Apple, but because it is just stable, predictable, and** relatively** safe.
Yes, it has come a long way since going to OSX... OSX is based on BSD, which is a cousin to linux.  I used to be a FreeBSD fangirl, and ran it as my main OS for about a year, until I got sick and tired of babysitting make.  That is another *nix alternative out there that is turnkey, and worth looking at for end users.
> Anyway, I think that Windows can come back, but I think it's going to take concentrating on Operating Systems, and not worrying themselves with DRM, Xboxes, and Xunes; its going to take not getting involved in decade long trials, and its definately going to take innovation as opposed to litigation and lobbying. 
That's not windows, that's microsoft.... make sure you keep the two seperate, as they are. MS is the company, windows is one of many products they make and one of many interests they have.  Yes, microsoft has serious issues as a company IMO being in bed with so many of the "big brother" companies MPAA RIAA and such, and I totally agree they need to get that stick out their bum to fix things right.  That is the biggest reason I refuse to run vista, I still stick with XP.
> Have fun, and I really enjoy your views, nice to see someone who isn't just coming from a fan-boy mentality.
Rob
Same here, definitely.
Sincerely,
~Jaqie Fox

---

### Post by eye208 on 2008-09-17
> **jaqie said:**
> That's (when more is involved) is not the fault of windows, it's the fault of the video card maker, when in windows.  When in linux and it's not simple, it's more hazy where the "blame" is depending on many factors like if it is an OEM binary (like the nvidia driver) or a user-contributed file, or... But I digress.
Did you notice that the vast majority of hardware devices does not require driver installation in Linux at all?

Linux drivers are kernel modules. They are a part of the kernel source tree. Most hardware vendors either contribute driver sources to the kernel themselves or at least publish the specifications so that the Linux kernel developers can write drivers on their own based on that information. Note that the developers do this free of charge.

The only reason why some drivers have to be installed separately (ATI, Nvidia) and others are not available at all (Broadcom wireless) is because the hardware manufacturers refuse to release driver sources and/or specs. If that is the case, there is **nothing** the Linux kernel developers can do about it. If you experience trouble installing drivers on Linux, it is always the hardware vendor's fault because **there should not be any driver installation at all.**

Some people may think that vendors should not be required to release sources or specs with their hardware products. These people fail to understand that Linux is

[list=a][*]platform-independent and[*]constantly evolving.[/list]
Windows supports only one CPU architecture; Linux supports dozens, from smartphones to mainframes. The time between two major releases of Windows may be up to 5 years; Ubuntu's release cycle is 6 months. No single manufacturer can handle this beast alone and release binary drivers for all possible configurations. The only viable way to keep drivers up to date with multiple platforms and multiple kernel revisions is by making them a part of the source tree used to build the kernel. There is no other way.

---

### Post by bmac on 2008-09-17
I don't understand why individuals believe that by simply installing Ubuntu (free OS), they feel automatically entitled to complain, bash or compared it to Windows. Never mind that it required a community effort just to provide this free OS. One must remember that it is not Windows and comparing functionality or usability between the two OS's won't resolve the issue of new user expectations.

Uninstall works - If you don't like Ubuntu or it doesn't meet your expectations then I strongly suggest uninstalling it. Or better yet try the Disk prior to installing. As I previously stated - Simply because you install Ubuntu for free and it doesn't meet your expectation, you shouldn't feel enabled, entitled or required to complain/bash the OS. If you prefer a Windows environment then use Windows. I don't think anyone in this forum will be offended...

I have used Ubuntu since FF on all five of our home systems and never plan on returning to Windows... So I uninstalled Windows and installed Ubuntu. Strange thing is I didn't return to a Windows forum and complain/bash or waste time making comparisons.. Wonder why????

---

### Post by nxtgen59 on 2008-09-17
> **tuxxy said:**
> So you have the same model graphics card as me, most likely a GT? 

A 8600GT should run out of the box, the driver for your card can be installed very easily, like 3 mouse clicks, the most you will have to do is download the program envyng to select the correct driver and install it automatically for you, even in windows you will have to download the driver.

Why would you have to use the terminal, to download envyng open synaptic and search for it, then run it from your menu as you would any other app.

This paticular card is well supported. If you were willing to install Ubuntu in the first place on your hard drive then Kudos to you. You have taken a great first step. Before you boldly make an accusation such as "Linux has a long way to go" it would be better simply to ask for help. The community being what it is chose to help you in spite of your insult. But, remember again this is not Microsoft it is GNU/Linux they are not comparible they are apples and oranges. It is something new to learn and probably will not be super easy. Trust me as computer technician i know that many people find it just as difficult to click an *.exe and they answer the questions. It is just something new to learn. Thanks and have fun with the unbelivable community support that Linux specifically Ubuntu is proud of. :)

---

### Post by nxtgen59 on 2008-09-17
My post is reply to bobwalters. Sorry tuxxy if I implyed that you were the one with the attitude. The point in quoting you was to illustrate that you were helping him inspite of his bold comment.

---

### Post by jaqie on 2008-09-17
> **eye208 said:**
> Did you notice that the vast majority of hardware devices does not require driver installation in Linux at all?
Yep, it's exactly why I said they do things in different ways. Did you notice that?
> Linux drivers are kernel modules. They are a part of the kernel source tree. Most hardware vendors either contribute driver sources to the kernel themselves or at least publish the specifications so that the Linux kernel developers can write drivers on their own based on that information. Note that the developers do this free of charge.
Yep, definitely. And when those do not work properly (which has happened does happen, and will again) they are the ones to blame.  This is exactly what I meant when I said that who is to blame is foggier in linux.  My best friend is a firefox code committer, and used to be a very active asterisk developer as well as doing work here and there on kernel drivers, I know this much better then you think. They should be lauded for helping, even when what they do doesn't work (which is not often) because yes they are doing volunteer work.  I didn't write a book in my post, and it seems you assumed one thing when the other was the case with what I wrote and what I did not say. Should every post in a forum be longer then a closed-source EULA? I think not.
> If you experience trouble installing drivers on Linux, it is always the hardware vendor's fault because **there should not be any driver installation at all.**
As for drivers in linux (and not aimed only at installed binaries as your statement was), they do not always function properly (all, not just binary drivers from MFRs).
> Some people may think that vendors should not be required to release sources or specs with their hardware products. These people fail to understand that Linux is platform-independent and constantly evolving.
it is their product, they designed and built it. they have the **right** to not divulge information about it, though it can definitely hurt sales, and is a stupid way to go.
> The only viable way to keep drivers up to date with multiple platforms and multiple kernel revisions is by making them a part of the source tree used to build the kernel. There is no other way.
Definitely agreed there, I hate the way drivers are done in windows, but it's the way it's done.
It should be more similar to what you want, but you know the saying... wish in one hand crap in the other, see which gets filled first. ;)

---

### Post by nxtgen59 on 2008-09-17
Also let's remember that anyone who has been using nVidia card for any amount of time will testify to the fact that thier drivers suck. Especially in windows thier drivers crash and give you blue screens alot. I actually prefer nVida because i have found the hardware to be of better quality. But the drivers over all leave something to be desired.

---

### Post by jaqie on 2008-09-17
> **nxtgen59 said:**
> Also let's remember that anyone who has been using nVidia card for any amount of time will testify to the fact that thier drivers suck. Especially in windows thier drivers crash and give you blue screens alot.
Whoa, whoa whoa whoa there. nVidia drivers are *ANYTHING* but unstable and slow in windows. Have you ever tried ATi's drivers extensively on windows? Ugh. The BS I put up with ATi drivers in windows is what drove me from liking ATI to trying nvidia again...and since then I have grown to adore the stability configureability and speed of the nvidia hardware **and drivers**. Their new .net control panel isn't nice, but that's easily disabled to classic control panel which still functions perfectly and has more options then any other driver I have ever seen nvidia ati or third party.

If you are having trouble with nvidia drivers in windows, something else is to blame.

---

### Post by nxtgen59 on 2008-09-17
My post was not to start a fight. Plain and simple i am a computer tech and i have noticed nvidia drivers specifically crashing a system more than any other driver. this is from personnel experience. I am happy for you if you have not had this problem. Many of my customers have. Not that ATI is much better. I don't have problems with thier drivers after i get the latest update to them but out of the box they are most of the time in my experience inadaquite. Again i do prefer nvidia as the hardware is wonderful but i really would like to see better out of the box drivers.

---

### Post by jaqie on 2008-09-17
> **nxtgen59 said:**
> My post was not to start a fight.
Neither did I post with the intention of fighting.
> Plain and simple i am a computer tech and i have noticed nvidia drivers specifically crashing a system more than any other driver. this is from personnel experience.
The problem that results in nvidia drivers crashing systems is almost always sourced from another part of the system malfunctioning. Usually a flaky/marginal power supply, bad RAM, or flaky/marginal motherboard bridge chip.  If you are having problems with the nvidia driver crashing locking or BSoDing, check the other parts of the system, and also check the power supply outputs with an oscilloscope. You will find that in every case it is from bad hardware, and this includes bad video cards.

Though I admit a certain range of their drivers in the past HAVE had stability problems like you mention, none of the drivers they have had for about two years now have given any of these problems when there weren't hardware sources for them.

Oh, and I've not mentioned it here yet, but I have been a PC and small network tech for 16 years now, with a specialization in PC hardware down to component level.
> I am happy for you if you have not had this problem. Many of my customers have. Not that ATI is much better. I don't have problems with thier drivers after i get the latest update to them but out of the box they are most of the time in my experience inadaquite. Again i do prefer nvidia as the hardware is wonderful but i really would like to see better out of the box drivers.
It is not just me that has "not had this problem" After a time, we sold nvidia video cards exclusively in our gamer systems, and lo and behold every single time one had problems with reliability, one of the pieces of hardware was marginal to bad.  Most of the time it was the power supply putting out horribly unstable voltages, but some of the time the video card, motherboard, or RAM was marginal to bad and casuing the issues.

---

### Post by nxtgen59 on 2008-09-17
> **jaqie said:**
> The problem that results in nvidia drivers crashing systems is almost always sourced from another part of the system malfunctioning. Usually a flaky/marginal power supply, bad RAM, or flaky/marginal motherboard bridge chip.  If you are having problems with the nvidia driver crashing locking or BSoDing, check the other parts of the system, and also check the power supply outputs with an oscilloscope. You will find that in every case it is from bad hardware, and this includes bad video cards.

My last reply to this as i will not be drawn into a pissing contest. I am well aware of the troubleshooting process. I have seen all these issues. I have also seen were updating the driver has fixed many. Plain and simple. 

I have seen many out of the box drivers for nvidia that are bad. that is not what the original context of the post was about. I was trying to say that sometimes even major corporations screw up there drivers for major Operating Systems. I have seen Creative do this as well as VIA. nvidia was just the example i chose. My intent was not to offend but to list an example so that it might be better understood the challenges that are involved with writting good drivers. The fact that most hardware that runs on GNU/Linux requires no installation of drivers and never crashes due to a driver issue, is testament to the fact that those who write these for the Linux comunity are definately professionals in thier field. 

Does that explain my position better?

---

### Post by bmac on 2008-09-17
Why this incessant need to defend Windows or Ubuntu? Pointing fingers at which system functions better on which drivers, only benefits those that argue. Defending Windows is useless on a Ubuntu forum, unless you intend is to recruit. I've used Windows since 3.1 and was in the SEM field for years working at component level. Integrating windows systems with electron microscopy technology. Never did I worry about a driver working - it either did or didn't. Now it appears that not only do we concern ourselves with hardware driver availability, but also which OS best utilizes said driver and argue over the benefits of each.

How does this help a new user? If a new user installs Ubuntu and requires a hardware driver that either is inferior or not available from the vendor, how does arguing over which OS is better, improve the new users situation? If the new user didn't investigate the OS prior to installation and confirm compatibility, how is that the responsibility of Ubuntu / Linux / Windows or any OS? Logic would suggest that prior to installing a new OS a review of system compatibility would be mandatory. Yet quite often on this forum a new user requests support for that very issue. Rather than arguing which OS is better or more user friendly, Why not write drivers and provide them to Ubuntu? Don't have time or knowledge then maybe aruging is fruitless - as it appears to take both. This oneupmanship is getting old in my opinion....

If an OS doesn't work for you or your system (and you don't wish to modify your system) - **Don't use it**. **How simple is that? At least you have a choice, if MS had it's way - you wouldn't...**

I don't understand when receiving the benefit of a free OS, some individuals can't refrain from complaining, bashing or comparing the OS. I didn't pay any money for Ubuntu and if I wasn't satisified I could have just thrown it away. I can't count how many things I've paid for (including Windows) that I've thrown away....:-k

---

### Post by jaqie on 2008-09-17
[http://www.google.com/search?q=define:forum](http://www.google.com/search?q=define:forum)
First result: ***a public facility to meet for open discussion***

Open discussion. I see no oneupsmanship here, no defending, just an open discussion of ideas, principles, and **experiences**. (note the subforum title?)

No rules are being broken here. If you do not like the content of a thread **you are free to leave it**.

---

### Post by nxtgen59 on 2008-09-17
My post was made in error

---

### Post by eye208 on 2008-09-17
> **jaqie said:**
> And when those do not work properly (which has happened does happen, and will again) they are the ones to blame.  This is exactly what I meant when I said that who is to blame is foggier in linux.
It seems we were talking about different things. The topic was not about bugs in drivers because bugs are everywhere anyway, all the time. The topic is about the troubles that you may go through when installing a driver manually. See the first post in this thread. Installing a driver manually is something that is not supposed to happen at all. If it does happen, the hardware vendor is to blame because he did not contribute in a way appropriate for Linux (i.e. sources or specs) or he did not contribute at all.

> It should be more similar to what you want, but you know the saying... wish in one hand crap in the other, see which gets filled first. ;)
The most important thing is not to fill a hardware vendor's pocket with money unless he offers good Linux support. For example, I will never experience the Broadcom wireless trouble because Broadcom is on my list of products not to buy.

This is also the first thing that I tell my friends if they feel they want to give Linux a shot. Unfortunately most people still choose their computers without Linux in mind. You can see them run into the Broadcom trap over and over again without ever blaming Broadcom. For some reason they would never blame Mac OS for being incompatible with 95% of the world's PCs, but they will surely blame Linux for being incompatible with 5%. So I just keep warning anyone upfront: Unless the Ubuntu live disc recognizes all of your hardware, either replace the hardware or keep your hands away from Linux.

---

### Post by nxtgen59 on 2008-09-17
> **bmac said:**
> Why this incessant need to defend Windows or Ubuntu? Pointing fingers at which system functions better on which drivers, only benefits those that argue. Defending Windows is useless on a Ubuntu forum, unless you intend is to recruit. I've used Windows since 3.1 and was in the SEM field for years working at component level. Integrating windows systems with electron microscopy technology. Never did I worry about a driver working - it either did or didn't. Now it appears that not only do we concern ourselves with hardware driver availability, but also which OS best utilizes said driver and argue over the benefits of each.

How does this help a new user? If a new user installs Ubuntu and requires a hardware driver that either is inferior or not available from the vendor, how does arguing over which OS is better, improve the new users situation? If the new user didn't investigate the OS prior to installation and confirm compatibility, how is that the responsibility of Ubuntu / Linux / Windows or any OS? Logic would suggest that prior to installing a new OS a review of system compatibility would be mandatory. Yet quite often on this forum a new user requests support for that very issue. Rather than arguing which OS is better or more user friendly, Why not write drivers and provide them to Ubuntu? Don't have time or knowledge then maybe aruging is fruitless - as it appears to take both. This oneupmanship is getting old in my opinion....

If an OS doesn't work for you or your system (and you don't wish to modify your system) - **Don't use it**. **How simple is that? At least you have a choice, if MS had it's way - you wouldn't...**

I don't understand when receiving the benefit of a free OS, some individuals can't refrain from complaining, bashing or comparing the OS. I didn't pay any money for Ubuntu and if I wasn't satisified I could have just thrown it away. I can't count how many things I've paid for (including Windows) that I've thrown away....:-k


You are correct. I apologize.

---

### Post by jaqie on 2008-09-17
> **eye208 said:**
> Installing a driver manually is something that is not supposed to happen at all. If it does happen, the hardware vendor is to blame because he did not contribute in a way appropriate for Linux (i.e. sources or specs) or he did not contribute at all.
You do realize that ubuntu IS NOT linux right? it is one distribution based on linux.  There are a lot of *nix out there where you do have to, in a way, install a driver... build kernel modules for it, configure their conf files, compile them.  I used to be a fangirl of FreeBSD, ran it as my main OS for about a year, and you definitely run into problems you have to fix with drivers (kernel modules) there. There are some actual linux distros that work just about exactly like FreeBSD.
> The most important thing is not to fill a hardware vendor's pocket with money unless he offers good Linux support. For example, I will never experience the Broadcom wireless trouble because Broadcom is on my list of products not to buy.
There is one product they make that I will. It is inside the linksys WRT54GL series... because they have full linux compatibility.
> This is also the first thing that I tell my friends if they feel they want to give Linux a shot. Unfortunately most people still choose their computers without Linux in mind. You can see them run into the Broadcom trap over and over again without ever blaming Broadcom. For some reason they would never blame Mac OS for being incompatible with 95% of the world's PCs, but they will surely blame Linux for being incompatible with 5%. So I just keep warning anyone upfront: Unless the Ubuntu live disc recognizes all of your hardware, either replace the hardware or keep your hands away from Linux.
Yeah, no kidding. broadcomm isn't the only one, though, sadly, far from it... just one of the worst.

---

### Post by eye208 on 2008-09-18
> **jaqie said:**
> You do realize that ubuntu IS NOT linux right? it is one distribution based on linux.
Yes, Captain Obvious, I do. Trust me on this. I've been around for a while.

> There are a lot of *nix out there where you do have to, in a way, install a driver... build kernel modules for it, configure their conf files, compile them.
You still don't get what I am talking about. Maybe it helps to quote someone else's summary of the problem:

[quote=http://www.kroah.com/log/linux/stable_api_nonsense.html]So, if you have a Linux kernel driver that is not in the main kernel tree, what are you, a developer, supposed to do? Releasing a binary driver for every different kernel version for every distribution is a nightmare, and trying to keep up with an ever changing kernel interface is also a rough job. 

Simple, get your kernel driver into the main kernel tree (remember we are talking about GPL released drivers here, if your code doesn't fall under this category, good luck, you are on your own here, you leech .) If your driver is in the tree, and a kernel interface changes, it will be fixed up by the person who did the kernel change in the first place. This ensures that your driver is always buildable, and works over time, with very little effort on your part. 

The very good side affects of having your driver in the main kernel tree are:

[LIST]
[*]The quality of the driver will rise as the maintenance costs (to the original developer) will decrease. 
[*]Other developers will add features to your driver. 
[*]Other people will find and fix bugs in your driver. 
[*]Other people will find tuning opportunities in your driver. 
[*]Other people will update the driver for you when external interface changes require it. 
[*]**The driver automatically gets shipped in all Linux distributions** without having to ask the distros to add it.
[/LIST]
As Linux supports a larger number of different devices "out of the box" than any other operating system, and it supports these devices on more different processor architectures than any other operating system, this proven type of development model must be doing something right[/quote]
I repeat: Driver installation is not supposed to happen on Linux. If it does happen, blame the hardware manufacturer because he refuses to release sources and/or specs.

---

### Post by leef on 2008-09-18
disregard

---

### Post by karellen on 2008-09-18
> **bmac said:**
> Why this incessant need to defend Windows or Ubuntu? Pointing fingers at which system functions better on which drivers, only benefits those that argue. Defending Windows is useless on a Ubuntu forum, unless you intend is to recruit. I've used Windows since 3.1 and was in the SEM field for years working at component level. Integrating windows systems with electron microscopy technology. Never did I worry about a driver working - it either did or didn't. Now it appears that not only do we concern ourselves with hardware driver availability, but also which OS best utilizes said driver and argue over the benefits of each.

How does this help a new user? If a new user installs Ubuntu and requires a hardware driver that either is inferior or not available from the vendor, how does arguing over which OS is better, improve the new users situation? If the new user didn't investigate the OS prior to installation and confirm compatibility, how is that the responsibility of Ubuntu / Linux / Windows or any OS? Logic would suggest that prior to installing a new OS a review of system compatibility would be mandatory. Yet quite often on this forum a new user requests support for that very issue. Rather than arguing which OS is better or more user friendly, Why not write drivers and provide them to Ubuntu? Don't have time or knowledge then maybe aruging is fruitless - as it appears to take both. This oneupmanship is getting old in my opinion....

If an OS doesn't work for you or your system (and you don't wish to modify your system) - **Don't use it**. **How simple is that? At least you have a choice, if MS had it's way - you wouldn't...**

I don't understand when receiving the benefit of a free OS, some individuals can't refrain from complaining, bashing or comparing the OS. I didn't pay any money for Ubuntu and if I wasn't satisified I could have just thrown it away. I can't count how many things I've paid for (including Windows) that I've thrown away....:-k

so true :)
one big plus from me ;)

---

