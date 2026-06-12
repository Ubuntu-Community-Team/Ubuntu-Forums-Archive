---
title: "Dell/Ubuntu: Abandoning my Windows Migration Strategy"
date: 2008-10-11
forum: Testimonials &amp; Experiences
---

### Post by Mysearch on 2008-10-11
*In light of the sticky post at the start of this specific forum, this post is not critical of Linux or Ubuntu, just the migration process required to get Ubuntu installed and working on Dell systems. I accept that many people may be able to install Ubuntu on their particular systems with all hardware working and configured properly from the start. Unfortunately, this was not my experience. However, the purpose is not to be negative per se, although installation problems are cited, but rather the purpose is to request the Ubuntu/Dell experts to further consider a more user-friendly migration strategy than that currently on offer to incumbent Windows end users. Given that Ubuntu is free software and I have no insight of Canonical’s business model, I guess I would like to see Dell be more responsive in providing an end-user friendly migration to its existing customer base.*
[CENTER]
-------------------[/CENTER]

So for what it is worth, here is my summary of a week’s effort trying to get Ubuntu 8.04 installed on my 2 laptops, i.e. Dell Inspiron 1525 & 1300. First, by way of background:  

[INDENT]o	Basically, I use my laptops as a tool to do my work and pursue general interests via the Web. My main packages are Office and Frontpage, although I have collected dozens of other Windows based applications over the years.

o	So why was I interested in Ubuntu? First, I see Vista as a pain in the ****, so when I saw Dell announce their support of Ubuntu, presumably after recommending Vista (!) I thought the time might be right to try a Unix OS. Equally, my Microsoft applications are getting old and, as such, have become increasingly difficult to install under Vista and the newer replacement versions are too expensive and often not backward compatible. Finally, I had already started to use OpenOffice, as an alternative to Microsoft, so wondered if I should start to migrate away from Vista as well.[/INDENT]

To be honest, I don’t necessarily expect my first impression to change anything, but I thought it was worth simply tabling my experience into this forum before giving up on the process.

[INDENT]o	While I realise that Ubuntu is focusing on many different market applications, the home-user market would seem to be critical for general acceptance. If so, Ubuntu should seek to offer a more turnkey plug & play solution to existing Windows users in partnership with system manufacturers like Dell. My experience suggests that this doesn’t exist as yet despite an undoubted attempt to address this issue.

o	Initially, it is easy to become snow-blinded by all the various installation options on offer and to find the required level of documentation, e.g. web sites, to help decide which is the most appropriate starting point for you and your specific system.

o	As an initial migration strategy, few Windows end-user will want to discard all their existing Windows applications on Day-1; therefore many will be focused on the dual boot option. However, this said, it is unlikely that many will want to re-partition their hard drives straight away without getting some first hand experience with Ubuntu and its available application packages. Therefore, I believe that many will want to just try the boot from CD option at first. 

o	While I understand the .ISO format is a recognised standard, it can take a while to even build a boot CD, i.e. my system had no default recognition of the ISO format and I had to learn about and download ISORecorder before I could even produce the required boot CD. Unfortunately, this option did not work on either of my Dell systems, i.e. 1525 & 1300, due to a range of problems, especially the configuration of the wireless network and sound cards.

o	When I tried to get some help via several of the Ubuntu forums, my questions disappeared without trace in a matter of minutes in what appears to be an endless stream of user issues. After this I was forced to switch to searching the net, which then threw up many purported, but different solutions to problems that appeared similar to mine, although all seemed to be a little too involved for a Ubuntu/Unix beginner, who just want to evaluate the system. Equally, it appeared that none of these solutions could be built into my boot CD option.

o	Due to the low speed of operation from the CD, I then tried the *`Install inside Windows*` option, but this didn’t change the basic Dell hardware configuration problems that essentially prevented Ubuntu from being evaluated on both my systems. I would also say I didn’t find Dell to be much use in this matter, especially given their publicised Ubuntu support, which seems more focused on future user recovery rather than exist customer migration.

