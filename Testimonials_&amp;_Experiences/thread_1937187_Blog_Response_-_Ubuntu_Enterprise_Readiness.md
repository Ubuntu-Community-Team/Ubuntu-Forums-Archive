---
title: "Blog Response - Ubuntu Enterprise Readiness"
date: 2012-03-07
forum: Testimonials &amp; Experiences
---

### Post by cdillard-hsp on 2012-03-07
I'm referencing a Canonical blog post that I commmented on originally.  I thought about writing this response on the Blog but figured that I'd post it here in the Forums so it wasn't so public and so that you folks could comment more easily.

The original Canonical Blog: [http://blog.canonical.com/2011/08/26/crunch-time-on-the-enterprise-desktop/](http://blog.canonical.com/2011/08/26/crunch-time-on-the-enterprise-desktop/)

... So, here goes:
I thought I'd come back to this blog post and comment since it's premise is that Ubuntu is 'enterprise desktop ready'.  First, I really love Linux.  I've been using a Linux desktop for daily business use since at least 2002.  I'm still not convinced that Linux (Ubuntu or otherwise) is ready for the enterprise, or even a home environment where the user is going to expect consistency, reliability and compatibility.  It pains me to say this, but I think the reality is that if a user expects to collaborate on documents with others who may not be running Linux and LibreOffice, if the user expects to be able to collaborate via online meetings (Webex, GoToMeeting, etc.), if the user expects to be able to enjoy multimedia (DVD, Blueray, Flash, etc.), and if the user expects to be able to use a laptop (especially with a docking station - like those found in work environments), then their only choice is Windows.  There are so many issues with cross-platform compatibility that using Linux for these types of things is very difficult.  

Here are a few examples of top issues that must be addressed:
1. Sharing and Collaboration on Documents in a Corporate Environment:  In a post above, Boris suggested Yworks/yEd for UML and diagramming, and it does work but there are new issues with fonts, no more Oracle Java in Ubuntu, changes in the x-server that cause the yEd installer to fail, etc. after upgrading to Ubuntu 11.10.  So that's not a good fit.  Besides, almost no one (in comparison to Visio) uses yEd so you really cannot collaborate unless you say "hey, toss away your $400 Visio and use this yEd software".

Even if a Windows, a Mac OS, and a Linux user are all running LibreOffice (particularly Impress) there are compatibility issues.  Text layout and framing in slides is broken and font compatibility is rarely there, so a presentation is really only usable on the system that created it.

Also, don't count on being able to reliably, consistently use Webex (just to name one) under Linux.  Maybe if you've ditched your existing, incompatible computer and purchased one from the Ubuntu/Canonical (or Red Hat, SuSE) HCL, you might be able to attend a Webex, but you might not be able to present, share your screen or an application, allow someone to control your desktop or take control of theirs, etc.  Windows, it just works every single time.

2. Hardware Support: Canonical, Red Hat, SuSE all certify laptops to work with their distribution but again, Windows just works, docking station and all, suspend/resume works.  Linux pm-utils and/or kernel cannot cope with dock/undock, and recurring suspend/resume issues make that feature risky at best to use under Linux.  With Microsoft companies are hit with vendor lock-in in terms of software but it seems with commercial Linux we would be hit with a narrow computer make/model lock-in penalty since unlike Windows, not all computers will function correctly with Linux.

So users wanting to run Linux are locked into a very small box in terms of what's available in modern harware.  The reality seems to be "don't use a computer with an ATI or Nvidia graphics card, you cannot use a docking station with your notebook and expect to be able to dock and undock while the computer is powered on or suspended, and don't count on suspend & resume to work consistently even on a 'certified' computer, especially after kernel or pm-utils updates.

3. Multimedia: Encrypted DVDs and Blueray either don't work at all or you spend time hacking together codecs, etc. only to discover that now only some of your DVDs will play.  Pay $40 for DVD playback software for Windows and you can be assured that all of your disks will work, every time.

Want to watch online multimedia?  Well, Adobe is killing Flash for Linux now and even as things are with current Flash, you'll end up with the plug-in crashing or some other problem that causes pain.

Want to play MP3s?  Hack that together too in Linux.

In conclusion, Linux is secure, it has a terrific shell, and many great in-OS features and I simply enjoy using it (most of the time).  That said though, the trade-off is compatibility with other users' software and documents, very limited collaboration options, and loss of hardware flexibility and support.  Windows is less secure and less flexible but it is very usable and since 99% of the world uses it you can rest assured that you won't have issues with compatibility.

---

### Post by ubudog on 2012-03-07
*Thread moved to Ubuntu Testimonials and Experiences.*

---

### Post by Juan Largo on 2012-03-07
Point 1 - Agreed.  Collaboration with Windows/Mac users is problematic.  However, universal use of OSS would fix that. 

Point 2 - Linux interfaces with hardware through the kernel (with some exceptions) whereas Windows interfaces with hardware through vendor-created drivers (for the most part).  The fact that Linux works at all is a minor miracle, given the fact that hardly any hardware vendors support Linux.

Point 3 - Disagree.  I have no problem at all playing/copying encrypted DVDs using Linux.  (Any DVD that can be played can be encoded, and thereby copied).

---

### Post by mastablasta on 2012-03-07
well i wonder how companies that use Linux do operate then? out of this world and in their own world? 
 
why you couldn't use a notebook with ATI graphics? and yes we all know that business users need to have a powerfull GPU. all those presentations.... 
 
what kind of hacks are you talking about? all you need to do is install the codecs form software center. Codecs also needed to be installed in windows. maybe they come included in win7, i don't know....
 
java and flash - you really didn't read what was said/written, huh? not surprised i see a lot of people doing this lately. they look at the title and form an opinion.
 
Java - Oracle will stop supporting it because all new java will be openjava, which they will support. inlcuding in windows.
Flash - will be replaced by other projects/tools within next 5 years. and let's not begin to discuss the HTML5 and how Apple already gave it flash finger for the iOS. Flash is getting obsolete even for Adobe.

---

### Post by cdillard-hsp on 2012-03-07
> **mastablasta said:**
> well i wonder how companies that use Linux do operate then? out of this world and in their own world? 
 
why you couldn't use a notebook with ATI graphics? and yes we all know that business users need to have a powerfull GPU. all those presentations.... 
 
what kind of hacks are you talking about? all you need to do is install the codecs form software center. Codecs also needed to be installed in windows. maybe they come included in win7, i don't know....
 
java and flash - you really didn't read what was said/written, huh? not surprised i see a lot of people doing this lately. they look at the title and form an opinion.
 
Java - Oracle will stop supporting it because all new java will be openjava, which they will support. inlcuding in windows.
Flash - will be replaced by other projects/tools within next 5 years. and let's not begin to discuss the HTML5 and how Apple already gave it flash finger for the iOS. Flash is getting obsolete even for Adobe.

I'm going to respond to your thoughts from the top:

1. I have no idea what you mean here.  Want to elaborate?

2. ATI is fine but if you're an organization with a significant investment in computers that have Nvidia cards then this is a big deal.  It's very well a show-stopper in a migration scenario.  The fact is that there are significant issues in terms of reliability and 'does it work at all' when it comes to Nvidia cards and it should be fixed.

3 - 5. You might be missing my overall point here.  Despite plans from Oracle and Adobe, which may happen over the course of the next few years, I'm referring to the here and now issues that Linux users face (corporate or otherwise) when it comes to having a platform that simply works as *the user expects it to*.  It's perhaps painful, but anybody moving from Windows to Linux is going to expect Linux to *work* like Windows does.  They may be forced to use Linux, as in a corporate migration project, and they will focus on what doesn't work.

My overall point here was in part to convey some of the long-term, consistently frustrating things about Linux.  I've been using Linux all day, every day since 2002 and I've seen some wonderful progress, so it's not all bad - not even by a long shot.  However, anybody who says that the overall ease of use and seamless user experience you'd get with Windows is present in Linux is not being honest.

A Windows box:
[LIST]
[*]Docks and Undocks reliably and without issue
[*]Has no issues with suspend and resume
[*]Has, in my experience, been far less frequently harmed by OS updates and patches
[*]Has no issues functioning fully with Intel, ATI, or Nvidia GPUs
[*]Works with Webex, GoToMeeting, etc. nearly 100% of the time.  You don't have to cross your fingers and hope you're not embarrassed when your Linux system leaves you hanging while your colleagues wait and wonder.
[*]..with MS Office, makes it easy to collaborate with others on docs
[*]Typically has no issues playing a variety of multimedia formats, albeit even if you have to shell out a little cash for an app or two
[/LIST]

The bottom line is that Linux is a great OS but there are some significant road blocks to wide-spread adoption.  I've just pointed out a few of the biggest IMHO.

---

### Post by 3rdalbum on 2012-03-08
> **cdillard-hsp said:**
> 
2. ATI is fine but if you're an organization with a significant investment in computers that have Nvidia cards then this is a big deal.  It's very well a show-stopper in a migration scenario.  The fact is that there are significant issues in terms of reliability and 'does it work at all' when it comes to Nvidia cards and it should be fixed.

That's simply not true. Intel, Nvidia and ATI all work well. ATI is the black sheep but its drivers are still very usable on Linux.

> A Windows box:
[LIST]
[*]Docks and Undocks reliably and without issue

I wasn't aware people used dockable PCs - I thought only Apple made them, back in the 1990s.

> [*]Has no issues with suspend and resume

Not actually true. One of my PCs runs Windows and resumes flakily; I don't suspend it anymore as it's likely to crash on resume. I don't know if I'm lucky or what, but my three Linux machines suspend and resume very reliably.


> [*]Works with Webex, GoToMeeting, etc. nearly 100% of the time.  You don't have to cross your fingers and hope you're not embarrassed when your Linux system leaves you hanging while your colleagues wait and wonder.

I have no experience with this software, but it wouldn't surprise me if this is the case. If there are issues with this software, best take them up with the developer; I believe these are proprietary products? There is nothing inherent in Linux that would cause these kinds of problems to occur.

I've worked at a big company before and I don't believe they used this software; different businesses work differently.

> [*]..with MS Office, makes it easy to collaborate with others on docs

Open-source software tends to lack polish and imagination and Libreoffice should definitely focus on collaboration features, as well as features that pre-empt what Microsoft is doing. Merely staying within a few years behind Microsoft is not good enough.

> [*]Typically has no issues playing a variety of multimedia formats, albeit even if you have to shell out a little cash for an app or two


I don't think you quite understand.

Codec installation on Ubuntu is easy, if you want to have legal codecs (as Enterprise doesn't want to be raided by Police and charged with unlicensed software). You buy the codecs and Fluendo DVD Player from the Ubuntu Software Center; it takes only a couple of clicks.

Home users typically would rather not pay for official licensed codecs and DVD playback software, so they need to add a repository and run a few commands to install the unlicensed codecs. Ubuntu doesn't officially support the unlicensed codecs so there is a small amount of hoop-jumping involved. Having said that, it's not as difficult as you make out. Copy and paste something from the Medibuntu website into the terminal, and you've got it all.

---

### Post by mastablasta on 2012-03-08
Actually latest ATi drivers work even with switchable/hybrid graphics on laptops.
And as i know nvidia only has issues with Optimus, but otherwise works just fine. 
We use Intel chips in most of our computers as they are the cheapest and they do their job. i knwo they owuld also work well under linux for office work.
 
i know they use docks here, though i don't know if and how well they work on Linux.
 
you meeting software is some very specific software that you chose. you could have used google talk, google hangouts and similar. i am sure there are also others avaialble in linux. 
 
my point was that you generalized. there for example are large car makers that use only linux in their companies despite your claim that it is not ready for corporate environment.
 
additionally, the tools i use at work - MS Word and Excel, outlook and SAP R/3 can all be either run on linux (wine or natively) or have good alternatives. i believe linux even has a good AD alternative. i've also noticed how they purchase (in our company) these packages from MS yet no one actually uses them or their features they payed so much for. for exmaple they bought servers and arranged that all "my documents" form all users would have their backups on server. but guess what? only  abotu 50 or so users have this feature enabled, the 15000+ others do not have.
 
Corruption anyone?
 
despite their negativism i am 100% we could easilly switch to linux. perhaps a few computers with specialised windows software would remain on windows, but the rest could just as well run Linux.

---

