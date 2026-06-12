---
title: "&quot;Online&quot; backup root directory?"
date: 2011-10-30
forum: Server Platforms
---

### Post by Apple_Eater on 2011-10-30
Hey all,
I am finally switching from a dedicated server to colocation for my personal server. I'm seeking advice on the best way to get a full root backup of the server without having physical access to it.

Best I could come up with would be to move necessary files to a ramdisk, chroot onto the ramdisk, take the root partition offline, and perform the backup at that point. I have already rsync'd the entire root directory of the server to my new server, but since the filesystem was online during the process, I'm sure this would leave major inconsistencies.

Is it even possible to accomplish a backup of the root directory without physical server access? My goal is to be able to copy the filesystem completely so that I could literally plug it into my new server and boot it up with minimal modifications. Am I dreaming?

I've already backed up the "important" stuff using rsync, but over the years I've spent a **lot** of time configuring various services just the way I like/need, and I'd love to have those configs/apps automagically on my new server, if such a thing is possible.

Anyone have any ideas for this? Does my idea make any sense? Anyone else had to pull a backup off a server without physical access before?

NOTE: I am not necessarily concerned that the server remain online during the backup, downtime doesn't really matter in this scenario. The main goal is that I need to be able to accomplish this entirely over the network without any physical access.

uname -r
2.6.32-33-server

lsb_release -a
LSB Version:	[trimmed]
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid

EDIT:
Forgot to include:
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             455G  392G   40G  91% /

---

### Post by volkswagner on 2011-10-30
You may be able to [safely backup a running system]("http://ubuntuforums.org/showthread.php?t=35087&highlight=remote+access+to+x-server").


Depending on your partition scheme you have an easy time of it.

Can you exclude any large data directories and backup data separately?

---

### Post by Jonathan L on 2011-10-31
Hi AE

>  Am I dreaming?No, just takes a little planning.  It sounded to me like you're intending to copy the programs and all of the OS with your data (if you've changed lots of things, it is your data!).  So you make your system as quiescent as possible, do your backups, copy them as you've planned.  As you appear to have 40 Gbyte, I'll guess you have lots more space on your new system: you can keep an entire backup online to fix things if you find you've missed something later.

The only thing I'd add is that if you really really want your data to be the same, never trust your backup program.  I've been shocked over the years at how badly copying files can go, and have normally insisted on 100% copy of data files.  (Really 100%: you might have tens of millions of data files, and you want every single one.)

So I recommend checking your files with a system like this: make a list of all the files, the md5 sum of the contents, and the user, group, mode, size, and mtime.  (I'd normally say atime doesn't matter, and ctime is about backups anyways, so I skip those.)  Then you do the same after the copy, on the target system.  Make a script to remove any files you know will have changed (typically logs), and compare them with diff.  If it's right, the only thing different will be an extra file on the target system, the list of things there !

The point about this is that you have corroboration of the files and their contents which is entirely independent of the method you use to make the copy, and so all assumptions will be different. 

To be concrete, here's a script, perhaps you put it in /usr/local/bin/checkit
```
#!/bin/sh

f=$1

TZ=Etc/UTC

# file must be readable (but broken symlink is okay)
if [ ! -r $f -a ! -L $f ]; then
    echo "$0: $f: No such file or directory" 1>&2
    exit 1
fi

# get details
m=`stat --printf '%a' $f`
u=`stat --printf '%u' $f`
g=`stat --printf '%g' $f`
t=`stat --printf '%y' $f | awk '{ print $1 "-" $2; }'`
s=`stat --printf '%s' $f`
if [ -f "$f" ]; then
    k='f'
    md5=`md5sum $f | awk '{print $1;}'`
elif [ -d "$f" ]; then
    k='d'
    md5=xxdirectoryxxxxxxxxxxxxxxxxxxxxx
    s=-1
elif [ -L "$f" ]; then
    k='l'
    md5=xxlinkxxxxxxxxxxxxxxxxxxxxxxxxxx
    s=-1
else
    k='X'
    md5=xxdevicexxxxxxxxxxxxxxxxxxxxxxxx
    s=-1
fi

printf '%s %4o %6u %6u %s %12d %s %s\n' $k 0$m $u $g "$t" $s $md5 "$f"
```Then you run it (presumably as root)
```
cd /
find . -depth -exec /usr/local/bin/checkit  '{}' ';' > /tmp/FILELIST1
sort --key=8 /tmp/FILELIST1 > /tmp/FILELIST1.S
```Then you copy, repeat file list on far side, and start checking.

