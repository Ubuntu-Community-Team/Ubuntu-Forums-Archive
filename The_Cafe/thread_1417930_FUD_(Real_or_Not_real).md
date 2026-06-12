---
title: "FUD (Real or Not real)"
date: 2010-02-27
forum: The Cafe
---

### Post by Brandel Valico on 2010-02-27
Yeah believe it or not I'm curious about what sort of FUD you have heard. All to often topics here get derailed by this person or that screaming FUD. Saying that what one person is saying is FUD all while saying things back at them without actually offering proof to either disprove the FUD they claim the person is spreading. Or for that matter to prove their own statements. 

[B]So whats the worst load of FUD you have ever heard that actually ended up being True?

Whats the biggest load of FUD you believed that ended up being False?[/B]

For myself I think the answer to both questions have been involved with the Conficker Virus/worm.

[http://en.wikipedia.org/wiki/Conficker]("http://en.wikipedia.org/wiki/Conficker")
(Please keep in mind the link is to Wikipedia which while mainly reliable is not 100%)

When I first heard about it I thought here we go again another big pointless scare for an issue with a nice easy fix all ready available Like the [Y2K]("http://en.wikipedia.org/wiki/Year_2000_problem") all over again. (Again used Wikipedia as a gathered info site not as proof positive) 

Then well nothing really happened except a lot of people spending a lot of money on upgrades and patches. Then it did do something.... It upgraded itself. So that was something to be sure. I honestly thought it was another big load of FUD that it didn't really exist.

The fact that all computers were at risk actually had me freaked out for a few hours. Because well the news (Evil people who speak with forked tongues :P) people said ANY computer was at risk. It wasn't until I looked into it more that I found out only Windows computers seemed to be at risk. 

So you have mine. I am curious what yours are. If they are one in the same like mine or two separate things.

Also I do ask that you actually offer some other source of collaborating information. The idea here isn't to start a FUD war. (If this does become so I ask that the thread be locked down quickly) But to share experiences we have all had were FUD fooled us into thinking something that was or wasn't true in the long run. As well as to hopefully in sharing them help others understand that screaming FUD without A) Disproving the other persons statements in a calm and logical way with actual proof not just your own POV. or B) Checking out the validity of their statements first and not just reacting do to your own preconceived notions, is just as bad as what you feel they are doing.

---

### Post by chillicampari on 2010-02-27
FWIW on the Y2K issue, a lot of people put in a lot of extra hours to make a comfortable transition.

---

### Post by hobo14 on 2010-02-27
Yeah, I've noticed people just use "FUD" as soon as someone says something they don't agree with.

---

### Post by Firestem4 on 2010-02-28
> **Brandel Valico said:**
> 

[B]So whats the worst load of FUD you have ever heard that actually ended up being True?

Whats the biggest load of FUD you believed that ended up being False?[/B]

For myself I think the answer to both questions have been involved with the Conficker Virus/worm.

[http://en.wikipedia.org/wiki/Conficker]("http://en.wikipedia.org/wiki/Conficker")


FWIW, I'll tell you that that virus is a f'**g b**** to get rid of in an infected network because of how easily it can propagate. I've had 3 encounters of the virus within my companies network. It wasn't easy but I managed to remove all traces of the virus each time..(while the rest of the I.T. staff slacked..yay me)

---

### Post by Brandel Valico on 2010-02-28
chillicampari: No doubts about that here. I know alot of work was done to make it a smooth transition. I'm more talking about the scare and misleading info in that respect. The fix for most computers was a quick download and patch job. (True this is how easy it was for end users and isn't meant to make it sound like the people who made it that easy for those users didn't work hard or don't deserve any credit they did and do)

