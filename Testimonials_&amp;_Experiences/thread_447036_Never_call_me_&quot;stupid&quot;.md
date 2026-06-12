---
title: "Never call me &quot;stupid&quot;"
date: 2007-05-17
forum: Testimonials &amp; Experiences
---

### Post by raidet on 2007-05-17
I remember some time ago I watched a Chris Morris show with an inspired sketch about the fact that people are all too willing to label eachother "stupid" before knowing anything about their thought processes, or the background info they're probably not privy to. That's all well and good until you encounter *true* stupidity. 

Ubuntu appeared to be the main open-source contender to Windows at the moment (what with Dell jumping on board), so I decided, as a reasonably geeky-type, to try it out. I realised I might have problems right away because of my RAID stripe, so I created a partition on an external primary. After all - native support for RAID without specialist knowledge was unlikely - this I was most willing to accept - and a glance at some ubuntu forums confirmed that it required pre-existing Linux knowledge. I'll deal with that later then.....

So, I downloaded Ubuntu and cranked it up at boot. Woo! A CD-based startup to sample the delights - bootiful! But never mind that - I want this thing on my disk, so went to "install".

The first couple of screens were very impressive. A GUI locale selector and simple questions about keyboard layout. Suddenly someone sits on the end of the piano, hitting a minor chord that felt like a sharpened rake across the frontal lobes. The question "guided" or "manual". Guided consuming your entire disk, and "manual" apparently allowing you to try Ubuntu without destroying all the data you own. Naturally I went for option 2. This is where it got "bad". Suddenly I'm expected to have prior knowledge about the internal CLI-level workings of Linux....BEFORE installing it for the first time. I'm expected to understand the function and necessity of the "swap" partition and opt for a filesystem type for it, and the same for the main OS partition. ERROR. I'm sorry, but demanding pre-existing (and highly detailed) knowledge of your operating system BEFORE it's even installed is ******* STUPID. Many give old Bill a hard time, but I was never asked by the Windows installer to pointlessly involve myself in low-level installation parameters simply because I didn't want my entire drive wiped, with absolutely NO effort made to enlighten the user as to what the **** is going on.

Chris Morris made a valid point, but he never encountered a world of geeks, with their deliberate obfuscation tactics designed to make them feel superior in some pathetic way. To the "norms" trying to bring Linux to the masses, here's one tip you frankly should already know: "Let people install the ******* thing before demanding specialist knowledge or your install CD gets frisbeed out the window into the trash where it belongs". Geeks will use technology (especially CLI) to promote a sense of their own superiority (they're the only ones with the time or inclination to learn the nuances of every "grep" in an extended shell command). You have a choice - be a deliberately exclusive geek-toy, or appeal to the masses and apply common sense. There is no in-between.

_rai

---

### Post by Bachstelze on 2007-05-17
> **raidet said:**
> Many give old Bill a hard time, but I was never asked by the Windows installer to pointlessly involve myself in low-level installation parameters simply because I didn't want my entire drive wiped, with absolutely NO effort made to enlighten the user as to what the **** is going on.

Wrong. When you want to format the partition during the Windows install, you're asked if you want to make it NTFS or FAT32. How is that any different from asking if you want ext3 or ReiserFS ?

And sorry to disappoint you but choosing a filesystem definitely is not "high level" knowledge ! The twelve-year-old I was when I installed my first Linux did it withoud a problem and trust me, the installers were far less user-friendly back then !

---

### Post by Acglaphotis on 2007-05-17
> This is where it got "bad". Suddenly I'm expected to have prior knowledge about the internal CLI-level workings of Linux....BEFORE installing it for the first time. I'm expected to understand the function and necessity of the "swap" partition and opt for a filesystem type for it, and the same for the main OS partition

You are "expected"? From who? How hard is to choose the "swap" filesystem for swap? 

-Acgla


EDIT: Isnt there an option to install and let ubuntu do the partitioning ( without deleting windoze?)

---

### Post by Atomic Dog on 2007-05-17
Too much coffee dude!

I alswys use Acronis to shrink and move my partitions, but the partition manager on the boot cd can do that for you too.  Just choose the automatic, make the partition decisions for me option, and be done with it.

---

### Post by phidia on 2007-05-17
I don't believe that there is a disclaimer stating you won't have to learn a few things if you try something quite diferent from what you're used to.
That seems to be true in many aspects of life & changing your OS falls into that catagory.

---

### Post by Bachstelze on 2007-05-17
> **phidia said:**
> I don't believe that there is a disclaimer stating you won't have to learn a few things if you try something quite diferent from what you're used to.
That seems to be true in many aspects of life & changing your OS falls into that catagory.

Very true. That's what I would call "common sense"...

---

### Post by gitfiddler on 2007-05-17
raidet,

The developers don't assume that you are stupid. They assume you've read the instructions.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Please, try it. If you don't like it, fine.

If you do, welcome aboard.

---

### Post by ginestre on 2007-05-17
[QUOTE=Acglaphotis;2673636]You are "expected"? From who? How hard is to choose the "swap" filesystem for swap? 

-Acgla

Very. 

Though I don't much care for the tone, Raidet has a good point: ubuntu is more accessible than many other distrros, and lots of good folk on this forum and elsewhere try really hard to make it less intimidating, NEVERTHELESS if you're coming in through the windows it can feel pretty intimidating; and a better guide at that precise point of the install process would certainly have helped me. I stopped twice, and spent a couple of days reading up on the options because I was paranoid about making a wrong choice exactly there.... you have to be pretty strongly intentioned to get through that, and most people would have (or more probably, do) frisbeed the cd out into the snow

---

### Post by toasterofirony on 2007-05-17
I never understand why people get so narked about something they are not familiar with being different. My first play with Linux was buying Red Hat 8.0 for Dummies and that was one of the best investments I have ever made and one of the defining moments of my computing life.

Yes, it helps to know what you are doing, but then, if you've an interest in Linux (esp. Ubuntu) you've probably done some reading (see above). Or you know about the *extensive* amount of stuff on the 'net about it.

Failing that, you do what I always do when I re-install an OS. You back up everything dear to you before hand. 

I tend to think of it like driving: You have to know a little about driving before you sit in the car and turn the ignition key.

And for the record, even when dual booting with a previous XP install on my HDD, I used the guided mode and never suffered for picking the "easy" option.

No-one ever finds the jump especially easy, Windows to Linux, but it is worth it. And whats more you get to learn a little along the way.

---

### Post by rich.bradshaw on 2007-05-17
Have you ever installed Windows? It's nowhere near as straight forward...

---

### Post by DaveyG on 2007-05-17
> **HymnToLife said:**
> Wrong. When you want to format the partition during the Windows install, you're asked if you want to make it NTFS or FAT32. How is that any different from asking if you want ext3 or ReiserFS ?

