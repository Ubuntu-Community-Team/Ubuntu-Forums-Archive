---
title: "foresight linux"
date: 2005-03-12
forum: The Cafe
---

### Post by ubuntu_demon on 2005-03-12
Hi,

There's a new distro that also features gnome 2.10.Seems like a distro with a goal to feature new technologies.  Like :


    *  Beagle :: Search tool that ransacks your personal information space to find whatever you're looking for.
    * f-spot :: Personal photo management.
    * Howl :: Cross-platform implementation of Zeroconf networking
    * Hal :: Hardware abstraction layer that makes hardware just work.
    * Conary :: A new way of looking at package management.
    * Oversite :: Web based systems management.
    * GNOME-Office :: Suite of Productivity Applications
    * Mono :: .NET implementation for Linux


[http://foresightlinux.com/](http://foresightlinux.com/)

So I think technologies like these should be in grumpy. We should want people who want to test new technologies trying Ubuntu. That would be nice.

---

### Post by tanari on 2005-03-12
Has anyone some screenshots?

>  * Conary :: A new way of looking at package management.
Is it alternative to RPM and DEB? Easy to use?

---

### Post by bored2k on 2005-03-12
[QUOTE=tanari]Has anyone some screenshots?


Is it alternative to RPM and DEB? Easy to use?[/QUOTE]
 Yeah what it is based on, why I cant find it anywhere on the site .

---

### Post by bored2k on 2005-03-12
> Conary is a distributed software management system for Linux distributions. It replaces traditional package management solutions (such as RPM and dpkg) with one designed to enable loose collaboration across the Internet. It enables sets of distributed and loosely connected repositories to define the components which are installed on a Linux system. Rather then having a full distribution come from a single vendor, it allows administrators and developers to branch a distribution, keeping the pieces which fit their environment while grabbing components from other repositories across the Internet.
Checking for out of date packages

There is a handy utility called "yuck" which compares your versions of packages to those available from the repository." Yuck can also update those packages (requires root), the default behavior is to simply display.

	  foresight$ yuck
	  
Does .deb/Debian do this already ?

---

### Post by tim1 on 2005-03-12
[QUOTE=bored2k]Yeah what it is based on, why I cant find it anywhere on the site .[/QUOTE]

There are lots of links and docs for conary. Did you actually visit the website? Click on Documentation, click on distro -> conary, click on conary right on the frontpage!

Maybe you should read the firefox documentation first   :-| 

greets, tim

---

### Post by bored2k on 2005-03-12
[QUOTE=tim1]There are lots of links and docs for conary. Did you actually visit the website? Click on Documentation, click on distro -> conary, click on conary right on the frontpage!

Maybe you should read the firefox documentation first   :-| 

greets, tim[/QUOTE]
 *lol* . I just quickly looked at it lol. I was hoping it said RPM or DEB in big 48 size bold verdana. Silly me :-P

---

### Post by machiner on 2005-03-12
I'm installing it today.

---

### Post by bored2k on 2005-03-12
[QUOTE=machiner]I'm installing it today.[/QUOTE]
 Let us know how it is / Package availability / etc / Dual Booting

---

### Post by TravisNewman on 2005-03-12
I might give it a shot tomorrow myself.

Give us some updates about how it goes!

---

### Post by machiner on 2005-03-12
Well -- I didn't get very far.

I have a spare drive, so I always use that when testing things out...no dual boots. If I like the OS then I'll consider installing in on my main architecture and dual boot.

It took > 1 hour to install (everything) and they warn you right away that the OS is not finished.

It uses the Anaconda installer and it's a no brainer (but I think it's a dog). It did not ask me to create a user, I had to log in as root and make one that way.

There was en error upon booting into the OS the first time: Error opening security policy. There was another one right after that but it was fast and I didn't catch it. I didn't do dmsg ( I always forget that syntax - that't the one, right - to get a readout of the boot messages ?).

When I booted it was a nice simple desktop - Gnome 2.10 and BEAGLE!!! Woohoo!

Gotta tell ya - that's the only reason I installed this puppy. 

It's optomized for 686 and seemed pretty responsive. Although I noticed Abiword and Gnumeric took longer to start than on my Ubuntu (linux-k7) install. It was not any more responsive than my Ubuntu setup, really - but I didn't put it through too many paces.

THe distro does not come with openoffice (good!). Installed were Epiphany and Firefox for browsers and Mozilla mail and Evolution for email. Abiword, Gnumeric, a blog poster and some other esoteric apps that I've never heard of.  I don't do instant messaging so I didn't notice any of those apps.

I gave up pretty quickly because networking wouldn't go...it saw all my hardware, which I expect of any distro. It uses the same networking config that fedora uses (it's a Gnome thing I think) so it's a piece of cake to add a DSL setup. 
I still like opening a terminal and typing sudo pppoeconfig better, though - but that's just me.  In order to start DSL I had to activate one of my NIC cards.