Firestem4: I had all ready switched to Linux at the time so after the initial shock of it actually doing something and my accepting it was a massive virus and the media all saying no PC is safe (I again later found it was only Windows PC's directly affected)  I did some research on it and actually had to remove it from my wifes Desktop and Laptop as well as my mom and brothers Desktop PC's. (Wife now uses Ubuntu) As much of a pain as it was for me to do. I don't even want to consider the hours you put in cleaning out a whole company network not just once but 3 times. (Was it people bringing in infected flash drives or other such media that reinfected the systems?) Is it still an issue?

Hobo14: nice to see I'm not the only one noticing this trend.

---

### Post by Firestem4 on 2010-02-28
> **Brandel Valico said:**
> 

Firestem4: I had all ready switched to Linux at the time so after the initial shock of it actually doing something and my accepting it was a massive virus and the media all saying no PC is safe (I again later found it was only Windows PC's directly affected)  I did some research on it and actually had to remove it from my wifes Desktop and Laptop as well as my mom and brothers Desktop PC's. (Wife now uses Ubuntu) As much of a pain as it was for me to do. I don't even want to consider the hours you put in cleaning out a whole company network not just once but 3 times. (Was it people bringing in infected flash drives or other such media that reinfected the systems?) Is it still an issue?

Alright, one of the reasons the Conficker Virus was so well known and credited as being the worst virus in years is because it was 1 parts sensationalistic journalism, and 2 parts marketing scare. (Can't tell you how many AntiVIrus vendors jumped on the scaremongering to sell their products, Norton was the worst culprit of that IMO).

I work at a small company with around 15 employees not including contractors. We have 16 servers and over 20 desktops. We build an embedded computer for Airborne Law Enforcement. The product that we sell runs on Windows XP Embedded. That has been the point of infection/vulnerability each time the Conficker Virus has outbroken in our network since the embedded image we use is quite old, and vulnerable to viruses of all kinds. We've had a few occasions where the Conficker virus would infect these machines and when we connected them to the network they would start distributing it themselves.

The 3 times where we had an infection were resultant due to our extensive use of networking when we repair, update, or do installations to these embedded computers. All of our setups and etc are stored on the network. Plug a vulnerable machine in; if its infected BAM..infected network. Or vice versa if you have an infected network, these machines can be easily infected. Tracking down the infection goes from working with the network monitoring tools, finding out which physical machine is infected, and manually doing a scan of each machine in an attempt to clean it. Its tedious and the first time it happened we didn't have the proper resources in place and were inbetween switching AntiVirus providers.

---

### Post by chillicampari on 2010-02-28
Brandel, sure, and you'll mostly think think of the end user side and single use load and go. Which most people do (which is fine) but it was the result of some pretty fine work on the backend for making that easy for the end user to apply that patch. But outside of the home- everything from billing systems to modem banks to whatever had to be looked at and fixed if needed. While technically a lot of thing were not -hard- per se (at least the work I did), every single thing had to be inspected, and tested, usually at some god-awful hour after main, swing and night shifts had left.  

The news pumped up the scare factor for sure to get the eyeballs *but* there some real problems I saw for myself when test rollovers were done so I don't write the whole thing off as lolFUD. 'cause I was there. And that's all I'm gonna say about that. ;)

---

### Post by gn2 on 2010-02-28
The word FUD always makes me laugh.
Where I lve it means something completely different......

---

### Post by DoeRayMe on 2010-02-28
> **gn2 said:**
> The word FUD always makes me laugh.
Where I lve it means something completely different......

indeed it does :D

---

### Post by Mark Phelps on 2010-02-28
Just as a historical note ...

From what I recall long ago, FUD (fear, Uncertainty & Dread) was an acronym coined to describe a tactic that Big Blue (what IBM was called back then) to SCARE customers into staying loyal to them -- rather than "jumping ship" on going to some other mainframe computer supplier.

It was never intended to be definitive because it was just a scare tactic.  The vaguer it was, the harder it was to disprove and, consequently, the better it worked.

How the term is used today, I profess that I don't know.

---

### Post by samjh on 2010-02-28
The biggest FUD I remember was the rumour that the world end in 1999.

---

### Post by xpod on 2010-02-28
> **gn2 said:**
> The word FUD always makes me laugh.
Where I lve it means something completely different......

Aye, fer sure. My Boardband provider assured me it was 20Mb and what a right old load of fanny that turned out to be.

---

### Post by _elgato on 2010-02-28
I am not sure if this is not exactly FUD, but via Gizmodo appeared a review of Consumerist talking about how Best Buy scams people using its "optimization" service to make the buyer pay 50$ extra.

Consumerist ran a series of test to determine whether this optimization was real or not and it turned out to be not only a optimization but rather a pointless installation of apps that slow the computer.

Link: [http://consumerist.com/2010/01/consumerist-investigation-best-buy-optimization-is-a-big-stupid-annoying-waste-of-money.html](http://consumerist.com/2010/01/consumerist-investigation-best-buy-optimization-is-a-big-stupid-annoying-waste-of-money.html) :KS

---

### Post by lisati on 2010-02-28
> **xpod said:**
> Aye, fer sure. My Boardband provider assured me it was 20Mb and what a right old load of fanny that turned out to be.

Well, my ISP encourages people to install a broadband help assistant, which, of course only works on Windows. Assuming you've got a spare copy of Windows lurking around to run the thing and choose to try it, it brings up a web page which brings the process to a halt if you're using IE8, advising you to "upgrade" to IE6 or IE7. When you finally get past this hurdle, it does a number of checks, and if you've chosen to install AV software other than their preferred one, it complains that you don't have AV software installed. D'oh!

I think I'll stick with Ubuntu for my day-to-day stuff, thank you very much!

---

### Post by LinuxFanBoi on 2010-02-28
The FUD I'm hearing almost daily now is that the recent earthquakes in Haiti & Chile is proof that the movie 2012 is going to come true.

---

### Post by xpod on 2010-02-28
> **lisati said:**
> Well, my ISP encourages people to install a broadband help assistant, which, of course only works on Windows. Assuming you've got a spare copy of Windows lurking around to run the thing and choose to try it, it brings up a web page which brings the process to a halt if you're using IE8, advising you to "upgrade" to IE6 or IE7. When you finally get past this hurdle, it does a number of checks, and if you've chosen to install AV software other than their preferred one, it complains that you don't have AV software installed. D'oh!

I think I'll stick with Ubuntu for my day-to-day stuff, thank you very much!

Many providers here seem to supply some kind of installation CD that supposedly configures your connection and often install the same kind of crap you`re talking about, which typically makes getting online ever harder than it might be already.
I`m forever telling people if they have an an Ethernet cable to plug in from a router or modem then they usually dont need the installation CD`s and any junk it might come with....just plug that cable in.

To be fair to Virgin Media the speeds are actually ok and it was only when we first upgraded from 10Mb to 20Mb that they left something to be desired. 
As well as their own Wireless assistant though they do kindly provide some resource hogging security software and even their very own toolbar....which even if i *did* use Windows i wouldn`t thank you for.

---

### Post by lisati on 2010-02-28
> **LinuxFanBoi said:**
> The FUD I'm hearing almost daily now is that the recent earthquakes in Haiti & Chile is proof that the movie 2012 is going to come true.
And what happened to the tsunami I was meant to be aware of? While there might have been some risk in some parts of the world, much of its power would have dissipated by the time it found its way to the part of NZ I live in. (I live up a hill on the west of NZ, so much of the force would have dissipated by the time any tsunami found its way to the local harbour let alone to the street I live.)

---

### Post by xpod on 2010-02-28
> **lisati said:**
> And what happened to the tsunami I was meant to be aware of? While there might have been some risk in some parts of the world, much of its power would have dissipated by the time it found its way to the part of NZ I live in. (I live up a hill on the west of NZ, so much of the force would have dissipated by the time any tsunami found its way to the local harbour let alone to the street I live.)

If you do live in an "at risk" area then it`s better to be safe than sorry though eh.

---

### Post by Giant Speck on 2010-02-28
> **xpod said:**
> If you do live in an "at risk" area then it`s better to be safe than sorry though eh.

True.  It's just not something you want to risk after what happened in 2004.  I think people in living along the Pacific should feel grateful that they even have a tsunami warning system - something those living along the Indian Ocean didn't (and still don't, if I recall correctly).

---

