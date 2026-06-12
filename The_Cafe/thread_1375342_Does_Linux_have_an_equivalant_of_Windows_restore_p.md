---
title: "Does Linux have an equivalant of Windows restore point?"
date: 2010-01-07
forum: The Cafe
---

### Post by JohneG on 2010-01-07
If not, why not and how do i sort out my system if anything happens?

---

### Post by NoaHall on 2010-01-07
> **JohneG said:**
> If not, why not and how do i sort out my system if anything happens?

Not really, but you can make back-ups. The way to fix? Either use your GNU/Linux knowledge/skills to fix it by yourself, as I do, or to post on the forums, so we can help you.

---

### Post by scrooge_74 on 2010-01-07
You can always do backups, install the OS in a separate partition from your /home.

No need for a restore point, PCs wont die cause of the software or because of a virus. There are a couple of tools but I havent use them.

I know for instance Open Solaris file system handles restore points in a nice way.

---

### Post by earthpigg on 2010-01-07
> **JohneG said:**
> why not

not as such, no.

>  and how do i sort out my system if anything happens?

identify the problem and fix it, with the help of ubuntuforums.org.

catastrophic failures *a la Windows* are very uncommon...

...and most settings that could go awry are stored in some plain text file somewhere on the system. even if the system doesn't boot, you can pop in a LiveCD and access those files.

the other common breakage is a kernel update that borks your system. ubuntu automatically keeps the old kernels -- look at your grub menu.


and as for truly catastrophic failures? don't play around with 'chown -r' and commands like that, and you don't have to worry.


that covers things that can truly break the system. as for personal settings for specific user programs? also stored in plain text files. run this command to see: "ls -a ~"

since these are mostly only text files that dont take up much space, you can back them up once a week or so. make it an automated cron job if you want.

---

### Post by juancarlospaco on 2010-01-07
Get Back In Time, or if you need remote, use RSnapshot.

---

### Post by matthew.ball on 2010-01-07
> **scrooge_74 said:**
> You can always do backups, install the OS in a separate partition from your /home.
If you go this route, I have some backup/restore bash scripts which will export/import a list of installed packages, copy/restore fstab and sources.list.

It's effectively a restore point, though I have used it more or less when upgrading distros (I always do a complete re-install, and remembering what packages I have installed, what download sources, and my fstab details is tedious).
If you're interested send me a PM with your email and I'll send it over. It's 2 pretty simple scripts, just some copying and some dpkg --get[set]-selections, but it does the job.

It wouldn't be very practical without a separate /home partition though (it doesn't save any data per say).

---

### Post by FuturePilot on 2010-01-07
Something may be possible once we get BTRFS [https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs]("https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs")

---

### Post by earthpigg on 2010-01-08
> If you're interested send me a PM with your email and I'll send it over.

no reason you can't post them here as an attachment to your post :D

---

### Post by Techsnap on 2010-01-08
I think Mandriva has a feature which is similar to Windows Restore, not certain though but it used to I'm sure.

---

### Post by Xbehave on 2010-01-08
> **FuturePilot said:**
> Something may be possible once we get BTRFS [https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs]("https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs")
BTRFS offers a way to do this inside the filesystem, but currently you can use LVM snapshots on any filesystem (i think you need to use rsync to restore, because remerging isn't available yet). But by far the easiest solution is backups.

---

### Post by ColeNi on 2010-01-08
> **earthpigg said:**
> not as such, no.



identify the problem and fix it, with the help of ubuntuforums.org.

catastrophic failures *a la Windows* are very uncommon...

...and most settings that could go awry are stored in some plain text file somewhere on the system. even if the system doesn't boot, you can pop in a LiveCD and access those files.

the other common breakage is a kernel update that borks your system. ubuntu automatically keeps the old kernels -- look at your grub menu.


and as for truly catastrophic failures? don't play around with 'chown -r' and commands like that, and you don't have to worry.


that covers things that can truly break the system. as for personal settings for specific user programs? also stored in plain text files. run this command to see: "ls -a ~"

since these are mostly only text files that dont take up much space, you can back them up once a week or so. make it an automated cron job if you want.

What is an "automated cron job" and how would I go about setting one up to backup these text files? I'm quite new to Ubuntu so if someone responds, please try to speak in simple language, thanks...

EDIT: Found a really good howto for how to backup and restore your files...not quite the same thing but that'll work for me.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by juancarlospaco on 2010-01-08
RSnapshot can make Snapshot of an EXT4 filesystem as is

---

### Post by betrunkenaffe on 2010-01-08
No, you can backup / and have /home on it's own partition and if anything happens, copy your backed up / over the messed up one..

Or you can do as I did when I accidentally deleted all my kernels when installing something (I don't know how I did it) and just do a reinstall and quick install of all the missing programs. Took me around 20 minutes.

---

### Post by betrunkenaffe on 2010-01-08
> **ColeNi said:**
> EDIT: Found a really good howto for how to backup and restore your files...not quite the same thing but that'll work for me.

How's it not even better? Restore Point only deals with some system files, it doesn't remove/replace broken files on the HDD which damaged it in the first place.

---

### Post by aaaantoine on 2010-01-08
And speaking of backups, it's time for me to back up my stuff again.  Especially in light of the fact that my friend's hard drive crashed last night and he didn't have any backups...

I have a miniature rsync bash script that does the backing up.  But I only back up /home.  I figure if there's a catastrophic system failure, I'm better off installing the system from scratch anyway.

I couldn't translate my current backup method to backup system files anyway because it rsyncs to a FAT32 filesystem and doesn't preserve file permissions.

Maybe you can just create a tarball of all your stuff and compress it to an external device.  But I seem to remember those files are limited to 4GB.

---

### Post by Exodist on 2010-01-08
> **JohneG said:**
> If not, why not
GNU/Linux was under a different philosophy. 1) You know what your doing, 2)Nothing is locked out from the user, so if there is a bad error. The user can enter the system and correct it without the use of automated restore points. Also practice backing up your software, this is a common practice that many miss for any OS. 



