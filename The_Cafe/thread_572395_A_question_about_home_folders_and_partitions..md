---
title: "A question about /home/ folders and partitions."
date: 2007-10-10
forum: The Cafe
---

### Post by ticopelp on 2007-10-10
Not in any of the help forums because I'm not actually going to do this, but I am curious. 

If you make a distinct /home/ partition on your computer, separate from the operating system, could you potentially install an entirely different Linux distro on the main partition, and have everything in your /home/ folder still work normally?

---

### Post by Crashmaxx on 2007-10-10
Yes, in fact that is one of the main advantages of a separate /home partition. But its not perfect, depending on what differs from distro to distro, something or other may not work as expected.

---

### Post by Foxmike on 2007-10-10
Technically, yes.  But since all your personnal configurations files are held in your /home directory, and other distros (with other version of software) might manage differently the configuration files, you can get into a great mess!  I would suggest to have a central directory/partition for personnal documents you would like to share from 1 distro to another, and keep each distro with their /home directory.  For instance, I would recommend such a setup (assuming that all the users are the same from distro #1 and distro #2:
```

/dev/hda1 -> root partition of distro #1 
/dev/hda2 -> root partition of distro #2
/dev/hda3 -> /home/(user1)/Documents
/dev/hda4 -> /home/(user2)/Documents

```
So then /home/(user1) will hold the configurations file in each distro, but also that /Document folder (which is in fact a mount point to a partition) that will hold the shared documents...

---

### Post by ticopelp on 2007-10-10
Okay, thanks. I was just curious. I think multiple /home/ directories like that might make my head explode... maybe if I have a spare machine and some time to kill someday...

Thanks!

---

### Post by maybeway36 on 2007-10-10
I actually keep the entire /home when I reinstall the same distro, but when I do a new distro I run first:
```
rm -r ~/.*
```
This deletes all my config. Usually I make a backup first.

---

### Post by az on 2007-10-10
Years ago, when everything was text-mode, this worked pretty well.

Nowadays, a later version of an application can completely screw up your configuration file so that it is unusable in the earlier version.  This makes running two versions of an OS while sharing the same home drive impractical.  Especially avoid this if you are running development software (for example, if you are running th development version of Ubuntu before it releases.)

There is no advantage to keeping a separate home partition.  It is much simpler and safer to just back up your data the conventional way.

---

### Post by wana10 on 2007-10-10
what if i'm upgrading to gutsy from feisty? can i install the new gutsy root over the old feisty root, keeping my /home the same and not expect major problems?

---

### Post by Kowalski_GT-R on 2007-10-10
> **az said:**
> It is much simpler and safer to just back up your data the conventional way.

I was about to pose this question myself, since i'm preparing for a Gutsy fresh install.

what's the best way to backup my browser bookmarks?

thanks,

Andre

---

### Post by Lord Illidan on 2007-10-10
In firefox, just click on Bookmarks -> Organise Bookmarks -> File  -> Export.

Then just save them as bookmarks.html somewhere safe.

Problem solved :guitar:

EDIT : Also, regarding the /home partition issue, I also read that different distros might use different UIDs, so you might not be able to log in.

Anyway, I tried it with Sabayon and Feisty, had a terrible mess due to all the different configuration files. Totally messed up GNOME, I had to reinstall it and purge the whole thing.

---

### Post by az on 2007-10-10
> **Lord Illidan said:**
> Totally messed up GNOME, I had to reinstall it and purge the whole thing.

Next time, just create a new user.  When an app starts for the first time, defaults get written into the dotfiles in the user's home directory if there are none there.

---

### Post by ticopelp on 2007-10-10
> **az said:**
> Years ago, when everything was text-mode, this worked pretty well.

Nowadays, a later version of an application can completely screw up your configuration file so that it is unusable in the earlier version.  This makes running two versions of an OS while sharing the same home drive impractical.  Especially avoid this if you are running development software (for example, if you are running th development version of Ubuntu before it releases.)

There is no advantage to keeping a separate home partition.  It is much simpler and safer to just back up your data the conventional way.

Well, that's disappointing. I spent an afternoon doing that so I wouldn't have to go through a laborious backup when Gutsy came out.

---

### Post by thisllub on 2007-10-10
> **az said:**
> Years ago, when everything was text-mode, this worked pretty well.

Nowadays, a later version of an application can completely screw up your configuration file so that it is unusable in the earlier version.  This makes running two versions of an OS while sharing the same home drive impractical.  Especially avoid this if you are running development software (for example, if you are running th development version of Ubuntu before it releases.)

There is no advantage to keeping a separate home partition.  It is much simpler and safer to just back up your data the conventional way.

I strongly disagree. I have had this home partition through a half a dozen distros without any serious problem.
If any app gives you trouble on first run delete its ~/.app folder.
If that doesn't work delete and reinstall the app.

The benefits far outweigh possible disadvantages.

I always have 2 working distros on this computer. If one corrupts for any reason, and while I was learning Linux there were plenty of reasons, I can work out of the other with all my stuff intact.

However it doesn't reduce the need for backing up, if anything it extends it.

---

### Post by Incense on 2007-10-10
> **thisllub said:**
> I strongly disagree. I have had this home partition through a half a dozen distros without any serious problem.
If any app gives you trouble on first run delete its ~/.app folder.
If that doesn't work delete and reinstall the app.

The benefits far outweigh possible disadvantages.

I always have 2 working distros on this computer. If one corrupts for any reason, and while I was learning Linux there were plenty of reasons, I can work out of the other with all my stuff intact.

However it doesn't reduce the need for backing up, if anything it extends it.

+1 I distro hop all the time, and don't muck around with my /home. Just actually blew out my OpenSUSE part and installed Gutsy. No issues yet, and my kontact info is still in tact.

---

### Post by Lord Illidan on 2007-10-11
> **az said:**
> Next time, just create a new user.  When an app starts for the first time, defaults get written into the dotfiles in the user's home directory if there are none there.

Sure, but I'd have to move all the data :P Reinstalling GNOME is easier.

---

### Post by FranMichaels on 2007-10-11
> **thisllub said:**
> I strongly disagree. I have had this home partition through a half a dozen distros without any serious problem.
If any app gives you trouble on first run delete its ~/.app folder.
If that doesn't work delete and reinstall the app.

The benefits far outweigh possible disadvantages.

I always have 2 working distros on this computer. If one corrupts for any reason, and while I was learning Linux there were plenty of reasons, I can work out of the other with all my stuff intact.

However it doesn't reduce the need for backing up, if anything it extends it.

I must agree with this. I don't distro hop, but I have the same /home that went through dapper, edgy, feisty, and then gutsy. Deleting .whatever is easier since my home folder contains my personal files too... It's just a matter of keeping things simple. The only caveat is when I did a fresh install, and had to play with chown to have it use my /home/user :)

---

### Post by Forlong on 2007-10-11
I always make a backup of my home folder (have a special backup partition) and use the same /home partition for everything. In case anything gets screwed, I pick the config folder from the backup. Easy as pie.

Same /home partition for all distros is the best invention since sliced bread, IMHO.

---

### Post by DoktorSeven on 2007-10-11
> **maybeway36 said:**
> I actually keep the entire /home when I reinstall the same distro, but when I do a new distro I run first:
```
rm -r ~/.*
```
This deletes all my config. Usually I make a backup first.

~/.* also matches **~/..**, the parent directory (/home/), and -r recurses back into your home directory and deletes everything.  If it doesn't, rm has gotten a lot smarter lately for some reason.

---

