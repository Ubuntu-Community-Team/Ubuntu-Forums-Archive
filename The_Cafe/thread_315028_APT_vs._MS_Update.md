---
title: "APT vs. MS Update"
date: 2006-12-08
forum: The Cafe
---

### Post by Hendrixski on 2006-12-08
Here's a question that should spark a lot of interesting debate: how does apt (and synaptic) compare to Microsoft Download center and Windows update?

How would it compare if Apt could support monetary transactions? (which brings up the debate of what if a business may need it to do so, could it be done, and how?)

---

### Post by aysiu on 2006-12-08
Let's see.

With Apt, you can update your entire system, including all the applications you have installed.

With Windows Update, you can update only the OS and Internet Explorer and Outlook Express.

What's to compare?

By the way, there is something similar to Apt called CNR--it's available for Linspire and Freespire and allows business transactions to work with the package manager.

---

### Post by taurus on 2006-12-08
Move to Cafe (and I can smell a flamewar coming)...

---

### Post by Hendrixski on 2006-12-08
> **taurus said:**
> Move to Cafe (and I can smell a flamewar coming)...

Please no flaming! Just facts, I need to discuss this in a business setting soon, I just want more ammunition to support the use of apt in the business world.

[QUOTE=aysiu]
there is something similar to Apt called CNR--it's available for Linspire and Freespire and allows business transactions to work with the package manager[/Quote]
That works the same I assume?  Do you know anyone who uses it?

---

### Post by aysiu on 2006-12-08
> **Hendrixski said:**
> Please no flaming! Just facts, I need to discuss this in a business setting soon, I just want more ammunition to support the use of apt in the business world.


That works the same I assume?  Do you know anyone who uses it?
I don't think Ubuntu's implementation of Apt currently supports business transactions the way CNR does for Linspire.

Can it, technologically speaking? It's probably not that difficult for the devs to implement.

Will it? Probably not. Ubuntu's commitment is to free software. Part of that "free" is freedom, but I think it also applies to cost.

You could always propose the business go with Freespire or Linspire.

---

### Post by Brunellus on 2006-12-08
> **aysiu said:**
> I don't think Ubuntu's implementation of Apt currently supports business transactions the way CNR does for Linspire.

Can it, technologically speaking? It's probably not that difficult for the devs to implement.

Will it? Probably not. Ubuntu's commitment is to free software. Part of that "free" is freedom, but I think it also applies to cost.

You could always propose the business go with Freespire or Linspire.
well, commercial vendors could still offer their own apt repositories of commercial software, and charge for access to the same, theoretically.  

Just to keep things safe, though, they'd probably have to do what Opera does and have all the dependencies linked into their app.  The downloads would be pretty hefty!

---

### Post by Klaidas on 2006-12-08
APT Update vs MS Update - I think APT's better.
I still voted "No" on the poll though - that was a different question than in the thread title.

---

### Post by aysiu on 2006-12-08
> **Brunellus said:**
> well, commercial vendors could still offer their own apt repositories of commercial software, and charge for access to the same, theoretically.  

Just to keep things safe, though, they'd probably have to do what Opera does and have all the dependencies linked into their app.  The downloads would be pretty hefty!
There would have to be some way to charge people, though--some kind of account creation and/or credit card transaction modification to Apt.

---

### Post by Hendrixski on 2006-12-08
Wow, did not know Linspire was still around.  I remember when they tried to sell Lindows at Wal*Mart.

CNR looks like a commercial solution for businesses who would want to sell for LINUX. You can buy things like StarOffice, and win4lin. I wonder if something like this would encourage more companies to write software for LINUX if they know they could sell it?

How new/old is CNR?  Is it getting any attention from the wider Linux community?

---

