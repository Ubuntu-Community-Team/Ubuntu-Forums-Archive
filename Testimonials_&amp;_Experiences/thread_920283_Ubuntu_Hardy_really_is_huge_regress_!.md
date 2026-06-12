---
title: "Ubuntu Hardy really is huge regress !"
date: 2008-09-15
forum: Testimonials &amp; Experiences
---

### Post by alex_ndc on 2008-09-15
I am a passionate computer scientist, and I'm using Ubuntu since Dapper. Since I am mainly a Unix programmer, I really prefer Linux. But I am apolitical, I don't really give a damn about "free as in free speech", and I also use Windows and Mac OS X, whatever gets the job done.

But lately it seems that all major distributions have more and more problems, and by major I mean Debian, Ubuntu, OpenSuse and Fedora.

And I just had to get it out of my system: **Ubuntu Hardy is the worst release yet.**

System crashes, keyboard layout not working properly, keyboard layout not working at all if auto-login is activated, a Firefox that slows down the system to a grinding halt, windows network not visible, system not starting without setting "irqpoll" in Grub, dependency problems, and I've only used it for two weeks.

Every time I found a problem, I checked in LaunchPad and all these errors have been reported. And some of them are there since Feisty.

Worst of all ... I expect to get tons of "works on my machine" replies.

Thanks,

**[COLOR="Red"]UPDATE[/COLOR]**

