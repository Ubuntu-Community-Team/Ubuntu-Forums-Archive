---
title: "mdadm: crashed reshape, missing backup, --invalid-backup flag?"
date: 2013-04-08
forum: Server Platforms
---

### Post by apokkalyps on 2013-04-08
I was reshaping a 5x2tb raid5 to a 6x2tb raid6.  Not knowing that ubuntu deletes the /tmp/ folder each reboot, I specified my --backup-file as /tmp/raid-backup.bak (this is not part of the array).  At 15.1% the system hung sufficiently that REISUB and the reset button were ignored and I had to hold the power button down to reset the server.  After booting back from the crash, the array would not start, and ubuntu had deleted the backup file (and everything else in /tmp).

The superblock already says it's raid6, all members are present and the event counters are the same on all disks.  I tried

```
ubuntu@ubuntu:~$ sudo mdadm --assemble --force --run --verbose
/dev/md0 /dev/sd[abcdef]
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdf is identified as a member of /dev/md0, slot 1.
mdadm:/dev/md0 has an active reshape - checking if critical section
needs to be restored
mdadm: Failed to find backup of critical section
mdadm: Failed to restore critical section for reshape, sorry.
      Possibly you needed to specify the --backup-file
```


My understanding is that the backup file is only for some early critical part of the reshape and that it isn’t even used after that.  15% into 8tb is well over a terrabyte so wouldn’t that be far past any filesystem metadata?  So what exactly is implied (about the state of the reshape) by the fact that programmatically it is still requiring the backup file?

I have read the [manpage]("http://linux.die.net/man/8/mdadm") on the --invalid-backup command but I didn't clearly get "use it here, not here" type of information.  I have the OS drive (with deleted /tmp/raid-backup.bak) in a data recovery process.  If I actually get the backup file recovered, it could potentially have corrupted bits.  Is the best course of action to:
[LIST]
[*]Supply the (potentially corrupted, but maybe some percent ok) recovered backup file as the legitimate backup file (without --invalid-backup)? (could this be worse than --invalid-backup and a blank file?)
[*]Supply the (potentially corrupted) recovered backup file WITH --invalid-backup?
[*]Supply --invalid-backup and an empty file?
[/LIST]

Or if I am on the wrong path, let me know of any other thoughts or suggestions you might have.

Thanks!

---

### Post by rubylaser on 2013-04-08
This sucks.  About the only thing to do at this point is to re-create the array using the same parameters prior to the reshape.  Do you know what order the disks where in and what metadata version you where running? To re-create it properly, you need to have the exact same order and parameters.

Here's an example (note the --assume-clean flag).  This is for the older 0.90 metadata format. 
```
mdadm -CR /dev/md0 --metadata=0.90 -n5 -l5 -c64 /dev/sd[abcde] --assume-clean
```
If your array was built more recently, it was likely using the 1.2 metadata version and as result, would use a different chunk size to (-c option)
```
mdadm -CR /dev/md0 --metadata=1.2 -n5 -l5 -c512 /dev/sd[abcde] --assume-clean
```

Do you have a copy of your /etc/mdadm/mdadm.conf file that you could post?
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by apokkalyps on 2013-04-09
Rubylaser you helped me a lot with this in the [previous episode]("http://ubuntuforums.org/showthread.php?t=2111008") but I made a new thread because after you helped me get the array assembled and it was working, my "re-breaking" it with a reshape sortof made it a new issue.  

That said, I'm not sure where you are going with this re-create idea.  I'm not sure if you are aware but since mdadm 3.2.1 there is an --invalid-backup flag for exactly my situation.

> 
For assemble:
--backup-file=
    If --backup-file was used while reshaping an array (e.g. changing number of devices or chunk size) and the system crashed during the critical section, then the same --backup-file must be presented to --assemble to allow possibly corrupted data to be restored, and the reshape to be completed. 
--invalid-backup
    If the file needed for the above option is not available for any reason an empty file can be given together with this option to indicate that the backup file is invalid. In this case the data that was being rearranged at the time of the crash could be irrecoverably lost, but the rest of the array may still be recoverable. This option should only be used as a last resort if there is no way to recover the backup file. 

This is what I was asking about, as it seems the most promising thing before any kind of array recreation.  I also asked this question on the linux-raid mailing list, and got this response from Neil Brown (the original mdadm designer/author).

Neil Brown on Linux-Raid
> There is no risk in providing an backup file - if it doesn't look good it
will be ignored.

When md does an in-place reshape like this it:
  - read several stripes
  - writes them to the backup file
  - writes them back to the devices
  - updates the metadata

If your crash was during the "writes them back" section, then you will have
some corruption that you cannot avoid without having exactly the right backup
file.

With luck the corruption should be fairly limited.

There is nothing better that you can do then reassemble the array with the
best backup file you can find, and with --invalid-backup.  Then 'fsck' and do
whatever you can to validate your data.

The docs combined with Neil's input gives me a reluctant optimism that even if I cannot get even an iffy version of the backup file, I should be able to supply --invalid-backup with a blank file and limit the damage to a few stripes of data (which would be a GODSEND).  If I can actually get some form of the backup file back from data recovery, the damage could be even less.  Is there another reason why you were suggesting the array recreation path?

Feel free to put my optimism in check. ;p

---

### Post by rubylaser on 2013-04-09
Recreating is non destructive if you pass the --assume-clean flag, and would almost certainly recover your whole array.  This is only re-creating the mdadm metadata and will not effect the data on the disks if you use the --assume-clean flag.  I have not used the --invalid-backup so I can't comment on it's effectiveness.  Why don't you post a question to the [linux raid group]("http://blog.gmane.org/gmane.linux.raid")?  You may even get Neil to help you fix your issue.

---

### Post by apokkalyps on 2013-04-09
I did post this exact question to linux-raid and that quote from Neil was his direct response to me, sorry if that was not clear.  (I made this ubuntuforums post because it took quite a while to get a response on linux-raid...also because there are many smart people here and any informed perspectives I can get are helpful)

As far as recreating the array, no one had mentioned that in the last thread or on IRC or linux-raid, but it is intriguing and I will consider it as an option.

So just to be clear, are you saying that recreating could potentially allow me to bring my array back active and working, even though right now an *assemble --force --run* fails without the backupfile of the critical section?  I assumed that if a force assemble wouldn't work, there were no other options without the backup file (or --invalid-backup flag).

Also, you say recreating will not affect the data on the disk but, presumedly, only the metadata.  Would this prevent me form doing the *assemble --backup-file=foo --invalid-backup* later?  I'm guessing its that same meta-data, which recreating would blow away, which is what might make a reassemble with the backup file work.  

So it seems like I should try the *assemble --backup-file=foo --invalid-backup* first, and if that fails try the recreate.  Is that sensible?

---

### Post by rubylaser on 2013-04-09
If Neil suggested to use the backup-file option, I would use that first (and post your results back here because I'm interested).  If that fails, then you can try to recreate the metadata.

---