### Post by aysiu on 2006-12-08
Back in March, Kevin Carmony from Linspire came on the forums and created [this poll](http://ubuntuforums.org/showthread.php?t=138616), asking Ubuntu users if they'd use or recommend a Ubuntu-ported CNR.

Based on the results, Linspire decided it wouldn't be porting CNR to Ubuntu at this time, but it did recently [open source CNR](http://www.osweekly.com/index.php?option=com_content&task=view&id=2344&Itemid=468), so if someone did want to port it to Ubuntu, it probably could be done... not sure how well it would integrate, though. There are probably differences in the file structure that might screw up installations through CNR.

---

### Post by Brunellus on 2006-12-08
> **aysiu said:**
> Back in March, Kevin Carmony from Linspire came on the forums and created [this poll](http://ubuntuforums.org/showthread.php?t=138616), asking Ubuntu users if they'd use or recommend a Ubuntu-ported CNR.

Based on the results, Linspire decided it wouldn't be porting CNR to Ubuntu at this time, but it did recently [open source CNR](http://www.osweekly.com/index.php?option=com_content&task=view&id=2344&Itemid=468), so if someone did want to port it to Ubuntu, it probably could be done... not sure how well it would integrate, though. There are probably differences in the file structure that might screw up installations through CNR.
somewhat off-topic:  I have always thought that KC was enormously brave to wade into the ubuntuforums and duke it out with the regulars here over CNR.  

I note that sabdfl doesn't hang out here, but KC does/did.

---

### Post by aysiu on 2006-12-08
> **Brunellus said:**
> somewhat off-topic:  I have always thought that KC was enormously brave to wade into the ubuntuforums and duke it out with the regulars here over CNR.  

I note that sabdfl doesn't hang out here, but KC does/did.
Yes, and I think Mr. Carmony handled the stress of it quite well and professionally. A lot of people tried to make it into a big flameware, but he didn't take the bait.

I've always had an enormous amount of respect for Linspire, even though I don't use it.

---

### Post by Brunellus on 2006-12-08
> **aysiu said:**
> Yes, and I think Mr. Carmony handled the stress of it quite well and professionally. A lot of people tried to make it into a big flameware, but he didn't take the bait.

I've always had an enormous amount of respect for Linspire, even though I don't use it.
Linspire is a "neither fish nor fowl" distribution to me.  And the "root by default...all the time" install was frankly terrifying.

---

### Post by Hendrixski on 2006-12-08
I think that's an interesting poll Mr Carmony had.  Most desktop Linux users were satisfied with the choices they have from non-proprietary apt repositories.  So even if there were commercial options in apt, they would have a hard time competing.

Do any big businesses actually use linspire?  Has Red Hat (which does have a few big named customers) thought of a commercial yum portal?

---

### Post by grte on 2006-12-08
Would it be possible to use, not necessarily apt itself, but something like apt, which would allow  you to pay for an app in a similar manner to the way itunes lets you buy a song?

---

### Post by Brunellus on 2006-12-08
> **grte said:**
> Would it be possible to use, not necessarily apt itself, but something like apt, which would allow  you to pay for an app in a similar manner to the way itunes lets you buy a song?
that'd be CNR.

---

### Post by lyceum on 2006-12-08
> **Brunellus said:**
> well, commercial vendors could still offer their own apt repositories of commercial software, and charge for access to the same, theoretically.  

Just to keep things safe, though, they'd probably have to do what Opera does and have all the dependencies linked into their app.  The downloads would be pretty hefty!

If I were to start a business like this I would create a gui, like Automatix2. When you pay it would allow you to apt-get without the termanal. I would also use credits, like allofmp3.com does. You give them money and then use the money to buy what you need. 

my 2 cents.

---

### Post by earobinson on 2006-12-08
the best way to do this would be to have a part of the program that the user would download and install from your site that is needed to run it, the deb file would install the new repos that would update the program as long as you had the little bit they installd originaly off your comptuer

---

### Post by Hendrixski on 2006-12-08
> **earobinson said:**
> the best way to do this would be to have a part of the program that the user would download and install from your site that is needed to run it, the deb file would install the new repos that would update the program as long as you had the little bit they installd originaly off your comptuer

That's a good idea.  So then the part you installed would contain the password info needed to get the product from the apt repository, and subsequent updates...  not bad.  so now.. What benefits would that give (compared to just downloading the software  off a website) to companies who want to expand to the Linux market?

---

### Post by Hendrixski on 2006-12-08
> **Brunellus said:**
> that'd be CNR.

Also, is there a way to download CNR outside of downloading linspire? I hope it's not "bundled".

---

### Post by Brunellus on 2006-12-08
> **Hendrixski said:**
> That's a good idea.  So then the part you installed would contain the password info needed to get the product from the apt repository, and subsequent updates...  not bad.  so now.. What benefits would that give (compared to just downloading the software  off a website) to companies who want to expand to the Linux market?
all the usual upsides of centralized repositories:  instant notification of updates, easy roll-out of updates, and graceful updgrades from one version to the next.

---

### Post by Brunellus on 2006-12-08
> **Hendrixski said:**
> Also, is there a way to download CNR outside of downloading linspire? I hope it's not "bundled".
the source, as far as I know, is available.  I don't think anybody but the Freespire types package it, though.

---

### Post by BWF89 on 2006-12-08
Apt-get (with a little help from Synaptic) could be used for buying software. Linspire/Freespire already lets you but software from their CNR service.

---

### Post by dbbolton on 2006-12-08
ms update is a joke. i can't recall how many times the "updating" process "failed" to download and/or install anything. not to mention the annoying and perpetual "would you like to reboot now?" pop up.

aysiu said it best. ms update is just much more limited than apt.

---

### Post by hkgonra on 2006-12-08
> **aysiu said:**
> Let's see.

With Apt, you can update your entire system, including all the applications you have installed.

With Windows Update, you can update only the OS and Internet Explorer and Outlook Express.

What's to compare?



Not exactly right but close. 
MSupdate updates Windows , and everything that comes with it , plus MS Office and I think other MS apps if you have them installed. 
Granted apt is still better.

---

### Post by Hendrixski on 2006-12-08
> **hkgonra said:**
> Not exactly right but close. 
MSupdate updates Windows , and everything that comes with it , plus MS Office and I think other MS apps if you have them installed. 
Granted apt is still better.

So apt can support non-open-source programs, but doesn't.  and MS update can support non-MS programs, but doesn't. Both of them would be better if they weren't trying to alienate the other guy.

---

### Post by aysiu on 2006-12-08
> **Hendrixski said:**
> So apt can support non-open-source programs, but doesn't.  and MS update can support non-MS programs, but doesn't. Both of them would be better if they weren't trying to alienate the other guy.
Actually, Apt *does* support closed source programs. The entire Multiverse repositories is almost all closed source.

What Apt *doesn't* support is doing online transactions (handling payment). As far as I know, neither does Windows Update, though.

---

### Post by usernamebob on 2006-12-09
my 2c..

I think having a program similar to apt that allowed non-free software to be bought for linux would be great. As much as I'd prefer to use an open source alternative when there is one.. sometimes there just isn't.. and honestly I think it'd be great if the companies currently selling software on windows could sell it on linux. The Foss community has come further than anyone could have predicted.. and it's amazing to think that we can have full a full workable open source operating system that rivals windows which is made by a company that has near unlimited finnancial resources to throw at it's development. But there has to come a point where we run out of people who are willing to create this software without finnancial backing.

Of course linux does have finnancial backing in the form of companies like Ibm/redhat/novell/whoever else, But the majority of development comming from these sources is never likely to be primarily aimed at the desktop market (imho).. 

I think this is part of the reason why linux has never realy managed to develope great support for things like games.. because most linux users are so adverse to buying a program that when companies have gone out on a limb and made linux version of games.. barley anyone has bought them (infact there was a company devoted to making linux ports of games for the gamming developers.. which went out of buisiness due to noone buying (can't remember name..))

anyway.. I proably didn't say anything usefull.. but oh well

---

### Post by aysiu on 2006-12-09
> **usernamebob said:**
> 
I think having a program similar to apt that allowed non-free software to be bought for linux would be great. It already exists. It's called CNR.

---

### Post by prizrak on 2006-12-10
It's pretty much gonna be a front end for apt with ability to charge. RedHat does do that with it's Yum system, you subscribe to updates and other goodies that can be gotten from their repositories. As for economic viability, Valve seems to be doing quite well with their Steam system ;)

---

### Post by Hendrixski on 2006-12-12
What exactly is Valve's stream system?  Google wasn't very informative about this.

---

### Post by prizrak on 2006-12-12
> **Hendrixski said:**
> What exactly is Valve's stream system?  Google wasn't very informative about this.

Instead of buying a game disk at the store you buy the game online and download it to your computer. Every time the game is started it will download all the updates and such, also keeps your info in case you need to install on a diff comp (won't work on the old one anymore).

---

### Post by Hendrixski on 2006-12-12
As much as I think games are a waste of time, I do have to admit they come up with some cutting edge stuff sometimes.

I hope this thread won't die.  What about the new MS Installer, version 4.0 that's going to come with Vista?  Anybody know how that might compare?

---

### Post by Brunellus on 2006-12-13
.msi will be as impossible as ever to implement in WINE.  *sigh*

also:  Steam is only doing, in a walled garden, what apt has been doing for far longer.

---

### Post by sailingboarder on 2006-12-13
i think apt would work well with comercial software
for now, the idea of paying for then download a program that will allow apt to download full program is a good idea, but transactions built into apt would be best(perhaps in feisty?)
if comercial programs were more widely avalible for linux, then more people would consider leaving windows

---

### Post by SunnyRabbiera on 2006-12-13
Apt has incredible system wide updating, MS update only gives you a few beans that really dont help much.
I really wish windows did have something like synaptic, heck any OS would be great with synaptic or some varient of it.
I like synaptic, it is very easy to use and operate and it does a good job at installing things.

---

