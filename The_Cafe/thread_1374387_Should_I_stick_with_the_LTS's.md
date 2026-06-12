---
title: "Should I stick with the LTS's?"
date: 2010-01-06
forum: The Cafe
---

### Post by ubudog on 2010-01-06
Should I only use the LTS releases?

---

### Post by Chronon on 2010-01-06
I'm not going to tell you what you should do.  I upgrade (or clean install) to each new release.  I enjoy seeing the progress with each new release and none of my machines are mission-critical enough to really cause a crisis if I needed to wipe my root partition and reinstall a previous version.  I have no idea how you use your machines or how much you value new features versus stability.  Therefore, I can't possibly assess which is better for you.

---

### Post by Dark Aspect on 2010-01-06
> **ubudog said:**
> Should I only use the LTS releases?

Depends,

If you can backup your home folder easily than I would do a clean install every six months. Of course you have to reinstall packages that way but that not really that big of a deal if you on a broadband connection IMO.

However, if you have no way to backup your home folder or its too big to backup and you’re on a slow internet connection than I would use an LTS.

And if you think the idea of reinstalling an OS every six months is stupid and ridiculous than I would use [Arch]("http://www.archlinux.org/"). Be warned however, Arch will eat you alive if your idea operating system is one that has a GUI after installation.

---

### Post by slakkie on 2010-01-06
> **Dark Aspect said:**
> Depends,

If you can backup your home folder easily than I would do a clean install every six months. Of course you have to reinstall packages that way but that not really that big of a deal if you on a broadband connection IMO.

And if you think the idea of reinstalling an OS every six months is stupid and ridiculous than I would use [Arch]("http://www.archlinux.org/"). Be warned however, Arch will eat you alive if your idea operating system is one that has a GUI after installation.

Non-LTS releases are supported for 18 months, you don't have to upgrade every six months. 

Use LTS or don't use LTS, it doesn't really matter :)

---

### Post by Xbehave on 2010-01-06
Should you?

It depends on where in the stability vs performance+current features line you lie?

---

### Post by alwayshere on 2010-01-06
For me lts 8.04 is stable and can do everything i want to do  but I have also used others versions but as i have found the newer the version the more bugs there are to sort out so i guess it comes down to if you want a o.s to use or an o.s to fix which if ya into puzzles and stuff would be just the thing for ya ,i have to admit  I have installed a latest version just for something to play about with before.

---

### Post by ubudog on 2010-01-06
Thanks for the replies, think I will just do an upgrade every 6 months with Update Manager.  Thanks everyone!

---

### Post by Hwæt on 2010-01-06
> **ubudog said:**
> Thanks for the replies, think I will just do an upgrade every 6 months with Update Manager.  Thanks everyone!

Whoa! Bad move. Ubuntu's updater is flaky at best. It's recommended to do a clean install when upgrading to a new version. Remember to back-up all of your important files, though!

Good luck.

---

### Post by ubudog on 2010-01-06
> **Hwæt said:**
> Whoa! Bad move. Ubuntu's updater is flaky at best. It's recommended to do a clean install when upgrading to a new version. Remember to back-up all of your important files, though!

Good luck.

OK, guess I'll just backup my home directory and then do a clean install.  Thanks for the help!

---

### Post by slakkie on 2010-01-06
> **Hwæt said:**
> Whoa! Bad move. Ubuntu's updater is flaky at best. It's recommended to do a clean install when upgrading to a new version. Remember to back-up all of your important files, though!

Good luck.

It is NOT recommended to do a clean install. Please never, ever, ever, ever say that again.

---

### Post by ubudog on 2010-01-06
[QUOTE=]Whoa! Bad move. Ubuntu's updater is flaky at best. It's recommended to do a clean install when upgrading to a new version. Remember to back-up all of your important files, though!

Good luck.[/QUOTE]

[QUOTE=]It is NOT recommended to do a clean install. Please never, ever, ever, ever say that again.[/QUOTE]


Kinda confused....:-s

---

