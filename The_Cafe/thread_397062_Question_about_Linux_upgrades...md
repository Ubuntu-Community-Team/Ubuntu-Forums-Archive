---
title: "Question about Linux upgrades.."
date: 2007-03-30
forum: The Cafe
---

### Post by latebeat on 2007-03-30
Hey guys,

I have a simple and hopefully not too dumb question for you :)

Say I've got dapper installed and I update my system with apt-get to all the latest software and patches and someone else has a new edgy install again updated to the latest patches why the systems aren't gonna be the same since both are updated to the latest software and patches? I mean what is the thing that differentiates the set-ups and the releases?

I'm sorry if the question is too naive but I'm new to linux and coming from windows the answer is not obvious to me. I mean windows 98 will never become windows 2000 with updates from microsoft because they are inherently different but what about Linux releases? Aren't all things the same with just different version numbers ? So why won't I be able to have a fully updated system (say edgy or feisty fawn?) when starting from dapper just by apt-get update or distupgrade?

Thanks :)
l8bit

---

### Post by teaker1s on 2007-03-30
your sources list will dictate what updates you get, if you wish to dist-upgrade then you will need to alter sources and correctly dist-upgrade to avoid disaster.
if you find your ubuntu is doing all you want and there are no new features you must have-I'd advise not upgrading and risking breaking it

---

### Post by mips on 2007-03-30
> **latebeat said:**
> So why won't I be able to have a fully updated system (say edgy or feisty fawn?) when starting from dapper just by apt-get update or distupgrade?


You will have a fully updated system if you use thr distribution upgrade feature. You have to change your sources list file to use the Edgy repositories if you are currently using Dapper. Once the sources list file is updated you can dist upgrade to Edgy. From Edgy you can do the same to get to Feisty.

But keep in mind that the above will require a lot of bandwidth. I prefer to simply download the latest release and burn it to cd and then do a fresh install. If you keep /home on a seperate partition it is very easy to backup your stuff and start fresh.

---

### Post by teaker1s on 2007-03-30
dist upgrade could also be done from cd by adding cd as source:lolflag:

---

### Post by use a name on 2007-03-30
Ow, that's a nice one!

---

### Post by latebeat on 2007-03-30
> **mips said:**
> You will have a fully updated system if you use thr distribution upgrade feature. You have to change your sources list file to use the Edgy repositories if you are currently using Dapper. Once the sources list file is updated you can dist upgrade to Edgy. From Edgy you can do the same to get to Feisty.

But keep in mind that the above will require a lot of bandwidth. I prefer to simply download the latest release and burn it to cd and then do a fresh install. If you keep /home on a seperate partition it is very easy to backup your stuff and start fresh.

1.So upgrading to a new release just with apt-get can be done then. That's good :)
The whole point is so that I won't have to do a fresh install every 6 months I guess :)

2. So when u have home in a separate partition and u do a fresh install everything works as before?
What if some application changes that way it saves their settings or their configuration files and u just have ur config files from a previous release?

---

### Post by prizrak on 2007-03-30
There is no need to change your sources if you wanna go to Edgy from Dapper, you just invoke the update-manager in CLI with a special argument (can't remember what it is). 

latebeat,
1) Yes you can upgrade all the way to current development version from any version of Ubuntu (tho going to the dev version will require you to change your sources manually). 

2) /home is where ALL of your settings are kept. Bookmarks, e-mail, how you like to view your folders so and so forth. If you reinstall without wiping your /home you will be back to what you had before. There is a problem with it however, sometimes you may confuse the program if the newer version doesn't use the same way of storing preferences. All your files are still gonna be intact though so not THAT big of a deal. 

