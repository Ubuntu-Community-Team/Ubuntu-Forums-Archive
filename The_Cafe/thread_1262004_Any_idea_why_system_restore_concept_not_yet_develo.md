---
title: "Any idea why system restore concept not yet developed in ubuntu??"
date: 2009-09-09
forum: The Cafe
---

### Post by kapmsd on 2009-09-09
Hi guys!!
I really wonder why SYSTEM RESTORE has not yet developed in ubuntu.
Unlike Windows, i have faced only few probs in ubuntu necessitating a SYSTEM RESTORE.(eg:[http://ubuntuforums.org/showthread.php?t=1161983](http://ubuntuforums.org/showthread.php?t=1161983))
Any idea reg this?

---

### Post by papuccino1 on 2009-09-09
Yesterday I raped my Ubuntu installation so I know for a fact this System Restore function would be incredibly useful. Linux isn't perfect after all.

---

### Post by kapmsd on 2009-09-09
Mr.papuccino1, as per ur ubuntu usage, pls list me the situations when u felt SYSTEM RESTORE will be useful?

---

### Post by mapes12 on 2009-09-09
You can configure your own quasi system restore. Here's what I do:

- "/" and home on their own partitions
- Keep regular backups to a removable drive of /home (Grsync)
- Keep a note in Google docs of any apps and tweaks you make to your system
- Clone "/" using something like Clonezilla

Then if all goes wrong you can put everything back together again in a number of different ways:

- Just restore the Clonezilla image of "/"
- or if things are so bad that a restored clone doesn't work then do a fresh install but don't format /home then just follow the list of tweeks etc. to have everything as it was before.
- if the entire drive has to be replaced then fresh install, copy back /home plus tweek list and your done
- or you can clone the entire drive if you want............many ways to keep stuff safe and restore it.

The above is clearly not extensive but it works. I'm also just experimenting with FSArchiver but haven't tested it yet.

---

### Post by JebusWankel on 2009-09-09
System restore is great for operating systems that are designed from the bottom up to be used by non-technical users. Linux was developed mostly by enthusiasts writing software for people like themselves, so GNU/Linux made slow, gradual but natural progress from a hard core geek OS. Ubuntu is the result of that progress, which is why it is so successful. Other distros that try to be user friendly aren't as successful because they made too big of a leap, so they don't have a community of experienced users to support the novice users.

But I digress. As mapes12 showed above, there are ways to do it. Eventually there may be something comparable to System restore on Linux. As it is, there's a significant barrier to entry to Linux, so a lot of people are less invested in their installs, so they are more likely to wipe their installs and start over. Linux users are also more likely to go get help and fix the problem at the source, because they're more likely to have the skills to do so. 

System restore is great as a catch-all. Rather than ask the user who can't explain what's wrong, let alone how it happened, the support person can just tell them to do a system restore.

Also system restore can be used to undo the affects of malicious software, and Linux isn't a big target for that.

Anyway, there's not much of a need.

---

### Post by LewRockwell on 2009-09-09
.
.
.
.
Clonezilla..........why reinvent the wheel?
.
.
.
.
.

---

### Post by credobyte on 2009-09-09
> **LewRockwell said:**
> .
.
.
.
Clonezilla..........why reinvent the wheel?
.
.
.
.
.

Clonezilla does work in background ( eg., makes silent backups every week or so ) and you can run it from GRUB ( if there's something wrong with your display drivers or whatsoever ) ?

---

### Post by LowSky on 2009-09-09
Why do you need a system restore? What did you break, and how would a system restore fix it?
More importantly how has the windows restore ever really worked correctly?
It doesn't bring back old deleted files or programs, all it does is fix the windows registry.

---

### Post by Darkwing-Duck on 2009-09-09
I agree and I disagree <G> The idea of a system restore from outside software I will agree with. But being someone who jumped into Linux headfirst and started tweaking everything to get my system running I found that I broke alot of things and by doing so I had to reinstall so many times. 
 
I think for the new user setting up a way for them to revert back would be very helpful and maybe even be quite popular.
 
As someone who came over from windows when I started off in Ubuntu I was overwhelmed with the use of terminal and was over dependant on GUIs. While this over time went away I know alot of people who will give up esp if they are just toying with the idea instead of swtching out of pure hatred for Windows (like me)
 
Just my thoughts on it.

---

### Post by credobyte on 2009-09-09
> **LowSky said:**
> 
More importantly how has the windows restore ever really worked correctly?

101 times ..

---

### Post by gn2 on 2009-09-09
[Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html").

---

### Post by earthpigg on 2009-09-09
> More importantly how has the windows restore ever really worked correctly?

i can vouch for it, from when i used to use windows.

also, +1 for remastersys.

not only will it back up your system, but it will do so in a *deployable* manner.

---

### Post by Pirolocito on 2009-09-09
Windows system restore is not a good example. When i was a windows user it was the first think i disable on every installation.

My wife got a virus, Virut, and system restore was so good, that restore files were also infected.... System restores in win saves the files with the same extension, and in this case all the exe files where infected too.

I needed to use a Linux antivirus tool to remove it... DRweb...

So why dont you use somekind of backup tool? and use a script on boot or on shutdown to run it? And for the installed packages you can see how to do a list and restore it back in the link

[http://ubuntu-unleashed.com/2008/05/howto-restore-all-installed-packages-in-ubuntu-hardy-heron-and-to-a-new-machine.html](http://ubuntu-unleashed.com/2008/05/howto-restore-all-installed-packages-in-ubuntu-hardy-heron-and-to-a-new-machine.html)

Best regards

---

### Post by The Cog on 2009-09-09
I rather hope that the snapshot feature on the btrfs filesystem will provide system restore like features, but that's some time away yet.

---

### Post by Zimmer on 2009-09-09
I have been here for 6 hours now trying to get Win XP to Restore a friend's laptop to a workable state, and this current attempt could also end in the message 'Unable to Restore to this point, please try again!!

If the laptop belonged to me it would have been wiped and Ubuntu'd by now, with a separate partition to store personal data on (easier to cope with than the /home partition idea, IMO.

must dash, XP is finally booting the next Restored config...  fingers crossed..

EDIT... Your computer cannot be restored to....  choose another restore point yadayada...
Here we go again..

---

### Post by aysiu on 2009-09-09
In my decades of Windows use, I've never found System Restore to actually work when I needed it to.

It sounds great in theory, though, and if Ubuntu could implement it well, I'd be in favor of it:
[Idea #1230: System Restore](http://brainstorm.ubuntu.com/idea/1230/)

---

### Post by aysiu on 2009-09-09
In my decades of Windows use, I've never found System Restore to actually work when I needed it to.

It sounds great in theory, though, and if Ubuntu could implement it well, I'd be in favor of it:
[Idea #1230: System Restore](http://brainstorm.ubuntu.com/idea/1230/)

---

### Post by SunnyRabbiera on 2009-09-09
> **aysiu said:**
> In my decades of Windows use, I've never found System Restore to actually work when I needed it to.

I agree, also if you have a separate home and root partition there is no real no need to have a "system restore"

---

### Post by bxcrx on 2009-09-09
I've found system restore to fix many "wacky" problems that are more like configurations gone corrupt for who knows what reason (See:wacky)

System Restore not really -- System restoration of proper configuration of the base o/s and programs without the removal / addtion of data -- Yes

Sorry but Ubuntu could use something like a Time Machine.

---

### Post by starcannon on 2009-09-09
Check out this guide; it has a variety of backup options, one is sure to be just right for you.
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

GL and HF
~Starcannon

p.s.
> **bxcrx said:**
> I've found system restore to fix many "wacky" problems that are more like configurations gone corrupt for who knows what reason (See:wacky)

System Restore not really -- System restoration of proper configuration of the base o/s and programs without the removal / addtion of data -- Yes

Sorry but Ubuntu could use something like a Time Machine.

Try [Timevault]("https://wiki.ubuntu.com/TimeVault").

---

### Post by LinuxRules1 on 2009-09-09
I would only use TimeVault just in case I accidentally delete a file that I need. Other then that, as long as I can get to the recovery console then I don't need system restore. Plus if the filesystem gets corrupted I can just boot off a live CD and recover the data off the drive and copy it to my server or something.

---

### Post by pastalavista on 2009-09-09
Insert Ubuntu live CD-->Run manual installation-->UNCHECK the format boxes-->System Restored

---

### Post by NormanFLinux on 2009-09-09
Linux is stable and if the bootloader becomes corrupted, its just faster to reinstall it.

---

### Post by MasterNetra on 2009-09-09
> **LowSky said:**
> Why do you need a system restore? What did you break, and how would a system restore fix it?
More importantly how has the windows restore ever really worked correctly?
It doesn't bring back old deleted files or programs, all it does is fix the windows registry.

And not very well I might add. though going back does remove .exe files and other executables. Leaves .txt and unknown files though... System Restore for me never really fixed anything in fact many times it seemed to make the system more unstable. But then again haven't seen if they improved it on Windows 7 as I have yet the need to use it there. Useless though in XP or better yet it was/is a cruel joke in XP. For me at least it was.

---

### Post by falconindy on 2009-09-09
**Amusing anecdote**: System Restore saved my butthole when I decided that installing SP3 after 2 years and many many many registry fixes on SP2 was a good idea.

**Fun fact**: System Restore does more than play with the registry.

**Pro tip**: You don't actually need system restore enabled to restore the registry. Ever taken a peek in the 'System Volume Information' folder? I can't tell you how many times I've recovered dying XP machines from a recovery console with that folder.

**Related content**: Second what everyone else has said about Linux being for developers. If you want a feature that Linux doesn't have, you write it yourself. In this case, taking an image of your disk is insanely easy and there's multiple solutions.

---

### Post by bryncoles on 2009-09-10
> **pastalavista said:**
> Insert Ubuntu live CD-->Run manual installation-->UNCHECK the format boxes-->System Restored

Really? Ten points! I once borked my graphics drivers (when I was just starting out no less, and had no idea how to fix it!). I ended up popping in the live cd and just replacing a few config files with their old versions, using good old copy/paste. 

And System Resore has never worked for me on Windows - even when it says it has done it does nothing! No experience of Time Machine though (or any idea what it is). 

All together now: "We don't need no system restore... DEVELOPER! Leave those system files alone..."

---

### Post by bodyharvester on 2009-09-10
when i used windows xp i SYSTEM RESTORED about as much as i restarted ;)

Ubuntu i still havent messed up, maybe coz i do not want to :D

---

### Post by recluce on 2009-09-10
I used Windows too long in order not to make backups before doing any major changes to my system (saved my a** a couple of times, after updates crashed Windows to a point where nothing worked anymore).

Here is the approach I use:

- root and home are on different partitions 
- use Ubuntu's backup functions to backup home
- use Acronis boot CD to backup root partition*
- make any changes
- in case of failure, restore home and/or root

* I do not recommend Acronis anymore, since it is limited to backup of reiserfs and EXT2/EXT3 with 128byte INodes. But you get the idea, use a similar tool that works with your root being _inactive_.

---

### Post by rmcellig on 2009-09-10
LinuxRules1,

Have you ever used Timevault? I am very interested in this app because it looks like it was made for mere mortals like me. I would love to use this in my Ubuntu setup. I have a 500GB USB external drive ready to accept backups, and Timevault would be the ideal candidate IMHO.

---

### Post by BigSilly on 2009-09-10
I really hope we never see system restore on Linux. It never works. Well, it never has for me anyway. It's the first thing I turn off on a fresh Windows install. Just keep back ups, and take a Ghost image. Much better imho.

---

### Post by collinp on 2009-09-10
If a System Restore of types got included with Ubuntu, I personally would just uninstall it. I prefer actually fixing things myself rather than trusting my OS's fate with a automated program that could mess things up worse (which it often does). And, for that reason, it is useless to me.

---

### Post by andras artois on 2009-09-10
I would have thought that a backup utility would work out better. Regular backing up of documents, settings and a list of installed programs compared to the standard installation.

---

### Post by bodhi.zazen on 2009-09-10
Actually there are a few options :

Time Vault :
    [http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php](http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php)
    [https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

    Dirvish : [http://www.dirvish.org/](http://www.dirvish.org/)

    Others : [http://ubuntuforums.org/showthread.php?t=723535](http://ubuntuforums.org/showthread.php?t=723535)

I find what works best is to keep your data separate from your OS. If you need to "restore" your system, simply re-install.

---

### Post by Ric_NYC on 2009-09-10
Everybody makes mistakes.
A "system restore" utility gives some "forgiveness" for those mistakes.
Re-installing an OS is too radical.


If a "system restore" utility is available it doesn't mean that the user of the OS is going to use all the time.

---

### Post by NormanFLinux on 2009-09-10
Even the best restore program program in Windows, like Rollback RX, can only restore Windows to the state it last worked. Its best to back up data so you don't lose it if Windows won't boot or something goes amiss.

---

### Post by LinuxRules1 on 2009-09-10
> **rmcellig said:**
> LinuxRules1,

Have you ever used Timevault? I am very interested in this app because it looks like it was made for mere mortals like me. I would love to use this in my Ubuntu setup. I have a 500GB USB external drive ready to accept backups, and Timevault would be the ideal candidate IMHO.

I just started using it. I haven't figured out much yet.

---

### Post by rmcellig on 2009-09-11
Actually I am trying to remove it permanently from my system but don't know how. Can't do it from the Synaptic Package Manager. Any ideas?

---

### Post by Screwdriver0815 on 2009-09-11
rsnapshot FTW!

its a commandline backup utility and can be configured to back up certain folders (system and home folders) in certain timeframes.

[http://rsnapshot.org/](http://rsnapshot.org/)

it is in the repos too...

---

### Post by megamania on 2009-09-11
> **kapmsd said:**
> Mr.papuccino1, as per ur ubuntu usage, pls list me the situations when u felt SYSTEM RESTORE will be useful?
Mr.Kapmsd, uninstall hdparm and then tell me if you miss a system restore function.

:-)

---

### Post by thisllub on 2009-09-11
> **mapes12 said:**
> You can configure your own quasi system restore. Here's what I do:

- "/" and home on their own partitions
- Keep regular backups to a removable drive of /home (Grsync)
- Keep a note in Google docs of any apps and tweaks you make to your system
- Clone "/" using something like Clonezilla

Then if all goes wrong you can put everything back together again in a number of different ways:

- Just restore the Clonezilla image of "/"
- or if things are so bad that a restored clone doesn't work then do a fresh install but don't format /home then just follow the list of tweeks etc. to have everything as it was before.
- if the entire drive has to be replaced then fresh install, copy back /home plus tweek list and your done
- or you can clone the entire drive if you want............many ways to keep stuff safe and restore it.

The above is clearly not extensive but it works. I'm also just experimenting with FSArchiver but haven't tested it yet.

Too hard.

Use LVM on the / partition and create a snapshot before you do something dodgy.
If it fails dump the snapshot, if you are happy merge it.

LVM can do a lot if you look into it.

ZFS under OpenSolaris already supports Time Slider BTRFS will support something similar.

---

### Post by hoppipolla on 2009-09-11
It would be great to see more system restore features in Ubuntu, and maybe even things that compare to "Time Machine" on a Mac.

All in good time though, I'm sure we'll see them :)

---

### Post by quinnten83 on 2009-09-11
> **Ric_NYC said:**
> Everybody makes mistakes.
A "system restore" utility gives some "forgiveness" for those mistakes.
Re-installing an OS is too radical.


If a "system restore" utility is available it doesn't mean that the user of the OS is going to use all the time.

I agree with you on this one on principle.
But, reinstall of ubuntu is usually around 15 to 30 minutes. Combine this with a seperate home partition (which I do not live without) and you got your system up and running again in less than an hour.
True, sometimes you need to configure some stuff, but many times you don't.
My advice, backup your homefolder on a regular basis using unison or conduit. And if you know how, keep a bash script that will install all the stuff you need.

---

### Post by Screwdriver0815 on 2009-09-11
> **hoppipolla said:**
> It would be great to see more system restore features in Ubuntu, and maybe even things that compare to "Time Machine" on a Mac.

All in good time though, I'm sure we'll see them :)

Time Machine?

[http://backintime.le-web.org/](http://backintime.le-web.org/)

its in the style of Time Machine. Linux is not so far behind ;)

---

### Post by hoppipolla on 2009-09-11
> **Screwdriver0815 said:**
> Time Machine?

[http://backintime.le-web.org/](http://backintime.le-web.org/)

its in the style of Time Machine. Linux is not so far behind ;)

That's pretty cool I like that! A great thing to have :)

---

### Post by kapmsd on 2009-09-13
Guys, Happy to see your active participation in the thread.
But most of the solutions discussed can't be done by a common user.

**I will tell a scenario:**

In many events,most of the big companies sponsoring gives laptop installed with Linux as prizes ,as they r free of cost.

Now think how can you expect them to use any backup utility or other techie stuffs to restore their laptop once they are down.

---

### Post by mcduck on 2009-09-13
> **kapmsd said:**
> Guys, Happy to see your active participation in the thread.
But most of the solutions discussed can't be done by a common user.

**I will tell a scenario:**

In many events,most of the big companies sponsoring gives laptop installed with Linux as prizes ,as they r free of cost.

Now think how can you expect them to use any backup utility or other techie stuffs to restore their laptop once they are down.

In the same way everybody else does, by copying important files to some external media.

Backups are not advanced stuff, they are basic aspect of computing.

Just like avoiding obstacles, other cars and pedestrians is basic aspect of driving a car. And in the same way both skills, using a computer and driving a car, are things that require learning at least a few basics, but are still things that everybody is able to do if they want to. The only difference is that for some reason people assume that they shouldn't have to learn *anything* to use their computers. ;)

Besides, System Restore shouldn't really even be counted as a way of making backups. The data isn't secured if it's in the same machine, any fault causing the original data to be lost could easily cause you to loose the backup as well.

Time Machine isn't a backup either if used with an internal drive, or external drive that's always connected to the machine. When used with a network drive that's ,a t the very least, connected to different power outputs or to UPS it could be considered as some level of a backup.

But in the end my point is this, making backups is really simple. If you are able to write a CD, or copy files to external drives, you are able to make backups.

---

### Post by aikiwolfie on 2009-09-13
Windows System Restore feature is just a  backup feature. It's considered best practice to back up any critical file you want to make a change to. It's also considered best practice to make regular back ups anyway. In the worst case scenario you can restore your system from your latest backups using a live CD. 

Applications like gedit will also routinely make back ups of files before saving a new version of that file. So you should at least always be able to roll-back one edit. There's also loads of options for installing backup software from the repositories.

Personally I backup my fstab file, my xorg file and my home folder with the following commands.

```
sudo cp -r -u -x -v /home /media/eSATA_01/backup/moonstone/
sudo cp -r -u -x -v /etc/fstab* /media/eSATA_01/backup/moonstone/etc/
sudo cp -r -u -x -v /etc/X11/xorg* /media/eSATA_01/backup/moonstone/etc/X11/"
```

To back up your entire system without using any extra software you could run a similar command.

```
sudo cp -r -u -x -v / [add your back up destination here.]
sudo cp -r -u -x -v /home [add your back up destination here.]
```

You need to use the -x switch to stop cp eating it's tail since using the -r option to recursively copy all subdirectories would include any removable media mounted to /mnt or /media or anywhere else for that matter.

Which of course means you need to back up /home separately if it's on a separate partition.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-13
A simple GUI with this function would be very-useful. I would like something like this to be bundled

---

### Post by Screwdriver0815 on 2009-09-13
> **&#1057 said:**
> A simple GUI with this function would be very-useful. I would like something like this to be bundled

do you mean the commands, posted by aikiwolfie?

so you are not able to copy-paste the commands and adapt the destination-paths in the first 3 commands to your personal circumstances and to complete "[add your back up destination here.]" with the actual path where you want to have the backup?



no comment...

---

### Post by Regenweald on 2009-09-13
Since we have live cd's a system restore feature would be kind of redundant. Also, for the first few months using a linux distro, don't mess around with your system in areas you do not understand, take the time to learn first.

---

### Post by aysiu on 2009-09-13
Remastersys is pretty good, and it's fully point-and-click. It can back up just your system files and configuration... or your full installation (including personal files).

---

### Post by bodhi.zazen on 2009-09-13
> **aysiu said:**
> Remastersys is pretty good, and it's fully point-and-click. It can back up just your system files and configuration... or your full installation (including personal files).

Remastersys is nice, just be careful to read the documentation, if you click the wrong button it can make unwwanted changes to your system.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-13
> **Screwdriver0815 said:**
> do you mean the commands, posted by aikiwolfie?

so you are not able to copy-paste the commands and adapt the destination-paths in the first 3 commands to your personal circumstances and to complete "[add your back up destination here.]" with the actual path where you want to have the backup?



no comment...
I would like more options of course.Such as time-based backups,event-based backups and other things related

---

### Post by Screwdriver0815 on 2009-09-13
> **&#1057 said:**
> I would like more options of course.Such as time-based backups,event-based backups and other things related

so your xorg.conf changes its content over time? 

but anyway as posted before... [http://backintime.le-web.org/](http://backintime.le-web.org/) is also in the repositories and many many many many more backup programs. But I have to admit: finding things like backup programs in Synaptic requires searching for them by typing "backup" into the search-bar... ;)

but generally: when you are not able to copy some files via terminal, you also don't need to backup your system files because you could not use this backup anyway if a systemcrash occurs.

---

### Post by aikiwolfie on 2009-09-13
> **&#1057 said:**
> A simple GUI with this function would be very-useful. I would like something like this to be bundled

There several backup utilities in the repositories. On the top menu click Applications > Add/Remove and then type backup as the search string. Select the application you want and click Apply Changes. Enter your password when prompted.

I of course can't vouch for any of those applications as I've never used them. However they are there if you want them. However Keep seems to be the most popular.

>  Keep
Keep is an automatic backup program that allows users to set the parameters of the backup, including the frequency and the number of backups. 
Homepage: [http://jr.falleri.free.fr/keep](http://jr.falleri.free.fr/keep)

Canonical does not provide updates for Keep. Some updates may be provided by the Ubuntu community.

---

### Post by Screwdriver0815 on 2009-09-13
> **aikiwolfie said:**
> There several backup utilities in the repositories. On the top menu click Applications > Add/Remove and then type backup as the search string. Select the application you want and click Apply Changes. Enter your password when prompted.

I of course can't vouch for any of those applications as I've never used them. However they are there if you want them. However Keep seems to be the most popular.

keep is not maintained anymore.

I propose Backintime, as I posted before

---

### Post by nerdopolis on 2009-09-13
One nice thing about Keep is that it is a GUI front end to rdiff-backup instead of rsync.

With rdiff-backup you can backup just the differences from a changed file, instead of copying the complete file.

For example if you had a 20gb virtual hard disk file, and you only change a little bit of data on it between your old back up, and currently running backup, it will copy just the data that was changed, and stores it in some binary diff format.

---