### Post by Hwæt on 2010-01-06
> **slakkie said:**
> It is NOT recommended to do a clean install. Please never, ever, ever, ever say that again.

How on earth is updating the entire OS through the update-manager better? A quick forum search will show you a ton of topics about people having problems after updating from the update-manager. 

Plus, with a clean install, you can make a separate partition, test it out for a few days, and if you don't like it, delete it, resize the original Ubuntu partition, and go back to normal. 

(Note: This is not done by default! You would have to do this yourself by fiddling around with the partitions during set-up.)

Show me an update manager that can do **that** and I'll use it.

---

### Post by slakkie on 2010-01-06
> **ubudog said:**
> Kinda confused....:-s

Well, he's misinformed.. 

[http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/)

An upgrade is perfectly doable, workable and can be done on multiple ways. Ubuntu has its own upgrader (update-manager package) which updates your machine without too much user-interaction. You can also do command line upgrades with another application (provided by update-manager-core) and/or upgrade via the proven method Debian uses. 

A clean install is, too me, a last-resort fix.

---

### Post by markinf on 2010-01-06
> **slakkie said:**
> It is NOT recommended to do a clean install. Please never, ever, ever, ever say that again.

why then ubuntu keeps breaking in all my attempts to upgrade.
Oh yeah, I tried on several hardwares. Notebook, Desktop, Netbook, WorkStation.

---

### Post by slakkie on 2010-01-06
> **Hwæt said:**
> How on earth is updating the entire OS through the update-manager better? A quick forum search will show you a ton of topics about people having problems after updating from the update-manager. 


Read the blog post :)

> 
Plus, with a clean install, you can make a separate partition, test it out for a few days, and if you don't like it, delete it, resize the original Ubuntu partition, and go back to normal. 


Clonezilla, backup your OS prior to upgrading, upgrade, test it, do not like it? Restore the backup. Backing up/restoring takes 10-15 minutes with clonezilla. 

> 
Show me an update manager that can do **that** and I'll use it.

An update manager doesn't need to partition your OS, you have already done it. If you are not happy about your partitioning scheme, then yes, I can understand a clean install, but even that can be done with an existing install.

---

### Post by Hwæt on 2010-01-06
> **slakkie said:**
> Well, he's misinformed.. 

[http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/)

That's **your** blog! That holds so much more weight than a forum full of topics where people are asking for help after upgrading!

---

### Post by Hwæt on 2010-01-06
> **slakkie said:**
> Clonezilla, backup your OS prior to upgrading, upgrade, test it, do not like it? Restore the backup. Backing up/restoring takes 10-15 minutes with clonezilla.

Assuming that you already know how to use the program. Partitioning in the installer is much simpler.

> 
An update manager doesn't need to partition your OS, you have already done it.

You seem to forget about the fact that Jaunty and Karmic use Ext4 by default, and that upgrading from a previous version would leave you with the obsolete Ext3.

---

### Post by NoaHall on 2010-01-06
> **Hwæt said:**
> Assuming that you already know how to use the program. Partitioning in the installer is much simpler.



You seem to forget about the fact that Jaunty and Karmic use Ext4 by default, and that upgrading from a previous version would leave you with the obsolete Ext3.

It's no-where near obsolete. Don't call it that.

---

### Post by Hwæt on 2010-01-06
> **NoaHall said:**
> It's no-where near obsolete. Don't call it that.

Have you seen the benchmarks?

---

### Post by slakkie on 2010-01-06
> **Hwæt said:**
> That's **your** blog! That holds so much more weight than a forum full of topics where people are asking for help after upgrading!

That is your argument to say that clean installs are better then upgrading? Tell that to the hours I spend on upgrading Ubuntu from 4.10 to 8.04. Yes, that are all the upgrades that I have done (excluding the upgrades from 8.04 to 10.04). Plus my Debian stable to unstable upgrades. 

And look on these forums for installations problems and please tell me how many topics you find.

