---
title: "How should I use the rsync to bopy data between disk with little room"
date: 2016-05-18
forum: Server Platforms
---

### Post by sed_faster on 2016-05-18
hello everyone,

I used the rsync to copy data between disk 500GB.I used this parameter (sudo rsync -Cravzp --delete-after $source $destiny) with the proposer to make a effect mirror! The disk one has 450GB and the disk two has 480GB. The volume of the data which would copy was more a less 150GB. When the process was run it is stopped because the disk two was out of space. I understand why this occur, but I can't find how I can resolve this situation. I need your ideas guys 

Thanks

---

### Post by sed_faster on 2016-05-19
Hello,

Anyone can help or direct me? Thanks

---

### Post by sudodus on 2016-05-19
Please tell us what you think makes the target partition get full, even though it is bigger than the source partition :-)

-o-

I use rsync, but I am no expert. Let us hope more people will reply with tips.

I often use the following command line

```
sudo rsync -Havn $source/ $target
```

**-v** alias 'verbose', **-n** alias 'dry run'[/B], and if it looks good

```
sudo rsync -Hav $source/ $target
```

From ```
man rsync
```

```
       -a, --archive
              This  is equivalent to -rlptgoD. It is a quick way of saying you want recursion and want
              to preserve almost everything (with -H being a notable omission).  The only exception to
              the  above  equivalence  is  when  --files-from  is  specified,  in which case -r is not
              implied.

              Note that -a does not preserve  hardlinks,  because  finding  multiply-linked  files  is
              expensive.  You must separately specify -H.
...
       -H, --hard-links
              This  tells rsync to look for hard-linked files in the source and link together the cor&#8208;
              responding files on the destination.  Without this  option,  hard-linked  files  in  the
              source are treated as though they were separate files.

              This  option  does NOT necessarily ensure that the pattern of hard links on the destina&#8208;
              tion exactly matches that on the source.  Cases in which the destination may end up with
              extra hard links include the following:

              o      If  the  destination  contains  extraneous  hard-links (more linking than what is
                     present in the source file list), the  copying  algorithm  will  not  break  them
                     explicitly.   However,  if one or more of the paths have content differences, the
                     normal file-update process will break those extra links (unless you are using the
                     --inplace option).

              o      If  you  specify a --link-dest directory that contains hard links, the linking of
                     the destination files against the --link-dest files can cause some paths  in  the
                     destination to become linked together due to the --link-dest associations.

              Note  that  rsync  can only detect hard links between files that are inside the transfer
              set.  If rsync updates a file that has extra hard-link connections to files outside  the
              transfer,  that  linkage will be broken.  If you are tempted to use the --inplace option
              to avoid this breakage, be very careful that you know how your files are  being  updated
              so  that  you  are certain that no unintended changes happen due to lingering hard links
              (and see the --inplace option for more caveats).

              If incremental recursion is active (see  --recursive),  rsync  may  transfer  a  missing
              hard-linked file before it finds that another link for that contents exists elsewhere in
              the hierarchy.  This does not affect the accuracy of the transfer (i.e. which files  are
              hard-linked  together), just its efficiency (i.e. copying the data for a new, early copy
              of a hard-linked file that could have been found later in the transfer in another member
              of  the  hard-linked  set  of  files).  One way to avoid this inefficiency is to disable
              incremental recursion using the --no-inc-recursive option.
```

---

### Post by sed_faster on 2016-05-19
Hello,

Thanks. What I think which do the disk was full is the total of the archived. for example:

On both disk I have this files (the disk is the 500Gb each):
/
file 1 with 200GB
file 2 with 200GB

This files is on the base of the disk. But I arranged the files on the disk one and the structure was so:
/
file 1 with 200GB
folder 1
-----file 2 with 200GB

On the disk two the structure remains.
When I ran this command "sudo rsync -Cravzp --delete-after $source $destiny" the rsync will be create , on the disk two, the same structure which find on the disk one but while don't delete the older files the disk will be full. Conclusion, before the process the backup finish the disk two was full and the programmer rsync hasn't space two management files.

I explain me well?

---

### Post by sudodus on 2016-05-19
You are right, there is not space enough for doublets. Please consider this syntax description (of the trailing slash in the path of the source).

```
       A  trailing slash on the source changes this behavior to avoid creating an additional directory
       level at the destination.  You can think of a trailing / on a source as meaning "copy the  con&#8208;
       tents  of  this  directory"  as  opposed to "copy the directory by name", but in both cases the
       attributes of the containing directory are transferred to the containing directory on the  des&#8208;
       tination.   In  other  words,  each of the following commands copies the files in the same way,
       including their setting of the attributes of /dest/foo:

              rsync -av /src/foo /dest
              rsync -av /src/foo/ /dest/foo
```

---

### Post by darkod on 2016-05-19
So if you know what is the issue why don't you delete file2 on disk2 and start rsync immediately? That will leave you without a sync only for a few hours...