o	Finally, tried the Virtualbox approach, which did actually worked despite all Vista’s dire warnings, although I couldn’t overcome the 800x600 screen resolution problems. Again, searched in vain through many proposed solutions, which simply did not work on my systems. So to cut this long story short, I have decided to call it a day for now.[/INDENT]

I have now uninstalled everything and have gone back to Vista for the time being. I sure many Ubuntu, Vista and Dell experts/devotees that participate in this forums will simply dismiss my problems as ignorance. In part, this is probably true, although it misses the point of what a migration strategy needs to offer existing Windows end-users, who simply want to boot up a system that works without first having to spend countless hours learning about Unix command line syntax before they can even familiarise themselves with the basics of Ubuntu. So….

[I]If Dell and Ubuntu are in serious partnership and want to promote its adoption, can they not offer a customised download of Ubuntu that will work for a given specified systems, or at least tell people in advance of the known problems without leaving them to discover the issues by themselves and then have to search the Web for their own potentially risky solutions before they can even  get started?

Does anybody know if Dell plans to offer a dual-boot option on new laptops?[/I]

---

### Post by wolfen69 on 2008-10-11
buy a dell computer with ubuntu preinstalled, and you wont have any issues. your computer was made for vista, not ubuntu.

---

### Post by aysiu on 2008-10-11
Most failed migrations I see are a combination of incompatible hardware and a bad user attitude.

Yours seems to be a combination of incompatible hardware and bad luck. Wubi and VirtualBox didn't work for you? Well, I think in that case you should stick with Windows until you're in a position to buy a new computer and then take wolfen69's suggestion.

---

### Post by armandh on 2008-10-11
if your computer works but slowly on the live cd then IMHO...

use the vista utility to reduce the vista partition by 10GB
search 'reduce partition size' for instructions
then install as a dual boot using the 'largest free space' option when selecting the partition.

this worked on my wife's hp-compaq laptop
and they are usually more dificult than dell

---

### Post by wolfen69 on 2008-10-11
and, if you get a pc with ubuntu preinstalled, you can always add windows and dual boot. that is the best way to go about it imho. it's a fact of life that some pc's made for vista just won't play nice. heck, i know some xp users that can't upgrade to vista even though there's a sticker that says "vista capable". if you go about things logically, and *plan* to use linux, you should have no problems. millions of people are doing it just fine.

i know lots of people using linux without any problems. plus, i've installed it many computers without fail. but it's ok if you bail to windows, as some people just aren't willing to put any planning or effort into it. good luck whatever you decide.

---

### Post by tgalati4 on 2008-10-11
Print out your post and store it for a year.  Then reread it and see what has changed.

---

### Post by Mysearch on 2008-10-12
Hi,
Thanks for the feedback, however, I would like to respond with some additional comments because I am not sure the perspective I was trying to put across was fully understood.

> *#2: “buy a dell computer with ubuntu preinstalled, and you wont have any issues. your computer was made for vista, not ubuntu.”*

I would never simply buy a computer preinstalled without first getting some hands-on experience. This was why I was attempting to install Ubuntu on my existing computers. I believe the vast majority of incumbent Windows end-user would not be able to simply switch wholesale to Ubuntu, i.e. they need access to existing applications as they attempt to transit to Ubuntu and Unix based applications. This was why I asked the question:

*Does anybody know if Dell plans to offer a (pre-installed) dual-boot option on new laptops?*

As far as I know Dell only offer Ubuntu or Vista, possibly XP/SP3 if you push hard enough. Most Windows end-users would want the reassurance of Windows pre-installed, especially as Microsoft doesn’t give this away, but might welcome the chance to try Ubuntu, if they didn’t have to address all the potential installation issues on day-1. Not sure I understand the comment about my computer being made for Vista not Ubuntu. As far as I understand the situation, only software is at issue, e.g. unix based drivers for Broadcom wireless are not available, hence the NDISWRAPPER approach.

> *#3: “Most failed migrations I see are a combination of incompatible hardware and a bad user attitude.”*