There are two reasons I posted here:
[LIST=1]
[*]To warn new users that Ubuntu Hardy has some issues
[*]To relieve myself from the stress, and pass it on to others :) (I'm joking of course, but this is something humans do)
[/LIST]

I hate "*works on my machine*" replies, because such replies are given as a way to demonstrate somehow that the complainer is wrong, or meaningless. As one reply said ... it works for most other people.

And yet, some of the problems I experienced are in Launchpad, so I guess I'm not the only one.
[LIST]
[*][A GNOME login without keypress doesn't set GNOME keyboard settings]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277")
[*][keyboard layout shortcuts dont work with automatic login enabled 8.04]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/226129")
[*][Unable to boot 7.10 on abit ib9 due to ata xfermode](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/172300) (yeah, this is an older bug that still reproduces on my machine ... yet it works on OpenSuse 10.3 and 11 just fine)
[*][font in terminal does not resemble font in preview](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848) (I experienced blurred fonts in gnome-terminal since Gutsy, I still have the same problem in Hardy, but it works fine with Xfce's or Kde's terminal or OpenSuse's gnome-terminal)
[*][various bugs related to Firefox crashing in Hardy](https://launchpad.net/+search?field.text=hardy+firefox+crash&field.actions.search=Search)
[/LIST]

You see, there's a difference between a big software company like Microsoft, or Adobe, or Google and this community ... they care about their customers enough to not reply with "*works on my machine*". And when they do a minor mistake, thousands of people cry in anger.

I don't want help, I just wished those problems would get solved. I attended the last Mysql conference in Santa Clara and guess what: 50% or more of the attendees had Mac Books. And another 40% had Windows. I also went to Yapc, and an overwhelming majority of the attendees also had Mac Books. With all this talking about Linux "being ready for the desktop" and about "world domination 201", Linux is leaving behind the people that actually matter: Unix developers that are currently fleeing in droves to Mac OS X: because Mac OS X usually just works, and the quality of the delivered tools is getting better and better. The latest version even comes with DTrace and a ZFS port is also available.

And it's funny when I think that Dapper and Feisty, and even Gutsy after the initial bugs got fixed ... those where pretty decent versions. But with every release it gets worse.

So yes: while you can ridicule my choice of words, I advise people to stay away from Hardy and from these forums.

**PS:** if you really need Ubuntu Hardy, try Xubuntu. It is more stable (probably because it doesn't do much). Faster too.

---

### Post by Crafty Kisses on 2008-09-15
A lot of people are having issues with Hardy, personally I'm experiencing none.

---

### Post by ukripper on 2008-09-15
> **Codename said:**
> A lot of people are having issues with Hardy, personally I'm experiencing none.

:)perhaps we should consider ourselves (more than 90% of Hardy users)lucky for not having problems the OP explained above, especially coming out from **passionate computer scientist** himself!:)

---

### Post by Greyed on 2008-09-15
> **alex_ndc said:**
> Worst of all ... I expect to get tons of "works on my machine" replies.

Works in my VM.  HA, didn't expect that, did you!  :P

Seriously, if your a computer science person and you've checked Launchpad about these bugs and found them there since Feisty I have two questions.

A: How could it be a regression if it was there previously and...
B: Since this is happening sporadically as the majority of people who have installed either Fawn or Heron did so without the problems your describing did you do any analysis, report your setup, anything to add to the corpus of data to track down what would be causing the problems?

My guess, no.

---

### Post by BluePlum on 2008-09-15
I'm having all these problems! If you find a soloution let me know, i really wished i had stayed with 7.4

---

### Post by frankleeee on 2008-09-15
I think your all being rick trolled.

---

### Post by derjames on 2008-09-15
As a scientist, I would give the most information I can to my peers so they could replicate the problem and eventually explain it. 
On launchpad, at least Did you take the time to confirm the bugs/problems/ report you hardware?

---

### Post by Idefix82 on 2008-09-15
> **alex_ndc said:**
> I am a passionate computer scientist, and I'm using Ubuntu since Dapper. Since I am mainly a Unix programmer, I really prefer Linux. But I am apolitical, I don't really give a damn about "free as in free speech", and I also use Windows and Mac OS X, whatever gets the job done.

But lately it seems that all major distributions have more and more problems, and by major I mean Debian, Ubuntu, OpenSuse and Fedora.

And I just had to get it out of my system: **Ubuntu Hardy is the worst release yet.**

System crashes, keyboard layout not working properly, keyboard layout not working at all if auto-login is activated, a Firefox that slows down the system to a grinding halt, windows network not visible, system not starting without setting "irqpoll" in Grub, dependency problems, and I've only used it for two weeks.

Every time I found a problem, I checked in LaunchPad and all these errors have been reported. And some of them are there since Feisty.

Worst of all ... I expect to get tons of "works on my machine" replies.

Thanks,

What did you post this for? Was this supposed to be helpful to anybody? You didn't say anything about your hardware or about any attempts on your part to solve the problems. Or did you just want to let the world know that you are a "passionate computer scientist"?
Since, according to you, Linux currently just sucks across the board, I suggest that you switch to Windows and continue your whining on the Windows forums. But don't forget to mention that you are a passionate computer scientist, otherwise people might not take you seriously.

Oh, and yes, on my Dell Vostro 1710 it works, even the 64 bit version, apart from some minor glitches which are far outweight by the user friendlyness and the productivity of the OS.

---

### Post by Samizdat on 2008-09-15
> **Idefix82 said:**
> otherwise people might not take you seriously.


Sure that whining's not an echo from the far side of the canyon?  I'm going to get a cuppa (Ubuntu, of course) joe for this cacophony of ridiculous ad hominems.  Keep 'em comin!'

---

### Post by lukjad on 2008-09-15
I haven't tried Gutsy, and I doubt you have tried Breezy and before. I can say that I have had problems with it but I hear that most should be fixed with Intrepid.

---

### Post by bmac on 2008-09-15
As the Troll anticipated:.
Works on my machines....:lolflag:

---

### Post by -Zeus- on 2008-09-15
works perfectly on 8 laptop installs.

---

### Post by Darrell Lawrence on 2008-09-15
Since you are a compassionate computer scientist that prefers using Linux, I would think that you would want to contribute to Linux. Certainly reporting your computer configuration and what you were doing at the time of the incidences occurring would help the folks on Launchpad that work on these problems.

With each new release of any operating system there is a multitude of new hardware to contend with. And since you are a compassionate computer scientist I'm sure that you are aware that even an update to some files may cause problems for some folks but not for others. 

If a new release is an absolute show stopper for you, you can file bug reports to help the developers and go back to the previous release. Each release of Ubuntu has 18 months of support, and the long term releases have 3 years of support. Thus you have the choice of sticking with what works for you for a considerable length of time. And certainly with the Live CD's you have the opportunity to see how well a new release will work on your system without installing it. 

And yes, I'm one of those users were Ubuntu 8.04 works perfectly, including peripherals. I purchased a Dell computer with 8.04 preloaded.

Darrell

---

### Post by Comhra on 2008-09-15
> **alex_ndc said:**
> I am a passionate computer scientist, and I'm using Ubuntu since Dapper. Since I am mainly a Unix programmer, I really prefer Linux. But I am apolitical, I don't really give a damn about "free as in free speech", and I also use Windows and Mac OS X, whatever gets the job done.

But lately it seems that all major distributions have more and more problems, and by major I mean Debian, Ubuntu, OpenSuse and Fedora.

And I just had to get it out of my system: **Ubuntu Hardy is the worst release yet.**

System crashes, keyboard layout not working properly, keyboard layout not working at all if auto-login is activated, a Firefox that slows down the system to a grinding halt, windows network not visible, system not starting without setting "irqpoll" in Grub, dependency problems, and I've only used it for two weeks.

Every time I found a problem, I checked in LaunchPad and all these errors have been reported. And some of them are there since Feisty.

Worst of all ... I expect to get tons of "works on my machine" replies.

Thanks,


I feel sorry for people who are having problems; I guess that I'm one of the lucky ones.  I feel relaxed while I'm using Hardy, the kind of relaxation that come with the knowledge and confidence that nothing will go wrong.  Gutsy was extremely stable on my laptop and Hardy is just the same.  I just love Ubuntu! 

You know, Ibex will be here in 6 weeks time and it's not that long to wait.

---

### Post by ddarsow on 2008-09-15
Hardy works flawlessly for me. Of course I am merely a "passionate law student" and have not attained the coveted status of "passionate computer scientist."

I am a hobbiest programmer / web developer, but that hardly counts. Perhaps they only disperse the faulty code to passionate computer scientists in hopes of them fixing it? Hmm.....anyway, glad someone felt sorry for me a nd made sure I installed a working version of Ubuntu.:)

---

### Post by ukripper on 2008-09-16
> **ddarsow said:**
> Of course I am merely a "passionate law student" and have not attained the coveted status of "passionate computer scientist."


:lolflag: nice one..

---

### Post by ukripper on 2008-09-16
#Just having one post proves this entity is a troll, and not worth even posting anything in this thread as it just want us to keep posting to its headless thread.

But can't help having a laugh at "passionate computer scientist"!:)

---

### Post by alex_ndc on 2008-09-16
Hi people,

Yes this was my first post in this forum. I'm sorry this was a rant, which appears to be trolling.

I felt necessary to mention that I am a computer scientist (as in emphasizing more on science than engineering), but I didn't mention "professional", or anything that would imply arrogance on my behalf ... I just wanted to mention that I know my way around computers. English is not my primary languages, so I'm not familiar with common cliques.

The thread was also posted in "Testimonials" and I felt it was necessary because I do have a love and hate relationship with Ubuntu. On every upgrade, even if I wait patiently a couple of weeks before upgrading, things break.

As a reply said, maybe I should just shut up and contribute, but people, the thing that hurts the most is this holier-than-thou attitude, and some people just don't get it. Do you feel you help Ubuntu by replying "works on my machine"? Or do you feel you are doing anyone a service by calling a frustrated user "troll" or other names? Since when did attacking people instead of ideas became acceptable?

Is this how you help out? Jesus.

---

### Post by lukjad on 2008-09-16
Most people who post and define themselves as "computer experts" are troll, even well intentioned ones. Trolling is just making comments that make people flare up. Even if that is not your true intent, that is the result.

---

### Post by kaldor on 2008-09-16
I like Hardy. But yes, it does have a lot of flaws. Though, I haven't had as many problems since I got 8.04.1.

---

### Post by lazyart on 2008-09-16
> **alex_ndc said:**
> Is this how you help out? Jesus.
Probably if you want to see how we help out then ask a question.  When post #1 isn't a request for help but instead a whiny rant, well you're gonna get what you got.
You see, we are all pretty passionate here.  Some of us are passionate students, some passionate doctors, likely some passionate pizza-delivery folks.  But we are all pretty passionate about the choice that Ubuntu affords us.
If it's not working for you, ask a question and someone will answer it.  If you can't take the time to ask for help, but can take the time to piss and moan... well, we can't really take the time to take you seriously-- we have people who are looking for help.

---

### Post by fiddledd on 2008-09-16
> **alex_ndc said:**
> Hi people,

Yes this was my first post in this forum. I'm sorry this was a rant, which appears to be trolling.

I felt necessary to mention that I am a computer scientist (as in emphasizing more on science than engineering), but I didn't mention "professional", or anything that would imply arrogance on my behalf ... I just wanted to mention that I know my way around computers. English is not my primary languages, so I'm not familiar with common cliques.

The thread was also posted in "Testimonials" and I felt it was necessary because I do have a love and hate relationship with Ubuntu. On every upgrade, even if I wait patiently a couple of weeks before upgrading, things break.

As a reply said, maybe I should just shut up and contribute, but people, the thing that hurts the most is this holier-than-thou attitude, and some people just don't get it. Do you feel you help Ubuntu by replying "works on my machine"? Or do you feel you are doing anyone a service by calling a frustrated user "troll" or other names? Since when did attacking people instead of ideas became acceptable?

Is this how you help out? Jesus.

Yes, some people do react to posts such as yours with a less than helpful response.

But you have to remember, there are many posts like yours, and when you are sitting at your computer running Ubuntu without problems, an emotional response is sometimes unavoidable.

Incidentally, I'm not using Ubuntu at this time, hence the lack of an emotional response.

If indeed you do want help to solve your problems, then posting in this sub forum probably isn't the best way to get it.

If you post the specifics of each problem in the Help sections of these forums, people will be more than happy to try to help you.

---

### Post by Idefix82 on 2008-09-16
> **alex_ndc said:**
> Hi people,
Yes this was my first post in this forum. I'm sorry this was a rant, which appears to be trolling.

I felt necessary to mention that I am a computer scientist (as in emphasizing more on science than engineering), but I didn't mention "professional", or anything that would imply arrogance on my behalf ... I just wanted to mention that I know my way around computers. English is not my primary languages, so I'm not familiar with common cliques.


It almost seemed like you were trying to repair the damage and to introduce yourself properly in these forums but then the last part
> **alex_ndc said:**
> 
As a reply said, maybe I should just shut up and contribute, but people, the thing that hurts the most is this holier-than-thou attitude, and some people just don't get it. Do you feel you help Ubuntu by replying "works on my machine"? Or do you feel you are doing anyone a service by calling a frustrated user "troll" or other names? Since when did attacking people instead of ideas became acceptable?

Is this how you help out? Jesus.

was a huge regress!
Basically, many people are on these forums to get help. But a huge number of people is only here to help others. I only joined the forums a couple of weeks ago and I really like this "place" because so many people are so helpful. If you had asked a proper question or had asked for advice, you would have got it. But instead you introduced yourself as somebody who knows everything and has used Linux forever, and so on (sorry, but that's how it came across) and then you went on to just say that the OS is bad, full stop. To put it bluntly to you: yes, people who replied that it works on their machine do think that they help Ubuntu because they hope that you will get duly annoyed at such replies and will refrain from posting completely useless whining threads in the future. Instead you could start browsing the forums and help other people, since you are so knowledgeable.

One more thing: yes, there are bugs in the system. How do you think they get removed? By people using the system, reporting the bugs and by other people fixing them. Almost nobody gets a single penny for working on the development of Ubuntu and its progress relies on the community. It's certainly much easier to use the system and when something doesn't work to say so, than to actually implement bug fixes and develop the whole thing. So you should be glad that you are doing the easier part (or not doing it, as the case may be), despite being so experienced and knowledgeable and passionate. If you don't like the way open source works, then it's just not for you. But maybe you should think about it for long enough before you decide whether or not you like it, there is absolutely no reason for any love hate relationships as far as I can see.

---

### Post by zombrax on 2008-09-16
2 posts great!! :( Thanks for helping us out, o great computer scientist. 

Ppl MIGHT help you IF you REQUEST/ASK for their help and NOT through a whiny post. Then again I see a pattern of whingers and ppl who complain a lot by the number of posts on here. I'm NOT saying that its a DEFINITE way but there is a pattern, IMHO....

---

### Post by Samizdat on 2008-09-17
alex, your only mistake was in apologizing to these self-important knuckleheads.

> **zombrax said:**
> Ppl MIGHT help you IF you REQUEST/ASK for their help and NOT through a whiny post.

There's plenty of whine for everyone in this thread, chum.

---

### Post by ElanVital on 2008-09-17
As a recovering self-important knucklehead, I resent your comment Samizdat. ;)

---

### Post by BlueFiberOptics on 2008-09-17
I will say that on release, Hardy Heron was pretty bad.

Now that it has had time to become stable, it's all right for me.

Kubuntu on the other hand, that is a monster that just crashes on me for no reason any time I try to use it.

Oh well, I'm still looking forward to future releases.  :)

---

### Post by StormPCs on 2008-09-17
> **alex_ndc said:**
> 
And I just had to get it out of my system: **Ubuntu Hardy is the worst release yet.**




Finally...someone with a brain.

I'm going to wait until someone gets their head out before I try Ubuntu again.

---

### Post by bmac on 2008-09-17
Hmmm....

I installed a free OS (Ubuntu) and now I'm "**Entitled"** to complain that it doesn't meet all my expectations and requires some effort on my part... This OS really sucks...:lolflag:

---

### Post by darrenn on 2008-09-17
Well I know some mcse's that think they are real engineers.

Just kidding

---

### Post by ammikulka on 2008-09-18
i am not a computer scientist, however i did manage to get ubuntu working flawlessly on my laptop despite some drawbacks......

---

### Post by Idefix82 on 2008-09-19
> **Samizdat said:**
> alex, your only mistake was in apologizing to these self-important knuckleheads.

Samizdat, have a look at the code of conduct for these forums. Just to help you: the important bit is in bold.

---

### Post by ukripper on 2008-09-19
> **Idefix82 said:**
> Samizdat, have a look at the code of conduct for these forums. Just to help you: the important bit is in bold.

Don't worry about Samizdat mate. It just needs to get over itself!

---

### Post by mikewhatever on 2008-09-19
> **alex_ndc said:**
> 
Worst of all ... I expect to get tons of "works on my machine" replies.

Why is it so bad? Are you unhappy it works for others?

> **alex_ndc said:**
> 
As a reply said, maybe I should just shut up and contribute, but people, the thing that hurts the most is this holier-than-thou attitude, and some people just don't get it. Do you feel you help Ubuntu by replying "works on my machine"? Or do you feel you are doing anyone a service by calling a frustrated user "troll" or other names? Since when did attacking people instead of ideas became acceptable?

Is this how you help out? Jesus.

You've said things and got replies, and seem to be unhappy. Note, the replies to your 'testimonial' were not intended to help neither you nor Ubuntu. I am confused, but did you even asked for help?

> **alex_ndc said:**
> I added an update to my testimonial at the start of this thread, since I don't expect people to search for my replies in a thread that's a couple of pages long. Hope you don't mind.

It strikes me as odd, that a computer scientist gets so emotional, and doesn't understand how ridiculous the OP's arguments are.

---

### Post by sargetech on 2008-09-19
Okay, time for me to jump in..** Hardy is cool**, I have really no problem with it except for the login screen being off center
That's it....Which thanks to folks in this forum, has been solved.. My love for Ubuntu is larger than a few bugs...
Free is free, & Free is free :) I love this forum. it has helped me
loads of times, I'm glad I jumped out of XP's & Vistas window....I will not miss them!!!!

using P4 256mb ram, Broadcom wireless card, (which I configured thanks to helpful folks here),48x16x48 benq burner,Avermedia capture card, DVD-Rom drive, all in a (Busted up old case) that is held together with (Spit & Snot) chuckle:)

Peace to all,:KS

---

### Post by MNICY on 2008-09-19
> Worst of all ... I expect to get tons of "works on my machine" replies.Why is that a bad thing? The fact is, Hardy works perfectly for almost everyone. The few people who have problems insist on complaining, but everyone else either fixes the problems or does not have them. As a passionate computer scientist, i would expect you to put a bit of effort into solving your problems instead of complaining about them!

Ubuntu is faster and much more stable then Windows XP or Vista. It may have some bugs, but they are not anything that can not be worked around with a bit of effort. 

My Ubuntu box works perfectly. May Dad's XP box is having horrible problems with the graphics. They are so bad that he can barely play any games (on a $2000 system). Compare that to how well my $700 Ubuntu box plays the same games, on WINE.

Sorry, but just because Hardy does not work for you does not mean it is the "worst Ubuntu ever!".
I have found the releases have improved each time, consistently since i started using in Dapper. 

Remember though, Linux is not for "noobs". You need to be able to have the patience to search through and solve any problems you encounter. (but as i said, if you are such a passionate computer scientist this should not be a problem). 
Its not like with Windows (which has just as many problems in my opinion) where you can take it into the shop and have them fix it for $150.

Sorry, i think i may have flamed a bit.. of course, you are giving off the smell of a troll, so i don't feel so bad.

---

### Post by gjoellee on 2008-09-19
I am using Intrepid Ibex at the moment and I find it both faster and more stable then Hardy...LOL "MORE STABLE THEN HARDY"!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by alex_ndc on 2008-09-20
I added an update to my testimonial at the start of this thread, since I don't expect people to search for my replies in a thread that's a couple of pages long. Hope you don't mind.

---

### Post by lukjad on 2008-09-20
So long as it is clearly defined as an update, that is fine. Also, I would put the date of the update too.

---

### Post by AusIV4 on 2008-09-20
I administer four machines with a variety of motherboards, processors, GPUs, etc. The transition to Hardy has been the smoothest transition since Breezy -> Dapper.

When you give specific problems, we can try to help you to fix them. When you come to the forum and assert "Ubuntu Hardy really is huge regress!" and moan that "**Ubuntu Hardy is the worst release yet.**" we can't do much to help. We're inclined to disagree with you (because our experience has been contrary), and to try and encourage most users that they likely won't face the same, broadly stated problems.

This community tries to be helpful when someone comes politely looking for help. We tend to get defensive when we perceive an attack on our favorite OS. You've stated that you're not looking for help, so we're going to go on the defensive.

---

### Post by Jive Turkey on 2008-09-20
> **alex_ndc said:**
> I am a passionate computer scientist, and I'm using Ubuntu since Dapper. Since I am mainly a Unix programmer, I really prefer Linux. But I am apolitical, I don't really give a damn about "free as in free speech", and I also use Windows and Mac OS X, whatever gets the job done.

If you are a CS why not get involved in fixing some of these problems you've found?

I have to agree with you on some points, I think the developers should focus more on bug squashing and stability issues than new features.  I think there were some bad decisions made in package selection with Hardy too.  One example would be using aqbanking3 that has no consumer in the repos, while aqbanking2.9 could have.  Ive only been using linux for about 2 years now and I'm starting to outgrow these forums as far as the usefulness of the help here, they were very helpful in the beginning though. 

I carefully selected the hardware for my latest desktop for Linux compatibility and I think I did a pretty good job based on my final results.  Incidentally it runs Vista Ultimate x64 quite nicely too.

Edit:"Ready for the Desktop" and "ready for the laptop" I think are two separate things when it comes to linux.  

Good luck finding something that works for you.

---

### Post by alex_ndc on 2008-09-21
> **Jive Turkey said:**
> If you are a CS why not get involved in fixing some of these problems you've found?
Ah, I wish I had the time. Someday in the future maybe.

Currently I installed Xubuntu, with Xfce, and it works better.

I am planning to buy a laptop, and I need one that works with Ubuntu (wifi, suspend). Any tips?

---

### Post by pwaugh on 2008-09-21
Alex,

As a psychologist, I wanted to point out a couple of things:

> **alex_ndc said:**
> I am a passionate computer scientist, and I'm using Ubuntu since Dapper. 


The subject that you used for your post clearly indicates that you are far from being a "scientist".  In fact, your entire post has no scientific "data", only what we who are actually scientists (Ph.D.s) call anecdotal experience.  You can not draw such sweeping conclusions from such experience.  So, please don't make us real scientists look bad by calling yourself one.  =)


> 
Since I am mainly a Unix programmer, I really prefer Linux. But I am apolitical, I don't really give a damn about "free as in free speech", and I also use Windows and Mac OS X, whatever gets the job done.


FYI, Unix is not Linux, and one doesn't "program Unix".  Unix is not a computer language. By this time in your post, most have likely already become as annoyed with you (as a psychologist I'm using my intuition to share with you how others might perceive you in order to help you get more of a perspective on how you come across).