I agree with sudodus that rsync -Hav is mostly enough, you don't need to put as many parameters as you did. Do you really need them all or you simply started adding them up?

Even the -v is not needed unless you are sitting in front of the monitor and looking at it. If this is a scripted operation or on a headless server, I don't see a point for -v.

You can also consider using the --delete-before option instead of --delete-after which should sort your problem with file2 location because it should delete it before starting the transfer of folder1/file2. That should leave enough free space for the rsync to finish.

---

### Post by sed_faster on 2016-05-20
> **darkod said:**
> So if you know what is the issue why don't you delete file2 on disk2 and start rsync immediately? That will leave you without a sync only for a few hours...

I agree with sudodus that rsync -Hav is mostly enough, you don't need to put as many parameters as you did. Do you really need them all or you simply started adding them up?

Even the -v is not needed unless you are sitting in front of the monitor and looking at it. If this is a scripted operation or on a headless server, I don't see a point for -v.

You can also consider using the --delete-before option instead of --delete-after which should sort your problem with file2 location because it should delete it before starting the transfer of folder1/file2. That should leave enough free space for the rsync to finish.

I tried with parameter "--delete-before", and it is possibly copy the data (because it deleted the data first and copy after). But didn't copy all data :/ The disk two it has less free space than disk one, but the data is not there! I ran the command diff and the result was a report with various files missing. And when I accessed, on disk two, on various directors many files missing. But when I ran again rsync he talk doesn't missing anything :S The most interesting is that he created the folders but not copied the contents!

Before I delete all data on the disk two and ran again command rsync I'd like to know why this is happen!
Thanks

---

### Post by darkod on 2016-05-20
Have you tried using only rsync -av options? You never replied whether you really need all those extra options in the command.

If it is not copying any data, then you are not using something correctly. Also it helps to know if you are trying to copy data or maybe the complete OS disk? I know people try to use rsync as backup copying the full OS disk but I'm not sure if it copies 100% of files...

I have used it to sync data files and it always worked for me.

---

### Post by sed_faster on 2016-05-21
Hello,

I tested this command:

```
sudo rsync -Cravzp --delete-before $source $destiny
```

and missing files. Test again but this set:

```
sudo rsync -ravzp --delete-before $source $destiny
```

and all files was copy. After ran this command I ran diff and didn't had any difference between drives. But when I did "df -kh" the report show diferent values between drives:

```

Filesystem         Size  Used Avail Use% Mounted on
/dev/sdb1          459G  360G   76G  83% /media/5001
/dev/sdc1          459G  397G   39G  92% /media/5002

```

Why I have this difference?

The reason to I chose all parameter in rsync was because I see this set on article in the internet and I read the manual and this set do this:

-C:--cvs-exclude           auto-ignore files in the same way CVS does -> Ok, I don't know why I left this parameter but I don't need this. But this is set that eas giving problems; 
-r:--recursive             recurse into directories -> I need this parameter to copy all files in directories, right?
-a:--archive               archive mode; equals -rlptgoD (no -H,-A,-X) -> I don't understand why I need this parameter but I think better used;
-v: I used this parameter because I like see failing the lines on terminal, and this is usefull to see if the command finish or not!
-z: --compress              compress file data during the transfer-> This parameter will do the transfer be faster;
-p: --perms                 preserve permissions;

Sorry my late for respond your answer but I need time to write on English. I hope which you can read my English :) Thanks

---

### Post by darkod on 2016-05-22
As you can see in the explanations, the -a option equals all the -rlptgoD options. Which means using -a you don't need to use -rp too, they are already contained in the -a. So your command becomes rsync -avz.

I also don't think the -z helps you much during rsync from local folder to local folder because they are on the same machine. I think the compression is designed to be used when transferring data over slower internet connections, that's why it could help compressing it first and then decompressing on the destination. On a local machine that might actually be slower because it does need time to do the compress/decompress. You can try without the -z and compare speeds.

As for the difference between the used space on /media/5001 and /media/5002, you don't say which is the source and which the destination. Was the destination empty before you ran the rsync? If it wasn't, don't forget that by default rsync doesn't delete files on the destination, it only copies files from the source to the destination. If a file was copied and was later deleted from the source, rsync will not delete it on the destination the next time you run it. Not unless you specifically tell it to. That can explain why the destination can have more used space. You said the diff command showed there is no difference, so rsync copied the files correctly.

---

### Post by sed_faster on 2016-05-22
> **darkod said:**
> As you can see in the explanations, the -a option equals all the -rlptgoD options. Which means using -a you don't need to use -rp too, they are already contained in the -a. So your command becomes rsync -avz.

I also don't think the -z helps you much during rsync from local folder to local folder because they are on the same machine. I think the compression is designed to be used when transferring data over slower internet connections, that's why it could help compressing it first and then decompressing on the destination. On a local machine that might actually be slower because it does need time to do the compress/decompress. You can try without the -z and compare speeds.

