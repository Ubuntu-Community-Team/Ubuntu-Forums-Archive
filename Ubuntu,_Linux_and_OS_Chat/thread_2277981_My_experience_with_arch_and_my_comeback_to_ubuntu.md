---
title: "My experience with arch and my comeback to ubuntu"
date: 2015-05-13
forum: Ubuntu, Linux and OS Chat
---

### Post by user1397 on 2015-05-13
I'm sure stories like this have been posted 1000 times here but maybe others can identify with it so here it goes.

I had always been interested in the idea of arch linux.  Rolling release, never having to upgrade to a new release again, always up to date packages, minimal bloat, utmost control.  A lot of things ubuntu does not have.  Not that one is better than the other, they just have different goals.

I installed it in virtualbox successfully a while back, but I didn't mess with it too much.

I finally decided to take the plunge the other day and go all out; I decided to install it as my main OS, dualbooting with windows 8.1 on my laptop (before I was dualbooting with ubuntu 15.04).

I followed the beginner's guide once again to the letter, and I only had one hiccup.  I was able to get help from the arch irc channel, and I resolved the issue and was able to successfully install arch (a dualboot set up with win 8.1, GPT disk, UEFI, grub2, secureBoot off).

***
If interested in what my hiccup was during the install, read this section.  So I got to the very last part of the beginner's guide, installing a bootloader.  I planned on installing grub2 since that is what I'm most familiar with.  What confused me was the wiki didn't specify exactly what to do if you're dualbooting with windows 8 for example.  It suggested reading the actual grub page for more complicated setups, so I went there.  Once there, there was a little section specifying that if you were dualbooting with windows 8, you had to find out on which partition resided the EFI files from windows.  I found out what that partition was, but the only problem is that in the next section of the wiki it didn't say what I had to do different in accordance with the information I just found out about my EFI partition.  So basically, before the chroot, I had only mounted the / partition and not the /boot partition, so when installing grub inside the chroot and after executing grub-mkconfig no entries were listed.  I rebooted and I just arrived at the grub shell.  Luckily with the help of some people on the arch irc channel, all I had to do was boot back into the live medium, mount / and /boot, go back into the chroot, and reinstall both the kernel and grub, and re-run the grub-mkconfig command.  By reinstalling kernel I literally just mean "pacman -S linux" :)
***

Although there was one moment during the install that I started to lose hope, I got through it and was back at the command line, ready to setup my new arch system.  I had always thought that the most annoying part about arch would be the install, and not the setting up afterwards.  I found out I had been wrong.

Although there are quite a few little things to customize and setup during the initial install, it seems like a tiny bit compared to the amount of configuring post-install.  The more things I installed, the more arch wiki pages I had to pull up, to customize this and that all over the place.  It started wearing down on me, and the more I thought about the conveniences of an ubuntu installation I became more and more dismayed by the sheer amount of time I would have to spend configuring everything to my liking.  I still have to configure and customize some things in ubuntu, but not like this.

So, I had an epiphany, and I said screw it.  I gave it a try, installed it correctly, got a DE (kde plasma 5) setup and was starting to customize it.  But I had a realization that I simply don't care enough *myself* to sit there and customize this seemingly infinitely customize-able distro.

I am now using Kubuntu 15.04 and loving it.  I don't agree that there is no point to arch...quite the contrary I think it serves a good purpose and the option is there for anyone to try it and customize it to their liking.  I just personally don't have that arch itch anymore, and boy am I glad it's over, because I ended up wasting a lot of time trying different distros and never feeling satisfied :)

**TL;DR**
I installed arch, ended up thinking effort-to-time ratio wasn't good enough, so now I'm back on Kubuntu.  C'est la vie

---

### Post by vellon on 2015-05-13
Setting up KDE or Gnome with Arch is hardly its best use case, in the same way it would not be an especially rewarding experience trying to recreate Kubuntu from an Ubuntu Minimal install. Arch users have a massive over-representation in usage of simpler window managers like Openbox, i3 and Awesome and more minimalist software like mpd and vim. That is where Arch shows its strengths.

Like anything there is a learning curve, so early experiences are never going to be as comfortable or speedy as something you have used for years.