> 
But lately it seems that all major distributions have more and more problems, and by major I mean Debian, Ubuntu, OpenSuse and Fedora.


Again, you state a clearly un-scientific opinion which is completely unsupported by facts.  No one here is interested in your opinion on the state of linux distributions, only on your experience with Ubuntu.


> 
And I just had to get it out of my system: **Ubuntu Hardy is the worst release yet.**


Perhaps for you.  I think you would get a better response from the community if you worded this something like:

"The Ubuntu Hardy release has not gone well for me.  It has been the worst experience I have had with a relese yet."

Then, you would be "owning" your feelings, instead of trying to speak for the rest of us.


> 
System crashes, keyboard layout not working properly, keyboard layout not working at all if auto-login is activated, a Firefox that slows down the system to a grinding halt, windows network not visible, system not starting without setting "irqpoll" in Grub, dependency problems, and I've only used it for two weeks.


Finally, you get to the "meat" and tell us (at least in overview) what you have experienced.  Sorry you have had so many problems, but you need to use a "divide and conquor" approach (which you would know if you were a scientist).


> 
Every time I found a problem, I checked in LaunchPad and all these errors have been reported. And some of them are there since Feisty.


A far more effective approach would be to NOT assume that your problem is a bug, but rather put your massive ego aside and post of the support forums exactly what you are experiencing on what equipment with what software, and see if anyone has ideas for things you might try.  However, your ego prevents you from seeking help, so instead you just complain as then you can blame others instead of accept that you may not live up to your own reified image of yourself.

