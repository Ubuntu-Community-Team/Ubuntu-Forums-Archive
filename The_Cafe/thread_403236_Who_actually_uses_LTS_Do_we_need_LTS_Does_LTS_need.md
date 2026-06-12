---
title: "Who actually uses LTS? Do we need LTS? Does LTS need updates?"
date: 2007-04-06
forum: The Cafe
---

### Post by r3m0t on 2007-04-06
Please move this thread as appropriate. (Mods.)

Note: I'm only talking about desktops in this whole post.

Who uses LTS? Please vote in the poll. If your business uses a certain version, pick that version. Otherwise, if you're using more than one version, pick the oldest.

It's a nice idea, but hardware support is constantly improving on Linux. The old Dapper isn't getting the new printer drivers, wireless drivers and whatever else is going on. (Is it?) An LTS release is meant to last 36 months. A lot can change in those 36 months in the world of hardware support. Surely it will soon become more useful to use the latest version of Ubuntu, even if it isn't LTS? Then, the LTS version will no longer be particularly useful. Also, I would worry if the Canonical website is recommending the outdated LTS version as a first download. If somebody got a new laptop, that's quite a few hours they could waste trying the old LTS before moving on to the latest version. Of course, they might just give up.

Also, isn't simultaneous support of 3 releases rather taxing on developers?

Maybe I have misunderstood LTS. :)

---

### Post by 23meg on 2007-04-06
> An LTS release is meant to last 36 months. A lot can change in those 36 months in the world of hardware support .Surely it will soon become more useful to use the latest version of Ubuntu, even if it isn't LTS? 

The LTS releases are largely meant for use cases where there won't be hardware changes in that 36 months. If a certain hardware configuration works with a not-very-up-to-date kernel version *today*, it will also work 36 months later.

---

### Post by maxamillion on 2007-04-06
Edgy is the oldest I have running on a desktop machine, I also have Feisty running for testing purposes but I use dapper on servers and yes, it needs updates and possibly some bug attention ... there has been an issue with libapache2-mod-python on AMD64 since it released and nothing has been done about it. I actually completely swore of ubuntu on servers as of late and went back to debian which I switched away from because of the appeal for newer packages but I can't tolerate Ubuntu's instabilities for production level servers handling thousands of requests at any given moment of the day. Don't get my wrong, I love Ubuntu to death ... but I see it as a desktop distro and nothing more.....

that's my opinion, take it for what its worth..... or don't :)

EDIT: I do still run dapper on testing servers because its quick and easy to get up and running from a blank hard drive, but not production level ..... just for clarification (I re-read my post and it wasn't very clear)

---

### Post by picpak on 2007-04-06
It's made for people like my mom who have no intention of updating their hardware or upgrading every 6 months; they just want something that works.

---

### Post by macogw on 2007-04-06
I use Feisty on my computer.  I was going to have my mom use LTS, but when I put Beryl on my comp, I knew that as soon as my siblings saw it, they'd want it too, so I upgraded her computer to Edgy and installed Beryl when I visited her at Christmastime.

---

### Post by r3m0t on 2007-04-06
> **picpak said:**
> It's made for people like my mom who have no intention of updating their hardware or upgrading every 6 months; they just want something that works.

Yes, but are people using it? Are those "computer-casual" people using Ubuntu at all? ;-)

---

### Post by picpak on 2007-04-06
> **r3m0t said:**
> Yes, but are people using it? Are those "computer-casual" people using Ubuntu at all? ;-)

If you go throughout this forum, you can still see a couple Dapper users.

---

### Post by maxamillion on 2007-04-06
> **r3m0t said:**
> Yes, but are people using it? Are those "computer-casual" people using Ubuntu at all? ;-)

Well ... that's kinda the goal of the Ubuntu project, so yes ... we hope those computer casual people are using it or are atleast able to use it without problems.

---

### Post by r3m0t on 2007-04-06
> **maxamillion said:**
> I actually completely swore of ubuntu on servers as of late and went back to debian which I switched away from because of the appeal for newer packages but I can't tolerate Ubuntu's instabilities for production level servers handling thousands of requests at any given moment of the day. Don't get my wrong, I love Ubuntu to death ... but I see it as a desktop distro and nothing more.....

that's my opinion, take it for what its worth..... or don't :)

I agree - I don't really see why Ubuntu is targeting the server market. Seems silly, because there are only about 10 salaried people (right?) and the server market has already been penetrated with a strong whiff of freedom. (Actually it's been a permanent presence...)

---

### Post by maxamillion on 2007-04-06
> **r3m0t said:**
> I agree - I don't really see why Ubuntu is targeting the server market. Seems silly, because there are only about 10 salaried people (right?) and the server market has already been penetrated with a strong whiff of freedom. (Actually it's been a permanent presence...)

I do understand why they are because in the instance you have deployed an entire Ubuntu network you would probably want a local apt mirror for package updates across your network so you can then run an update script in the cron of each machine and it will update and upgrade against your local server and only sap bandwidth from the lan. I'm sure there are other examples of why you would **really** want an Ubuntu server, but that is just the first that came to mind.

---

### Post by r3m0t on 2007-04-06
> **maxamillion said:**
> I do understand why they are because in the instance you have deployed an entire Ubuntu network you would probably want a local apt mirror for package updates across your network so you can then run an update script in the cron of each machine and it will update and upgrade against your local server and only sap bandwidth from the lan. I'm sure there are other examples of why you would **really** want an Ubuntu server, but that is just the first that came to mind.

Actually, to run apt-mirror you don't even need Debian. Unless you mean that the network admin will individually approve updates from the Ubuntu repository, and maybe make a new meta-package to deal with adding new packages?

---

