---
title: "Ubuntu Rolling Development"
date: 2013-09-14
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-09-14
Well, only about  a month now until 13.10 is finalized...I was wondering if anyone has heard anything new about the symlink the developers were supposed to be working on since the conference when they decided that development IS considered the Rolling Release (even Mark Shuttleworth made that comment as such) and they were going to create a simple symlink that would make it easier to "roll" from each development version into the next (without having to fuss with source lists or doing an actual "upgrade")...

I realized at the time they decided this that it would not be ready in time for the switch over from 12.10 to 13.04 but it has been like 6 months since that time, so i would think that they would have something ready in time for the switch to from 13.10 development to 14.04 development...

So any new information would be appreciated ;)

Also, if any of the moderators, or participators on the ubuntu forums have any contacts with any of the ubuntu developers and might be able to get some information from them and post it here, would also be appreciated as well... 

I found changing the source lists to be a bit too tricky and technical for me personally (and had messed up when i tried) so i would not want to do that again....
If the symlink isn't ready for the switch, i will use one of the early "daily build 14.04s" and do the upgrade from the iso (which is how i moved from 13.04 to 13.10 development)
But of course, it would be great if we could get that easier symlink method by then...because it will simply "point" to each next version automatically...

My main questions are:
1) will the "symlink" or whatever it is be ready in time for the 14.04 change over?
2) how would it be done by the user?  Is it just a simple matter of typing in a command or two in the terminal?
3) How will the Ubuntu Community be notified of when it can be done and the instructions on how to do it?

Thanks in advance to anyone who can get any new information about this...:D

---

### Post by craig10x on 2013-09-14
By the way...i did some googling on the topic and it was hard to find recent updates on this subject...however i did find this blog that was posted by one of the developers who was at the summer conference and posted this information on June 24th:

[COLOR=#000000][FONT=Verdana]During the last Ubuntu vUDS Rick Spencer was tasked with finding a good [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]name for the new development series alias which would allow users to [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]stick to whatever is the current development release (or to use it as an [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]upload target). 

Rick came up with "rolling" as the suggested name. After [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]a bit of discussion between the present TB members, it appears the [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]members prefer "next" instead. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
The main concern about using "rolling" is added confusion with regard [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]to the how Ubuntu is developed as it'd surely be interpreted by some as [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ubuntu being on a Rolling Release schedule which it's not. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The Technical Board didn't make a final decision on the name though as [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Rick couldn't attend the meeting himself to defend his proposal. 

As a[/FONT][/COLOR] [COLOR=#000000][FONT=Verdana]result, the Technical Board feels that Colin should go ahead with the [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]implementation of the feature in Launchpad but not put it live until [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]after our next meeting (8th of July) so to leave until that time for [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Rick to defend his proposal (on our mailing-list or at our next meeting) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]or for someone else to propose a better name. In any case, we expect to [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make a final decision on the matter on the 8th. [/FONT][/COLOR]

---

### Post by JMB74 on 2013-09-14
[http://ubuntuforums.org/showthread.php?t=2172898](http://ubuntuforums.org/showthread.php?t=2172898)

devel repo symlink is already there according to that?

---

### Post by craig10x on 2013-09-14
@jmb74:  Yes, that is probably it...however, they would still need to let us know what command(s) we would need to enter in the terminal to switch over to the "devel" symlink...

I doubt it would be automatic, as i would imagine that some may just want the development version to finalized (as normally happens) where as others may want to set up their development to actually "roll on" to each new version...so some kind of manual entry will no doubt be required...and that is what we will need to know...

---

### Post by grahammechanical on 2013-09-14
So, here is a test for someone who is bored. Put in an install of Saucy and change the repositories from saucy to devel and then do a dist-upgrade and see if anything changes or breaks. In theory or to put it another way, guessing, what is in the devel repositories should be exactly the same as what is at present in the saucy repositories. How bored will I be tomorrow?

Regards.

---

### Post by JMB74 on 2013-09-14
Well doing that with 'devel' gives me exactly the same on a dist-upgrade as 'saucy' in the sources.list

---

### Post by craig10x on 2013-09-14
Interesting...although the whole idea is to make it so you do not have to change the sources list...so that is what i am wondering...
Assuming those devel packages we see on that link page (which duplicates everything you see at the bottom where the saucy packages are listed) how will we change our source from saucy to devel (thus putting us on that symlink) WITHOUT having to actually manually change our source lists???

That is what i would like to know...;)

---

### Post by monkeybrain20122 on 2013-09-14
I asked this question some times ago on Ubuntu Forum and was told basically that the idea was scrapped and that new installation will be required though I don't remember any source was cited. I can't find the thread now as it might be before the UF meltdown (and I typed in the wrong user name when reregistered,--note the extra "2",-- so can't even dig it up from my old posts). Anyway I am going to stick with 13.04 til eol, it is the best Ubuntu release for me so far, don't want to risk f^^king up a good thing until I have to upgrade, wish they make 13.04 the LTR instead of 12.04.

---

### Post by craig10x on 2013-09-14
monkeybrain20122 i had upgraded (using the iso) from 13.04 to 13.10 development and i must tell you it's as solid as 13.04 and continues to improve so it's kind of like 13.04 Plus (lol)...
I was going to just do upgrades (using the iso method) from 13.04 stable to 13.10 stable to 14.04 stable, etc...but now that i am actually back in development again, i figured i might as well try rolling with it...

Would still like to know how it's going to be done....i don't recall seeing anything about the symlink idea being scrapped...they did scrap the idea of a rolling release but decided they would make a development symlink so it could just point at each new version instead of needing to change the source lists each time...

The developers as well as Mark now consider development the rolling version of ubuntu due to the great improvements in automatic quality control checking on the updates which is now quite excellent....

---

### Post by monkeybrain20122 on 2013-09-14
> **craig10x said:**
> monkeybrain20122 i had upgraded (using the iso) from 13.04 to 13.10 development and i must tell you it's as solid as 13.04 and continues to improve so it's kind of like 13.04 Plus (lol)...
..

I can believe that it is all well and good for other things, but how is Xmir? I tried testing several daily isos and every time xmir gave me blackscreen and I don't have the time to try fixing it so I don't bother testing any more, but that was a month ago so hopefully things have improved.

---

### Post by grahammechanical on 2013-09-15
> **JMB74 said:**
> Well doing that with 'devel' gives me exactly the same on a dist-upgrade as 'saucy' in the sources.list

Another thought entered my brain over night. What if those devel repositories are just mirrors of the saucy repositories and are being kept up to date for the day after 13.10 is released and then they get a name change to something beginning with T?

There should be no difference between the devel repositories and the saucy repositories because Saucy is still the development branch. The differences should start a day or two after 13.10 release. So,  as far as I can see, we have two questions

1) will the devel repositories stay devel repositories or will they become T<code name> repositories?
2) will we get some kind of symlink or script to make it easy to switch repositories?

I think I will put in a fresh install of saucy and switch the repositories to devel and then see what happens over the next month. The install will either continue to be updated into November and onwards or not get updated due to broken links to the respositories.

Regards.

---

### Post by mc4man on 2013-09-15
> **monkeybrain20122 said:**
> I can believe that it is all well and good for other things, but how is Xmir? I tried testing several daily isos and every time xmir gave me blackscreen and I don't have the time to try fixing it so I don't bother testing any more, but that was a month ago so hopefully things have improved.

Considering the late date it, (xmir/unity-system-compositor) will be included then nothing is going to really change from now meaning it's use is optional. If it presents issues then simply disable or remove u-s-c completely (and any supporting libs if desired.

If when u-s-c is default installed it presents issues with doing an install then that would be a problem though could be worked around or otherwise grab an iso before that time. 
(the initial 'bug' report on making u-s-c default mentioned Sept. 19th as the cutoff but I think that date **may** be erroneous, could be anytime from now to before FF

---

### Post by JMB74 on 2013-09-15
> **monkeybrain20122 said:**
> I can believe that it is all well and good for other things, but how is Xmir? I tried testing several daily isos and every time xmir gave me blackscreen and I don't have the time to try fixing it so I don't bother testing any more, but that was a month ago so hopefully things have improved.

Happily running saucy here without any Mir/Xmir. Just good old X. 

If you don't like the new display server, just uninstall or disable it and fall back to X.

---

### Post by craig10x on 2013-09-15
@grahammechanical: That should be an interesting "experiment" ;)

Yeah, that is the question...what happens to those duplicate "devel" repos when 13.10 is released...If that is the name of the new rolling development then it should remain the same, while the normal repo lists should change to the new "T" name (whatever they pick for 14.04)...And then some type of symlink command should be supplied by them to the community, if you want the option of continue rolling instead of just finalizing with 13.10...

I wish we could contact one of the developers involved to find out (they must know by now)...that is also why i was asking if anyone here or even any of the moderators, have any contact with any of them and might be able to find out for us curious about it... 

I did try e-mailing Rick Spencer...but no reply...he probably gets tons of e-mails and doesn't have time to reply to most of them, unfortunately...

---

### Post by cariboo on 2013-09-15
@craig10x, you may have better luck, if you ask your question on the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list. This mailing list is open to everyone, and is a good way to ask the devs questions.

---

### Post by grahammechanical on 2013-09-15
Things have improved with xmir. I do not notice any difference between xmir and xserver. With the development branches there are always glitches. We must be careful not to blame xmir when in the past we saw the issue as with Compiz or some video driver or even with xserver and the kernel.

Remember, the ghost app indicator menus? A few months ago Libreoffice menus did not highlight with a mouse over. These affects were nothing to do with xserver. So, why should simliar issues be the fault of xmir? May be. May be not. I remember all the complaints about Compiz that were going around when I first started reading the posts on this section of the forum. Well, 14.10 will not have Compiz. It will have MIR. 

The important point as far as I can see is that with the release of 13.10 there will be six months of user testing until 14:04 is released to the world. We, ubuntu+1 testers, will be running 14.04 development branch and after that 14.10 development branch whether it is rolling or not and that gives us a front row seat.

Regards.

Edit. I am watching for a Saucy ISO that will install with xmir as default. I think the problem will be with the installing of third party software. That automatically includes proprietary video drivers which will then default the installation to xserver. The path has already been trodden by that Xubuntu-xmir ISO that we tested a few weeks ago.

---

### Post by craig10x on 2013-09-15
Thanks Cariboo907 for the suggestion...i will have to check into that...
@grahammechanical: Seems to me that the quality control of the updates for development have become extremely reliable as the developers and Mark have pointed out....

I once ran LMDE (Linux Mint's rolling) and had far more problems with that then i ever have had with ubuntu development so i'd say it's definitely ready to become the rolling version of ubuntu...
I just hope they have that Symlink ready by the 13.10 release...It would make it soooo much easier to switch over ;)

---

### Post by craig10x on 2013-09-15
These were some comments from Rick Spencer i found:
The tech meeting he is referring to happened some time ago...apprently it is the developer Colin Watson that has the technical solution for this...not sure what he means about "subscribing" to the new name that will be symlinked...how would you "subscribe" to it?
[B]
Rolling Release[/B]

[COLOR=#3E3E3E][FONT=Segoe UI]After the unfortunate kerfufle last cycle when I pushed hard to move Ubuntu to a model of LTSs with rolling releases in between, it was nice to close in on one nice outcome. Namely, Colin has a technical solution that will allow users to subscribe to essentially the tip of development. Instead of using &#8220;raring&#8221; or &#8220;saucy&#8221; in your sources lists, you&#8217;ll subscribe to a new name which is symlinked to whatever is the current development release. In this way, each day you will be on the latest. Even the day after a development release becomes a stable release, because the symlink will just point to the next development release.

I ended up with a couple of [action items from this session]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-1305-development-release-planning"). Mostly, to come up with a name and bring it to the next Tech Board meeting for approval. I&#8217;m very much leaning to &#8220;rolling&#8221;, but I am open to discussion ;) This would mean you could say &#8220;I am on Raring&#8221;, or &#8220;I am on Precise&#8221;, or &#8220;I am on Rolling&#8221;. &#8220;I am on Rolling&#8221; means that you are on the tip of development. Fun![/FONT][/COLOR]

---

### Post by PaulW2U on 2013-09-15
But surely 'devel' is the symlink.

How else would you explain the following directory listing?

[ATTACH=CONFIG]246256[/ATTACH]

---

### Post by zika on 2013-09-15
The proof of the pudding's seen i' the eating.
```
:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu saucy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu saucy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu saucy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu saucy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu saucy partner
deb http://extras.ubuntu.com/ubuntu saucy main
# deb http://archive.ubuntu.com/ubuntu saucy-proposed multiverse restricted main universe
#
deb http://archive.ubuntu.com/ubuntu devel main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu devel-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu devel-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse
# deb http://archive.ubuntu.com/ubuntu devel-proposed multiverse restricted main universe
```gives```
...
Fetched 33.1 MB in 42s (773 kB/s)                                              
Reading package lists... Done
W: Conflicting distribution: http://archive.ubuntu.com devel Release (expected devel but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-updates Release (expected devel-updates but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-security Release (expected devel-security but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-backports Release (expected devel-backports but got saucy)
```while```
:~$ cat /etc/apt/sources.list
#deb http://archive.ubuntu.com/ubuntu saucy main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu saucy-updates main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu saucy-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu saucy-backports main restricted universe multiverse
#deb http://archive.canonical.com/ubuntu saucy partner
#deb http://extras.ubuntu.com/ubuntu saucy main
##deb http://archive.ubuntu.com/ubuntu saucy-proposed multiverse restricted main universe
#
deb http://archive.ubuntu.com/ubuntu devel main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu devel-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu devel-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu devel-proposed multiverse restricted main universe
```gives```
Fetched 14.1 MB in 18s (749 kB/s)                                              
Reading package lists... Done
W: Conflicting distribution: http://archive.ubuntu.com devel Release (expected devel but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-updates Release (expected devel-updates but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-security Release (expected devel-security but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-backports Release (expected devel-backports but got saucy)
```again...
O.o o.O
Kerfuffle... Does not look like symlink to me...

---

### Post by grahammechanical on 2013-09-15
@craig10x

> [COLOR=#3E3E3E][FONT=Segoe UI]you&#8217;ll subscribe to a new name which is symlinked to whatever is the current development release. [/FONT][/COLOR]

I am not at all sure how it would all work. At the moment the sources lists contain http links to servers/repositories. But what if the "new name" was part of an http link that was then re-directed to whatever http link was the actual development repository? The six monthly changes to the redirect/symlink would be done at the server/repository end and not at our end as at present.

The sources list of a fresh install of the development branch would point to the usual development repositories but by changing the sources list to the "new name" we would be "subscribing" to having a rolling development install. Do I get a prize if I guess right? NO? Oh well.

I now have a saucy install with devel as the repositories instead of saucy. I ran update and upgrade before changing the sources lists and then again afterward but the system was up to date. So, there is nothing extra in the devel repositories. It could be that devel is actually a symlink. We will not know until after 13.10 release day or until we get some information from on high.

Regards.

---

### Post by craig10x on 2013-09-15
Thanks...you could very well be right...maybe it will work that way...i guess we will find out soon enough....meanwhile, i have also tried e-mailing Colin directly...though i do not know if he will send me a response...i asked the same questions i posted here...

What you said though makes a lot of sense...if it turns out that way, although i can't award you a prize i will certainly acknowledge that you "hit the mark" :D

I just hope we won't have to make our own manual adjustments to the source lists to change over...that it is some command that takes care of that automatically...i am just not good at doing the manual changing...i messed up last time i tried...

I guess that is why i am getting so curious ;)

---

### Post by JMB74 on 2013-09-15
> **grahammechanical said:**
> It could be that devel is actually a symlink.

It is a symlink.

A ftp directory listing shows that.

> ftp> dir
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.

lrwxrwxrwx    1 1002     1002            5 Sep 12 15:34 **devel -> saucy**
lrwxrwxrwx    1 1002     1002           15 Sep 12 15:34 **devel-backports -> saucy-backports**
lrwxrwxrwx    1 1002     1002           14 Sep 12 15:34 **devel-proposed -> saucy-proposed**
lrwxrwxrwx    1 1002     1002           14 Sep 12 15:34 **devel-security -> saucy-security**
lrwxrwxrwx    1 1002     1002           13 Sep 12 15:34 **devel-updates -> saucy-updates**
drwxr-xr-x    6 1002     1002         4096 Oct 14  2011 lucid
drwxr-xr-x    6 1002     1002         4096 Mar 18 05:51 lucid-backports
drwxr-xr-x    6 1002     1002         4096 Sep 13 05:20 lucid-proposed
drwxr-xr-x    6 1002     1002         4096 Aug 01 05:18 lucid-security
drwxr-xr-x    6 1002     1002         4096 Sep 10 05:24 lucid-updates
drwxr-xr-x    6 1002     1002         4096 Oct 14  2011 oneiric
drwxr-xr-x    6 1002     1002         4096 Feb 21  2013 oneiric-backports
drwxr-xr-x    6 1002     1002         4096 Mar 23 05:56 oneiric-proposed
drwxr-xr-x    6 1002     1002         4096 Apr 25 06:21 oneiric-security
drwxr-xr-x    6 1002     1002         4096 Apr 25 06:21 oneiric-updates
drwxr-xr-x    6 1002     1002         4096 Apr 26  2012 precise
drwxr-xr-x    6 1002     1002         4096 Jul 22 05:11 precise-backports
drwxr-xr-x    6 1002     1002         4096 Sep 15 05:16 precise-proposed
drwxr-xr-x    6 1002     1002         4096 Sep 10 05:22 precise-security
drwxr-xr-x    6 1002     1002         4096 Sep 10 05:22 precise-updates
drwxr-xr-x    6 1002     1002         4096 Oct 20  2012 quantal
drwxr-xr-x    6 1002     1002         4096 Jul 31 05:12 quantal-backports
drwxr-xr-x    6 1002     1002         4096 Sep 15 05:15 quantal-proposed
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:08 quantal-security
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:08 quantal-updates
drwxr-xr-x    6 1002     1002         4096 Apr 26 06:42 raring
drwxr-xr-x    6 1002     1002         4096 Sep 08 05:22 raring-backports
drwxr-xr-x    6 1002     1002         4096 Sep 15 05:14 raring-proposed
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:07 raring-security
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:07 raring-updates
drwxr-xr-x    6 1002     1002         4096 Sep 15 05:14 saucy
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:07 saucy-backports
drwxr-xr-x    6 1002     1002         4096 Sep 15 05:14 saucy-proposed
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:07 saucy-security
drwxr-xr-x    6 1002     1002         4096 Sep 11 06:07 saucy-updates

226 Directory send OK.
ftp> 



---

### Post by grahammechanical on 2013-09-15
I often mess up commands. Perhaps, when the time is right, we should create a wiki page that explains all of this and had correctly typed commands that can be copied and pasted into a terminal.

---

### Post by craig10x on 2013-09-15
> **grahammechanical said:**
> I often mess up commands. Perhaps, when the time is right, we should create a wiki page that explains all of this and had correctly typed commands that can be copied and pasted into a terminal.

Big +1...I think that would be a GREAT IDEA...

And sure looks like that is the symlink from what jmb74 posted above...so looks like it should be ready in time for the change over...
perhaps they decided to just called it devel since they felt rolling would be too confusing...even though Rick proposed calling it that, the other developers weren't keen on that name...as you will recall from the conference...

---

### Post by grahammechanical on 2013-09-16
I well, I am back in this Saucy install where I changed the repositories to devel. Update Manager stumbled a bit, telling me to check my internet connection but after a few seconds it offered somthing to update and when I ran apt-get update nothing else was available.

I can tell you this. All the sources are put in the Other Software tab as if they were PPAs. And nothing is ticked in the Ubuntu Software tab. I think this is as it should be. It is why we get that error message about expecting devel main but finding saucy main. It is possible that the symlink to saucy main is not yet in place. May be it will never be in place because the symlink is suppoed to be to Tcode name. I do not know. I am just experimenting. What happens if I try to install something from software centre?

I do think that things are progressing in the direction we would want it to be. Perhaps, it is a bit too early.

Regards.

---

### Post by craig10x on 2013-09-16
Colin was kind enough to answer the e-mail i sent him (and rather promptly too!)...I am going to paste in my questions with his answers which brings us up to date on what is happening with it!
And judging by the answers, looks like indeed that would be the symlink we are seeing on there...However, because of a little bit of a "glitch" which you will read in his answers, it sounds like it could be hit or miss as far as whether it will be ready for the time of the 13.10 to 14.04 switchover (probably depending on whether he gets enough time to correct the problem before then...Otherwise, i would say it would be implemented some time after that...

If that happens, since i myself personally, am kind of fearful of attempting the "change the source lists" method...i may have to end up using an early live daily build iso of 14.04 to make my upgrade to 14.04 development...:(

It does sound like (once he gets the glitch out) that it should be very EASY to switch over using the optional software-properties method he mentioned that will be available...i would assume that feature will be added in the software sources?...probably something you would check i guess...

I'll post the questions and answers in my next post...And a salute to Colin Watson for taking a few minutes out of his busy time to provide me with an update to this interesting new feature that we will (hopefully) soon have available...

By the way, when he says "software-properties" is that the software and updates section we bring up from the dash search?

---

### Post by craig10x on 2013-09-16
Here are my questions to Colin and his answers:

[COLOR=#500050][FONT=arial] My main questions are:
> 1) will the "symlink" or whatever it is be ready in time for the 14.04
> change over?

[/FONT][/COLOR]
[FONT=arial]It's already in place on the server.  However when I tried it in[/FONT]
[FONT=arial]practice I found that apt-get produces warnings; I need to figure out[/FONT]
[FONT=arial]whether the right fix is to change apt or to reimplement things on the[/FONT]
[FONT=arial]server, and I haven't had time for that yet.[/FONT]
[COLOR=#500050][FONT=arial]
> 2) how would it be done by the user? Is it just a simple matter of typing
> in a command or two in the terminal?

[/FONT][/COLOR]
[FONT=arial]There'll be a control for it in software-properties, though in advance[/FONT]
[FONT=arial]of that people can change sources.list.[/FONT]
[COLOR=#500050][FONT=arial]
> 3) How will the Ubuntu Community be notified of when it can be done and the
> instructions on how to do it?

[/FONT][/COLOR]
[FONT=arial]I expect we'll announce it in the usual sorts of places[/FONT]
[FONT=arial](ubuntu-devel-announce, news sites), and I'm sure the word will get[/FONT]
[FONT=arial]around by itself too; I haven't thought about that a whole lot yet.[/FONT][FONT=arial][IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
[/FONT]

---

### Post by zika on 2013-09-16
> **JMB74 said:**
> It is a symlink.

A ftp directory listing shows that.
I was obviuosly tired when I tried... I should have thought of that... Nice proof...

---

### Post by craig10x on 2013-09-16
And confirmed by Colin, in his answers to my e-mail...
Now if he can just get the glitch straightened out and add in the new feature soon..."fingers crossed" (lol) :D

---

### Post by monkeybrain20122 on 2013-09-16
> **grahammechanical said:**
> 
  I remember all the complaints about Compiz that were going around when I first started reading the posts on this section of the forum. Well, 14.10 will not have Compiz. It will have MIR. 

.

Is it supposed to be a good thing? I have never had any issue with Compiz (no big issue anyway, some glitches in 12.04 were fixed by mc4man's ppa )  and it is a lot smoother and with a lot less problems than Kwin and clutter in my experience (with open drivers, nvidia or adm blobs on several machines). I think complaints come from people with very old hardware or gamers mostly (the most demanding and whiny bunch of users. :)) 

Compiz is more than just eye candy, it is very important in making unity productive. I hope that features like multiple desktops, scale and edge flip and application switchers will get ported to Unity 8 (shift switcher a lot faster than Unity's alt-tab and more beautiful too)

---

### Post by craig10x on 2013-09-16
I'm sure mir will work itself out fine..I am just glad to know (thanks to the response i got from Colin Watson, ubuntu developer who is working on it) that the symlink is indeed in place and there will be an easy way for us to add it, and once the "glitch" is worked out, then they will add the feature on...:D

Though no doubt with all the regular stuff he has to do in ubuntu development, it is probably a "side project" so i do wonder if it will be ready and working properly by the time 13.10 is released...
I have this funny feeling i am going to have to do at least one more upgrade from the iso to move into the next development version...but after that, well it should be smooth sailing for Ubuntu Rolling Development...

---

### Post by grahammechanical on 2013-09-17
I was just wondering about all those people moaning in the past about compiz, how many of them are now critical of MIR being developed? That is all.

By the way, I have been able to install Psensor and System Load Indicator through the Software Centre without any problems or error messages but when I tried to install Chromium through the terminal I got "package not available". But the Software Centre installed it just fine. I just now realise that the command should have been chromium-browser and not chromium. I will remove chromium and try again to install it through the terminal.

The only clitch that I have seen is with Software Updater. It gives a check your internet error message but when I click OK it continues and offers updates in the usual way which download and install without issues.

Regards.

Edit: Yes, chromium-browser installs fine through the terminal. This devel installation is working fine.

---

### Post by craig10x on 2013-09-17
When Colin says there will be a control for it in software-properties do you think he is referring to the software and updates section?
That's what it sounds like to me...i assume there would be some box to check added on that would switch everything over (without having to modify the source lists manually as you do now)...

---

### Post by zika on 2013-09-17
> **craig10x said:**
> When Colin says there will be a control for it in software-properties do you think he is referring to the software and updates section?
That's what it sounds like to me...i assume there would be some box to check added on that would switch everything over (without having to modify the source lists manually as you do now)...I do hope there will be a manual/CLI way of doing that...

---

### Post by craig10x on 2013-09-17
Well he did mention you could also modify the source lists manually, so i would imagine that would still be an option as always...but why would you WANT to do it manually if it could do it automatically for you instead?  seems so much easier that way and eliminates the chance of error...I'd use the automatic feature but i would hesitate to do it manually again because i got messed up when i tried it last switch over...

I'd sooner do another upgrade (using live iso) as i have more confidence in that method (after excellent success moving from 13.04 to 13.10 development using that) then doing manual changes in source lists...

---

### Post by grahammechanical on 2013-09-17
Synaptic says this about software-properties "manage the repositories that you install software from." It gives a screenshot that looks very much like the Software Updater/ Update Manager. We also have a python3-software-properties which gives the same screenshot but the one that I find interesting is the screenshot for software-properties-gtk. It brings up a screenshot of the Software Sources/Software and Updates dialog but the language is Italian. The developer must be an Italian.

This is the comment: > This software provides an abstraction of the used apt repositories. It allows you to easily manage your distribution and independent software

So, I guess it is what you think it is. There might be checkboxes in the Other Software tab that can be ticked. It can be done in the terminal. I have already done it using

```
sudo sed -i 's/saucy/devel/g' /etc/apt/sources.list
```

The updates from the devel repositories are mirrowing the updates from the saucy repositories (comparing 2 saucy installs of course)

Regards.

---

### Post by zika on 2013-09-17
> **grahammechanical said:**
> Synaptic says this about software-properties "manage the repositories that you install software from." It gives a screenshot that looks very much like the Software Updater/ Update Manager. We also have a python3-software-properties which gives the same screenshot but the one that I find interesting is the screenshot for software-properties-gtk. It brings up a screenshot of the Software Sources/Software and Updates dialog but the language is Italian. The developer must be an Italian.

This is the comment: 

So, I guess it is what you think it is. There might be checkboxes in the Other Software tab that can be ticked. It can be done in the terminal. I have already done it using

```
sudo sed -i 's/saucy/devel/g' /etc/apt/sources.list
```

The updates from the devel repositories are mirrowing the updates from the saucy repositories (comparing 2 saucy installs of course)

Regards.I still do get:```
W: Conflicting distribution: http://archive.ubuntu.com devel Release (expected devel but got saucy)W: Conflicting distribution: http://archive.ubuntu.com devel-updates Release (expected devel-updates but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-security Release (expected devel-security but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-backports Release (expected devel-backports but got saucy)
```
Should I just disregard these warnings?
Or, just a random thought, should I clear package database and let it form from a scratch...?
Second thought: no that would not help, warning is very clear and, as a matter of fact, quite right... It did expect devel and got saucy, via simlink... ;)

---

### Post by craig10x on 2013-09-17
@zika: he (Colin) did mention this: (maybe that relates to your results...and this is the glitch he has to work out to get this going properly)
[COLOR=#000000][FONT=arial]
It's already in place on the server. However when I tried it in[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]practice I found that apt-get produces warnings; I need to figure out[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]whether the right fix is to change apt or to reimplement things on the[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]server, and I haven't had time for that yet.

@grahammechanical:  yeah, then i guess that is what he was talking about...he will probably add a tab in the software sources section where you could tick the proper items to make the change over to the new symlink)...[/FONT][/COLOR]

---

### Post by zika on 2013-09-17
> **craig10x said:**
> @zika: he (Colin) did mention this: (maybe that relates to your results...and this is the glitch he has to work out to get this going properly)
[COLOR=#000000][FONT=arial]
It's already in place on the server. However when I tried it in[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]practice I found that apt-get produces warnings; I need to figure out[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]whether the right fix is to change apt or to reimplement things on the[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]server, and I haven't had time for that yet.

@grahammechanical:  yeah, then i guess that is what he was talking about...he will probably add a tab in the software sources section where you could tick the proper items to make the change over to the new symlink)...[/FONT][/COLOR]
I just gave a try now, it seems that I can work with apt-get despite these warnings as if nothing were wrong... We'll see...

---

### Post by zika on 2013-09-20
UPS:
```
W: Conflicting distribution: http://archive.ubuntu.com devel Release (expected devel but got saucy)
W: Conflicting distribution: http://archive.ubuntu.com devel-updates Release (expected devel-updates but got raring)
W: Conflicting distribution: http://archive.ubuntu.com devel-security Release (expected devel-security but got raring)
W: Conflicting distribution: http://archive.ubuntu.com devel-backports Release (expected devel-backports but got raring)
```
It is rolling but backwards...?
Now I see why I was getting some packages on wait and similtar stuff last few days... O.o

---

### Post by grahammechanical on 2013-09-20
I am using Software Updater. At first it gave a "check your internet connection " error message but clicking OK would allow the utility to run its course as usual. Now I am getting the Partial Upgrade invitation which we often get during the development cycle.

I look at it this way: At the start of the development cycle when we first change the repositories to the new name we find that not all the repositories are in place. Such as extras. So, we get warnings. I think that what we are seeing now is the same thing. The difference being that now the link to the missing devel repositories is trying to direct apt-get to the equivalent raring/saucy repositories and it is not working so well. Or at least just giving an error message.

The question to ask is: if these repositories are not giving the rolling development version updates, does it matter when it is a rolling development version? So, do we need a backports repository in a rolling development version? Can we live with these error messages?

Regards.

---

### Post by ventrical on 2013-09-20
I did an experiment with the sources list and used 'tenacious' (with the assumption that the next release will be named 'tenacious tiger') instead of 'devel'. My assumption was that  the sources list would cough up info on any abitrary file entered into it:



```

ventrical@ventrical-asus:~$ sudo sed -i 's/saucy/tenacious/g' /etc/apt/sources.list
ventrical@ventrical-asus:~$ sudo apt-get update && apt-get dist-upgrade
Ign http://security.ubuntu.com tenacious-security InRelease
Ign http://security.ubuntu.com tenacious-security Release.gpg                  
Ign http://security.ubuntu.com tenacious-security Release                      
Ign http://extras.ubuntu.com tenacious InRelease                               
Ign http://extras.ubuntu.com tenacious Release.gpg                             
Ign http://extras.ubuntu.com tenacious Release                                
Err http://extras.ubuntu.com tenacious/main Sources                            
  404  Not Found
Err http://extras.ubuntu.com tenacious/main i386 Packages                      
  404  Not Found
Ign http://extras.ubuntu.com tenacious/main Translation-en_CA                 
Ign http://extras.ubuntu.com tenacious/main Translation-en                    
Err http://security.ubuntu.com tenacious-security/main Sources                
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/restricted Sources          
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/universe Sources
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/multiverse Sources
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/main i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Ign http://security.ubuntu.com tenacious-security/main Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/main Translation-en
Ign http://security.ubuntu.com tenacious-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/multiverse Translation-en
Ign http://security.ubuntu.com tenacious-security/restricted Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/restricted Translation-en
Ign http://security.ubuntu.com tenacious-security/universe Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/universe Translation-en
33% [Connecting to ca.archive.ubuntu.com (91.189.91.15)]
33% [Connecting to ca.archive.ubuntu.com (91.189.91.15)]^Cventrical@ventrical-asus:~$ 
ventrical@ventrical-asus:~$ sudo apt-get update
Ign http://security.ubuntu.com tenacious-security InRelease
Ign http://security.ubuntu.com tenacious-security Release.gpg                  
Ign http://security.ubuntu.com tenacious-security Release                      
Ign http://extras.ubuntu.com tenacious InRelease                               
Ign http://extras.ubuntu.com tenacious Release.gpg                             
Ign http://extras.ubuntu.com tenacious Release                                
Err http://extras.ubuntu.com tenacious/main Sources                            
  404  Not Found
Err http://extras.ubuntu.com tenacious/main i386 Packages                      
  404  Not Found
Ign http://extras.ubuntu.com tenacious/main Translation-en_CA                 
Ign http://extras.ubuntu.com tenacious/main Translation-en                    
Err http://security.ubuntu.com tenacious-security/main Sources                
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/restricted Sources          
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/universe Sources
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/multiverse Sources
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/main i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com tenacious-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Ign http://security.ubuntu.com tenacious-security/main Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/main Translation-en
Ign http://security.ubuntu.com tenacious-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/multiverse Translation-en
Ign http://security.ubuntu.com tenacious-security/restricted Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/restricted Translation-en
Ign http://security.ubuntu.com tenacious-security/universe Translation-en_CA
Ign http://security.ubuntu.com tenacious-security/universe Translation-en
33% [Connecting to ca.archive.ubuntu.com 

```


then I did this:

```
ventrical@ventrical-asus:~$ sudo sed -i 's/tenacious/devel/g' /etc/apt/sources.list
ventrical@ventrical-asus:~$ sudo apt-get update
Ign http://security.ubuntu.com devel-security InRelease
Get:1 http://security.ubuntu.com devel-security Release.gpg [933 B]            
Get:2 http://security.ubuntu.com devel-security Release [49.6 kB]              
Get:3 http://security.ubuntu.com devel-security/main Sources [14 B]            
Get:4 http://security.ubuntu.com devel-security/restricted Sources [14 B]      
Get:5 http://security.ubuntu.com devel-security/universe Sources [14 B]        
Get:6 http://security.ubuntu.com devel-security/multiverse Sources [14 B]      
Get:7 http://security.ubuntu.com devel-security/main i386 Packages [14 B]      
Get:8 http://security.ubuntu.com devel-security/restricted i386 Packages [14 B]
Get:9 http://security.ubuntu.com devel-security/universe i386 Packages [14 B]  
Get:10 http://security.ubuntu.com devel-security/multiverse i386 Packages [14 B]
Get:11 http://security.ubuntu.com devel-security/main Translation-en [14 B]    
Get:12 http://security.ubuntu.com devel-security/multiverse Translation-en [14 B]
Get:13 http://security.ubuntu.com devel-security/restricted Translation-en [14 B]
Get:14 http://security.ubuntu.com devel-security/universe Translation-en [14 B]
Ign http://security.ubuntu.com devel-security/main Translation-en_CA           
Ign http://security.ubuntu.com devel-security/multiverse Translation-en_CA     
Ign http://security.ubuntu.com devel-security/restricted Translation-en_CA     
Ign http://security.ubuntu.com devel-security/universe Translation-en_CA       
Ign http://extras.ubuntu.com devel InRelease                                   
Ign http://extras.ubuntu.com devel Release.gpg                                 
Ign http://extras.ubuntu.com devel Release               
Err http://extras.ubuntu.com devel/main Sources                                
  404  Not Found
Err http://extras.ubuntu.com devel/main i386 Packages                          
  404  Not Found
Ign http://extras.ubuntu.com devel/main Translation-en_CA                      
Ign http://extras.ubuntu.com devel/main Translation-en                         
100% [Connecting to ca.archive.ubuntu.com (91.189.91.15)]

```

at which point it froze up. The I did this:

```

^Cventrical@ventrical-asus:~$ 
ventrical@ventrical-asus:~$ sudo sed -i 's/devel/saucy/g' /etc/apt/sources.list
ventrical@ventrical-asus:~$ sudo apt-get update && apt-get dist-upgrade
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy InRelease          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates InRelease   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports InRelease                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources 
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy Release [49.6 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports Release                       
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Sources [1,012 kB]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_CA     
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Sources [6,598 B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_CA       
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Sources [6,097 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_CA                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                         
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Sources [175 kB]           
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main i386 Packages [1,262 kB]         
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted i386 Packages [10.0 kB]    
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe i386 Packages [5,647 kB]    
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse i386 Packages [133 kB]    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Translation-en_CA                  
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/main Translation-en [713 kB]         
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Translation-en [101 kB]   
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Translation-en [2,904 B]  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Translation-en_CA              
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/universe Translation-en [3,879 kB]   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Sources                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main i386 Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Translation-en           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/multiverse Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy/restricted Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/main Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/multiverse Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/restricted Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-updates/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/multiverse Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) saucy-backports/universe Translation-en_CA    
Fetched 19.1 MB in 1min 15s (253 kB/s)                                         
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ventrical@ventrical-asus:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libunity-core-6.0-7 linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic unity unity-lens-applications
  unity-services
The following packages will be upgraded:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo apparmor apport apport-gtk apt apt-transport-https
  apt-utils at-spi2-core avahi-autoipd avahi-daemon avahi-utils bamfdaemon
  bind9-host binutils ca-certificates-java checkbox checkbox-qt cpp-4.8 cups
  cups-browsed cups-bsd cups-client cups-common cups-daemon cups-filters
  cups-ppdc cups-server-common dh-python dmidecode dmsetup dmz-cursor-theme
  dnsutils duplicity empathy empathy-common file-roller firefox
  firefox-locale-en flashplugin-installer foomatic-db-compressed-ppds gcc-4.8
  gcc-4.8-base ghostscript ghostscript-x gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-gmenu-3.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gir1.2-notify-0.7 gir1.2-syncmenu-0.1
  gnome-accessibility-themes gnome-control-center gnome-control-center-data
  gnome-control-center-datetime gnome-desktop3-data gnome-icon-theme
  gnome-menus gnome-orca gnome-session gnome-session-bin gnome-session-common
  gnome-settings-daemon grub-common grub-pc grub-pc-bin grub2-common
  gstreamer1.0-alsa gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-tools
  gstreamer1.0-x gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs hplip hplip-data hud ibus ibus-gtk ibus-gtk3 ifupdown
  indicator-bluetooth indicator-datetime indicator-messages indicator-power
  indicator-sound indicator-sync isc-dhcp-client isc-dhcp-common
  language-pack-en language-pack-gnome-en libaccounts-qt5-1 libapparmor-perl
  libapparmor1 libapt-inst1.5 libapt-pkg4.12 libasan0 libasound2
  libasound2-data libatk-adaptor libatk-bridge2.0-0 libatomic1 libatspi2.0-0
  libaudio2 libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-core7 libavahi-glib1 libavahi-gobject0 libbamf3-2 libbind9-90
  libbonobo2-0 libbonobo2-common libboost-date-time1.53.0
  libboost-program-options1.53.0 libboost-system1.53.0 libcups2 libcupscgi1
  libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1 libdjvulibre-text
  libdjvulibre21 libdns99 libfontembed1 libgail-3-0 libgcc-4.8-dev libgcc1
  libgdata-common libgdata13 libglib2.0-0 libglib2.0-bin libglib2.0-data
  libgnome-control-center1 libgnome-desktop-3-7 libgnome-menu-3-0 libgomp1
  libgpg-error0 libgpod-common libgpod4 libgs9 libgs9-common
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0
  libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0
  libhpmud0 libhud-client2 libibus-1.0-5 libindicator3-7 libindicator7
  libisc95 libisccc90 libisccfg90 libitm1 liblightdm-gobject-1-0 liblvm2app2.2
  liblwres90 libmessaging-menu0 libmirclient2 libmirplatform libmirprotobuf0
  libmirserver1 libnet-dns-perl libnm-glib-vpn1 libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libnotify-bin libnotify4 liborbit2 libpam-systemd
  libparted0debian1 libpci3 libpulse-mainloop-glib0 libpulse0 libpulsedsp
  libqt5location5 libqt5qml5 libqt5quick5 libqt5webkit5 libquadmath0
  libquvi-scripts libsane-hpaio libstdc++6 libsync-menu1 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libudev1 libupower-glib1
  libvisio-0.0-0 libwpd-0.9-9 libxcb-dri2-0 libxcb-glx0 libxcb-randr0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync0 libxcb-xfixes0 libxcb1
  libyelp0 lightdm linux-firmware linux-libc-dev lsb-base lsb-release
  mcp-account-manager-uoa mobile-broadband-provider-info mountall
  nautilus-sendto-empathy network-manager network-manager-gnome
  openprinting-ppds parted pciutils printer-driver-foo2zjs
  printer-driver-hpcups printer-driver-postscript-hp pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils
  python-cupshelpers python-gi python-gi-cairo python-gobject python-ibus
  python-oauthlib python-sip python3-apport python3-distupgrade python3-gi
  python3-gi-cairo python3-oauthlib python3-problem-report python3-pyatspi
  python3-update-manager shotwell shotwell-common software-center
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev systemd-services telepathy-gabble thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us ttf-ubuntu-font-family ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-settings udev unattended-upgrades
  unity-scope-home unity-scopes-master-default unity-system-compositor
  unity-webapps-common update-manager update-manager-core update-notifier
  update-notifier-common upower x11-xserver-utils xdiagnose xorg-docs-core
  xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-radeon
  yelp
305 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 181 MB of archives.

```

which fixed  it and reverted me back to saucy.


 This tells me that I can put in any abitrary first before last prefix and it will create a sources list, however nonfunctional.

 It's just an experiment to demonstrate the vanilla file structure of some aspects of the sources list editing framework.
```

ventrical@ventrical-asus:~$ sudo sed 's/saucy/devel/g' /etc/apt/sources.list
#deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Alpha i386 (20130716)]/ tenacious main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious universe
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ tenacious-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ tenacious-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu tenacious-security main restricted
deb-src http://security.ubuntu.com/ubuntu tenacious-security main restricted
deb http://security.ubuntu.com/ubuntu tenacious-security universe
deb-src http://security.ubuntu.com/ubuntu tenacious-security universe
deb http://security.ubuntu.com/ubuntu tenacious-security multiverse
deb-src http://security.ubuntu.com/ubuntu tenacious-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu tenacious partner
# deb-src http://archive.canonical.com/ubuntu tenacious partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu tenacious main
deb-src http://extras.ubuntu.com/ubuntu tenacious main

```

Regards..

---

### Post by grahammechanical on 2013-09-20
Hi ventrical. I have been waiting for your input to this enquiry. "Tenacious Tiger?" Aiming for the Indian market are we? :)

Whatever, the next code name is, I am getting updates with a sources list pointing to devel repositories. I think that at the moment with a couple of exceptions they are just mirrors of the saucy repositories. It remains to be seen if we continue to get updates once the saucy repositories are stabilised when saucy is released. Then we will be on a rolling development branch. Roll on the Tenacious Tiger!

Regards.

---

### Post by ventrical on 2013-09-20
> **grahammechanical said:**
> Hi ventrical. I have been waiting for your input to this enquiry. "Tenacious Tiger?" Aiming for the Indian market are we? :)

:) lol Siberia? :)

> 
Whatever, the next code name is, I am getting updates with a sources list pointing to devel repositories. I think that at the moment with a couple of exceptions they are just mirrors of the saucy repositories. It remains to be seen if we continue to get updates once the saucy repositories are stabilised when saucy is released. Then we will be on a rolling development branch. Roll on the Tenacious Tiger!

Regards.

Yes .. it is almost like a roll-back repository system but I think it is like you say  "they are just mirrors"  so there must be an asign and much less sophisticated than I have pressumed .

Regards..

---

### Post by craig10x on 2013-09-20
Probably the various error messages and oddities you guys are getting relates to the problem that Colin, the ubuntu developer has to fix on it which he described in his e-mail reply to me...once that is straightened out, i would imagine things should go very smoothly...my only hope is he gets the time to fix it before the change over to 14.04...If not, no doubt he will get it working sometime after that...

For you guys...it will be easy....you 'll just change your source lists over (for the last time) to 14.04 and when he gets the symlink fixed and ready for use, you will just add it in and be all set...

For myself...since i mess up when it comes to changing over the source lists, i would probably have to do one more upgrade to 14.04 development, using an early daily build iso for 14.04 when they start coming out...Then, after that, i should be able to properly switch to Rolling using Colin's new symlink method... :D

---

### Post by craig10x on 2013-09-21
I'll try contacting Colin again about a week before the final release of 13.10 but i suspect he probably won't have it fixed in time for the switch over...so for you guys, you will probably need to change the source lists to 14.04 (whatever they decide to call it) and for me, it will be one more upgrade...i am sure he will get the problem sorted out and the new feature added some time during the 14.04 development cycle ;)