But you don't have to believe me:
[http://journal.dedasys.com/2008/05/19/ubuntu-update-dont-reinstall](http://journal.dedasys.com/2008/05/19/ubuntu-update-dont-reinstall)

---

### Post by NoaHall on 2010-01-06
> **Hwæt said:**
> Have you seen the benchmarks?

It's still not obsolete.

---

### Post by slakkie on 2010-01-06
> **Hwæt said:**
> Assuming that you already know how to use the program. Partitioning in the installer is much simpler.



You seem to forget about the fact that Jaunty and Karmic use Ext4 by default, and that upgrading from a previous version would leave you with the obsolete Ext3.

ext3 is not obsolete and you can convert your disk from ext3 to ext4. The exercise is quite trivial. You will have part of your disk in ext3 mode and parts in ext4. Doing a clean install for ext4 is a valid reason. But it doesn't make your statement more true.

And Jaunty did support ext4, but the default was still ext3.

---

### Post by Shippou on 2010-01-06
Actually, it really depends on you.

For the most part, the latest *stable* release is fine.

I do think LTSs are best in mission-critical applications, or if you want long term support.

Personally, I prefer the latest release. Not the beta nor the alpha, but the latest public release. The only beta OS I have is Win7.

If you want a bleeding-edge Linux distro, then I suggest you check Fedora. Or Lucid Lynx.

---

### Post by Hwæt on 2010-01-06
>  Tell that to the hours I spend on upgrading Ubuntu from 4.10 to 8.04. Yes, that are all the upgrades that I have done. Plus my Debian stable to unstable upgrades. 

4.10 to 8.04 is a large leap, and you spent years on customizing that. I'm talking more about 8.10 -> 9.10, for example.

> 
And look on these forums for installations problems and please tell me how many topics you find.

Most installation problems have to deal with drivers not working because the hardware is poorly supported on their machine. Whereas upgrading problems are more about programs crashing frequently after an install. Almost always, someone in those topics suggests doing a clean install, and a lot of the time, that works! Find me a topic where someone has suggested updating as a solution for an installation problem.

---

### Post by Hwæt on 2010-01-06
> **slakkie said:**
> ext3 is not obsolete and you can convert your disk from ext3 to ext4. The exercise is quite trivial.

I did not know that this was possible at the time of that post. Surely there is quite a risk to upgrading in that manner, right?

Forgive me if I'm wrong here, but wouldn't trying to revert that unholy hybrid be nearly impossible if you encounter a major problem?

> 
And Jaunty did support ext4, but the default was still ext3.

Was it? Sorry about that, it's been a while since I've used Jaunty.

---

### Post by slakkie on 2010-01-06
> **Hwæt said:**
> 4.10 to 8.04 is a large leap, and you spent years on customizing that. I'm talking more about 8.10 -> 9.10, for example.


I can do the 4.10 to 10.04 upgrades for you in a day.. Fully working. I wrote the whole EOLupgrade guide, I think I can say I have some experience in upgrading Ubuntu, understand how apt works, and how packages are upgraded (or not). 

>  Find me a topic where someone has suggested updating as a solution for an installation problem.

Can you read Dutch? The website fok.nl had kernel panics at Intrepid, an upgrade to Jaunty fixed it. They now run Karmic. They came from 6.10 (edgy?) and upgraded in one day. Without loss of data.

> **Hwæt said:**
> I did not know that this was possible at the time of that post. Surely there is quite a risk to upgrading in that manner, right?


Changing anything on a system could cause downtime due to unexpected issues. That is why you backup your important data. In case things do go wrong you can go back. I did it several times during the karmic development release. Didn't go wrong once, but that doesn't mean some people could have issues. Ext4 had a bug with big files (>1 GB) back then, perhaps it is still present. New software brings change and change could mean breakage.

> 
Forgive me if I'm wrong here, but wouldn't trying to revert that unholy hybrid be nearly impossible if you encounter a major problem?


Your data is as important as the amount of backups that you have. Yes, you have a problem when it happens. But with a backup you can always go back, unless your backup got corrupted (painful).

> 
Was it? Sorry about that, it's been a while since I've used Jaunty.

I installed it a couple of days ago for my girlfriend, forgot to use ext4.. :{

---

### Post by ubudog on 2010-01-06
Oh well, thanks for all the help. ;)

---

### Post by user1397 on 2010-01-06
Ubuntu's upgrade system is meant to work and be used by all.  Yes, sometimes it doesn't work properly, but I think that's the minority of cases (who complains about a clean upgrade?).

I would recommend actually having a separate /home partition and trying the upgrade, and if all goes bad then do a clean reinstall but just** don't** mount your /home partition during the reinstall.

Oh and, if you have the patience, don't upgrade for at least a month till after it's released to prevent those initial release bugs to, well, bug you.

---

### Post by slakkie on 2010-01-06
> **ubudog said:**
> Oh well, thanks for all the help. ;)

