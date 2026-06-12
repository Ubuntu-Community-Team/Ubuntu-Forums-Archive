---
title: "IBM supports redhat, not linux"
date: 2006-12-05
forum: The Cafe
---

### Post by Circus-Killer on 2006-12-05
today i tried to download iseries access for linux from the ibm homepage. i got let down severely by the fact that they only had .rpm files. at the end of this year, i was hoping to switch my folks over to ubuntu, but they need to have iseries access which they currently run in windows.

as you can see, this is more a general rant than a question. my only question is (more of a rhetorical question), why create a linux version and then limit it to only a handful of rpm based distributions. anyways, this just goes to show that no big corporation can be trusted to keep linux users in mind.

guess my parents wont be switching, which is rather a pity, because i honestly think it woulda made their lives so much easier.

---

### Post by LostShootingStar on 2006-12-05
you could probably just use alien to convert the rpm to a deb...

---

### Post by Circus-Killer on 2006-12-05
didn't know that, will have to give it a try, but i still think a major player like ibm (especially one that is known to support linux) should have more than just .rpm's.

woulda thought they would have a plain binary installer or something, not just rpms. but thanks for the tip on alien, i will give it a bash when i get home this evening.

---

### Post by chaosgeisterchen on 2006-12-05
Don't they provide source packages for this application? If you can find it somewhere it would be no problem to build a *.deb out of it.

---

### Post by Circus-Killer on 2006-12-05
> **chaosgeisterchen said:**
> Don't they provide source packages for this application? If you can find it somewhere it would be no problem to build a *.deb out of it.
 
please read the first post. it states quite clearly that they only have RPM's. let me just re-iterate for you.....there are RPM's. no source code, just RPM's.
 
*Clip*

---

### Post by chaosgeisterchen on 2006-12-05
I misunderstood it, as I thought you would mean that they only have RPM **binary** packages. So it's a rather bad thing to see that, have you contacted IBM already to provide them a request for *.deb binary packages?

---

### Post by Circus-Killer on 2006-12-05
busy doing that now.....writing a nicely-worded lengthy letter explaining the problem......and i'll recommend that they make either .deb or a normal binary installer (such like enemy-territory has).

although, i'm sure .deb would be best for them, cos it will help with sorting dependency issues. still miffed that i have to email them, but what can you do. i woulda expected more from ibm.

---

### Post by rlozano on 2006-12-05
there is no doubt that big corporations like IBM, oracle, and the likes only support RPMs for their utilities and applications. this is because Red Hat was the first to go Enterprise and unfortunately using RPM. Red Hat have established its ground very well in the enterprise level. this is more a product of marketing than actual usage and feeling of the linux community. 

it is just sad to say that at this point in time, debian was quite lef-out in the enterprise level, considering it is the most stable linux engine. no private/commercial organization have really put a great focus on using debian in an enterprise class server, should there be, i would bet that packages will also be available to .deb.

for now, we all have to be contented to moving those RPMs to .deb using alien. but good developments are on their way already, as some major corporations have started looking into debian (ubuntu specifically), like Oracle, as they have recognized it's wide use in the end-user level.

just a note too... if i remember it correctlym IBM even released a P-series machine exclusively for Linux, and Red Hat Linux, that is. tsk, tsk, tsk... really a marketing hype product.

---

### Post by aysiu on 2006-12-05
I've had some experiences where *alien*ed RPMs have installed better than regular DEBs. Rare, but they've happened.

---

### Post by Circus-Killer on 2006-12-05
well, as i said, i will give alien a try when i get home this evening. i really hope it works out fine, cos my parents really should switch to linux.

i'm even going to buy my folks a new adsl modem for them just so they can change (its a kak usb one that has never been successfully used in linux (no, its not the alcatel one)).

oooo double brackets, gotta know i'm a programmer. anyways, as i was saying, i know my folks would love ubuntu, and would make my life easier. atm i'm the one who has to make sure the antivirus is up-to-date, same with XP, and keep the harddrive defragged. with ubuntu, all i have to show my folks is how to click the update button when it comes up.

