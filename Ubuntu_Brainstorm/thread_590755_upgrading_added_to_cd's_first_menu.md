---
title: "upgrading added to cd's first menu"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by pdlethbridge on 2007-10-25
I would like to see an ***_upgrade option_*** added to the screen where you load the cd and have these options
run or install
safe mode install
oem install for manufacturers
cd check
etc...

---

### Post by aysiu on 2007-10-25
It would have to be an option only on the Alternate CD.

The Desktop CD doesn't have the packages necessary to perform an upgrade with.

---

### Post by sbjaved on 2007-10-25
The Desktop CD should detect if an ubuntu install is present and download necessary packages required to upgrade (assuming they aren't too many) and proceed with the rest of the upgrade from the CD. How about that?

---

### Post by aysiu on 2007-10-25
> **sbjaved said:**
> The Desktop CD should detect if an ubuntu install is present and download necessary packages required to upgrade (assuming they aren't too many) and proceed with the rest of the upgrade from the CD. How about that?
Well, the problem with that is that the Desktop CD contains virtually *no* packages required for an upgrade. You'd be downloading almost every single package from the internet, in which case, what's the point of having the CD to begin with? You might as well do a regular net-based upgrade... or use the Alternate CD.

---

### Post by pdlethbridge on 2007-10-25
The idea behind directly installing from the cd is to avoid potential problems with the partitions. Have you ever started a download and realized you didn't mark the home folder home rather than the hda3 or what ever that is given. Rather than channging the home folder after the install, I'd rather reinstall and get it right before installing. I don't like the idea of unmounting and mounting a drive and loosing valuable info in the process

---

### Post by aysiu on 2007-10-25
> **pdlethbridge said:**
> The idea behind directly installing from the cd is to avoid potential problems with the partitions. Have you ever started a download and realized you didn't mark the home folder home rather than the hda3 or what ever that is given. Rather than channging the home folder after the install, I'd rather reinstall and get it right before installing. I don't like the idea of unmounting and mounting a drive and loosing valuable info in the process
What? If you do a regular upgrade via downloads from the online repositories, you don't have to mark home as home or unmount anything. You just let the updates download and install themselves. Then you reboot the computer.

---

### Post by pdlethbridge on 2007-10-26
Now what if you have trashed your install and want to reinstall, why does the home folder get its name changed from /home to hda2 or something. Installing the OS should be easy and as painless and trouble free as possible. There are many new users out there that have a difficult time, give them a break

---

### Post by aysiu on 2007-10-26
> **pdlethbridge said:**
> Now what if you have trashed your install and want to reinstall, why does the home folder get its name changed from /home to hda2 or something. Installing the OS should be easy and as painless and trouble free as possible. There are many new users out there that have a difficult time, give them a break
I think what you mean is [this](http://ubuntuforums.org/showthread.php?t=411871).

---

### Post by pdlethbridge on 2007-10-26
Windows has a non destructive install in its install program. 
aysiu, yes thats what I'm talking about

---

### Post by sbjaved on 2007-10-26
> **aysiu said:**
> Well, the problem with that is that the Desktop CD contains virtually *no* packages required for an upgrade. You'd be downloading almost every single package from the internet, in which case, what's the point of having the CD to begin with? You might as well do a regular net-based upgrade... or use the Alternate CD.
Don't want to be flamed but with a Windows you just kinda pop in the CD and go to sleep after answering a load of ********. Umm...could we *think* of something like that? That'd be nice :)

---

### Post by aysiu on 2007-10-26
> **sbjaved said:**
> Don't want to be flamed but with a Windows you just kinda pop in the CD and go to sleep after answering a load of ********. Umm...could we *think* of something like that? That'd be nice :)
Why would we want to think of something like that?

In Ubuntu, you don't even have to answer any questions in order to upgrade (except "Do you want to upgrade?"). When you install, you answer a few questions in the beginning and can have Ubuntu installed in twenty minutes.

In Windows, you answer one question, wait five or ten minutes, answer another question, wait a half hour, answer another few questions, wait two more minutes, etc. That's annoying as hell. I had to reinstall Windows for my parents-in-law and I couldn't go to sleep. I had to keep coming back to answer more questions!

---

### Post by sbjaved on 2007-10-26
> **aysiu said:**
> Why would we want to think of something like that?

In Ubuntu, you don't even have to answer any questions in order to upgrade (except "Do you want to upgrade?"). When you install, you answer a few questions in the beginning and can have Ubuntu installed in twenty minutes.

In Windows, you answer one question, wait five or ten minutes, answer another question, wait a half hour, answer another few questions, wait two more minutes, etc. That's annoying as hell. I had to reinstall Windows for my parents-in-law and I couldn't go to sleep. I had to keep coming back to answer more questions!
No. That part's hell. Ubuntu is great with that. I was talking about the way they (Microsoft) handle upgrades...You pop in the CD and the update starts from the CD...system reboots and you're upgrading. 
Imagine popping a Hardy Desktop CD in Gusty. A dialog pops asking the user if he'd like to upgrade? Click "Yes" and whammo. That would be Godsend for users with slow internet connections like us. We don't want to re-install Ubuntu every six months :)

---

### Post by aysiu on 2007-10-26
> **sbjaved said:**
> No. That part's hell. Ubuntu is great with that. I was talking about the way they (Microsoft) handle upgrades...You pop in the CD and the update starts from the CD...system reboots and you're upgrading. 
Imagine popping a Hardy Desktop CD in Gusty. A dialog pops asking the user if he'd like to upgrade? Click "Yes" and whammo. That would be Godsend for users with slow internet connections like us. We don't want to re-install Ubuntu every six months :)
Isn't that what already happen when you pop in the Alternate CD?