---

### Post by zika on 2013-09-21
> **craig10x said:**
> I'll try contacting Colin again about a week before the final release of 13.10 but i suspect he probably won't have it fixed in time for the switch over...so for you guys, you will probably need to change the source lists to 14.04 (whatever they decide to call it) and for me, it will be one more upgrade...i am sure he will get the problem sorted out and the new feature added some time during the 14.04 development cycle ;)As we did already so many times before...

---

### Post by rrnbtter on 2013-09-21
Greetings,
I intend to do a complete reinstall when the Final Release occurs. A reinstall is the best latent bug remover that I have found. This x-mir already runs beyond any hope or expections that I may have for my Intel system. My only regret is that we probably won't be getting Unity 8 with this release.  All that being said, what I have now is perfect.

---

### Post by craig10x on 2013-09-21
> **rrnbtter said:**
> Greetings,
I intend to do a complete reinstall when the Final Release occurs. A reinstall is the best latent bug remover that I have found. This x-mir already runs beyond any hope or expections that I may have for my Intel system. My only regret is that we probably won't be getting Unity 8 with this release.  All that being said, what I have now is perfect.

That is also something i am considering...i absolutely love the further improvements on 13.04 that have occurred during 13.10 development...
Actually my original plan was to run 13.04 stable until 13.10 final arrived and then i was going to try my first "upgrade from iso" but my curiosity got the better of me, and i did the upgrade during the mid cycle of development...