### Post by etotehpii on 2007-04-06
Dapper is fine for the moment.  I just built a computer last August and have everything working great under Dapper.  I'm a college student and don't have a lot of time to fix things like a broken system from upgrading.  However, I'm planning on upgrading to Fiesty this summer and perhaps play with a few other distros with my free time.

When I do go from Dapper to Fiesty:

Should I go Dapper to Edgy to Fiesty or should I just go straight to Fiesty in terms of upgrading my system?

---

### Post by 23meg on 2007-04-06
> Should I go Dapper to Edgy to Fiesty or should I just go straight to Fiesty in terms of upgrading my system?Skipping versions isn't supported and will most likely be troublesome.

---

### Post by whitefort on 2007-04-06
> **r3m0t said:**
> Yes, but are people using it? Are those "computer-casual" people using Ubuntu at all? ;-)

Well, I think I fall into that category, and I'm using Dapper.  Personally I HATE the idea of having to reinstall all my stuff every 6 months or so.  It was a real nightmare getting it all to work in the first place - modem, printer, wireless  - almost nothing seemed to work 'out of the box' on my system.  It all required lots of messing about and help from people in this forum.  I'm not really looking forward to going through all that again.

Then there's all the extra drivers and codecs and stuff that had to be separately installed.  And I've got my wallpaper, sounds, and lots of other little things set up just the way I like it.

So personlly I'm happy to stick with Dapper for as long as possible.  Though I admit II DO miss being able to get the latest versions of software from the repository (OpenOffice, Blender, etc).  I assumed that this would be included in the 'Long Term Support,' and not just security fixes.  This is the one thing that might tempt me to try more up-to-date versions.

---

### Post by IYY on 2007-04-06
I still have Breezy on one old machine. It works, and is only used to browse the internet, so there's really no point of upgrading.

---

### Post by r3m0t on 2007-04-06
> **whitefort said:**
> Well, I think I fall into that category, and I'm using Dapper.  Personally I HATE the idea of having to reinstall all my stuff every 6 months or so.  It was a real nightmare getting it all to work in the first place - modem, printer, wireless  - almost nothing seemed to work 'out of the box' on my system.  It all required lots of messing about and help from people in this forum.  I'm not really looking forward to going through all that again.

Then there's all the extra drivers and codecs and stuff that had to be separately installed.  And I've got my wallpaper, sounds, and lots of other little things set up just the way I like it.

So personlly I'm happy to stick with Dapper for as long as possible.  Though I admit II DO miss being able to get the latest versions of software from the repository (OpenOffice, Blender, etc).  I assumed that this would be included in the 'Long Term Support,' and not just security fixes.  This is the one thing that might tempt me to try more up-to-date versions.

If you run an upgrade, your documents and your settings will be kept. If you do a new install, it's quite likely that more of your hardware will work "out-of-the-box" - but you might have a few sticking points.

However, apparently the Dapper -> Edgy upgrade caused a lot of people a lot of problems. I remember at the time that people were downplaying the problem a lot - "after all, Edgy is a cutting-edge distribution and Dapper should be enough for people at the moment". :lol: Now, people who want to upgrade to Feisty have to go through Edgy - and the upgrade process is still unreliable!

There's another matter - how can people upgrade an LTS release? The next LTS release looks to me like it could be about 9.04. Will people need to go 6.06(.1) -> 6.10 -> 7.04 -> 7.10 -> 8.04 -> 8.10 -> 9.04?? That's six reboots, and Ubuntu is the new Windows! :lol: 

That would be difficult - Gnome 2.14 -> 2.26 (or so), Firefox 1.5 -> 3 at least, Xorg 7.0 -> 7.3 or so, OO 2.0 -> 2.3 or so, and kernel 2.6.15 -> 2.6.30 (although kernel releases are erratic).

On the other hand, maybe LTS releases can be more often than every 3 years. In that case, the developers would have to track *more* than three versions of Ubuntu at a time - ouch!

---

### Post by Compucore on 2007-04-06
I think personally THe LTS thing is beneficial on the server end of things here. Mainly that once you get a server set up once with the latest patches att he time of its release. It should be good for 36 months. It is not like your going to go into your server room each and every time for a small update that does come out for it. On my home computers that I have which have ubuntu installed on them. It is not that bad. But whe its mission critical  server. I do not think the big bosses wuld be happy when they ask why the mission ciritcal serv running ubuntu went down. and back up for every little update that comes out. During the LTS. 

Compucore

---

### Post by mephisto786 on 2007-04-06
The closest analogy at the moment to the debian world, is that dapper is like running sarge.....it will get dated, but security is kept updated, it is (at least on this laptop) quite stable, and has 18000 plus tools at your disposal to get things done on.  I found it the perfect solution on a laptop where I had to work while traveling, without worrying about the latest bugs hosing my system,  or glitches in the very latest version of Open Office mucking up my deadlines.

 Edgy , as the name was meant to imply is full of more testing software, the latest  and (sometimes) greatest.  Like Debian testing, it generally provides a good stable environment as well.   But if you dont need the latest, and have all the tools you need already, the fact that dapper was a LTS release takes away the headache of a 'must do ' update and/ or r einstall and the resetup of your system.  Ive done enough upgrades on enought systems to know they are always hazardous.

 Then theres the Unstable .......Feisty.  Great to see whats coming up and to help bug hunt.  There are many types of users and quite a few don't need to update just because something is new. Or just released.   Matt Welsh's philosophy of upgrading rings true to alot of us.......dont upgrade unless there is something you need.

The smartest move Ubuntu has made was the LTS editions for people who wont to work with their computer, not ON their computer.   Constantly clamoring after upgrades is usually the domain of devs, techies and hobbyists.   Of course for devs and tech folk, upgrading is part of their job........but after the first few years swapping distros as the latest flash in the pan was released, or the most bleeding edge apps hit the bandwidth, you start to rely on what works, tweak that to the max and only upgrade what you really need.  