>  and how do i sort out my system if anything happens?Learn what your doing wrong. GNU/Linux again assumes you know what your doing, if your naturally clueless as a frog sitting on a lillypad. GNU/Linux is probably not your best choice of OSs.

---

### Post by mickie.kext on 2010-01-08
Windows System Restore is seriuos candidate for worst feature ever. On any OS. I happen to work with lot of Windows computers, and every time I use (or saw anybody other using) "System restore", damn thing creates more problem than it fixes and always results in having to reinstall Windwos. Sometimes "System restore" completely b0rked the system. Windows would be better OS without it. 

On Linux on the other hand, you make backup just by copying everything from the / drive except **/proc**, **/lost+found** **/mnt** and **/sys**. Those are folders who are gona be re-created anyway and backuping them can only spell troubles.

---

### Post by NoaHall on 2010-01-08
> **mickie.kext said:**
> Windows System Restore is seriuos candidate for worst feature ever. On any OS. I happen to work with lot of Windows computers, and every time I use (or saw anybody other using) "System restore", damn thing creates more problem than it fixes and always results in having to reinstall Windwos. Sometimes "System restore" completely b0rked the system. Windows would be better OS without it. 

On Linux on the other hand, you make backup just by copying everything from the / drive except **/proc**, **/lost+found** **/mnt** and **/sys**. Those are folders who are gona be re-created anyway and backuping them can only spell troubles.

I disagree. If there is not a virus on the system, and they restore it properly - not turning it off half way, it works every time.

---

### Post by forrestcupp on 2010-01-08
> **juancarlospaco said:**
> Get Back In Time, or if you need remote, use RSnapshot.

Lol.  Linux should come with a Delorian and a Flux Capacitor.

---

### Post by chrisinspace on 2010-01-08
I'm with NoaHall.  I actually use it to clear out a Windows virus.  Once those things are embedded into a Windows system, it is practically impossible to repair.  System Restore works so much better than trying to have an AV program clean out the virus.

Not that you're like to have a problem like that in Linux, but you might want to check out [TimeVault]("https://launchpad.net/timevault/").

---

### Post by NoaHall on 2010-01-08
> **chrisinspace said:**
> I'm with NoaHall.  I actually use it to clear out a Windows virus.  Once those things are embedded into a Windows system, it is practically impossible to repair.  System Restore works so much better than trying to have an AV program clean out the virus.

Not that you're like to have a problem like that in Linux, but you might want to check out [TimeVault]("https://launchpad.net/timevault/").

Well, if you have a virus - some infect the restore points. Or rather, aren't removed by restore points.

---

### Post by aaaantoine on 2010-01-08
> **mickie.kext said:**
> On Linux on the other hand, you make backup just by copying everything from the / drive except **/proc**, **/lost+found** **/mnt** and **/sys**. Those are folders who are gona be re-created anyway and backuping them can only spell troubles.

Don't forget **/dev**.  You certainly do *not* want to back /dev up.

Also skip **/media** if you have it, for the same reason you would skip /mnt.

---

### Post by toupeiro on 2010-01-08
For some reasons already mentioned in this thread, system restore points were already very bad ideas for people who didn't take the time to manage them (which is most people on average).  If you get an infection, it starts getting captured in all of your restore points, and like many people, you don't know when you truly first got it.  Good system use practices and some very basic knowledge of backups will keep you from ever having to rely on this.  Those practices will benefit you across any OS  you choose to use now and in the future.

---

### Post by chrisinspace on 2010-01-08
> **NoaHall said:**
> Well, if you have a virus - some infect the restore points. Or rather, aren't removed by restore points.

Yeah...I have come across that before, but System Restore works for me 9 times out of 10.  It works best from Safe Mode.  Some virus writers, however, discovered this and now specifically target restore points.  At that point, I usually do my best to recover the data on the machine, then go with the reinstall.  That's why Windows is IT job security.

---

### Post by matthew.ball on 2010-01-08
> **earthpigg said:**
> no reason you can't post them here as an attachment to your post :D
Ahh, so I can. Awesome.

Ok, so it's just 3 files tar'd up - backup-script, restore-script and README. Hopefully the README explains everything. The only things I can think of to point out are: remember to chmod the scipts. The restore script should be run with su rights. But these are both said in the README.

---

### Post by NoaHall on 2010-01-08
> **matthew.ball said:**
> Ahh, so I can. Awesome.

Ok, so it's just 3 files tar'd up - backup-script, restore-script and README. Hopefully the README explains everything. The only things I can think of to point out are: remember to chmod the scipts. The restore script should be run with su rights. But these are both said in the README.

You could have put the scripts together, then give the user a choice between backup and restore. Or included the variables in a different file.

---