I'm really being blunt here, because someone in your life needs to be, and you aren't paying me to take 2 years to tell you nicely in hourly sessions.  =)


> 
Worst of all ... I expect to get tons of "works on my machine" replies.


Here your intuition is trying to tell you something, but you fail to see it.  It does work on our machines, and this might be a clue that your ego can't handle.  I bet it could work on your machine too, if you could stop thinking you are such an expert, and start openning yourself up to seeking help.


> 
There are two reasons I posted here:
[LIST=1]
[*]To warn new users that Ubuntu Hardy has some issues
[*]To relieve myself from the stress, and pass it on to others :) (I'm joking of course, but this is something humans do)
[/LIST]


I doubt your reason for posting was so altruistic.  More likely, you posted out of the anger and frustration of your inner child (which is not so inner unfortunately), and wanted to lash out since you could not call "tech support", whine and demand a refund.

Freud often points out that when people say, "I'm joking" they really are not, and this is the case here.  You are correct that "humans" do vent, and it is sad that you see this as a weakness and something that you yourself could never do.


> 
I hate "*works on my machine*" replies, because such replies are given as a way to demonstrate somehow that the complainer is wrong, or meaningless. As one reply said ... it works for most other people.


Yes, you hate being wrong, which is why you should go back to Windows, and will never be a scientist.  Science is about being willing to be wrong, as being wrong is what leads to the knowledge of what is right.  Edison first found 1,000 things that did not work as a filament for the light bulb.  Were it up to you, we'd all still be in the dark.


> 
You see, there's a difference between a big software company like Microsoft, or Adobe, or Google and this community ... they care about their customers enough to not reply with "*works on my machine*". And when they do a minor mistake, thousands of people cry in anger.


This just again highlights how narcissistic you are, and is very insulting to others.  Thank God we have had the opportunity to be educated by you.  What would we have done without you!  I had no idea that businesses cared about their customers!  Wow!  BTW, unlike you, when Microsoft makes a "minor mistake" we don't cry (that's something babies do), we LAUGH, because we are using Linux.  Moreover, most people don't cry over mistakes, they learn from them and accept them as a part of life and "growing up"!  Dare I suggest you grow up?


