---
title: "backup all users files - please help !!!"
date: 2007-02-05
forum: Server Platforms
---

### Post by neill on 2007-02-05
hi

i want to do something quite simple - i thought !! - backup all the users on my fileserver

it's driving nuts- i can't get it to do what i want


the backup destination is a NAS device, statically mounted in fstab with

\\192.168.0.5\backup_share  /mnt/backup/nas cifs defaults,passwd= 0 0

what i want my backup to do is reproduce /home on the NAS

i need to run the job nightly, snapshot style would be nice (say keeping a weeks worth with hardlinks to save space) and i want to be able to restore using standard file management tools

also all permissions/ownerships should be preserved - so if i have to copy a chunk back i don't have to change all the permissions back again

can i do it ...................... ](*,) 

pdumpfs, faubackup - all generate a ream of error messages and save files as root owned

sbackup - compresses the files (which i want to avoid) and saves them as root owned

rdiff-backup - throws off errors and won't actually save *anything *to the backup directory at all

i'm sure there is some simple way to backup - effectively mirror - /home to /mnt/backup such that the files are all saved 'as is' - not compressed, not archived and with all the original ownerships intact

can anyone help me ????

thanks

neill

---

### Post by yabbadabbadont on 2007-02-05
You might try using the good old "tar" utility.  Usually tar archives are compressed, but they don't have to be.  You'll need to do some research on the various options to make sure that everything is saved and restored the way you expect.  (mainly you need the "--same-permissions --same-owner" options when restoring)

To create a backup: sudo tar cvf /mnt/backup/nas/yyyymmdd-home-backup.tar /home
(you may want to leave off the 'v' verbose option, unless you like watching the filenames scroll by :))

To restore a backup: sudo tar xvf /mnt/backup/nas/yyyymmdd-home-backup.tar -C /
(again, you can leave off the 'v' if you like)

If you wish to have fairly quick compression enabled, just add the 'z' gzip option to the create and restore commands and change the backup file name to be like yyyymmdd-home-backup.tar.gz

---

### Post by jtc on 2007-02-05
Here comes my usual advice in cases like this :-)

[rsnapshot]("http://www.rsnapshot.org/")

---

### Post by neill on 2007-02-05
i hadn't thought about doing it manually - like just writing a tar command - so i'll look into that

ditto rsnapshot - i've had a quick look at rsnapshot.org and superficially it seems likely to do what i want so again i'll research and feedback

thanks for being so fast :)

---

### Post by yabbadabbadont on 2007-02-05
> **jtc said:**
> Here comes my usual advice in cases like this :-)

[rsnapshot]("http://www.rsnapshot.org/")

rsnapshot's homepage claims that they use hardlinks while backing up to a remote (or different local) filesystem.  Everything I've ever seen, tried, and read tells me that you can't create hard links across filesystems....  I'm sure I've just misunderstood what they are doing.  :-k

---

### Post by jtc on 2007-02-05
Message removed. I'll come back when I know when I've gotten my beauty-sleep

---

### Post by yabbadabbadont on 2007-02-05
> **jtc said:**
> You are right, you misunderstood :p

...or I guess it depends on how you define "remote (or different local) filesystem"

An externally mounted usb-drive? Yes can do that.
Send it through ssh/scp, like username@host:/file? No, you can't do that.
A more transparrent remote mount, liks nfs or sshfs. I'm not sure, but I agree it would probably not be a good idea.

Anyhow, the basic usage of rsnapshot is to fetch files locally and/or from remote sites and backup it locally.

I see.  So basically, rsnapshot isn't recommended in this case given that the OP said that the backups are sent across the network to a storage device that is mounted using cifs...  ;)

---

### Post by jtc on 2007-02-06
Bummer, didn't delete that quick enough :)

Ohh well, now I've slept and hopefully I think more clearly.

Still, I have to admit I'm not sure whatever hard links, etc across a CIFS-mount is is a good idea or not. 

**neill:** Sorry about answering without thinking it through completely. Rsnapshot might still be a good solution in your case, but it isn't something I know for sure it is.

---

### Post by neill on 2007-02-06
a lot of these backup solutions use linking of some sort to reduce backup space

i know that pdumpfs and faubackup do certainly - maybe that's my problem ?

certainly when i try these solutions on a local filesystem i have none of these problems

so maybe i need to look at rsync or persevere with rdiff-backup

:confused:

---

### Post by neill on 2007-02-08
OK i think i fixed it

my NAS was using CIFS to serve the shares

i changed this to NFS and - shazaam !! - the problems disappeared

now all the various backup solutions which use some form of linking for 'snapshots' all seem to work as they should

thanks for the input :)

---