So as a possible alternate route to staying on (the eventual) rolling development would be to simply upgrade into each new stable version of ubuntu...thus kind of getting a rolling ubuntu in that manner (not a day to day rolling but version to version rolling with all the newest features)...

My success with doing the upgrade directly from the iso is making me consider that alternate option very seriously...of course, my hope would be that each upgrade goes as smoothly as my first did...it was a REAL TIME SAVER for me (not having to add in all my extra apps and data again)... :D

Of course, that would mean i would want to fresh install 13.10 final to start on such a stable to stable rolling version, since i'd want to kind of "clear things out" and start fresh with 13.10 since i have been in development all this time...And that would mean re-installing programs and data again but hopefully, for the last time (lol)! ;)

---

### Post by rrnbtter on 2013-09-21
Greetings,

> **craig10x said:**
> That is also something i am considering...i absolutely love the further improvements on 13.04 that have occurred during 13.10 development...
Actually my original plan was to run 13.04 stable until 13.10 final arrived and then i was going to try my first "upgrade from iso" but my curiosity got the better of me, and i did the upgrade during the mid cycle of development...  ;)

We are on the exact same page. I also stayed back on 13.04 due to the heavy breakage when 13.10 started. I have the heart to test but not the time.  My wife is still using Raring and is very pleased.  I think I will stay with Saucy when it releases just to see the further development that occurs. Also it gives the software devs time to catch-up. Quite often the complaints with a release are with Software and not with the OS. If Unity 8 arrives in the next dev I will switch.

