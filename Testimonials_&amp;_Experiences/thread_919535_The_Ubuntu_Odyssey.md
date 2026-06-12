---
title: "The Ubuntu Odyssey"
date: 2008-09-14
forum: Testimonials &amp; Experiences
---

### Post by aaror on 2008-09-14
I am changing the first post because I am tired of the trolls on this thread.  If you want to improve Linux and see it become something better than the sad little pastime of geeks in basements, read the bottom part of the post.  If you are a Linux fanboy who doesn't think anything should be done to improve the program or gain market share, read the top part of the post.

OK, I am going to explain the purpose of this thread. If you are not interested in this purpose, please do not post in this thread. I will be editing the first post to mirror what I say here.

Windows has a huge market share, Linux is a fringe market, if you don't like it, change it, don't whine like a baby. I like Linux, but can't do all the things I want on it. There are a lot of great programs that don't run on Linux because "there is no market for it."

As long as fanboys say "Who cares if the average user can use Linux, I'm happy being 'leet,'" Linux will remain a minor blip on the market, and thus inconsequential. If you want a real OS, make one, make Bill Gates shiver in his boots. To do that, guess what, you need market research.

I am going to post my experiences with Linux, what I wanted to do, what frustrated me, what I found cool. I will try to post what I figured out, and what I could not figure out.

The posts I would like to see:
1. I'm a newbie too, and I had a problem with X.
2. I'm a newbie too, had a problem with X, and fixed it with Y.
3. I'm an expert, and saw that someone posted a problem with X, have you tried Y?

All other posts are just fanboy spam!



(Original Post)
Fair warning, some of the stuff in here will seem like a mild flame, or seem as though I dislike Ubuntu.  That is not the case, I already prefer it to Winblows, but I'd like to see more folks using Linux, and this thread is an attempt to help that process.
Most of the people using Linux in any form are skilled computer users, who can figure out problems.  The vast majority of Windows users are not.  If we are going to get real traction, we need to figure out "user friendly."  As a complete newbie to Linux and Ubunto (and wine, and mplayer...) I am going to write all the problems I have here, and the fixes I discover.  This blog will not be for new users to copy my example (though they can if they want) but for the folks who do the real work on this project to come see what isn't understood by the new user.
That said, I welcome other newbies to post their problems understanding the help and code too, so that we too can contribute to Linux.
Thank you for joining me on my odyssey.

---

### Post by aaror on 2008-09-14
Wish I had thought of this three days ago when I first got the beast working...  Oh well, we will just start with today.
Going to start by posting my stats, I will come back and edit this with more info if someone tells me what is useful.  I have a Dell Inspiron 530 with Ubuntu 8.04 pre-loaded, and re-loaded (interesting story), so I can dual boot using either Ubuntu or Ubuntu (remind me to fix that).  I use an ATI driver (pre-loaded) for my 256 MB Radeon HD 2600 XT.  For processor I am using a quad-core Intel Core2 processor Q9300 (2.50Ghz,1333FSB) and 6 MB cache.  I have installed Wine 1.1.4, and have installed Neverwinter Nights 2 and yahoo instant messenger 8 (I think, the beta one), neither of which is working yet.
Next post will be the first real post, but I want to keep this somewhat organized (remind me to do a table of contents if this gets long).
If anyone wants to converse with me about this thread, including folks telling me it is dumb, I am at aaror2005 at yahoo dot com (hopefully only humans and not e-mail bots can read that).

---

### Post by howefield on 2008-09-14
> **aaror said:**
> ..... Most of the people using Linux in any form are skilled computer users, who can figure out problems.  The vast majority of Windows users are not.

Can't agree with that, too black and white. I think you over estimate linux users and under estimate windows users ;)

Anyhow, good luck in your endeavour.

---