By way of contrast, as a long-time Arch user, I recently had to do a minimal Ubuntu/Xfce install for the first time in years. I was surprised how much googling was necessary to get everything sorted. I cursed the need for PPAs, and don't get me started on the (lack of) speed of apt compared to pacman...

As ever, happiness lies in using the right tool for the job.

---

### Post by user1397 on 2015-05-13
> **vellon said:**
> Setting up KDE or Gnome with Arch is hardly its best use case, in the same way it would not be an especially rewarding experience trying to recreate Kubuntu from an Ubuntu Minimal install. Arch users have a massive over-representation in usage of simpler window managers like Openbox, i3 and Awesome and more minimalist software like mpd and vim. That is where Arch shows its strengths.

Like anything there is a learning curve, so early experiences are never going to be as comfortable or speedy as something you have used for years.

By way of contrast, as a long-time Arch user, I recently had to do a minimal Ubuntu/Xfce install for the first time in years. I was surprised how much googling was necessary to get everything sorted. I cursed the need for PPAs, and don't get me started on the (lack of) speed of apt compared to pacman...

As ever, happiness lies in using the right tool for the job.

Perhaps.  I wasn't aware of the massive over-representation, are there any statistics on that? I always thought the kde/gnome arch wiki pages were very popular, so much so that for example kdemod became chakra etc.  You have a point either way, being a minimalist distribution, it makes more sense to use a minimalist WM or DE.  I personally don't like that level of minimalism, but I understand why some do.

There is definitely a learning curve, but I must admit the arch wiki for the most part has such excellent documentation that you hardly need to be a kind of expert to get through anything.  I do admire that about arch.

I will say I'm surprised at your comment about installing kubuntu from a minimal install.  It is insanely different from an arch install + kde.  Once you have the base ubuntu minimal system installed, you literally just sudo apt-get install kubuntu-desktop and you have the exact same experience as you would installing it from the kubuntu iso.  Not so with arch, where after installing kde for example, you must configure a million things still.

True, pacman does seem faster to me as well, I'll give you that.  PPAs are unclean in a way, and I don't currently use any other than the google chrome stable repo, but I still think they're far more convenient than the AUR and packagebuilds.  I mean, you have to usually do more with a AUR package and look up more things than for your usual ppa install.  

Couldn't agree more with your last statement though :P

---

### Post by vellon on 2015-05-14
> **ubuntuman001 said:**
> Perhaps.  I wasn't aware of the massive over-representation, are there any statistics on that? I always thought the kde/gnome arch wiki pages were very popular, so much so that for example kdemod became chakra etc.  You have a point either way, being a minimalist distribution, it makes more sense to use a minimalist WM or DE.  I personally don't like that level of minimalism, but I understand why some do.


Just observations from reading the Arch forums. There was a long-running poll of favourite window manager/desktop, and it was dominated by Openbox and tiling window managers. Also check out the monthly screenshot posts. There are plenty of Gnome/KDE and Xfce users, of course, but nowhere near the same percentage of other build-your-own distros. There will, naturally, be some bias as a result of the most technical users being the most prolific posters, but the same would be true of the Debian forums, and, anecdotally, they show far more mainstream desktop favour.

---

### Post by buzzingrobot on 2015-05-14
> **vellon said:**
> Just observations from reading the Arch forums. There was a long-running poll of favourite window manager/desktop, and it was dominated by Openbox...


The amount of noodling around needed to get Openbox beyond the its barren and basic default state seems to fit in quite nicely with the noodling opportunities presented by Arch across the board.

I've done Arch, and my Linux experience began with Slackware.  At this point, I don't see enough payoff from the Do It Yourself approach.  It's all the same code and it can all be tweaked as much as anyone wants on any distribution if someone wants to go to the effort.

---

### Post by malspa on 2015-05-14
> **buzzingrobot said:**
> The amount of noodling around needed to get Openbox beyond the its barren and basic default state seems to fit in quite nicely with the noodling opportunities presented by Arch across the board.

I get Openbox set up quickly these days -- I keep copies of my old Openbox config files, so I simply paste those into the new installation. Makes things very easy; just a few minor tweaks and it's done.