---

### Post by Mateusz Stachowski on 2013-09-21
> **craig10x said:**
> 
My success with doing the upgrade directly from the iso is making me  consider that alternate option very seriously...of course, my hope would  be that each upgrade goes as smoothly as my first did...it was a REAL  TIME SAVER for me (**not having to add in all my extra apps and data  again**)... :grin:


In your previous forum [thread]("http://ubuntuforums.org/showthread.php?t=2171771")  about upgrading with live iso you mentioned that it removed Google  Chrome but I'm curious is that the only thing that it removed. What  about all the other extra apps that you mention. Did you install them  from repos or PPA or with 3rd party package.

I have quite a lot  things installed and I wouldn't want to install all of that again. I've  been using Ubuntu since 8.04 and always upgrading the system with the  usual upgrade command. Through all these years I've had only one broken  upgrade. I think it was when going from 10.10 to 11.04. I also decided  to start a fresh install when 12.04 LTS came out because things were  definitely slowing down (all that clutter from older releases) and the  new install was much faster in the end. Now that 12.04 install started 27th April 2012:

```
$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
kwi 27 2012


```

and  it was already upgraded to 12.10 Final and then to 13.04 Beta. That was  with upgrader but I will probably use live iso for 13.10 upgrade.

---

### Post by craig10x on 2013-09-21
@rnnbtter: Yes we are absolutely on the same page...when i got into 13.10 development it wasn't until about mid development, so apparently i avoided any early cycle borking (as it were)...my updates have been very smooth every day but then i wasn't in during the early stages...so it probably would be much safer to go from version to version "rolling" by doing iso upgrading as a means of accomplishing that...and with far far less potential problems, if any....I was really amazed at how well the iso upgrading works these days...But rather then upgrade each time into development, i am considering just a clean install of 13.10 stable when it arrives and then try to upgrade as each new stable versions becomes available...

