---
title: "[Video] A real first-time Ubuntu User"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-16
I really enjoyed this video and wanted to share with you all.
I'm not sure if we can post links to YouTube here anymore, but I think there are no copyright issues in this case.  

[http://www.youtube.com/watch?feature=player_embedded&v=ltE_ekc8kE8](http://www.youtube.com/watch?feature=player_embedded&v=ltE_ekc8kE8)

The video shows a real user, an older man, using Ubuntu for the first time.

It makes me rethink the relevance of what we do here

I wonder if Quality Assurance shouldn't also be more about user experience aspects (not only the technical and "under-the-hood" bugs), and include UX/UI feedback to GUI devs. UX/UI feedback and discussion, at least the mailing lists of it, are unusable and packed with trolls and haters. Traffic is huge and mostly off-topic. 

Coherent, organized people like us could provide a much more useful input on UX/UI aspects under Testing/Quality Assurance processes. 

Regards,
Effenberg

---

### Post by synaptix on 2012-03-16
[http://ubuntuforums.org/showthread.php?t=1940426](http://ubuntuforums.org/showthread.php?t=1940426)

---

### Post by kaldor on 2012-03-16
> **effenberg0x0 said:**
> 
I wonder if Quality Assurance shouldn't also be more about user experience aspects (not only the technical and "under-the-hood" bugs), and include UX/UI feedback to GUI devs. UX/UI feedback and discussion, at least the mailing lists of it, are unusable and packed with trolls and haters. Traffic is huge and mostly off-topic. 

Coherent, organized people like us could provide a much more useful input on UX/UI aspects under Testing/Quality Assurance processes. 


+1

The only issue here is separating valid UI problems (like the Global menu hiding- non-technical users HATE this) from "it changed, therefore unusable" reports. ;)

A community IRC channel could be an option. Over time, information can be collected and communicated to the UI guys, etc.

---

### Post by rg4w on 2012-03-16
> **kaldor said:**
> +1

The only issue here is separating valid UI problems (like the Global menu hiding- non-technical users HATE this) from "it changed, therefore unusable" reports. ;)

A community IRC channel could be an option. Over time, information can be collected and communicated to the UI guys, etc.
A bug report was recently opened for this:
[https://bugs.launchpad.net/ayatana-design/+bug/955193](https://bugs.launchpad.net/ayatana-design/+bug/955193)

---

### Post by effenberg0x0 on 2012-03-16
> **synaptix said:**
> [http://ubuntuforums.org/showthread.php?t=1940426](http://ubuntuforums.org/showthread.php?t=1940426)

Yes, thanks for noticing. I can understand that other people in the world might have seen the same video and commented about it. Unsurprisingly Google shows many other places where it was posted too. But the thread at the Café has a 80%/20% chance to evolve to the same old pros/cons/conspiracy we can't stand anymore until the thread gets closed. It's a lot like the UI mailing lists - which are of no use to UI developers. Ordinary-users focus on aspects that are of small interest to us. Example: I have recently blocked Unity-Dev mails as I was getting 50 mails a day from people arguing Unity interface vs religion preferences. It's really a waste of time.

The approach here, from a testing point of view, is potentially more interesting. And also inadequate for the Café.

Here's what ticked my brain when seeing this video: Considering we have an independent testing-team that can engage into any activity, and a QA-Team potentially undergoing structural changes and very open to improvement:
- Is it valid to develop processes for better testing of UX/UI (considering both have been strongly focused in technical aspects)?
- If so, do we have the resources to do it? 
- What would better testing consist of?
- How can we do it? How does one evaluates UX/UI without investing money into focus group sessions? 
- Do we have the people to delegate this to? What are the skills required?
- How do we evaluate the performance of UX/UI testing managers?
- How do we report results efficiently, thus rapidly and efficiently causing positive changes in UX/UI?
- Has it been done before, and correctly? Is it being done right now? 

I think in terms of project management and results. Would it be possible to: 1) Create samples of users from the community (regions, age ranges, accessibility groups, etc). 2) Have they test Development Releases UX/UI features regularly. 3) Collect results via OnLine survey. 4) Use statistics to evaluate results;