> 
I don't want help, I just wished those problems would get solved. 

Good thing you don't want help, because:

  a) Your massive ego will not let you accept that you need help.
  b) You could never accept help from others
  c) No one would want to help someone who acts the way you do toward
     others!
  d) There is no need to get help, because you have "wished" they
     would get fixed, so someone will get right on that.


> 
I attended the last Mysql conference in Santa Clara and guess what: 50% or more of the attendees had Mac Books. And another 40% had Windows. I also went to Yapc, and an overwhelming majority of the attendees also had Mac Books. With all this talking about Linux "being ready for the desktop" and about "world domination 201", Linux is leaving behind the people that actually matter: Unix developers that are currently fleeing in droves to Mac OS X: because Mac OS X usually just works, and the quality of the delivered tools is getting better and better. The latest version even comes with DTrace and a ZFS port is also available.


Yes, clearly your perceptions are correct.  In fact, why are you here?  You have clearly seen the future is Mac, so go Mac?  Have you left yet?  How about now?  Damn.


> 
So yes: while you can ridicule my choice of words, I advise people to stay away from Hardy and from these forums.


Even your own unconscious is desperately trying to tell you that your words are deserving of "ridicule".  This is because this is a recurring theme in your life.  Please get some help, so your life can be better.


> **alex_ndc said:**
> Ah, I wish I had the time. Someday in the future maybe.


You have the time to post this garbage, but not to actually do anything about your problem?  You definately should go MAC.  This is NOT the OS for you.


> 
Currently I installed Xubuntu, with Xfce, and it works better.