@Mateusz: Well, let's see....my upgrade into 13.10 (using the live iso method) was my first attempt at upgrading...I figured it would be the safest and most potentially reliable way, as compared to doing it either by terminal or using the software updater (both which require it keep going to the internet for files, as opposed to live iso where it does it DIRECTLY from the disc image)....

A friend of mine had done the upgrade from iso method about a year ago and he had the same success so that encouraged me to try it and i was not disappointed...
The only outside programs i use are Google Chrome and the web8 oracle java installer and updater...everything else i get from ubuntu software center and all of those carried over...

The key things are:  1) you should have you important data backed up (like music, videos, documents, photos, etc) backed up just in case....i have mine on a 32 gb flash drive myself (i get the San Disk ones from Radio Shack here in the U.S. and they are great)...
                             
2) Any ppas should be unchecked prior to doing the upgrade (in the software sources of your updater)...
                             
3) after installing, as long as it is a ppa that is not ubuntu version specific (where it says, for example: saucy) no problem...but any "specific" (to the version) ones you should delete and replace with the new version's ppa
                                 in my case, i had only 2....Google Chrome (which is not ubuntu version specific) and web8's oracle java updater...that one was version specific so i deleted it (and my oracle java) and re-installed their latest ppa for it...Chrome i simply checked again and it worked fine....
                             