As I said before, the Desktop CD doesn't have the packages necessary to perform an upgrade with.

---

### Post by sbjaved on 2007-10-26
> **aysiu said:**
> Isn't that what already happen when you pop in the Alternate CD?

As I said before, the Desktop CD doesn't have the packages necessary to perform an upgrade with.
Could we have them packages? :))

---

### Post by aysiu on 2007-10-26
> **sbjaved said:**
> Could we have them packages? :))
There's not enough space to have both a live session that installs *and* all the packages necessary for an upgrade.

The Desktop CD doesn't install by unpacking and installing individual .deb files. It installs by copying over the live session to your hard drive.

---

### Post by pdlethbridge on 2007-10-26
Would it help if they switched from cd to dvd, then would the alternate have room?

---

### Post by aysiu on 2007-10-26
> **pdlethbridge said:**
> Would it help if they switched from cd to dvd, then would the alternate have room?
They already have. There are Ubuntu DVDs that are live sessions that also contain the entire Main and Restricted repositories (that includes Ubuntu, Kubuntu, Xubuntu, and Edubuntu).

The problem is that many people (me, for instance) do not have DVD burners, and even those that do may not want to download a 4 GB file (700 MB takes a lot less time to download).

---

### Post by pdlethbridge on 2007-10-26
you could order the free disk from canonical. OR get road runner

---

### Post by suchawato on 2007-10-27
Yes, actually, it is not as easy in implementation as some would like to think.
I have had problems with every version of Ubuntu installed.
The Internet upgrade f*ck*d  my sytem so bad that I had to download the disc image and do a clean install on a different partition.
I also noticed that in the Beta version of Gutsy, it had a nice feature to let you choose the "most unused space on a harddrive" to create a partition. In the final release, this option was no longer present.
To date, the cleanest install I've ever seen with a Linux distro, is Suse, which detects the Windows partition automatically, AND does not delete it, it is detected, and instead does exactly what I had just mentioned: Installs Suse in the largest Unused space (leaving some extra for Windows) and Then makes it available as a Boot option in the Suse Lilo boot Splash Menu.

Aysiyu, you underestimate the enfluence Ubuntu actually has reached.
I know many, Computer illiterate people, who have heard from their techie friends that they should use Ubuntu or Linux. 

They are willing to give it a try, but not at the expense of wipeing out Windows. 
At the moment, the Default install, does exactly this.
And most common users From Windows are used to just hitting "OK" and letting the default install load.
At the moment there is no middle ground between "wiping it out" and manually setting up a partition, 
AND THIS IS VERY IMPORTANT:
Most Windows users don't even know what a partition IS.
Much less feel comfortable setting one up for the first time. -Especially when the consequences of getting it wrong could mean wiping out their data.
There needs to be an automatic "wizard" that safely sets up an Ubuntu partition for them, AND, allows them to easily boot back and forth from the get-go.
If its any more complicated than this, they won't do it.
And those who try to do it manually, and maybe f*ck it up, will be left feeling scared and intimidated by Linux and Ubuntu, and not want to use it again.
I know of at least one person this has allready happened to.

---

### Post by suchawato on 2007-10-27
This actually happened to me the first time I installed a version of Ubuntu.
I lost everything on my computer.
I had expected it to be like Suse, and it certainly wasn't.

It happened a second time, with a later distro, trying to set up a partition, I made a mistake, when typing in the space to be used, and wiped out Windows again.

I had a third issue using an internet upgrade to a newer distro: it wreaked the sytem.

I had a fourth, trying to upgrade to UbuntuStudio: it created a disabled system.

There have also been issues trying to install it on a friend's laptop.

So, the overall impression is that Installing Ubuntu is NOT Pain-free, it is in fact a Pain-full learning process.

I am a person who was and is bound and determined to make it work.
But I am the exception to the rule.
Most Windows and Mac OS users would never touch it again, or for at least a long time, if these things had happended to them.
They would rather buy a Mac.

---

### Post by sbjaved on 2007-10-27
Very Good points. In fact I got scathed by Gusty too. In the middle of an internet upgrade...i lost connection. The upgrade app said it was rolling back changes..when i rebooted...BAM!...nothing...no xserver...it didn't boot. Ubuntu should look at different distros which have done some good work and pick up things. It would help make it better and users happy

---

### Post by pdlethbridge on 2007-10-27
I've always used the KISS principle. Keep It Simple, Stupid. Remember, The majority of folks that come to linux come from windows. It has been said here that they don't know how to partition, and this is probably very true. Example, my daughter bought a car with a standard transmission. All of her friends drive automatics. Guess how many of her friends will ask to borrow her car, none. People are basically lazy, they go for the fastest, the easiest, the cheapest of anything. They don't want to take the time to learn, especially something like the standard transmission of OS's, linux. If you want them to use it, you have to automate it. We all ready have some tools to automate some processes, Envy and Automatix come to mind.

---

### Post by pdlethbridge on 2007-10-28
bump

---

### Post by suchawato on 2007-10-29
I have used Automatix and EasyUbuntu.
I haven't tried Envy.
I'll google it.

---

### Post by suchawato on 2007-10-29
For graphics cards.
Neat. Useful. 
I do try to stay away from Automatix though,
I read a coder's review on it and it wasn't pretty.
Lots of stuff about how this or that line was sloppy or potentially dangerous.
And it sounds like it doesn't do some basic system safety features that it should as a high level system installer that it is apparently attempting to be.
But that's a side note.

---

### Post by pdlethbridge on 2007-10-29
the tools that should be in the distro are an easier partitioner and a home folder creator. Also a tool should be included that saves all previously installed OS's like windows or only uses the unused space by default rather than the whole drive.

---

### Post by suchawato on 2007-10-29
Yes.
Agreed.
100%

---