For Arch, my approach was to first spend some time with a few Arch derivatives (Bridge Linux, ArchBang). After a few months, I decided I was liking what I was seeing, so I did a "practice" Arch installation on a spare computer. I took lots of notes. Then I went back and installed Arch again, on a different computer. The second time around went smoothly, especially with the help of my notes, and the end result's worth the time spent, in my opinion. Of course it's "rolling-release," so I have no plans (and no need) to do another Arch installation anytime soon. Excellent distro.

---

### Post by buzzingrobot on 2015-05-14
> **malspa said:**
> ...I keep copies of my old Openbox config files...

Very smart idea. I could live quite happily with Openbox.  Just have never gotten around to doing it.  

The rolling nature of Arch goes a long way to resolving an issue that affects Linux:  Shared libraries. Two applications that depend on the same version of the same library may, or may not, be able to be upgraded individually.  If upgrading to App One version 1.1 pulls in a upgrade to Library One that breaks App Two version 1.0, then the user who needs to use the new version of App One and the current version of App Two has a problem. By upgrading every package more or less as soon as possible, rolling releases either push this annoyance aside or make the pain as short lived as possible. Of course, not everyone has the patience or time to spend tending to the Arch garden.

---

### Post by craig10x on 2015-05-14
When Ubuntu "snappy desktop" stable version is ready for prime time, it may become the ultimate solution for a rolling style distribution...stability plus getting new features, apps, kernels drivers when stable and ready to be pushed to it (with no need to re-install every 6 months to get it all)...Of course, that is assuming that the concept as it has been presented, works out as well in reality...

---

### Post by vellon on 2015-05-15
> **buzzingrobot said:**
> 
I've done Arch, and my Linux experience began with Slackware.  At this point, I don't see enough payoff from the Do It Yourself approach.  It's all the same code and it can all be tweaked as much as anyone wants on any distribution if someone wants to go to the effort.

Fair enough. If you are not a tweaker, then Arch is not for you. For me, using something that is not available as an Ubuntu ISO, the one-off investment in set-up is worthwhile to me,  would be required from Ubuntu Minimal anyway, and avoids periodic re-installs/configuring.

---

### Post by user1397 on 2015-05-15
> **vellon said:**
> Fair enough. If you are not a tweaker, then Arch is not for you. For me, using something that is not available as an Ubuntu ISO, the one-off investment in set-up is worthwhile to me,  would be required from Ubuntu Minimal anyway, and avoids periodic re-installs/configuring.
The thing is, most people don't use ubuntu minimal, but even if they do, ubuntu minimal is in no way like the base arch system.  It is 1000 times easier to install.  Yes, you would avoid periodic reinstalls, but honestly from what I've learned, the minimal amount of configuring you need to do post-ubuntu/kubuntu install is so tiny compared to most other distributions.  So I'd rather reinstall every 6 months and have a fresh new system and configure a few things here and there than to do the gargantuan task of configuring everything from the start.  

The worst case scenario in arch is if you mess something up so badly that you have to reinstall and retweak everything.  I get that.  The thing is, if you mess something up in ubuntu and you have to reinstall, you just have to back up your personal files, and reinstall the OS in 20 min and then you can spend maybe up to 1 hour reconfiguring things and then you're done.  So it's still worth it.

---

### Post by kevdog on 2015-05-15
I don't know -- I understand what you are saying.  I've installed Arch like on 3 different computers.  It's been a process.  The base system if you read the wiki is easy to get up and running.  And yes the tweaking if you want to do it could be endless.  However it seems over times, the tweaks I make, I just take the config files to the next setup so I never have to start back from scratch.  I'd agree Ubuntu is really easy from the start, but the problem is upgrades.  You can only upgrade so many times at least in my experience before something breaks and an reinstall is necessary -- kind of reminds me of Windows in a way where the registry became so corrupted over time a fresh install was needed in my experience about every 1-2 years.  The thing with Arch is it really never needs upgrading which at least for me is a big time saver.  I guess my time configuring everything in the Arch install is a time waster, but I can do this at my leisure and overtime.  I guess it just really depends on how much you want to tweak your system, and maybe I'm not one to overly tweak the system.  For the record, I'm using both Cinammon and KDE on Arch, so I'm not one of those minimalists you see.  I see the role for those, but just need something a little bit heavier at least for me. Usually however I find the Arch forums very helpful, however because of the smaller user base sometimes the answers just dont come as quick.

---

