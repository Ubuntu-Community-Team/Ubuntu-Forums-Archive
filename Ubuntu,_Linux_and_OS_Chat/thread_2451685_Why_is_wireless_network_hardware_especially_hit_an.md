---
title: "Why is wireless network hardware especially hit and miss with Linux?"
date: 2020-10-09
forum: Ubuntu, Linux and OS Chat
---

### Post by jcdenton1995 on 2020-10-09
As per the title, I'm just curious as to why a particular type of device is especially poorly supported compared to others?

---

### Post by slickymaster on 2020-10-09
Not a support thread.

*Thread moved to ****Ubuntu, Linux and OS Chat****.*

---

### Post by grahammechanical on 2020-10-09
If Linux distributions had a monopoly on desktop and laptop computers then hardware manufacturers would be falling over themselves to provide Linux drivers for their hardware. In reality, it is Microsoft Windows that has an almost monopoly and it is that operating system the manufacturers provide drivers for. If they did not then their hardware would not be purchased for installation in computers.

With a some exceptions most Linux drivers are written by Linux developers without cooperation of the manufacturers who do not wish to reveal details of their intellectual property.

Linux is based on the concept of Free and Open Source Software (FOSS) but there is another concept that business people have even greater difficulty accepting. It is Open Source Hardware (OSH) along with open documentation about their hardware. Without documentation open source community developers will have great difficulty in creating drivers.

Another factor to consider is the rapid advance of technology. By the time community developers create a driver for a particular device it might already be replaced by an improved version. Why spend time and effort producing a driver for a device that is not a mass market product?

