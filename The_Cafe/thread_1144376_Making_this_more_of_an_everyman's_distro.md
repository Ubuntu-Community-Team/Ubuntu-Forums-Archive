---
title: "Making this more of an everyman's distro"
date: 2009-04-30
forum: The Cafe
---

### Post by gamelord12 on 2009-04-30
There are a few things I think Ubuntu is missing from a default installation.  I can only assume that they're missing because Canonical is trying to hammer out the basics first or because these programs won't fit on a 700 MB CD.  Still, I feel these things are essential for the average user, and I'd rather have programs that can do these things with no hassle as well:

1) Back-ups: both for regular files and a "system restore" type of feature.  The file back-ups is a no-brainer for why it's needed.  As for the system restore, you guys may come up with this reason or that reason for why Linux doesn't need one, but my roommate and I have both encountered instances now where we've been interrupted in the middle of updates and that rendered Ubuntu useless, dropping it down to a shell where hope of getting things working again only exists for people who have a much better idea of what they're doing.  I know there are file back-up programs out there: could you guys recommend one?  Is there a system restore-esque program for Linux as well so that I can boot to a time when I know my system worked?

2) Instant search: Deskbar isn't installed by default in Ubuntu 9.04...why not?  Sure, it's not perfect.  It seems like it only works half the times you want it to, but it's better than nothing at all.  Tracker does a great job of indexing the machine, and when Deskbar decides to work, it's a great instant search solution.  Is there an alternative to Deskbar, or is it nearing a time when it'll work as it's supposed to?

3) Ubuntu Tweak should be installed by default or integrated into GNOME altogether.

4) Open Office 3 has some pretty bad bugs concerning drawing the screen in my experience.  I posted another topic about this issue particularly, thinking it was a problem with my GPU.

---

### Post by smudi on 2009-04-30
2) Gnome-DO ?

---

### Post by sgtbug on 2009-04-30
3) i had that issue too.. try using open java.. that solved my problem..

---

### Post by 3Miro on 2009-04-30
The first thing one does when getting into a new car is adjust the seat and mirrors. The first thing one should do when getting into a new system/installation is adjust the software. Some people would prefer some options as default others would prefer others. There is no way to satisfy everyone. In my opinion if something should be set by default or not is a pointless discussion since anyone can set it up to their preference anyway.

---

### Post by gamelord12 on 2009-05-01
Okay, the Java thing and GNOME-Do were great suggestions.  They both work great for my needs (I always thought GNOME-Do was just a program launcher).  What about my back-up needs?  What's good for that?

---

### Post by mb_webguy on 2009-05-01
A "system restore" feature is nearly essential in Windows because of the system registry.  You can backup and restore files and folders, but you can't do much to revert to a previous configuration without some means of reverting the registry as well.

Linux doesn't have a registry.  Everything is contained in files and folders, so reverting to a previous configuration is just a matter of restoring backup files.  Numerous applications exist to aid in the backup and restoration of files, but it can be done fairly easily from the file manager or the terminal.  A simple script could easily backup certain files and folders on a regular basis.  My entire system minus data files (like movies, music, etc.) totals just over 5GB, and I have a considerable amount of software installed.  That's not really a lot to backup.  It can fit on a dual-layer DVD with room to spare.

So basically, Linux already has a system restore feature: copy and paste.

The problems mentioned with updating are not at all related to any kind of "system restore" feature.  They're simply due to interrupted and corrupted package files, and can generally be fixed by running a command in the terminal (which is almost always included in the error message of your package manager).

As for integrated search... There's the "Search for Files" applet, if you want it.  And Deskbar, Gnome-Do, and Beagle are available in the repositories if you want them.  I can actually see something like this included in a default installation.  On the other hand, it would be one of the first things I'd remove after installation, since the indexed desktop search apps are all resource hogs when indexing (which they seem to do constantly), and if I need to find files I'm happy to use Search for Files in Nautilus, or locate in the terminal.

And Ubuntu Tweak is more definitely *not* something that needs to be included.  While it's a fine program, most (if not all) of the things it can do are already available through the normal configuration utilities.  And those that aren't already available fall into the area of customization and appearance.  If I had to guess, I'd say that the majority of users have little interest in turning their systems into the equivalent to one of those modified cars with hydraulic suspensions and flames shooting out of the exhaust.  

The default installation of Ubuntu should be simple and to the point, providing only those applications used almost universally by all users.  Everything else is optional, and thanks to the repositories and Add/Remove Applications, extremely easy to install.

---

### Post by gamelord12 on 2009-05-01
The problem with the system restore thing is that I don't know enough commands to be able to get my system back up and running if something like that happens.  I'd like to be able to see a working configuration of Ubuntu available in GRUB to boot to in case my normal one doesn't work.  I *can* memorize commands, but I have much more finite space in my brain than I do on my hard drive, and the whole point of computers is to automate things, so if Ubuntu aims to make it to the average user, this feels like something that should be done, if not by default than at least easily after installation of the OS.

---

### Post by mb_webguy on 2009-05-01
Searching for "backup" in Add/Remove found a number of backup solutions, depending on need and personal preference.

[Simple Backup Suite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")

[File Backup Manager]("http://andrewprice.me.uk/projects/pybackpack/") (a.k.a. Pybackpack, a Python-based backup manager with a very simple interface)

[Keep]("http://jr.falleri.free.fr/keep/wiki/Home") (though it apparently hasn't been actively developed since 2006)

[Déjà Dup]("https://launchpad.net/deja-dup")

[Bacula]("http://www.bacula.org/en/") (network-based backup)

This isn't like OpenOffice, where there is a clear best choice, or Firefox, where "best" is debatable, but the choice is made easy because of the popularity of the application.  These programs have different advantages and disadvantages that could make one preferable to a given user over the others.  Some backup to a local drive, some to removable media, some to online services like Amazon S3, and some over a network.  Some have the ability to automatically restore backup data, while others may not.  Different users have different needs and preferences when it comes to backing up and restoring their system.  So which of these do you think should be included in Ubuntu by default?  I say none, because if a user wants a backup application, they have the ability to easily choose the one that best suits his needs.

---

### Post by aysiu on 2009-05-01
If you have suggestions for Ubuntu, go to [Brainstorm](http://brainstorm.ubuntu.com) and make them.

Your first suggestion has already been made, so you can vote for it:
[System Restore](http://brainstorm.ubuntu.com/idea/1230/)

---

