---
title: "Howto: Back up your entire system using TAR"
date: 2012-08-28
forum: Tutorials
---

### Post by newb85 on 2012-08-28
**Preface**
The overall concept for this tutorial came from the howto by Heliode.  My reasons for creating a new howto are several.  His tutorial was created seven years ago, when Hoary was the latest release.  He hasn't been active on the forums in nearly five years.  He leaves out critical steps, resulting in a method that is not reliable.  Moreover, that thread has nearly 1400 replies, many of which have nothing to do with using [FONT=Ubuntu Mono]tar[/FONT] to back up a system.
 I give this tutorial two objectives: to familiarize you with the [FONT=Ubuntu Mono]tar[/FONT] command, and then to expound on approaches to backing up your system using [FONT=Ubuntu Mono]tar[/FONT].  Please note that using [FONT=Ubuntu Mono]tar[/FONT] to backup an entire system is not for the faint of heart, nor is it something to be taken lightly.  The behavior of [FONT=Ubuntu Mono]tar[/FONT] is not always intuitive, and wrong assumptions can lead to the loss of data.   
 For that reason several important nuances of [FONT=Ubuntu Mono]tar[/FONT] are demonstrated within the examples.  These examples are for educational purposes, and I expect it would be beneficial for the average reader to run them.  They only affect a sample directory within the [FONT=Ubuntu Mono]/home[/FONT] directory, so if they're run correctly, they shouldn't affect the rest of the system.  
 However, I will not provide lines of code that I expect readers to copy-and-paste to back up their entire system.  My examples and suggestions will have to be tailored to meet your specific situation and needs.
 I start with the assumption that the reader is familiar and a somewhat comfortable with executing commands in the terminal.  To those who are not, I recommend reading the documentation here.  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
 [B]
Introduction to TAR[/B]
[FONT=Ubuntu Mono]tar[/FONT] is a simple yet very powerful archiving tool.  It stands for Tape ARchiver, which should tell you how long it's been around.  (Tape drives fell into disuse some while ago...)  If you've ever downloaded a file you had to extract (or “unzip”, to use Windows terminology) in Ubuntu, you probably used Archive Manager, which is built on [FONT=Ubuntu Mono]tar[/FONT].
 When the [FONT=Ubuntu Mono]tar[/FONT] command is issued, it requires one “option” to set the operation mode.  There are nine operation modes, but I will only cover a three of them.  All options of tar are in the man page, which can be viewed by issuing the command [FONT=Ubuntu Mono]**man tar**[/FONT].
 
Create (create an archive)
 Function Letter: [FONT=Ubuntu Mono]c[/FONT]
 Long handle: [FONT=Ubuntu Mono]--create[/FONT]
 
 Extract (extract or unpack an archive)
 Function Letter: [FONT=Ubuntu Mono]x[/FONT]
 Long handles: [FONT=Ubuntu Mono]--extract[/FONT] [FONT=Ubuntu Mono]--get[/FONT]
 
List (spits out a list of all the contents of an archive)
 Function Letter: [FONT=Ubuntu Mono]t[/FONT]
 Long handle: [FONT=Ubuntu Mono]--list[/FONT]
 
 For demonstration purposes, I create a folder [FONT=Ubuntu Mono]tartest[/FONT] with a few sample documents.
 
 ```
aaron@aaron-Satellite-P755:~$ mkdir Documents/tartest
aaron@aaron-Satellite-P755:~$ cd tartest
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch acerbic.odt biting.odp \
> scathing.txt tangy.ods
aaron@aaron-Satellite-P755:~/Documents/tartest$ mkdir piquant
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch piquant/acidulous \
> piquant/trenchant
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  biting.odp  piquant  scathing.txt  tangy.ods 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls piquant 
acidulous  trenchant  

```My goal is to back [FONT=Ubuntu Mono]tartest[/FONT] up in an archive within a directory [FONT=Ubuntu Mono]backup,[/FONT] but I don't want the archive to include the archive, which will be contained within [FONT=Ubuntu Mono]tartest.[/FONT]
 
