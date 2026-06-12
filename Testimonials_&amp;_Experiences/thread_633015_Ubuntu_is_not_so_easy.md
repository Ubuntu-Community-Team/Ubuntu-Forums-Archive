---
title: "Ubuntu is not so easy"
date: 2007-12-06
forum: Testimonials &amp; Experiences
---

### Post by Mooseknuckle on 2007-12-06
Yes, another frustrated would-be-convert ...

After reading all these articles on Digg about how great Ubuntu is, and how it can do all the great things Windows can, and easier, I have to say this is honestly far from true.

I'm not whining.   I'm letting all the fanboys who think that Ubuntu is for the common man know why it isn't (at least in my case).

Keep in mind, I'm computer illiterate, but not afraid to learn.   When they say "Windows just works", here's what didn't "just work" for me in Ubuntu, and how I had to solve it:

1) First off, I have an Nvidia 8800 card, and Ubuntu didn't even pretend to know what it was.   When I started X, the system would just freeze.   No alt-f2 to get a shell or anything.   Reboot required.   How I fixed it:  I booted into singleuser mode and issed a terse wget command to download a runnable binary from Nvidia which ran me through the steps to create my X config file which would work.

2) I hooked up my 30" Dell monitor.   Again, as soon as X started, no dice.  Not even crappy graphics ... just blackness ... darkness.   How I fixed it: I manually edited my /etc/xorg.conf and added my new monitor's resolution.   

3) I plugged in my HP printer and the OS didn't see it.  How I fixed it:  I went to some site which has a crapload of linux hp drivers, and downloaded some RPM which allowed it to be recognized.   As soon as I changed the usb port to which it was connected, the printer was no longer recognized, and I had to move it back to the other port.  eww...

4) My mouse scroll wheel doesn't work.   I'm too tired to figure out why atm.

5) I tried to use compiz, which caused all of my window decorations to vanish, and I could no longer close open windows.   How I fixed it:  hit ctrl-alt-f2, logged in as root, blew away my user's home directory, recreated it, and rebooted.

6) Wireless... I installed a runofthemill netgear wireless card.   Of course, no wlan device was autodetected ...  I had a sinking suspicion this would be the case.  After about 4 hours of research, I learned that I needed to install ndis, and get the windows drivers off the CD that came with my card.   Well, my Netgear driver CD had no .INF, or .SYS files ... just some dll's... I googled around and eventually found a tarball with the files I needed.   Installing them was very arcane and mojo (modprobes and iwconfigs ... mumbojumbo).   

6b) Finally got wireless working after hardwiring into a network to download the appropriate packages and applications to wrapper up my windows drivers so that Linux could understand them.   Now, when my computer boots, wlan0 is detected, but the network is not connected.   I need to open a terminal window, run "exalt", and click on wlan0.   Then, I need to "disactivate" and "reactivate" wlan0, then his "apply" which runs for about 2 minutes and locks up my system.   When it's done, I MIGHT have network connectivity, but usually I have to repeat the above about 3-5 times before I get a network.   And if I leave the machine idle for more than 10 minutes, I have to do it all again.

6c) Exalt often crashes my machine, requiring a hard-reboot (no way to get a shell).


Other than all that, the interface is pretty slick.   ALL of the above things "just worked" in windows XP.   The HP printer, wireless card, NVidia card, 30" monitor, mouse scroll wheel... all of them.   Autodetected, and perfect.

I understand you get what you pay for, and a lot of selfless folks have worked tens of thousands of man hours to make Ubuntu what it is today, and I for one, sincerely applaud that, and appreciate it.

I give you these problems so that the developers can see for themselves what isn't working out of the box, and what is deterring would-be converts (like myself), and causing them to go back to windows, probably for good.

Goodbye, world.

PS ... I was using Gutsy

---

### Post by CameronCalver on 2007-12-06
Yeah it isnt as easy and everything doesnt work as it does in windows but after about a year of using and learning it . It is so easy now i can do everything i can do on windows but its FREE!! and thats a big one just try and get to no everything about the os first because you dont think when people started using windows for the first time if they had a problem they gave up becuase of cause WINDOWS  is the maker of the BLUE SCREEN!! :)