### Post by vellon on 2015-05-15
^Ubuntuman,  all irrelevant to me, so no need to defend Ubuntu. Ubuntu minimal will install and configure no more of xorg, i3, a notification daemon, samba and ssh than will Arch. The Arch installation procedure is no big deal to those who have done it a few times, despite all the internet perceived wisdom on the subject.

---

### Post by buzzingrobot on 2015-05-15
> **vellon said:**
> Fair enough. If you are not a tweaker, then Arch is not for you. For me, using something that is not available as an Ubuntu ISO, the one-off investment in set-up is worthwhile to me,  would be required from Ubuntu Minimal anyway, and avoids periodic re-installs/configuring.

These days, I know what I like, don't like, and don't care about, so I just focus on distributions, etc., that I know deliver something I like. Desktop Linux, happily, is mature enough that good options are available.

So, I don't have the patience or interest any more to start from scratch. The distribution that takes me an hour to set up is going to lose to the distribution that takes 15 minutes to get to my liking. I don't really need, either, to be on the Latest-and-Greatest rolling release train for my primary system.  I do use Fedora pre-release frequently, and Rawhide sometimes, which can be interesting.

Arch's install procedure is very well documented and should be foolproof for anyone with a bit of non-GUI experience. It's much easier to install Arch today than it was to install any Linux a few years into its existence. (I don''t think I ever got Debian 3 installed.).  Dependency resolvers and package programs weren't there either.

---

### Post by vellon on 2015-05-15
> **buzzingrobot said:**
> These days, I know what I like, don't like, and don't care about, so I just focus on distributions, etc., that I know deliver something I like

So do I, but no distribution produces an ISO matching those preferences.


> **buzzingrobot said:**
> Arch's install procedure is very well documented and should be foolproof for anyone with a bit of non-GUI experience. It's much easier to install Arch today than it was to install any Linux a few years into its existence. (I don''t think I ever got Debian 3 installed.).  Dependency resolvers and package programs weren't there either.

Agreed. As I said, no big deal, but Arch seems to have gathered (or kept) a reputation for being hard to install.

---

### Post by buzzingrobot on 2015-05-15
> **vellon said:**
> 

...Arch seems to have gathered (or kept) a reputation for being hard to install.

The "...non-GUI experience" bit eliminates most people.

---

### Post by monkeybrain20122 on 2015-05-16
You do arch because you want to poke inside a bit, not the same purpose for people who use Ubuntu. I mean, who the hell would go through all the hoops just to set up the OS if he just wants something that works? :) I set a side a 25 G partition for this kind of purpose and if thing break, or if it takes a week to figure out something before I can proceed, no prob. Ubuntu is the OS I use to get things done. :)

Meanwhile there are easy Arch distros such as Manjaro Last time tried it, liked it quite a bit until something upgraded and hosed the system. Had to reinstall,--but reinstalling Manjaro is rather painless comparing to reinstalling Arch :o


Sure Arch has the best wiki. But how did I install it while reading the wiki? A bit of a chicken and egg problem. I have no printer, I am not going to copy it by hand. I have two computers. One I was installing Arch on, the other was on Arch wiki. Otherwise you will have to read it on a phone (pain) or better, on a tablet. If you have only one computer and no gadget and no printer, like I was for a long time, then I don't know how to do it other than print the wiki from my neighbourhood internet cafe. :)

---

### Post by vellon on 2015-05-16
> **monkeybrain20122 said:**
> 
Sure Arch has the best wiki. But how did I install it while reading the wiki? A bit of a chicken and egg problem. I have no printer, I am not going to copy it by hand. I have two computers. One I was installing Arch on, the other was on Arch wiki. Otherwise you will have to read it on a phone (pain) or better, on a tablet. If you have only one computer and no gadget and no printer, like I was for a long time, then I don't know how to do it other than print the wiki from my neighbourhood internet cafe. :)

Don't worry, that's been thought of.... :)  The elinks text-based browser is on the installation media/base system, so you just need to get an ethernet connection up and running

---

