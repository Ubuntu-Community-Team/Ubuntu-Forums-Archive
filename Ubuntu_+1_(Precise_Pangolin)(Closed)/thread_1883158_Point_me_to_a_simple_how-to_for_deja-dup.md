---
title: "Point me to a simple how-to for deja-dup"
date: 2011-11-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2011-11-18
I'm trying to figure out deja-dup as part of my "classic w/o effects" project and I'm really confused :confused:

The man pages are too complex and I'm both finding too much info that I'm unsure of, and a lack of info that relates to my personal needs :(

---

### Post by effenberg0x0 on 2011-11-18
> **kansasnoob said:**
> I'm trying to figure out deja-dup as part of my "classic w/o effects" project and I'm really confused :confused:

The man pages are too complex and I'm both finding too much info that I'm unsure of, and a lack of info that relates to my personal needs :(

Hey Kansasnoob, I don't use this tool, but it's just a GUI over the command duplicity. I have used only basic commands of duplicity like:

Full backup my local home folder to my network backup folder
duplicity /home/ahsl file:///media/nas/ahsl/backup

Incremental backup of my local home folder to my network backup folder
duplicity inc /home/ahsl file:///media/nas/ahsl/backup

Full backup my local home folder, excluding my ISOs directory, to my network backup duplicity --exclude /home/ahsl/Downloads/ISO /home/ahsl file:///media/nas/ahsl/backup
duplicity /home/ahsl file:///media/nas/ahsl/backup

Backup of all the local home folders, excluding the test user:
duplicity full --exclude /home/test /home file:///media/nas/ahsl/backup

To restore: change the order (first the destination previously used / URL format, and then the directory). E.g.
duplicity file:///media/nas/ahsl/backup /home/ahsl

There's a million options more, like encryption, etc. But I really have never used them. These basic stuff was enough for me. (I had some duplicity incremental backup commands in a script that was invoked by cron every hour).

I imagine you want to backup a couple of "dot" files within the user $HOME, right? Wouldn't it be a lot easier to just tar.gz them? After all, who knows if the guy already uninstalled deja dup or something like that.

sudo tar -zcvf /var/backups/classic-look.tar.gz $HOME/.??*

**EDIT: **It really is hard to go through all those man pages... I just happened to see the magic word **regexp** while holding PgDown lol. Now that would help.If you really want to use Deja Dup to gest that dot files, you can probably tell it to exclude files tha start with a letter (and not with a dot). Like **"^[(a-z)(A-Z)]"**.

---

### Post by kansasnoob on 2011-11-19
I marked this solved, but I've decided that 'deja-dup' is not the answer for me.

I'll post more in the classic megathread.

---

### Post by Canaryguy on 2011-12-13
What do you want to do exactly? What I have done with Deja-Dup in Ubuntu 11.10 is to backup all my home folder in an external hard disk and to update that backup every now and then
.
Now what I don't know is if I make a fresh installation of Ubuntu and I restore my home folder from the backup I'll recover also the programs that I had installed or only my files. I've noticed that it saves Firefox configurations (bookmarks and preferences and all) but I don't know if after the restoring process I have again my applications installed like Pidgin, Skype, VLC...

---

### Post by kansasnoob on 2011-12-13
> **Canaryguy said:**
> What do you want to do exactly? What I have done with Deja-Dup in Ubuntu 11.10 is to backup all my home folder in an external hard disk and to update that backup every now and then
.
Now what I don't know is if I make a fresh installation of Ubuntu and I restore my home folder from the backup I'll recover also the programs that I had installed or only my files. I've noticed that it saves Firefox configurations (bookmarks and preferences and all) but I don't know if after the restoring process I have again my applications installed like Pidgin, Skype, VLC...

I've decided Deja-Dup is just not really designed for me, not that it's poorly designed, just that I'm set in my ways ;)

But in regards to this;

> if I make a fresh installation of Ubuntu and I restore my home folder from the backup I'll recover also the programs that I had installed or only my files. I've noticed that it saves Firefox configurations (bookmarks and preferences and all) but I don't know if after the restoring process I have again my applications installed like Pidgin, Skype, VLC...

Your home folder does NOT contain "installed apps/programs", it only contains personal info and/or configuration files/folders. So you do still need to reinstall those apps that are not installed by default.

I always create somewhat of a barbaric script (that's not really a script) where I install any known needed PPA's or extras like Medibuntu and then a simple command like "sudo apt-get install app1 app2 app3 etc etc".

But, with the change from Gnome 2 to Gnome 3 (and gtk2 to gtk3), I'm finding that in both Oneiric and Precise that it's actually best to go one step at a time - not because of breakage - but the Canonical devs are simply fixing bugs so fast ATM it makes many of my "known work-arounds" totally obsolete.

I've been doing early testing since Hardy and I've never in all that time seen the devs so focused on fixing bugs this early in a dev cycle. I'm now ashamed that I criticized the name Precise :redface:

I think Canonical/Ubuntu is gonna knock this one out of the park :guitar:

---

### Post by effenberg0x0 on 2011-12-13
> **Canaryguy said:**
>  Now what I don't know is if I make a fresh installation of Ubuntu and I restore my home folder from the backup I'll recover also the programs that I had installed or only my files. I've noticed that it saves Firefox configurations (bookmarks and preferences and all) but I don't know if after the restoring process I have again my applications installed like Pidgin, Skype, VLC...

@canaryguy Linux is a multi-user operating system. Programs are _usually_ stored at default locations and per-user settings are stored at their homes, while global settings are inside /etc. So no, if you restore home from a backup, you won't get your programs back. You'll have to reinstall them.

@everyone
Given that Ubuntu provides a tool aimed at making the act of backup easy  and WYSIWYG for the average-user, there are two different uses / backup  strategies users will eventually try:
 
 1) Backup of home normal files, or of specific content folder, not  including dot files. I won't discuss it because it is standard, no big  deal.
 2) Backup of programs and their config files, believing they can be restored in a working state at the same or a new install of Ubuntu. 
 
I see a problem here with strategy 2. Others may correct me if I'm wrong. Backing up $HOME dotfiles only makes  sense if the programs that use them are also backed up. Why?
- Version conflict: Software reinstalled from repos may require new config file options
- Is anyone really gonna go selective and look at all dotfiles and /etc to make a list of  the programs that should be individually backed up? And do that at  every new backup? No.
  - What about /etc? How to filter what to backup / what not to backup?
 - More complicated: Is anyone gonna backup gconf/dconf? I think that's a terrible idea.
 - Every time you do a new backup, you'll have to look again at which new programs you have installed, which config they use, etc to change the backup setup? Well, that kills the idea of automatic or incremental.

Alternatives
- Bulk approach: Backup installed packages (burns unnecessary storage space).
- System-wide backup. Impossible to keep hourly/daily/weekly snapshots for the average user (easily exceed some TBs, according to my own experience). Backups are too big and slow and so is the restore of single files.

Mid to advanced users will script something using cron+tar+rsync-whatever that will fit what they want/need perfectly and efficiently. Average users will:

- Setup the backup program in an inefficient way (backup $HOME). Restore will create problems.
- Setup the backup program in a way that snapshots fill the HDD in a week (whole system backup). My personal daily-snapshot (7-day keep) folder in the NAS has 16TB today. But most people don't have a storage server in the network.

If I'm right, unless someone codes a way to detect which programs  are installed in the user PC, which config files these programs use and  only then proceed to a very well-thought and selective way to backup only these files, there's no out-of-the-box  easy/bulletproof approach to system backup/restore for the average user. Backup will sort of work. Restore will be problematic, which is disappointing.

So, considering we don't have it now, how useful is it to provide any backup tool installed as a default, if not to make the forum Google Analytics report greater audience (support  for failed restore / full disk)? 

I probably am missing something... would like to hear other opinions.

---

### Post by cariboo on 2011-12-13
[OneConf]("https://wiki.ubuntu.com/OneConf"), once it works properly should allow you to duplicate your installation on as many systems as you want. It works in conjunction with The Software Center and UbuntuOne.

Once you've done your initial installation, you go to the Software Center and use the configuration file to install all the extra packages you need.

---

### Post by grahammechanical on 2011-12-13
I have a point to make.

If I do fresh install of the OS to the / partition and then re-install my usual (non-default) programs then I may still get this anyway:

> - Version conflict: Software reinstalled from repos may require new config file options

Why? Because I did not format /home. I backed up /home as a precaution but it was not needed.

It is a while since I formatted /home. I may do it when I do a fresh install of 12.04 on my working partition just because I think that a clear out every once in a while avoids config file conflicts.

I would say that if a program has changed its way of working dramatically then the developers would need to take into account the need to transfer certain settings from the old version into the new version or the users of the program would be very unhappy.

I did not notice any problem like this when Libreoffice took over my files from Openoffice.

I once solved a problem I had running a program under wine by renaming the .wine folder and letting wine create a new .wine folder and I re-installed the problem Windows program.

So, I do understand what you mean about not backing up dot folders. My sister's Vista laptop has a 160GB disk but only half is available to the OS. The other half is set aside, I assume, for system backup/restore points. Let us not go down that route.

Backup important data. Re-istall software. And re-configure. And get used to it.

Regards.

---

### Post by effenberg0x0 on 2011-12-14
> **cariboo907 said:**
> [OneConf]("https://wiki.ubuntu.com/OneConf"), once it works properly should allow you to duplicate your installation on as many systems as you want. It works in conjunction with The Software Center and UbuntuOne.

Once you've done your initial installation, you go to the Software Center and use the configuration file to install all the extra packages you need.

Yes, that's something I'm looking forward to. It's a smarter approach to record the information of programs, versions and configs instead of the real files. I have no idea about it's maturity though. Hopefully it will be available soon. Actually if there's a way to implement this on a lan (save the different profiles of every PC in a local server that apt-proxies the packages) it would be fantastic. There probably is some tool like that, I'll search for it when I got some time. 

But, meanwhile, considering the traditional local backup tools we have (backintime, dejadup, etc). I don't see a viable way an average-user can accomplish a system-wide backup with, say, daily snapshots and a 7-day archive in a 320GB HDD, taking under consideration time to backup, time to restore and chance of of restoring in a fast-and-guaranteed-restore-of-the-previous-state way.

---

### Post by effenberg0x0 on 2011-12-14
> **grahammechanical said:**
> I have a point to make.

If I do fresh install of the OS to the / partition and then re-install my usual (non-default) programs then I may still get this anyway:



Why? Because I did not format /home. I backed up /home as a precaution but it was not needed.

It is a while since I formatted /home. I may do it when I do a fresh install of 12.04 on my working partition just because I think that a clear out every once in a while avoids config file conflicts.

I would say that if a program has changed its way of working dramatically then the developers would need to take into account the need to transfer certain settings from the old version into the new version or the users of the program would be very unhappy.

I did not notice any problem like this when Libreoffice took over my files from Openoffice.

I once solved a problem I had running a program under wine by renaming the .wine folder and letting wine create a new .wine folder and I re-installed the problem Windows program.

So, I do understand what you mean about not backing up dot folders. My sister's Vista laptop has a 160GB disk but only half is available to the OS. The other half is set aside, I assume, for system backup/restore points. Let us not go down that route.

Backup important data. Re-istall software. And re-configure. And get used to it.

Regards.

Yeah, you're right. It does demand some work. It's not something my mother would do by herself without calling me (as a very real example) :)
Sometimes I have tried to create another user, to have a different home and newer config files, etc. But, in the end, things get messy anyway when you start diffing and moving config files from one home to another, etc... Totally doable, of course, but it's not something you can call easy and painless.

---