Sorry for the heated discussion ;)

---

### Post by mamamia88 on 2010-01-06
as much as i would love to stick to lts i know i will be tempted and install the latest eventually anyway.

---

### Post by chessnerd on 2010-01-06
There are two things to consider: your needs (1) and your amount of free time (2).

If you need an OS that is going to be stable and supported for a while, then an LTS is perfect.

If you need an OS that is at the cutting edge of technology and is going to have the newest applications, then the normal releases are the way to go. This is especially important if you have newer hardware.

The amount of time have to you spend on the computer matters as well. If you don't have the time to completely back-up your system and do a reinstall every six months then an LTS would be better.

It usually takes me 20-30 minutes do download/burn the ISO, 5 minutes to do a backup, and 45-60 minutes to install. That's about 70-100 minutes. If you can afford to carve 2 hours out of your schedule every six months, great. If not, the LTS is for you.

When Lucid comes out, I'm going to upgrade my desktop and leave it as Lucid until Ubuntu 12.04 Pearly Penguin (Like the name? Just came up with it. :P) On the other hand, I'll probably upgrade my laptop every six months so that I'm always using the latest applications and drivers (especially since it has an N wireless card).

Whatever you decide, I wish you the best of luck and hope that we both stick with Linux long enough to use Pearly. It'll be a great OS, I'm sure of it!

---

### Post by plurworldinc on 2010-01-06
What I have always found a great rule of thumb for me is, LTS is perfect for you home desktop and any main systems you want to remain stable at all cost.

  But for you laptop, netbook and MIDs, go for the latest and greatest.....:popcorn:

---

### Post by ssulaco on 2010-01-07
> **ubudog said:**
> Should I only use the LTS releases?
 Hardy (which is an LTS) is very solid,I have had no issues,Jaunty which is not an LTS gave me a few problems,I decided against upgrading to Karmic,and will wait for Lucid which is the next LTS.
Should you use LTS?if you want stability and 3 year support cycle,I would say yes,go LTS
[http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle)

---

### Post by cariboo on 2010-01-07
If you do keep on using Hardy, you can upgrade to Lucid when it comes out in April. The LTS editions are the only versions you can do a direct upgrade to without having to go through upgrading from one version to the next.

---

### Post by Queue29 on 2010-01-07
> **Hwæt said:**
> Have you seen the benchmarks?

Have you seen the documentation regarding known issues with file corruption on any file larger than 512 MiB?

---

### Post by Warpnow on 2010-01-07
There's nothing wrong this using the update manager. For each problem you find with it (which are few overrepresented because everyone who has a problem makes a thread, not everyone who doesn't have a problem), there are about 10 million things that can go wrong on a clean install.

Resizing a partition alone can -easily- result in data loss. If you create a new partition for each ubuntu release you are bound to eventually experience this loss. If you do a clean install, that's great, but you're going to need some kind of backup solution, otherwise its not safer, its less safe..

No

---

### Post by adeypoop on 2010-01-07
> **Warpnow said:**
> 
Resizing a partition alone can -easily- result in data loss. If you create a new partition for each ubuntu release you are bound to eventually experience this loss. If you do a clean install, that's great, but you're going to need some kind of backup solution, otherwise its not safer, its less safe..
No