---

### Post by linuxlizard on 2007-12-06
ahhh- I don't know. To be fair I think you are looking at it the wrong way.

My experience with gutsy-

My nvidia card worked by just clicking and accepting when asked about it. My hp printer worked by just plugging it in, my monitor worked out of the box, etc. Compiz worked with a single click and bang there it was no problem.

For me it was easier than windows, which I run on another partition. My video card I had to install drivers from a cd in windows for example, and same for my printer. My printer drivers took a good 30 minutes to install and set up on xp, on ubuntu- like I said, I plugged it in and it was ready to go out of the box.

The problem as I see it, with your experience, is that you chose the wrong hardware. The same will happen if you try to hook mac hardware up  to your windows computer. If you want linux to go easily and smoothly, you need to use linux compatible hardware. The fact that you can tweak hardware like yours and get it to work is a bonus. 

The second problem is that you are expecting the user, rather than the manufacturer to install the os and set up all the hardware like the video card. If you had purchased a linux machine from a manufacturer with linux already installed and purchased compatible hardware like printer and wireless from such a manufacturer, you would have had none of the issues you bring up.

On the other hand, how many new windows users who have never touched windows before can install the os and set up the hardware for it?

Some, but not all- same can be said for linux.

I think what many users are saying is *using* the system once set up is easier than windows.

I don't think anyone is claiming that setting up any piece of random hardware out there someone may purchase without checking if it's linux compatible is as easy as windows.

I do, however think that for most hardware, most of the time, it is easier than windows to set up- like my printer and video card and monitor for example- no probs for me with anything. It set everything up smoothly, quickly, and automatically.

Installing software is as easy as a couple of clicks. Can't do that in windows.

---

### Post by wolfen69 on 2007-12-06
> **linuxlizard said:**
> 
On the other hand, how many new windows users who have never touched windows before can install the os and set up the hardware for it?



that is an excellent point. well said.

if people dont want to take the time to learn, then they should stick with a PC pre-installed with windows.

Oh, btw, windows doesn't "just work". if you've ever done a clean install of windows, you would know this. you need to install graphics drivers, sound drivers, codecs, anti-virus, anti-spyware, among other things. let's not forget about tweaking it to run good. if windows was that easy, i wouldnt be getting calls from people to fix their computers.

---

### Post by malangaman on 2007-12-06
It would be sensible to warn owners of certain hardware of possible trouble with Ubuntu install.

---

### Post by TameLion on 2007-12-06
I can imagine the meeting..

"Today, ladies and gentleman, you will test every single piece of hardware under the sun and write down how well it performs under the system you are volunteering to put together."

Will you be starting us off? :)

---

