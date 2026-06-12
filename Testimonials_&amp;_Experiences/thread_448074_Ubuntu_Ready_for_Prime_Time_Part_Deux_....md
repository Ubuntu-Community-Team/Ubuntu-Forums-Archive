---
title: "Ubuntu Ready for Prime Time Part Deux ..."
date: 2007-05-18
forum: Testimonials &amp; Experiences
---

### Post by Geekkit on 2007-05-18
If you recall I had posted my experience with 6.10 and some of the problems I encountered:

[http://ubuntuforums.org/showthread.php?t=410395&highlight=geekkit](http://ubuntuforums.org/showthread.php?t=410395&highlight=geekkit)

Yesterday I stuck 7.04 on my work computer. I'm not sure that this is a reasonable comparison to make since we are talking about two different versions of Ubuntu with two very different pieces of hardware (my work machine is a local company brand called Seanix).

The install actually took less time than did burning the ISO image. Cool. No hang on start up, no crashy crashy with Synaptic, Compiz/Beryl didn't lock up, X didn't refuse to work, hell I even hooked up my Nokia phone via USB and used two applications:

[LIST]
[*]Waamu
[*]Gnome Phone Manager
[/LIST]

And? And I sent SMS messages from my keyboard and Ubuntu. Waamu saw the phone, connected to it and allowed me to see my phone book, inbox, outbox, contacts, on my phone. It didn't see memory card, or images but hey, the phone is quite new (the 6126 just came out in December).

It's weird because I've been lurking and seeing a lot of people with problems with 7.04 and saying it's not stable and yet I've seen more stability with 7.04 than I did with 6.10. Weird. Either way, I'm happy, I've said goodbye to Novell (*shudder*), goodbye to XP (*applause*) and don't have to fumble with MSYS on Windows - sorry but it really didn't work out for me, although MinGW worked quite well.

Either way, cheers and I guess I can now say it works

:P

---

### Post by Kobalt on 2007-05-20
I also believe that 7.04 is a good and quite stable release. I guess a lot of problems are due to the increased number of people wanting such things as Compiz/Beryl. They inherit a lot of bugs from that.[I]

La vie est belle[/I] in Ubuntu ! :)

---

### Post by Geekkit on 2007-05-21
> **Kobalt said:**
> I also believe that 7.04 is a good and quite stable release. I guess a lot of problems are due to the increased number of people wanting such things as Compiz/Beryl. They inherit a lot of bugs from that.[I]

La vie est belle[/I] in Ubuntu ! :)

I'm not just talking about Beryl and/or Compiz, I'm talking about Synaptic no longer crapping out and the add remove programs telling me I can't install something because of some dependency (followed by some cryptic message).

EDIT: I also like how the Ubuntu team placed a very high priority on X being something that doesn't crap out. Somewhere there is a feature request/bug related item, that suggested that X should always be able to come up. Stability seems to be a very important part of this release. I think this is going to be what brings all the non techie types over to the Linux/Ubuntu world.

Personally I really don't need Beryl - I suspect no one really does. It's eye candy. It's neat to look at but it surely wouldn't sway my decision to pursue this distro or Linux in general. What I have always wanted is something that is stable and capable of replacing my Microsoft Windows solution. I haven't installed my development tools but unless they broke something those too should work. Actually, Netbeans and JDK 1.6 had been a no brainer last time so I can't see them being a problem now.

I still have to set up my home machine (the original machine that had all the problems). I'm also going to have a go at Fedora which I guess is hitting a big milestone this month. I'm still quite partial to Ubuntu since it's so darn easy to set up.

:D

---

### Post by Steve_Karl on 2007-11-18
First: this is not a troll post. I'm just being honest with my opinion.

I've been working with Windows since Win 95. Windows Networking since early Win 98 and setting up and maintaining small windows networks for home and small business for over 6 years and making a decent living at it.

I think ubuntu is a great os for many reasons but there are 2 things that makes it not ready form prime time in my opinion and will stop me from recommending it to clients.

First: Networking is NOT consistent or predictable.
As an example, the first time I installed 7.04 on it's own dedicated box ( no dual boot ) everything worked fine. Easy access to my windows work group no permission issues at all. No need to even know what Samba was. In fact ... I'd never heard of samba until the third time I installed 7.04.

Install # 2 and # 3 were ( I as were because # 2 was wiped yesterday and # 3 is scheduled for a visit from my DELPART floppy as soon as I finish this post ... ) on a dual boot with XP.

I followed a few tutorials. I did all of the recommended changes with the samba setup. Still .... no access to my windows workgroup.
Contents of folder can't be seen.

I see the work group, at times I've even seen the ubuntu machine inside of the windows workgroup allong with windows XP machines.

Still ... no access. And Too much work with no results.

Second: Install # 2 and # 3 fdisk/mbr lets xp just boot without grub getting in the way, but both times the partitions are still hosed.

Partition magic can read them.

Well .... DELPART from a floppy and reload a drive image and that's it.