And sorry to disappoint you but choosing a filesystem definitely is not "high level" knowledge ! The twelve-year-old I was when I installed my first Linux did it withoud a problem and trust me, the installers were far less user-friendly back then !

Agreed, if a 12 year old can choose a suitable filesystem then pfft.. it cant be that hard

Davey

---

### Post by raidet on 2007-05-17
Of course, it's the prerogative of Ubuntu or anyone else to demand any prior knowledge they want. My point is that it's not necessary *at all* to demand pre-existing knowledge of the user at the point of installation just because they don't want their entire drive wiped. Either default/recommended options can be presented (like Windows) or the options can be explained. Just about nobody will trial an OS at the expense of their entire machine, AS WELL as not really knowing what they're doing. Deliberately making it difficult for normal users to take-up, while professing to present an alternative to Windows, is completely demented - for the most silly and pointless of reasons.... because I'm sure Ubuntu CAN represent a true alternative. It's simple, ordinary stupidity that is doing all the blocking, and that's my gripe.

---

### Post by wthanna on 2007-05-17
Wow.. many beat my to the response here... but as has been pointed out, WINDOWS EXPECTS YOU TO KNOW THE EXACT SAME THING!  if you are doing a fresh install or trying to install to a system with either no partitions, or pre-existing partitions.

---

### Post by Znupi on 2007-05-17
Excuse me, but: what the hell? The installation of Ubuntu is as easy and user-friendly as possible. It just asks you to create two filesystems, one ext3 and one swap, and choose their mount points accordingly ( ' / ' and ' swap' ). What's so high-level about that?...

---

### Post by ahaurw01 on 2007-05-17
I admit I didn't do a whole lot of research when first wanting to install Ubuntu Dapper on my system.  But when I went through the install process, I needed to choose how much space to give my / partition and my swap partition. Also, the options of creating partitions for /home, /boot, ...etc were available. At the time I had no idea how much space to give what. Just yesterday I was reinstalling feisty on my laptop and if I didn't have prior knowledge about what filesystems meant what, how to mount partitions as different filesystems, and what sizes were appropriate, I'd have been completely lost. (I was lost the first time I installed- had to do it about 4x to get it completely right.)  Also especially now with Feisty it doesn't have the gparted frontend anymore and you have to click on 'edit partition' and choose how to mount it (various options including /, /home, /boot, /windows or /dos for ntfs/fat32 ...etc). If I had no idea what I was doing, I'd never want to "edit partition" in the first place! That sounds like I'll have to repartition my disk if I'll do that, not necessarily giving me options on how to mount it. (And by the way, what complete newbie knows the word 'mount' anyway?! I sure didn't...)  

I agree with part of your rant in that the installation process should be as painless as possible. All thats needed in the "manual" installation are simple explanations along the way. Define mount. Define what the filesystems are. Define appropriate sizes for filesystems according to user types. Define what swap is and what an appropriate swap size is. Click here to choose what filesystem this partition should represent, and so on... Please let me know if this helpful documentation is included on the liveCD. It may be that in my hurry to install I have always just missed it. 

I'm a huge Ubuntu fan and I will never go back to using windows for my day to day tasks.  We have an amazing product here to offer and I hate to see people turned away at the beginning just by the silly installation process thats hard to figure out.

---

### Post by lazyart on 2007-05-17
> **raidet said:**
> The first couple of screens were very impressive. A GUI locale selector and simple questions about keyboard layout. Suddenly someone sits on the end of the piano, hitting a minor chord that felt like a sharpened rake across the frontal lobes. The question "guided" or "manual". Guided consuming your entire disk, and "manual" apparently allowing you to try Ubuntu without destroying all the data you own. Naturally I went for option 2. 

Ok, you know nothing about Ubuntu, so when asked if you wanted to go guided or manual, you chose manual.....?  Trying it out means NOT installing it, just running the CD... just like it says when you fire up the live CD.

> That's all well and good until you encounter *true* stupidity.

You couldn't have put it any better.

---

### Post by derred on 2007-05-17
Sorry your first contact with Linux was so unpleasant but you have to admit that if the roles were switched and you were installing windows for the first time it would have been even harder. 
I mean there's no Windows live CD to check out if you even like the OS or if it works with your hardware, hardware that requires driver cd's of it's own, hardware that is useless without software like MS Office, Photoshop and so on.

So let's recap: 
Linux - live CD, most stuff supported out of the box, tons of free software
Windows - text based installer(for the first part anyway), a million tons of driver cd's, a fair bit of money on the OS and buckets of money on software for it

I have to admit it's hard to choose.

---

### Post by aysiu on 2007-05-17
> **raidet said:**
> My point is that it's not necessary *at all* to demand pre-existing knowledge of the user at the point of installation just because they don't want their entire drive wiped. I'm sorry, but you can't set up a dual boot without knowing what you're doing--Windows, Linux, Mac, whatever.

> Either default/recommended options can be presented (like Windows) or the options can be explained. There is a default/recommended option. > Just about nobody will trial an OS at the expense of their entire machine, Oh, you mean Ubuntu should create a live CD like Windows' live CD that allows you to run a fully functioning version of the entire operating system using the CD itself and your computer's RAM without affecting the hard drive? I know Windows is way ahead on this one, but maybe Ubuntu will eventually find such a non-intrusive way to try the OS without costing someone the entire machine... > Deliberately making it difficult for normal users to take-up Normal users don't install their own operating systems. Normal users buy the operating system preinstalled or have a "techie" friend install the OS for them.

You seem sadly misinformed about the differences between Windows and Ubuntu. I suspect you've never installed Windows before.

---

### Post by phidia on 2007-05-17
> **ginestre said:**
> [QUOTE=Acglaphotis;2673636]You are "expected"? From who? How hard is to choose the "swap" filesystem for swap? 

-Acgla

Very. 

Though I don't much care for the tone, Raidet has a good point: ubuntu is more accessible than many other distrros, and lots of good folk on this forum and elsewhere try really hard to make it less intimidating, NEVERTHELESS if you're coming in through the windows it can feel pretty intimidating; and a better guide at that precise point of the install process would certainly have helped me. I stopped twice, and spent a couple of days reading up on the options because I was paranoid about making a wrong choice exactly there.... you have to be pretty strongly intentioned to get through that, and most people would have (or more probably, do) frisbeed the cd out into the snow

I came to ubuntu after lots of dabbling with others unix/linux distros. And while I agree that doing some reading and research is important. The above is also accurate. It just may be that through experience many of us have moved beyond this point, but for someone completely new it is a chasm to leap.

---

### Post by Toadmund on 2007-05-17
I found the easiest way to do it is to create or delete a partiton on your HD using partition editor, then tell  it (OS) to install on 'the largest continuous free space' .