I agree all did you say :)

> As for the difference between the used space on /media/5001 and /media/5002, you don't say which is the source and which the destination. Was the destination empty before you ran the rsync? If it wasn't, don't forget that by default rsync doesn't delete files on the destination, it only copies files from the source to the destination. If a file was copied and was later deleted from the source, rsync will not delete it on the destination the next time you run it. Not unless you specifically tell it to. That can explain why the destination can have more used space. You said the diff command showed there is no difference, so rsync copied the files correctly.

I did two different test:
Between 5001 and 5002, deleted all data in 5002 and used this command:

```
sudo rsync -ravzp --delete-before $5001 $5002
```

The result with command diff didn't any difference.
Between usb1 and usb2 didn't delete which has in usb2, it was incomplete - Because in the past I used the parameter -Cravzp - this time I only ran this command:

```
sudo rsync -ravzp --delete-before $usb1 $usb2
```

Copy all data, the result which command diff hasn't any value difference, but the difference on space occupy and free between disk also occur. May be file hidden?

```

Filesystem         Size  Used Avail Use% Mounted on
/dev/sdb1          459G  360G   76G  83% /media/5001 (source) - System=Linux
/dev/sdc1          459G  397G   39G  92% /media/5002 (destiny) - System=Linux

/dev/sdd1          932G  811G  121G  88% /media/usb1 (source) - System=HPFS/NTFS/exFAT
/dev/sde1          917G  811G   60G  94% /media/usb2 (destiny) - System=Linux

```

**Note:** How should I do to "sweep" an directory at the end their forks (entire disk) to find all directory and files hidden (with extension .something)? Because I used command "ls -la" the result only reaches the level where I executed the command.

Exist difference in filesystem, but only verify between usb1 and usb2. Where usb1 has 932GB and usb has 917GB. But I can't find answers to difference in available space (121GB differente 60GB).
If I check the space on disc through environment graphic the value is 425,1GB, but if I did through terminal with command "df -kh" the value it is diferrence (it is 360GB). Why this occur? Probably it has the type/parameter I used on command df?
Lastly, I verificed the folder it was copy and all folder was the same values. Therefore, it is means which all data was copied (This test served to complementy the test with command diff). 

Thanks

---

### Post by darkod on 2016-05-22
Honestly, I don't understand your problem any more... :) You said rsync correctly copies all files, so it is doing its job. By the way you are still using -ravzp after we discussed that -rp are included in the -a so you don't need to type them too.

If you think the usb disks should show more free space, that has nothing to do with rsync. From the used space it seems equal to me (811GB for both). The total size of different usb disks can differ slightly, plus the filesystems are not the same which also makes a difference in available space.

If you want to find folder sizes you can open /media/5002 for example and run:
```
du -sh *
```

That will show you all folder content with size. After that you can go into another folder and check its content too, and try to find any difference like that...

---

### Post by volkswagner on 2016-05-22
As @darkod pointed out, your two filesystems may not be equal.

What file system are used for each disk/partition?

If they are both ext[2-4] you can use the command in [this post]("http://ubuntuforums.org/showthread.php?t=1553289") to find the block size.

Let's say one filesystem uses 4096Bytes block size, this means any file smaller than 4096Bytes will still use an entire 4096Bytes block. Additionally, any file greater than 4046Bytes but
less than 8192Bytes, will use two entire blocks.

You'll also notice when running ls command, folder sizes will usually consume just one block (it's generally a good indication of file system block size).

---

### Post by sed_faster on 2016-05-22
Hello,

Sorry, I forget explain this detail. But when I used the command rsync I chose this set: -ravzp. An I needed explain my result with this set.

@volkswagner
The output to block size this that:
**sudo dumpe2fs -h /dev/sdb1 | grep -i "block size"**
dumpe2fs 1.42.9 (4-Feb-2014)
Block size:               4096
**sudo dumpe2fs -h /dev/sdc1 | grep -i "block size"**
dumpe2fs 1.42.9 (4-Feb-2014)
Block size:               4096

I just found which directory was different. 
**On 5002(destiny)**
du -sh *
25G    Downloads
[B]On 5001(source)
[/B]du -sh *
6.5G    Downloads

This is weird! Because when I explore both directory I found the same content! By the way, when I see the size through button right on environment graphic I see 26GB on both folder with the same number of the items :/
@volkswagner, After read your post I think the problem consist on the block size, right? Which command and how can I see the real size of my files and directories?

Thanks

---

### Post by darkod on 2016-05-22
Then focus taking a better look on /media/5001/Downloads because it seems to report 6.5GB incorrectly. Go into that folder and run the du command again and you can try comparing it with 5002 (unless there are too many items inside).

Use the diff command too and compare the Downloads folder on both locations.

It's difficult for us to say like this where the "problem" is, but it should be easy to find. Maybe some hidden/deleted files, etc...

At least now you know where to look. I have no more ideas...

---