### Post by aaror on 2008-09-14
September 14th, Day 4 of the Odyssey.
Today I rented two movies figuring I would watch them on my computer.  The movies were "Get Smart's Bruce and Lloyd out of control," and "Babylon 5, the lost tales."  (Yes I am a nerd, but what did you expect, I am blogging about learning an OS, anyway...)  Both fils are region 1, Warner Bros, and have a copy protection warning on the case.  Spent two hours of trying to get one of the movies to play at all, including downloading VLC media player and mplayer, still no luck.  At some point I did something to my browser so that I can no longer make it less than full screen (even hiding my tabs !@#$%).  I finally opened the movie in the totem movie player that comes with, and clicked the "report bug," using the name of the error message to describe the bug.  It sent me to this page:
 [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/219062](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/219062)
WORKAROUND:
- install packages libdvdcss2, libdvdread3 and libdvdnav4
- run 'sudo /usr/share/doc/libdvdread3/install-css.sh'
unfortunatly libdvdcss2 said something about file not found, and after running all of this I still could not watch the movies.
went to this site:
[http://packages.ubuntu.com/hardy/i386/mplayer/download](http://packages.ubuntu.com/hardy/i386/mplayer/download)
to get mplayer (after several attempts to find an easy way to do it).  Almost had to download the patch like a windows user, since like all newbies, I did not know how to apt-get.  If the owner of that page will put full instructions (open terminal, type XXX, do XXX, etc.) I think it would reduce headaches for many.
I got out my Windoze XP laptop and watched the movies there.
Still not willing to give up, I found this page:
[http://davestechsupport.com/blog/2008/03/02/six-things-to-do-after-you-install-ubuntu/](http://davestechsupport.com/blog/2008/03/02/six-things-to-do-after-you-install-ubuntu/)
I am not sure all of these are crucial, and I had already figured one out on my own, but it is a wonderful page for a newbie anyway.  Looking for the source of my problem, that page sent me here:
[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)
Step 2 I had to guess that hardy replaces edgy, not that it mattered, step 3 gave me "gpg: no valid OpenPGP data found."
So I went to this page (thanks for the last page at least pointing me there):
[http://www.medibuntu.org/](http://www.medibuntu.org/)
Wow, that was a lot easier, and for any newbies, check out this link:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Wish I'd had that page the very first time I loaded Ubuntu.
Anyway...
Yey! the instructions and help from medibuntu allowed me to watch the movies.  Of course, since I already watched them on my Windoze machine I didn't actually watch them now, but at least I know I can.
Btw, I found a lot of folks who said mplayer was the best movie player, but most of my 2 hours trying to fix my computer were spent trying to find out how to install mplayer.  If I had done the medibuntu fix first I would never have bothered, so if you think folks should use mplayer, make a page that makes it easy to install for newbies.

Howefield, I agree that many Windows users (including maybe me) are skilled computer users who can figure out problems, and some Linux users may need to call their brother/friend/etc. every time they want to install something.  All generalizations are false (grin).  But if you look at the computer skills of the 80th percentile windows user (knowing more than 80% of other windows users), I think they would be below the 50th percentile of linux users.

Disclaimer, If I ask for a change to a page or criticize the page, I am only trying to help.  I will try to stick to constructive criticism.  I only mention pages which either have useful info, or which seem to have info that would be useful if I were smart enough to use it.  AKA I'm sorry if I offend, please do not flame-bomb me or send viruses.

---

### Post by Oldsoldier2003 on 2008-09-14
Moved from General Help to Ubuntu Testimonials & Experiences. Though the OPs intentions are to provide help, the scope and methodology make the thread unsuitable for GH.

---

### Post by howefield on 2008-09-14
May I add another link I found really useful ?

[http://www.category5.tv/content/view/77/38/](http://www.category5.tv/content/view/77/38/)


It is an article written by Robbie Ferguson, titled The Perfect Hardy. I don't use all of it, but it is good for the dvd codecs ect.

---

### Post by Comhra on 2008-09-15
> **howefield said:**
> Can't agree with that, too black and white. I think you over estimate linux users and under estimate windows users ;)

Anyhow, good luck in your endeavour.

I agree with this, have a peep in Wilders if you want to experience the best Window's forum on the net and be amazed.

---

### Post by powerpleb on 2008-09-16
> **howefield said:**
> Can't agree with that, too black and white. I think you over estimate linux users and under estimate windows users ;)

Yea, what about all the third world school kids with their OLPC systems. I don't think many of them are compiling their own kernels just yet.

---

### Post by aaror on 2008-09-18
OK, not all folks using Linux are skilled computer users, me for instance, that is why I had to reinstall it after I messed up my internet connection (was trying a Wine fix to allow Yahoo messenger 9 to work, instead lost all internet for 3 days and the computer got buggy...).
That said, the average linux user could easily learn Windows, I don't think the converse is true, at least not yet.
Oldsoldier2003, totally understand the move, sorry for putting it in the wrong place.
Howefield thanks for the link.  I had a nice long post including stuff from your link, but after I put it together and saved it (bad experiences with blogs and forums in the past), my internet problem occurred, and when I did the reinstall I formatted my post.
Not really going to have anything for here for a day or so while I reinstall the basics.  Lucky I have this post to work from...

---

### Post by Idefix82 on 2008-09-18
I think that your criticism is partially unfounded. OK, so you had to install some software before being able to watch a DVD. Installing software is made extremely easy for the user if one uses the Synaptic Package manager. One could argue that there should be an application welcoming the new user and helping him to get started (eg. pointing out the package manager) but personally, when I install a new OS the first thing I do is click through the preferences and administration menu to see what sorts of tools it offers me. When I discovered the package manager within the first half hour of my Ubuntu experience, I instantly fell in love with this system. 

One could also argue that certain software should be pre-installed but you will always get people complaining that their favourite software didn't come shipped with the OS and others complaining that the same OS was overloaded with useless stuff. There is a balance to be found.

Now, about getting things to work the way you want them to work: one of the reasons some hardware doesn't work with Ubuntu is because some hardware manufacturers don't provide full specifications. You can rest assured that the Ubuntu developers also see it as a major priority that hardware should work out of the box (which is far from being the case in Windows by the way) and I don't think anybody needs to tell them that. But of course, everybody should tell them if something doesn't work if they don't know it yet.

Finally, in my Windows experience, I don't recall ever having thousands of people "around me" who are as eager to help as in the Ubuntu community. The average user who simply wants things to work somehow by default will get step by step instructions, the ones who want to learn and to have control over the system will get guidance and explanations. Personally, that's all I could ever ask for.

---

### Post by jaqie on 2008-09-18
> **aaror said:**
> I had a nice long post including stuff from your link, but after I put it together and saved it (bad experiences with blogs and forums in the past)
Just a bit of knowledge here... opera saves form data even when it crashes, even when the os crashes. it also saves open tabs under those circumstances. You may wish to give opera a try. I used to do the same thing you do, until I got used to opera's awesomeness in this regard.

---

### Post by aysiu on 2008-09-18
> **aaror said:**
> 
Most of the people using Linux in any form are skilled computer users, who can figure out problems.  The vast majority of Windows users are not. I agree with this observation completely. > If we are going to get real traction, we need to figure out "user friendly." I don't see where you're getting this from or how it's relevant.

I guess in your imaginary world, everyone tries out both Linux and Windows preinstalled and then most people decide Linux isn't user-friendly enough, so they decide to go to Windows.

That doesn't happen.

In the real world, almost everyone uses Windows. They see advertisements for Windows-preinstalled computers. They have to use Windows at work or for school. They get trained on how to use Windows. They get used to using Windows. They have friends who use Windows. Most have never even heard of Linux.

So who are the people who find an obscure operating system, download it, burn it, install it, and configure it themselves? Naturally, skilled computer users. If you have to go out of your way to find an alternative, you are not going to be an average user. This has nothing to do with user-friendliness and everything to do with inertia, ignorance, and fear of change.

---

### Post by zoomy942 on 2008-09-18
> **aysiu said:**
> I agree with this observation completely.  I don't see where you're getting this from or how it's relevant.

I guess in your imaginary world, everyone tries out both Linux and Windows preinstalled and then most people decide Linux isn't user-friendly enough, so they decide to go to Windows.

That doesn't happen.

In the real world, almost everyone uses Windows. They see advertisements for Windows-preinstalled computers. They have to use Windows at work or for school. They get trained on how to use Windows. They get used to using Windows. They have friends who use Windows. Most have never even heard of Linux.

So who are the people who find an obscure operating system, download it, burn it, install it, and configure it themselves? Naturally, skilled computer users. If you have to go out of your way to find an alternative, you are not going to be an average user. This has nothing to do with user-friendliness and everything to do with inertia, ignorance, and fear of change.

I completely agree.  However, it is up to us computer users to show the blind-windows user what a glorious machine their PC can be.  I have converted several people over to ubuntu - but 100% of the time they didnt even know they didnt have to use Windows.  they seriously thought all computers used Windows.

man.

---

### Post by aaror on 2008-09-19
K, I am going to try this again from the beginning...

---

### Post by greenleaf on 2008-09-19
[COLOR="White"].[/COLOR]

> **aaror said:**
> K,
Point taken, everything is hunky dory in Ubuntu land.  It is the easiest OS to learn in existence and there is nothing whatsoever that could ever improve it.

Because my premise in starting this thread has been massively disproven I ask that any ops please delete the thread.  I will go get a copy of Windows (XP hopefully, Vista is trash) and stop bothering you.



[FONT="Lucida Sans Unicode"][SIZE="2"]aaror,

i understand your vision with this thread....

When i read your first post here, i knew this thread will not last long....

I thought only Macs had fanboys... but this community has proved me wrong. They are just not open to change. Every time some fresher tries to share his problems with ubuntu & tries to make suggestions based on his problems, he is bashed left & right. "this is linux, that's how we are & that's how we do things... linux will not change for you... you better get used to it... don't like? get back to windows... don't whine here" is the general tone in their answer. I too started a thread to give [[COLOR="DarkOrange"]my feedback[/COLOR]]("http://ubuntuforums.org/showthread.php?t=922515") & then the bashing started... i tried my best to get my point across but to no avail & then i stopped replying altogether. If any of you here don't agree with me, then just show me one thread in this forum where a newbie has made a suggestion & you've welcomed it. "OK, i agree that's a problem for new users, we wish it was different... we'll work on it"... just show me one such reply... How can linux make progress if you do not respond to end-user's feedback.... Just delete this entire forum section...there is no point in keeping it if you only expect praise & do not welcome suggestions. If linux wants to make a difference in people's lives, a fresher's perception of linux experience is more important than an expert's.

You can learn a lot from apple.. Why are they so successful? because they understand what the end user wants... You need to connect with computer illiterates/average users... This small segment of linux users notwithstanding, I still believe the majority of linux community is open to change & will strive hard to make linux not just different than other choices but also better for users. 

I'm not undermining the progress that linux has made so far... I've installed linux on my own, without any help whatsoever, just one day after coming to know that there are alternatives to windows... And i'm no expert with computers... that's how easy it is to get started. And i believe with wubi (i've not tried it) it has even got easier...I take this opportunity to thank all those selfless open source developers who have made linux what it is today.... And i believe it can get better.

PS: jaqie & MetalHellsAngel you are few of the exceptional people i've found in this community... linux needs more open minded people like you to make a difference. Thanks![/SIZE][/FONT]

[COLOR="White"].[/COLOR]

---

### Post by aaror on 2008-09-19
OK, I am going to explain the purpose of this thread.  If you are not interested in this purpose, please do not post in this thread.  I will be editing the first post to mirror what I say here.

Windows has a huge market share, Linux is a fringe market, if you don't like it, change it, don't whine like a baby.  I like Linux, but can't do all the things I want on it.  There are a lot of great programs that don't run on Linux because "there is no market for it."

As long as fanboys say "Who cares if the average user can use Linux, I'm happy being 'leet,'"  Linux will remain a minor blip on the market, and thus inconsequential.  If you want a real OS, make one, make Bill Gates shiver in his boots.  To do that, guess what, you need market research.

I am going to post my experiences with Linux, what I wanted to do, what frustrated me, what I found cool.  I will try to post what I figured out, and what I could not figure out.

The posts I would like to see:
1.  I'm a newbie too, and I had a problem with X.
2.  I'm a newbie too, had a problem with X, and fixed it with Y.
3.  I'm an expert, and saw that someone posted a problem with X, have you tried Y?

All other posts are just fanboy spam!

---

### Post by aysiu on 2008-09-19
> **aaror said:**
> OK, I am going to explain the purpose of this thread.  If you are not interested in this purpose, please do not post in this thread.  I will be editing the first post to mirror what I say here.

Windows has a huge market share, Linux is a fringe market, if you don't like it, change it, don't whine like a baby.  I like Linux, but can't do all the things I want on it.  There are a lot of great programs that don't run on Linux because "there is no market for it."

As long as fanboys say "Who cares if the average user can use Linux, I'm happy being 'leet,'"  Linux will remain a minor blip on the market, and thus inconsequential.  If you want a real OS, make one, make Bill Gates shiver in his boots.  To do that, guess what, you need market research.

I am going to post my experiences with Linux, what I wanted to do, what frustrated me, what I found cool.  I will try to post what I figured out, and what I could not figure out.

The posts I would like to see:
1.  I'm a newbie too, and I had a problem with X.
2.  I'm a newbie too, had a problem with X, and fixed it with Y.
3.  I'm an expert, and saw that someone posted a problem with X, have you tried Y?

All other posts are just fanboy spam! So in other words, unless people agree exactly with what you say, you are going to mischaracterize their responses, resort to namecalling, and then whine about it and insist they not post in your thread?

No one has said "I'm happy being 'leet" or even close to that.

If you can't handle a discussion that has actually been quite civil, then perhaps this thread shouldn't continue.

If you don't like Linux, help to make it better.

For more details, read [What's better than whining on the forums? Making a difference.](http://ubuntuforums.org/showthread.php?t=78741)

You can also post on [the Ubuntu Brainstorm site](http://brainstorm.ubuntu.com) *practical* suggestions for improvement.

---