anyways, i'll post back tonight (south african time UCT+2) with the results from aliening the rpm.

---

### Post by prizrak on 2006-12-05
RedHat is the main business distro so IBM supports it. I'm pretty sure that's their thinking. Also they are also most likely thinking that what works in one distro can be made to work in another (which is true).

---

### Post by Virogenesis on 2006-12-05
hate to say it but this isn't uncommon, its not only redhat rpm are used for but also novell, etc. 
Debian for some reason has never had the enterpise market like redhat and suse because of this IBM hasn't provided the packages but doesn't mean they are against linux, it just means they have common sense thats all.
I'd suggest you look at what IBM has done for linux before making such silly remarks because it is totally ungrateful. 
Be happy that there are atleast packages.

---

### Post by Circus-Killer on 2006-12-05
> **prizrak said:**
> RedHat is the main business distro so IBM supports it. I'm pretty sure that's their thinking. Also they are also most likely thinking that what works in one distro can be made to work in another (which is true).

you just proved my point RIGHT THERE. it can be made to work in another distro! so why dont they? so that they can keep you in the novell/redhat lock-in. woohoo! going from one lock-in os to another.

yes, i know i could try aliening it, which i will do. but i still feel that a company like ibm could spend the little extra time and effort to make a generic binary. its been done a hundred times, so it can be done. or hell, they could release rpms, debs, tgz, and whatever other package management system there is. but i find it convenient that the two distros that are supported are commercial for-money distros that probably give kick-backs to ibm. im just tired of companies saying they support linux and then just sit there riding the current wave trend without putting in a **decent** effort.

this is just my opinion. so dont flame me **again**. i just would like to see companies that claim to "support" linux to actually put in some actual effort. supporting linux is different to supporting only commercial OS's.

---

### Post by Brunellus on 2006-12-05
> **Virogenesis said:**
> hate to say it but this isn't uncommon, its not only redhat rpm are used for but also novell, etc. 
Debian for some reason has never had the enterpise market like redhat and suse because of this IBM hasn't provided the packages but doesn't mean they are against linux, it just means they have common sense thats all.
I'd suggest you look at what IBM has done for linux before making such silly remarks because it is totally ungrateful. 
Be happy that there are atleast packages.
...because debian doesn't care about competing in the enterprise market.  They care about making free software.

If that means not having a certain degree of support, so be it.  The Great Bearded Ones may be harsh, but they do have a certain degree of internal logical consistency.

---

### Post by StarsAndBars14 on 2006-12-05
> **Virogenesis said:**
> 
I'd suggest you look at what IBM has done for linux before making such silly remarks because it is totally ungrateful. 
Be happy that there are atleast packages.

I second that.

---

### Post by dbbolton on 2006-12-05
agreed

---

### Post by KiwiNZ on 2006-12-05
> **Circus-Killer said:**
> .
 
this is just my opinion. so dont flame me **again**. i just would like to see companies that claim to "support" linux to actually put in some actual effort. supporting linux is different to supporting only commercial OS's.
 
This seems a little harsh , I do not see any "Flames" here . Please keep this calm .
 
Thanks

---

### Post by prizrak on 2006-12-05
> **Circus-Killer said:**
> you just proved my point RIGHT THERE. it can be made to work in another distro! so why dont they? so that they can keep you in the novell/redhat lock-in. woohoo! going from one lock-in os to another.

yes, i know i could try aliening it, which i will do. but i still feel that a company like ibm could spend the little extra time and effort to make a generic binary. its been done a hundred times, so it can be done. or hell, they could release rpms, debs, tgz, and whatever other package management system there is. but i find it convenient that the two distros that are supported are commercial for-money distros that probably give kick-backs to ibm. im just tired of companies saying they support linux and then just sit there riding the current wave trend without putting in a **decent** effort.

this is just my opinion. so dont flame me **again**. i just would like to see companies that claim to "support" linux to actually put in some actual effort. supporting linux is different to supporting only commercial OS's.

