---
title: "[SOLVED] Hard drive problems (URGENT!!)"
date: 2008-07-15
forum: Windows
---

### Post by dbbolton on 2008-07-15
I have an old Dell Dimension with some valuable data on the hard drive. After an unclean shutdown, I get this error at boot:

          A disk read error occurred. Press ctrl+alt+del to restart.

It comes up every time, and I can't get in to Windows. I booted the XP disc and entered the recovery console to run this command
```
chkdsk /R
```
About a quarter of the way through, chkdsk told me that there were some unrecoverable errors.

Is there anyway that I can get the data off the hard drive?

I tried connecting the Windows hard drive to my Ubuntu hard drive as a slave, then mounting it from inside Ubuntu, but it didn't work as there were errors on the drive. mount told me to run 'chkdsk /f' but that is an invalid option, according to the XP cd.

Any suggestion would be appreciated.

---

### Post by scragar on 2008-07-15
[http://en.wikipedia.org/wiki/Dd_(Unix)#Recovery-oriented_variants_of_dd](http://en.wikipedia.org/wiki/Dd_(Unix)#Recovery-oriented_variants_of_dd)

I'm sure one of those will be helpful, provided you've got an extra HD to store the info on as it's recovered. I don't think windows will like being moved about though, so you may need to reinstall.


Another thing you could try, would be placing the drive somewhere cold(freezer is a good choice) for a while, and trying it then, although this is unlikly to have much of an effect it could be enough to help.

---

### Post by dbbolton on 2008-07-15
> **scragar said:**
> [http://en.wikipedia.org/wiki/Dd_(Unix)#Recovery-oriented_variants_of_dd](http://en.wikipedia.org/wiki/Dd_(Unix)#Recovery-oriented_variants_of_dd)

I'm sure one of those will be helpful, provided you've got an extra HD to store the info on as it's recovered. I don't think windows will like being moved about though, so you may need to reinstall.


Another thing you could try, would be placing the drive somewhere cold(freezer is a good choice) for a while, and trying it then, although this is unlikly to have much of an effect it could be enough to help.
Do you think that one of those programs would be helpful if I don't need to fix the system (ie, just want to get documents, pictures, etc) ?

---

### Post by scragar on 2008-07-15
The variant of the **dd** command that dd_rhelp uses would be very helpfull, since it will skip the bad section of the HD instead of failing to read it and throwing errors, it will then come back and try again to read the corrupt part until it has either read it or given up.
That looks to be your best chance of restoring any information on your HD.

---

### Post by wolfen69 on 2008-07-15
try a puppy linux cd. you can get into any drive with it.

---

### Post by dbbolton on 2008-07-15
> **scragar said:**
> The variant of the **dd** command that dd_rhelp uses would be very helpfull, since it will skip the bad section of the HD instead of failing to read it and throwing errors, it will then come back and try again to read the corrupt part until it has either read it or given up.
That looks to be your best chance of restoring any information on your HD.

I'll give this a try first

> **wolfen69 said:**
> try a puppy linux cd. you can get into any drive with it.

If I manage to boot a puppy linux cd, how will I get the files off the hard drive onto some other media?

Basically, I just want to get the 'My Documents' folder.

---

### Post by Rhubarb on 2008-07-15
If you are having similar problems to this post:
[http://ubuntuforums.org/showthread.php?t=858415](http://ubuntuforums.org/showthread.php?t=858415)
Please refer to my comment number 7:
[http://ubuntuforums.org/showpost.php?p=5381899&postcount=7](http://ubuntuforums.org/showpost.php?p=5381899&postcount=7)
Which fixed up the problem and allowed that person to mount and read from a problematic NTFS partition.

---

### Post by dbbolton on 2008-07-15
> **Rhubarb said:**
> If you are having similar problems to this post:
[http://ubuntuforums.org/showthread.php?t=858415](http://ubuntuforums.org/showthread.php?t=858415)
Please refer to my comment number 7:
[http://ubuntuforums.org/showpost.php?p=5381899&postcount=7](http://ubuntuforums.org/showpost.php?p=5381899&postcount=7)
Which fixed up the problem and allowed that person to mount and read from a problematic NTFS partition.
This did sound similar to my problem, but when I tried your suggestion, I got the same error as the first time I tried to mount the drive:

```

# sudo mount -t ntfs-3g /dev/sdb1 /bak -o force
Error reading $MFT: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

---

### Post by Rhubarb on 2008-07-15
In that case photorec (which can be found in the testdisk package in the ubuntu repos) is a very good command line based application that can restore photos, documents, and many other file types regardless of filesystem.
Type in man photorec for details of usage in Ubuntu.

---

### Post by dbbolton on 2008-07-16
> **Rhubarb said:**
> In that case photorec (which can be found in the testdisk package in the ubuntu repos) is a very good command line based application that can restore photos, documents, and many other file types regardless of filesystem.
Type in man photorec for details of usage in Ubuntu.
Thanks for this suggestion, but the man page isn't very helpful:

```
PHOTOREC(1)                  Administration Tools                  PHOTOREC(1)

NAME
       photorec - Recover lost files from harddisk, digital camera and cdrom

SYNOPSIS
       testdisk [/log] [/debug] [/d recup_dir]

       testdisk /list [/log]

DESCRIPTION
          PhotoRec  is  file  data  recovery software designed to recover lost
       files including video, documents and archives from Hard Disks and CDRom
       and lost pictures (Photo Recovery) from digital camera memory. PhotoRec
       ignores the filesystem and goes after the  underlying  data,  so  it'll
       work  even if your media's filesystem is severely damaged or formatted.
       PhotoRec is safe to use, it will never attempt to write to the drive or
       memory support you are about to recover lost data from.

OPTIONS
       /log   create a photorec.log file

       /debug add debug information

```

The broken NTFS is on /dev/sdb1 , so how would I go about restoring files from it to, say, /home ?

---

### Post by Rhubarb on 2008-07-16
Ok, it's not too hard thankfully, there are a few helpful hints about photorec scattered around the net.

Firstly, to get photorec working, you need to re-size your terminal window, as photorec requires at least 25 lines in a terminal window to work.

Then just:
```
sudo photorec /dev/sdb1
```
And follow the prompts.

More data recovery documentation can be found here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

And this website may be of assistance too:
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

### Post by wolfen69 on 2008-07-16
those links are helpful, and appreciated, but the bottom line is, if you can't access your stuff with a live cd, your pretty much done. unless you have alot of money to give to a specialty (recovery) business, give it up.

---

### Post by dbbolton on 2008-07-16
I found a program called VirtualLab Data Recovery, and it is able to read files from the broken hard drive. Bad new is, I had to wipe my Ubuntu hard drive to install XP, and the program costs $40.

---

### Post by dbbolton on 2008-07-17
I ended up using photorec, once I realized that it was doing almost the same thing as VirtualLab Data Recovery, and that $40 only covered a 10MB quota (30GM is like $150). 

So, I got about 5 GB of various files off the drive. the only problem is that now I have to go through 70 folders to sort and rename the files. It's a small price to pay next to professional data recovery though. Thanks to everyone for the suggestions.

---