Were Ubuntu thinking of dropping LTS, or their releases spread out even longer than debians stable release cycle ,  theres always debian.

Dappers LTS has secured this distro in a place with some of the standards like slackware and debian by allowing users who want to use ubuntu but want rock stable as well.  You ll notice that soon after Suse went Open Suse, they became a bleeding edge test ground and the once famous easy to use Suse became a nightmare of pkg management,  etc.  Heres hoping theres another LTS to try in the ooming year to fill the gap between newer machines and updates that will not fit into dappers foundations. Stable isnt only for servers anymore   :-P

cheers

---

### Post by 23meg on 2007-04-06
[QUOTE=r3m0t]There's another matter - how can people upgrade an LTS release? The next LTS release looks to me like it could be about 9.04. Will people need to go 6.06(.1) -> 6.10 -> 7.04 -> 7.10 -> 8.04 -> 8.10 -> 9.04?? That's six reboots, and Ubuntu is the new Windows!

That would be difficult - Gnome 2.14 -> 2.26 (or so), Firefox 1.5 -> 3 at least, Xorg 7.0 -> 7.3 or so, OO 2.0 -> 2.3 or so, and kernel 2.6.15 -> 2.6.30 (although kernel releases are erratic).[/QUOTE]

No, direct upgrades from one LTS release to the next are supported. There wouldn't be much point to LTS releases otherwise.

> On the other hand, maybe LTS releases can be more often than every 3 years. In that case, the developers would have to track more than three versions of Ubuntu at a time - ouch!

There's no exact schedule for LTS releases; they don't necessarily come every three years.

---

### Post by JAPrufrock on 2007-04-06
> The smartest move Ubuntu has made was the LTS editions for people who wont to work with their computer, not ON their computer.

I run Dapper on my main machine because it's dependable.  As the adage goes, "If it ain't broke, don't fix it."

---

### Post by macogw on 2007-04-06
> **r3m0t said:**
> If you run an upgrade, your documents and your settings will be kept. If you do a new install, it's quite likely that more of your hardware will work "out-of-the-box" - but you might have a few sticking points.

However, apparently the Dapper -> Edgy upgrade caused a lot of people a lot of problems. I remember at the time that people were downplaying the problem a lot - "after all, Edgy is a cutting-edge distribution and Dapper should be enough for people at the moment". :lol: Now, people who want to upgrade to Feisty have to go through Edgy - and the upgrade process is still unreliable!

There's another matter - how can people upgrade an LTS release? The next LTS release looks to me like it could be about 9.04. Will people need to go 6.06(.1) -> 6.10 -> 7.04 -> 7.10 -> 8.04 -> 8.10 -> 9.04?? That's six reboots, and Ubuntu is the new Windows! :lol: 

That would be difficult - Gnome 2.14 -> 2.26 (or so), Firefox 1.5 -> 3 at least, Xorg 7.0 -> 7.3 or so, OO 2.0 -> 2.3 or so, and kernel 2.6.15 -> 2.6.30 (although kernel releases are erratic).

On the other hand, maybe LTS releases can be more often than every 3 years. In that case, the developers would have to track *more* than three versions of Ubuntu at a time - ouch!
The Dapper > Edgy upgrade was painful for people (like me, 12 hours to fix it) who did it the Debian way: edit sources.list and run dist-upgrade.  If you use gksu "update-manager -c" it works perfectly (yes I tested this) because it uses more safety checks.

I've been hearing 8.04 is the next LTS so there's a year in which to migrate.  I assume there will be a special LTS -> LTS updater.

---

### Post by Adamant1988 on 2007-04-06
the LTS is for anyone who *needs* a stable environment that's going to work. For users like you and I who are always wanting the latest features Ubuntu LTS releases won't be worth much to us, unless they're fresh.  

So.. 
For more experienced casual users: Latest release will probably be best
For the enterprise or desktop users who just want stability: LTS releases will be best.

---

### Post by macogw on 2007-04-06
> **Compucore said:**
> I think personally THe LTS thing is beneficial on the server end of things here. Mainly that once you get a server set up once with the latest patches att he time of its release. It should be good for 36 months. It is not like your going to go into your server room each and every time for a small update that does come out for it. On my home computers that I have which have ubuntu installed on them. It is not that bad. But whe its mission critical  server. I do not think the big bosses wuld be happy when they ask why the mission ciritcal serv running ubuntu went down. and back up for every little update that comes out. During the LTS. 

Compucore

Even if there were updates on the server, why go to the server?  SSH into it from the comfort of your couch.

---

### Post by FuturePilot on 2007-04-06
I use Dapper on the main desktop PC mainly for it's stability. For the most part it's been rock solid stable. But I'm planning on updating to Feisty once it is released. The software in Dapper is really starting to get old and Feisty has so many nice new features. Amarok supports MTP devices by default, Compiz, Beryl, etc... Edgy had some problems so I never installed it on that computer. The big thing I like about Dapper is that where Edgy had problems, Dapper just worked. No matter what, it just works. But another thing is that there seems to be vanishing support for Dapper. The Ubuntu Beryl Project has removed the the Beryl packages for Dapper form their repos? Why though? Dapper is going to be around longer that Edgy.

Just a side note, there seems to be a random:cool: in the pole

---

### Post by dbbolton on 2007-04-06
> 6.04 Dapper LTS (support ends June 2009)

isn't dapper 6.06

---

