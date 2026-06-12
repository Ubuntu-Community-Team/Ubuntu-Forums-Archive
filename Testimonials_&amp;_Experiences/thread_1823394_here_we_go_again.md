---
title: "here we go again"
date: 2011-08-12
forum: Testimonials &amp; Experiences
---

### Post by oscalation on 2011-08-12
Having an issue with my school requiring some propriety software. Photoshop specifically.  by looking around, it appears adobe has no interest in linux

[http://forums.adobe.com/thread/487814](http://forums.adobe.com/thread/487814)

"Is this a robo-posting?  You're just repeating the same stuff you said  before (which still makes no difference: next to nobody is buying  commercial software on Linux, which includes the ubuntu distribution)."

"You don't have to convince anyone here -- you just need to make Linux a  better place for application development (develop some standards, fix  the problems, etc.), and develop a market of users willing to pay for  commercial software."

ect ect.. you get the point.. those are comments from what their user profile says to be.. an "employee" so i take it they are creditable. there are tons of threads that all lean towards the same conclusions. 


Now, im not  advocating for adobe products, i would much rather see an open source solution .. obviously gimp has some room to grow.. im more so interested in the internal discussion and plans to attempt to remedy the ongoing issues between interoperability and software devs creating .. the vendor lock in effect.

---

### Post by 3rdalbum on 2011-08-12
Adobe spends too much time complaining about lack of standards and "fragmentation".

For instance, they complained that "There's no one standard for video decode acceleration on Linux". They cited VDPAU, X-Video and VA-API as the confusing, fragmented standards that are preventing them from accelerating video in Flash Player. The best API was VDPAU, and Adobe claimed it was missing features that made it impossible to use Flash Player with it.

The Gnash developers just implemented VDPAU support, despite it being "impossible" to do.

Adobe likes to complain about "Linux fragmentation" but in reality it's fairly simple to make the right decision for your program. If there was a big enough market for Photoshop on Linux, Adobe would grumble... but it would port it.

---

### Post by jasonrisenburg on 2011-08-12
> **bigthinker said:**
> ill keep this short. Been using linux for around 6-7 years, finally got some close friends to switch over for them to only experience many of the same obstacles i experienced as a new linux user and as i continue to use linux

the biggest obstacle i experience  is my education system/work/insert otherplace i use a computer here/, requiring proprietary software, photoshop,at school i was  pre informed  that i will need a mac, i will need photoshop, indesign, most of the software and extras that come with the college books are all windows or mac based... and im not doing web design or anything related to graphics. yes its easy to say use this great open source alternative.. though.. sometimes you dont  have a choice, college being one. You pay to go, you use what they say, or you fail. Period. 

by looking around, it appears adobe has no interest in linux

[http://forums.adobe.com/thread/487814](http://forums.adobe.com/thread/487814)

"Is this a robo-posting?  You're just repeating the same stuff you said  before (which still makes no difference: next to nobody is buying  commercial software on Linux, which includes the ubuntu distribution)."

"You don't have to convince anyone here -- you just need to make Linux a  better place for application development (develop some standards, fix  the problems, etc.), and develop a market of users willing to pay for  commercial software."

ect ect.. you get the point.. those are comments from what their user profile says to be.. an "employee" so i take it they are creditable. there are tons of threads that all lean towards the same conclusions. 


Now, im not  advocating for adobe products, i would much rather see an open source competitor .. obviously gimp has some room to grow.. im more so interested in the internal discussion and plans to attempt to remedy the ongoing issues between interoperability and software devs creating .. the vendor lock in effect. 

the adobe crowd seems to ring a good point, linux fragmentation and standards, i would argue that the linux community actually has a hand up in terms of creating Open standards that tend to be better suited and easier for vendors and developers to pick up and use.. less restriction. Though without going into detail i understand what they are referencing. And it appears to solve this issue, its going to take either;

1. a huge growth in our user base to make linux ports valuable 
2. a collaborative effort to solve some of these doubts and concerns about fragmentation 

most likely it will take both. This same concept is accountable across the board for our struggling market share, do i want to use photoshop on linux? not really, but i have to. So for now, users are forced to boot into MS or Mac to get what we need. No matter  how slow, how sluggish, and they tend to forget the dual boot option and say... linu what? ubuwho?


the answer to me is clear. Dual boot. you will have all the function of Linux with Mac..lol that or carry around 2 laptops.
Im glad to be of servie.

---

### Post by Juan Largo on 2011-08-12
> **jasonrisenburg said:**
> the answer to me is clear. Dual boot. you will have all the function of Linux with Mac..lol that or carry around 2 laptops.
Im glad to be of servie.
Don't dual boot just to run Photoshop.  You'll either have to pay muchos dollars for a Windows license or install one of those virus-laden pirated copies.

Photoshop has a "silver" rating from Codeweavers.  In other words, it'll run in Linux under CrossoverOffice.  

[http://www.codeweavers.com/compatibility/browse/?app_id=8](http://www.codeweavers.com/compatibility/browse/?app_id=8)

Of course CrossoverOffice isn't free, but neither is Photoshop.

---

### Post by Spice Weasel on 2011-08-14
> **3rdalbum said:**
> Adobe spends too much time complaining about lack of standards and "fragmentation".

For instance, they complained that "There's no one standard for video decode acceleration on Linux". They cited VDPAU, X-Video and VA-API as the confusing, fragmented standards that are preventing them from accelerating video in Flash Player. The best API was VDPAU, and Adobe claimed it was missing features that made it impossible to use Flash Player with it.

The Gnash developers just implemented VDPAU support, despite it being "impossible" to do.

Adobe likes to complain about "Linux fragmentation" but in reality it's fairly simple to make the right decision for your program. If there was a big enough market for Photoshop on Linux, Adobe would grumble... but it would port it.

Yep, clearly their claims are baseless and stupid and they are just too lazy to make the effort. :rolleyes:

[IMG]http://i.imgur.com/SqPUXl.jpg[/IMG]

Related:

"Remember, never look at your own faults. Always blame someone or something else "

---

### Post by 3rdalbum on 2011-08-15
Fun diagram.

The obvious answer to this "fragmentation", as evidenced by the diagram, is to target ALSA. Everything feeds into ALSA and ALSA is available on all Linux distros.

This probably breaks support for FreeBSD users, but then Adobe never claimed to support FreeBSD anyway. If they wanted to support FreeBSD they just need OSS support as well. Or maybe Gstreamer - it has ALSA, Pulseaudio and OSS backends doesn't it?

The diagram is a bit old now, actually. OSS is depreciated on Linux. ESD and aRTs are no longer available.

---

### Post by 3Miro on 2011-08-15
Fragmentation in Linux is overstated and things are a lot more standard than people think. As pointed out, everyone else can make good software for Linux, Adobe somehow can't. They either haven't hired the right people or they just don't care and use "fragmentation" as an excuse.

---

### Post by Peter09 on 2011-08-15
There is a driver these days that hopefully will kick Adobe and others (Silverlight sites for example) to become more open and standard - its called Android.

---

### Post by TBABill on 2011-08-15
To me the problem is simple. Linux cannot meet all needs. We live in a world where we must use what provides us with the best end result and there's no shame in using whatever that may be. Windows and Mac do win in several areas, software availability being one of them. For me, Linux does meet all my needs except with iTunes. Otherwise I don't need any other OS. But the reality is, when you work in an environment that requires specific, proprietary software, then it makes sense to use the infrastructure that best supports the requirement.
 
I'm of the belief that it just makes sense to get the job done as easily and cleanly as possible. If that means using Windows or Mac, then take that path of least resistance. 
 
As stated, you use what others require unless you find an adequate solution around that roadblock. Open source is great when it fulfills your needs, but can be mind numbingly frustrating when you have a need it cannot meet. I just cut out the middle and use whatever I need at the time.

---