### Post by user1397 on 2015-05-21
> **kevdog said:**
> I don't know -- I understand what you are saying.  I've installed Arch like on 3 different computers.  It's been a process.  The base system if you read the wiki is easy to get up and running.  And yes the tweaking if you want to do it could be endless.  However it seems over times, the tweaks I make, I just take the config files to the next setup so I never have to start back from scratch.  I'd agree Ubuntu is really easy from the start, but the problem is upgrades.  You can only upgrade so many times at least in my experience before something breaks and an reinstall is necessary -- kind of reminds me of Windows in a way where the registry became so corrupted over time a fresh install was needed in my experience about every 1-2 years.  The thing with Arch is it really never needs upgrading which at least for me is a big time saver.  I guess my time configuring everything in the Arch install is a time waster, but I can do this at my leisure and overtime.  I guess it just really depends on how much you want to tweak your system, and maybe I'm not one to overly tweak the system.  For the record, I'm using both Cinammon and KDE on Arch, so I'm not one of those minimalists you see.  I see the role for those, but just need something a little bit heavier at least for me. Usually however I find the Arch forums very helpful, however because of the smaller user base sometimes the answers just dont come as quick.True.  I do agree the arch install itself is not that bad as I've said earlier, compared to the post-install work.  Not a bad idea to just transfer the config files over from setup to setup.  And yes, ubuntu upgrades can be problematic.  Thing is, I do clean installs most of the time cause my post-install tweaking is so minimal.  Again, i'm not discounting arch or saying there's no point to it, just saying it's not for me.  About the arch community though, I will say I don't have much experience in the forums (never posted there) but I have read online about some members being hostile or unwelcoming (don't know if that's true or not).  Either way I've rarely seen any hostility in these forums, and I've been here since 2006.  I will say I find it kind of weird that to sign up on the arch forums you need a linux terminal to be able to return some code that lets you complete the signup process on the forums.  I think that's a bit excessive...what if you're curious about arch and want to explore the forums and ask questions but you happen to be on a windows comp at the time?  Doesn't make much sense to me...

> **vellon said:**
> ^Ubuntuman,  all irrelevant to me, so no need to defend Ubuntu. Ubuntu minimal will install and configure no more of xorg, i3, a notification daemon, samba and ssh than will Arch. The Arch installation procedure is no big deal to those who have done it a few times, despite all the internet perceived wisdom on the subject.I see what you're saying, and the actual arch install procedure if following the wiki closely isn't that involved, but it's still more involved than an ubuntu minimal.  Because an ubuntu minimal automatically configures mostly everything, and then only thing you have to do at the end is sudo apt-get install whatever you want and then reboot and you're good, whereas it's not that simple on arch (you have to separately install the dm, configure it to autostart, setup user accounts and possibly sudo,etc)

> **buzzingrobot said:**
> These days, I know what I like, don't like, and don't care about, so I just focus on distributions, etc., that I know deliver something I like. Desktop Linux, happily, is mature enough that good options are available.

So, I don't have the patience or interest any more to start from scratch. The distribution that takes me an hour to set up is going to lose to the distribution that takes 15 minutes to get to my liking. I don't really need, either, to be on the Latest-and-Greatest rolling release train for my primary system.  I do use Fedora pre-release frequently, and Rawhide sometimes, which can be interesting.

Arch's install procedure is very well documented and should be foolproof for anyone with a bit of non-GUI experience. It's much easier to install Arch today than it was to install any Linux a few years into its existence. (I don''t think I ever got Debian 3 installed.).  Dependency resolvers and package programs weren't there either.Agreed.  The only thing that was bothering me about kubuntu 15.04 was that plasma wouldn't be updated more frequently, but I added the kubuntu ppa and now I'm on the latest and everything's surprisingly stable!

> **vellon said:**
> So do I, but no distribution produces an ISO matching those preferences.

Agreed. As I said, no big deal, but Arch seems to have gathered (or kept) a reputation for being hard to install.what do you mean no distribution produces an iso matching those preferences, what are you referring to? (just confused)

> **buzzingrobot said:**
> The "...non-GUI experience" bit eliminates most people.yep

> **monkeybrain20122 said:**
> You do arch because you want to poke inside a bit, not the same purpose for people who use Ubuntu. I mean, who the hell would go through all the hoops just to set up the OS if he just wants something that works? :) I set a side a 25 G partition for this kind of purpose and if thing break, or if it takes a week to figure out something before I can proceed, no prob. Ubuntu is the OS I use to get things done. :)