Again, MAC is the OS for you, not something that requires an inquiring mind, logic, and openness to learning new things, and sometimes using a command line.


> 
I am planning to buy a laptop, and I need one that works with Ubuntu (wifi, suspend). Any tips?


Yes... here are my tips:

  a) Get a MAC.
  b) Get therapy for that nasty personality disorder.

The last thing you need is Ubuntu or any linux system.

Good luck.

---

### Post by ukripper on 2008-09-22
> **pwaugh said:**
> Alex,

As a psychologist, I wanted to point out a couple of things:



The subject that you used for your post clearly indicates that you are far from being a "scientist".  In fact, your entire post has no scientific "data", only what we who are actually scientists (Ph.D.s) call anecdotal experience.  You can not draw such sweeping conclusions from such experience.  So, please don't make us real scientists look bad by calling yourself one.  =)




FYI, Unix is not Linux, and one doesn't "program Unix".  Unix is not a computer language. By this time in your post, most have likely already become as annoyed with you (as a psychologist I'm using my intuition to share with you how others might perceive you in order to help you get more of a perspective on how you come across).




Again, you state a clearly un-scientific opinion which is completely unsupported by facts.  No one here is interested in your opinion on the state of linux distributions, only on your experience with Ubuntu.




Perhaps for you.  I think you would get a better response from the community if you worded this something like:

"The Ubuntu Hardy release has not gone well for me.  It has been the worst experience I have had with a relese yet."

Then, you would be "owning" your feelings, instead of trying to speak for the rest of us.




Finally, you get to the "meat" and tell us (at least in overview) what you have experienced.  Sorry you have had so many problems, but you need to use a "divide and conquor" approach (which you would know if you were a scientist).




A far more effective approach would be to NOT assume that your problem is a bug, but rather put your massive ego aside and post of the support forums exactly what you are experiencing on what equipment with what software, and see if anyone has ideas for things you might try.  However, your ego prevents you from seeking help, so instead you just complain as then you can blame others instead of accept that you may not live up to your own reified image of yourself.

I'm really being blunt here, because someone in your life needs to be, and you aren't paying me to take 2 years to tell you nicely in hourly sessions.  =)




Here your intuition is trying to tell you something, but you fail to see it.  It does work on our machines, and this might be a clue that your ego can't handle.  I bet it could work on your machine too, if you could stop thinking you are such an expert, and start openning yourself up to seeking help.




I doubt your reason for posting was so altruistic.  More likely, you posted out of the anger and frustration of your inner child (which is not so inner unfortunately), and wanted to lash out since you could not call "tech support", whine and demand a refund.

Freud often points out that when people say, "I'm joking" they really are not, and this is the case here.  You are correct that "humans" do vent, and it is sad that you see this as a weakness and something that you yourself could never do.




Yes, you hate being wrong, which is why you should go back to Windows, and will never be a scientist.  Science is about being willing to be wrong, as being wrong is what leads to the knowledge of what is right.  Edison first found 1,000 things that did not work as a filament for the light bulb.  Were it up to you, we'd all still be in the dark.




This just again highlights how narcissistic you are, and is very insulting to others.  Thank God we have had the opportunity to be educated by you.  What would we have done without you!  I had no idea that businesses cared about their customers!  Wow!  BTW, unlike you, when Microsoft makes a "minor mistake" we don't cry (that's something babies do), we LAUGH, because we are using Linux.  Moreover, most people don't cry over mistakes, they learn from them and accept them as a part of life and "growing up"!  Dare I suggest you grow up?



Good thing you don't want help, because:

  a) Your massive ego will not let you accept that you need help.
  b) You could never accept help from others
  c) No one would want to help someone who acts the way you do toward
     others!
  d) There is no need to get help, because you have "wished" they
     would get fixed, so someone will get right on that.




Yes, clearly your perceptions are correct.  In fact, why are you here?  You have clearly seen the future is Mac, so go Mac?  Have you left yet?  How about now?  Damn.




Even your own unconscious is desperately trying to tell you that your words are deserving of "ridicule".  This is because this is a recurring theme in your life.  Please get some help, so your life can be better.




You have the time to post this garbage, but not to actually do anything about your problem?  You definately should go MAC.  This is NOT the OS for you.




Again, MAC is the OS for you, not something that requires an inquiring mind, logic, and openness to learning new things, and sometimes using a command line.




Yes... here are my tips:

  a) Get a MAC.
  b) Get therapy for that nasty personality disorder.

The last thing you need is Ubuntu or any linux system.

Good luck.

The best post of the year !!!:)

---

### Post by Ms_Angel_D on 2008-09-22
> **ukripper said:**
> the best post of the year !!!:)

+1

---

### Post by alex_ndc on 2008-09-26
Wow, and you guys spend all this time showing frustrated users how wrong they are?

That's useful for, like, everybody :lolflag:

---

### Post by lukjad on 2008-09-26
> **alex_ndc said:**
> Wow, and you guys spend all this time showing frustrated users how wrong they are?

That's useful for, like, everybody :lolflag:
Wow! You go around and respond to annoyed people? Even better. ;)

---

### Post by alex_ndc on 2008-09-26
> **lukjad007 said:**
> Wow! You go around and respond to annoyed people? Even better. ;)

Yes, but this is fun ;)

---

### Post by ukripper on 2008-09-26
> **alex_ndc said:**
> Yes, but this is fun ;)

I didn't know that serious computer scientists actually have got time for having this kind of fun.

---

### Post by *B* on 2008-09-26
And these type of negative attacks/responses are exactly why Linux will never be a major player in the O.S. market, in any flavor. 

No one wants away from M$ any more than I do. But why would I want to take on the huge task of switching, when they are enough big obstacles to overcome already? Then, if I have a problem and come here to post about it, I have to worry about getting bashed, being called a liar, a troll.... everything in the book. I have read countless posts on this forum. Why is it when someone posts something negative, they get bashed for it? 

If you personally are not having the same trouble that the OP had, then posting "it works for me" is useless, and you arent helping the problem, you're adding to it. Unless you have the EXACT hardware setup as the OP, saying it works for you is useless unless you are going to post that in every thread on this forum. Its silly. 