I prepared for simplicity.

---

### Post by justin whitaker on 2007-05-17
> **raidet said:**
> The first couple of screens were very impressive. A GUI locale selector and simple questions about keyboard layout. Suddenly someone sits on the end of the piano, hitting a minor chord that felt like a sharpened rake across the frontal lobes. The question "guided" or "manual". Guided consuming your entire disk, and "manual" apparently allowing you to try Ubuntu without destroying all the data you own. Naturally I went for option 2. This is where it got "bad". 

Ok, let's pause here for a second. Are you absolutely certain there were only the two options? I haven't installed from the LiveCD in a while, but I'm pretty sure that there should be 3 options: Guided/Resize, Guided/Wipe, and Experts only. 

> Suddenly I'm expected to have prior knowledge about the internal CLI-level workings of Linux....BEFORE installing it for the first time. 

Yes, manual partitioning assumes that you know these things. The guided mode is there to let you just click and go...otherwise, you are expected to do some reading. 

> I'm expected to understand the function and necessity of the "swap" partition and opt for a filesystem type for it, and the same for the main OS partition. ERROR. 

[https://help.ubuntu.com/7.04/installation-guide/i386/](https://help.ubuntu.com/7.04/installation-guide/i386/)

That's the installation guide. 

> I'm sorry, but demanding pre-existing (and highly detailed) knowledge of your operating system BEFORE it's even installed is ******* STUPID. Many give old Bill a hard time, but I was never asked by the Windows installer to pointlessly involve myself in low-level installation parameters simply because I didn't want my entire drive wiped, with absolutely NO effort made to enlighten the user as to what the **** is going on.

Nice name calling. There is plenty of documentation on Ubuntu.com to cover this issue. If you are out of your depth, don't you think applying a little common sense is in order?

> Chris Morris made a valid point, but he never encountered a world of geeks, with their deliberate obfuscation tactics designed to make them feel superior in some pathetic way. 

Did I just stumble into the Gentoo Forums?

> To the "norms" trying to bring Linux to the masses, here's one tip you frankly should already know: "Let people install the ******* thing before demanding specialist knowledge or your install CD gets frisbeed out the window into the trash where it belongs". 

I agree, but that doesn't mean that someone should think that they should know absolutely nothing about their hardware, or how to do basic things like partition a drive. 

Last I checked, partitioning a drive was neither OS specific, nor was it particularly esoteric knowledge. Partitioning makes good sense on XP, so you can reinstall without losing your data. It's not a power thing, it's about taking control of your hardware, and being smart about how you use it. 

> Geeks will use technology (especially CLI) to promote a sense of their own superiority (they're the only ones with the time or inclination to learn the nuances of every "grep" in an extended shell command). 

CLI users use it because it is FASTER. They can be more productive, which is the point of these little boxes of electronics and cables. It's not about superiority. I recall that I thought something like this when I started with Linux, but as I grew to understand it more, there are many tasks where going to the command line just makes more sense. 

> You have a choice - be a deliberately exclusive geek-toy, or appeal to the masses and apply common sense. There is no in-between._rai

Sure there is. Ubuntu tries to make Linux accessible, while retaining some of the underlying flexibility of Debian...it's appeal is actually walking the line between being powerful enough for a Linux power user, while being "noob-friendly" enough to get past most of the really mundane, tedious, and frankly anachronistic parts of using UNIX based operating systems.

That does not mean that it is a geek toy, and there are alot of good, common sense reasons for why it is the way it is. 

I can't help but think that for someone that was just interested in trying out Ubuntu, you sure seemed to apply little of the common sense you claim in your position, and you certainly had your own agenda. Pointing out that Linux is not Windows is hardly new.

---

### Post by raidet on 2007-05-17
Understand the reason for my choice of tone. It's very encouraging to hear a couple of these responses getting the jist. Infantile geek drivel like "My 4 year old knew by osmosis therefore you should" has to end NOW if open source OS have a future. The time is soo ripe it makes me drool! ...and Ubuntu appears to have the greatest opportunity of all. Come on Ubuntu powers-that-be! Remember the average user, start *properly* tackling the compatibility issue and the war will become *very* interesting. Everyone (even "noobs") despise the arrogance and non-user focus of Microsoft. However, while Microsoft are corporate deal-focused rather than ordinary-user focused, Linux disties are still geek-focussed, despite the beginnings of claims to the contrary. The intolerable thing is that it would take such *simple* changes to bring Ubuntu in line with the true ideals of open source....so make it happen - and quickly!!!! Get everyday users installing Linux, and show them how easily they can still use firefox, and be compatible with MS Office etc, rather than making the whole endeavour a dead-ended techie-masturbation exercise.

_rai

---

### Post by aysiu on 2007-05-17
I won't call you stupid, but I will call you either sadly misinformed or a troll--your pick.

---

### Post by Znupi on 2007-05-17
"Everyday users" **ARE** installing Linux. If you are not able to, it's your problem.

Windows is much harder to install than Linux. **Period**. Just because you banged your head on a trivial task of clicking on "Guided" doesn't mean everybody has to, or that Ubuntu is not noob-friendly.

---

### Post by aysiu on 2007-05-17
> **Znupi said:**
> "Everyday users" **ARE** installing Linux. I doubt this highly... well, maybe you and I differ on the definition of an "everyday user." I don't know everyday users who install *any* operating system, not even Mac OS X.

An "everyday user," to me, is someone who wants to spend as little time on the computer as possible--email, listening to music, maybe some online shopping, and that's it.

I'd say the bulk of people installing Linux now are what I'd call "Windows power users." Typically, ex-Windows power users know a lot about Windows and very little about Linux. They tend to want the latest versions of all the software they use (often even installing beta or alpha versions) and know little tips and tricks about customizing Windows that most everyday users couldn't care less about. Windows power users are also more likely to play commercial PC games (as opposed to Solitaire, Hearts, etc. ... or just console games on Playstation or Wii).

---

### Post by raidet on 2007-05-17
"I doubt this highly... well, maybe you and I differ on the definition of an "everyday user." I don't know everyday users who install any operating system, not even Mac OS X."

Indeed. But the cool thing is that Linux (specifically Ubuntu) is being handed a unique opportunity to make this possible due to the publicity given by the Dell takeup, coupled with a growing mainstream displeasure with Microsoft's corporation-biased "content delivery" paradigm. 

People WILL give Ubuntu a chance if allowed to do so. Just extend the ease-of-use of the first couple of installation screens across the whole process, bundle firefox, apply in-your-face information about MS Office compatibility and the job is done. It would be nice to automate RAID support too - but maybe I'm just taking the piss now.  ;-)

_rai

---

### Post by WilliamKB on 2007-05-17
I agree with 'aysiu'. Most ppl have never installed a operating system and wouldn't be able to if they had to use MS Win.

MS has been doing it for us for so long that COMMON SENSE has become a MUTED SENSE. Most ppl don't want  to think for themselves so when a real computer question happens they don't know what to do. And because they don't know what to do they blame some else for their lack of knowledge.

I would suggest 'raidet' accept that thinking is a requirement of installing an operating system and that means finding the answers he needs by ASKING or SEARCHING. There are a lot of good ppl on this site who are more then happy to help - just ask!

---

### Post by raidet on 2007-05-17
"I would suggest 'raidet' accept that thinking is a requirement of installing an operating system and that means finding the answers he needs by ASKING or SEARCHING. There are a lot of good ppl on this site who are more then happy to help - just ask!"

You're not getting my point at all. People don't need to come to Ubuntu. They won't. Ubuntu needs to go to people. The 99% of ordinary users will stick with the devil they know if presented with hurdles.

---

### Post by aysiu on 2007-05-17
> **raidet said:**
> 
But the cool thing is that Linux (specifically Ubuntu) is being handed a unique opportunity to make this possible due to the publicity given by the Dell takeup > People WILL give Ubuntu a chance if allowed to do so. Just extend the ease-of-use of the first couple of installation screens across the whole process I don't see how these two ideas go together. The whole point of "the Dell takeup" is people *not* having to install Ubuntu themselves. Dell does it for them, just as they do now with Windows.

---

### Post by raidet on 2007-05-17
Thanks for the comments, all. 

Either we can argue in circles, "defending" the status quo in some kind of self-defeating yet face-saving farce, or we can collectively contribute to Ubuntu taking a true step into the mainstream. Now I'm tired and my attention will probably be elsewhere for quite some time - just like your target user base. You get but one chance.  ;-)

Good luck,
Rai

---

### Post by shavenlunatic on 2007-05-17
i picked up Ubuntu a few months ago, I have only ever used DOS/Windows so knew nothing of GNU/Linux or Ubuntu

I didn't read ANY guides, I jumped in both feet first, the installation was fine, infact EASIER than windows when dealing with partitions IMO.  I find a windows installation, managing partitions (either in windows installer or using fdisk from command line) and formatting the hard disk(s) to be **less** intuitive and user-friendly than Ubuntu.

Putting it this way, if we wiped my brain of all Operating System knowlefge, sat me in front of 2 PC's and got me to setup ubuntu on one and XP on antoher.. then pick which I want to keep, it would be Ubuntu.  YES both would have problems, YES I would struggle with both etc... but come on, the ubuntu install REALLY couldn't be easier, I think you seem to just think windows is "easier" purely because it's what you're used to


just because it's familiar doesn't make it better



just my 2p, counts for nothin' :)

---

### Post by aysiu on 2007-05-17
> **raidet said:**
> 
Either we can argue in circles, "defending" the status quo in some kind of self-defeating yet face-saving farce, or we can collectively contribute to Ubuntu taking a true step into the mainstream. I'm glad you said that.

If you want to contribute to making Ubuntu a better OS, try one of more of these methods:
* Propose a feature for the next Ubuntu release: [https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)
* Donate some money to Ubuntu: [http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations)
* Contribute code if you know how to code
* Write/revise documentation
* File bug reports when you encounter problems
* Help new users with their problems

---

### Post by Znupi on 2007-05-17
aysiu, you read my mind. That was exactly what I wanted to say. You want Ubuntu to be better? Help it by contributing with code / bug reports / etc. This is the basic idea of free, open-source software. It's community-based... So instead of clicking "Send Error Report" in Windows, you log in to this forum and click on "Create New Topic". It's the same thing, only here you will actually get a response, and not be sent to a webpage not even closely related to the problem you're experiencing...

---

### Post by ginestre on 2007-05-18
May I edit one of Aysiu's post to give my summary of the position of most posts here? 
<quote> 
I'm sorry, but you can't set up ........  without knowing what you're doing--Windows, Linux, Mac, whatever.
</quote>

And of course this is right. However, Raidet has made a very strong argument: a lot of people are intimidated here, and only the strong will survive. This is a great pity if it is avoidable. 

But what if the  two positions were not  incompatible? What if the information needed were somehow provided at this point? For me -as a writer of educational materials for other subjects than computers- it seems essential to give newcomers the  knowledge they need AT THE POINT the knowledge is needed. That is when your learner understands that (s)he actually has a knowledge gap, and wants to fill it. When there is a need to know coupled with a desire to know, coupled with access to information, you have a newly-empowered learner.  It's a very, very strong force for growth. 

If you (we?- I'm still very new to this business, but I begin to feel at home) can give clear, un-frightening useful information at that exact moment, neither before nor after, then you have set the scene for the information to be both taken and used: and taking information and using it is generally called 'learning'. 

A lot of posts here insist that newcomers should study before coming, at least a little: but studying and learning are not the same.

As a side point, I'd be happy to give some time, input and maybe even help to tidying up the "newbie user experience" at point of delivery, if someone would be kind enough as to tell me where to aim my efforts.

---

### Post by shavenlunatic on 2007-05-18
> **ginestre said:**
> 
A lot of posts here insist that newcomers should study before coming, at least a little: but studying and learning are not the same..

I've never found these forums and its contributors to be anything but useful.  Most questions are usually responded to within minutes and either provide a decent answer or pointing in the right direction.

It helps nobody to basically go onto a forum and say "bleh, this sucks, I don't understand it therefore it should be better" rather than saying "I'm struggling with [scenatio] and I'm new to linux, could someone help me / point me to the information?"

I have used the latter on several occasions and received nothing but helpfulness and wilfullness (is that a word? :) ).  I would expect little to no help is i posted the prior

---

### Post by lazyart on 2007-05-18
It's the same thing over and over... You'll get someone who walks in, has trouble or doesn't quite understand the installation process. Presuming that this "Linux for Human Beings" equates to "so easy a child can do it" they are insulted and therefore lash out against the community who has adopted this (in their eyes) "so easy a child can do it" operating system.

Anyone who is prepared to be humbled, will admit that they are in foreign territory and will ask for guidance should do just fine.

The others will post as such, whine and moan, then will put in their "system restore" disk and swear up and down that installing Windows is so much easier.

The going rate in town to install Windows is $150.  Once you've done it a few times you know how to get around certain problems, understand the true worth of a NIC driver, and know that it will be hours before all the updates are run.  But it's priced that way for a reason.

Hey, we like our OS and will defend it.  I'm long past saying silly things like "M$" and "Microshaft"-- it's all about what you want and what works for you.  Admittedly, we listen better to a soft voice than one hollering and insulting what we like.

Criticism is good when delivered correctly.  We all made it through the install process.  We'll happily help anyone who asks.

---

### Post by compmodder26 on 2007-05-18
I think ginestre has a valid idea.  I know the installation on the live CD gives you the opportunity to open Firefox and ask a question during any step.  But how about on the first partitioning screen, give a link for the user to click on to look at the installation guide.  Or even add another link for the the forums as well.  That would go a long way to help the user figure out the partitioning step.  I certainly don't think that would be hard to implement would it?

I think the other steps are pretty self explanatory on their own.

---

### Post by ginestre on 2007-05-19
> **compmodder26 said:**
> ... I know the installation on the live CD gives you the opportunity to open Firefox and ask a question during any step.  But how about on the first partitioning screen, give a link for the user to click on to look at the installation guide.  Or even add another link for the the forums as well.  That would go a long way to help the user figure out the partitioning step.  I certainly don't think that would be hard to implement would it?



That would certainly have gone a long way towards reassuring me!  And I really think reassurance is a not a bad thing to build into any process where a newbie is possibly going to be not quite brave enough to go it alone, because of either real or perceived risks...... 

And here's another threepenny thought of mine:  I'm not sure the comparison with paying for a windows installation is a helpful one, even though it is self-evidently true that a windows user in difficulty can usually pay and get it done. However, while this fact gives us some sense of the market value of helping people install operating systems, at least here in my part of Sicily I know of no-one  selling parallel services for ubuntu, or for linux. So once we've established our market value, and acknowledged that there is always going to be a minimum level of difficulty,  we haven't actually helped anyone do anything concrete...

---

### Post by lazyart on 2007-05-19
Again, that goes back to "Linux for Human Beings" vs "Linux so easy a kid can install it".

Maybe there should be a pop up window for the first 6 (arbitrary number) logons reminding that there is help in the ubuntu community?  Some people will feel they are insulting their own intelligence by asking for help... you can't get to them no matter what.

---

### Post by Toadmund on 2007-05-19
Actually it's smart people who ask the most questions, how does one think they got that way?
And there is always someone out there who knows more than the next guy/girl, ask him/her.

---

### Post by guitarchris on 2007-05-20
If Raidet is so experienced that he thinks he can install Windows then I just don't believe he can't manage to install Ubuntu. The "Guided" options are just that - guided. While I may not know what a "swap" or "/" partition actually are Ubuntu offers defaults and enough info for me to do the neccessary anyway. I think Raidet is more interested in undermining us and wasting our time than anything else, perhaps he has a hidden agenda?
Whatever let's  hope he keeps his promise and occupies himself with trampling sandcastles and kicking balls into the long grass or whatever it is he amuses himself with.
I am of the opinion that for anyone interested enough to try Ubuntu with an open mind the installation process is already fine (even very good) and leaves Windows in the dust. Any more simple and it would become patronising.
BTW I am not a geek but a musician with limited funds and a firm belief in community power. Previous attempts at using Linux were stalled by how much time it was taking me to understand the basics of getting everything working (especially the music-making side), dependency hell etc. but  with Feisty 7.04 I had a fully functioning set-up in 30minutes.
I feel very sorry for poor old Raidet, preferring the grumpy corner to the verdant pastures of Ubuntu land. I hope he tries again but this time in good faith. It really is NOT hard if you really want to.

---

### Post by sandman55 on 2007-05-20
Smart people check out the forums from their windows computer and ask questions and when they feel comfortable they give it a go. The people on this forum are very helpfull.

---

### Post by guitarchris on 2007-05-20
How right you are, Sandman. i'm writing this on my W2k box - but it's days are numbered. Heh! Heh!

---

### Post by DFreeze on 2007-05-21
> **guitarchris said:**
> While I may not know what a "swap" or "/" partition actually are Ubuntu offers defaults and enough info for me to do the neccessary anyway. I think Raidet is more interested in undermining us and wasting our time than anything else, perhaps he has a hidden agenda?
...
I feel very sorry for poor old Raidet, preferring the grumpy corner to the verdant pastures of Ubuntu land. I hope he tries again but this time in good faith. It really is NOT hard if you really want to.

Allthough I'm tempted to agree with you, I can recall my first time installing Linux. I did some reading upfront, but being presented with options during partitioning was daunting, to say the least. There was no 'automatic' mode, so I had to make partitions and give them names (/swap, /home, /, ...). I was installing on a fresh harddisk, so I thought: what the heck, I can always do it over if I fail. And I proceeded without really knowing what I was doing. Two years later I&#8217;m still a 100% Ubuntu user, so I ended up doing it right, but raidet makes a point. Not everyone proceeds when in doubt. There are areas where I'm less certain than computers, and I would've quit if I was not certain I was doing it right. For many, computers are such an area...

How hard can it be to explain the options in a little text-window. I didn&#8217;t know that an installation at least needs a / partition. Only after trying to proceed with the installation I was given that info. Maybe a little text explaining that a minimal partitioning scheme contains a / and a /swap partition. 
Furthermore, like someone else mentioned, give the filesystems a default value, so that users that don&#8217;t know the differences, get a feeling that the settings are &#8216;secure&#8217;, that they are not about to mess things up. 

I know that is basic linux knowledge, but it doesn&#8217;t hurt to copy / paste some of it from the help.ubuntu.com into the installer. By the way, I couldn&#8217;t find an explanation of the filesystems and recommended partition layout in help.ubuntu.com easily. 

What raidet is saying, with a bit of a spicy sauce, is that we can improve in this area. I think he is correct. Maybe the installation-procedure is better and simpler than ever, but adding some cherry-picked explanation info would hurt no one. 

But I agree with the &#8216;fine: here&#8217;s how you contribute&#8217; attitude. It&#8217;s nice that someone finds something to improve, just don&#8217;t rely on others to make your voice heard. Make a specification, file a bug report, or if you&#8217;ve never done anything like that before: ask how to do so.

---

### Post by shavenlunatic on 2007-05-21
but the whole point is, during a windows installation, you are presented with the SAME options, but in (IMO) a less user friendly fashion, also during a windows install you have no connection to the internet, during ubuntu install you can have firefox running!

Both windows AND Ubuntu require you to sort out your partitions on a fresh install

---

### Post by ankursethi on 2007-05-21
Duh. It's a LiveCD. Start Firefox and search the forums for some kind of help. And if you don't know how to partition a hard drive, then you're probably **not** one of the geeky types because Windows requires the exact same knowledge. Does calling a partion C: or sda1 make any difference?

---

### Post by ginestre on 2007-05-21
I don't understand why there is so much resistance to providing extra help.  Fine, most of you don't need it.  But some of the rest of us, do. Is that so bad?

---

### Post by DFreeze on 2007-05-22
> **shavenlunatic said:**
> but the whole point is, during a windows installation, you are presented with the SAME options, but in (IMO) a less user friendly fashion, also during a windows install you have no connection to the internet, during ubuntu install you can have firefox running!

Both windows AND Ubuntu require you to sort out your partitions on a fresh install

Exactly, so both still have some improvement to do. Saying that the other guy does it too, doesn't help much in improving the situation.

---

### Post by aysiu on 2007-05-22
> **DFreeze said:**
> Exactly, so both still have some improvement to do. Saying that the other guy does it too, doesn't help much in improving the situation.
Maybe you missed the first post in this thread: [quote=OP]Many give old Bill a hard time, but I was never asked by the Windows installer to pointlessly involve myself in low-level installation parameters simply because I didn't want my entire drive wiped, with absolutely NO effort made to enlighten the user as to what the **** is going on.[/quote]

---

### Post by kelvin spratt on 2007-05-22
The Person who started this thread do they read the contents of a CD before they buy, do they study before taking exams, do they check what's on the tv before watching, check the film
before going to see it, check where they are going before driving a long way where they have not been before. these may seem stupid questions. But the answer to the question  is the the last word of the HEADER.

---

### Post by ginestre on 2007-05-22
I'm worried this thread has lost its way, or perhaps I shouldn't be following it. Maybe it's just not what I thought it was when I happened into it accidentally. 

Anyway, as a moderately experienced computer user who has been installing ubuntu for the last two weeks or so, with great pleasure, lots and lots of consistently kind help from you folks out there, as well as a fair amount of unexpected difficulty in places I really didn't think would be difficult (PRINTING!), the orignal post on this thread had some resonance for me, even though I confess I didn't like the aggressive tone at all. However, leaving the slanging match aside, it seemed to me in my ingenuity that this might be a golden moment to give back something to the community that has been so helpful to me: and a few suggestions for 'improving' the install process seemed a good way to do this. After all, I at least still have it fresh in my mind, and would dearly like to offer some feedback, if it's thought to be useful: but this isn't apparently the right place. Can anyone point me at the right place for constructive dialogue on this issue?

Another consideration, for what it's worth: aside from the issue of what is easy or difficult on a computer, many people who install also have a language barrier to deal with, and a greater degree of clarity and support will certainly help not only the technologically challenged, but also the linguistically challenged without taking anything at all away from those of you who already know it all.

---

### Post by ankursethi on 2007-05-22
Okay, **how** do you want the install process to be? Go on, everybody's listening.

---

### Post by LaRoza on 2007-05-22
I don't think installing an OS should be an *easy* process.

Take into consideration the numerous set-ups people would want. If the process were a "click here and wait" process, it would be easier for one type of setup, with the options now, the **user** has control. Taking control away from the user is a very bad idea.

Some users do not have enough knowledge to make such decisions. This is understandable, because the OS has not been the users choice. You got Windows and windows only if you were an average user.
 
If people had to buy everything and assemble everything and nothing was preinstalled, only those technically knowledgeable would use computers. It was like that once, and experienced users often do buy everything separately and then build their own computer to their own specifications.

People may complain about technical terms and not understanding, but the truth is:

**A computer, hardware and software, is technical by its nature.**

If you don't understand something, ask. Don't try to simplify something just because you don't understand.

This page explains it: [http://www.computerjokes.net/105.htm](http://www.computerjokes.net/105.htm)

---

### Post by lazyart on 2007-05-22
Which brings me back to a not-uncommon misconception about Ubuntu, and could be filed as a bug report:

"Linux for human beings" does not equal "Linux simple enough to be installed by any human being".

---

### Post by ginestre on 2007-05-22
> **ankursethi said:**
> Okay, **how** do you want the install process to be? 


Despite reading up for almost two weeks on the web and in books- and with the benefit that all of the information I had was readily available in English, which is a language I don't have problems with- and after also having used the live CD for sessions of "work" to gain familiarity with the way ubuntu works, I didn't realise that the web was available DURING the install process until I read it somewhere in this thread. So during my first installation, whenever I hit an uncertainty or a worry (and I hit several)  I needed help. I got lots of good help from these forums, but I thought I had to abort the installation and boot windows to be able to come to the web and ask: which I did maybe four or five times. This  considerably lengthened the installation process, and undoubtedly tested my resolve to ubuntu.   If I have understood correctly - that installing from the live CD would have permitted  me to suspend and consult the forums- then that is a FANTASTIC opportunity to help people like myself to help ourselves. Improving things could be as simple as flagging this more visibly.

It's not about making it simple, or about taking options away. It's about making the options that exist accessible . In Sicily where I live, I find it's very easy to get lost when I go to a new place. Perhaps it's just me, perhaps I shouldn't drive. After all, there are always taxis.  It's not that there aren't any road signs to help- there are lots. But they are generally all very small, and oriented away from the road. If you want to read them, you have to pull over, stop the car and get out. It makes getting there very frustrating. But you get there in the end. Installation needn't be like that: the forum is a great GPS.

---

### Post by LaRoza on 2007-05-22
It is easy to get frustrated, I sympathize with you, but remember, it is easy to get answers too:D.

---

### Post by KillerKlown on 2007-05-22
> **justin whitaker said:**
> 

I can't help but think that for someone that was just interested in trying out Ubuntu, you sure seemed to apply little of the common sense you claim in your position, and you certainly had your own agenda. Pointing out that Linux is not Windows is hardly new.

thank the creator, for that....i'm a broken carpenter,  with rage issues...(head injury, i'm not a prick, lol), i don't know squat about computers, i smoke METRIC TONS of weed, and have managed to install 6.06, 6.10,and 7.04... dude, I SHOULD NOT BE ALLOWED ANYWHERE NEAR A COMPUTER!!!!, AND IF /I/ CAN PULL IT OFF, YOU CAN TOO.......

i went and bought me a brand new320g HD for the ubuntu os WHEN I GET IT RIGHT... i still have my XP os on the other HD just so i can do my every day tasks, like chattin', lookin' at porn, playin' vids, and luring young single mothers to debauchery, and animal lovin', this has been a learning  prosess for me, but when i get the TV running, the soft shone, and all the other "take over the world" type stuff up and running, i'll return to the ever ending battle to get my spinning desk top stable...and then , old bill will have, truly, a nightmare on his exceedingly wealthy hands :-({|=

---

### Post by ankursethi on 2007-05-24
Here's an idea : Ubuntu could come preinstalled with XChat and there could be a shortcut to :
1. launch XChat and login directly to the #ubuntu or #ubuntu-support (whatever that channel is) after asking the user his name and alternate name(s) ;
2. a file that explains quickly how to install Ubuntu and links to other files which contain more detailed explanations ;
3. these forums

All that on the desktop or in a separate menu called "Help" or a folder on the desktop named "Help". Or something like that. The LiveCD could also launch an HTML page in Firefox on startup explaining what help options are available.

This ought to stop these "Ubuntu is hard to install" complaints.

---

### Post by regomodo on 2007-05-24
Have you ever done a fresh install of windows? 

Granted, i don't like the new partition tool in Feisty, nowhere near as intuitive as Edgy's.

---

### Post by 3rdalbum on 2007-05-24
> **ankursethi said:**
> Here's an idea : Ubuntu could come preinstalled with XChat and there could be a shortcut to :
1. launch XChat and login directly to the #ubuntu or #ubuntu-support (whatever that channel is) after asking the user his name and alternate name(s) ;

XChat did used to come installed with Ubuntu, and set up to automatically log into #ubuntu @ irc.freenode.net.  Unfortunately, it doesn't come with it anymore; bad move, devs!

---

### Post by sprinkles on 2007-05-24
I think what the problem here is (sorry if it's been mentioned, I don't have time to read the other 2 pages) that his Windows partition was mounted. This stumped me when I was doing an install yesterday, as last time I install the windows drive didn;t automount.

---

### Post by blacksadness on 2007-05-25
hey,
Well first of all let me say i'm an experienced gentoo user, i moved to ubuntu for 2 main reasons, i was trying it out and i liked the simplicity, and it's faster to get what i need going, anyway about the topic, well he obviously did miss an option as i installed ubuntu on many pcs and i've seen a guided option to resize the windows partition, though i never really tried it as i did the resizing (when needed) with GParted. But i could say that the installer, from what i experience, can be improved to target more users, for example there could be an option to choose what partition to resize (naming them C:\ and D:\ so the user will know what he needs) also one more guided option to get the user first free up the space he needs then choose automatic i say this after i tried installing linux on my friends' laptops they wanted to delete a partition and install ubuntu on it, well i had to either do a manual configuration or free up the partition with gparted.
So here are the suggested steps:
"Guided" --> List box to choose a partition --> Resise and Delete options,  --> Use newly freed space.

Another suggestion in the partitioner is to ask the user if he wants to seperate his home partition (refering to it as documents) explaining how if needed to reinstall this would preserve all settings, i usually keep my home partition seperate and would simply commit suicide if i loose it ;) 

Anyway just some ideas, and i would be happy to help out coding it (and others) as soon as i finnish my exams, but that's another thread.

---

### Post by ginestre on 2007-05-25
> **blacksadness said:**
> ....
So here are the suggested steps:
"Guided" --> List box to choose a partition --> Resise and Delete options,  --> Use newly freed space.

Another suggestion in the partitioner is to ask the user if he wants to seperate his home partition (refering to it as documents) explaining how if needed to reinstall this would preserve all settings, i usually keep my home partition seperate and would simply commit suicide if i loose it ;) 
.