### Post by aysiu on 2007-12-06
> **malangaman said:**
> It would be sensible to warn owners of certain hardware of possible trouble with Ubuntu install.
And [that's what I try to do.](http://ubuntuforums.org/showthread.php?t=63315)

While I think the OPs point about letting the developers know is lame (i.e., the developers already know what the problems are, and they're doing the best they can... a little third-party support--the kind Microsoft has--couldn't hurt), the point about Ubuntu fanboys going on and on about how easy it is needs to be corrected.

New users should be given realistic expectations, not the impression that Ubuntu is some kind of dream OS that will solve all your problems.

So, to sum up...

**Good point**> **Mooseknuckle said:**
> 
After reading all these articles on Digg about how great Ubuntu is, and how it can do all the great things Windows can, and easier, I have to say this is honestly far from true.

I'm not whining.   I'm letting all the fanboys who think that Ubuntu is for the common man know why it isn't (at least in my case). **Bad point** > I give you these problems so that the developers can see for themselves what isn't working out of the box, and what is deterring would-be converts (like myself), and causing them to go back to windows, probably for good.

---

### Post by Nano Geek on 2007-12-06
> **Mooseknuckle said:**
> 
Other than all that, the interface is pretty slick.   ALL of the above things "just worked" in windows XP.   The HP printer, wireless card, NVidia card, 30" monitor, mouse scroll wheel... all of them.   Autodetected, and perfect.Perhaps that was because they were made to work with Windows, not Linux. Windows by its self, without any drivers from the manufactures detects less hardware than Linux does. Just be thankful that there are people out there coding a free operating system for you that, if it didn't exist, you would be paying $500 to Microsoft. 

But anyway, so long and good bye.

---

### Post by steveneddy on 2007-12-06
> **malangaman said:**
> It would be sensible to warn owners of certain hardware of possible trouble with Ubuntu install.

I thought that is what the linux compatible hardware websites were all about?

---

### Post by aysiu on 2007-12-06
> **steveneddy said:**
> I thought that is what the linux compatible hardware websites were all about?
Yeah, but most of the Dugg articles that hype up desktop Linux and Ubuntu do not usually link to those sites.

---

### Post by steveneddy on 2007-12-06
> **aysiu said:**
> Yeah, but most of the Dugg articles that hype up desktop Linux and Ubuntu do not usually link to those sites.

Yeah, you're correct. I wonder if we need to have a section, a sticky thread, about the most successful hardware that various versions of Ubuntu can be installed and run on with some links to various workarounds for hardware, Like ATI video, that seems to be so cumbersome for a novice Ubuntu user?

Just a thought.

But yeah, the Digg and other sites that promote latest/greatest with new software or hardware don't really get to the meat of the issue that not all hardware is going to work with Ubuntu, or other types of Linux for that matter, without a little user "persuasion", so to speak.

---

### Post by SunnyRabbiera on 2007-12-06
well granted Ubuntu is not the easiest one out there, heck I know a good number of distros out there that are far easier

---

### Post by steveneddy on 2007-12-06
> **SunnyRabbiera said:**
> well granted Ubuntu is not the easiest one out there, heck I know a good number of distros out there that are far easier

To be honest, I have never had a problem with Ubuntu, but then again I run middle of the road generic hardware. I don't have any odd or Compaq stuff around my house, so Linux runs and sets up well of this type of hardware.

:popcorn:

---

### Post by lespaul_rentals on 2007-12-06
I seriously think that Digg is responsible for a lot of the noobs that come around and are unwilling to learn how to run Linux.  I'm sorry the threadstarter didn't find what he was looking for, but to be quite honest he most likely would never have pre-assumed the way he did if it wasn't for the "land of milk and honey" that Ubuntu was portrayed to be.  It seems that scores of "UBUNTU ROCKS SWITCH NOW" articles spring up, all thanks to anti-Linux trolls who **know** that if massive amounts of technology-challenged noobs switch to Linux, bad press will be generated.  If Grandma is getting tired of her slow Windows 98 computer and reads about this "program" that will make it work perfectly, well, Grandma's going to be disappointed.  The more people who switch to Linux, the more negative reviews we will get, obviously.  However, Digg appeals to noobs and psuedo-nerds, and if we are getting large amounts of new users through that site, the proportion of negativity will rise.  Just something to think about.

Sorry you didn't have a good time, but Linux is **not** guaranteed to fit your needs.  Sometimes Linux just isn't the glove for your hand, perhaps because of hardware, software, or time.  You could always try a different distro (OpenSuSE perhaps) but to be honest, Windows sounds like it will be what you are looking for.

---

### Post by Mooseknuckle on 2007-12-06
I understand that my hardware may not be "supported", but I think that my hardware is pretty darn "common":

Netgear WG511 PCI wireless card
Dell WFP 30" Monitor
Nvidia 8800 GTX
Microsoft 3 button mouse
HP 4P printer

It's not just that these components dont properly function I guess, but what was most frustrating to me is how the OS happens to dump you into oblivion when one or more of these components isn't recognized.

Why is it that the ubuntu installer can recognize my video card, and guide me through the install process, but X cant?   It would be nice if when I booted up, X would detect that it doesn't recognize my card, but put me into some default resolution instead, and perhaps suggest that I "click here" to get the latest nvidia drivers.    The system knows that I have an nvidia card, because if i do an 'lspci', it's detected.

Similarly with the monitor... The boot sequence can display text and such, it's just that when X started, the computer decided to grind to a halt.   If it indeed could not render a graphical desktop environment, at least giving me the option to stay at a console prompt, and tell met that my resolution isn't recognized, and perhaps I might need to add it to the /etc/X11/xorg.conf would have been a helpful hint.

The components not working to their full capicity is one thing, but halting the system, and leaving the user in the dark is something else.   I know that if the system tried to catch each and every hardware edge-case that could arise and "suggest" a solution to the user would be nearly impossible, and potentially annoying.   But opting to halt the system seems a bit extreme.

I mean if they could add 1900X1200 to my resolution in the xorg.conf, why not just stick 2560X1600 in there while they're at it?   Seems like a REALLY simple solution to a debilitating problem.   I mean really, that's all it took for me to fix the problem ...

---

### Post by Geekkit on 2007-12-06
> **wolfen69 said:**
> Oh, btw, windows doesn't "just work".

And to prove this point, here's an e-mail from our IT department concerning the installation of fonts under XP:

[INDENT]   1. You may need to reboot Windows before these TrueType fonts will work properly in all applications. This is usually required if an application or a printing process was started before the font was installed. This is a common issue with Crystal Reports, Crystal Application Servers and Microsoft Office Applications.
   2. Very rarely Windows will not recognize these fonts at all (even after a reboot). To correct this you will need to refresh the fonts in Windows Control Panel:

            select Start
            select Control Panel
            open Fonts
            - simply opening the folder triggers a re-register of the font. [/INDENT]

How many people are going to know about this and how many people are going to know how to do this? I don't ever remember this sort of thing happening in Linux/Ubuntu.

My point is that there are always problems. It's just that with commercial software the problems are harder to swallow because you've paid for something and it doesn't work. Ubuntu/Linux is free and so if it even half works you've gotten something out of it. :)