(NB, that script is weak against tricky filenames, and is a bit slow with something like 8 processes per file.  If you have to do this very often, have large filesystems, or have tricky filenames, let me know privately and I'll dig out the source of better ones for you.)

You're not dreaming to think of exactly accurate backups, but it might be more work than you were anticipating.  Hope that's of some use and gives you some ideas.  

Kind regards,
Jonathan.

PS.  It occurs to me that the problem could be made easier too if you had more than once chance to get it right.  I'm a huge fan of rent-by-the-hour servers (I use the ones as AWS): in this case you could prep your data, copy across, check it, and repeat the whole process until the checks were good.  You just throw away the ones which didn't work.

---

### Post by knight187 on 2011-10-31
Its not cheap but this product works quite well. 

[http://www.acronis.com.au/backup-recovery/server-linux/?source_detail=ASIA-AU-SEM-branded-abrsl11&c=9539246338&k=acronis%20linux&gclid=CMjsxZPPkqwCFQwY4god4xWVlw](http://www.acronis.com.au/backup-recovery/server-linux/?source_detail=ASIA-AU-SEM-branded-abrsl11&c=9539246338&k=acronis%20linux&gclid=CMjsxZPPkqwCFQwY4god4xWVlw)

or if bandwidth is disposable just mount an NFS share on your server and run this command

cd /
find -xdev | cpio -p /mnt/nfsshare

once the server has been cloned to a dir on the backup server you can tar it up using resources and processing power from the backup server. To restore it untar it to a new drive and run grub to create the necessary records on the MBR.

This is clearly a very brief description of a complex process, if your interested I will be happy to elaborate further.

Cheers.

---

### Post by Apple_Eater on 2011-10-31
> **volkswagner said:**
> 
Can you exclude any large data directories and backup data separately?

Yes. The general "storage" volume on the server is 369G of purely static files (backups of personal stuff: games, music, movies, etc) and can easily be transferred separately. 

My email server/archive is 3.8G and can easily be transferred separately.

Since the drive usage is 392G, this leaves only 19.2G that I have to worry about doing "online".

The link you provided is pretty much exactly what I'm doing presently except I am using rsync to do it remotely rather than gzip to do it locally. The main issue I am concerned with is consistency: it'll take at least a few minutes (probably closer to hours) to make that 19.2G backup. During this time, webservers are running, DNS is running, logfiles are being generated, configurations may be changing, etc. So it's entirely feasible that Program A could modify /data/A.dat at some time, and then modify /data/B.dat at some other time and only one of these changes make it into the archive. If Program A isn't expecting this, it might crash, lose all data, etc. This is why I am trying to figure out if I can keep the system running after dismounting the filesystem.

Here is a breakdown of my current process:

The following is run from the TARGET server:

```

rsync -zaHv --log-file=/root/email_sync.log hostname:/opt/zimbra/ /mnt/email        

(This copies the full directory of my email server (Zimbra) to the target server, preserving links, etc)

rsync -zaHv --log-file=/root/storage_sync.log hostname:/storage /mnt/storage

(This copies the contents of my largely static, ~370G storage volume)

rsync -zaHv --log-file=/root/root_sync.log --exclude=/proc/* --exclude=/tmp/* --exclude=/lost+found/* --exclude=/opt/zimbra/* --exclude=/storage/* hostname:/ /mnt/root

(This copies "everything else" with specific exclusions based on what I've read about not copying certain parts of the filesystem)

```

As stated above, I'm worried about critical files that may change during the transfer and lead to issues. Since rsync is pretty good at update detection, I could do an initial sync of the root to copy the bulk, then re-run the command over to transfer any updates that happened during the first sync. Is something like that "likely" to work?

Also, how do I go about bringing the copied filesystem online on the target server? I had planned to basically make sure everything is mounted correctly and chroot into /mnt/root (or whereever I mount it) and just hope it works. Is there a more graceful way to accomplish this?

---

### Post by Apple_Eater on 2011-10-31
> **Jonathan L said:**
> 
So I recommend checking your files with a system like this: make a list of all the files, the md5 sum of the contents, and the user, group, mode, size, and mtime.  (I'd normally say atime doesn't matter, and ctime is about backups anyways, so I skip those.)  Then you do the same after the copy, on the target system.  Make a script to remove any files you know will have changed (typically logs), and compare them with diff.  If it's right, the only thing different will be an extra file on the target system, the list of things there !

The point about this is that you have corroboration of the files and their contents which is entirely independent of the method you use to make the copy, and so all assumptions will be different.

So essentially I should use an additional check for consistency across the filesystem after whatever process I use for copying to ensure that no inconsistencies develop? 
> **Jonathan L said:**
> 
Then you run it (presumably as root)
```
cd /
find . -depth -exec /usr/local/bin/checkit  '{}' ';' > /tmp/FILELIST1
sort --key=8 /tmp/FILELIST1 > /tmp/FILELIST1.S
```Then you copy, repeat file list on far side, and start checking.


That script looks very useful for my situation. I assume I can just alter the arguments to the "find" command to match my situation? i.e. I'm not concerned about consistency for my /storage directory which makes up the massive bulk of the data (370 out of 398G). So I could just manipulate the find command to only pipe the "useful" filenames into the script? I assume (not terribly familiar with find) that I could exclude certain directories from the list (like /proc/ and other things you wouldn't want to generate checksums for!)

Thanks for your help and I will definitely be using that script to check consistency after I finish.

---

### Post by Jonathan L on 2011-10-31
Hi again AE

```
So essentially I should use an additional check for consistency across the filesystem after whatever process I use for copying to ensure that no inconsistencies develop? 
```Absolutely.  So I use a very naive check, which will trap the (very common) bugs in usage, and the (very infrequent) bugs in software.

> That script looks very useful for my situation. I assume I can just alter the arguments to the "find" command to match my situation? i.e. I'm not concerned about consistency for my /storage directory which makes up the massive bulk of the data (370 out of 398G). So I could just manipulate the find command to only pipe the "useful" filenames into the script? I assume (not terribly familiar with find) that I could exclude certain directories from the list (like /proc/ and other things you wouldn't want to generate checksums for!)Don't mod the script; just run it once per filesystem.  Note I added -xdev, which means don't cross a mount point (which is the best  way to exclude /tmp, /proc and so on)