If you want people to respect the O.S. you support and it's users in their forums, then how about you show that in return? Don't be surprised when you aren't taken seriously and your distro doesnt gain support from the masses when these childish tactics are displayed. Im sorry, but I come here to learn and try to fix problems I am having with Ubuntu, and I get sick of seeing all the bashing and negative comments.

---

### Post by ukripper on 2008-09-26
> ***B* said:**
> Im sorry, but I come here to learn and try to fix problems I am having with Ubuntu, and I get sick of seeing all the bashing and negative comments.

Exactly, can someone tell this to the computer scientist (OP) as well!

---

### Post by *B* on 2008-09-26
Im sorry, but I dont feel he was bashing. And from what Ive read, only the die hard Linux fans did. I read his OP, and thought he had a right to post his opinion on his experience. I think if you're going to ask people to try your OS they have a right to voice their opinion........... good or bad........ after all the effort they put forth to try it. His opinion/experience was bad. Fine. Lets move on. For users of this forum to carry on for 6 pages with negative comments...... puts them on the same level they claim he is on. He had a right to speak his mind and he did. If it had been left at that, it would have been different. Personally, I will now follow my own advice, and not post anymore in this thread, as it has nothing whatsoever to do with the OP, nor do 99% of the posts in this thread. Besides, I have some networking issues to read about and try to resolve. Good day.

---

### Post by lukjad on 2008-09-26
*B*, please realize that the OP was not asking for help. He asking for attention. When someone complains, there are many other people that will complain also. Since the people who do not like Linux/Ubuntu do not frequent this forum much. While this does not absolve the people who responded in a spiteful way, you must understand that many people here are reading posts similar in spirit to this one. After a while, people just stop being sympathetic.

When someone says things like "**Ubuntu Hardy is the worst release yet.**" this ruffles feathers. It is not productive as it gives no specifics and it does not tell us what he did to try and fix the problem. With the "I am a passionate computer scientist" comment, it makes people somewhat annoyed at him since he seems to be showing off how smart he is. 

In short, this thread is getting the exact same type of responses as the original post was. Argumentative and unproductive.

---

### Post by carusoswi on 2008-09-26
> **lukjad007 said:**
> Most people who post and define themselves as "computer experts" are troll, even well intentioned ones. Trolling is just making comments that make people flare up. Even if that is not your true intent, that is the result.

The above might be your definition of a troll.  I don't agree.  There is a tendency on this forum for anyone who is critical of Ubuntu to simply get shouted down.  It's happening in this thread now.  People who have either had no problems or simply want to support Ubuntu gang up on anyone who posts critically of it.

This is an experience/testimonial section of the forum.  That's the only justification a poster needs to post here, either for or against the OS.

This is the section of the forum where you come to sound off - no bug reporting, no launchpad checking required.

That's how testimonials/experience threads work.  They communicate ones feeling about the OS.

If no negative posts are allowed, or if they are all shouted down, then, why have this section?

Perhaps the mods should separate this section into two, one for positive posts, one for negative posts.

Then, if you only want to read positive remarks, you won't have to sift through those that are negative.

Caruso

---

### Post by Samizdat on 2008-09-26
> ***B* said:**
> Im sorry, but I dont feel he was bashing. And from what Ive read, only the die hard Linux fans did.

Exactly.  Evidently the code of conduct doesn't apply if it's a mob doing the bashing.

---

### Post by pwaugh on 2008-09-28
> ***B* said:**
> And these type of negative attacks/responses are exactly why Linux will never be a major player in the O.S. market, in any flavor. 


While your comment lacks any sort of logic, and fact, I'm guessing what you are trying to say is that you are bothered by some of the human give & take that occurs.  I can understand that, but it also takes wisdom to know that sometimes the healthiest response involves irreverent confrontation.  People sometimes get from others what they give.  It might surprise you to know that the responses give here have nothing to do with this being a Linux forum, and would have just as easily happened (and have happened) on a Windows forum.

Others, such as this OP get themselves in trouble, and have some social skills to learn, that's all.  Has nothing to do with you, although like the rest of us you may have your own learning to do.


> 
No one wants away from M$ any more than I do. But why would I want to take on the huge task of switching, when they are enough big obstacles to overcome already? Then, if I have a problem and come here to post about it, I have to worry about getting bashed, being called a liar, a troll.... everything in the book. I have read countless posts on this forum. Why is it when someone posts something negative, they get bashed for it? 


Not sure why you want to take money away from MS, or why you assume that this is the point/goal of Linux, but let me start out by saying that this is not the point.  MS has earned their money, and frankly the world of PC's wouldn't even exist (at least in the way it does today) without them.  No one bad mouthed them here, so you are way off topic here with this comment, and it just illustrates your own bias you are bringing to the discussion and projecting on others.

Switching to Linux from Windows is not something that is intrinsically "right", just an option available to you as you learn more, and need more power and flexibility.  My mom uses Windows, and it (or a MAC) is the right OS for her.  She will never have the need, or intellectual curiousity to move to Linux.  Nothing wrong with that at all.  Use what works for you.  We are not going to be sad or hold it against you if you find that Ubuntu is not right for you.

On the other hand, if you are willing to learn, and know how to properly ask questions, or are open to learning, then others will graciously help you anytime!


[/QUOTE]
If you personally are not having the same trouble that the OP had, then posting "it works for me" is useless, and you arent helping the problem, you're adding to it. Unless you have the EXACT hardware setup as the OP, saying it works for you is useless unless you are going to post that in every thread on this forum. Its silly. 
[/QUOTE]

Well, you have just missed the point.  Remember, the OP did NOT ask a single question in his post, or provide anyone any information other than his own reified self-perception of himself as an "expert".  In other words, he came here to share his negative experience, but did so in an extremely offensive way, and so others here were simply calling him on it.

Moreover, you should read the book, "Boundaries", and then not try to insert yourself in between two other adult's conversation.  He can defend himself, and learn from it.  If you had a bad experience asking a question, I'm sorry, and hope that you got the info you needed.