### Post by WalmartSniperLX on 2007-04-07
I personally ONLY use Dapper. I've tested Feisty and I tested Edgy when it was still an alpha, however as far as my productive pc goes, Ill only run an LTS release since I don't have to worry about upgrading. Honestly, keeping up with the latest releases is only beneificial for those who strive to work with the latest software and features of linux, and like to work ON Linux. It does not benefit one who needs a long lasting install that is dependable and secure for any kind of serious work unrelated to the OS. 

However because the rapid releases of Ubuntu, I no longer even use Ubuntu on my main pc. This is the reason that keeps me from wanting Ubuntu on a productive system. I would use 6.06 but the repos have older programs on it and Ive had nothing but problems when trying to add Edgy repos and updating from there. Right now Im running Gentoo (ironic because it takes more time to set up) because once it's set up, I can update it without having to do clean installs, broken programs, and the performance is extremely beyond Ubuntu or any other distro that I've used. Its faster than PC BSD and Solaris. Its simply perfect for me. 

However I have nothing against Ubuntu's rapid release cycle. The LTS Lineup is one of the many great things about Ubuntu. In general I still think its the best community supported Distribution and its the best choice for people who are migrating from OS X, Windoze, or any other proprietary os that they're sick of to Linux. If you're one of these newcomers to Linux, then I would deffinately recommend Ubuntu 6.06 LTS without any other considerations.

---

### Post by siimo on 2007-04-07
I am still using Warty on my old machine.  Another machine my parents use has Breezy.  I have no plans to upgrade either of them.

---

### Post by RandomJoe on 2007-04-07
I use Dapper on my primary machines.  (A desktop and a laptop.)  While I like to play around with the latest-and-greatest, and am quite enjoying Beryl on a Feisty machine, I need/want my primary systems to Just Work, so they don't get updated/upgraded a bunch.  Also, the last time I did an upgrade, 5.10 -> 6.06, two of three machines got hosed and I had to do a fresh install -- kind of kills the desire for upgrades!

The fact that Dapper is an LTS is why the desktop got it even though I built it in December.  

I am considering upgrading (fresh install) at least one of these to Feisty once it's been released just because I really like the way it's shaped up.  But I'll decide that for sure later on.  I'm much too happy with my fully-functioning system to make that change on a whim!

---

### Post by daynah on 2007-04-07
I'm the type of person who wants to update my system every 6 months... but I think Edgy stunk. Edgy ate my laptop. And then I didn't trust it for my desktop. I closed my eyes and quickly went through the updates to get my laptop to Feisty beta on my desktop, but I went back to Dapper on my laptop until Feisty is ready.

That's another reason, imho, we have LTS.

---

### Post by daxumaming on 2007-04-07
I'm still using Dapper on my other PC and I still use it regularly. I just like having Dapper around when I need him.

---

### Post by qpieus on 2007-04-07
I still use dapper on my main desktop pc. I thought I would be one who would upgrade every 6 months when the new release came out, but I found that I'd rather have a working system that I don't have to mess with. That's what I have with my dapper setup - no problems and it works. While I would like to have the latest and greatest versions of some packages, that is not as important to me as a well running care-free system. As someone wrote here in an earlier post - if it isn't broken, don't fix it. For the tinkerer I have lurking within, I have an older pc I can play around with to try out the new releases.

---

### Post by nauseaboy on 2007-04-07
I use dapper on a number of my servers. I don't want to reinstall my servers every 6 months.

---

### Post by Pikestaff on 2007-04-07
I'm using 6.06 Dapper primarily because it's the only version that works out-of-the-box with my wireless card.  Edgy and Feisty don't.

---

### Post by salsafyren on 2007-04-07
I'm using dapper on a machine where it should just work.

On my laptop I have both edgy and feisty.

I think the LTS idea is great but at the same it has some weaknesses. Such an old distribution makes it hard to get current packages for. An example of this is the fakenes package which I wasn't able to compile on dapper, but works fine on feisty.

Getdeb.net or backports is a great idea for people wanting newer packages. However, I think that the Linux community should strive for a more stable base because upgrading all the time is not going to work in the long run.

You could ask "why are you not satisfied with the packages that dapper has?"

I want stability of the platform AND a possibility of installing new packages without compromising the stability of the OS.

The interesting question is when will we be able to have a stable OS and be able to install and upgrade non-OS (OS being Gnome, Kernel, X, KDE etc) packages?

I know that my wish needs a great deal of work and money. But I think the advantages it will give us in the long run will outweigh the disadvantages.

---

### Post by Shay Stephens on 2007-04-07
I use three computers in my business, one desktop that does photo editing and video generation.  That one is running edgy.  My second computer is a desktop that does business related stuff and lightscribe disks.  That is running dapper.  And I have a laptop that is just for travel which is running feisty.

When Feisty goes gold, I plan on upgrading all the computers to it as it looks like it will support lightscribe burning as well as it did on dapper.  Dapper has been important to me but it is getting close to being too old for me.  I am looking forward to feisty.

---

### Post by Erik Trybom on 2007-04-07
I'm running Dapper on my parents' computer because:

1) I just want it to work.
2) At the time I installed it Dapper was the latest version and I've never bothered upgrading it.
3) They don't need any new packages (we're talking old hardware).
4) Did I say I didn't bother?

But really, you don't need a reason for NOT upgrading. All you need is too little reason FOR upgrading.

---

### Post by djheadley on 2007-04-07
I use Dapper on both my desktop and laptop (both older machines) because it "just works".  I'm starting to put together older machines (that won't run XP or Vista) and hope to sell them to people who currently can't afford even a basic new computer.  I plan on using LTS releases because they are stable and since I'm not going to be using the "latest and greatest" hardware, I want something that "just works" with older hardware.  It also would be less work for me, not having to go and upgrade every computer I sell every 6 months and will, I hope, be a good selling point.  BTW most of my proposed clients would probably be using dial-up (rural area) so upgrading by the internet would be REALLY awkward.