Exclude (exclude a file matching PATTERN from the archive)
 Long handle:  --exclude PATTERN
 
 File (designate the archive file—yeah, this one's important)
 Function letter: [FONT=Ubuntu Mono]f[/FONT]
 Long handle: [FONT=Ubuntu Mono]--file[/FONT]
 
 Preserve permissions (leave dates, ownership, and permissions unchanged)
 Function letter: [FONT=Ubuntu Mono]p[/FONT]
 Long handles: [FONT=Ubuntu Mono]--preserve-permissions[/FONT] [FONT=Ubuntu Mono]--same-permissions[/FONT]
 
In the following steps, I'll create the directory [FONT=Ubuntu Mono]backup[/FONT], then create an archive of everything in [FONT=Ubuntu Mono]tartest[/FONT] except for [FONT=Ubuntu Mono]backup[/FONT], delete the file [FONT=Ubuntu Mono]scathing.txt[/FONT], then restore [FONT=Ubuntu Mono]tartest[/FONT] from the archive (thereby restoring [FONT=Ubuntu Mono]scathing.txt[/FONT]).
 
 ```
aaron@aaron-Satellite-P755:~/Documents/tartest$ mkdir backup 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar cpf backup/backup1.tar \ 
> --exclude backup . 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar tf backup/backup1.tar 
./ 
./tangy.ods 
./piquant/ 
./piquant/trenchant 
./piquant/acidulous 
./acerbic.odt 
./scathing.txt 
./biting.odp 
aaron@aaron-Satellite-P755:~/Documents/tartest$ rm scathing.txt 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  backup  biting.odp  piquant  tangy.ods 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar xpf backup/backup1.tar 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  backup  biting.odp  piquant  scathing.txt  tangy.ods  
 Success!  Everything worked as expected.  Now I delete tangy.ods and create caustic.odt, followed by another restore of tartest.
 aaron@aaron-Satellite-P755:~/Documents/tartest$ rm tangy.ods 
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch caustic.odt 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  backup  biting.odp  caustic.odt  piquant  scathing.txt 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar xpf backup/backup1.tar 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  backup  biting.odp  caustic.odt  piquant  scathing.txt  tangy.ods  
```Notice that after the restore, [FONT=Ubuntu Mono]caustic.odt[/FONT] persists.  By default, [FONT=Ubuntu Mono]tar[/FONT] doesn't do any comparing.  In extract mode, it simply creates every file represented within the archive.  An effective backup and restore method needs to keep track of both what should be there and what should not be there.
 [B]
Listed Backups[/B]

 Listed Incremental (handle incremental backups based on list FILE)
 Function Letter: [FONT=Ubuntu Mono]g[/FONT]
 Long Handle: [FONT=Ubuntu Mono]--listed-incremental FILE[/FONT]
 
 I won't address incremental backups yet, but for the moment the important thing to note is that this option changes the behavior of [FONT=Ubuntu Mono]tar[/FONT] so that it uses a list file for comparison, and in extract mode removes the files that shouldn't be there.  Observe.
 
 ```
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar cpf backup/backup2.tar \ 
> -g backup/backup2.snar --exclude backup . 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar tf backup/backup2.tar 
./ 
./piquant/ 
./acerbic.odt 
./biting.odp 
./caustic.odt 
./scathing.txt 
./tangy.ods 
./piquant/acidulous 
./piquant/trenchant 
aaron@aaron-Satellite-P755:~/Documents/tartest$ rm biting.odp 
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch snappish.odp 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  caustic.odt  scathing.txt  tangy.ods 
backup       piquant      snappish.odp 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar xpf backup/backup2.tar \ 
> -g backup/backup2.snar 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  backup  biting.odp  caustic.odt  piquant  scathing.txt  tangy.ods
``` [B]

Multiple Exclusions[/B]
There's another limitation of [FONT=Ubuntu Mono]tar[/FONT] that I've found to be very poorly documented.  [FONT=Ubuntu Mono]tar[/FONT] is not very good at accepting multiple [FONT=Ubuntu Mono]--exclude[/FONT] options.  I haven't found documentation giving a limit to how many it will accept, and in my experience, the number it accepts is inconsistent.  The result of giving too many is that the last [FONT=Ubuntu Mono]--exclude[/FONT] options are ignored with no warnings.  When excluding multiple files or directories, I recommend using one or both of the following alternatives.
 
 Exclude-from (excludes files listed in FILE from the archive)
 Function letter: [FONT=Ubuntu Mono]X[/FONT] (not to be confused with [FONT=Ubuntu Mono]x[/FONT])
 Long handle: [FONT=Ubuntu Mono]--exclude-from FILE[/FONT]
 
 Exclude-tag-all (excludes all directories containing FILE from the archive)
 Long handle: [FONT=Ubuntu Mono]--exclude-tag-all FILE[/FONT]
 
To demonstrate the Exclude-from option, I've added the file [FONT=Ubuntu Mono]exclusions.txt[/FONT] in the [FONT=Ubuntu Mono]backup[/FONT] directory to exclude the directory piquant.
 
To demonstrate the Exclude-tag-all option I will add the file [FONT=Ubuntu Mono]backup.excl.tag[/FONT] to the directory [FONT=Ubuntu Mono]backup[/FONT].
 
 ```
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch backup/backup.excl.tag 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar cpf backup/backup3.tar \ 
> -g backup/backup3.snar -X backup/exclusions.txt \ 
> --exclude-tag-all backup.excl.tag . 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar tf backup/backup3.tar 
./ 
./acerbic.odt 
./biting.odp 
./caustic.odt 
./scathing.txt 
./tangy.ods
```Both exclude-from and exclude-tag-all have their merits and drawbacks.  Exclude-tag-all requires that a tag file be placed in each folder to be excluded.  When backing up an entire system, some system directories need to be excluded (to be discussed later), and it's not a good idea to add a tag file in those directories.  For those, exclude-from is invaluable.  However, there may be directories that one only wants to exclude sometimes.  In those cases, those folders may be tagged with descriptive tag files that can be used when appropriate (also to be discussed later).
 [B]
Compression[/B]
Now, all this is well and good as far as backing up a small sample directory goes.  However, when backing up something the size of an entire system, drive space has potential to be an issue.  Fortunately, tar has many built-in compression options.  The two most widely used are gzip and bzip2, but one can read about the rest on the man page.
 
Gzip (use the gzip compression format)
 Function letter: [FONT=Ubuntu Mono]g[/FONT]
 Long handle: [FONT=Ubuntu Mono]--gzip[/FONT]
 (Note that for gzip files, the suffixes [FONT=Ubuntu Mono].tar.gz[/FONT] and [FONT=Ubuntu Mono].tgz[/FONT] are both acceptable, but [FONT=Ubuntu Mono].tgz[/FONT] is more commonly used.)
 
 Bzip (use the bzip2 compression format)
 Function letter: [FONT=Ubuntu Mono]j[/FONT]
 Long handle: [FONT=Ubuntu Mono]--bzip2[/FONT]
 (Note that for bzip files, the suffixes [FONT=Ubuntu Mono].tar.bz[/FONT] and [FONT=Ubuntu Mono].tbz[/FONT] are both acceptable, but [FONT=Ubuntu Mono].tbz[/FONT] is more commonly used.)
 
Auto-compress (uses the compression format indicated by the file suffix)
 Function letter: [FONT=Ubuntu Mono]a[/FONT]
 Long handle: [FONT=Ubuntu Mono]--auto-compress[/FONT]
 
In general, it's a good idea to use auto-compress.  [FONT=Ubuntu Mono]tar[/FONT] would be more than happy to create an archive with the wrong suffix (or even no suffix) if you told it to, which could lead to confusion down the road.  Auto-compress ensures that the file suffix and the actual compression method match.
 
 ```
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar capf backup/backup4.tgz \ 
> -g backup/backup4.snar -X backup/exclusions.txt \ 
> --exclude-tag-all backup.excl.tag . 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar tf backup/backup4.tgz 
./ 
./acerbic.odt 
./biting.odp 
./caustic.odt 
./scathing.txt 
./tangy.ods
``` [B]
Incremental Backups[/B]
Earlier we started using the listed-incremental option because it created an index so that the exact state of the file system could be restored.  However, there are a couple more benefits to this option.
 First, creating a backup that is a snapshot of the entire system can tie up resources for a while and take a good chunk of storage space.  Much of this time and space can be saved by creating an incremental backup—a backup that only tracks the changes from a previous backup.
 In my previous examples creating an archive with [FONT=Ubuntu Mono]-g[/FONT], the index files were files that did not yet exist.  However, if the index file already exists [FONT=Ubuntu Mono]tar[/FONT]'s behavior changes.  It starts by comparing the index file with the system, and any files that have been added or modified in the system are placed in a new archive.  Then, the index file is updated to reflect the current state of the system.
 
 ```
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch pungent.odt 
aaron@aaron-Satellite-P755:~/Documents/tartest$ cp backup/backup4.snar \ 
> backup/backup5.snar 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar capf backup/backup5.tgz \ 
> -g backup/backup5.snar -X backup/exclusions.txt \ 
> --exclude-tag-all backup.excl.tag . 
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar tf backup/backup5.tgz 
./ 
./pungent.odt 
aaron@aaron-Satellite-P755:~/Documents/tartest$ rm pungent.odt biting.odp 
aaron@aaron-Satellite-P755:~/Documents/tartest$ touch acetose.ods 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  acetose.ods  backup  caustic.odt  piquant  scathing.txt  tangy.ods
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar xpf backup/backup4.tgz \ 
> -g backup/backup4.snar 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  backup  biting.odp  caustic.odt  piquant  scathing.txt  tangy.ods
aaron@aaron-Satellite-P755:~/Documents/tartest$ tar xpf backup/backup5.tgz \ 
> -g backup/backup5.snar 
aaron@aaron-Satellite-P755:~/Documents/tartest$ ls 
acerbic.odt  biting.odp   piquant      scathing.txt
backup       caustic.odt  pungent.odt  tangy.ods
```The most common incremental backup paradigm is chain incremental backups, where each incremental backup is the difference from the previous backup.  An alternative is baseline incremental backups, where each incremental backup is the difference from the last full backup.  The baseline paradigm will take a little longer to back up the further you get from the last full backup, but it has the advantage that restoring your system will only require extraction of the last full backup and the last incremental backup.
 [B]
Housekeeping[/B]
In all examples, I was very careful to exclude directories, not just the contents of the directories.  When using listed backups, this is important, because otherwise extraction will remove some or all of the contents of those directories.
 I also ran all [FONT=Ubuntu Mono]tar[/FONT] commands from within the top directory to be backed up ([FONT=Ubuntu Mono]tartest[/FONT]).  If they were run with different working directories, but the resulting [FONT=Ubuntu Mono].tar[/FONT] files would look different.
 [B]
Things to know about backing up an entire system[/B]
Of course, creating a backup of your system within your system provides limited security.  A HDD crash could wipe out your system and your backup in one fell swoop.  System backups should be placed outside the system partition, or better yet, on an entirely different HDD.  This will require you to learn the path to the backup location.  On the other hand, having the [FONT=Ubuntu Mono]backup[/FONT] directory outside the system will mean you don't need to worry about excluding it.
 Before moving on from a test folder to the entire system, there are a few things to know.  First, normal users don't by default have permissions to create or modify files outside their home directory, so commands will need to be executed as root.  You could change the permissions of your [FONT=Ubuntu Mono]backup[/FONT] directory to allow everyone to write to it.  That way, root permissions would only be needed for restoring your system.
 In modern Linux distros [FONT=Ubuntu Mono]/proc[/FONT], [FONT=Ubuntu Mono]/sys[/FONT], and [FONT=Ubuntu Mono]/dev[/FONT] are all virtual filesystems.  This concept is similar to a mounted partition, but in the case of these three directories, the contents (which don't really exist on any hard drive) are merely way of presenting information from the kernel—information that exists on RAM.  (If one were to boot from a live CD and examine these directories on the hard drive, they would find them completely empty.)  It is not necessary to back up or restore the contents of these directories; moreover, it is not a good idea to add to or modify them.  They should therefore be excluded from all archives.  (These are the folders I mentioned should not be excluded using exclude-tag-all.)
 I have read some recommendations that the [FONT=Ubuntu Mono]/lost+found[/FONT] directory also be excluded.  I disagree.  The pedant's argument is that it would be chronologically incorrect to exclude it.  The pragmatist's argument is that in the unlikely event that the disk check puts a file in [FONT=Ubuntu Mono]/lost+found[/FONT], it's unlikely it will be modified or removed (or needed, for that matter).  Really, at the end of the day, whether /lost+found is excluded will be inconsequential.
 One should always be mindful of what partitions and drives are being backed up and restored.  Typically, other HDD partitions are mounted to the [FONT=Ubuntu Mono]/mnt[/FONT] directory.    Removable media (such as CDs and USB drives) are mounted to the [FONT=Ubuntu Mono]/media[/FONT] directory.  You will probably want to exclude both from your backups.  Note that while it is possible to include Linux installs on other partitions, including Windows or Mac installs is futile.  Their closed-system formats make it impossible to even read many system files.  Backup software intended for those operating systems will have to be used.
 If you're restoring to the same HDD with all the partitions unchanged, everything should be up and running.  Otherwise, you may have to restore your grub (recommended reading: [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)) and fix your fstab to reflect the new situation.
 [B]
Suggestions[/B]
I will wrap up with a few ideas to consider:
 
[LIST]
[*]Given that     compression is ineffective on most media files, you could back up     folders like [FONT=Ubuntu Mono]~/Music[/FONT] and [FONT=Ubuntu Mono]~/Videos[/FONT]     in separate archives.
[*]If you plan to     back up regularly, creating a shell script for backing up would save     time and cut down the risk of entering the command wrong.
[*]You could also use     [FONT=Ubuntu Mono]cron[/FONT] to schedule the backups.
[*]The first time you     create a backup of the entire system, it would be a good idea to     check the backup to be sure it contains what it's supposed to.  The     file will be large, and depending on your system it may take Archive     Manager a long time to open.  As an alternative, you could run tar     in list mode and have it output to a [FONT=Ubuntu Mono].txt[/FONT]     file.
[/LIST]

---

