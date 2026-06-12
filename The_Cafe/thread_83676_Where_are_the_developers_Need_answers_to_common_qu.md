---
title: "Where are the developers?? Need answers to common questions"
date: 2005-10-29
forum: The Cafe
---

### Post by ghaspias on 2005-10-29
I have been using Ubuntu for almost a year, and altough these foruns have helped me with some issues, I have some issues that nobody answered yet - apart from users that report the same problems.
What I'd like to see is some 'official' answers to common questions, so that either:
- those issues can't be solved, and users stop trying, and just wait for a new release to solve them;
-those issues can be solved by some tweaking, and perhaps someone would come up with an easy to use script/applet for that.

Let me be more specific:
I have a pending issue with my webcam - a philips toucam model 720k. It's the 'decompressor not found' issue. It seems lots of people have similar webcams, and nobody knows how to make them work. Tere are a lot of threads about this, but no 'official' answer - can it be done without recompiling the kernel/drivers/etc, i.e., is there any workaround for non-geek people? (Even my router supports this webcam, why shouldn't Ubuntu? Is it the proprietary decompressor? Can't it be installed from a package in Universe?)

Another old issue is ATI M7 (Radeon Mobility 7500) performance. 2D performance from this card is awful with any settings I've tried in xorg.conf. I am no expert, as most Ubuntu users, so I blindly test whatever tips I can find. Tere are many threads on this problem in the foruns, but only complains, no explanations or 'oficcial' answers. Is it normal that dragging a window leaves a trail for more than 1 second?? My graphics card draws 700 fps in glxgears, cna't it refresh my windows at, say, 30 fps?

I am sure these problems afect a small percent of the users, but that amounts to lots of users anyway! Also, surely many other problems afect other users - some of them find pretty good answers here, but others don't.

So, there should be some place where users can find more than other users complaints... someone should take the answers to common problems and organize them, and if there is no answer, the 'people who know' should take a lokk at it - I am sure the smart and friendly people who put Ubuntu together can answer most of the questions with a 'can't be done without large effort' or 'if you want that, you must tweak this'.

Please report your experiences with this forum - do you have many pending questions? Have your questions got an authoritative anser - by someone who knows about the subject, not some user who knows little more than yourself?

---

### Post by Xian on 2005-10-29
[QUOTE=ghaspias]So, there should be some place where users can find more than other users complaints...[/QUOTE]
There are two places you should go:

1. File a [ Bug Report](http://bugzilla.ubuntu.com/) on any issues (including hardware compatibility) that are outstanding with the Ubuntu version you are running. First check to see if the problem you are having has not already been reported and a fix suggested.

2. Subscribe to the [Ubuntu Developer Discussion](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel) mailing list.

---

### Post by ghaspias on 2005-10-29
I've walked that road before... submiting bug reports, hours spent in bugzilla, contacting developers, trying to get some understanding of the cvs, staring at the code... but I am no developer.
I have installed and used dozens of linuxes, from redhat in PoewrMacs, Debian in 68k Mac, all flavors in intel boxes, routers, etc... but now I feel I should just use it. So, I decided that I wouldn't recompile anything, wouldn't spend hours on the web looking for obscure tarballs, and for that I choose Ubuntu.
I already had to let go one of my original self-imposed rules, and added universe repos to synaptic. Now, I have to options: either I admit Linux isn't capable of providing the same 'works out of the box' experience as Windows (for existing 'designed for windows' hardware, with their windows-only binary drivers et al.), or I try  to find the (I hope) simple answers that linux usually has to anything - you just have to ask the right person the right question...

The bottom line is: I know I could do this and that and recompile and install and patch... and then I would eventually have everything working. But I don't want to - if I have to go that way, then I will just choose Gentoo - it's more appealing to the geek inside me!

---

### Post by Xian on 2005-10-29
I'm not sure where you are going with this. You initially wanted a suggestion on how to communicate with the devs (as per the thread title) on system issues, and to my knowledge the answer given was appropriate and workable. Now you seem to be off on another track, and I'm not clear what it is you are experiencing that can be resolved in this discussion format. We of course all desire some degree of ease of use and functionality, combined with system management preference, but it is also true that not everyone finds this in the same place.

---

### Post by Doc.Caliban on 2005-10-30
[QUOTE=Xian]I'm not sure where you are going with this. [/QUOTE]


I believe that I do.  

I have used Windows nearly every day of my life for 16 years, 10 of which were spent working ON it at Microsoft.  I've never tried Linux, as much of a geek as I am, because I've never hated Windows quite enough to bother starting over with something else.  (And I hate it a lot sometimes.)  I also wasn't really interested in a "hobby" OS, as I'd always thought of Linux, not because I don't like that aspect of it, but because my computer use has evolved to the point where I, like ghaspias, just want to use my computer.  I don't want constant tinkering to be mandatory.

The other day I booted Linux for the first time via a live CD so that I could use some networking tools on the disc and found that I was enjoying being completely out of my element for the first time in 15 years.  After speaking with a good friend who has used Linux at work for years, I decided that Linux was sounding mature enough that I might just be able to get away from Windows without having to pay for doing so with constant fudging about with the new OS.

For various reasons I ended up with Ubuntu as my first distro ever, and I had a pretty good time with it in the first 24 hours or so.  

But then I started to notice that there were several things that weren't working very smoothly, if at all.  Programs that I depend on that ship in Linux versions and are listed in the app install list of Ubuntu that have problems ranging from not starting at all after installing them, to starting but not functioning.  There have been driver issues and problems encountered when doing things that are supposedly doable by design.  In other words, things are still too much like Windows so far.  :-)

While that's a bit disappointing, it's not the real problem.

The problem seems to be that when asking a question here, it's hard to get in-depth and straightforward answers.  I've spent more time in Google trying to find answers that I thought I'd find here than I've spent simply using the OS so far.  

This is not meant as criticism, it's just an observation.

-Doc

---

### Post by aysiu on 2005-10-30
I still don't know where you're going with this. The people on these forums are just other users like yourself. Even "staff" are all volunteers and other users. Sure, some users know a lot and are even programmers themselves, but we're all just Ubuntu users. We don't know everything, and we have no more control over how the developers do things than you do. And the Ubuntu developers do not read these forums.

Maybe you should take a look at this thread: [Got ideas for Dapper? Let the developers know! Posting here is not enough!](http://www.ubuntuforums.org/showthread.php?t=75000) 

Dapper is the next release after Breezy.

I probably have nowhere near the amount of experience with computers you have, but I haven't experienced any serious problems. My screen resolution was a little off, and I asked a few questions and got it fixed.

What's your point?

Well, in the meantime, while you're trying to figure out what you're trying to say, you may want to read up on a few things:

[http://www.ubuntuforums.org/showthread.php?t=63315](http://www.ubuntuforums.org/showthread.php?t=63315)
[http://www.ubuntuforums.org/showthread.php?t=58017](http://www.ubuntuforums.org/showthread.php?t=58017)
[http://www.ubuntuforums.org/showthread.php?t=78741](http://www.ubuntuforums.org/showthread.php?t=78741)
[http://www.ubuntuforums.org/showthread.php?t=65103](http://www.ubuntuforums.org/showthread.php?t=65103)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Xian on 2005-10-30
[QUOTE=Doc.Caliban]The problem seems to be that when asking a question here, it's hard to get in-depth and straightforward answers.  I've spent more time in Google trying to find answers that I thought I'd find here than I've spent simply using the OS so far. [/QUOTE]
That's fair enough. I've posted several tail-chasing threads as well on some forums. That is the nature of things sometimes. The result of a forum which is staffed with mostly enthusiasts is that answers are often hit and miss. This is why I often advise using multiple lines of communication when researching an issue, and these would certainly include IRC and mailing lists along with other avenues which are less traditional.

I can recall a X freezing problem I had with Debian a long while back that I posted repeatedly and quizzed devs about any chance that I got. I never particularly cared for most of the answers myself, feeling that they did not perhaps encompass the more technical aspects of my issue. However, nearly a year later I finally came upon the solution and it turned out to be something which was machine specific and could not even be reproduced. Just a crazy glitch on my system which would have gone undetected save for another item I was working on at the time.

In the end we are just people trying to help people.

EDIT:
Oh, and if you'll post links to those threads you mentioned I'll have a look.
Maybe I can help with your issue.

---

### Post by ghaspias on 2005-10-30
First things first:
I didn't mean to start a rant, and I relly appreciate all the work the Ubuntu staff are doing; I find these foruns very interesting; and I didn't want to sound rude.

All I wanted with my original post was to get the feedback from other users.

I ackowledge that, as Xian pointed out, this is an users forum - developers don't come here often. And it is alright. But then, where should users find 'definitive' answers, not just simple tips from other users? Well, perhaps the answer to my original question already exists, but I am not still very familiar with it - it's launchpad.
The fact is, it seems to me that most users will start by looking up ansewrs in this foruns, but there are lots of questions that keep popping and never answered in a clear way.
I will take a second look at launchpad (a name I saw plenty of times but really only understood after upgrading to breezy) and the bug database... but it still doesn't seem fit to serve as a knowledge base for regular ubuntites.
OK, now I noticed the use of this two words: knowledge base. This is what we need, and a forum isn't exactly that - altough it could serve as a starting point.
How do you think a knowledge base for ubuntu could be set up?
I don't know, and certainly won't think very much about it, but I would like to ear other people's thoughts...

[EDIT]
I spent 10 minutes fudging around in [http://launchpad.org](http://launchpad.org)
For those who don't know what it is: launchpad is accessible from the help system of ubuntu (the dreadful yelp) or from the help menu of some applications. It takes you to  a page where you could submit a bug report, view existing bugs, or find help about an application)

I didn't find any useful info regarding my two issues; well, I didn't find _any_ info at all. I just don't understnd how that is supposed to work.
The only thing I could do was find a (few) bug reports, none related to what I was looking for. If people don't report bugs (I didn't) perhaps it's just because it should be easier. Users are required to register before submitting bug reports or requesting support. The page isn't linked form the main ubuntu site.

[EDIT]
@aisyu:
I read the threads you mentioned. I agree to most of your points (altough I don't see myself as a troll ;-) ), but I wish the best for linux and ubuntu in particular; I do believe that the ultimate goal for ubuntu is to be easier for a newbie to use than windows or mac. When things break in a mac, it's said to be by design, and you just don't think bout it; in windows, you have a knowledge base where you can find how to do all the crazy stuff with the registry, or navigate trough dozens of tabs and dialogs to configure something. But users aren't left talking to each others wondering and experimenting.
I have been marveled by the amount of documentation in linux since the first time I installed a linux distro on an old powermac: how-to's, mini-how-to's, man pages info pages, all that installed in my machine! Today, I still think that is wonderful, but many newcomers just don't want that - they want easy to find answers, either 'that is something you shouldn't do / can't be done' or 'yes, it can be done, follow these steps'.
I have made several suggestions after the hoary release regarding the upcoming (breezy) release. But my actual complaints have not been solved. That's ok, but I expect ubuntu to become even better than it is now.

---

### Post by poofyhairguy on 2005-10-30
[QUOTE=ghaspias]
I ackowledge that, as Xian pointed out, this is an users forum - developers don't come here often. And it is alright. But then, where should users find 'definitive' answers, not just simple tips from other users?[/QUOTE]

Well, most of the stuff in the wiki is looked over by the doc team so many solid answers are there. There are some things there are just not definative answers for. If you need one, fil a bug a developer will see it and you will get the answer you seek.

> 
OK, now I noticed the use of this two words: knowledge base. This is what we need, and a forum isn't exactly that - altough it could serve as a starting point.
How do you think a knowledge base for ubuntu could be set up?


Thats the purpose of the wiki.

---

### Post by aysiu on 2005-10-30
[QUOTE=ghaspias]in windows, you have a knowledge base where you can find how to do all the crazy stuff with the registry, or navigate trough dozens of tabs and dialogs to configure something. But users aren't left talking to each others wondering and experimenting.[/QUOTE] I've seen the Windows knowledge base, and it sucks. Their instructions do not compare to the HowTos in this forum. The wealth of knowledge here is amazing. I can't find the answers to my Windows problems, even with Google, even with Microsoft.com. I usually find my answers right here on the Ubuntu forums, either by asking or by searching.

I don't understand your beef. Make documentation, use what's there, or leave. Those seem the only options.

---

### Post by Big Venus on 2005-10-30
I've submitted bug reports before too, especially to microsoft about windows and redhat about fedora. Of the 20 or so only 5 did I get responses from. I had to take and experiment on windows and fedora to get them to run right and when I came across the same problems in ubuntu, I knew what to do. I am not trying to say that you won't get your question or problem fixed by asking the developers. But as a user of linux, you sometimes need to learn things on your own. 

For instance, when Fedora came out I was one of the ones that download the first copies of it the night before the official launch. I had problems with the OS after the install and had to practically rewrite the code for Xorg and a few programs. Still to this moment, I am waiting for a reply to those questions.

Sorry, but I just wanted to make a point.

---

### Post by raublekick on 2005-10-30
[QUOTE=poofyhairguy]Well, most of the stuff in the wiki is looked over by the doc team[/QUOTE]

And most of the stuff in the wiki is over looked by the user. Just a thought for anyone reading.

---

### Post by ghaspias on 2005-11-01
After my last post I did try the suggestion to search the wiki - and I found some answers. (It was not clear to me that a wiki was the place to look for that kind of info)
Anyway, it seems my sugestion is not totally invalid :p : [https://launchpad.net/products/launchpad/+spec/launchpad-knowledgebase](https://launchpad.net/products/launchpad/+spec/launchpad-knowledgebase)

---

### Post by Jussi Kukkonen on 2005-11-01
[QUOTE=ghaspias]
What I'd like to see is some 'official' answers to common questions
...
I am sure the smart and friendly people who put Ubuntu together can answer most of the questions with a 'can't be done without large effort' or 'if you want that, you must tweak this'.
[/QUOTE]

There are 90 000 threads on these forums with 470 000 posts. Each and every one of those questions is very important to the submitter... Answering to most of them with any authority is pretty much the definition of *Sisyphean task*.

---

### Post by brentoboy on 2006-05-15
if you want in depth descriptions of how things work, goto a gentoo forum, and just read it with a grain of salt. Things like emerge obviously dont work--but the way apps work on the inside isnt really different between the two distros.

the difference between the gentoo wiki/forums and the ubuntu wiki/forums is that gentoo is all about answers, and they shoot people who ask questions that have already been answered.  the ubuntu group welcomes the "stupid" questions, becuase they arent stupid to the person answering them.

in these forums, you get peer help and suggestions.  at the gentoo forums, you get deep geek insight.  there are guys on this forum that also frequent that one, so you get some insite from them as well, but only if they have tinkered with what you are asking about.

---

### Post by ssam on 2006-05-15
if no body here can help, then you could consider paid support [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

---

### Post by Mustard on 2006-05-15
[QUOTE=ssam]if no body here can help, then you could consider paid support [http://www.ubuntu.com/support](http://www.ubuntu.com/support)[/QUOTE]

I think this is a good point to bring up.  Fixing obscure problems in an operating system is a time consuming task.  Free user based support has its limitations and the reality is that expert advice costs money.  Most people don't like paying for support, so they attempt to become 'experts' themselves and be self sufficient with regards to fixing their own problems.  Either way someone has to spend a considerable amount of time on this activity and either way someone is being compensated.  If you get someone else to do it, you compensate them with a payment.  If you do it yourself, you compensate yourself, through not having to pay. If your time is worth more than the cost of paid support, then paid support becomes a favourable option.

An open source operating system at least gives the user the freedom to fix all their problems if they are willing to spend the time to gain the expertise.  A closed source system limits your freedoms in this regard and makes paid support the only option in some cases.

---