While I understand why you are saying this, I not sure that I totally agree. Yes, I am sure some people who post threads in this forum have an ulterior agenda, but I think most people who try Ubuntu simply want to see it work. Certainly, my Dell laptops (1525, 1300) appear to be incompatible with Ubuntu 8.04 without some major patch reconfiguration. In part, the reason for detailing my experience in this forum was in the hope that the Ubuntu experts and Dell might reflect on a more helpful migration strategy for existing Windows users. I think if this were addressed, you would see a lot less ‘*bad user attitude’*.

> *#4 “if your computer works but slowly on the live cd then IMHO...”*

As stated, the slow operation from CD was expected, but would have been adequate to try Ubuntu if everything had worked. It was the fact that network and sound cards were not configured properly that caused most of my problems. Installing on the hard-drive and re-partitioning would not have changed this, i.e. I would still have needed to learn how to install all the necessary Unix command line patches. As a footnote, many of the fixes I tried simply didn’t work or came with health warnings, e.g. I saw several sites arguing against the use of the NDISWRAPPER approach that was worrying.

> *#5: “and, if you get a pc with ubuntu preinstalled, you can always add windows and dual boot. that is the best way to go about it imho. it's a fact of life that some pc's made for vista just won't play nice. heck, i know some xp users that can't upgrade to vista even though there's a sticker that says "vista capable". if you go about things logically, and plan to use linux, you should have no problems. millions of people are doing it just fine.”*

Wolfen, you are clearly a very knowledgeable person on these topics and from the number of posts accumulated you have tried to help a lot of people. I am sure millions are doing just fine, but this number is still small in comparison to the number of incumbent Windows users. The only point I was trying to raise was simply that further consideration of the migration strategy to Ubuntu from Window is (IMHO) necessary. Again, for what it is worth:

[I]1)	Most incumbent Windows user will simply want to initially try Ubuntu on their existing machines for a few months in order to get some hands-on experience and confidence.

2)	Ideally, this process would be essentially risk free and involve a minimal learning curve with no dependency on understanding Unix command line syntax on Day-1.

3)	Most Windows users need to retain a dual system to allow a phased migration.

4)	As such, I am not sure many would buy a PC with only Ubuntu pre-installed and then pay for Windows, which they normally get included in the base price. If they go with Windows, then Ubuntu has to work out-of-the-download-box.[/I]

Given the publicised partnership of Ubuntu & Dell, I was mainly disappointed with Dell’s support of Ubuntu on its existing machines. I would have thought Dell knew how to get Ubuntu to work on both the Inspiron 1525 & 1300 and could offer a modified version of Ubuntu 8.04 that worked for both of these systems. By way of positive closure, I will try Ubuntu again, but will probably take the following advice offered:

> *#6: Print out your post and store it for a year. Then reread it and see what has changed.*

Anyway, appreciated the feedback and the opportunity to let out a bit of frustration. Thanks

---

### Post by Riffer on 2008-10-12
I'm sorry for your frustration and the points you made in your OP are fair comments.  But the fact of the matter is that when installing an OS yourself there is a learning curve, whether its Windows or Linux.  So it's fair comment for others to point out that the safest and easiest method is to buy a pre-installed  Ubuntu computer, other then that you have to be prepared to get your hands dirty.

Having said that it shouldn't be that hard, a little scary yes, but not hard.  The install program is easy and straight forward and using the recommendations is pretty safe.  

On another note.  The next release has more support for wifi you may want to wait for it (Oct. 30th)

---

### Post by Darrell Lawrence on 2008-10-12
I can understand your frustration. Getting any Linux distribution to work on a computer that came preloaded with Windows can be completely painless where everything works, or, at the other extreme, impossible  to use. Your experience will very depending on your hardware configuration.

IMHO migration instructions really resides with the Linux vendor/community. For Ubuntu I would start here:

[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

As far Canonical/Dell collaboration on customized installs of Ubuntu on Dell PCs already sold configured for Microsoft Windows - I don't see the financial incentive for Dell to allocate the money and resources that would be needed.

Canonical and the Ubuntu community continue to strive for compatibility on as much hardware as possible, but that's always limited by the willingness of hardware vendors to release Linux drivers. I think trying to add customized installs for any particular computer brand or configuration would only slow down efforts for broader hardware compatibility.

Bottom line is we are all stuck with doing a certain amount of research to find out if our hardware and peripherals will work. For instance, I bought a Dell laptop preloaded with Ubuntu so I knew it would work. However, I bought a new printer at the same time, and that required doing some research prior to the purchase. That resulted in an brand new HP Deskjet all-in-one printer that does everything Ubuntu asked ... well it won't make lunch for me, but nothings perfect.


You might find these links helpful to some degree:

[http://www.dellcommunity.com/supportforums/board?board.id=sw_linux](http://www.dellcommunity.com/supportforums/board?board.id=sw_linux)
[http://linux.dell.com/](http://linux.dell.com/)

Best wishes in your endeavors.

Darrell

---

### Post by cardinals_fan on 2008-10-12
> **wolfen69 said:**
> and, if you get a pc with ubuntu preinstalled, you can always add windows and dual boot. that is the best way to go about it imho. it's a fact of life that some pc's made for vista just won't play nice. heck, i know some xp users that can't upgrade to vista even though there's a sticker that says "vista capable". if you go about things logically, and *plan* to use linux, you should have no problems. millions of people are doing it just fine.

i know lots of people using linux without any problems. plus, i've installed it many computers without fail. but it's ok if you bail to windows, as some people just aren't willing to put any planning or effort into it. good luck whatever you decide.
Buying Windows preinstalled through an OEM costs perhaps $10-25.  Buying it yourself costs $100+.  Also, Windows is not immune from hardware issues, and I would personally rather have it preinstalled so I don't have to deal with fixing it.

---

### Post by Mysearch on 2008-10-13
Hi,
I much appreciated the latest comments, as I believe they give a good insight of the potential migration problems ahead. I realise that this discussion has to timeout soon, but I wanted to continue to make the case for further migration support. First, Riffer, your comments raised a valid point:

> *#8: the fact of the matter is that when installing an OS yourself there is a learning curve, whether its Windows or Linux. So it's fair comment for others to point out that the safest and easiest method is to buy a pre-installed Ubuntu computer, other then that you have to be prepared to get your hands dirty.*

I basically agree, but isn’t the requirement for pre-installed dual-boot systems, i.e. Windows and Ubuntu, being ignored. From my experience, the vast majority of people who use PC’s don’t want to install any OS of any sort. I don’t know what the legal issues are for the manufacturer, but the comments in #10 suggest the costs for the end user would favour this pre-installed dual boot approach. However, the key point is that dual-boot is essential for any practical phased transition from Windows to Ubuntu. 

Darrel, I suspect your summary of the current business logic is probably correct, but there is also the axiom: *“in business you get what you want by giving other people what they want”* which may become increasingly important as the current economic turmoil comes to affect the PC market over the next few years. So to comment on your key point:

> *#9: As far Canonical/Dell collaboration on customized installs of Ubuntu on Dell PCs already sold configured for Microsoft Windows - I don't see the financial incentive for Dell to allocate the money and resources that would be needed.*

As stated earlier, I don’t pretend to know Canonical's long-term business model; therefore, I am not sure whether they are motivated to go after the huge base of incumbent Windows users. Of course, Dell is driven by a profit and loss sheet, but I would suggest that it would be a mistake for Dell to ignore the requirements of its current customer base, i.e. a migration strategy to cost-effective applications, as they might not remain customers in the future. I have bought Dell for a good number of years, but was very upset by their recommendation/insistence that my last laptop came with Vista. While I can't live without Windows in the short-to-medium term, Microsoft now only seem to focus on what is good for Microsoft rather than its home-office customers. Therefore, now may be a good time to offer a practical alternative, as long as it comes with a cost-effective migration strategy. I also don’t know what it would cost for Dell to offer a modified version of Ubuntu with the necessary fixes for some of its PC’s still under warranty, but it would sure go a long way to changing my opinion of them when I buy my next laptop.

Anyway, I doubt that I am going to influence the powers that be in this matter, but still it was worth a try. Again, thanks for your insights.

---

### Post by Riffer on 2008-10-13
The eternal question, "why don't they"?  I have no clue why Dell doesn't do as you suggest.  At present Dell's commitment to Linux/Ubuntu is lukewarm at best.  They could do so much more and why they don't is a shame.  I think one part of the company sees the value of Linux/Ubuntu while other parts are quite comfortable with the status quo.  I also think this is the case with most big hardware companies.  They're fed up with the present state of affairs with MS, but they are holding on just in case Windows 7 is actually something worth while.

Having said all that Canonical's hands are tied. They're pushing as much as they can for the OEM business.  The only other thing they can do (which IMO they are) is to produce an OS where users are willing to go through the "hassle" of installing onto their present system.  To that end Canonical has produced probably the easiest install of any OS, its one of the big things they're known for.

As to your problem, I would bite the bullet and do a dual boot install to your system.  Save all your important data to either a flash stick or DVD.  Boot to your LiveCD click on "INSTALL" and follow the setup screens.  As for partitioning choose what is recommended in setup.  In less the 30 minutes you'll have your system up and running.

If your wifi doesn't work you can cable into router till you get it sorted.  I bet that just getting the "Ubuntu restricted extras" and perhaps NDISWRAPPER as well.  Also take note that Ubuntu 8.10 which comes out at the end of the month has far greater support for wifi, you may want to wait for that release.  

In any case I think at the end of the day you'll be surprised how easy it all is.

---

### Post by mikewhatever on 2008-10-13
I think, in theory, it would be great to offer a migration strategy  for all Dell users that want to try Ubuntu, however, given the variety of hardware in use, the simple lack of drivers for some of it, and the diversity of technical levels of potential users, it's hard to imagine how that is feasible.
Dell actually offers 7.10 and 8.04 isos, but, once again, if your notebook has a broadcom wireless, and the company chooses not to support linux, there isn't much, Dell can do. You'd still need compatible hardware, to learn about iso files, etc.
[http://digg.com/linux_unix/The_New_ISO_for_Dell_Ubuntu_8_04_is_now_available_here](http://digg.com/linux_unix/The_New_ISO_for_Dell_Ubuntu_8_04_is_now_available_here)

---

### Post by kg4cna on 2008-10-13
> **Mysearch said:**
> 
I would never simply buy a computer preinstalled without first getting some hands-on experience.

Did you buy your computer with Windows preinstalled OR did you install it yourself?  If you bought it preinstalled...you did just what you said you'd never do.  I know...you've probably used windows before you bought it right?  At any rate, any OS requires learning how to use it...we're not born knowing how to use any OS.  It's all what you get used to. I find Ubuntu much easier to deal with than Windows..especially Vista...and I'm definitely NOT an expert.

If I may ask, what problems did you have with your Inspiron 1525?  I have a 1525 and I had no problems.  My 1525 came with Vista and I promptly wiped it off in favor of Ubuntu 8.04.  Everything worked fine except the wireless (Dell wlan card). I cabled into my router until my Intel Pro card came in and I swapped it.  Everything works works fine..audio, video, network..everything.  I'm using it to write this response...and it's also my every day work computer.

Just my opinion ;)
Allen

---

### Post by gwenn on 2008-10-13
I'll give you another variant.You can or better must download some linux from the web,give them a try with live cd .It's simple and you can look by yourself how's look linux.Even old distro.You'll find someone that works for you out of the box without any issues.Once you learn how to use one,you can use all linux.I think this is the better way to do.After a while you will be able to choose by yourself YOUR distro like we all did.It's just a matter of time.

---

### Post by Tamlynmac on 2008-10-13
> Microsoft now only seem to focus on what is good for Microsoft rather than its home-office customers. Therefore, now may be a good time to offer a practical alternative, as long as it comes with a cost-effective migration strategy. I also don’t know what it would cost for Dell to offer a modified version of Ubuntu with the necessary fixes for some of its PC’s still under warranty, but it would sure go a long way to changing my opinion of them when I buy my next laptop.

Again I must admit confusion regarding expectations. Is Canonical's primary objective to displace MS as the world's "ONLY" OS? Or are they endeavoring to produce a competitive quality alternative? I for one don't wish to see Ubuntu compromised, based on completion with the sole purpose of attracting Window's users. A big part of me enjoys the fact that Ubuntu isn't compromised by this philosophy. I suspect I may be in the minority.

I don't feel entitled or believe my opinion will result in a modification to Canonical's long term marketing strategy's, just hope they don't deviate from the "quality first" philosophy. I've been so pleased with Ubuntu, primarily because of it's functionality and user friendliness. It's always easy to blame my inabilities on the software and then complain that it doesn't meet my expectations. Whats hard is to understand that success is linked to investment - with Ubuntu it's a time investment (learning) - with Windows it's a financial and time investment. I've already made my choice.

---

### Post by Comhra on 2008-10-14
> **armandh said:**
> if your computer works but slowly on the live cd then IMHO...

use the vista utility to reduce the vista partition by 10GB
search 'reduce partition size' for instructions
then install as a dual boot using the 'largest free space' option when selecting the partition.

this worked on my wife's hp-compaq laptop
and they are usually more dificult than dell

While I was still dual-booting with XP, my Ubuntu partition was only 10 Gb for Feisty.  I quickly found that I much preferred Ubuntu even though I didn't like the default theme or fonts and that 1o Gb was not enough.  This was in the days before I realised that I could customize everything in the OS, lol.

20 Gb might be a better starting partition if you do opt to go down that road.

---

### Post by Mysearch on 2008-10-14
Hi,
Again, some very informative opinions to which I would like to make some response.

> *#12: At present Dell's commitment to Linux/Ubuntu is lukewarm at best. They could do so much more and why they don't is a shame.*

I suspect, as alluded by others, it is basically a question of the `*bang for the buck*`. Dell have probably opened the door to Ubuntu because it creates a good story, but don’t want the costs to get out of control for what is probably, at present, a small volume of the total number of systems shifted. Equally, Dell probably doesn’t want to be seen as trying to undermine Microsoft’s dominant position.

> *#13: I think, in theory, it would be great to offer a migration strategy for all Dell users that want to try Ubuntu, however, given the variety of hardware in use, the simple lack of drivers for some of it, and the diversity of technical levels of potential users, it's hard to imagine how that is feasible.*

This is probably a fair comment, but all the Ubuntu supporters keep telling me that the number of problems with systems like the Inspiron 1525 and 1300 are minimal and even the wireless problems can be overcome. Presumably, Dell already knows these problems and the necessary work-round solutions, so how much would it cost them to package up these existing solutions into a range of Dell specific Ubuntu releases for its existing customer to download, especially in light of the Ubuntu/Dell partnership?

> *#14: Did you buy your computer with Windows preinstalled OR did you install it yourself? If you bought it preinstalled...you did just what you said you'd never do.*

For me, this is a weak argument because my use of computers pre-dates even Windows. Yes, I’m old. As such, I kind of just grew up with Windows and acquire familiarity of its quirks along the way as each new release emerged. Equally, in the early days, I was happy to waste hours installing all sort of stuff on my PC’s, but now I have a dependency on these systems to do my work, therefore much more reluctant to just install an untried OS. For the record, I have actually tried many fledgling Linux systems over the years and had to discard them all. However, Ubuntu looks as though it could be a contender, hence my persistence in arguing for a better migration strategy.

> *#14: If I may ask, what problems did you have with your Inspiron 1525?*

The sound card didn’t work and my wireless card had some problems. To be honest, the real problem for the beginner is the risk to their existing operation, the effort required to learn about Unix command syntax and verifying the reliability of all the various fixes on offer. As such, this is why I am making the case for Dell/Ubuntu to better address these issues, if they want to seriously offer a viable alternative to the existing Windows home-office user market.

> *#15: You can or better must download some linux from the web,give them a try with live cd .It's simple and you can look by yourself how's look linux.Even old distro.You'll find someone that works for you out of the box without any issues.*

Thanks for the suggestion, you may be right, but I can’t really afford the time or the potential security risk of this approach at this point.

> *#16: Again I must admit confusion regarding expectations. Is Canonical's primary objective to displace MS as the world's "ONLY" OS? Or are they endeavoring to produce a competitive quality alternative? I for one don't wish to see Ubuntu compromised, based on completion with the sole purpose of attracting Window's users. A big part of me enjoys the fact that Ubuntu isn't compromised by this philosophy. I suspect I may be in the minority.*

I think this is both an excellent and valid point, which I have also reflected on. So some expansion of my motivation for the arguments I am making into this forum regarding a better migration strategy. 

[INDENT]1.	[I]I believe Microsoft has become too dominant in the home-office market and we, the individual end-users, have had little option but to accept whatever Microsoft releases. Therefore, I would love to see more healthy competition via Ubuntu in the low-cost end of the market, i.e. Apple and Sun are too expensive for me.

2.	Of course, as you allude, there may be no long-term advantage, if Canonical were just to become another Microsoft clone. However, I believe Canonical roots in open-source software may ensure Ubuntu’s credentials as a competitive alternative. However, whether it can deliver on quality given my limited perception of its current business model may be more of an open issue.

3.	You have also raised the question: what is a realistic market for Canonical/Ubuntu? It would seem to me that Sun is the main top-end Unix provider and therefore I would have thought that most Linux distributions would have to compete for the remaining and lower-end markets, which includes the small home-office. As far as I can see Ubuntu is already being marketed to the small end-user, albeit requiring more Unix savvy than most Windows users may initially wish to accept.

4.	Canonical will undoubtedly need the proactive support of several PC manufacturers, like Dell, to succeed in gaining any significant share in the markets under discussion. Again, this may ultimately be predicated on some percentage of the current base of Windows end-users migrating to Ubuntu. However, as far as I can see, Dell doesn’t really have too much incentive, at this time, regarding Ubuntu unless it see the potential for increased market share. If so, maybe it is in Ubuntu’s interest to offer a better migration strategy to existing Windows users.

5.	Ultimately, IMO, Dell will only get serious about supporting Ubuntu if they think a significant portion of its customer base want Ubuntu. For me, this requires the dual-boot option, i.e. Windows and Ubuntu, to be pre-installed when I buy my next PC.[/I][/INDENT]Would be interested in any specific response concerning the viability of the pre-installed dual boot option and how this requirement could be best highlighted to Dell? Thanks.

---

### Post by Tamlynmac on 2008-10-14
> 2. Of course, as you allude, there may be no long-term advantage, if Canonical were just to become another Microsoft clone. However, I believe Canonical roots in open-source software may ensure Ubuntu’s credentials as a competitive alternative. However, whether it can deliver on quality given my limited perception of its current business model may be more of an open issue.

Your basing assumptions predicated on a lack of information. Sine neither you nor I can predict what Canonical's strategies are.
As a point in fact most all of your responses (1-5) are founded in those assumptions.

I don't disagree with many of your statements. However, the future of Ubuntu can only be decided by Canonical.

You do make one statement that I found odd.
> Thanks for the suggestion, you may be right, but I can’t really afford the** time** or the potential security risk of this approach at this point.
This response indicates you struggle with time management. But you continue to write lengthy responses. It is possible that both your ability to express your opinion and typing speed, far exceed mine. However, you did review and to some extent evaluate each response. Time is the true investment, as I indicated in my prior response...

---

### Post by Riffer on 2008-10-14
You know I really don't know what you want.  A lot of shoulda's woulda's and if only's.  It seems you want guarantees and nobody can give you that.  Even if you got an Ubuntu install disk from Dell there is still a chance that your system will have problems.  The only guarantees is if you bought a system pre-loaded with Ubuntu, after that you take a risk.  And this would also hold true the other way around (Ubuntu to Windows).

At this point you have a choice, either forget about it or going for it and installing Ubuntu on one of your machines.  As I said before, its not that hard, theres lots of resourses, and HOWTOs out there.  

Just on the Dell site and there seems to be an iso there, whether its will work for your machine or not is another question.  May be phone Dell and find out.  Heres the link.

[http://linux.us.dell.com/files/ubuntu/hardy/iso-images/](http://linux.us.dell.com/files/ubuntu/hardy/iso-images/)

I just found out that iso will work for 1525n.

Here is the wiki pages

[http://linux.dell.com/wiki/index.php/Wiki_Main_Page](http://linux.dell.com/wiki/index.php/Wiki_Main_Page)

---

### Post by Riffer on 2008-10-14
Also while I was at the Dell site I checked out their forums.  Lots of good info and pointers to setting up a Dell machine with Ubuntu.  I would also check that out to.

---

### Post by Mysearch on 2008-10-15
I guess my posts have become counterproductive &#8211; sorry that was not the intention. Having spent a week trying 3 different installations approaches on 2 machines and reading through lots of patch solutions, I felt that there might be some value in outlining my own experience and perspective on Ubuntu at this time, possibly I was wrong. 

> *#20: &#8220;You know I really don't know what you want&#8221;*

It was simple enough; I was making the argument for the need of a dual-boot system to work without the end-user having to search for unsupported solutions on the net. Tamlynmac was right to point out that I don&#8217;t know Canonical business strategy, although I made this point myself. However, IMO, the ultimate success of Ubuntu will not be based on a hobbyist acceptance of its current installation weaknesses. Bye.

---

### Post by Riffer on 2008-10-15
You quoted me out of context.  The point I was making was that you want guarantees, and with you trying to setup a dual boot machine after market, you're not going to get one.  Put it into context, if MS to supply you with an install solution to dual boot your Ubuntu machine, they would laugh. Lets take it even further, if you build your own comp and tried to install Windows on it you run a risk of running into trouble.  Certainly you will have to install drivers and if you think MS supports these drivers, think again.  And even after installing all the proper drivers etc. there is still a chance that you would have a conflict some where.

Given all that to think that Canonical should have an install solution for Dell machines that is flawless in all cases is unreasonable.  What Canonical does is supply an install that works for most machines, its up to the hardware vendors (in this case Dell) to supply the appropriate drivers for their machines.  From what I garnered from the Dell and their forums is that indeed Dell does have downloads for their drivers, as well as instructions for install Ubuntu onto your machine.

---

### Post by Darrell Lawrence on 2008-10-16
> **Riffer said:**
> You quoted me out of context.  The point I was making was that you want guarantees, and with you trying to setup a dual boot machine after market, you're not going to get one.  Put it into context, if MS to supply you with an install solution to dual boot your Ubuntu machine, they would laugh. Lets take it even further, if you build your own comp and tried to install Windows on it you run a risk of running into trouble.  Certainly you will have to install drivers and if you think MS supports these drivers, think again.  And even after installing all the proper drivers etc. there is still a chance that you would have a conflict some where.

Given all that to think that Canonical should have an install solution for Dell machines that is flawless in all cases is unreasonable.  What Canonical does is supply an install that works for most machines, its up to the hardware vendors (in this case Dell) to supply the appropriate drivers for their machines.  From what I garnered from the Dell and their forums is that indeed Dell does have downloads for their drivers, as well as instructions for install Ubuntu onto your machine.

Well said. Plus if you happened to purchase as Dell system with Vista that has a video card that only supports Windows your video is not going to work properly with Ubuntu or any other Linux distribution unless the Linux community has been able to reverse engineer a Linux driver for that video card. Video card drivers are the responsibility of the video card OEM, not the computer manufacturer. Some support Linux, others flat out refuse.

To have a system that you can be sure will give you a hassle free dual-boot you can either buy a Windows Vista system that you know works (you've done all your homework before hand by checking out compatibility lists.) Or you can buy a dual-boot system from companies such as Linux Certified or Emperor Linux that have done all this for you - giving you a turnkey dual-boot system out of the box. 

I haven't heard anything about Dell offering dual-boot Ubuntu/Windows systems. As I recall the requests were for Linux only machines.

Anyhow, based on Riffer's post, it sounds like Dell does have solutions for running Ubuntu successfully on your laptops, but you'll have to do some work to get them there. Certainly your choice.

Whatever your decision, happy computing.

Darrell

---