All my data and files were carried over in the upgrade....the majority of my previous settings as well...i think the volume control was one of the few things i needed to reset to my preferred level (it returned to default)...All my added apps were carried over, with their settings and everything...

There was only 2 apps that were knocked out...Google Chrome and MS-Core Fonts....both which have license agreements and that is likely why they didn't carry over...

I re-installed Chrome from a new deb file...it remembered all my previous settings!
I re-installed MS Core Fonts...actually ubuntu software centre said it was installed but i could tell from the looks on web pages that it wasn't really....so i simply uninstalled and then re-installed it and that took care of it...

So, to do that, took like 15 minutes instead of spending hours, putting programs on, re-installing my data, etc...a BIG time saver....

When upgrading iso, it looks like a normal fresh install with slide show and everything...it is only if you look at the technical stuff going on underneath that you see certain different things are going on...
Time usually taken for a fresh install...about 20 minutes....Time taken to do an Upgrade from the iso...about 25 minutes....i was amazed at how fast it was...:D

It also seems to do a great job of replacing stuff from previous version...on package manager i don't see any listings for the kernel that 13.04 has, for example)...i think it is probably the BEST way to upgrade and it is also the fastest...

---

### Post by grahammechanical on 2013-09-21
> [COLOR=#000000]My only regret is that we probably won't be getting Unity 8 with this release[/COLOR]

True, but I think that the next 8 to 10 months will be very interesting to those who have an install of the development branch. We know that proprietary vider drivers issues apart, 13.10 will default to xmir. Which means that it will also default in 14.04 LTS. We have also been told that Mir & Unity 8 will come into 14.10. But this is what interests me. Ubuntu Touch will be running on Mir and it was said that the Ubuntu Edge superphone would get an OS update about a month after the device was shipped to all those who had ordered one. That update was to bring in the convergence function - plug in a monitor and get a PC.

So, I am guessing that some point over the coming months Mir and Unity 8 will be tested on the 14.04 development branch even though it will not be going into 14.04. Or perhaps soon after 14.04 is released. I cannot wait.

---

### Post by craig10x on 2013-09-21
@grahammechanical:  I was curious...both my experiences in ubuntu development (13.04 and 13.10) has involved getting in at about "mid point"...in other words, about 3 months in...
At that point, i found that updates were never a problem really...but i was wondering how it is during the first few months (i just mean the standard updates...not doing fancy stuff like trying kernels in advance, etc...just the stuff ubuntu will normally send you)...

---

### Post by jerrylamos on 2013-09-22
> **craig10x said:**
> @grahammechanical:  I was curious...both my experiences in ubuntu development (13.04 and 13.10) has involved getting in at about "mid point"...in other words, about 3 months in...
At that point, i found that updates were never a problem really...but i was wondering how it is during the first few months (i just mean the standard updates...not doing fancy stuff like trying kernels in advance, etc...just the stuff ubuntu will normally send you)...

Very early on, usually O.K. not much has changed.

Then  a month or two in the floodgates open and anything and everything happens.

Now with rolling updates I'd expect hitches from time to time as linux images change and desktops change which could happen anytime.

Lately my major hang ups have been with the display support mir and xmir.  I'd expect problems in that area for months (years) as ubuntu development tries to find the least common denominator between pc's, tablets, and phones.  Oh, yes, ubuntu on chromebook.  Only one of those I don't have is phone.

---

### Post by cariboo on 2013-09-22
@craig10x, I think what you experienced was an in place install, in other words, a new installation was done, without formatting the partition, that's why you had to re-install chrome and MS-Core Fonts.

---

### Post by craig10x on 2013-09-22
Ah...interesting, cariboo907...that could very well be...have to tell you this, however it does it, it sure works very well...I was encouraged to try it because a friend of mine had done it about a year ago, and had much the same results...Other then those 2 items i had to re-install, and a few settings that had returned to default, everything else was moved over exactly as i had it...even things like the pixel size of my unity dock that i had it set at, appearance theme (radiance) etc...all my data and files too...When i re-installed Chrome, all my settings that i had originally set it to came right back as well...

It seems to be a very reliable way to upgrade....i guess it is kind of like a clean install but it also brings in just about everything you had before...perhaps when you do it via terminal or the software updater, it works in a different manner...So, based on my experience, i would HIGHLY recommend doing upgrades via live iso installer...

Request cariboo:  please change that new avatar you have...hard to look at ;)
You're a Canadian aren't you?  How about a nice moose instead...:D

---