---

### Post by Shay Stephens on 2007-04-07
> **Erik Trybom said:**
> But really, you don't need a reason for NOT upgrading. All you need is too little reason FOR upgrading.

That is sooo true

---

### Post by Erunno on 2007-04-07
I thought that the LTS versions were meant for cooperate environments where update policies are much more conservative. For instance, there were a lot of Windows 2000 machines in many departments I visited which only upgraded recently to XP after the support for Win2k ran out and don't have any plans for an Vista upgrade right now. So it's not unusual that some businesses and universities stick with the same base system for a couple of years due to improvement in support for a largely known platform. And that servers tend to get upgraded sometimes even less has already been mentioned :P

As a private user, LTS is also not very interesting to me as I like all the shiny new packages :D

---

### Post by getaboat on 2007-04-07
For the rest of my household a computer is a tool not a toy so it just has to work. Having switched the house computer from W98 to Dapper and my own personal computer from W98 to Edgy - I'm trying to persuade the other Windows users in my house that life is more relaxed with Linux.

LTS to me is a pointer to stability. I will go to Feisty for my own personal computing just as soon as it is out of Beta.

---

### Post by jbonll05 on 2007-04-07
Dapper's place in the scheme of things is as i have 6.06.1 running my small business office, since June of last year. With support until 2009, I can expect it not cause hangups or errors due to trying to stretch it out. My projects machine, on 6.10, will not burn cds/dvds. The build towards Fiesty from 6.10 has the kernal ahead of the cd/dvd writer. It doing error messages. Updates will take care of that. I transfered my first quarter 07 projects to this machine(with 6.06) with a usb drive and put them on a cd also. Updates will sync the burner and kernal shortly. I did not loose any files.
  It is also for the "everyday" user that does not want to change their os everytime the moon changes. People who want it to run the way it use to everytime thay turn it on. That is LTS. If any of the people like this that I have loaded Ubuntu for ever had a problem they would call me. Most were running M$ 98 or ME. They have had some hardware failures, but not os problems - and they have not had to pay for professional help. I am backed up by a local professional network and website manager that I got to switch from Mandrake to 6.10 by giving him a cd.                                                       
jbonll05; Ubuntu since 4oct05

---

### Post by bone_saw on 2007-04-07
> **WalmartSniperLX said:**
> . . . I still think its the best community supported Distribution and its the best choice for people who are migrating from OS X, Windoze, or any other proprietary os that they're sick of to Linux. If you're one of these newcomers to Linux, then I would deffinately recommend Ubuntu 6.06 LTS without any other considerations.

That right there is the biggest reason I went with Dapper when I started switching from XP to Linux.  And that was only a couple of months ago.

---

### Post by Atreus12 on 2007-04-07
I run 6.06 dapper, because I * need * my computer to work every day. Plus, I finally have dapper running exactly the way I want it. The last thing I want to do is start over from scratch every six months.

-Andrew

---

### Post by urukrama on 2007-04-07
I still use Dapper, and probably will so for quite a while. When Dapper came out, I upgrade from Breezy, but saw no need to upgrade further to Edgy (or Feisty in a while). I've even had to reinstall Ubuntu on my laptop, and just reinstalled Dapper.

I don't see why I need Edgy or Feisty. I know what changed and/or improved, but I don't need any of it. Dapper provides a stable work environment, and that's all I need. 

When the next LTS comes out, I'll probably switch to that, though,  (by that time I'll probably need a new computer as well) But for the moment I'm quite happy with Dapper.

---

### Post by weasel fierce on 2007-04-07
I eventually updated to Edgy, but as far as I can see, there's little difference. Dapper still does what most people want, and without problems

---

### Post by d.j.schroeder on 2007-04-07
Similar to many others here, I'm using Dapper on a server (web).  I don't have any plan or need to upgrade hardware unless something breaks, and possibly not then if I can get replacements.  I love the concept of a LTS OS for applications like this.  The system needs to work, it does not need to be cutting edge.

---

### Post by AndyCooll on 2007-04-07
I have Dapper running my file server. Like others, no need to upgrade, stability is important, and no need for the new features.

I'm currently running Edgy on my desktop and laptops.

:cool:

---

### Post by FuturePilot on 2007-04-07
I think I'm probably going to just leave Dapper on my laptop. It's very stable and it never gave me any problems. It's amazing how it just seems to work. I wonder what will be in the next LTS.

---

### Post by Eddie Wilson on 2007-04-07
Good Day,
I started with 5.10, went to 6.06, then tried 6.10. Had a lot of problems with Edgy not being stable every day. Some days it would work great and other days it wouldn't and then it would work good again. I went back to Dapper 6.06.1. I will try Feisty when it comes out. I agree that a lot of people just want things to work and don't want a bug fest. I'm hoping that the problems with Edgy being stable will be corrected in Feisty. I really like Ubuntu and would hate to have to move to another distro to get latest stable software.
Eddie

---

### Post by MrHorus on 2007-04-08
I run Dapper on my laptop and XUbuntu on my old laptop as both are aging (P3 and Sempron) and both have crappy graphics cards that aren't up to much (damn you SiS!).

On my server I use Debian Etch and on my VM server I run Debian Experimental as I prefer and trust Debian more for that sort of environment.

If I get a new laptop or desktop later in the year (and it's very likely) then i'm going to have a choice on my hands although I suspect I might stick Feisty on it for a laugh.

---

### Post by DC@DR on 2007-04-08
I've been on Dapper since the day I started to switch completely over to Ubuntu from Windoze. Since then, I've had no complaint at all for Dapper's stability and "just work" feature. Gonna stick with it till the next LTS rolled out. I think I'm gonna play with LTS version only, cause I need my workstation "just work", no need for extra whistles and bells :-)