```
cd /storage
find . -xdev -depth -exec /usr/local/bin/checkit  '{}' ';' > /tmp/FILELIST_STORAGE_A

```Which means:
Find, from here (.), and without descending through a mount (-xdev), directories after their contents (-depth) all the files ... when you find one, run /usr/local/bin/checkit FILENAME
Put all the output in /tmp/FILELIST_STORAGE_A

But I don't recommend changing the find for things you don't want, I recommend ignoring them in the diff at the end.  It's much better to say "ah, that's okay" when you see /var/log/syslog is different.

If you have lots of things you want to ignore, consider 
```
myignoreprogram FILELIST_STORAGE_A.SORT > FILELIST_STORAGE_A.SORT.IG
myignoreprogram FILELIST_STORAGE_B.SORT > FILELIST_STORAGE_B.SORT.IG
diff FILELIST_STORAGE_A.SORT.IG FILELIST_STORAGE_B.SORT.IG

```

Hope that's made me a little clearer about what I was suggesting.

Kind regards,
Jonathan.

---

### Post by Apple_Eater on 2011-11-01
Well after running thru the scripts, I checked the diff which immediately printed out the entire lists... #$!@.

I then opened them and compared the first line, they were exactly the same except a 2hr offset because the servers are set to different timezones... whoops.

Instead of running the process again (3-4 hours) I just awk '{$5=" "}1' FILELIST1.S > test1.s for both files to remove the dates and it worked perfectly. No difference in the filesystems. I justified this since all the files included MD5 hashes so that would not be an issue. I can't think of any reason not comparing the times would cause a problem, so I neglected to do so.

Otherwise, worked perfectly on my storage volume. I did not run it on the root yet because root had not been copied completely, but when I finish copying root today, I will run the script there as well and see if the results are good.

Also note that I had to slightly modify the script to deal with the many oddly-named files on my system; I changed a few of the $f to "$f" and then the script was able to parse every file on the system without issue.

Thanks a million for your help!

EDIT: One "strange" thing though, when I do du -h -s on my storage volume on SOURCE:
du -h -s
339G	.

Yet on destination:
du -h -s
356G	.


I'm sure there is something funny about the way my filesystems are setup that would explain this, but I am at a loss. The scripts showed no differences at all in the files, yet we've got some magic storage eating stuff on my destination volume? While I fully trust the script (as I understand it so I can verify it *should* work) I am still a bit nervous about this. Any thoughts?

EDIT #2:
Never mind, I tried this as well:
SOURCE:
du -h -s -x --apparent-size
356G	.

DESTINATION:
du -h -s -x --apparent-size
356G	.

So I guess there must be some sort of sparse files(?) somewhere in the volume to account for the space difference. Weird.

---

### Post by Jonathan L on 2011-11-03
Hi Apple Eater

Glad you found the scripts helpful.

**_Sizes_**

> ... some magic storage eating stuff on my destination volume? While I  fully trust the script (as I understand it so I can verify it *should*  work) I am still a bit nervous about this. Any thoughts?

So I guess there must be some sort of sparse files(?) somewhere in the volume to account for the space difference. Weird
Different sizes: typically caused by directories being different sizes and different block allocation strategies on different versions of operating systems.  On a working filesystem directories tend to grow but not shrink.  If you add up the size of just the files without directories etc, they should be exactly the same:
```
find . -type f -ls | awk '{x+=$7; print $7, x, $11; }'
```**_Timestamps_**

> I can't think of any reason not comparing the times would cause a problem, so I neglected to do so.personally, I'm fanatical about the timestamps being exactly right, for any number of reasons (photos having right time of day, just for one).  If you ran the script with the TZ=Etc/UTC then you have "pure" timestamps in your FILELIST files and can process them into time-setting scripts:

```
awk '($1=="f")||($1=="d") { printf("touch \"-d%s %s +0\" \"%s\"\n", substr($5,1,10), substr($5,12), substr($0, 98)); };' FILELIST

```This makes lots of 
```
touch "-d2011-11-03 20:32:32.599032622 +0" "./path/some/file"
```which you run to get the timestamp right

**_Filenames_**

> Also note that I had to slightly modify the script to deal with the many  oddly-named files on my system; I changed a few of the $f to "$f" and  then the script was able to parse every file on the system without  issue.As I said, it was weak against unusual filenames: it can be very fiddly indeed to deal with them 100% correctly.

Glad to hear it was a success

Kind regards,
Jonathan.

---