As far as updating and dist-upgrading goes the two are different. Once the version has been releazed it will not get anything but security updates (actually it's about 2 months before that it is frozen but you still get new software in once in a while). So a fully updated Dapper and fully updated Edgy are two different things with different versions of software. Dist upgrade is basically same as a fresh install, it does more or less the same thing while keeping your settings. Funnily enough an upgrade from Dapper to Edgy worked well for me but a fresh install did not :)

---

### Post by Mateo on 2007-03-30
I wouldn't advice a seperate home partition as it adds up to a lot of wasted space.

---

### Post by prizrak on 2007-03-30
> **Mateo said:**
> I wouldn't advice a seperate home partition as it adds up to a lot of wasted space.
Please don't spread misinformation. As it stands I have a 64MB /boot 4GB / and 68GB /home and a 1gig swap (for a total of 80 marketing gigs). I only have about a gig unused on / and bunch of free space on /home. Typical Ubuntu install won't take more than 3GB of your drive. So right now I'm "wasting" about a 1.5 DVD rips worth of space. Sure it could be a concern on an older system with smaller drive but not on anything even remotely modern (and by that I mean just about anything from the past 4 years). Yes it's a decision you have to make, whether you want to play it safe and have a separate /home just in case or "save" an extra gig (or make your / 3.5 GB and waste even less space) and make / take up the entire drive but you are by no means wasting a lot of space.

---

### Post by justin whitaker on 2007-03-30
> **latebeat said:**
> 1.So upgrading to a new release just with apt-get can be done then. That's good :)
The whole point is so that I won't have to do a fresh install every 6 months I guess :)

Well, the upgrade from Dapper to Edgy, or from Edgy to Feisty, or any other 6 month release is only if you really want to keep up with the latest, greatest, and bleeding edge. You do not need to actually dist-upgrade each time. Dapper has LTS (Long Term Support) status, so you could just go on using Dapper for the next 2.5 years (or whatever) quite happily. 

> 2. So when u have home in a separate partition and u do a fresh install everything works as before?
What if some application changes that way it saves their settings or their configuration files and u just have ur config files from a previous release?

Well, no, it doesn't work perfectly. If you made alot of configuration changes, then you probably should either save the config files to your /home partition so you can copy them back later, or you should dist-upgrade. 

As far as which is better....well, I have successfully updated from Dapper to Edgy, but many people had all sorts of breakages....it's probably better to just start over.

---

### Post by daynah on 2007-03-30
I "bought" ubuntu Breezy (for the price of $0) online. So when I wanted to upgrade, I had to buy the next upgrade also online, using dist-upgrade (not update). Just because it's free doesn't mean it's update. The best things in life are free. Like dandelions.

---

### Post by Mateo on 2007-03-30
> **prizrak said:**
> Please don't spread misinformation. As it stands I have a 64MB /boot 4GB / and 68GB /home and a 1gig swap (for a total of 80 marketing gigs). I only have about a gig unused on / and bunch of free space on /home. Typical Ubuntu install won't take more than 3GB of your drive. So right now I'm "wasting" about a 1.5 DVD rips worth of space. Sure it could be a concern on an older system with smaller drive but not on anything even remotely modern (and by that I mean just about anything from the past 4 years). Yes it's a decision you have to make, whether you want to play it safe and have a separate /home just in case or "save" an extra gig (or make your / 3.5 GB and waste even less space) and make / take up the entire drive but you are by no means wasting a lot of space.

You're right, you have to either choose between wasting space or not downloading stuff.  If you only have 1 gig left on your /, that means you can only install 1 more gig of stuff.  That's fine if you never want new software, or don't want games, etc.

Partitions are not flexible.  It's better just to have the 1.

---

### Post by prizrak on 2007-03-30
> **Mateo said:**
> You're right, you have to either choose between wasting space or not downloading stuff.  If you only have 1 gig left on your /, that means you can only install 1 more gig of stuff.  That's fine if you never want new software, or don't want games, etc.



Yeah I don't play any games on Linux other than something like Wormux. Not sure what kind of new software you have in mind, I got a full Ubuntu install and couple of 3rd party applications sitting on there so anything other than updates I don't get. Also you can install software into your /home directory (if you are not going through the repos).
> Partitions are not flexible.  It's better just to have the 1.
That is a huge issue as far as I'm concerned and I wish I knew enough about programming file systems to change that.

---

### Post by Mateo on 2007-03-30
well that works for your situation, but not necessarily for others.  it's best that people know the strengths and weaknesses of going that right. the strength is the minor convenience in case something breaks in your system.  the weakness is that you either forfeit flexibility or you waste space (usually both).

---

### Post by mips on 2007-03-30
Nothing stops you from resizing your partitions. If that is not good enough for you there is always the flexibility of LVM.

---

### Post by prizrak on 2007-03-30
> **Mateo said:**
> well that works for your situation, but not necessarily for others.  it's best that people know the strengths and weaknesses of going that right. the strength is the minor convenience in case something breaks in your system.  the weakness is that you either forfeit flexibility or you waste space (usually both).

I've gotten into quite a bit of trouble with a single partition. I have been in a situation where I actually broke the / partition and couldn't get data out of it at all. It's not really a minor inconvenience to loose your files. I don't see it as losing any flexibility or wasting space. If you know your usage patterns then you will know how much space you need. The wasted space argument makes very little sense considering size of modern drives and size of general linux software.

---