---

### Post by weekend warrior on 2007-04-08
Actually I have one of each version on different systems going back to Hoary. The oldest system is a little 500 Mhz 'Frankenbox' which started with Warty in 2004 and was upgraded to Hoary two years ago and still runs well; no net connection but still useful for simple tasks - word processing, media player, that sort of thing. 

My Thinkpad started with Breezy and then I resized that partition down to make way for Dapper, keeping Breezy for backup. It's stayed that way ever since and probably will for some time since it's perfectly stable and I'm happy with it.

The main box now is a P4 dual core running Edgy and I've been testing Feisty on it too. I'll probably 'upgrade' the same way as on the laptop - via another partition keeping the older just in case, which I think is one of the saner ways to upgrade.

So there you go, (almost) one of each version. It's interesting comparing and seeing the evolution of Ubuntu over the past three years.        

To answer the OP, it's good to remember that some people  have neither time nor inclination to bother with upgrades every six months and prefer a familiar, stable system. In my case, the older boxes aren't worth my time and effort to upgrade, nor do I have any reason to do so. They work well and the hardware isn't going to change. 

Another thought (from my former Debian days) is that 'newer' doesn't *necessarily* equal 'better'. I voted for Dapper LTS, long may she live. :wink:

---

### Post by Sunnz on 2007-04-08
My school seems to be running 6.06 LTS Kubuntu... started from around June last year!!!

When I install Ubuntu (for friends & family) I always get the server edition then install (k/x/ed)ubuntu-desktop, I find it to be more efficient than to download the whole thing just to download the update for it.

---

### Post by SlayerMan on 2007-04-09
Isn't it 6.06 Dapper LTS instead of 6.04? Just wondering...

---

### Post by r3m0t on 2007-04-09
Yes, I made a mistake in the original poll.

Results were very interesting - excluding the people who don't run Ubuntu at all, 2% run Breezy (possibly also with newer versions), 42% run Dapper (possibly also with newer versions), 34% run Edgy, and 23% have already moved all their computers to Fiesty for all their Ubuntu needs.

I never expected somebody to still be running Hoary though. Or was it Warty...? ;-)

---

### Post by sloggerkhan on 2007-04-09
As a desktop user, it annoys me when stuff isn't backported. So I am now using feisty beta as my main OS because there weren't backports of Rhythmbox, among other things. (I wanted the fluendo store plugin really bad.)

Also, as far as my computer goes, Feisty has just been so much better than any Ubuntu I've ever used on it so far as desktop use goes. It's the only linux to correctly detect my graphics card that I've ever used, it added support for a wine menu in the applications menu, and is overall just much more polished and complete than the other Ubuntu releases.

But I digress. The main reason I update through stuff is that I like relatively new versions of software but don't like installing from source, adding weird repos, or waiting for backports.

---

### Post by centered effect on 2007-04-09
> **Pikestaff said:**
> I'm using 6.06 Dapper primarily because it's the only version that works out-of-the-box with my wireless card.  Edgy and Feisty don't.

Amen to that.  I installed Edgy multiple time with 2 of my wireless cards and both a no go with wireless.  Dapper just picks everything right up.  Sucks,  I can't get Firefox 2.0 from the repos.  But hey it works beautifully.

---

### Post by Hobbsee on 2007-04-10
> **r3m0t said:**
> 
Also, isn't simultaneous support of 3 releases rather taxing on developers?

Maybe I have misunderstood LTS. :)

Yes, it is.  The main focus is on the development release, so only occasional things get backported.  The Stable Release Updates process is very strict, involving lots of testing, etc - particularly in main, as Canonical is professionally supporting it.

LTS *only* means security fixes, and maybe fixes for severely-broken apps.  People seem not to understand this.  Backports sometimes happen, for some things, but the time used there is not being used for making the development release as best as it can be.  

Most of the devs (for universe) arent getting paid, so can work wherever they like - and for the most part, that's feisty, which they're running.  If you're interested in helping out, which requires actual work, not wand waving and asking "can you upgrade this for me?", and then complaining when it's not done, then please see [http://wiki.ubuntu.com/MOTU/Documentation](http://wiki.ubuntu.com/MOTU/Documentation)

Of course, the devs working on main tend to be coding applications like the update manager, ubiquity, fixing network manager, gnome, kde, etc etc etc in feisty.  Which you all want working, too.

They occasionally even take a couple of days off!  gasp!

---

### Post by IcemanV9 on 2007-04-13
What does LTS mean to me? Mostly it is for servers (btw, it's 5 yrs for servers and 3 yrs for desktops). I would not want to upgrade servers every 6 months. That IS crazy. I rather to install LTS on servers and "forget it" for 5 yrs. All I need is to maintain those boxes with updates (security fixes and/or bug fixes). Same goes for desktops. It would be more productive/efficient for projects/tasks to be done without a problem. Basically, I don't have to mess with it except updates for 3 yrs. Now, that IS long term support.

The BIGGEST drawback for the LTS is the backports (and/or repo). It IS not part of LTS anyway. However, I strongly believe backports (and/or repo) should be seriously maintained for ALL (currently supported) versions. It would be great to update lots of app (and drivers) to the latest (stable, of course) version, such as, ATI, Nvida, OpenOffice.org, Firefox, Network-Manager, rhythmbox, gaim, evolution, Gnome and etc. BUT, unfortunately, the best way to get the latest version is to upgrade OS just like M$ OR compile it only if you have time to mess with it (errors). AND, don't forget there are lots of noobies who don't have skills or understanding on how to compile stuff.

Anyway, at home, I have 6.06.1 (LTS) on a primary laptop with lots of important documents, photos, music (mp3, ogg, wav) and data (Oracle). And, another laptop which is running 6.06.1. It will be upgraded to 7.04 (once it is released).

---

### Post by freesitebuilder on 2007-04-13
> **DC@DR said:**
> I've been on Dapper since the day I started to switch completely over to Ubuntu from Windoze. Since then, I've had no complaint at all for Dapper's stability and "just work" feature. Gonna stick with it till the next LTS rolled out. I think I'm gonna play with LTS version only, cause I need my workstation "just work", no need for extra whistles and bells :-)

This was my plan too - but is it practical? Or should I update fairly often? I don't use cutting edge hardware, or change my hardware much. But I do want my machine to work when I need it.

Is there always going to be an LTS version available?

---

### Post by Sunnz on 2007-04-13
> **freesitebuilder said:**
> This was my plan too - but is it practical? Or should I update fairly often? I don't use cutting edge hardware, or change my hardware much. But I do want my machine to work when I need it.

Is there always going to be an LTS version available?
If your LTS worked, there's nothing wrong with staying with a working OS.

Maybe you can also ask yourself: is it practical to update every 6 months?

---

### Post by Fascination on 2007-04-13
[IMG]http://i21.photobucket.com/albums/b279/fascuk/rofl.jpg[/IMG] 

Thats the main reason Im on dapper. ;)

