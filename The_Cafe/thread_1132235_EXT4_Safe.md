---
title: "EXT4 Safe?"
date: 2009-04-21
forum: The Cafe
---

### Post by Prominence on 2009-04-21
Is the Ubuntu 9.04 EXT4 Filesystem safe yet?

---

### Post by jsowoc on 2009-04-21
Based on this thread, I believe they enabled the option "ordered", which sacrifices speed in order to be "safer".

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all)

I'm running ext4 and haven't had any problems...

---

### Post by Prominence on 2009-04-21
Oh...so that means no improvements or what exactly?

---

### Post by bodhi.zazen on 2009-04-21
Define "safe". I never thought it was unsafe. IMO people made a big deal about potential data loss in the event of a power failure, can happen with any OS and any file system.

Your option may vary.

---

### Post by Prominence on 2009-04-21
As in it won't crash or mess up or anything, basically, does it have a good chance of making something bad happen?

---

### Post by jsowoc on 2009-04-21
The version of ext4 that came out with the 9.04 alpha had an interesting side effect of delayed allocation. If an application were writing a file, didn't do an "fsync" on the file, and renamed it over an old file, you could end up with neither old file nor new file. This was because the metadata (i.e. the renaming of the file) was done out-of-order with writing of the file.

This side-effect of delayed allocation has been fixed and will make it into 9.04 final (I'm not sure if it made it into the RC).

Trusting ext4 with your data is as safe as trusting ext3 with your data. In either case, your hard drive could crash, you could get a power surge, etc., so you should keep reasonable backups of all important data.

---

### Post by lisati on 2009-04-21
I'm using EXT4 on one of my machines and haven't encountered any difficulties so far.

One of the things with designing ANY program (or system component for that matter) is to make sure it does what it's meant to without it turning into a major disaster. Not everyone's system has the exact same specifications, and it's very easy for unpleasant side effects to sneak in.

I've been caught out myself, where I got a set of MS-DOS programs I'd written myself working brilliantly on my 80286-based machine with a "Hercules" graphics card. I even included a test for which video mode the user's computer was set to (the intended user had an EGA card). Trouble is, I overlooked the possibility that the CPU might be different: the intended user didn't have a '286 but a "lesser" (different) cpu. End result: scrambled data. (Solution: do my best with the backup I'd made for program testing purposes, even though it was a month or two out of date, and rework the offending sections of code to work on an 8086/8088)

That is why it's always a good idea to make backups.

---

### Post by Therion on 2009-04-21
> **Prominence said:**
> As in it won't crash or mess up or anything, basically, does it have a good chance of making something bad happen?
If it's important, back it up.  No one can promise your data is going to be any safer on an ext4 partition than it is/was on an ext3 partition.

Backups, backups, backups.

---

### Post by Prominence on 2009-04-21
That's all true, but should I use ext4? Like reinstall Ubuntu and install ext4 and go on from there?

---

### Post by lisati on 2009-04-21
> **Prominence said:**
> That's all true, but should I use ext4? Like reinstall Ubuntu and install ext4 and go on from there?

The choice is yours. 

On the machine I have with EXT4 I used the installer's manual partition option to select EXT4 as the format while doing a fresh install.

---

### Post by lisati on 2009-04-21
> **Prominence said:**
> That's all true, but should I use ext4? Like reinstall Ubuntu and install ext4 and go on from there?

The choice is yours. 

On the machine I have with EXT4 I used the installer's manual partition option to select EXT4 as the format while doing a fresh install.

EDIT: Feel free to let us know how you get on.

---

### Post by Prominence on 2009-04-21
I'm aware, but is it worth it?

---

### Post by pickboy87 on 2009-04-21
> **Prominence said:**
> I'm aware, but is it worth it?

The general consensus that I've seen says its a nice improvement. If my computer was working properly right now, I'd be sure to let you know.

---

### Post by ubu-for on 2009-04-21
> **Prominence said:**
> Is the Ubuntu 9.04 EXT4 Filesystem safe yet?
No!

I've moved two folders and Jaunty crashed, so the files in the origin folder are deleted and not written to the new place.

[http://ubuntuforums.org/showthread.php?t=1132299](http://ubuntuforums.org/showthread.php?t=1132299)

---

### Post by octopuskevin on 2009-04-21
I'm also looking for an answer on this. I'm planning on doing a fresh install once Jaunty is released, and setting up my root / directory with ext4 and my /home directory as a separate partition with ext3. Does anyone know if this setup would mitigate some of the write errors associated with ext4? 

I know that this type of setup may not see as dramatic of a speed increase over using strictly ext4 for / and /home, but it should theoretically increase boot times, and reduce the risk of lost data from the ext4 issue, right?

Thanks!

---

### Post by Yellow Pasque on 2009-04-21
Is it worth it from a performance standpoint for most users? Probably not.
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=9](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=9)

