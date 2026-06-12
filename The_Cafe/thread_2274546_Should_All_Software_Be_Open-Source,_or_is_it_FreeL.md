---
title: "Should All Software Be Open-Source, or is it Free/Libre?"
date: 2015-04-20
forum: The Cafe
---

### Post by benrob0329 on 2015-04-20
Ok, so I can hardly make sense out of the political reasoning of the Free Software Foundation, but then there is the Open-Source Movement. But wait, then there's the neutral,  FLOSS and FOSS. So, here is my question to the UbuntuForums community, Should all software be free/libre (sold or free/$0.00), or is closed-source ok? If not, why?

I'll give my opinion first, I am somewhere in between free/libre and open-source, but not quite FLOSS or FOSS. somewhere like the Debian free definition.

[https://www.gnu.org/philosophy/free-sw.html](https://www.gnu.org/philosophy/free-sw.html)
[https://www.debian.org/intro/free](https://www.debian.org/intro/free)

---

### Post by grahammechanical on 2015-04-20
Me? I do not really care.

I use an awesome Linux distribution. And I have freedom of choice. I also allow freedom of choice to others. If some wants only Open Source software, then I will not force them to run proprietary code. Nor, will I prevent anyone from running proprietary code if that is their choice. Furthermore, I will not hinder those who want to purchase software. 

I have noticed several examples in human history where groups of people have demanded freedom or Liberty, as they call it, only to deny freedom to others.  The person who is intolerant is not free but is a slave.

Regards.

---

### Post by benrob0329 on 2015-04-20
You have a really good point, but their are some issues with a lot of closed-source software which should be taken care of, one of which is the spying problem. The NSA, 3rd parties, and others all like to get there hands on what you do and I can't stand it!

Google is another great example, thats why I use DuckDuckGo.

---

### Post by monkeybrain20122 on 2015-04-20
The FSF's position, as far as I understand is that it is OK to make money with software either by selling it or providing services (freedom doesn't imply free as beer)  but it is not OK to do so by restricting access to the source codes, since it is wrong to restrict access to knowledge. As an analogy, physical laws and mathematical theorems are in open domain. You are welcome to create a product and sell it for $$ with such knowledge or provide paid services based on it (e.g as a consultant or a math professor) but it is wrong to restrict access to such info behind a patent wall. It would be like having a patent on the quadratic formula, if you think it is far fetched, during the Renaissance competing mathematicians kept the formula to solve cubic equations a trade secret and charged money for access, look up names such as Cardano and Tartaglia.

The FSF's case is independent of security concerns, which is merely incidental to the core argument.

I don't understand the oft repeated line that it is a "freedom" to choose proprietary software. Freedom is implied in choice but some choices happen to be proprietary has nothing to do with freedom, and if it crowds out libre sofware then it hurts choice in the long run.

Mind you I am not a free software purist, or I won't use Ubuntu in the first place. :) I also use Media codecs, flash, skype and Chrome. But I understand where the FSF comes from and am quite sympathetic to its view. It is a laudable vision but it is not practical when you have to get certain things done. vision needs to be tempered by pragmatism but at the same time one should not dismiss a vision on pragmatic ground. There needs to be a balance.

---

### Post by benrob0329 on 2015-04-20
So here's a question, if someone wanted to sell a piece of software the wrote but didn't want other people to sell it, or give it away since it was his livelihood. The only way of doing that would be to do a closed-source license. Just throwing this out there. (I would choose free software over paid)

---

### Post by monkeybrain20122 on 2015-04-20
I can be wrong, but proprietary software that sold for substantial amount usually are developed by companies rather than lone developers. The developers usually give up their rights over the codes to the company as a condition for employment in the first place so your scenario is not typical.

---

### Post by TheFu on 2015-04-20
Some software should be paid.
Data formats should always be open.
Some software should be libre, open, available to be modified, improved, by anyone, and licensed to require other people to continue that.  That is the GPL.  GNU has a few different licenses that each have a specific purpose.  Any changes distributed must be shared under the same GPL.  If I make GPL code, then anyone who modifies it, must also release their code under the GPL too.

Closed/commercial software that uses proprietary data formats is the real issue to me.  It locks companies into a product and payments for as long as they need access to the data.
Closed/commercial software that uses open data formats is of no concern to me, provided those open formats can be validated for compliance.  MSFT's .doc files are well known closed formats that even MSFT cannot be consistent between different versions of their MS-Word software. 

F/LOSS is mostly about the freedom to modify the software to our needs - it is less about the price.  It is perfectly legal to charge for GNU software, but the first person who pays can push the exact same software to 1M websites so that everyone else can get it for free / $0.

Open Source doesn't necessarily mean "Libre" - there could be highly restrictive licenses attached - you can see, but cannot touch, for example.  That is slightly useful, but not nearly as useful as being able to modify the code for a specific need.  In a corporate environment, it is common to need modifications to software to aid integration between 2 different systems. In the old days with closed software, we'd pay each vendor $200K to add the interface to the other system ($400K total) ... just to have them communicate directly. Then we'd be charged 15% of that price annually for "support."  If the software was F/LOSS, an in-house developer would find where outputs and inputs for each system happens and she'd add an extra output to transmit the data to the other system over the network (or into an ESB - enterprise services bus) to forward the data to 1 or 50 other systems, as needed.  The input code would accept the output. That change could likely be made in about 2 weeks and no more costs would happen for a simple integration. Every 6-12 months, a recompile might be needed with a round of testing ... about 3 days of effort.   Additionally, the company might push the new capability back to the "upstream project" and everyone would get the new feature for free. With GPL software, that is optional. With AGPL software that sharing is mandatory.  

For home users, F/LOSS matters more about being able to not track license keys or online accounts.  Being able to clone an OS and not worry about some software license agreement and key management.  Ever had to call MSFT and beg for a key to be accepted after a HDD failure? I have.  Managing license keys sucks - for businesses it costs REAL money to track all that stuff.

I'm more about freedom. Freedom for a vendor to choose to sell or give away their code. Freedom from being locked into software to access my data. Freedom to swap programs to access the same data.  If the cost for the options is identical and the data can be accessed to the same level of compliance by all the options, then the merits of software will be the deciding factor.  If the prices are not the same, but everything else is - then the least expensive should win, right?

So - let's think about a few famous software license uses - 
* Facebook, the commercial company, is built on GNU licensed software. If the software wasn't free, they would never have been able to start up. The same applies to google, twitter, and pretty much all the other "cloud" providers. There is a loop-hole in this license. If the company never "distributes" the code, then they are not required to share updates/fixes back to the core project team.
* Apple, the commercial company, does not use GPL software.  They use BSD licensed software and didn't pay 1 penny back to those projects.  BSD license says - give us credit, but use this code anyway you like.  If apple gave 0.01% of their profits to the BSD coders, think of all the great BSD software we'd have for the world?  OTOH, when a software developer elects to use the BSD license (or similar MIT/Apache/Perl licenses), they are saying - enjoy using my code in good health for any purpose, including commercial, that you like. I don't want anything in return.  It is the programmer who choose that license - freedom.
* Because Google, Facebook, TiVo and other companies used GPL software, but didn't return any updates/fixes, GNU created a new license - the AGPL. This is designed to force companies who never distribute code (like a cloud service provider) is required to provide updates and fixes back to the community.  Code that is always improving is a good thing.

There are thousands of other licenses.  I've been releasing my code under the BSD license for a few years now, but I've worked in commercial software companies and we sold our software which had proprietary data formats - not really, but making any use of the data without out software is next to impossible.

The licenses that I avoid are closed/commercial - and shareware.  I'd rather have a $30 cost and 30 day trial than "shareware license." 

Sorry this is so long. Didn't review it for organization or flow.

---

### Post by benrob0329 on 2015-04-20
Both are very good points. Are there any software licenses that require credit to the original project?

---

### Post by TheFu on 2015-04-20
> **benrob0329 said:**
> Both are very good points. Are there any software licenses that require credit to the original project?

> There are thousands of other licenses.  You can create a license, I can create a license, your Mom can create a license, so there may be millions of licenses. 

What I'm getting at is that every different license may have a clause about giving credit (or not).  To know if  specific attribution is needed, you'd have to read them all - EVERY DIFFERENT VERSION too.

If you develop software or you are a company that makes software, knowing which licenses the code your development team uses is absolutely critical. I've worked places that wouldn't use any non-commercial software over fears of being sued. They were a "big fish" and being wrongfully sued all the time. Settlement was their method, just to stay out of the papers even when they did nothing wrong. I was involved on the corporate side in a copyright claim - they settled for over $200K over 1 image even with the proof that an in-house artist had created the image 100% independently.

 I've worked other places that only used F/LOSS software, didn't modify it and preferred any of the GPL/LGPL/AGPL/MIT/BSD/Apache licenses because we didn't ship anything with software - zero risk in using it.  And I've worked places that would only build on top of non-GPL software that were compatible with the BSD license. I had to train my team of developers about which licenses for software we could use and teach them to ask before pulling/copying any software off the internet or out of books. Example code in books is copyrighted - cannot be used. It was unlikely we'd ever get caught, but we wanted to follow the actual license agreements. Most of my team just asked if "software X" could be used and I'd get stuck doing the research.  Almost got screwed by RMS (Richard Stallman) when a noob developer outside our company gave his code to the FSF. RMS deemed it to be GPL and that screwed the 30 companies using it as "public domain" prior to that point.  Public Domain is not a safe license to use if you are a company. Almost everyone on UNIX/Linux DB systems used that code to link proprietary DB drivers. Those aren't compatible with the GPL and would force Oracle/Microsoft/Informix/IBM/Sybase and about 30 other companies to GPL license their DBMS drivers. For a few months, we all got scared and tried to convince RMS this driver manager needed to be LGPL, which solved everything.  However, in the meantime, one of the commercial driver vendors, Openlink, decided they couldn't wait, so they wrote a replacement DM and released it under the BSD license.  My company immediately switched to the non-LGPL driver manager and I stopped contributing to unixODBC project - trivial as my contributions were.  You can look up these companies and probably find the arguments about this on usenet. [http://www.unixodbc.org/](http://www.unixodbc.org/) - look at the lgpl comment there. ;)

---

### Post by fkkroundabout on 2015-04-22
i found the similarity monkeybrain made about mathematical formulae and source code very curious, and a good point

i also found thefu's comparison of the level of contribution to linux and to BSD a good point, as there is dramatically obvious differences in their adoption and development rates

unfortunately i don't have many independent thoughts on the topic

i do vaguely remember, when watching videos of linus torvald's speak, that i think he said something along the lines of "if you give businesses too much freedom, they get greedy"

---

### Post by buzzingrobot on 2015-04-22
As with all things, the person who makes a 'thing' gets to decide who else can see it, use it, copy it, distribute it, market it, etc.  All rights in a 'thing' that I make are initially mine and only mine.  No one else has any of those rights unless I transfer one, some, or all of them.

So, it's as equally virtuous to decide to write closed code as it is to write open code. The two approaches obviously have different effects and impacts, but those are not ethical matters.

The problem with zealotry about this issue is, just as it is elsewhere, it's hard to escape the impression that some folks are so convinced of their own ethical wisdom that they are willing to impose their own choices on everyone, if given enough power.

---

### Post by user1397 on 2015-04-22
> **buzzingrobot said:**
> As with all things, the person who makes a 'thing' gets to decide who else can see it, use it, copy it, distribute it, market it, etc.  All rights in a 'thing' that I make are initially mine and only mine.  No one else has any of those rights unless I transfer one, some, or all of them.

So, it's as equally virtuous to decide to write closed code as it is to write open code. The two approaches obviously have different effects and impacts, but those are not ethical matters.

The problem with zealotry about this issue is, just as it is elsewhere, it's hard to escape the impression that some folks are so convinced of their own ethical wisdom that they are willing to impose their own choices on everyone, if given enough power.
I wouldn't say that these are not ethical matters.  After the Snowden revelation, we know for example, that many companies like Microsoft, Facebook, Apple, and Google were forced to let the NSA put code through backdoors in their code.  One could argue that if closed-source software were illegal (as a crazy example), that this could never have happened in the first place, for obvious reasons.

It's a great debate, and one that I think won't have a conclusion for a long time.  But to say this doesn't concern ethics, is a bit odd considering current events and the seemingly pervasive, global, government-spying phenomenon we face.

---

### Post by buzzingrobot on 2015-04-22
> **ubuntuman001 said:**
> I wouldn't say that these are not ethical matters.  After the Snowden revelation, we know for example, that many companies like Microsoft, Facebook, Apple, and Google were forced to let the NSA put code through backdoors in their code.  One could argue that if closed-source software were illegal (as a crazy example), that this could never have happened in the first place, for obvious reasons.

It's a great debate, and one that I think won't have a conclusion for a long time.  But to say this doesn't concern ethics, is a bit odd considering current events and the seemingly pervasive, global, government-spying phenomenon we face.

The incidents Snowden says happened could have happened with closed or open code. Some like to imagine that open code is a panacea to ward off all kinds of things.  It isn't, if for no other reason than that billions of lines of code exist and no organized effort exists to vet them, and probably can't exist.

My broader point is there are many reasons why I might release code as open or closed. None of them are ethical in nature.

---

### Post by monkeybrain20122 on 2015-04-22
> **buzzingrobot said:**
> As with all things, the person who makes a 'thing' gets to decide who else can see it, use it, copy it, distribute it, market it, etc.  All rights in a 'thing' that I make are initially mine and only mine.  No one else has any of those rights unless I transfer one, some, or all of them.
.

Well unless you make your creation out of thin air you also owe it to others. It will be an ethical issue if you take and don't give back. Now it may be your right to do certain things because of the way the law is created by lawyers (e.g to sue someone over using a loop for patent infringement, or to outsource manufacturing jobs to China where you can get away with sweatshop condition) but these are still rotten things to do. So there is ethics involved. On the other hand in the real world we usually have a hierarchy of moral principles, some are taken more seriously and others less. But still there is an ethical dimension.

"Intellectual property right" is a legal fiction. The reason why it exists is the (IMO mistaken) belief that it can lead to greater social good such as encouraging innovations. But you have no more natural right to sue people for using your source codes than Renaissance mathematicians had to demand payment for accessing their secrete formulae for solving the cubic.

---

### Post by monkeybrain20122 on 2015-04-22
> **buzzingrobot said:**
> The incidents Snowden says happened could have happened with closed or open code. Some like to imagine that open code is a panacea to ward off all kinds of things.  It isn't, if for no other reason than that billions of lines of code exist and no organized effort exists to vet them, and probably can't exist.


Perhaps. But how about the analogy of selling processed food without disclosing the ingredients? For all you know my "delicious secrete sauce" could be a health hazard. Should the law allow it? So open code may not be a panacea but at least in principle you can find out he ingredients if inclined.

Edited: Just to be clear, I don't insist that all software has to be open unless there are some compelling reasons (security, or some kind of antitrust considerations etc), but I don't agree that there is no ethics involved (even though it may be far away from the top on the hierarchy of ethical principles). However, I do think that standards have to be open. So e.g MSOffice formats are unacceptable for document standard.

---

### Post by benrob0329 on 2015-04-22
> **monkeybrain20122 said:**
> However, I do think that standards have to be open...

I agry.
(Grr, spell check isn't working!)

---

### Post by 1clue on 2015-04-22
If anyone feels there is an ethical problem with proprietary/nonfree software then they should really question whether they want to run any variant of Ubuntu.  Ubuntu is produced by Canonical, which is a for-profit commercial company which sells proprietary software.

There is nothing wrong with free software, and there is nothing wrong with commercial software.  Each has its place, each can be better for a particular use, and each has advantages and disadvantages in terms of the qualities of the software produced.

IMO it's better to ignore the politics of the various groups and look at these things:
[LIST=1]
[*]The qualities of the software.
[*]The quality of the documentation.
[*]The license.
[*]The community.
[*]The suitability for your specific purpose.
[*]The interoperability with other required components of your larger system.
[*]The maintainability and response time to security/stability issues.
[/LIST]

IMO there is no reason why free and proprietary software cannot coexist on the same system.  There may be a licensing issue if the two are linked together, but usually there is a way to do things without breaking any commonly used licenses.

The world is a big place, but when any group insists that everyone else must play by some specific set of rules, the world suddenly shrinks to the point where the Dictator of Rules no longer fits.  I take issue with commercial organizations which insist I must not use Open Source.  I take equal issue with Open Source fanatics who insist I must not use proprietary software.  Do your own thing, but get off my lawn.  If you're going to break a license agreement then don't brag about it to me, I have no tolerance for that either.

---

### Post by flaymond on 2015-04-23
In my opinion, not every software should be libre/free and not all of them should be closed-source software. Spying issue is indeed the most hot problem for closed-source software, increasing paranoia. However, closed-source software is one of the main source, for developers to get money, at least to buy a cup of coffee. FOSS is good, for learners, developers and programmers, but might  not beneficial for others, especially a commercial company. Well, I support FOSS, I cannot view the source code of encryption program in repositories legally if these softwares, not follow the standard FOSS rules. :D

---

### Post by 1clue on 2015-04-23
IMO the spying thing is something each user needs to understand and appreciate, and know how to minimize risk.  You need to do that with FOSS too, because you may get a deliberately altered build or there may be a vulnerability that was not published, but is exploited.

You may think of your phones and tablets and computers, but did you think of your TV and your blu-ray?  Your home monitoring system?  Wireless cameras, baby monitors?  You're not going to replace all the software with something you personally have reviewed and trust.  Your car might  connect to your wifi when you get close to home, what about all the systems in that?  Modern cars have wifi and bluetooth, and according to Ford they have or will have up to 20 ip addresses, and very probably will be able to connect to cellular Internet whether you have access to the connection or not.  They can also have the automotive equivalent of an aircraft's black box.  I know years ago a friend told me he took his BMW to his mechanic and the mechanic bitched him about for how he was driving it.  That was in the late 90s.

So with all that into account, I think if you're worried about spying you should put an outbound firewall filter, and log each device you don't trust.

In any case I don't see how free/proprietary plays into the spying aspect.  Some pretty common Linux exploits install open source chat/newsgroup software which monitors certain channels for updates, or posts to them.  

It's my intent to set up a very good firewall/UTM and then block everything outbound, and see what breaks.  I'll log all that and then go device by device to fix what's broken once I understand it and have some reasonable level of trust.  Part of that is having a trusted network which has no unknowns, and a regular home network which has wifi and all the tcp/ip-wielding devices in my home.  Last time I checked our two-person home had 37 devices, you may want to check your dhcp reservations on your router.  You may be surprised.

---