Dapper works great on it, doesnt clog it up as much as the newer releases and its reliable while doing the job I need it to do (remote into other servers, chat on irc, post on here, play music).

---

### Post by QwUo173Hy on 2007-04-15
> **centered effect said:**
> Amen to that.  I installed Edgy multiple time with 2 of my wireless cards and both a no go with wireless.  Dapper just picks everything right up.  Sucks,  I can't get Firefox 2.0 from the repos.  But hey it works beautifully.
Odd, I found my USR wireless card to behave even better with Edgy. It's always connected to the router on boot up and hardly ever drops the connection.

---

### Post by keithpeter on 2007-04-15
> **Fascination said:**
> [IMG]http://i21.photobucket.com/albums/b279/fascuk/rofl.jpg[/IMG] 

Thats the main reason Im on dapper. ;)


Nice machine there!

I use Xubuntu 6.06.1 LTS on a P4 with an old graphics card as my main 'do stuff' computer. It works with most features and I like the basic desktop approach. I decided to install OpenOffice 2.1 as I found aspects of 2.03 broken in the Dapper release. I can live with Inkscape and Dia in the LTS versions. I hope there is an LTS -> LTS upgrade path for Xubuntu users.

I have a P3 laptop that I mess with. Xubuntu 7.04 is on that one. I want to see if 7.04 is usable on a laptop that is  6 years old. That is ace isn't it, a fully up to date OS with current packages running on old hardware?

---

### Post by RockinRob2258 on 2007-04-15
Quite frankly, LTS has a definite place as some people and organizations do not ugrade hardware every 36 months and need long term solutions.  A great example is the Electrical and Computer Engineering department at the University of Tennessee.  Last year, we switched our linux lab over to Dapper Drake.  I asked if the tech guys if they were going to switch over to 6.10.  Their answer was no, they need long term solutions that are relatively stable and don't necessarily want the hot new thing.  LTS defintely has its place.

---

### Post by FuturePilot on 2007-04-15
Kubuntu Edgy started giving me problems, so now I'm back on the tried and true Ubuntu Dapper on my laptop. Dapper has never given me any problems and it's reliable. This is an older laptop so I'm not to worried about hardware support as everything works fine and I don't plan on upgrading any of the hardware, not like that's exactly easy or even possible in some cases on a laptop.

I'm going with Feisty on the desktop though.

---

### Post by tripolitan on 2007-04-15
I use my PC for production on a daily basis. I learned by experience ( and I have lots) that stability is what I need most out of an operating environment, therefore, once I'm set with a distribution, I will not "upgrade" and risk hosing a perfectly good system, like I have done numerous times before with Ubuntu and many other distros. 

That is why I chose LTS, all my hardware is supported and works, including scanners and webcams, all I need is the odd security fix. I think that 3 years is a good age for a stable production distribution.

---

### Post by kdrlx on 2007-04-19
> **picpak said:**
> If you go throughout this forum, you can still see a couple Dapper users.

A couple ? I use Dapper and I think there are many here, as depicted by the poll that use Dapper.

---

### Post by ske1fr on 2007-04-19
> **r3m0t said:**
> Maybe I have misunderstood LTS. :)

I use it because it works, and it's stable.  Edgy lasted four days before X broke beyond my ability to repair (and I'm experienced in fixing it with my dodgy laptop...).  Dapper just goes on, and on, and on...It's the thing that has finally broken my Windows dependency.

In the end, I want my machine to be functional and reliable.  Having said that, I'm panting at the starting gate for a Kubuntu Feisty final image, because I'd like to try it out!

---

### Post by 3rdalbum on 2007-04-19
I'm running Dapper on my main x86 desktop, and Breezy on my iMac. I'll probably still run Breezy on the Mac even after support runs out.

Admittedly, I will be switching to Feisty on the x86.

---

### Post by jvc26 on 2007-04-19
I have a computer on edgy - but because its more stable than dapper, with the more updated packages - sound weird? Basically, that pc has weird issues with dapper at times, and furthermore now dapper has some stuff which I needed newer versions of etc. From its use, edgy was more stable than dapper and fitted my spec better so I stuck that on - and I wont upgrade to feisty I'll probs wait for an LTS or not bother til its support runs out. On my main pc I have been running Feisty since herd4 (dangerous I know, but fortunately I never had an issue I couldnt sort out) -  that'll jinx it ;) But yeah, thats my pc setup - oh and have had 6.06 on the server til I switched it out and put freeNAS on it as a NAS box experiment.
Il

