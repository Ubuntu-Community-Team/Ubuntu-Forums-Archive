---
title: "Reducing US's deficit with Linux?"
date: 2011-12-23
forum: The Cafe
---

### Post by kalfusisagod on 2011-12-23
Hello, 

Just a quick question. Do you think that if the US government made a full transition to any distro (or a custom build) of Linux (doesn't have to be Ubuntu), that it would reduce cost in the long run and lower the country's deficit? I've been reading the forums on here and seen that the DoD has made a few changes to RHEL and other open source solutions. I work for the DoD and can tell you that every desktop and laptop we use has Windows on it. Seems to me that the DoD is paying billions to Microsoft for licenses and support including all the MS Office 2007 suites. There are some custom Linux servers and platforms, but not nearly as many Windows. I know it's a drop in the bucket when you're talking about billions when referring to the country's deficit. 

I've been doing some research on these forums and found out other countries and even many companies (mostly US based) have made a transition to some sort of Linux OS; although it might not be a full transition. 

Furthermore, reading on here that Linux lacks in computer gaming (FPSs/DirectX), iTunes support, and Netflix is something the government doesn't need on their computers. The main requirements that the DoD and the US government need (in my eyes) is a secure multi-user computer environment that is reliable. Both Linux and Windows fit the bill, although Windows wasn't a multi-user environment to start out with and costs a lot for their intellectual property. One thing that I am going to stress is that we need a 2 factor authentication system (you need a DoD smart card and the smart card's PIN to login to the domain of our systems). I've heard that Linux supports this, but there is a complicated workaround for this. Also, one thing that Microsoft uses is Sharepoint. It's like a LAN web portal where you can upload, view, and modify documents (by having only **one **person checking out and modifying a document at a time) their documents. Does Linux have some sort of Sharepoint collaborative solution?

I understand that some Linux distros do offer some kind of buisness support like Ubuntu and RHEL, but the DoD is also paying Microsoft for their techs to work on our systems. Support will be a big issue when switching over to Linux. I mean, I don't expect the transition to happen overnight, but maybe put  some Linux supporting lobbyist to plant some seeds in congressman's  ears. I think if the US goverment pushes to get Linux into their computers, it will put Linux in more of a spot light and push other companies to support Linux (like Netflix dropping Silverlight and iTunes making a Linux binary.) It'll be a win win for both the government and Linux.

I've been using Linux on and off for about 10 years now. Right now I have a Ubuntu 10.04 VM hosted on my Win7 box learning the command line. I was hoping for some opinions on the push to save taxpayer money with a transition to some sort of Linux distro. Any ideas?

---

### Post by CharlesA on 2011-12-23
That would be an insane migration. I would think that the training alone would make it not worthwhile, not to mention the problem of specialized applications.

---

### Post by KL_72_TR on 2011-12-23
Somebody is already doing what you are saying:
[http://ostatic.com/blog/russian-government-will-transition-to-linux-by-2015](http://ostatic.com/blog/russian-government-will-transition-to-linux-by-2015)
Also some 'good thinking' people have done something:
[http://ostatic.com/blog/the-u-s-federal-government-open-sources-two-useful-tools](http://ostatic.com/blog/the-u-s-federal-government-open-sources-two-useful-tools)
[http://ostatic.com/blog/despite-the-u-s-cios-exit-open-source-is-entrenched-in-the-federal-government](http://ostatic.com/blog/despite-the-u-s-cios-exit-open-source-is-entrenched-in-the-federal-government)

---

### Post by |{urse on 2011-12-23
They already have/are.

---

### Post by KL_72_TR on 2011-12-23
> **CharlesA said:**
> That would be an insane migration. I would think that the training alone would make it not worthwhile, not to mention the problem of specialized applications.
This is nothing compared to 'Landing a man on the moon and returning him safely to the Earth'

---

### Post by collisionystm on 2011-12-23
The whole world is moving to OpenSource. It just makes sense. 

It does not mean that all software will be given away for free, but it will mean a greater majority of the world will have the opportunity to build programs, computers, games...etc. For the past couple decades, Microsoft and Apple have been the leaders and the computer science industry is becoming empty. There is no room for creativity in a world that is controlled that way. Linux / Opensource in general is paving the way for a new generation of computing. Its exciting.

---

### Post by kalfusisagod on 2011-12-23
Is Linux really that hard to use? Training, yes maybe like a couple day thing to the end user. But I don't think training will be the actual downfall of migrating. The sysadmins will probably be the ones with the blunt of the work *during *the migration. Also, I'm sure the sysadmins can lock it down to where the end user can't really break anything. I'm sure the end user will not be the ones installing Linux themselves.  If I can use Linux, anyone can :) As far as specialized applications, the main ones we use are email, document suites, and being able to scan/print to a networked all in one. The only specialized software I think would be natively supporting smart cards within the OS or through the middle ware (currently ActivClient for the DoD). The other thing we need is a collaborative portal like SharePoint. About 60 percent of the Internet is ran on a Linux box for christ sake, which is a huge collaboration portal. All we need is a portal like solution for a LAN made for Linux if there isn't one already. On the other hand, there are a few workstations that do specialized things, but let's have the majority running Linux and the other "applications that ONLY run on Windows" the other 10 percent, instead of what it is now. I'm not a die hard Linux fan boy, but I think in the long run it would save us some money to put into other good use.

---

### Post by JDShu on 2011-12-23
The United States government has separated IT systems for confidentiality reasons. What each place uses is up to the IT director of that particular bureau or office to decide. Nobody in the government can really tell everybody else to use a particular system.

---

### Post by 3Miro on 2011-12-23
Even if everything moves to FOSS, this would be only a small dent in the whole deficit thing. Every bit helps and it would be good if they do, but it wouldn't solve all or even many of the issues.

Don't get me wrong, they should move to FOSS.

---

### Post by Paqman on 2011-12-24
> **KL_72_TR said:**
> This is nothing compared to 'Landing a man on the moon and returning him safely to the Earth'

It'd probably be comparable. The Apollo Programme involved 400,000 people and took about 9 years to get to the moon landing. The US federal government has 2 million employees and the migration would take at least that long between initial studies and the first deployments.

Costs? I'd hate to say, but initially they'd be high. Dozens (hundreds? thousands?) of business systems and pieces of software would have to be evaluated for impact and new plans drawn up. That would probably mean lots of new hardware, new processes and lots and lots of new training. Plenty of the current vendors of software and support would fight tooth and nail and you'd be likely to get compromise solutions implemented across the board. It could (at least initially) be a very expensive project.

---

### Post by Paqman on 2011-12-24
> **kalfusisagod said:**
> Is Linux really that hard to use? Training, yes maybe like a couple day thing to the end user. But I don't think training will be the actual downfall of migrating. 

Have you actually got any experience in migrating a business from one type of software to another? Training is a very big deal. Remember that some people find *any* kind of software difficult to use, and need to be shown specifically how to do their job.

---

### Post by KL_72_TR on 2011-12-24
> **Paqman said:**
> It'd probably be comparable. The Apollo Programme involved 400,000 people and took about 9 years to get to the moon landing. The US federal government has 2 million employees and the migration would take at least that long between initial studies and the first deployments.
Thinking this way, you are right. But the reality is completely different. Apollo Program was an experiment and the experiment is the most difficult part in any activity. On the other hand: Linux, migration and training are things that have already been tested. The only thing that scares people here is the number - 2 million employees. It is only a number! 

> **Paqman said:**
> Costs? I'd hate to say, but initially they'd be high. Dozens (hundreds? thousands?) of business systems and pieces of software would have to be evaluated for impact and new plans drawn up. That would probably mean lots of new hardware, new processes and lots and lots of new training. Plenty of the current vendors of software and support would fight tooth and nail and you'd be likely to get compromise solutions implemented across the board. It could (at least initially) be a very expensive project.
I'd hate to say it... But this and much worse are already happening with Microsoft in their hands :-(

---

### Post by Paqman on 2011-12-24
> **KL_72_TR said:**
> 
I'd hate to say it... But this and much worse are already happening with Microsoft in their hands :-(

Don't get me wrong, I'm not saying that the stranglehold Microsoft has on government IT is a good thing. I just think a lot of Linux fans vastly underestimate how difficult migrating a big organisation to any new OS can be, and tend to overestimate the benefits of Linux being that OS. Historical case studies have shown plenty of big Linux migrations that have been a costly flop, for a variety of reasons.

---

### Post by Paddy Landau on 2011-12-24
As has already been hinted at, I have seen several government organisations and large businesses throughout the world converting, or already converted, to FOSS. I believe the French government is seriously looking at it now.

The training costs are needed anyway -- imagine the cost of retraining when Windows 8 comes out in a few months! You might as well retrain in Ubuntu (or some other distribution). The savings on the licenses will pay for themselves probably in the first two years, as there will be no need for massive hardware upgrades.

---

### Post by bouncingwilf on 2011-12-24
Seems to me that this may be counter-productive as regards reducing the US deficit. Microsoft is US based so that profit revenues flow inwards - i.e a foreign currency earner. The internal US market is effectively neutral and so any trend to move away from MS (or Apple) products would, if duplicated world-wide would likely result in an increase in the US deficit.

Sorry my friends across the pond - I'm still not going to buy their products - I prefer Linux.

Bouncingwilf.

---

### Post by KL_72_TR on 2011-12-24
> **Paqman said:**
> Don't get me wrong, I'm not saying that the stranglehold Microsoft has on government IT is a good thing. I just think a lot of Linux fans vastly underestimate how difficult migrating a big organisation to any new OS can be, and tend to overestimate the benefits of Linux being that OS. Historical case studies have shown plenty of big Linux migrations that have been a costly flop, for a variety of reasons.
You are right. I'm not getting you wrong at all. It was my mistake not to make my self clear. I meant they have done all the calculations and they have done all the experiments yet this process is still in hold. Why? They have all the potential to reduce, minimize any kind of risk. One must not live in fear. In the beginning losses are inevitable, but reward and gain come along the way.

---

### Post by Old_Grey_Wolf on 2011-12-24
> **kl_72_tr said:**
> somebody is already doing what you are saying:
[http://ostatic.com/blog/russian-government-will-transition-to-linux-by-2015](http://ostatic.com/blog/russian-government-will-transition-to-linux-by-2015)
also some 'good thinking' people have done something:
[http://ostatic.com/blog/the-u-s-federal-government-open-sources-two-useful-tools](http://ostatic.com/blog/the-u-s-federal-government-open-sources-two-useful-tools)
[http://ostatic.com/blog/despite-the-u-s-cios-exit-open-source-is-entrenched-in-the-federal-government](http://ostatic.com/blog/despite-the-u-s-cios-exit-open-source-is-entrenched-in-the-federal-government)

+1

It appears to be in the works; however, I don't know how much of a dent it will make in the deficit. I also found this [http://www.cio.gov/pages.cfm/page/FDCCI](http://www.cio.gov/pages.cfm/page/FDCCI). Although FDCCI is not based totally on FOSS or Linux, FOSS and Linux both have a strong position in cloud computing, vertualization, and data centers.

:)

---

### Post by WinterMadness on 2011-12-24
i really think training people on linux would be hard, aside from the i.t departments... ive worked for the federal government as a programmer btw

---

### Post by kalfusisagod on 2011-12-24
Like some stated earlier, when another upgrade to Windows comes out we'll just have to migrate again. Currently we're migrating to Windows 7 from XP! That's not DoD wide but that's my organization and I could see why they did that [Insert Vista Joke Here]. Anyway upgrading to a new OS will happen every few years in a big organization. Training will happen every few years. If a Linux distro is up to par, then it may work. I'm in the IT section (not doing the actual migration to 7) and hear all the behind the scenes of what it takes to migrate. It'll be hard, but it may work. As far as MS being a US based company, yeah they'll lose a huge contract but I can guarantee that 8 out of 10 computer in Best Buy, OfficeMax, MediaMarkt, Saturn (German Based Electronic stores) have Windows on them with the other 2 being OSX. Microsoft and OSX have a world dominance. Losing the Govt contract will be a drop in the bucket, but also along with the deficit. But I think if the US govt did have a Linux contract, I think that would put Linux in more of the spot light which in turn would push hardware and software developers to be more Linux friendly.

---

### Post by Quadunit404 on 2011-12-25
I believe large parts of the government already use Linux. I know the FAA switched to RHEL in 2006, the White House website (among other US Federal websites) runs on a Drupal + LAMP combo, among other cases like that (all the distros are RHEL.)

---