---

### Post by night_fox on 2009-04-21
You dont have to reinstall ubuntu. Ext3 can be upgraded to Ext4 very easily.

---

### Post by bodhi.zazen on 2009-04-21
To be honest, unless you are doing disk intensive tasks, which most desktop users are not, I have not found a significant difference in file systems and speed / performance.

Sure if you make 10,000 1k files, move them, and delete them you can see differences, but seriously you really need to take "benchmarks testing" with a huge grain of salt.

There are valid reasons to select a file system, but speed I am afraid is not one of them for most users under most "normal" circumstances.

---

### Post by Slim Odds on 2009-04-21
> **bodhi.zazen said:**
> To be honest, unless you are doing disk intensive tasks, which most desktop users are not, I have not found a significant difference in file systems and speed / performance.

Sure if you make 10,000 1k files, move them, and delete them you can see differences, but seriously you really need to take "benchmarks testing" with a huge grain of salt.

There are valid reasons to select a file system, but speed I am afraid is not one of them for most users under most "normal" circumstances.

I have to agree. I looked closely at the changes made for ext4 and most of then have little or no effect on overall performance for the typical desktop machine.

There are some very nice changes and a lot of little improvements. But if folks think that this new file system is going to make their GUI much 'snappier', I think they are going to be very disappointed.

---

### Post by FredB on 2009-04-22
No data lost since I used ext4 on my main partition. But doing backup is something **mandatory**.

---

### Post by northwestuntu on 2009-04-22
i really want to try out ext4, but i really like having my personal files stay on my computer :)

guess i'll wait til next release.

---

### Post by jdeslip on 2009-04-23
If you had a ext4 filesystem before Ubuntu changed the kernel to avoid delayed_allocations do you have to reformat the drive?  

How does this go for future releases?  Will you have to reformat your ext4 filesystems as the format changes in future kernels?  Or are all the changes in the kernel and don't require a reformat?

---

### Post by Eversmann on 2009-04-23
i had ubuntu 8.10 with ext3 installed on my netbook advent 4211, and then i installed ubuntu 9.04 with ext4 from installation.

Right now, i don't notice any difference on speed. And i have it running since alpha 6.

Looks like moving big files or moving lots of small files the improve can be noticed, but the usual, you don't get a thing.

For instance, i have ubuntu 9.04 with ext3 on a good computer (seagate 500gb sata, asus p5k, intel e8500) and the hard disk loads great with ext3. 

Btw, doing fsck takes less time.... ;-)

---

### Post by Doctoxic on 2009-05-24
I am running 9.04 with 2.6.28-11

Are all the EXT4 data loss issues fixed in this?

thanks

---

### Post by Liolikas on 2009-05-24
> **northwestuntu said:**
> i really want to try out ext4, but i really like having my personal files stay on my computer :)

guess i'll wait til next release.
You can then keep you files (/home) in ext3 and make / ext4.

---

### Post by Rich_B_uk on 2009-08-07
Is EXT4 being considered a default option for Karmic do we know? I suppose that's the best gauge! :D

---

### Post by sasho_zl on 2009-08-07
EXT4 is not safe at all! I was using it since the Jaunty release and everything worked almost fine until yesterday. When I was trying to delete one big file (around 7 GB) a known issue with ext4 appeared - the system crashed. Not only the GUI but the entire system! I had to hard reboot and after that all my documents and pictures and many other stuff was just gone!!! I couldn't restore it even with different data recovery utilities! 
My advice to everybody reading this is to switch back to ext3. The ext4 filesystem needs more time to clean itself from bugs.

---

### Post by Midahed on 2009-08-07
> **northwestuntu said:**
> i really want to try out ext4, but i really like having my personal files stay on my computer :)...
Absolutely right!

I don't understand the desire of people to always be using the latest release - especially of something as important as the file system.  Fine to use it on a test PC, but I'd never entrust my data to a new file system until it's been in common use for a lot longer than ext4 has.

Maybe I'm just on old guy who has become risk-averse, but I'll leave it to other 'braver' souls to find the bugs in ext4 before I go anywhere near it.

Mike

---

### Post by epictete on 2009-08-08
> **Midahed said:**
> I don't understand the desire of people to always be using the latest release - especially of something as important as the file system.

I'd never entrust my data to a new file system until it's been in common use for a lot longer than ext4 has.


So wise Mike! To my mind, we may use ext4 for the root partition but not the home partition which will be safer under ext3 file system! This means that one actually have a **separate home partition** which (to my point of view too) is a good security pattern.

---

