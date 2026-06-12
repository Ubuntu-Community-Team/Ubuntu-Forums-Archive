---
title: "Alternative to Linux Mint?"
date: 2009-05-03
forum: The Cafe
---

### Post by Jim_Rogers on 2009-05-03
The two things I really liked about Linux Mint were:

1. The extra (i.e., proprietary) stuff that installed automatically.

2. The ranking system for updates that ensured that I got relatively secure packages that would not break my system (Fedora always did that to me).

How much of that would I really miss if I switched to Ubuntu? Is there some automatic way (through a third party or otherwise) to easily get those proprietary things after an Ubuntu install?

Is taking all the updates (without ranking) dangerous in Ubuntu as I found them to be in Fedora?

Is there another distribution worth looking into?

Interested in any advice on the best alternative to Mint.

Thanks,

--Jim Rogers

---

### Post by Pasdar on 2009-05-03
I'd say Linux Mint is quite unique.

---

### Post by Screwdriver0815 on 2009-05-03
in Ubuntu you can use the medibuntu repo. It has the proprietary stuff too.

Updates are safe in Ubuntu when you do not activate the proposed repo.

---

### Post by gjoellee on 2009-05-03
To recommend you anything wisely we **_have_** to know_** your**_ needs...!

---

### Post by pastalavista on 2009-05-03
crunchbang linux

---

### Post by mwalimu54 on 2009-05-03
How much of that would I really miss if I switched to Ubuntu? Is there some automatic way (through a third party or otherwise) to easily get those proprietary things after an Ubuntu install?


Installing proprietary stuff in Ubuntu is relatively easy.  It's just a matter of installing a package through the Add/Remove Applications option.  You can either use the command line or graphic interface.  The exact details for installation through the graphic interface are:

1. click System/Administration/Software Sources

2. under the Ubuntu Software tab make sure the "Multiverse" repository is checked.

3. click Applications/Add Remove

4. Search for "Restricted Extras"

5. Select and install

6. Reboot

---

### Post by eragon100 on 2009-05-03
I would say regular ubuntu, because they are 95% identical, and ubuntu can install all the propietary codecs + flashplayer + fonts + java with one mouse click. (Go to add/remove and install "ubuntu-restricted-extras"), you will still be able to listen to music and watch videos :wink:

---

### Post by Jim_Rogers on 2009-05-03
> **Screwdriver0815 said:**
> in Ubuntu you can use the medibuntu repo. It has the proprietary stuff too.

Updates are safe in Ubuntu when you do not activate the proposed repo.

Thank you-- that's helpful.