> 
If you want people to respect the O.S. you support and it's users in their forums, then how about you show that in return? 


You again failed to see that it was the OP who was offensive, and unproductive.  Moreover, the goal of our communication was to engender "respect", but to confront someone on their poor social skills.  People can like/dislike Linux, or Ubuntu as they please... no skin off our backs.  And FYI, it's not "our" distribution.


> 
Don't be surprised when you aren't taken seriously and your distro doesnt gain support from the masses when these childish tactics are displayed. Im sorry, but I come here to learn and try to fix problems I am having with Ubuntu, and I get sick of seeing all the bashing and negative comments.


This is a bit like you going to Iraq and saying you are sick of seeing all the violence.  No one likes it, but sometimes it is necessary.  Perhaps you should stick to your posts requesting help then?

Anyway, I'd worry about how people help you, not how they deal with trolls like the OP.  That's where that book can help.

---

### Post by Idefix82 on 2008-09-28
Thank you for this post, pwaugh!

---

### Post by alex_ndc on 2008-09-28
> **pwaugh said:**
> Remember, the OP did NOT ask a single question in his post, or provide anyone any information other than his own reified self-perception of himself as an "expert".

That's funny :)

Where have I said that I'm an expert in anything? Is that quote mine?

Let me remind you that a *testimonial* is *of, relating to, or constituting testimony*, where testimony in my case is an open acknowledgment by a witness (me) that the latest version of Ubuntu has too many issues, and it gets worse on every release, serving as a warning to users that want a stable and solid release (implied by Hardy being a LTS).

Where's the "asking the question" part?

I thought we were talking English here.

---

### Post by ukripper on 2008-09-30
> **pwaugh said:**
> 

pwaugh - very well described yet again!

---

### Post by ukripper on 2008-09-30
> **alex_ndc said:**
> That's funny :)

Where have I said that I'm an expert in anything? Is that quote mine?

Let me remind you that a *testimonial* is *of, relating to, or constituting testimony*, where testimony in my case is an open acknowledgment by a witness (me) that the latest version of Ubuntu has too many issues, and it gets worse on every release, serving as a warning to users that want a stable and solid release (implied by Hardy being a LTS).

Where's the "asking the question" part?

I thought we were talking English here.


you have answered your own question as below in your original post.

> **alex_ndc said:**
> 

I don't want help, I just wished those problems would get solved.


To solve problem you need to ask for help, ain't gonna get solved by itself mate!

Naively, I wish I could win the lottery!

---

### Post by applecookie on 2008-09-30
I must agree to the thread opener: Hardy IS still a bug festival and for a LTS version, it's a catastrophe. Intrepid is much better - an this is an alpha version!!!

And I also must agree to him, that it's no good style to attack someone, who is not the opinion, that "all is wonderful" and "praise to hardy...". I've made the same experiences: Some of the posters of this forum do not accept the opinion of others.

I must say, that the niveau of the posts of other linux forums in THIS CASE is much better! 

Live and let live!

And now you can start the flaming war also on me... ;-)

---

### Post by stalkingwolf on 2008-09-30
alex_ ndc said>  “ Jesus”  ,  as perfect as this OS works for many people, I don't recall him posting on this forum.

> “if I have a problem and come here to post about it,”

If you had a problem you would be better server to seek help in the forum/area that served your particular problem.
  
> “Unless you have the EXACT hardware setup as the OP, saying it works for you is useless “

As is saying that the OS is useless and a huge regression.

> Let m“e remind you that a testimonial is of, relating to, or constituting testimony, where testimony in my case is an open acknowledgment by a witness (me) that the latest version of Ubuntu has too many issues, and it gets worse on every release, serving as a warning to users that want a stable and solid release (implied by Hardy being a LTS).”

this lacks the qualifier : for you and your specific hardware configuration.


Now let me say I have at times ranted about this or that problem with this OS.  I have never been bashed at any time.  But then that could be because I provided the necessary information to attempt to solve the issue.

In only a couple cases have I not gotten answers to issues. In those instances further investigation has shown me that at this time there simply is no answer available, or a limited use answer.  The VIA /S3 Unichrome PRO IGA as an example.  I have gotten this adapter to work in some instances, others not.

I know the OP will not like this "works for Me" but others may find it helpful.   With UbuntuEEE 8.04.1 it works. Installing the same distro
with wubi inside a full install of XP it works. Inside an upgrade install of XP* it does not.

* to use some of my old software I have to install ME then upgrade to XP.
Happily one of the apps is no longer needed. I am confident that i have found and figured out the software to print my business cards.  The only other I am sure will no longer be required as soon as I learn to use the
corresponding application in Ubuntu.  If this one doesnt work I have no doubt there is one that will.

So to quote a famous (or realatvely so) person from history,> as for me and mine, we will continue to believe the tenets of Mother Church

---

### Post by Flynn555 on 2008-09-30
i have yet to have any issues. :/

---

### Post by its_jon on 2008-09-30
> You see, there's a difference between a big software company like Microsoft, or Adobe, or Google and this community ... they care about their customers enough to not reply with "works on my machine". And when they do a minor mistake, thousands of people cry in anger.

Erm..... I believe Google have wrote quite a lot of code within the Linux Kernel as they are passionate about Linux and the people who use it. 
In reality the biggest 'company of people/programmers/developers' is Linux.

I see your post as a HUGE thumbs up for Hardy.... no other reason you would have gone to such lengths to dis the distro. Your opening line gives you away when cross referenced with your content... ie "computer scientist" :D

---

### Post by Samizdat on 2008-09-30
> **its_jon said:**
> Erm..... I believe Google have wrote

You believe Google "have wrote," huh?  Is that Hardy English?

---

### Post by Samizdat on 2008-09-30
> **applecookie said:**
> 
And now you can start the flaming war also on me... ;-)

Don't worry, this mindless mob has nothing better to do.

---

### Post by Samizdat on 2008-09-30
A heads-up mod would have called this thread deep enough at two or three whine-about-the-OP posts.  The thread has outlived its usefulness by 6+ pages.

---

