---
title: "Always surprising."
date: 2021-04-11
forum: Ubuntu, Linux and OS Chat
---

### Post by hagrid3 on 2021-04-11
Things that have been called "paper cuts", ranging from annoying to infuriating.

Over the recent several years of being a full time U/M user - after part time uses of various distros since ~2006, I have helped other folks to make their transitions to it, and have run across some things which have been referred to as "paper cuts" by other forum members.

_Some are merely minor annoyances, vs. others which can be important enough as to be infuriating, like this one:_
For LAN users who share uses of files stored centrally on a single PC, the most common methods are just nasty to get working correctly.
A truly simple method of making persistently mounted shared resources still (AFAIK...) has not come around.
(I was fortunate to find a workable solution via SSHFS - but this need should have a dead easy tool to cover it by now.)

_Here is the other end of the scale:_
Excessive numbers of utterly useless fonts - but no really great tool to just wipe 'em out !!
Digging around availed me of some CLI methods to get rid of some of them, but truly there's still like 100 left and I am NOT deleting all of those 1 by 1.

_Here is a sort of middling annoyance..._[SIZE=3]_[FONT=arial]Email Notifications:[/FONT]_
[SIZE=2]The OS's own notifier is visible - but it don't do nuffin a'tall.
And audible notifications work rather oddly no matter how they get configured in Thunderbird.
This may seem trivial at 1st glance - but when one does NOT spend every waking minute in front of the screen, having an alert that is [SIZE=2]audible [/SIZE]in the next room, as well as a lingering visual [SIZE=3][SIZE=2]notification that remains up while one is away are very helpful things.
[/SIZE][/SIZE][/SIZE][/SIZE](I finally got Mailbox Alert to make enough of a nuisance of itself that it can catch my attention in the next room - which is good enough, but the useless system notifier remains present.)[FONT=arial][SIZE=2]

_Trying to use an Android phone as webcam has been a totally wasted effort under 18.04._
No matter what I found or tried I've never gotten past this error:
[/SIZE][/FONT]*"FATAL: Module v4l2loopback not found in directory /lib/modules/5.4.6-050406-generic"*
All the directions I could find were 100% useless for my system & I finally had to buy a webcam when they got back into stock.
That simply connected & worked - but the deays in getting one were significant.

_[FONT=arial][SIZE=2]Gnome-disks does very odd things after running GParted.[/SIZE][/FONT]_
My PC has a 500GB HDD with a large space unallocated & the only primary partition is /boot, its other partitions are extended.

When I open gnome-disks at 1st it shows all my partitions correctly, but=>
If I want to check for something via GParted, after opening & then closing it, then re-opening gnome-disks ONLY shows the single primary partition & it has no way to make it re-scan or refresh the view.

That is baffling to me, so I've tried partprobe with & without the -s, and it had no visible effect on gnome-disks.
This behaviour is **VERY** annoying, but can be corrected by re-booting...which seems excessive to me.
Others have also gotten this to happen regularly - but it has not been fixed at all AFAIK.

_The last goofy thing that comes to mind is regarding the Geeqie image viewer, which I happen to like._
So I installed it easily enough, but...
Anytime I use apt, it pokes me to do an autoremove for several things - and the 1st time that this happened after intentionally installing Geeqie, I missed that it was on that list - and it got removed - so I just reinstalled it - but I do not know how I may exclude it from that dialogue, so I've not used autoremove since that 1st happened.

Very soon I'll be allowing my main PC to do the upgrading from 18.04 to 20.04, and maybe some of these paper cuts have been fixed by now.

Having done several upgrades for other folks previously I was delighted to see that some of the wifi ills have been fixed, but in place of those there are now some very strange USB problems instead.

There have been other oddities involving printers & their connections, notebook video errors, file permission snafus that should not have ocured at all, and so on - but those I've listed above are the most worthy of mention IMO & it will be great if they can ever be fixed !!

Thanks for reading all that.

---

### Post by QIII on 2021-04-11
Moved to ***Ubuntu, Linux and OS Chat***

A list of annoyances/complaints is not a help request.

---

### Post by hagrid3 on 2021-04-12
OK, thanks for that assistance.
I had been tempted to post here originally - but was uncertain, so did otherwise.

---

### Post by grahammechanical on 2021-04-12
To be balanced, could you now give a list of 6 things that please you about Ubuntu?

The things that frustrate you do not bother me. No mobile phone. No LAN. 

The number of fonts does not trouble me. In fact I find it quite useful. I like how we can install different language keyboard layouts and easily switch between different languages. Not that I am multi-lingual at all. But it is useful for someone who likes to write in different languages and does not want to go searching for fonts. Earlier today I was downloading the Greek text of some books of the Bible. There was no need to install a Greek font. Great.

Autoremove deletes unnecessary packages and Software Updater runs it as part of the update/upgrade process. Whereas, in the terminal we have to specifically call the autoremove command.

I have never had a problem with WiFi drivers. I have used GParted several times as I install/delete/move partitions so as to install different Linux distributions. I have never noticed anything strange happening to Disks utility. Mind you I never run GParted from an installed version of Ubuntu but only from a live session. So, I always reboot into installed Ubuntu and I guess that process allows the OS to understand the reconfigured hard drive.

In the 14 years I have been using Ubuntu there have been many things that have caused frustration. It is often due to my ignorance and inability to understand difficult concepts. I have learned to just give up the struggle and content myself with doing something else that I can be good at. On the other side of the balance sheet I have gained some skills in Linux/ubuntu.

Regards

---

### Post by hagrid3 on 2021-04-12
In 'A Course in Miracles' such disdainful activity is described as this:
'Forgiveness to destroy'.

Discrediting another's observations and desires is actually rather hostile - and since I require none of that in this life, it is best left to others.

---

### Post by QIII on 2021-04-12
Original content of opening post restored.

Please do not delete the content of posts.  We consider that to be Forum vandalism.

Nobody put down your observations.  Another user made observations.

However, to keep others from doing the same, this thread is closed.

---