Thank you, blacksadness. That's a very succinct expression of what I would have liked to have had. Marry it to a more explicit means of connecting to the forums for extra help if needed, and bob's your uncle.....

---

### Post by tbuss on 2007-05-26
**raidet,**

I've been a Ubuntu user for about 2 months now. My first os was winxp about 5 yrs ago. I'm not sure why I made the switch, I just felt there had to be more than what I was experiencing. I have had many frustrating moments with Linux; and I wanted to quit many times. And yes, there have been folks that I would consider condescending at times; almost understandable but not entirely. With that said, I absolutely believe in Ubuntu. It's hard to explain (and may sound corny) but I really feel like I'm part of something unique; something I never felt as a windows user. Installing and configuring Ubuntu can be difficult, but only if you allow it to be. If your serious about using open source software, and you have considered the pros and cons before making the switch; then take it a step further and research what you might need to know as far installing. I've tried many distros before I landed on Ubuntu. There was about a 6 month time frame of installing, testing, uninstalling and reinstalling something new before I found one that suited me. To me that's key: 'before I found one that suited me'. 

Is there room for improvement? Yes, always. Can constructive criticism be hard to handle? sometimes. I'm not sure why you are so adamant about Ubuntu not being ready for the masses (or being a legit contender in the battle of the OS's) because you consider the installation to be particularity confusing or hard to follow for some users. You seem intelligent enough, your background suggest you have a fair amount of computer experience. Get involved. I know you see that phrase often in the forums and chats; but if there is something you feel could be improved on, instead of ranting about it maybe collaborate with some other users and see what happens. 