I agree. it sounds risky creating and deleting partitions for every install.

My own **personal **recommendations are this, yes stick to LTS (unless you see a release that is worth upgrading for or are really tempted by. I upgraded from Hardy to Karmic because the new Intel drivers were a good reason for me). One thing that did annoy me a little on Hardy was some of the applications seemed very old though. 

Incidently on the upgrade versus clean install debate I am very much on the clean install side. This way you can try the distro as a live CD and make sure things work and you like the look of it before installing.  For me its not a problem to reinstall software that I still want to use, and a good chance to get the system cleaned up and purged from things I maybe installed and didn't like.

Whatever you choose won't be the wrong desicion. Have fun with Ubuntu :P

---

### Post by Khakilang on 2010-01-07
If it ain't broke why fix it or change.

---

### Post by XubuRoxMySox on 2010-01-07
I too would stick with LTS versions on a mission-critical 'puter. And while I'm sure that upgrading is fine for lots of people, I find just too many threads in these forums that describe how an upgrade borked someone's system.

Y'know that "Computer Janitor" thing? It cleans away old packages that you don't need and, according to its description in Synaptic, "makes your OS more like a fresh install." Which kinda tells me that a fresh install is more desirable.

I've tried both (I just started with Linux in March of last year, so I'm still officially a newbie I guess) and find the fresh installation simple and easy and fast. Last time I partitioned my hard drive like this:

[COLOR="Navy"]10 gigs for "**/**" (that's more than enough room for the "guts" of the system and all the programs I use)

1 gig for "**swap**" (2X my 'puter's RAM)

All the rest "**/home**" (music, pics, documents, videos, e-mail settings and mailboxes, favorites, personal stuff).[/COLOR]

When I do my fresh installation, I choose "manual" when the Partitioner starts up and *un-check* the "format this partition" box. This installs the new OS and leaves all my settings and stuff alone. I lose *programs*, but when they are re-installed through Synaptic, bingo! Firefox already has my extensions and all my bookmarks are there! Thunderbird is already configured for my e-mail, my Address Book is intact as before, and even all my saved e-mail messages and folders are right there! Try *that* with Windows!

**That doesn't mean you should try this without backing up everything you want to save!!** Stuff can still happen. 

But it's pretty amazing that you can completely re-install an entire OS and still keep all that stuff. What time saver!

It's so easy even a dixiedancer can do it! And I think it has an advantage over upgrading, since you don't have to use a "janitor" to "make" it "more like" a fresh install.

-Robin

---

### Post by Dragonbite on 2010-01-07
> **ubudog said:**
> Should I only use the LTS releases?

For my laptop, where I am managing things, I probably will keep updating it about every year.  I have multiple hard drives, so I generally have one I can update with and then another, possibly LTS, to do my "steady" work.

For the desktop that everybody uses, I plan on sticking with LTS releases because they are not so keen on things changing all of the time.

It all depends on how "customized" you make your system or have ot modify it to get it the way you want, and weigh that against the "latest and greatest" version of applications.

---

### Post by BrokenKingpin on 2010-01-07
I used to install every release, but once the next LTS is released I am sticking with the LTS releases. I like no features, but not at the cost of stability.

---

### Post by snowpine on 2010-01-07
I recommend a fresh reinstall every 6 months if you want the full Ubuntu experience.

I would not personally choose Ubuntu for a situation where stability is the #1 goal, therefore the LTS releases are meaningless to me. 

Your Mileage May Vary, therefore I did not vote in your poll. ;)

---

### Post by MasterNetra on 2010-01-07
My 2 cents, If you want the lastest from Ubuntu then every release it should be. However if you want to hang on to your system for as long as you can then LTS is the way to go. Its all about preference really.

---

### Post by sanderella on 2010-01-07
> **BrokenKingpin said:**
> I used to install every release, but once the next LTS is released I am sticking with the LTS releases. I like no features, but not at the cost of stability.

Me too. I always say that, but when the new releases come I always break my rule and upgrade.  Duuhh:( am I a nerd or what?

---