This is, of course, no problem, but when either NIC failed and I checked the syslogs I saw an error that the network was down.  I didn't believe it, and sure enough after I shut down and plugged my regular hdd in and booted in Ubuntu I was online.  So, the NETWORK IS DOWN error was erroneous.

I was unable to check the Conary Package Manager because of networking woes. I really wanted to see it in action.

Aside from my point of failure and the errors upon boot it ran pretty well - responsive, but no faster than my Ubuntu install.  Except for one standout - it comes with Gnomebaker and that started almost instantly. I didn't burn any discs.

I plan to boot back into it tomorrow and get networking going then I'll spend some time in the distro -- this synopsis of my first exposure really doesn't do the OS justice.

I keep calling it an OS -- I should call it a distro, ey?

The name kills me - Foresight. I keep wanting to call it Foreskin.

---

### Post by TravisNewman on 2005-03-12
[QUOTE=machiner]

The name kills me - Foresight. I keep wanting to call it Foreskin.[/QUOTE]

First time I saw the thread I thought it said Foreskin, and ever since, I STILL think I'm seeing the word "foreskin," I'm just glad I'm not the only one ;)

---

### Post by bored2k on 2005-03-12
[QUOTE=machiner]Well -- I didn't get very far.

I have a spare drive, so I always use that when testing things out...no dual boots. If I like the OS then I'll consider installing in on my main architecture and dual boot.

It took > 1 hour to install (everything) and they warn you right away that the OS is not finished.

It uses the Anaconda installer and it's a no brainer (but I think it's a dog). It did not ask me to create a user, I had to log in as root and make one that way.

There was en error upon booting into the OS the first time: Error opening security policy. There was another one right after that but it was fast and I didn't catch it. I didn't do dmsg ( I always forget that syntax - that't the one, right - to get a readout of the boot messages ?).

When I booted it was a nice simple desktop - Gnome 2.10 and BEAGLE!!! Woohoo!

Gotta tell ya - that's the only reason I installed this puppy. 

It's optomized for 686 and seemed pretty responsive. Although I noticed Abiword and Gnumeric took longer to start than on my Ubuntu (linux-k7) install. It was not any more responsive than my Ubuntu setup, really - but I didn't put it through too many paces.

THe distro does not come with openoffice (good!). Installed were Epiphany and Firefox for browsers and Mozilla mail and Evolution for email. Abiword, Gnumeric, a blog poster and some other esoteric apps that I've never heard of.  I don't do instant messaging so I didn't notice any of those apps.

I gave up pretty quickly because networking wouldn't go...it saw all my hardware, which I expect of any distro. It uses the same networking config that fedora uses (it's a Gnome thing I think) so it's a piece of cake to add a DSL setup. 
I still like opening a terminal and typing sudo pppoeconfig better, though - but that's just me.  In order to start DSL I had to activate one of my NIC cards.

This is, of course, no problem, but when either NIC failed and I checked the syslogs I saw an error that the network was down.  I didn't believe it, and sure enough after I shut down and plugged my regular hdd in and booted in Ubuntu I was online.  So, the NETWORK IS DOWN error was erroneous.

I was unable to check the Conary Package Manager because of networking woes. I really wanted to see it in action.

Aside from my point of failure and the errors upon boot it ran pretty well - responsive, but no faster than my Ubuntu install.  Except for one standout - it comes with Gnomebaker and that started almost instantly. I didn't burn any discs.

I plan to boot back into it tomorrow and get networking going then I'll spend some time in the distro -- this synopsis of my first exposure really doesn't do the OS justice.

I keep calling it an OS -- I should call it a distro, ey?

The name kills me - Foresight. I keep wanting to call it Foreskin.[/QUOTE]
 By that review I think i'll give it some cooking time.

---

### Post by machiner on 2005-03-12
[QUOTE=panickedthumb]First time I saw the thread I thought it said Foreskin, and ever since, I STILL think I'm seeing the word "foreskin," I'm just glad I'm not the only one ;)[/QUOTE]


LOL - yeah, me too.

---

### Post by TravisNewman on 2005-03-12
>   By that review I think i'll give it some cooking time.