Nothing good ever came easy...

---

### Post by youspeakmylanguage on 2007-05-27
Call me paranoid, but if I were Microsoft it would seem to me to be a good investment to hire a room full of folks who spend 8 hours a day posting garbage to Ubuntu Forums. Garbage like long rants about how hard it is to install Ubuntu, how difficult it is to make the transition from Windows, how Ubuntu and GNU/Linux in general isn't ready for the desktop. Bonuses would be awarded for impassioned statements like "You had your chance to convert me to a Linux user! Now I'm going back to Windows!" or "Only geeks can figure out this Linux stuff!"

From this point forward I don't think we should waste our time even answering people who are rude, obnoxious, and/or completely unwilling to do the most basic research. Otherwise we will eventually be buried under the weight of these posts once the Dell newbies start finding their way here and it becomes important for "others" to sabotage our support system.

---

### Post by ginestre on 2007-05-28
> **youspeakmylanguage said:**
> Call me paranoid, but if I were ..........

With enormous sadness I realise you may have a point.

---

### Post by Kourosism on 2007-05-31
> **raidet said:**
> So, I downloaded Ubuntu and cranked it up at boot. Woo! A CD-based startup to sample the delights - bootiful! But never mind that - I want this thing on my disk, so went to "install".


This was what really stood out for me when I read the original OP.