### Post by craig10x on 2013-09-22
A bit off topic...but i was curious about "mir"...I read many articles that it is shipping with 13.10 release and i do see it when i check in the synaptic package manager (though it does not appear to be installed)...
I know it only works with open source drivers and my computer is all intel with the intel processor and graphics card (intel has no proprietary option as it's open source driver is identical as i am sure you all know)...

So, since i am running an open source driver, i would assume it has not yet been enabled in the updates...though i know it can be optionally installed...do you think it will be enabled before the final release?

---

### Post by mc4man on 2013-09-22
> **craig10x said:**
> ...do you think it will be enabled before the final release?
they have until final freeze to make u-s-c (xmir) default installed, odds are heavily in favour of that happening

[https://wiki.ubuntu.com/Mir/13.10AcceptanceCriteria](https://wiki.ubuntu.com/Mir/13.10AcceptanceCriteria)

[https://bugs.launchpad.net/ubuntu/+source/unity-system-compositor/+bug/1218097](https://bugs.launchpad.net/ubuntu/+source/unity-system-compositor/+bug/1218097)

---

### Post by craig10x on 2013-09-22
Thanks...appreciate the link too...yeah, i see the packages are already in, so looks like it is just a matter of them enabling it by default by the final freeze on October 10th...

---

### Post by craig10x on 2013-09-23
Are there any substantial advantages of doing a clean install of 13.10 when it is released as opposed to just letting my 13.10 development "finalize" itself?

I think i will be going stable to stable from this point (using upgrade from iso to roll into each new stable release) but i am debating whether i should clean install 13.10 final when it arrives or just letting my development go to final and keep it that way until i upgrade to 14.04 final when it's released next April....

All feedback and thoughts on this appreciated :D

---

### Post by JMB74 on 2013-09-24
A clean install resets everything to default configs, so removes any hassle that might be caused by changes you have made manually to things that you might have forgotten about but don't play well with new packages/versions. Also clears out all the residual and obsolete packages, dependencies and libraries that can be left behind when just upgrading multiple times.

Personally I have no trouble just running with an upgraded version though. This laptop was originally clean installed on quantal, and has been twice been upgraded mid development cycle by the brute force method of switching out the sources.list to the new version and dist-upgrade. Still running just fine and has allowed me to keep custom  software and settings, whereas a clean install would have involved a significant amount of tinkering to get thinks back the way I like it and reinstall/config software.

---

### Post by craig10x on 2013-09-24
@JMB74: yeah, i was thinking the same thing...as long as everything is running ok, perhaps better just to leave things be and let it finalize as it is...then when i upgrade to 14.04 stable next April...using the live iso, it should clear out all the left over stuff when it installs the 14.04 version, and just carries over my actual programs and data files...

So i guess unless i notice any bugs induced by all the updating during the development, then there really would not be a pressing need to do a clean re-install of 13.10...and it would save me the hassle of having to put all my favorite programs back on and transferring my data files back on again...

I used the upgrade from iso method to move into this development, so it had pretty much cleaned out all remnants of my 13.04 install anyway...of course, in development i have gotten tons of updates, but everything seems to be working ok...and when i upgrade to 14.04 stable from this, i will be using the same method again to change over to it...

Appreciate the input and if anyone else has any comments/feedback on this...let me know :)

---

### Post by jerrylamos on 2013-09-24
From a testing view, I frequently find bugs on the release .iso.
I have also found some differences in things like desktop.
Now if disk space is of interest, multiple updates occupy more and more disk space.  I usually have four linux plus library on my ssd which can get tight.

Now if you want fewer bugs, just update.

---

### Post by su:bhatta on 2013-09-24
+1 to upgrading than fresh install.
I'd hate to lose all the applications and related settings I've introduced to my Ubuntu Studio, not to mention drivers et al.

I have upgraded and been happy with it during Maverick to Natty, and in this bout with Ubuntu, returning after a couple of years, I'm just gonna update from 13.10 to 14.04 to 14.10...(in case there is no major problems with Mir)

---

### Post by cariboo on 2013-09-24
> **jerrylamos said:**
> From a testing view, I frequently find bugs on the release .iso.
I have also found some differences in things like desktop.
Now if disk space is of interest, multiple updates occupy more and more disk space.  I usually have four linux plus library on my ssd which can get tight.

Now if you want fewer bugs, just update.

You can reduce disk space usage, by cleaning out /var/cache/apt/archives using apt-get clean.

Before:

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.9G  2.2G  77% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.7M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  780K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   83G  124G  40% /home
```

After:

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.3G  2.7G  71% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.7M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  780K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   83G  124G  40% /home
```

I just cleaned the archive directory out last week, so there isn't a great difference, but I did gain about 500MiB.

---

### Post by jerrylamos on 2013-09-24
After updates, if it includes a linux image, I do:
sudo apt-get purge linux-image-3.10.0-7           or whatever ls /boot shows
sudo apt-get purge linux-headers-3.10.0-7
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Still lately after install then a couple weeks of daily updates the disk image from df shows 500,000 more bytes used.  Maybe there are some big fat logs somewhere?

---

### Post by cariboo on 2013-09-25
> **jerrylamos said:**
> Still lately after install then a couple weeks of daily updates the disk image from df shows 500,000 more bytes used.  Maybe there are some big fat logs somewhere?

The log files that you should be checking when you run into problems are always located in /var/log. Ubuntu has logrotate installed by default, so new logs files are created periodically, the archived logs have a gzip (gz) file extension. It is usually safe to remove these files, unless you are working with a developer to resolve a problem.

---

### Post by craig10x on 2013-09-25
So looks like the general consensus is to just let it finalize without a clean re-install...i think that is the way i will be going...unless i detect any bugs that aren't on the final release (i always download the final anyway for a back up)...so i will check that when it comes out, and if there doesn't appear to be any real difference, i will save myself the bother of having to put all those programs and data back on again...

I don't think i will be continuing in development...probably at this point just roll with each new version by using the "upgrade from the iso installer" method to do that...i always like to have the newest version of ubuntu but i was tiring of doing clean re-installs with all the work it entails, every time...

I would have stayed in development, but i am not really a true "tester" basically just wanted a "rolling ubuntu" and i do get the impression from most of you testers that the early stages of each development release (first 3 months or so) can be a bit on the "dicey" side so i guess i better play it the safer way ;)

---

### Post by Mateusz Stachowski on 2013-09-25
> **jerrylamos said:**
> After updates, if it includes a linux image, I do:
sudo apt-get purge linux-image-3.10.0-7           or whatever ls /boot shows
sudo apt-get purge linux-headers-3.10.0-7
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Still lately after install then a couple weeks of daily updates the disk image from df shows 500,000 more bytes used.  Maybe there are some big fat logs somewhere?

You should check /var/log just like cariboo already suggested. I had there files larger than 1 GB. You can check it from terminal with this command:

```
find /var/log -size +100000k
```

This will search for files larger than 100 MB.

---

### Post by grahammechanical on 2013-09-25
@craig10x

> [COLOR=#000000]A bit off topic...but i was curious about "mir"...I read many articles that it is shipping with 13.10 release and i do see it when i check in the synaptic package manager (though it does not appear to be installed)...[/COLOR]

There is a lot of confusion about Mir. In one sense xmir is Mir, or at least it is part of Mir. Xmir replaces Xserver. At present we get xmir when we install unity-system-compositor. It is this that is in the repositories and it is this that will be default in the final release of 13.10.

From some experiments trying to load xmir on Ubuntu Gnome I came to the conclusion that Lightdm has been patched to load xmir or xserver. Whereas, gdm has not been patched in this way. Install lightdm on Ubuntu Gnome and then unity-system-compositor and xmir will load instead of xserver but continue to use gdm and xserver loads. Installing lightdm on Ubuntu Gnome will bring in Unity as an alternative desktop and the standard Ubuntu login screen instead of the Ubuntu Gnome login screen, as well.

I have also found out that Lightdm does more than manage the login screen. It is a display manager and it manages the xserver and now also the xmir server. This will be the situation on release of 13.10.

As for Mir as the display manager, and not just the xmir server, that will come with the release of 13.10. Mir will replace Xserver, Lightdm, and Compiz.

Regards.

---

### Post by su:bhatta on 2013-09-25
> **grahammechanical said:**
> @craig10x



There is a lot of confusion about Mir. In one sense xmir is Mir, or at least it is part of Mir. Xmir replaces Xserver. At present we get xmir when we install unity-system-compositor. It is this that is in the repositories and it is this that will be default in the final release of 13.10.

From some experiments trying to load xmir on Ubuntu Gnome I came to the conclusion that Lightdm has been patched to load xmir or xserver. Whereas, gdm has not been patched in this way. Install lightdm on Ubuntu Gnome and then unity-system-compositor and xmir will load instead of xserver but continue to use gdm and xserver loads. Installing lightdm on Ubuntu Gnome will bring in Unity as an alternative desktop and the standard Ubuntu login screen instead of the Ubuntu Gnome login screen, as well.

I have also found out that Lightdm does more than manage the login screen. It is a display manager and it manages the xserver and now also the xmir server. This will be the situation on release of 13.10.

As for Mir as the display manager, and not just the xmir server, that will come with the release of 13.10. Mir will replace Xserver, Lightdm, and Compiz.

Regards.

That was really informative ! I was in all confusion about this xmir business too. I think I read somewhere that the flavors are not coming with xmir in 13.10. 

I never checked what came with my Ubuntu Studio 13.10 alpha and kept updating it, still am (guess itz beta now). 
On top of the Ubuntu Studio I installed Gnome-desktop complete, with GDM and all. Whatever the servers the dependencies seem well resolved as there is no problem in my install. I am using UbuntuStudio with Gnome desktop exclusively now.

And, if I am not mistaken I read in your other post that anyways fglrx doesn't co-exist with xmir, and I have to use fglrx for my Radeon 6480 GPU.

---

### Post by grahammechanical on 2013-09-25
I like things to be specific and accurate. So, when someone's blog says that mir will be default in 13.10 I do not like it. Mir will be default in 14.10. This is just the way I am.

Yes, at the moment xmir will only work if we use open source video drivers. I last installed saucy salamander from the daily build of 15 September and the xmir code did not install by default. I had to install unity-system-compositor to get it. So, I am certain that your install of Ubuntu Studio 13.10 will not have the xmir code. If GDM is the display manager then it would only manage Xserver and not load xmir even if it was installed. I guess that Ubuntu Studio originally used lightdm like the other flavours because in the middle of July I installed Ubuntu Studio and was able to get it running on xmir. 

I feel that there has been a lot of unnecessary fuss over Ubuntu having xmir and certain flavours not having xmir. It is full Mir that is the great change. Mir will contain code to handle X applications and even Wayland applications. The decision to develop Mir has put a fire under the Wayland developers. They have gone from predicting that it would take years to develop MIr to racing to beat Mir to the desktop. Gnome.org has just announced that Gnome version 3.10 has some preliminary Wayland code. I think this is what is meant when people say that Ubuntu is disruptive. :)

Regards.

---

### Post by craig10x on 2013-09-26
Also...when is Unity 8 supposed to be the default in ubuntu? Is it 14.04 or 14.10?

---

### Post by e-Tiggy on 2013-09-26
14.10

---

### Post by craig10x on 2013-09-26
> **e-Tiggy said:**
> 14.10

Thanks :D

---

### Post by ventrical on 2013-09-26
> **grahammechanical said:**
> I like things to be specific and accurate. 



But as accurate as this is  (watch full) it doesn't help the situation.


[http://www.youtube.com/watch?v=Q1lSCI0bO_c](http://www.youtube.com/watch?v=Q1lSCI0bO_c)



> 
The decision to develop Mir has put a fire under the Wayland developers. They have gone from predicting that it would take years to develop MIr to racing to beat Mir to the desktop. Gnome.org has just announced that Gnome version 3.10 has some preliminary Wayland code. I think this is what is meant when people say that Ubuntu is disruptive. :)

Regards.

 ..and has caused division now and probably will proceed  with the rolling releases.. I have thought that this whole stink of a mess could of been handled more professionally on both sides of the isle, especially from  leaders and movers and shakers in the field - or , unless we all think that nVidia Corp  and Linus are going to forgive and forget? Who knows... but it makes  Ubuntu a hard sell to new users and also makes it appear clique.

   For the sake of the possible ensuing fallout I hedged my bets on Intel chipsets and graphics which seems to be transitioning smoothly through the whole heap of beans. 

Regards..

---

### Post by sammiev on 2013-09-26
Thanks for the link! :guitar:

---