This could be soooooooooo freakin' good. With some minor changes.
This could take over the world with some minor changes.
I'd have 1/2 of my mom and pop clients running ths and loving it ...
...but I can't in clear conscience recommend something that is:
1) going to be an incredible PIA to network and...
2) gonna hose the XP partition if it's a dual boot.

It's simply not ethical for me to recommend a free OS that will cost the client more is support fees that it would cost them to buy Win XP from eBay on the local Best Buy.

Hopefully the developers will realize how easy it would be to make this a prime time offering to the whole world ... and at a time ( Vista Hell ) when the public is begging and pleading for an alternative to over the top stupid annoying crap as being the only "obvious" alternative.

Ubuntu is sitting on the edge of a golden opportunity to do the world a great service, but it won't happen if it's too difficult to use.





..............................................

Running DELPART
Deleting all partitions

I'll check back in 6 months and see if there's been any changes.

Steve

---

### Post by erlyrisa on 2007-11-19
> **Steve_Karl said:**
> First: this is not a troll post. I'm just being honest with my opinion.

I've been working with Windows since Win 95. Windows Networking since early Win 98 and setting up and maintaining small windows networks for home and small business for over 6 years and making a decent living at it.

I think u.........................

.......................
I'll check back in 6 months and see if there's been any changes.

Steve


Hmm I have the same problem trying to convince people to use linux --> you see you wouldn't have a network problem if everyone on the network was a Penguin PC. - Linux has to comprimise, and give in to "the masses" and try and compatibilise. -hence samba -> reverse engineered from microsoft (I think it was technically illegal according to MS, but hey -what are they gonna do).

...funny thing today is

.remmeber how Apple macs were the devils computers? -but now with  the Dock, and it's underlying architecture (NeXTSTEP/UNIX), it's the bees knees, if anything, Linux , and particularly Ubuntu is like the 'Fresh OSX' -> just with a slightly higher learning curve.

The Problem/Advantage With Linux -> it's never finished/it's too finished.
Sometimes a programmer will just finish with a really good CLI based program, that only the avid nerd will ever use, other times a project trying to mimck some functionality never works.

I have noticed a pattern with the linux community on what gets done properly and what not... when it's something New and advanced it'll work like a charm ->> but it's usually only intended for the professors... when it's something that is being copied, eg. SodiPodi, it's never finished.

(In every proffesional programmers, heart beats the mind of an econimist -don't like SodiPodi? -hell buy CorelDraw and fund my existance, when you start paying for SodiPodi - > I'll finish it.)

---

### Post by stinger30au on 2007-11-19
> **Steve_Karl said:**
> 

Hopefully the developers will realize how easy it would be to make this a prime time offering to the whole world ... and at a time ( Vista Hell ) when the public is begging and pleading for an alternative to over the top stupid annoying crap as being the only "obvious" alternative.

Ubuntu is sitting on the edge of a golden opportunity to do the world a great service, but it won't happen if it's too difficult to use.




I think you will find the developers know this. Ubuntu has come a long way since its inception. I think it is very close to being a world beater. hang in there

---

### Post by Steve_Karl on 2007-11-19
> **stinger30au said:**
> I think you will find the developers know this. Ubuntu has come a long way since its inception. I think it is very close to being a world beater. hang in there

I'll definitely be watching and will always have a few Ubuntu Live CDs in my case when I go out on the road.
It is really an amazing package and I do love it.

It has helped me recover files from drives that were seemingly dead when using Windows to try to get into them.

I just wish I had the time to really get to the bottom of the networking issues.

Steve

---

### Post by msimon1960 on 2007-11-19
I agree with the networking sentiments...

Never could get SAMBA to function -- seems an essential step to be able to network a Windows desktop.

Hardware problems will always be there -- someone is always going to try and hook up some piece of junk and expect it to work.

What's crucial is the basic functionality -- if you can't link two computers together quickly and easily then Linux will never be more than a novelty act for disaffected Microsoft users.

Fast, easy networking -- Priority One.

Matt.

---

### Post by Geekkit on 2007-11-19
Wiow,

This thread I started back in May is still going O_o

As usual, my standard disclaimer applies ... The opinions expressed here are simply that ... my opinions. Remember, opinions are like belly buttons: everyone has one. This is mine ...

Anyways. not quite been six months yet but I'm still using Ubuntu 7.04 both at work as well as at home. I'm able to be productive to the same level I was productive using Windows ... at least for what it is that I have to do which teach IT/Comp Sci, write, create presentation slides, print out course material, write code, write code, write code, and play the odd game (Nexuiz is bloody addictive!!!)