---

### Post by lespaul_rentals on 2007-12-06
Like I said, Ubuntu isn't for everyone.  Try OpenSuSE 10.3 and see how it works for you.  If it doesn't, fine, go back to Windows.  If it does, cool, you just found yourself a distro.

---

### Post by aysiu on 2007-12-06
> **Mooseknuckle said:**
> 
It's not just that these components dont properly function I guess, but what was most frustrating to me is how the OS happens to dump you into oblivion when one or more of these components isn't recognized. I know you're talking about your Ubuntu experience, but that sentence could very well describe my Windows experience.

The few times I've had to install Windows from scratch (not a restore disk from the OEM), it's been a nightmare, and all I'm left with are a bunch of yellow question marks that give me no indication of what driver to look for.

With Ubuntu, on my desktop, I installed it, went to Restricted Drivers Manager, clicked the box next to Nvidia, and that was it.

With Ubuntu, on my laptop, I installed it, and everything worked perfectly out of the box.

I'm not saying my experience is typical, but yours isn't either.

---

### Post by Zipster90 on 2007-12-06
Everything "just worked" for me as well in Ubuntu. I did have one problem with the wireless, but a quick and painless install of Wicd fixed it. I am running on a laptop, mind you, but whenever I switched I was blown away by how *little* I was required to do. 

Oh, and has anyone else noticed that the threadstarter hasn't even replied yet? Smells like just another troll.

---

### Post by Irihapeti on 2007-12-06
Aysiu, it doesn't only apply to installing windows from scratch. 

My son bought a laptop with Vista preinstalled. When he started getting the online updates, all hell broke loose. Here's part of an email I received. I've edited it to comply with the family-friendliness of these forums :)

> I'm so tired of this computer business.

Now it only starts the first time after starting in Safe Mode.

Who the #$%%^ do these people think they are to release an operating system that doesn't operate? I have tried everything and now I'm stuck with a lame duck which I can never shut down without wondering whether it will restart or not, and then have to pull the plug on and unclip the battery.