[https://en.wikipedia.org/wiki/Open-source_hardware](https://en.wikipedia.org/wiki/Open-source_hardware)

Regards

---

### Post by CatKiller on 2020-10-10
> **grahammechanical said:**
> With a some exceptions most Linux drivers are written by Linux developers without cooperation of the manufacturers who do not wish to reveal details of their intellectual property.

The notable exception in this case being Intel.

The few other companies that make WiFi chips (Qualcomm, Broadcom, Realtek, Killer as was) a Linux, but we sometimes get a chip that benefits from Android work, which they *are* interested in.

---

### Post by TheFu on 2020-10-10
> **jcdenton1995 said:**
> As per the title, I'm just curious as to why a particular type of device is especially poorly supported compared to others?

Blame the vendors for their lack of support.  The only solution is for more people to use Linux on their computers so a significant number gets the attention of the vendor.  For a long time, HP was the best vendor for Unix printer support.  Today, Intel is the best vendor for Linux network cards.  We still have problems with others and quality control around drivers has been an issue not just for others, but for the 2 large guys - Intel and Realtek.

---

### Post by Tadaen_Sylvermane on 2020-10-10
I think in addition they are constantly changing and making new abilities requiring new drivers for wifi. For all intents and purposes I'd say ethernet has been static for a decade or two. Hence the consistency. Wifi things change every chip. Nothing is the same, so drivers always different. Can't keep up with all of them.

---

### Post by mastablasta on 2020-10-12
> **Tadaen_Sylvermane said:**
> I think in addition they are constantly changing and making new abilities requiring new drivers for wifi. For all intents and purposes I'd say ethernet has been static for a decade or two. Hence the consistency. Wifi things change every chip. Nothing is the same, so drivers always different. Can't keep up with all of them.

this is it. so many changes. even within the same letter models there can be a change in chip (which to me is understandable) that breaks compatibility with the old chip and needs new driver (this i do not understand). for desktop chips, they first make drivers for windows (otherwise they can't sell it), then linux and then it takes a year or 2 years for the driver to get in the kernel and to distributions that use older kernel (if ever).

what i don't understand is with the flood of the *new* chips what actually makes them better? it seems to me they have about the same speed and reliability. so why make (so many) new models.

---

### Post by jcdenton1995 on 2020-10-12
> **grahammechanical said:**
> With a some exceptions most Linux drivers are written by Linux developers without cooperation of the manufacturers who do not wish to reveal details of their intellectual property.

I actually find this bit really fascinating, how does someone begin to develop a driver for a piece of hardware that has no documentation? I suppose there must be standardised interfaces that are common to many different devices perhaps, which would potentially knock out a big chunk of the work? But I mean would this require a developer who also had an understanding of electronics to literally probe the device with a multimeter etc. and just poke it to see what it does?

---

### Post by jcdenton1995 on 2020-10-12
> **TheFu said:**
> Blame the vendors for their lack of support.  The only solution is for more people to use Linux on their computers so a significant number gets the attention of the vendor

I mean surely this is the way things are going, i.e more people switching to using Linux distributions. I've only been using Linux (Ubuntu) for as long as I've been a member of this forum, off the top of my head probably less than one year, and literally the only con I perceive (from the perspective of a normal user) are that Linux does come across as less user friendly than Windows - although to be honest I never used Windows in nearly as much depth as I use Linux, combined with the fact that I learn to do everything from a terminal and avoid GUIs, on reflection I think Ubuntu and Windows (or at least Windows 8.1) are probably actually on par in terms of user friendliness for those who choose to go the GUI route, and if you disregard the lack of an equivalent to 'control panel' for Ubuntu (maybe this exists?). Also that ingrained Windows familiarity is probably a big factor.

The hardware compatibility issue is trivial for a normal user unless they already own a decent amount of expensive devices that wont work with Linux. I just check before I buy.

I know that's a completely simplistic and uninformed analysis, but it's the perspective of a normal user, coming from someone who is not an IT professional or a life long techie. I honestly don't see how over the next ten years as Linux distributions become even more user friendly, coupled with the emergence of younger generations of computer users who are growing up in an ever more technological world, that they wont become far more mainstream. Also if you throw in privacy concerns surrounding proprietary software, and also the improving support for gaming on Linux, it just seems nailed on if things continue as they are (which is never guaranteed of course).

I'd be interested to hear more informed perspectives on this, especially regarding what business moves Microsoft might make to counter this...

---

### Post by TheFu on 2020-10-12
> **jcdenton1995 said:**
> I mean surely this is the way things are going, i.e more people switching to using Linux distributions. .... 

We all thought that when we started with Linux, but the statistics for desktop users hasn't moved in 20 yrs.  There ARE more Linux users today, but there are many more computers today.  Basically, it is population growth related.  At least on the desktop.

For servers, the entire world has changed in the last 20 yrs, except at 100% Microsoft companies.  Places that used commercial Unix have added Linux servers and those Linux servers have taken over 70-98% of what Unix systems did.

Then there is Android.  End-users of Android (and iOS) don't see them as Linux/Unix systems, but they are. When you get down to the non-GUI stuff underneath, Android is Linux just locked down in ways that a Linux desktop user would find frustrating. Google did some interesting things with userids and groups to make Android's security a little odd compared to our Ubuntu Desktops. That's all.

> **jcdenton1995 said:**
> The hardware compatibility issue is trivial for a normal user unless they already own a decent amount of expensive devices that wont work with Linux. I just check before I buy.

That's good advice, but sometimes we still get burned. A surface check for "Works with Linux" on a box isn't sufficient.
Other hardware that often doesn't/didn't work with Linux includes scanners, photo/slide scanners, some cameras, lots of wifi-enabled printers, some game controllers, webcams, microphones, wifi-NICs, ethernet NICs, RAID cards, some NVMe devices, some USB storage devices.  In short, assume hardware doesn't work until that exact model is proven to work ON THE RELEASE you intend.  I've got a RAID card that came with Linux drivers ... for 2.4.x kernels.  Nothing later. No way to make it work with any later kernels.  The box has "Linux Supported!" on the outside.  When I bought it, we were using kernels in the 3.0 line already.

> **jcdenton1995 said:**
> 
I know that's a completely simplistic and uninformed analysis, but it's the perspective of a normal user, coming from someone who is not an IT professional or a life long techie. I honestly don't see how over the next ten years as Linux distributions become even more user friendly, coupled with the emergence of younger generations of computer users who are growing up in an ever more technological world, that they wont become far more mainstream. Also if you throw in privacy concerns surrounding proprietary software, and also the improving support for gaming on Linux, it just seems nailed on if things continue as they are (which is never guaranteed of course).

At least you are thinking about this stuff. I never worked anywhere with an "IT" department my first 11 yrs in professional jobs.  When we needed a 10-base2 network put in, we came in over the weekend and ran the coax in the ceiling ourselves.  If we needed a printer, the boss would fill out some paperwork and it would show up in a box waiting to be installed. There was on guy who understood our normal connections to the mainframe systems (SNA). He had the same job as me. During the day, we were programmers.  If anything hardware related needed doing, we'd ask who wanted to help in the team, have a meeting, figure out a plan, and in a few weeks, the plan would be done taking about 5% of our time in that period. We did our normal programming jobs at the same time.

I feel bad for parents who allow their kids to only use Windows or only use iOS.  In the job market, we all need to be flexible. That means knowing at least 20% of multiple OSes until our careers are established - say 15 yrs in.  Then we each can make decisions.  I effectively stopped using Windows in any serious way in 2008.  I'd been using Linux since 1993 - about the same time I got a job doing Unix stuff, though my primary role was to port software from Unix to Windows and OS/2 at the time. Imagine trying to learn 12 OSes concurrently - and my degree isn't in computing.

Privacy concerns exist for all software.  There have been a number of F/LOSS modules across a number of projects that were modified to be anti-privacy. Some took a few weeks before anyone noticed. Some coders don't make a copy of the code, but point directly to the development tree online. This way, they get the most recent code ... with the anti-privacy changes.  GoLang and JavaScript coders commonly do that.  OTOH, Java coders tend to have crufty code because they don't get newer versions of libraries often enough.

> **jcdenton1995 said:**
> 
I'd be interested to hear more informed perspectives on this, especially regarding what business moves Microsoft might make to counter this...
There isn't any 1-true-answer for these things.  How it gets handled varies everywhere.

As for Microsoft, I have 1 rule.  Avoid whenever possible.  I don't use exFAT, because it came from MSFT.  I've seen MSFT destroy entire parts of industries through FUD use.  Recently, I keep hearing people claim they've been good recently.  So they aren't too nasty for 2 yrs and that should result in 30 yrs of forgiveness?  I can't forgive that quickly.  MSFT was behind the "organizations" who sued IBM over Linux use.  That lawsuit is still going, isn't it?  Has the BSA shut down?  As bad as most social networks are with our privacy, Microsoft was the "big bad" for 30+ yrs doing things to the entire industry.  Not everything any company does is bad. It is when they abuse their power to squash competition that I worry.  

Nobody worries about IBM being bad today, do we?  But we do worry about Oracle, Apple, Amazon, Microsoft, Twitter, Facebook, Walmart, Alphabet/Google.  These all have abused their power in ways that are morally questionable, if not illegal. Those are just the US companies. There are companies around the world like that. 

Sorry ... what was the topic again? ;) I forgot.

Ah ... hardware support for devices.   So, Google did something good for Desktop Linux users when they created chromebooks.  Because those have been really popular in schools (at least in the USA), vendors have been forced to support the Chromebook Linux kernels.  My webcam gained support for Linux that way.  It was Windows-only for years, then in 2016, I connected it to a chromebook and it worked.  Connected it to any older Chromebook from 2012-ish and it worked there too. That vendor had been notorious, at least to me, for being extremely popular, but never supporting Linux at all. Poof - I've learned that at least 4 different models of their webcams support Linux this year.  We're talking plug-n-play. The drivers are part of the kernel already for all of them.  So, while google is often bad, they aren't always bad when their market power does stuff like this.

---

### Post by grahammechanical on 2020-10-12
> how does someone begin to develop a driver for a piece of hardware that has no documentation?

They start with an actual example of the hardware. And that costs money they do not have. If there are alternative products that work in Linux then why spend time, energy and money trying to make every electronic device compatible with Linux? A person would have enough hardware to stock a computer museum.

Regards

---

### Post by jcdenton1995 on 2020-10-13
> **TheFu said:**
> Then there is Android.  End-users of Android (and iOS) don't see them as Linux/Unix systems, but they are. When you get down to the non-GUI stuff underneath, Android is Linux just locked down in ways that a Linux desktop user would find frustrating. Google did some interesting things with userids and groups to make Android's security a little odd compared to our Ubuntu Desktops. That's all.

This is a point, the way I was introduced to Linux was basically through having an android phone that I wanted to flash with another ROM, I'm sure that will be a gateway to Linux for others too, I notice particularly that a lot (the majority) of the community made informational material / blog posts etc. seem to be created by young east Asian men, who I always assume are Indian or thereabouts. Perhaps in that locale especially Linux use will grow because of the connection to android phones?

> Privacy concerns exist for all software.  There have been a number of F/LOSS modules across a number of projects that were modified to be anti-privacy. Some took a few weeks before anyone noticed. Some coders don't make a copy of the code, but point directly to the development tree online. This way, they get the most recent code ... with the anti-privacy changes.  GoLang and JavaScript coders commonly do that.  OTOH, Java coders tend to have crufty code because they don't get newer versions of libraries often enough.

I appreciate this, as someone who couldn't understand the source code anyway I like to think of it like taking part in a game of cards while hardly understanding the rules, I have no idea if the guy next to me is cheating (malware), but as long as everybody keeps their hands above the table (i.e open source), then I can have some confidence that if there is a cheat at the table, at some point someone who understands the game will notice and cry foul. Plus surely the open source community isn't exactly a soft target when compared with environments chock full of proprietary software, used by many people who are perhaps less aware of the potential pitfalls. But I understand open source isn't a panacea for all privacy concerns.


> Ah ... hardware support for devices.   So, Google did something good for Desktop Linux users when they created chromebooks.  Because those have been really popular in schools (at least in the USA), vendors have been forced to support the Chromebook Linux kernels.  My webcam gained support for Linux that way.  It was Windows-only for years, then in 2016, I connected it to a chromebook and it worked.  Connected it to any older Chromebook from 2012-ish and it worked there too. That vendor had been notorious, at least to me, for being extremely popular, but never supporting Linux at all. Poof - I've learned that at least 4 different models of their webcams support Linux this year.  We're talking plug-n-play. The drivers are part of the kernel already for all of them.  So, while google is often bad, they aren't always bad when their market power does stuff like this.

I wondered about this actually when I read that ChromeOS was a Linux distribution, I mean I don't know how similar to other distributions it is (a quick search turned up that it uses Google chrome as it's principle UI - sounds pretty new age) but perhaps this too is another factor that will lead to more people adopting Linux 'proper'?

Either way while I'm not massively impressed with Google's practices, or surveillance capitalism in general, I have to say that here in the UK the TV advert for the Chromebook absolutely nailed it. So many adverts for laptops completely fail to sell it to anyone who isn't technologically inclined, they just spout a load of spec jargon, but the chromebook advert actually addresses the main bug bears that normal people have with their laptops. I wouldn't be surprised if they do well as it sounds like they are in the US, especially with all the Covid related distance learning at the moment.

---