Meanwhile there are easy Arch distros such as Manjaro Last time tried it, liked it quite a bit until something upgraded and hosed the system. Had to reinstall,--but reinstalling Manjaro is rather painless comparing to reinstalling Arch :o

Sure Arch has the best wiki. But how did I install it while reading the wiki? A bit of a chicken and egg problem. I have no printer, I am not going to copy it by hand. I have two computers. One I was installing Arch on, the other was on Arch wiki. Otherwise you will have to read it on a phone (pain) or better, on a tablet. If you have only one computer and no gadget and no printer, like I was for a long time, then I don't know how to do it other than print the wiki from my neighbourhood internet cafe. :)Thing is, I'm one of those people that are sortof hybrids of what you describe...I do want something that just works but I was also very attracted by the ability to tweak and customize things to your liking and leaving bloat behind.  So I guess I am doomed to never be fully satisfied :P

> **vellon said:**
> Don't worry, that's been thought of.... :)  The elinks text-based browser is on the installation media/base system, so you just need to get an ethernet connection up and runninghaha I didn't know that, I guess that can help though probably not the most ideal scenario (have to constantly use elinks then get out to execute a command, then go back etc)

---

### Post by vellon on 2015-05-22
> **ubuntuman001 said:**
> True.  I do agree the arch install itself is not that bad as I've said earlier, compared to the post-install work.  Not a bad idea to just transfer the config files over from setup to setup.  And yes, ubuntu upgrades can be problematic.  Thing is, I do clean installs most of the time cause my post-install tweaking is so minimal.  Again, i'm not discounting arch or saying there's no point to it, just saying it's not for me.  About the arch community though, I will say I don't have much experience in the forums (never posted there) but I have read online about some members being hostile or unwelcoming (don't know if that's true or not).  Either way I've rarely seen any hostility in these forums, and I've been here since 2006.  I will say I find it kind of weird that to sign up on the arch forums you need a linux terminal to be able to return some code that lets you complete the signup process on the forums.  I think that's a bit excessive...what if you're curious about arch and want to explore the forums and ask questions but you happen to be on a windows comp at the time?  Doesn't make much sense to me...
The Arch community certainly expects you to have done your homework before asking for help. They first expect you to have worked through the appropriate Wiki, and then to post some useful info about the problem (logs, hardware info, what you have already tried, etc). If not, quite reasonably, you will be pointed to the Wiki to help yourself. This end result is fewer duplicate easy queries, and better quality technical replies/fewer random guesses than I have seen on other support boards. It is not the place for a chat, I'll give you that.

The sign-up process is an interesting one, and I am with Arch on this. If pasting a uname query on a terminal is too much like hard work, then Arch is not going to suit you, because you will be doing a whole lot more of that in the future.... It gets rid of the lightweights ;)


> **ubuntuman001 said:**
> what do you mean no distribution produces an iso matching those preferences, what are you referring to? (just confused)
I mean that I cannot download a ready-made Xubuntu or Lubuntu equivalent ISO with (all or even most of) the software I want, so I have to start with a minimal install of something and build up what I need. I may as well start from Arch as anything else in those circumstances.

> **ubuntuman001 said:**
> haha I didn't know that, I guess that can help though probably not the most ideal scenario (have to constantly use elinks then get out to execute a command, then go back etc)
Use two virtual terminals and flip between elinks and your install with Alt Fn keys

---

### Post by veddox on 2015-05-22
> You do arch because you want to poke inside a bit, not the same purpose  for people who use Ubuntu. I mean, who the hell would go through all the  hoops just to set up the OS if he just wants something that works? :smile:  I set a side a 25 G partition for this kind of purpose and if thing  break, or if it takes a week to figure out something before I can  proceed, no prob. Ubuntu is the OS I use to get things done. :smile:
Definitely agree with that. Having played around a little with Arch in the past, I really enjoyed the learning experience and the sense of total control you have over the system (once it's running). One of the things on my todo list is to set it up as another distro on my laptop - then I'd use Arch for programming (where I want the latest packages, not the outdated Ubuntu repos) and Ubuntu for "normal" work (where I need a stable system).

And the setup isn't that bad either, once you've done it a few times. The first time took me around three days, now I can do it in an afternoon.

---