Half the time it sits in welcome screen, and other half goes to blue screen. Have uninstalled updates, done every S&*(&*(^ thing under the sun, and now for sure my warranty's screwed because they'll say I've made too many changes and I'll have to spend more to go buy vista new because finding drivers for XP is a $@jrj nightmare ...

He did eventually get things more or less sorted, (without having to buy another copy of Vista!) but not completely. He laughs at it now, but it was no fun at the time.

---

### Post by aysiu on 2007-12-06
> **Zipster90 said:**
> 
Oh, and has anyone else noticed that the threadstarter hasn't even replied yet? Smells like just another troll. It's been only 11 hours.

---

### Post by Nano Geek on 2007-12-06
> **aysiu said:**
> It's been only 11 hours.And he's been here since March. Seems like a long time to wait just to troll.

---

### Post by aysiu on 2007-12-06
> **asjdfwejqrfjcvm msz34rq33 said:**
> And he's been here since March. Seems like a long time to wait just to troll.
The OP has posted three threads since March.

I don't see what being here since March has to do with the topic at hand. There are plenty of people who have been here longer than nine months who do not post in the forums every 11 hours. Sometimes people wait a day or even a week to follow up on a post.

---

### Post by Nano Geek on 2007-12-06
> **aysiu said:**
> The OP has posted three threads since March.

I don't see what being here since March has to do with the topic at hand. There are plenty of people who have been here longer than nine months who do not post in the forums every 11 hours. Sometimes people wait a day or even a week to follow up on a post.I know, I was just trying to show that nine months would be a long time to wait if you only wanted to troll, which I don't think he does.

---

### Post by Mooseknuckle on 2007-12-06
If you read back to the 2nd page, you'd see that I've already replied to this thread.

I dont think anything in my original observation smacked of trolliness.

This forum is for testimonials and experiences, and I thought I gave a pretty accurate descriptions of the obstacles I had encountered trying to get Ubuntu to work.

Nice to know that the folks who hang out here are realistic in their attitude about the OS.    I truly hope the new user experience continues to get easier.

---

### Post by aysiu on 2007-12-06
> **Mooseknuckle said:**
> If you read back to the 2nd page, you'd see that I've already replied to this thread.

I dont think anything in my original observation smacked of trolliness.

This forum is for testimonials and experiences, and I thought I gave a pretty accurate descriptions of the obstacles I had encountered trying to get Ubuntu to work.

Nice to know that the folks who hang out here are realistic in their attitude about the OS.    I truly hope the new user experience continues to get easier.
You did, in fact, respond, but even if you hadn't, I don't see why a lack of response in 11 hours would make you a troll.

Your experiences are valid, and they are your experiences.

Your point about people overhyping Ubuntu is also valid.

But I think the developers already know what works and doesn't work, and they are already working on what they can do. Unfortunately, reverse engineering a driver takes a bit more development and testing than having a driver provided for you by the hardware manufacturer.

---

### Post by karellen on 2007-12-07
> **asjdfwejqrfjcvm msz34rq33 said:**
> Perhaps that was because they were made to work with Windows, not Linux. Windows by its self, without any drivers from the manufactures detects less hardware than Linux does. Just be thankful that there are people out there coding a free operating system for you that, if it didn't exist, you would be paying $500 to Microsoft. 

But anyway, so long and good bye.

not that much, exaggeration is not such a wise thing to do. windows xp professional costs $299 and windows vista home premium $239

---

### Post by jbrevik on 2007-12-07
Windows != Linux

---

### Post by abstractcoder on 2007-12-07
To the author,

Compatibility is very important! Also, you didn't really expect to just pop in the cd and everything be done for you, did you?  You must take the time to configure your system.  That is the great thing about Linux, it's very hands-on, you can do anything you want with it (Unlike windows)

I have used Windows all of my life, and learning/setting up Ubuntu wasn't that hard. It's all about putting in the effort into solving the problems that arise.   The pros outweigh the cons(are there any cons? :P) 

Each system may respond differently, I have one computer which freezes before I can even install linux, compatibility!  

Personally, I would suggest reading more about Ubuntu, that way you can get past the problems that you've had/or are having. 

I absolutely love Ubuntu,  just read more!

---

### Post by bartos on 2007-12-07
The thing I have learnt about linux is it is a learning experiance.My first one was Desktop 10 and then back to windows until I found Mepis.With Mepis on my laptop , I had to dual boot so when I researched commands I needed i could just copy and paste them ina text file to read on Mepis .(was getting ndis wrapper setup and installing a windows driver).

That is the way I gradually made my way into linux full time with Ubuntu. There still is a Xp partition on my machine but is not accessed very often. 

My point is to try to dual boot and work on your linux install when you have time. When your linux is running proper, you will have learnt alot and will be proud that the time you put in paid off.

I have hardware that most poeple complain about and Ubuntu works great with it.:)

Good luck to you.

---

### Post by misfitpierce on 2007-12-07
I actually picked up linux faster than windows... People are different.

---

### Post by kelvin spratt on 2007-12-07
I think its more to do with mental attitude, people get used to their comfort zone. when they try something new and come across a problem they panic and madly click everything in sight. After totally nuking everything the Famous words come out, Linux is no harder than Windows, In that it uses the logical approach once you program your brain to think its simple.

---

### Post by de_valentin on 2007-12-07
I think this page should be more prominent on the livecd, it confronts everyone with the possibility that not everything 'just works'. 

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

It would save alot of questions later, and people would not try linux knowing some parts of their hardware configuration don't play well with linux. 
That would then again stop people from trying linux and 1 week later run back to windows and shout out how stupid ubuntu is and how nothing works etc. In short it would save the community a lot of bad publicity.

This year I assembled my new pc, and the hardware list was a great help I don't think I could have done it that easy without it, which of course would've helped the OP.

Of course I know that it's worse not to be talked about at all, but there is more bad publicity going round than good publicity, allthough it appears to be changing slightly lately, thank you Vista.

---

### Post by exactopposite on 2007-12-07
i think people forget that they had to learn how to use windows.

---

### Post by moe_syzlak on 2007-12-07
Have any of you Ubuntu/Kubuntu users tried using professional support, like the ones advertised on the main Ubuntu site. I think that Linux users, especially desktop users, should get professional support for their Linux OS.

Linux on servers is reaping all the benefits of using Linux, as they have admins who went to college to wrangle the Linux peculiarities and technicalities into submission. Desktop users on the other hand... not so much.

Some open source and Linux users don't care about open source or Linux. They just want software that they don't have to pay for. They want open source software (OSS) as in beer, and not OSS as in free speech (the ability to modify your stuff to a REASONABLE extent). Look at this resource for what open source software is: [http://en.wikipedia.org/wiki/Open_source](http://en.wikipedia.org/wiki/Open_source)


Maybe if we would show companies (Adobe, game companies like Bungie, device makers, peripheral makers) that there is a market on Linux. Then actually they will start making products for Linux.


Until we (as Linux desktop users) can show companies that they can market products to the Linux desktop segment, Linux will continue to be the red headed step child of the desktop operating system market.


What does all this mean? It means that we will have printers that only work 60% with Linux. It means that the majority of mp3 players out there will not work properly. It means that the legality of audio (mp3, aac) and video (wmv, mov, rm) codecs on Linux, except for Mandriva as they ask the mp3 patent holders to put mp3 codecs in the Mandriva distro, is shady business. Canonical does not ship Ubuntu with the ability to play mp3's, wmv's, or even mpg's; since, it would cost Canonical more money to produce Ubuntu due to licensing fees. In effect, Ubuntu gets around this by shirking the patent violation responsibility on the users of Ubuntu.


Yes, we are elite geeks that eventually get these to work at varying degrees, in addition we get our n00b padwons to master the task of hacking Linux to get their graphics cards, printers, iPods, and other device working properly with Linux. It is fun to hack sometimes. However, this hacking and trying to get things to work properly in Linux takes a big bite out of your productivity. But, wouldn't it be nice to not have to hack these devices and peripherals or to be neglected by the companies that produce them and just have them work 100% out of the box with your favorite distribution. It can. If manufacturers believe that they can make a PROFIT by selling stuff to Linux users. Bottom line, we Linux users want to get work done using Linux in a fast manner and efficiently.

Tell Mark Shuttleworth to start peddling Linux to the corporate bigwigs. And maybe one day, our Linux will not be discriminated against by companies who think the Linux desktop is only for people in third world countries, poor people, and cheapskates. While, the truth is that Linux is faster, more stable, and inherently more secure than the MS Windows operating systems.


In conclusion, Linux users should get support from a professional company that supports Linux. The type of support that costs you about $100 per year. Because 70% of the time on Linux help forums, the blind is leading the blind. Somehow, they get to their destination.

---

### Post by immrlizard on 2007-12-10
I must be one of the lucky ones then.   I haven't had much of any type of trouble installing Ubuntu.   I did have a bit of trouble with my ATI card and it has since got better support every new version.    I can't complain though.   It isn't perfect in windows either

I have installed it on a couple different machines and have only had minor problems.   This is one of the reasons my Linux troubleshooting abilities are so low.   I am sure that I will eventually get some hardware that it doesn't like at all.   Over all, I really enjoy Linux to this point.   I will have to see if it continues this weekend.   I am going to get myself an mp3 player.   It is listed as one that works without a problem.   Fingers crossed.

---

### Post by azimuth on 2007-12-10
> **immrlizard said:**
>   I am going to get myself an mp3 player.   It is listed as one that works without a problem.   Fingers crossed.

I hope it is one that supports OGG files also. Always nice to buy from folks who recognize there is an open source market.

---

### Post by movrshakr on 2007-12-18
From earlier:[B]

"It is fun to hack sometimes. However, this hacking and trying to get things to work properly in Linux takes a big bite out of your productivity."[/B]

And that nails it.  There are Soooooo many posts around by people touting how great and easy ubuntu is.  And it pretty much is easy from start through having a desktop screen on your monitor.  But from there on, not so much.

Sharing directories on a network, connecting to shared directories on a network, sharing existing printers on a network, connecting to existing printers on a network, using network printers (not shared off a machine)...things such as these are common even in home environments now.  Maybe I am the lone problem attractor, but NONE of these functions have been easy.  They have required hours and hours of work and web research and forum posting and command line interaction, etc.  No way I will call my last week with ubuntu easy.

---

### Post by David Ostrom on 2007-12-18
Man!! Looks like you got a crash course and now you want to give it up? You are well on your way to understanding Linux more than I. Once you get all the hardware issues ironed out, it shouldn't be   
too hard for you. Just don't give up, it gets easier.

---

### Post by Wazeem on 2007-12-19
> **David Ostrom said:**
> Man!! Looks like you got a crash course and now you want to give it up? You are well on your way to understanding Linux more than I. Once you get all the hardware issues ironed out, it shouldn't be   
too hard for you. Just don't give up, it gets easier.

I think this is really true.

I had problems with ubuntu too and thought the OS was really hard. However now that I am over those probs I saw how easy ubuntu is to use. Its hard to explain, but it really is easier to use that other OS's (imo).

Now if i had not had the problems i did i prolly would have not understood the OS and would have stumbled on every task but due to learning the stuff to set it up I guess it was useful in the end.

---

### Post by Nebutron on 2007-12-19
Yea,

I had a couple of issues with ubuntu at first.  Couldn't play DVD's without a hack.  Also had trouble getting WIFI to work.  However, I went into it knowing there would be a learning curve.  I'm an old guy (47).  Didn't grow up with computers.  Took me 15 years of using windows to know it like I do.  To put some perspective on the experience, I have been using Ubuntu for a little over two months and have becoming quite comfortable with it.  Now I am looking forward to never having to buy an OS again.  Also love the fact that when my motherboard craps out, I will not have to go through the hassle of trying to get Microsoft to issue me a new product key.  Been down that road a couple of times now.  

Linux is far from perfect.  But it appears to me that it has come a long way.  I agree that some of the hype can leave a person with the wrong impression.  I also believe that people make these glowing posts because they are truely loving the experience, despite the existing issues.  To me it has been like a video game with so many levels to achieve.  I look forward to the next discovery of what it can do and what tweak I can play with.  

Advise from the old guy:  If you are looking to get into Linux, be patient with the process.  Expect some challenges.  For most, the challenges will not be too large.  Then have fun!!

---