I think it is possible, it is something we never did here, it could be managed by one single member of the testing team, technical resources (sample selection, software distribution method, online survey, statistics analysis) are easy to implement and mostly automated. A summary of consolidated results is probably of more use to developers, to guide changes in UI, then browsing through a million off topic posts to try to detect valid points of view, analysis and feedback. Therefore such a project has the potential to  drive positive change if we adopt it and succeed.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-16
> **kaldor said:**
> +1

The only issue here is separating valid UI problems (like the Global menu hiding- non-technical users HATE this) from "it changed, therefore unusable" reports. ;)

A community IRC channel could be an option. Over time, information can be collected and communicated to the UI guys, etc.

Good idea, using IRC sessions with users can be a great alternative.

I'll draft some ideas for it: Rationale, some options on how it could be done, expected results, etc. 

Regards,
Efenberg

---

### Post by kaldor on 2012-03-16
> **effenberg0x0 said:**
> Good idea, using IRC sessions with users can be a great alternative.

I'll draft some ideas for it: Rationale, some options on how it could be done, expected results, etc. 

Regards,
Efenberg

It's also very easy to keep under control. It would be cool if there could be an *actual* UI channel with people who actually know what they're talking about, and able to set apart their personal bias for UI change and evolution. It's very understandable why Ayatana (or any UI devs) doesn't focus much on the community's concerns.

Note: just realized how blunt this post is. However, my point still stands. It isn't meant to offend anyone :)

---

### Post by rg4w on 2012-03-16
> **effenberg0x0 said:**
> Here's what ticked my brain when seeing this video: Considering we have an independent testing-team that can engage into any activity, and a QA-Team potentially undergoing structural changes and very open to improvement:
- Is it valid to develop processes for better testing of UX/UI (considering both have been strongly focused in technical aspects)?
- If so, do we have the resources to do it? 
- What would better testing consist of?
- How can we do it? How does one evaluates UX/UI without investing money into focus group sessions? 
- Do we have the people to delegate this to? What are the skills required?
- How do we evaluate the performance of UX/UI testing managers?
- How do we report results efficiently, thus rapidly and efficiently causing positive changes in UX/UI?
- Has it been done before, and correctly? Is it being done right now? 

I think in terms of project management and results. Would it be possible to: 1) Create samples of users from the community (regions, age ranges, accessibility groups, etc). 2) Have they test Development Releases UX/UI features regularly. 3) Collect results via OnLine survey. 4) Use statistics to evaluate results;

I think it is possible, it is something we never did here, it could be managed by one single member of the testing team, technical resources (sample selection, software distribution method, online survey, statistics analysis) are easy to implement and mostly automated. A summary of consolidated results is probably of more use to developers, to guide changes in UI, then browsing through a million off topic posts to try to detect valid points of view, analysis and feedback. Therefore such a project has the potential to  drive positive change if we adopt it and succeed.
I think you're onto something very important there.

Surveys are problematic because what people say they do and what they actually do are often different. This is where disciplined user testing is invaluable:  through direct observation we can see exactly what people do, where they move through a UI with ease and where they get stalled or confused.

I've long believed the FOSS world, and Ubuntu in particular, might benefit from what we could call "distributed user testing".

One of the problems with user testing is that it's expensive.  It takes a lot of time to do well, and even more time to analyze results.

But just as the code side of things benefits from distributing the workload across the community, I believe it should be possible to distribute usability testing across the community as well.

Ideally, the core design team at Canonical would draft a set of guidelines, ideally in partnership with interested usability engineers from outside the company, to establish goals and methods for testing, and to distribute A/B prototypes to the community to support such efforts.