When people asked Michael Dell why he doesn't support Linux his question was "I would love to, but what distro should I go with?" the response from the community was "It doesn't matter". IBM sells (well used to) servers with RedHat preloaded, SLED is another huge business distro that also happens to use RPM for their package management. As it is possible (and quite easy) for the community to use RPM's in a DPKG environment there is no need for extra packages. 

I really don't see a problem, so IBM didn't spend more time on it, it's not really their responsibility they provided a package that will work on a majority of business machines out there. 

Remember THERE IS NO VENDOR LOCK-IN IN LINUX. What works on Gentoo will work (perhaps with a bit of work) on Ubuntu and vice versa. 

P.S. The reasons RPM is the preferred standard for most business applications is because of RHEL's and SLED's dominance in the commercial market. Debian was always more along the lines of software for software's sake. I also believe that RPM is an older package management system.

---

### Post by Circus-Killer on 2006-12-05
> **KiwiNZ said:**
> This seems a little harsh , I do not see any "Flames" here . Please keep this calm .
 
Thanks

well, i got an infraction for calling someone stupid. and i dont appreciate being called silly or ungrateful. where do you draw the line? i was just giving my opinion, was uncalled for to call me silly and ungrateful...in the same sentence. luckily i have enough restrain to actually retaliate.

and please dont take this as a retaliation either, just curious on where you draw the line?

PS: now prizrak has given a decent response. this is the type of reply i was looking for. points of views without turning on eachother.

---

### Post by Circus-Killer on 2006-12-05
EDIT: sorry, messed up, double post

---

### Post by ComplexNumber on 2006-12-05
i don't see a problem. rpm is the format that is supported by the LSB. its in linux's best interest that all distros standardise on it.

---

### Post by crazedgremlin on 2006-12-05
so what does iSeries do??
I might have a use for it if I can keep track of people with it.

---

### Post by Circus-Killer on 2006-12-05
> **crazedgremlin said:**
> so what does iSeries do??
I might have a use for it if I can keep track of people with it.

if you dont know what it does then you most likely dont need it. and i dont see how tracking the people using it will help you decide if you need it. anyhow, to ease your curiosity, i mainly need it for its 5250 emulation.

---

### Post by crazedgremlin on 2006-12-05
> **Circus-Killer said:**
> if you dont know what it does then you most likely dont need it. and i dont see how tracking the people using it will help you decide if you need it. anyhow, to ease your curiosity, i mainly need it for its 5250 emulation.
ok misunderstanding... I'm not trying to keep track of people who use it, I was wondering if I could use it as a database to keep track of people I want to keep track of... kind of like a superpowerful address book. :)

---

### Post by Circus-Killer on 2006-12-05
> **crazedgremlin said:**
> ok misunderstanding... I'm not trying to keep track of people who use it, I was wondering if I could use it as a database to keep track of people I want to keep track of... kind of like a superpowerful address book. :)

hehe, oh okay. well, the answer would be no. its mainly for connecting to ibm servers along with emulation capabilities.

---

### Post by n8bounds on 2007-02-25
This one should actually work:

[http://ubuntuforums.org/showthread.php?t=368894](http://ubuntuforums.org/showthread.php?t=368894)

---

### Post by koenn on 2007-02-27
> his is just my opinion. so dont flame me again. i just would like to see companies that claim to "support" linux to actually put in some actual effort. supporting linux is different to supporting only commercial OS's.

[http://www.google.com/search?hl=en&q=IBM+Linux](http://www.google.com/search?hl=en&q=IBM+Linux)
[http://www-03.ibm.com/linux/](http://www-03.ibm.com/linux/)
[http://www-03.ibm.com/systems/browse/linux/](http://www-03.ibm.com/systems/browse/linux/)
And in the process, they've had **their ** employees write contributions /patches /enhancements to *Linux* and other open source software :[http://www-128.ibm.com/developerworks/linux/ltc/](http://www-128.ibm.com/developerworks/linux/ltc/) 

so, yeah, they didn't make that 1 .deb you were looking for.

---