I'm a real Linux newbie, but one of the very first things I did before installing Ubuntu was play around on the Live CD. In fact, I did so over several, across different releases. I can understand being eager, but after 15 years of usin Windows I wanted to make sure Ubuntu more or less does what I want/ And in the process, I learned a little about it.

I do agree with the OP that installing it can be a little overwhelming for a new user, especially if they haven't installed an OS before. Maybe this is something that can be taken into consideration in future - a few more introductory screens, describing what each step does may be useful for some people.

That said, I also feel that, in his eagerness, the OP must take some responsibility. Instant gratification is rarely that - rather it is usually tinged with disappointment. Take your time, learn a little... you may decide that Ubuntu isn't for you, in which case you've saved yourself unnecessary aggravation. You may decide that it is, and therefore have helped to prepare yourself for the years of computing ahead.

---

### Post by raidet on 2007-06-01
Good of you to retain the thread. I only hope that you understand the point was made with the force I thought necessary to raise attention - not to undermine Ubuntu, but quite the opposite. I, like many other users, am sick to the back teeth of the increasingly non user-centric stance Microsoft takes with each new release. With some of the more unsavoury "features" of Vista being made public, ordinary users are for the first time beginning to feel distrust toward Microsoft. Google will fill this market gap soon unless some excruciatingly simple steps are taken by Linux disties like Ubuntu to reach out their hands just a little more. And no other distie is better placed due to the recent global publicity granted by Dell. Linux can remain a geek toy forever, or it can go mainstream and change computing for all, for good. It's that simple. If it goes mainstream, some will complain, but the other 99.9% will use Ubuntu and experience some of the joy us "geeks" experienced during the 80's, when we plugged away at the rubber keys of our Spectrums - playing, programming, exploring; safe in the knowledge that this wonderous device before us was ours, and ours alone. May the joy of computing return, and this time to all.