Also, if I install Ubuntu, is it easy to upgrade my installation? With Mint they always recommended a clean install with each new version (although that's going to change soon).

That was a pain every six months.

In the old days, I remember that Debian didn't have an installer, but users said it didn't matter because once you did get it installed, you'd never have to do it again.

That certainly wasn't the case with Mint, does Ubuntu adhere to the old Debian "one install" philosophy?

--Jim

---

### Post by CraigPaleo on 2009-05-03
You could run this command in Ubuntu.
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by Vadi on 2009-05-03
Ubuntu + Medibuntu.

Really, Linux Mint does not offer anything ground-breaking.

---

### Post by Jim_Rogers on 2009-05-03
> **exploder said:**
> This guide explains everything.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Clem spoke out about something that was disturbing him very much. You or I could have easily done the same thing. Let's just leave it at that.

My question should not be construed as any type of rant against Clem.

I'm really asking about the best alternative.

The answers I've received are very helpful. I had no idea it was so easy to install the proprietary stuff by selecting a repository.

I think I'm going to try it.

Thanks all for the help.

--Jim

---

### Post by Screwdriver0815 on 2009-05-03
> **Jim_Rogers said:**
> Thank you-- that's helpful.

Also, if I install Ubuntu, is it easy to upgrade my installation? With Mint they always recommended a clean install with each new version (although that's going to change soon).

That was a pain every six months.

In the old days, I remember that Debian didn't have an installer, but users said it didn't matter because once you did get it installed, you'd never have to do it again.

That certainly wasn't the case with Mint, does Ubuntu adhere to the old Debian "one install" philosophy?

--Jim
you can upgrade the versions from the current installation if you want. In the Ubuntu-updating mechanism you can choose whether you want to get a message if there is a new version or a long term support version or not to get notified about new releases.
However I always do a new clean install with a new version because it only takes me 1 hour or so to get it the way I want it.

---

### Post by Delever on 2009-05-03
What about checking out Linux Mint, I heard it has things you need...

---

### Post by Jim_Rogers on 2009-05-03
> **Screwdriver0815 said:**
> you can upgrade the versions from the current installation if you want. In the Ubuntu-updating mechanism you can choose whether you want to get a message if there is a new version or a long term support version or not to get notified about new releases.
However I always do a new clean install with a new version because it only takes me 1 hour or so to get it the way I want it.

Thanks. It takes me a couple days to get things back to normal, and I'm always so busy at work that I've come to absolutely hate upgrade time.

I'm interested in LTS versions, but, for example, the LTS of Mint I'm using won't let me get OO.o 3, which has much better figure handling than 2.4 did.

So I want to upgrade as painlessly as possible!

--Jim

---

### Post by Jim_Rogers on 2009-05-03
> **Delever said:**
> What about checking out Linux Mint, I heard it has things you need...

It does, but sometimes one feels the need to explore alternatives. No sense in just using the same thing forever and not checking once in a while to see if there is something better out there.

I switched from Fedora to Mint about a year and a half ago because Fedora just wasn't working for me and Mint seemed to be trying to create just what I was looking for. Now I'm thinking about Ubuntu.

That's what open source is all about, and I take full advantage of it!

BTW, I'm also a fairly generous donor to whatever distribution I use, so I give back to whatever community works the best for me.

I think that, probably as of tomorrow, that will be the Ubuntu community!

--Jim

---

### Post by hanzomon4 on 2009-05-03
The rules of the forum prevent me from speaking my mind on the underlying issue of this thread. I will suggest however the perhaps you can just add the mint repos? By the way, we really can't help if you don't give a reason for switching. I mean if mint has what you need/want why stop using? Even if you don't have a reason, what do you like about mint? The menu, mint-install thingy, he theme... what?







Unpopular opinion attempting to break free... must restrain :-&

---

### Post by speedwell68 on 2009-05-03
> **Jim_Rogers said:**
> Thanks. It takes me a couple days to get things back to normal, and I'm always so busy at work that I've come to absolutely hate upgrade time.

I'm interested in LTS versions, but, for example, the LTS of Mint I'm using won't let me get OO.o 3, which has much better figure handling than 2.4 did.

So I want to upgrade as painlessly as possible!

--Jim

Get Ubuntu Tweak from GetDeb and use that to add the OpenOffice 3.0 repository.

---

### Post by aysiu on 2009-05-03
Please keep this thread on topic.

The OP asked for alternatives to Linux Mint. Stop drumming up all this business about politics, or I will start issuing infractions. The offending posts so far have just been moved to a closed thread.

---

### Post by SuperSonic4 on 2009-05-03
Thanks aysiu 

I would suggest installing ubuntu and enable the medibuntu repos. Without knowing what DE you want it is harder to recommend a distro. Mandriva and Chakra are good for KDE and ubuntu for gnome. Or you could try a *box

---

### Post by pbpersson on 2009-05-03
I was GOING to go with Mint originally.

However, it is my opinion that if you install the restricted-extras and the non-free-codecs you are so close to Mint that it didn't seem worth it to abandon Ubuntu and go to Mint

I have always thought Mint was just Ubuntu with a layer of "easy" added to make it more friendly.

I stayed with Ubuntu because it has a huge community and many people translates into more answers for problems.

---

### Post by Mehall on 2009-05-03
ubutnu-restricted-extras (or kubuntu-restricted-extras, or xubuntu-restricted-extras) and Medibuntu are all you really need. And while Ubuntu isn't quite as stability minded as Debian, it's certainly more stable than Fedora, though this means less new packages. PPA's sort that though, at the cost of some stability. (not much if you're careful)

If you're desperate to have the extras pre-installed, Crunchbang has this, and is fantastic, fast, minimal, and looks cool 8) Crunchbang doesn;t come with Open Office, but is easy enough to add. If you wait a week or so, Crunchbang 9.04.01 ISOs (well... #! 9.05 ;)) should be out, at current you can install 8.10.02 and upgrade, or install Ubuntu minimal and then use a simple bash script you can wget to turn it into Crunchbang 9.04.01

---

### Post by Jim_Rogers on 2009-05-03
OK, I was just asking about the closest alternative to Mint (a question that is independent of my particular needs), but since I've gotten so many helpful responses that included questions probing my particular needs, I'll elaborate by way of a bit of my history (which, if you'd like to skip, is contained between the lines):

---------------------------------------------------
I have no formal computer training. I began dabbling in Linux in 1999. Switched to full-time Linux usage in 2002 with RedHat 7.2.

I was always a DOS user and was a very late Windows adapter (1998 ) because I really liked using the DOS command line.

Because of my love of the command line and my desire to learn Linux more deeply, I used RedHat with the Black Box window manager and no desktop for three years. No Midnight Commander, nothing. Just the command line for everything for three years.

Was thrilled when Fedora was formed as I felt it was the community version of Red Hat that would be like an rpt Debian. Felt I had learned enough at the command line and started using Gnome at Fedora 3.

Hated upgrading Fedora. Sometimes there was this thing called the "Fedora Frog" that would help the setup with proprietary packages, but it was not always available. When it was not, upgrading took me several days.

I was becoming increasingly busy at work as the career took off and much less interested in messing with computers. I was starting to want something that "just worked." Was scared of Ubuntu/Debian because I had spent so much time learning yum at the command line, I didn't want to go through the same thing with apt.

Upgraded from Fedora 7 to Fedora 8 and it was a nightmare. No frog and when I got done, several things very important to me were completely broken. I was virtually unable to work for two weeks. The main response from the Fedora forums was "Hey, Fedora is a project, not a product. You don't want to mess around with stuff? Then use something else!" Gee thanks, guys.

This bad experience overcame my nervousness about joining the Ubuntu world. I chose Mint because it seemed like it was the equivalent of Fedora+Frog. It was! And with synaptic, I didn't even need to bother with the commend line as it was easy and intuitive. In fact, I've barely used the commend line in the last year and a half.

I give all this history to form a complete story and so you understand my technical ability (which is a bit weird-- some very technical things I know at great depth, while some basic things I know little about).
----------------------------------------------------------

Everything with Mint is fine, but they strongly recommend a fresh install at each upgrade. This is not really compatible with my work schedule as I do a lot of customization of my installation and have little time for recreating that every six months.

I thought of not upgrading (using the LTS for three years), but it seems if you do that you're stuck with old versions of software. E.g., my Evolution is pretty buggy and I can't get the newer versions without upgrading Gnome which means I have to upgrade everything.

It looks to me that Ubuntu has the ability to upgrade without reinstall while Mint is only in the development stage for that. I need to upgrade Mint this week because I have a project due June 15th and I really want OO.o 3 and a newer Evolution.

Before I upgraded Mint this week, I thought I'd check out the other possibilities. And here we are now.

I'd never heard of crunchbang, but I find it a bit intriguing as it hearkens me back to my black box days.

But really what I would love to have is a distribution where I can install it once, easily get the Mint extras, do my customizations, and then only perform upgrades (no fresh installs). I was always under the impression that that was how it was with Debian, so I was hoping it would be the case with Ubuntu.

That way I can have reasonably recent releases of the software I use with a minimum amount of hassling with upgrades.

These days my computer is a work-horse, not a hobby. I just want it to work so I can work.

I'm strongly leaning toward Ubuntu at this time as (per all of your previous responses) it looks like Ubuntu has what I want AND I've been reading about how Jaunty is absolutely killer.

See? No politics. While I do have strong feelings about Clem's post, I'm not dealing with that here. Just trying to decide on my next distribution.

I really appreciate everyone's input.

--Jim

---

### Post by SuperSonic4 on 2009-05-03
If you want the ultimate in stability go with debian but it will be at the cost of new packages

---

### Post by hanzomon4 on 2009-05-03
Don't use Ubuntu... it's does not believe in rolling releases/ seriously lets lighten up folks :)

 Give Arch Linux a try or Debian Unstable? Basically you can get everything mint has in any distro but what you really want, that you can't get in every distro, is rolling releases. I hear Arch is the best for that sort of thing.

---

### Post by Mehall on 2009-05-03
> **SuperSonic4 said:**
> If you want the ultimate in stability go with debian but it will be at the cost of new packages

Or use Debian Testing.

Fairly stable, and rolling release style, so never upgrading.

(ok, ok, when they do release the new stable, you need to edit you sources.list to make it for the new testing, but that's simple)

EDIT: at guy above me: I would NOT advise using Debian Unstable or experimental (Debian sid) on a production, workhorse machine. I believe you probably meant Debian testing

---

### Post by hanzomon4 on 2009-05-03
Yeah I get them confused

---

### Post by pbpersson on 2009-05-03
If you read through several of the threads on this forum relating to upgrades to Jaunty (9.04) you will discover that WHILE you can do an upgrade, a fresh install is still best.

I am toying with a process in the back of my mind that would allow me to get a snapshot of what I have installed in my current OS, compare it with a package manifest in the new version, and then create a re-install script that you can just run after a fresh install to put all your packages back onto your system.

This would just include packages without dependencies and would rely on apt to install the new dependencies for the new packages.

However, it is just a concept at this time.

---

### Post by Seventh Reign on 2009-05-03
> **SuperSonic4 said:**
> If you want the ultimate in stability go with debian but it will be at the cost of new packages

Debian (Stable) crashes more than Karmic for me.

Another alternative is Ultimate .. But I'd stick with Mint .. I love that menu.  I know it can be installed in Ubuntu but it never seems to work as well.

---

### Post by HappinessNow on 2009-05-03
I am trying hard to think of a Linux alternative to Linux Mint and can think of none, but I can instantly think of a BSD alternative to Linux Mint:

PC-BSD

I hope this helps you out.

---

### Post by Jim_Rogers on 2009-05-03
Thanks to all for the suggestions so far.

Arch Linux sounds perfect, but it seems to have it's own package system and I'm a bit nervous about moving out of the apt world since the support community is so large (I like finding solutions to problems where I can just copy an apt-get line, run it and it's fixed!). Would I have that kind of support in Arch?

Debian testing might be the ticket. Is there a good installer now? It used to be very difficult to get that first install done.

As a more general question, why don't all distributions use (or at least have the option for) rolling releases?

Don't you guys find it a pain to upgrade every six months? Do you not do that much customization? Am I missing some trick that everyone else uses to upgrade easily?

--Jim

---

### Post by HappinessNow on 2009-05-03
> **Jim_Rogers said:**
> Thanks to all for the suggestions so far.

Arch Linux sounds perfect, but it seems to have it's own package system and I'm a bit nervous about moving out of the apt world since the support community is so large (I like finding solutions to problems where I can just copy an apt-get line, run it and it's fixed!). Would I have that kind of support in Arch?

Debian testing might be the ticket. Is there a good installer now? It used to be very difficult to get that first install done.

As a more general question, why don't all distributions use (or at least have the option for) rolling releases?

Don't you guys find it a pain to upgrade every six months? Do you not do that much customization? Am I missing some trick that everyone else uses to upgrade easily?

--Jim

Again Jim, I can only highly recommend PC-BSD as easily upgradable alternative. I was able to upgrade from the first release to the most recent with No breakage what so ever. Give it a try, if you like Gnome or KDE PC-BSD may be what you seek.

---

### Post by pastalavista on 2009-05-03
> **Jim_Rogers said:**
> 

Don't you guys find it a pain to upgrade every six months? Do you not do that much customization? Am I missing some trick that everyone else uses to upgrade easily?

--Jim

If you create a /home partition when you first install, when you reinstall, leave the ?home partition as is and only reformat the / directory. All your settings will be maintained on the new install. You'll just have to reinstall your applications.. and all their settings will be kept too.

---

### Post by Jim_Rogers on 2009-05-03
> **&#20170 said:**
> Again Jim, I can only highly recommend PC-BSD as easily upgradable alternative. I was able to upgrade from the first release to the most recent with No breakage what so ever. Give it a try, if you like Gnome or KDE PC-BSD may be what you seek.

Thanks. To be perfectly honest, I know almost nothing about BSD. I'll look into it more, but what package system does it use? Would I be able to get help from the Ubuntu community? Or, is the BSD support community large?

I'm interested, but nervous. BSD seems very different, and I want to be as mainstream as possible (for support!).

--Jim

---

### Post by Jim_Rogers on 2009-05-03
> **pastalavista said:**
> If you create a /home partition when you first install, when you reinstall, leave the ?home partition as is and only reformat the / directory. All your settings will be maintained on the new install. You'll just have to reinstall your applications.. and all their settings will be kept too.

That's true, but Mint doesn't have LVM, so that discouraged me from doing that. Does Ubuntu have LVM? Maybe I should just bite the bullet and do it anyway. In Fedora it was a great solution to this problem (and LVM made it even better!).

--Jim

---

### Post by &#32 Greg on 2009-05-03
If you're willing to give Arch a try, it's excellent. Just follow the documentation, and you'll have everything you need. Even compiling from source is a breeze with the Arch Build Service, and Pacman is a great package manager; yaourt does the trick if you need things outside the standard bunch of repositories. You get a fast, personalized system with everything you need and want- no more, no less.

Very different from Linux Mint, though.

---

### Post by Jim_Rogers on 2009-05-03
> **  Greg said:**
> If you're willing to give Arch a try, it's excellent. Just follow the documentation, and you'll have everything you need. Even compiling from source is a breeze with the Arch Build Service, and Pacman is a great package manager; yaourt does the trick if you need things outside the standard bunch of repositories. You get a fast, personalized system with everything you need and want- no more, no less.

Very different from Linux Mint, though.

At this point I'm really considering anything. From your (and others) posts, Arch sounds very interesting. I love the idea of customization and rolling releases.

Just nervous about the size and helpfulness of the support community. I'm not a power user, so I depend heavily on the support community.

That's one reason why I set up monthly donations to any distribution I use.

--Jim

---

### Post by &#32 Greg on 2009-05-03
> **Jim_Rogers said:**
> At this point I'm really considering anything. From your (and others) posts, Arch sounds very interesting. I love the idea of customization and rolling releases.

Just nervous about the size and helpfulness of the support community. I'm not a power user, so I depend heavily on the support community.

That's one reason why I set up monthly donations to any distribution I use.

--Jim

Bigger!=Better, per say. The Arch support community, while not as large as the *buntus, is well established and dedicated. A higher percent of Arch users have a better understanding of Linux than with the *buntus. That's not to take anything away from the excellent support found here, but... well, I think you get what I mean.

The wiki is also excellent.

---

### Post by Jim_Rogers on 2009-05-03
> **  Greg said:**
> Bigger!=Better, per say. The Arch support community, while not as large as the *buntus, is well established and dedicated. A higher percent of Arch users have a better understanding of Linux than with the *buntus. That's not to take anything away from the excellent support found here, but... well, I think you get what I mean.

The wiki is also excellent.

I hear you and your right. I guess one reason I consider the Ubuntu community to be good by virtue of its size is that I virtually always find the answers to my questions without ever having to post.

I generally do a quick Google and the answer to my question is in the first few hits.

For smaller distributions, I have a picture in my head of having to post every stupid little problem I have to a forum and wait around for someone to answer. My questions are often low-level enough that I feel like I'm bothering groups composed of power users.

But I could have a distorted view on this, and I'll have to say that Arch seems to fit the description of what I'm looking for.

Right now I think I'll research Arch, BSD, and Debian Testing.

Again, I really do appreciate all suggestions here, even ones I did not respond to.

--Jim

---

### Post by exploder on 2009-05-03
Jim_Rogers, If you are interested in a rolling release you might want to look at PCLinuxOS. Texstar does excellent work and the built in Make LiveCD tool makes it possible to have a Live/Install CD of your perfectly set up system.

Mepis is also a very good choice. Mepis is more or less a rolling release now that there is a community repo. I know for a fact that the Mepis community will work with you to resolve issues until they are fixed.

I do not know if you are a KDE fan but these two distributions are outstanding for support and quality.

---

### Post by Jim_Rogers on 2009-05-03
BTW-- I realize I've been writing "rpt" instead of "rpm" when I was talking about RedHat/Fedora.

I just got tenure this month, so my credentials went before the college Re-appointment Promotion and Tenure (RPT) committee.

My life has revolved around RPT this year, so I got them confused!

--Jim

---

### Post by drawkcab on 2009-05-03
[http://distrowatch.com/](http://distrowatch.com/)

Shop around here ^^^ it should help you decide!

---

### Post by Scotty Bones on 2009-05-04
If you like the menu in mint and would like a replacement (given you decided to stay with ubuntu as i have), try the project it was forked from, Ubuntu System Panel.

---