not discrediting machiner in the least, he's one of the most well-informed contributors to the forum as far as I can see (not to mention the wonderful topics about cookies and witch-doctor school excuses and toaster ovens that we enjoy so much), but you should never assume that one person's experience is going to mirror your own. Lots of people have posted here and elsewhere that Ubuntu needs more cooking time because they couldn't get it installed, etc, etc. 
So it's STILL worth a shot. If you decide to try it, take machiner's experience as something to look out for, but you may have NO issues whatsoever. That's one of the bad things about GNU/Linux-- sometimes there's odd inconsistencies.

---

### Post by bored2k on 2005-03-12
[QUOTE=panickedthumb]not discrediting machiner in the least, he's one of the most well-informed contributors to the forum as far as I can see (not to mention the wonderful topics about cookies and witch-doctor school excuses and toaster ovens that we enjoy so much), but you should never assume that one person's experience is going to mirror your own. Lots of people have posted here and elsewhere that Ubuntu needs more cooking time because they couldn't get it installed, etc, etc. 
So it's STILL worth a shot. If you decide to try it, take machiner's experience as something to look out for, but you may have NO issues whatsoever. That's one of the bad things about GNU/Linux-- sometimes there's odd inconsistencies.[/QUOTE]
 Yes but I still need to know how is Dual Booting and little stuff like that working. Since I'm not the only one working on this PC, I have to keep it in good conditions all the time. When Yoper came out I rushed and installed it, and it killed my brother's XP. Later I read on its forums "its great, but dont dual boot on it yet ! ".

I'm no developer/tester so i'll probably wait some more reviews.

And btw , that toaster story was pretty sad !

---

### Post by TravisNewman on 2005-03-12
[QUOTE=bored2k]Yes but I still need to know how is Dual Booting and little stuff like that working. Since I'm not the only one working on this PC, I have to keep it in good conditions all the time. When Yoper came out I rushed and installed it, and it killed my brother's XP. Later I read on its forums "its great, but dont dual boot on it yet ! ".

I'm no developer/tester so i'll probably wait some more reviews.

And btw , that toaster story was pretty sad ![/QUOTE]
 Good point!

yeah, if you have to keep it in running order for other people using it, experimental software should NOT go on the pc.

It reminds me of a Zits cartoon from a while back (I think it was Zits)

[color=DarkSlateGray] Mom, I want to install Linux on our computer.[/color]
[color=Navy] Oh no, I don't think that would a good idea.[/color]
[color=DarkSlateGray] But I can put it on another partition and you'd never even notice it![/color]
[color=Navy] How could you not notice it?!? Open sores!![/color]
[color=DarkSlateGray] Source, Mom. Open SOURCE.[/color]

---

### Post by ubuntu_demon on 2005-03-13
[QUOTE=bored2k]Yes but I still need to know how is Dual Booting and little stuff like that working. Since I'm not the only one working on this PC, I have to keep it in good conditions all the time. When Yoper came out I rushed and installed it, and it killed my brother's XP. Later I read on its forums "its great, but dont dual boot on it yet ! ".

I'm no developer/tester so i'll probably wait some more reviews.

And btw , that toaster story was pretty sad ![/QUOTE]
 good point. I think I'll wait with trying it till someone has tried a dual boot install and has faith in it.

---

### Post by Lovechild on 2005-03-13
great, now everytime I see my.. member.. I think of Linux because of the forskin comment.

---

### Post by TravisNewman on 2005-03-13
Uhhh... I think you need to spend some time away from your computer. 

The day I look at my naughty bits and think of Linux is the day I dismantle my PC and bury the parts  of it miles away from each other.

---

### Post by totalshredder on 2005-03-14
[http://www.capnkirby.com/Foresight.html](http://www.capnkirby.com/Foresight.html)

A nice short review of this distro; Found it on distrowatch, it just got added to their list thing :)

Luke

---

### Post by TravisNewman on 2005-03-14
Rock on, not only is he a Linux geek, he's a fan of the greatest band the world has ever seen. I like the cap'n

---

### Post by Xian on 2005-03-14
I installed Foresight today and there were a few missing pieces, however it was certainly a nice addition to the Specifix project. There are less than 100 source packages are different. Just keep in mind that it is being built upon a distro that is still in the alpha stage. Definitely not for stable minded persons.

---

### Post by kassetra on 2005-03-14
[QUOTE=Xian]I installed Foresight today and there were a few missing pieces, Definitely not for stable minded persons.[/QUOTE]

WAHAHAHAHAHAHA
I'm sorry but that is what stuck out as I was reading this post.

I just have to learn to read slower.

---