---

### Post by ticopelp on 2007-06-01
I'm not that much of a geek, and frankly I found the installer to be very clear and intuitive in what it does. The OS is fully operational from the live CD without putting anything on the hard disk. If you didn't know what you were doing -- and, plainly, you didn't -- you should have used the guided install or done a little research before potentially blowing away your hard drive. 

That has nothing to do with Linux; I would say the exact same thing to anyone who was trying to upgrade or install a new Windows OS: back up your data, block out a good chunk of time, and prepare for the worst., and most of all, have some clue what you're getting into. I say this as someone who's blown away perfectly good installs on many occasions by just diving in without paying attention or considering the possible consequences. 

I don't think you're stupid, but frankly, it sounds to me like you got in over your head and found it more convenient to blame the OS. No amount of "reaching out" is going to exempt the necessity of learning.

---

### Post by raidet on 2007-06-01
Take the opportunity to make some minor changes and shoot into the public consciousness, or leave it and eventually become nothing. My point is no more than that, if I have to spell it out in caps. The disenchanted masses will attempt to install if the option is presented, and will succeed if the process is simple enough. They install programs every day, and won't know that "normal users don't install OS" or other such blinkered trash until they try it and fail due to pointless barriers. You know what? I'm off to wank to some porn. I can't be arsed with this.