Things I love about Ubuntu/Linux/Gnome/Nautilus/Metacity:
[LIST]
[*]I love Open Office
[*]I love Nautilus
[*]I love Netbeans 5.5 and even love Netbeans 6 despite 6 being a pig on memory (it's a little excessive sitting at 370 MB with NO file opened O_o )
[*]I love Eclipse (both Eclipse and Netbeans are great for Web apps, and XML including XML Schema)
[*]I love the high degree of configurability (custom transparent PNG panels, funky window borders, scalable icons, interesting sounds, change to different fonts, change font rendering, change the menu, change the panels, change where the panels show up, change what panels display what, change Nautilus to look like Windows explorer, and of course: Gnome-look.org)
[*]I love the huge stock piles of developer apps ... if you can't find a developer app that suites your needs, you got problems buddy!
[*]I love, and I mean I LOVE apt-get ... apt-get install new_dishwasher ...blah blah ... Nothing remotely similar to this in Windows
[*]Playing media (Shoutcast and Groove Salad, play DVDs, MP3s, etc.)
[*]Qtpfsgui for doing wild funky HDR images: this really got me into doing some interesting HDR images with such ease
[*]Rhythmbox. I know a lot of people seem to want more but for me Rhythmbox is more than I need, I love it.
[*]The plugin for making MP3s play when you mouse over them in Nautilus
[*]How Nautilus (or which ever process it is) knows what a file is by checking the header and "guessing" without a file extension and then rendering the proper icon.
[*]No viri, no worries concerning spyware/malware, or some ridiculous process called GrooveMonitor.exe. I mean come on, and that baby blue UI? I'm talking about M$ Office 2007 in case you haven't guessed.
[*]Ease of use like I plug my SLR camera in, it's recognized by an app that wants to know if I want to download, print, view, save, etc. files. Ubuntu does the same with my Wife's camera, I can access my phone (mentioned in original post), printers print (both local and network printers), speakers work, USB headphones work better than XP (I just plug them in, choose them as the default sound device renderer, pause Rhythmbox, then play and I'm listening to music via the USB headphones ... absolutely NO drivers required ... Just found this out yesterday)
[*]And of course ... this forum!
[/LIST]

Problems I still have:

[LIST]
[*]NVidia driver is buggy. I'm not laying blame on anyone at this point, I'm simply pointing out the "what" part. Nexuiz is the only game that doesn't lock up the kernel and cause me to hit the restart button. Quake 3, Urban Terror, Open Arena and even OpenGL screen savers kill Ubuntu. I suppose a micro kernel-ish architecture is actually worth something, but I digress.
[*]GIMP still insists on 42 different windows on the screen. Please oh please GIMP developers, only ONE window with dialogs and for god's sake man, don't put all those dialogs into the panels ... that's just silly
[*]To access my phone's memory card I had to diddle the fstab file ... not necessarily hard but was a little bit of a pain to figure out how to do this
[*]I like Nautilus but there are bugs (sometimes the tree doesn't expand when you click on an icon on the right side. I want Nautilus to have icons that can move to arbitrary positions like on Windows and Mac. I know, these are small things but to me they matter.
[*]NLE apps are all broken. I know, I know there's this, there's that. Trust me, I've spent weeks upon weeks looking at all of them, compiling the latest of every one of them via SVN and all the countless hours spent fixing dependencies to make them compile and then run - or not. None work without crashing and none offer an intuitive interface. I've looked at: KDEnlive, Open Movie Editor, Kino, LIVES, Avidemux, Cinelerra, and Jahshaka. The closest to something that worked was KDEnlive which crashed if you looked at it wrong and when I imported a 20 minute 400 MB file in, when I used the razor tool it would slice at a completely different point on the video. That bug was listed on the KDEnlive site as "not critical" which was ... amusing. Either way, nothing for editing out there. Hell, I was even considering buying a package but when I realized that the only commercial NLE video editing package had gone the way of the Dodo (Main Actor), I was disheartened. Video on Linux is borked and I would actually pay for software at this point to do NLE.
[*]Common accounting packages not available under Linux (e.g., Simply Accounting, ACCPAC, Quickbooks). They do not work under WINE at all. Period.
[/LIST]

All in all, I'm still using 7.04 and like I always do, I wait for a few months for the dust to settle before jumping into a new release (7.10 can wait). I'm not a zealot but I do recommend Ubuntu to my students and colleagues (as I have been) to those that are tired of Windows. I am seeing more and more people/students either reverting back to XP, buying a Mac, or choosing Ubuntu as their OS of choice. This year I have seen more and more of this than at any other point in the last 15 years I've been playing with computers. Okay, it's not like half or anything (probably not even 10%) but 5 years ago suggesting that Windows wasn't a great choice would be followed with ridicule. Now, many are actually agreeing that Vista is a mistake.

Ubuntu not perfect, it's a WIP, there are some rough edges, and sometimes Ubuntu is frustrating. But then again, so is Windows. Ubuntu just annoys me less than anything else out there for now.

Anyways, that's it for me. I have work to do.

:P

Edit:

More things that I like:
- the character map applet is under the accessories menu not the stupid administration tools menu like in windows which is such a silly place to put it
- small memory footprint
- fast to shut down

---

### Post by Steve_Karl on 2007-11-22
> **erlyrisa said:**
> 


(In every proffesional programmers, heart beats the mind of an econimist -don't like SodiPodi? -hell buy CorelDraw and fund my existance, when you start paying for SodiPodi - > I'll finish it.)

I wonder if anyone has ever considered a donation fund that is aimed at specific tasks to fix / finish.
I would donate to get the networkng solved and I know I wouldn't be the only one based on how many people have seemingly given up on it.

---