---

### Post by UrbanSlayer on 2007-04-19
I still run one Breezy machine, and that is my MythTV box.  While it, and its Myth install is now very out of date, it does still just work and do exactly what I need.  I will probably upgrade it, but I know it will take me a weekend of fiddling to get everything working right.

My X300 laptop runs Edgy at the moment, although will most likely upgrade to Feisty, and my desktop has Feisty on it after a hardware upgrade. 

My Linux servers however all run Debian Stable.  Why?  Because I havent found anything else that is as stable for a server environment that is tried and tested.  The release schedule might be slow, but everything does just work and it needs minimal maintenance.  

Since I have a a few spare machines, it isnt a massive problem if one of them is down while I tinker with it to make stuff work, but thats only the desktop side, my servers have to be rock solid stable with minimal downtime.

---

### Post by diskotek on 2007-04-19
i already installed 6.06 LTS - Dapper on my desktop / amd64. i just click on update icon and now i have edgy eft i think. i wished to use LTS, but i would like to have updates of software. is that possible to just update software not all system?

---

### Post by Wartooth on 2007-04-19
I'm using LTS.  I am completely new to Ubuntu, Linux, etc. I also don't see any appeal in upgrading and fiddling with things every six months.  Given that I am new, I am unsure as to when I will be 'ready' to undertake such things, anyway.  I've considered moving up, but right now I don't have the time or patience to deal with endless tweaks, so it is likely I will just hang on until a new LTS comes out.

---

### Post by dca on 2007-04-19
Hmmm, I will only use LTS releases from Ubuntu...  That even goes for my personal laptop and desktop(s).  
 
I know the mid-releases are stable (to a point maybe) but I generally equate them to openSuSE/Fedora releases every four to five minutes and then those lead up to their commercial release either SLES-SLED or Red Hat...  Ubuntu does the same thing to an extent, however, the benefit is the commercial (LTS) release is just as free as the others versus RedHat/SLES charging for it.

---

### Post by freesitebuilder on 2007-04-20
I think that normally we can only upgrade from one version to the next, without skipping versions.

But can we upgrade from one LTS to the next, or must we still do all the upgrades in between?

---

### Post by cjax1 on 2007-05-18
If I see another poll I'll scream.

:)

---

### Post by jerrylamos on 2007-05-18
Why do you want back levels to run?  It's easy.  Look at the bug lists for Feisty.  A number of people tried Feisty, got bugs, figured out there wasn't that much advantage, and went back to Edgy.  We need at least a couple back levels of Ubuntu supported because it might take 6 months to a year for some of the more technically complex bugs in Feisty to get fixed.

Fall back plan absolutely necessary.

Cheers, Jerry

---

### Post by FuturePilot on 2007-05-18
I had Feisty on my laptop for a while, and except for a few minor bugs I thought it was pretty stable. Until....it started randomly freezing on me.#-o:cry: I'm not using any compositing either so that's not the problem. So, once again I've got good old rock solid Dapper on my laptop.

---

### Post by jariku on 2007-05-19
> **jerrylamos said:**
> Why do you want back levels to run?  It's easy.  Look at the bug lists for Feisty.  A number of people tried Feisty, got bugs, figured out there wasn't that much advantage, and went back to Edgy.  We need at least a couple back levels of Ubuntu supported because it might take 6 months to a year for some of the more technically complex bugs in Feisty to get fixed.

Fall back plan absolutely necessary.

I don't see how this is not already implemented. Ubuntu 6.10 is supported to April 2008, Ubuntu 7.04 to October 2008 and the LTS version Ubuntu 6.06 to 2009.

These three are all currently supported. By the time support for Ubuntu 6.10 is dropped, two more Ubuntu releases are out.

---

### Post by eentonig on 2007-05-19
I haven't read through the entire topic.

But I can garantuee that companies who plan to rollout a linux desktop environment, will want/ask/need a LTS version for their desktops. 

They usually keep the same machines for three to four years. And don't change the companie default installation that often.

---

### Post by SunnyRabbiera on 2007-05-19
I am going to downgrade to dapper very soon here, as FF really doesnt do it for me.

---

### Post by QwUo173Hy on 2007-05-19
Hi SunnyRabbiera. I'm curious - what do you use your installation for? Obviously a server admin probably wouldn't have a major need to upgrade to Feisty just yet so I'm assuming you're a fairly demanding user (multimedia / gaming ).

Also, do you have special hardware requirements that aren't met by Feisty, like a grahpics tablet for instance?

I upgraded from Edgy on an old Dell laptop (850Mhz, 512MB Ram) and it went well, although I can't have 3D graphics. How was your experience?

---

### Post by slipperhead on 2007-05-19
i use dapper as it does all i need for the moment. feisty wont boot on my laptop so i cant try it unless i do the whole upgrade edgy/feisty thing which i dont want to do without knowing i wont have problems at the end of it.

---

### Post by AusIV4 on 2007-05-19
My computers run the gammut. I have a MythTV box that runs Dapper, because edgy was giving me trouble with my RAID setup when it first came out (I think this is fixed, but I haven't bothered to check). I figure if it ain't broke, don't fix it, and this is the computer I need to have the most stability.

I have a laptop that runs Edgy (though I'm phasing it out in favor of my System76 Gazelle). I haven't upgraded it because it has lots of software that isn't in the repositories and would likely break if I tried to upgrade.

I have another laptop (my Gazelle) that dual boots feisty and Edgy, though I'm using Edgy at the moment because of an issue with power management. Once the System76 team puts a patch through for that, I suspect it will be feisty full time.

I intend to leave my MythTV box on Dapper until it's no longer supported - even then I'll probably leave it on Dapper until the lack of updates makes it fall completely to pieces.

---