In the early stages of the design process these A/B prototypes can be made with paper - there's a surprising amount of literature available on the value of paper prototyping, and with innovations like Dash, the HUD, and others, such early-stage prototyping can be invaluable to test.

In later stages semi-functional A/B UIs can be tossed together in something like Quickly or LiveCode for such testing at reasonably low cost, and probably with community participation (personally I'd love the opportunity to contribute such prototypes made with LiveCode).

Interested members of the community could apply to be outside test organizers, and use a variety of "guerilla usability" methods to collect useful data.  In fact, with available software for simultaneous recording of webcam and screen, good data can be collected quite cheaply.

These community teams would be given a place to upload their data and also deliver their own analysis if they like.   The Canonical team would then be able to focus on analysis more than data collection,  and would give due consideration to submitted analyses as well.

I think such an initiative could gather better data at more stages of the design process than relying on one team in London, and probably cost Canonical less than shouldering the responsibility themselves as they have.

But it would of course require that the design team at Canonical is as open to accepting outside assistance as the engineering teams are.

If so, it seems worth trying.

---

### Post by effenberg0x0 on 2012-03-16
> **rg4w said:**
> I think you're onto something very important there.

Surveys are problematic because what people say they do and what they actually do are often different. This is where disciplined user testing is invaluable:  through direct observation we can see exactly what people do, where they move through a UI with ease and where they get stalled or confused.

I've long believed the FOSS world, and Ubuntu in particular, might benefit from what we could call "distributed user testing".

One of the problems with user testing is that it's expensive.  It takes a lot of time to do well, and even more time to analyze results.

But just as the code side of things benefits from distributing the workload across the community, I believe it should be possible to distribute usability testing across the community as well.

Ideally, the core design team at Canonical would draft a set of guidelines, ideally in partnership with interested usability engineers from outside the company, to establish goals and methods for testing, and to distribute A/B prototypes to the community to support such efforts.

In the early stages of the design process these A/B prototypes can be made with paper - there's a surprising amount of literature available on the value of paper prototyping, and with innovations like Dash, the HUD, and others, such early-stage prototyping can be invaluable to test.

In later stages semi-functional A/B UIs can be tossed together in something like Quickly or LiveCode for such testing at reasonably low cost, and probably with community participation (personally I'd love the opportunity to contribute such prototypes made with LiveCode).

Interested members of the community could apply to be outside test organizers, and use a variety of "guerilla usability" methods to collect useful data.  In fact, with available software for simultaneous recording of webcam and screen, good data can be collected quite cheaply.

These community teams would be given a place to upload their data and also deliver their own analysis if they like.   The Canonical team would then be able to focus on analysis more than data collection,  and would give due consideration to submitted analyses as well.

I think such an initiative could gather better data at more stages of the design process than relying on one team in London, and probably cost Canonical less than shouldering the responsibility themselves as they have.

But it would of course require that the design team at Canonical is as open to accepting outside assistance as the engineering teams are.

If so, it seems worth trying.

I completely agree. I've seen some focus group sessions, including those in which there's a cam measuring where the user eyes are looking at, the level of uncertainty in their mouse moves, average time to interpret screen info and perform actions, locate programs, menus, options, etc. It is really expensive... But the alternatives you mention could be done and maybe would create a valuable data set for analysis. I'm gonna add your suggestions to a blueprint.

Regards,
Effenberg

---

### Post by rg4w on 2012-03-16
> **effenberg0x0 said:**
> I'm gonna add your suggestions to a blueprint.
Wonderful, Effenberg.  Please post the URL when it's up. Thanks.

---

### Post by Andrew_P on 2012-03-16
The video was nice for showing a first-time Linux user for a few minutes.  What's *more* interesting is a long-time Windows/DOS/Apple user after being exposed to Linux for 5-10 hours discovering the things that are *missing* or *broken* in Linux, even after over 15 years of development.  Although it's gotten better over the last 10 years, it's enough to drive all but the geekiest, hard-bitten Linux user into the arms of Apple or Microsoft.  Being a complete computer novice and not knowing things could be different is an advantage when beginning with Linux.

---

### Post by cariboo on 2012-03-16
> **Andrew_P said:**
> The video was nice for showing a first-time Linux user for a few minutes.  What's *more* interesting is a long-time Windows/DOS/Apple user after being exposed to Linux for 5-10 hours discovering the things that are *missing* or *broken* in Linux, even after over 15 years of development.  Although it's gotten better over the last 10 years, it's enough to drive all but the geekiest, hard-bitten Linux user into the arms of Apple or Microsoft.  Being a complete computer novice and not knowing things could be different is an advantage when beginning with Linux.

Even though this is off topic, in most cases when a Windows/Dos/Apple user finds something they think is broken or missing, it is more than likely because they are trying to do something the same way they would using Windows or OSX.

You can also say the same thing about Windows and OSX, it doesn't take very long to find many things that don't work the Linux way with both operating systems.

---

### Post by tlcstat on 2012-03-16
Greetings,
I honestly don't get the significance of one new user's response to a new distro. I have Windows customers that have been paying me to answer the same questions over and over for twenty years, and I closed my consulting business when I retired in 2004. I still answer the questions and I still get checks in the mail. Thing is these are successful people in their own field of expertise. They are just task oriented on a computer. One guy who owns a real estate appraisal service doesn't know what he is looking at when he opens a folder browse window. This has been the same since he became my customer with Windows Work Groups 3.1. It really isn't that uncommon for users not to know very much. I have old geezers that run printers, cameras, usb drives, scanners, dual monitors, etc but can't update software or deal with spyware and antivirus. They will invariably click on the scam on the web page and infect their system. This problem is more than just a debate between Unity and Gnome UI and whether anyone is making a buck from all of this work. Ultimately it is the software that counts and there are a lot of favorites that aren't ported to Linux. It really doesn't matter to a Windows user that I am happier than I have ever been in my life with Oneiric, Unity and Linux native software. This is a really great experience for me. But I don't mind going bald learning something new. 
tlcstat

---

### Post by Andrew_P on 2012-03-17
> **tlcstat said:**
> Greetings,
I honestly don't get the significance of one new user's response to a new distro ...

What you describe sounds like a form of "computer dyslexia", if you will, just as some people never learn to recognize a make/model of automobile or haven't the foggiest idea of how an internal combustion engine works to propel a vehicle.  Since I'm technology-minded, I have great difficulty in putting myself into that mindset, but considering that there are other fields of endeavor that don't interest me and in which I am virtually illiterate, I must accept that this is so.  There are people that use these high-tech gadgets like they would an household appliance, without needing to understand what makes them work, and that's exactly what the designers intended.

---

### Post by tlcstat on 2012-03-17
Greetings,

Original by Andrew_P
> There are people that use these high-tech gadgets like they would an household appliance, without needing to understand what makes them work, and that's exactly what the designers intended.


Exactly! The "video" is just one persons opinion, yet there are millions using Ubuntu everyday of the week and in quite a few alterations. There are even countries like Brazil that have their own official national version. The truth is that every single OS and every single software and every single processor is broken. Until every option, in every circumstance, with every hardware arrangement is tested, perfection cannot be proven. Someone will invariably have some unconventional need that puts some unexpected demand on a part of the process that fails [read bug]. I made a living supporting business customers and their needed work-a-rounds for all of those bugs and the saga continues. Doesn't matter what platform is used. I could break out of retirement today and make a pretty good living supporting any system running any OS with any software. All that being said I have become a Ubuntu junkie over the last two years and I haven't found much to complain about. I did have to reinvent myself so far as software is concerned however. But the power is there if one takes the time to look for it. 
tlcstat

Greetings,
And P.S. it doesn't hurt to buy a computer with Ubuntu tested hardware before you complain. After all, if you want to be a system engineer then at least be a good one and use compliant hardware. 
tlcstat

---