---

### Post by DucentiVigintiDuo on 2007-06-01
> **lazyart said:**
> 
> 
That's all well and good until you encounter *true* stupidity.

You couldn't have put it any better.

Ouch. Right on the spot.


Ubuntu is not Windows. It's as simple as that.
And besides, correct me if I'm wrong, but I've done 3 installs of Feisty, and there was always a third option: "Guided - use empty space"
or something of the sort.

Finally, if you're willing to try out a system that has its basis on customization and delving into the core of the system, why don't you do some research considering the installation/filesystems/etc beforehand?

I'm sorry to other posters if this has been said before, I'm just exhausted and couldn't find the strength to read through all the pages in this topic.

---

### Post by raidet on 2007-06-01
Intelligence is the ability to avoid doing work, yet getting the work done.
Linus Torvalds 

The irony of this compared to your post is fantastic. The masses have more "intelligence" than you think.  ;-)

---

### Post by ticopelp on 2007-06-01
Go on, son, your porn's waiting.

---

### Post by raidet on 2007-06-01
mate, i can multitask. i got widescreen and 2 hands here.  ;-)

---

### Post by Kourosism on 2007-06-02
> **raidet said:**
> Intelligence is the ability to avoid doing work, yet getting the work done.
Linus Torvalds 

The irony of this compared to your post is fantastic. The masses have more "intelligence" than you think.  ;-)

My word, thou quoth the Torvalds.

Look, I'm glad that you passed your driving test without taking a single lesson, that you aced your University course without attending a lecture, and that you never turn up to your highly paid job because you know it'll get done anyway. Heck, we've all been in that boat, we're all part of the intelligent masses too.

However Ubuntu isn't like the real world, sometimes you do have to learn a little before it does your work for you. It's a bug, maybe it'll be fixed in Gutsy Gibbon.

---

### Post by tact on 2007-06-02
> **aysiu said:**
> I won't call you stupid, but I will call you either sadly misinformed or a troll--your pick.

Exactly...  and had he chosen the first and default option...  
a.  all done automagically
b. repartitioning etc totally transparent
c. dual boot set up with no more input from the user

so easy.  its the person who admits he has no knowledge, choosing a manual option to set things up, making a rod for his own back.

---

### Post by ToySouljah on 2007-06-02
As a new user of Ubuntu (less than a week) I have to say that the install process was actually a lot easier (and faster) than any Windows install I've ever done.  I've installed Windows I don't know how many times and it wasn't a pain, but it was sort of time consuming.  I'd reinstall about once or twice a year just to clear the clutter from installs, uninstalls, as well as various other little things that may have crept into my system along the way...lol.  With Ubuntu though there is a lot to be learned which is great since it keeps me interested.  I love everything about the OS so far (except for my Lexmark being listed as a paperweight...lol).  Other than that everything seems to work much better since I switched.  I ran into a few problems with codecs and a minor issue with my video, but like I said...there is a lot to learn and I love it.  After coming here and looking online I found the answers I was looking for with no problem and have almost everything up and running (still need to get a new printer).  The forums here have been a life saver for about 99% of my issues.  I still have a few kinks I'm trying to workout, but mostly due to me "experimenting" and so it's my fault, but I guess it's part of the learning process  :)

---

### Post by sabrewolf2006 on 2007-06-02
Doesn't the guided install have some sort of algorithm that will generate a partition layout
(a logical one, such as a small-ish space for OS and majority of space for /home and a swap partition relative to the amount of RAM installed in the system) and select filesystem types for the user whilst allowing for the hdd not to be completely wiped..?
All the user would need to do is look it over and click 'accept'..

He's got a point tho.. that big empty gap in the bottom of the installer could come in handy for explaining what's going on above..
A bit like anaconda on Fedora.. it has this block on the left side that explains what needs to done in the right pane...  where the install is taking place
Then it comes down to the user choosing whether or not to read

---

### Post by aysiu on 2007-06-02
> **sabrewolf2006 said:**
> Doesn't the guided install have some sort of algorithm that will generate a partition layout
(a logical one, such as a small-ish space for OS and majority of space for /home and a swap partition relative to the amount of RAM installed in the system) and select filesystem types for the user whilst allowing for the hdd not to be completely wiped..?
All the user would need to do is look it over and click 'accept'.. This is, in fact, the case. If you just follow the directions, a logical partition layout happens automatically.

> He's got a point tho.. that big empty gap in the bottom of the installer could come in handy for explaining what's going on above..
A bit like anaconda on Fedora.. it has this block on the left side that explains what needs to done in the right pane...  where the install is taking place
Then it comes down to the user choosing whether or not to read I agree fully, which is why I proposed this idea:
[ [IDEA]: Tutorial / intro to Ubuntu during installation](http://ubuntuforums.org/showthread.php?t=411481)

And it appears to have been accepted:
[https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-slideshow](https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-slideshow)

---

