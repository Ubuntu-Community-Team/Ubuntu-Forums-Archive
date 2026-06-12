---
title: "How to: Recover data with testdisk!"
date: 2007-03-18
forum: Tutorials
---

### Post by Higgo on 2007-03-18
Go easy on me. This is my first how to. I have been up for 36 hours trying various methods to recover my lost data! Given that i'm not the most confident Linux user and I managed to succeed. I though it was necessary to share my experience.

I was making the transition from windows xp to Ubuntu Edgy. Somewhere along the line I hurt my NTFS data partition. I have all my music, videos, thunderbird profile, everything on this one drive! I was unable to mount it or use ntfsfix or even chkdsk from the recovery console off the windows xp install CD. I was not paying the best of attention when I broke it but I believe I accidentally installed grub to /dev/hda instead of /dev/sda! Maybe?

After trying ddrescue and failing. I came across [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").
I decided to give it a go: 
sudo apt-get testdisk 
Don't ask me which repo it is on. It wasn't working very well. It kept exiting.

The version on the repositories is not the current version. However there was a rpm on the main website. I thought I would try alien out for the first time.

Steps:

```
sudo apt-get install alien
```

```
wget http://www.cgsecurity.org/testdisk-6.6-1.i386.rpm
```

```
sudo alien testdisk-6.6-1.i386.rpm
```

```
sudo dpkg -i testdisk_6.6-2_i386.deb
```


Ok we have TestDisk and PhotoRec installed.

Change to the folder of where you want to recover your files to. 

```
cd /media/data/recover
```

```
sudo testdisk
```

The following steps may not replicate your needs. There are some examples of how to use TestDisk [here]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples")

Choose create log file

Select which device to use for me it was /dev/hda

Select INTEL/PC Partition

Choose 'Analyze' then 'Proceed' then select 'Search'. TestDisk should now scan your device for partitions (If it hasn't already discovered them). This may take a little while. About 5 minutes on my 80 GB hard drive.

TestDisk should now list a series of partitions. I think it is listing past partitions on my drive. I'm not to sure. There are are a couple of  NTFS  and EXT partitions displayed. I'm guessing from past installations. Select your partition and choose 'List'. From here you can get a folder listing. Pressing 'C' to copy that folder and it's child objects in to your recovery folder. 

Browse to your recovery folder!


Tips:

DMA enabled on your drive? Does your drive support it?

```
sudo hdparm -d /dev/hda

```

Turn it on

```
sudo hdparm -d1 /dev/hda
```


I can finally go to sleep now knowing I have my important data back. This has been a 36 hour ordeal and taught me a lot about Linux.  I believe Christophe Grenie is the author of this great utility. I am in debt to him. Thank you.

I also believe this program can fix corrupt filesystems and be used to recover data from recently formatted drives. There are probably better how to's and easier way to recover your data, but this is all I know for now. Don't ask me what PhotoRec does! The project website has great documentation.

I guess I should also start backing up my data...


Higgo

---

### Post by ceeg on 2007-03-22
I am totally in debt to you for discovering TestDisk and posting this guide. I resized my windows partition without backing anything up and had thought I lost the rails application i've been developing for the last two weeks :(

What a scare.

---

### Post by kpkeerthi on 2007-03-22
Nice one. Thanks.

---

### Post by BarNone49 on 2007-03-24
Very nice.  Works perfect.  I recovered entirely wiped NTFS OS partitions using this, and it worked like a charm.

---

### Post by slick1a on 2008-03-14
The above seems to be what im looking for .

my thread (to save copy and paste the same thing)  [http://ubuntuforums.org/showthread.php?p=4514259#post4514259](http://ubuntuforums.org/showthread.php?p=4514259#post4514259)

I got as far as 
Code:

sudo apt-get install alien    <here no probs ldconfig deferred processing now taking place


Code:

wget [http://www.cgsecurity.org/testdisk-6.6-1.i386.rpm](http://www.cgsecurity.org/testdisk-6.6-1.i386.rpm)  < for this :

 wget [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
--17:01:39--  [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
           => `testdisk-6.6.1.i386.rpm'
Resolving wwwcgsecurity.org... failed: Name or service not known.

Code:

sudo alien testdisk-6.6-1.i386.rpm  <for this  :  

wget [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
--17:01:39--  [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
           => `testdisk-6.6.1.i386.rpm'
Resolving wwwcgsecurity.org... failed: Name or service not known.

Code:

sudo dpkg -i testdisk_6.6-2_i386.deb   <and for this :

 wget [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
--17:01:39--  [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
           => `testdisk-6.6.1.i386.rpm'
Resolving wwwcgsecurity.org... failed: Name or service not known.

By taking a quick glance @ my above thread link you will see the dilema im having. 

1. what am i doing incorrectly ?

2. I have the tools i need but cannot locate them to use

3. Can anyone help ????

---

### Post by DigitalRedneck on 2008-03-14
It seems you forgot the period after the www

Also, the file is not available anymore.  Only v6.9 seems to be available on the site now, and it doesn't want to convert with alien.

---

### Post by aysiu on 2008-03-14
This tutorial's a bit old. You don't need to use an .rpm to install *testdisk*.

There's a native (.deb) Ubuntu package for it:
[http://packages.ubuntu.com/gutsy/testdisk](http://packages.ubuntu.com/gutsy/testdisk)

---

### Post by slick1a on 2008-03-15
The following is intended for research purposes only , I take no resposibility if you do not  read this post in full before trying anything.

If TestDisk is not yet installed, it can be downloaded from TestDisk Download. Extract the files from the archive including the sub-directories.

 One condition:

    * TestDisk must be executed with "Administrator privileges." 

Important points for using TestDisk:

    * To navigate in TestDisk, use the Arrow and PageUp/PageDown keys.
    * To proceed, confirm your choice(s) with the Enter key.
    * To return to a previous display or quit TestDisk, use the q (Quit) key.
    * To save modifications under TestDisk, you must confirm them with the y (Yes) and/or Enter keys, and
    * To actually write partition data to the MBR, you must choose the "Write" selection and press the Enter key. 

Code sudo testdisk-6.9/linux/testdisk_static

Here's how i did it; 

1. opened terminal typed 'pho' and hit the autocomplete button (tab) why didnt i just think of this in the first place ?? dur !!

2. Enlarged terminal window as 'Photorec' needs 25 lines to work

3. Of options : Disk /dev/hdc - 2048 B (R0)  selected Disk /dev/sdf - 320 GB / 298 GiB (R0)

4. Hit proceed   - N/B of note: Some disks won't appear unless your a root user. Disk capacity must be correctly detected for a successful recovery. if a disk listed above has an incorrect size, check jumper settings, BIOS detection, and install the latest OS patches and disk drivers.

5. now select the partion table type, pushing enter when done :
[intel] Intel/PC Partition   < my choice > usually the default value is the correct one as TestDisk auto-detects the partition table type
[Mac] Apple partition map
[None] non partitioned media
[Sun] Sun solaris partition
[Xbox] Xbox partition
[return] return to disk selection

6. checked file options photorec searches for, as i'm specifically searching for .jpegs

7. To recover lost files, Photorec needs to know the filesystem type were the files are stored:

[ EXT2/EXT3]  EXT2/EXT3 filesystem
[ Other] FAT/NTFS/HFS+/ReiserFS/. . .       < my choice

8. then i got fumbled so i looked up  

9. [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

10.  After following the above link , I located missing .jpegs . I recommend this tool for anyone who has accidently deleted a hard drive or has missing files which YOU KNOW are there somewhere.

---

### Post by bryncoles on 2008-04-27
hello! sorry to jump on an aging thread, but i was very impressed with this software when i first found it. it detected external drives when i plugged them in and recovered files fine. then i ran it as 'root', using the 'sudo' command. i was curious to see if it would work on the internal drives you see! 

now, it wont do anything at all unless i run as root - wont recover files from digital camera's etc. this is rather perplexing! have i changed the file permissions on it or something? how can i change it again to its initial state - where it could detect and read external drives without being root?

---

### Post by pac-man on 2008-05-14
I was wondering if this application works for this:

I was using ubuntu to transfer some files from my NTFS partition to the external drive (NTFS too). suddenly the system locked up and I had to reboot the computer using the power button. WHen I was back data was lost!

Can this application recover specific folders and files or only whole partitions?

---

### Post by az on 2008-05-15
> **pac-man said:**
> I was wondering if this application works for this:

I was using ubuntu to transfer some files from my NTFS partition to the external drive (NTFS too). suddenly the system locked up and I had to reboot the computer using the power button. WHen I was back data was lost!

Can this application recover specific folders and files or only whole partitions?

Testdisk can recover partitions.  The testdisk package also installs photorec which is a file-carving program.  File-carving can find lost files.

What data was lost and where was it (on your machine's disk or the external disk?)

There are other ways to restore lost files by using what's left of the filesystem.  

See 
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)
and
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by quixote on 2009-01-02
testdisk is a real find!  Thank you, thank you, thank you!  (I'd mark the official "Thanks" button, only it's not there for some reason.)

I managed to make an 8GB PCMCIA completely inaccessible by being careless and confused in Virtualbox - WinXP.  Needless to say, I had files on it that I *really* wanted.  I searched the forums, found this thread, installed testdisk, ran it, and was back in business.  The partition table had lost its end-of-file.  Testdisk wrote it back in, and everything was accessible again.

Why isn't that great program part of the OS?  Why doesn't it live right under "system tools"?

Thanks for the tip.  You saved me several days of maddening file recovery!

---

### Post by chicken65 on 2009-02-05
hey, i need some help...

im a complete newbie to this knoppix shiz nizzle, 

basically i went into test disk, it did its thaaang,

i eventaully found my drive and the files, and copied the entire DOCUMENTS directory (btw i had vista) - i booted knoppix from a cd i burned since my HD isnt working...

anyway i pushed c to copy, so where did that copy to? i just want my documents and then i say bye to this laptop! 

plze someone help

thanks

---

### Post by fluxerj on 2009-02-06
TestDisk is a data recovery designed to help recover lost partitions
and/or make non-booting disks bootable again when these symptoms
are caused by faulty software, certain types of viruses or human error.
It can also be used to repair some filesystem errors.

Information gathered during TestDisk use can be recorded for later
review. If you choose to create the text file, testdisk.log , it
will contain TestDisk options, technical information and various
outputs; including any folder/file names TestDisk was used to find and
list onscreen.

---

### Post by quixote on 2009-02-06
chicken65: one way to figure out where knoppix puts things might be to try the same process on a different machine that still works.

1) boot from the liveCD
2) tell it you want to copy a (small!) directory (=folder)

>>> pay really close attention to anything on the screen.  Is it telling you that it will copy to, say, "/dev/sda1" unless you specify a different destination?  That gobbledygook is linux's way of referring to specific drive.  The "/dev/sda" part refers to the physical object, say a 320GB drive.  "/dev/sda1" refers to the first "partition" on that object, i.e. a formatted portion that windows might refer to as drive c: for instance.  The next formatted partition would be /dev/sda2, and Windows might call that d:, and so on.  

Very often, size is the only way to figure out what equals what.  For instance, you know you have drives c: e: and f:, of 8GB, 20GB, and 200GB respectively. F: let's say is a USB hard drive to which you want to copy.  Linux calls them, for instance, /dev/hda1, /dev/hda2, /dev/sda1, but by the sizes you can guess which is which.  You might want to copy from, eg /dev/hda1 (drive c: ) to /dev/sda1 (drive f: ).

Anyway, back to the process:
3. Try to copy the files as you did before, and see where it puts them.
4. Go back to the bad laptop and try to copy the files to where you actually want them.

Hope it works!  Come back and tell us how it goes.

---

### Post by quixote on 2009-02-06
(Just parenthetically: this hasn't got anything to do with testdisk, as such.  It has to do with how to use a Knoppix LiveCD to recover your data.  If you search the forums using those terms, somebody has probably answered the question already, in much better detail than I can give.)

---

### Post by grs on 2009-03-02
When I tried running it I got a "segmentation error" and the PC froze, what does that mean? How can I get past it.

---

### Post by quixote on 2009-03-02
I believe (this is way beyond my level of expertise) that "segmentation errors" happen when the system is having trouble allocating memory.  That always leads to a system crash, but why it occurs can vary.  Maybe it could just be two pieces of software that didn't work well together, in which case a reboot is all you need.  Or I think it can also indicate deeper problems.  Why specifically testdisk might do that in your case, I don't know.  It may be a symptom of the same problem that led to you trying to use testdisk?  :-)

---

### Post by Dreamglider on 2009-03-05
I Like this alot :) i messed um my disk but am able to access it with testdisk.

i had a 80Gb disk with 3 partitions.
NTFS from beginning to 60Gb
EXT3 from 60 to 75Gb
and a swap at the end.
i did a dd if=/source of=/destination
Being a noob and confused i did it the wrong way around and when i finaly figured it out dd had coppied some 40Gb.
Now i know the ubuntu partition is there and safe and i also know that test disk cant see the ntfs partition as parts (some 40Gb) were written with 0'es is there a way to see the remaining 20 gb of the ntfs partition ?

---

### Post by noesiseon on 2009-03-06
I'm hoping someone with more testdisk experience than I have can help me out.

Due to an unfortunate series of events, my MBR and partition tables have been wiped out on a 160gb system drive with 3 NTFS partitions.  I am almost positive that no data has been lost, and I'd really rather not reformat.  Testdisk is able to see the partitions and all of their files just fine, but only if I search using "None" for partition type.

The problem is that when using "None", I am unable to create or write a new partition table.  Can someone please point me in the right direction for rebuilding the tables within testdisk, or at least using the info it generates?

Thanks.

---

### Post by noesiseon on 2009-03-06
Ok, I figured out how to do it after a lot of testing.  For anyone else who is interested, here's what I did:

1.  Make sure that testdisk is creating a log file as it goes.
2.  Use the "Analyse" feature on your "None" partitioned disk.
3.  After it finds the partitions, open up your log file.

In my case, the reason the NTFS partitions were not reading in the "PC" partition section was that the wrong Head and Sector #s were being used.  The proper #s are listed in the log file.  It looked something like 

D 35 heads/cyl(NTFS) 24 sectors/track : hdd 255 heads/cyl 64 sectors/track
So, in my case the partitions were use 35 heads and 24 sectors instead of the default 255/64.

4.  After you've figured out the proper number of heads and sectors for your partition(s), fire up testdisk again, but this time select "PC" for partition type.
5.  Go into "Options" and then "Geometry".
6.  Now change the cylinders and heads to the proper #s.
7.  Run "Analyse" and the partitions should show up and be writable to the partition table.

Hope that helps someone.

---

### Post by kiprit on 2009-03-23
I am trying to use testdisk but when i select advanced options the options that come are:
Type Superblock Image Creation and Quit
I do not have undelete option. Do you know what may be causing this?

If I am to use photorec can I filter the files it will search with the location of the folder to look for or with the file name?

---

### Post by mal_conductor on 2009-03-29
These are my notes on testdisk and photorec.

with a solution for recovering specific files and seeing what was the old file names:

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

### Post by DarkReo on 2009-09-08
Thing have happened after i accidently delete the partition of my external hard drive and i want to get back all my data on it. I'm a complete newbie.... what should i do?

I have done until the Rebuild part, but after that what should i do? Do I have to format the drive?:confused:   

EDIT: luckily i didn't format it!!! after the rebuild instead of format i do the following again.

What I have done the 2nd time is 
1st: choose "Create" option
2nd:select my external and choose "proceed"
3rd: Intel
4th: Analyze
5th: Quick search
6th: and this come out [http://i118.photobucket.com/albums/o81/NgRoMeo/changes.jpg](http://i118.photobucket.com/albums/o81/NgRoMeo/changes.jpg)
 I choose "continue" without changing anything
7th: Deeper search
8th: the same thing on step 6th come out i choose continue again
9th: Write

Lastly I want to say thank you for everyone's sharing the experience and thx for testdisk's helps!!

---

### Post by mal_conductor on 2009-10-23
> **DarkReo said:**
> Thing have happened after i accidently delete the partition of my external hard drive and i want to get back all my data on it. I'm a complete newbie.... what should i do?

I have done until the Rebuild part, but after that what should i do? Do I have to format the drive?:confused:   

EDIT: luckily i didn't format it!!! after the rebuild instead of format i do the following again.

What I have done the 2nd time is 
1st: choose "Create" option
2nd:select my external and choose "proceed"
3rd: Intel
4th: Analyze
5th: Quick search
6th: and this come out [http://i118.photobucket.com/albums/o81/NgRoMeo/changes.jpg](http://i118.photobucket.com/albums/o81/NgRoMeo/changes.jpg)
 I choose "continue" without changing anything
7th: Deeper search
8th: the same thing on step 6th come out i choose continue again
9th: Write

Lastly I want to say thank you for everyone's sharing the experience and thx for testdisk's helps!!

DARKREO,

Did the manual help you?

Did you find errors in the steps?
If there are errors I want to know so I can edit the manual.
I deleted my partition by accident, and the I recovered it using testdisk.  I wrote the manual after I recoverd the partition.  I had to recreate the problem and may not have been the same as my original problem; so the steps may have been different.

Thank you.

---

### Post by Hobbsilla on 2009-11-02
How would you go about doing this if you wanted to recover data from an external harddrive. Would you create the folder to where you want to restore you files in the external hard drive or you computer's internal harddrive? I accidentally formated my external harddrive and don't have enough space on my laptop to restore all of the files onto. Hope someone can help me.

---

### Post by quixote on 2009-11-03
Hobbsilla: you want to recover files off the *formatted* external HD?  I don't think you can do that with testdisk.  (Not sure.)  I think then your only option is direct disk reads, and going through the results cluster by cluster, and putting critical files back together by hand.  I haven't done that myself.  I know one of the commands involved is "dd" so you could search for "dd" "disk recovery" (all together on the search line).

Maybe there are better methods.  That one is very tedious and the files have to be life-or-death issues to be worth the bother.

To answer the HD question: best would be a second external HD as large or larger than the one you're trying to recover, assuming you're trying to recover the whole thing.

---

### Post by aysiu on 2009-11-03
> **Hobbsilla said:**
> How would you go about doing this if you wanted to recover data from an external harddrive. Would you create the folder to where you want to restore you files in the external hard drive or you computer's internal harddrive? I accidentally formated my external harddrive and don't have enough space on my laptop to restore all of the files onto. Hope someone can help me. You would create a folder on your internal hard drive and use ```
sudo photorec
``` to recover the deleted files off your external hard drive. You would need enough space to restore all the files onto, though, so either get a bigger internal hard drive or don't restore all the files.

More details here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

And, yes, it can be done even if the drive is reformatted. I've done it many times before.

---

### Post by Hobbsilla on 2009-11-03
According to Evergreen's Linux Techcons, Testdisk should be able to recover all/almost all of my files without the need of getting a new harddrive to transfer them over to. I'm about to test it out.

---

### Post by emc on 2009-12-15
Hello all!  I am so excited to be using Ubuntu and so proud of the community who have worked so hard to make this operating system what it is!  Now- I am a noobie Linux user and just starting out in college with Java programming next semester.  I have very little programming knowledge and never any command line work with Linux.  I was trying to dual boot Windows XP and Ubuntu when somehow I accidentally put an additional partition that was too large on one of my internal hard drives(1 Tera byte Hard-drive) I immediately went to Google for answers.  I quickly found Testdisk and installed it on Windows XP.  It found three partitions and said they were "bad" and from what I could tell it was due to over-lapping of space allocation.  (I truly meant to put Ubuntu on C drive so I don't know what I was thinking or doing when this all happened to my E drive...)  In any event, I could not figure out how to "restore" or "delete" one of the partitions.  After getting upset of this matter I finally said I'm done with Windows XP all together and I installed Ubuntu on my C drive knowing I was going to have to swim in the new world of Open Source because I can no longer take Windows and their crap.  I realize this happening was my fault and nothing to do with Microsoft but they were my enemy so I blame them nonetheless!  (lol)  Ok so I have loaded Ubuntu and I love it!  I found out how to install Testdisk using packages (bravo to me!) And a few hours later I even found where the package was installed!  An hour after that I figured out the whole "run by administrator using Alt & F2"  :)  

Ok... so I ran TestDisk and it found no partitions this time.  I am now going through the process of "deeper search" and it is taking a long time.  I suspect it will not be done for several hours.  

My question is this: 

Presuming it finds three partitions, what is my next step within this program?  I found them before while on the Windows XP side but after spending a few hours trying to figure out how to "fix" the partitions or even delete one of them, I was at a loss.  

If it finds no partitions - my problem is the size of this dang drive is 1 Tera byte.  I have no other drive that size that is empty to provide a copy and past of these files and photos etc...  

Any suggestions or potential solutions?  Thanks so much Ubuntu for any help you can give.  I am sorry for the long post.

---

### Post by Hobbsilla on 2009-12-15
Oh jesus. You're going to need to go out an get a 1TB external harddrive to be able to transfer all that data. I had a 250GB harddrive that recovered and it took about 11 or 12 hours. Your drive might take a couple of days.

---

### Post by Erik Trybom on 2009-12-28
Can Testdisk be used to recover a filesystem that was reformatted with *the same filesystem*? In my case, ext3 to ext3.

---

### Post by quixote on 2009-12-29
I don't think testdisk will work on a reformatted disk.  The only thing to try in that case is something that does direct disk reads.  aysiu's Nov 3 comment above has good info and links.

---

### Post by mal_conductor on 2010-01-06
> **Hobbsilla said:**
> How would you go about doing this if you wanted to recover data from an external harddrive. Would you create the folder to where you want to restore you files in the external hard drive or you computer's internal harddrive? I accidentally formated my external harddrive and don't have enough space on my laptop to restore all of the files onto. Hope someone can help me.

Hobbsilla,

Go here:  [http://ubuntuforums.org/showthread.php?t=1082417](http://ubuntuforums.org/showthread.php?t=1082417)

---

### Post by mal_conductor on 2010-01-06
> **emc said:**
> 
My question is this: 

Presuming it finds three partitions, what is my next step within this program?  I found them before while on the Windows XP side but after spending a few hours trying to figure out how to "fix" the partitions or even delete one of them, I was at a loss.  

If it finds no partitions - my problem is the size of this dang drive is 1 Tera byte.  I have no other drive that size that is empty to provide a copy and past of these files and photos etc...  


EMC go here: [http://ubuntuforums.org/showthread.php?t=1082417](http://ubuntuforums.org/showthread.php?t=1082417)

---

### Post by meganomics on 2010-01-08
First off, thank god for this thread (and all the knowledgeable people posting in it)--it's the only truly helpful thing I've found so far to help newbies use testdisk.

Here's my problem--I analyzed the partition structure with no apparent problems, and once it was finished it told me the structure was ok and both partitions showed up in green.

I now have the option to "Load backup," but when I choose this option I have no backups to restore (which makes sense, since I never created a backup, at least not that I was aware of).

I haven't done "deeper search" yet, and I noticed in the advanced options there is an "Image Creation" option which seems like the best bet for actually copying the drive--or is the problem that I didn't create a log when I was analyzing the drive [which I started about 3 days ago, so I can't really remember, but I could have sworn I elected to create a log].

At no point did I mess with the partitions of my HD, and they actually appear intact-- small EFI system partition, and then the main partition with all my data.  I'm trying to recover a 300GB harddrive off a macbook pro that seized up when I tried installing Snow Leopard.  The irony of all this is that my attempts to get KDE running on Mac OS X are probably what caused the SNAFU.  =p

---

### Post by quixote on 2010-01-08
meganomics: you're trying to get the data from the 300GB drive to another drive, one that's working, right?

You don't need to do deeper searches.  I don't remember the choices under test disk, but, yes, you want something like the "create image" option.  That means you'd have to have a disk drive of equal or larger size attached to the system where it could create that image.

But, first, are you sure you need to do that?  Have you tried booting from a LiveCD and checking to see whether your data partition is maybe normally accessible?  I'm not sure from your description whether you've done that already.

There may not be anything wrong with it.  If the OS partition is what blew up, you may need to reinstall an OS, but your data may not be involved at all.

---

### Post by meganomics on 2010-01-08
quixote: thanks for the reply.

of course, i was able to boot from a livecd of knoppix, but i'm guessing that's not what you're referring to.  i can't see the HD when i'm just in knoppix; i can only get at it through testdisk [though that may be because i don't know my way around knoppix very well].  i already tried to reinstall from the OSX dvd, but that told me the HD was partitioned wrong or corrupted or some such thing so that it couldn't install.  in fact, the computer can't do much of anything from the OSX disk, other than offer to erase all my data.  =p

is this what you were referring to?

---

### Post by quixote on 2010-01-08
Try booting with a LiveCD of Ubuntu to make it easier on yourself.  I'm not sure how knoppix refers to drives, (/dev/sda1 and the like, or something friendlier) but I'd guess if you can see the partition under knoppix, there may well be no problem there at all.  check using ubuntu.

The only real problem may be the Mac install disk being stupid, but that's the next problem after we're sure you have your data.

---

### Post by meganomics on 2010-01-09
Quixote:

You're the best!  I'm booted in Ubuntu right now and can see all my files.  Of course, now I have a new problem: I can't seem to get them onto the drive I was going to back up onto.

I get one of two error messages: one when a folder has a picture of an X over it, when I get the following:
The folder "Desktop" cannot be handled because you do not have permissions to read it.

I assume I need to be logged in or use the terminal to give myself privileges; but it's been a loooooong time since I used Linux, so I have no idea how to get around it.

The files I can view and try to move over give me this error message when I try to do so:
Error while copying "file.jpg".
There was an error copying the file into smb://harddrive.local/.
Operation not supported by backend

I don't have the remotest idea what this means or how to get around it.  I can view the files and open them and everything, but I can't move them over.  Is this because it's a stupid Apple-made hard drive?

Either way, at least my files are still there.

---

### Post by quixote on 2010-01-10
It's late here and I absolutely have to go to sleep, but I just wanted to say: don't worry.  Those are just drive mounting and permissions problems.  "smb" means samba is trying to get involved.  is this drive on another computer on the local network?  Much easier if you can use a usb HD or the like on the computer itself.  I'll get back on tomorrow and answer in a bit more detail.

---

### Post by quixote on 2010-01-11
(Sorry, forgot to get back. :( )  Okay, where were we?

First: are you trying to do this across a local network?  The commands are a bit more complicated then.

> folder "Desktop" cannot be handled because you do not have permissions to read it. What are the permissions and who owns the file?  You can see this by right-clicking on the name, selecting "properties" and going to the "permissions" tab.  

To change ownership you have to be the current owner to do that.  So if the files are owned by root, you have to use "sudo."  If not, you have to be logged in as the user who currently has the ownership.  e.g.: if Desktop is owned by root for some reason: ```
$sudo chown -R meganomics /home/meganomics/Desktop
``` (root says to change ownership recursively (-R) through all directories included under Desktop to meganomics starting with Desktop/).  

Be careful how use use the chown command.  Only use it on your home or data directories.  System files, eg in /etc and other places, must be owned by root or the computer will cease to work.  Make sure the directories you're specifying are the ones you think you're specifying.  You can test things by trying to list the dir first: ls -l /path/you're/testing.  ("-l" means "long" and makes it list owners and permissions too.)

> Error while copying "file.jpg".
There was an error copying the file into smb://harddrive.local/.
Operation not supported by backendThis sounds to me like trying to access a network drive without using the right command.  Is it a network drive?

---

### Post by eaglemystic69 on 2010-02-18
Help is appreciate . . . and totally needed.

Below is my testdisk.log upto a deeper test.  Im not a nubu to Ubu, Im a GUI guy and fairly dangerous with code that is more than cut and past.

**_Senerio_**:  I use LiveCD to format a USB external with gparted, instead of the "USB startup disk creator"..  .. Oh, what a dumb idea!  I lost the info to both USB drives with my backup files while connected together. (I forgot the master USB was still attached).  One USB was written over with 9.04 Jaunty and the other now contains the BOOT folder over the other set of files . . . .  while my laptop had a GRUB2 headspin for a while.  

If I can recover the USB drive with the BOOT (45mb) that wiped access to my files, I'll be alright (less data was over written I assume).  . . aside from hours and hours of figuring out how to search, ask, download, try, and ask again.  My hair has greyed since I began this journey into the terminal world.  

I have not seen any indication Testdisk has found my pics, music, docs, etc.   

I eventually want to save it to /media/storage/recovery

================================================

Thu Feb 18 21:25:49 2010
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.31-19-generic (#56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.9, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, LBA48, DCO support
/dev/sda: size       625142448 sectors
/dev/sda: user_max   625142448 sectors
/dev/sda: dco        625142448 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Warning: can't get size for Disk /dev/sr0 - 0 B - CHS 1 1 1 (RO), sector size=2048 - hp CDDVDW TS-L633M
Hard disk list
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA SAMSUNG HM320II
Disk /dev/sdb - 100 GB / 93 GiB - CHS 12161 255 63, sector size=512 - HTS42121 0H9AT00

Partition table type (auto): Intel
Disk /dev/sdb - 100 GB / 93 GiB - HTS42121 0H9AT00
Partition table type: Intel

Analyse Disk /dev/sdb - 100 GB / 93 GiB - CHS 12161 255 63
Geometry from i386 MBR: head=255 sector=63
FAT32 at 0/1/1
Info: size boot_sector 195366402, partition 195366402
FAT1 : 32-47705
FAT2 : 47706-95379
start_rootdir : 95380 root cluster : 2
Data : 95380-195366387
sectors : 195366402
cluster_size : 32
no_of_cluster : 6102219 (2 - 6102220)
fat_length 47674 calculated 47674
set_FAT_info: name from BS used
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * FAT32 LBA                0   1  1 12160 254 63  195366402
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sdb - 100 GB / 93 GiB - CHS 12162 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 100 GB / 93 GiB - CHS 12162 255 63
FAT32 at 0/1/1
FAT1 : 32-47705
FAT2 : 47706-95379
start_rootdir : 95380 root cluster : 2
Data : 95380-195366387
sectors : 195366402
cluster_size : 32
no_of_cluster : 6102219 (2 - 6102220)
fat_length 47674 calculated 47674
set_FAT_info: name from BS used

FAT32 at 0/1/1
     FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT32, 100 GB / 93 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT32, 100 GB / 93 GiB

interface_write()
 1 * FAT32 LBA                0   1  1 12160 254 63  195366402

search_part()
Disk /dev/sdb - 100 GB / 93 GiB - CHS 12162 255 63
FAT32 at 0/1/1
FAT1 : 32-47705
FAT2 : 47706-95379
start_rootdir : 95380 root cluster : 2
Data : 95380-195366387
sectors : 195366402
cluster_size : 32
no_of_cluster : 6102219 (2 - 6102220)
fat_length 47674 calculated 47674
set_FAT_info: name from BS used

FAT32 at 0/1/1
     FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT32, 100 GB / 93 GiB
FAT32 at 0/1/7
FAT1 : 32-47705
FAT2 : 47706-95379
start_rootdir : 95380 root cluster : 2
Data : 95380-195366387
sectors : 195366402
cluster_size : 32
no_of_cluster : 6102219 (2 - 6102220)
fat_length 47674 calculated 47674
set_FAT_info: name from BS used

FAT32 at 0/1/7
     FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT found using backup sector!, 100 GB / 93 GiB
NTFS at 1275/0/1
filesystem size           174883590
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               10930224
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1275   0  1 12160 254 63  174883590
     NTFS, 89 GB / 83 GiB
FAT32 at 1305/1/1
FAT1 : 32-42589
FAT2 : 42590-85147
start_rootdir : 85148 root cluster : 2
Data : 85148-174401563
sectors : 174401576
cluster_size : 32
no_of_cluster : 5447388 (2 - 5447389)
fat_length 42558 calculated 42558
set_FAT_info: name from BS used

FAT32 at 1305/1/1
     FAT32 LBA             1305   1  1 12160 254 62  174401576
     FAT32, 89 GB / 83 GiB
FAT32 at 1305/1/7
FAT1 : 32-42589
FAT2 : 42590-85147
start_rootdir : 85148 root cluster : 2
Data : 85148-174401563
sectors : 174401576
cluster_size : 32
no_of_cluster : 5447388 (2 - 5447389)
fat_length 42558 calculated 42558
set_FAT_info: name from BS used

FAT32 at 1305/1/7
     FAT32 LBA             1305   1  1 12160 254 62  174401576
     FAT found using backup sector!, 89 GB / 83 GiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
     FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT32, 100 GB / 93 GiB
     HPFS - NTFS           1275   0  1 12160 254 63  174883590
     NTFS, 89 GB / 83 GiB
     FAT32 LBA             1305   1  1 12160 254 63  174401577
     FAT32, 89 GB / 83 GiB

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sdb - 100 GB / 93 GiB - CHS 12162 255 63
Geometry from i386 MBR: head=255 sector=63
FAT32 at 0/1/1
Info: size boot_sector 195366402, partition 195366402
FAT1 : 32-47705
FAT2 : 47706-95379
start_rootdir : 95380 root cluster : 2
Data : 95380-195366387
sectors : 195366402
cluster_size : 32
no_of_cluster : 6102219 (2 - 6102220)
fat_length 47674 calculated 47674
set_FAT_info: name from BS used
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * FAT32 LBA                0   1  1 12160 254 63  195366402
Ask the user for vista mode
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 100 GB / 93 GiB - CHS 12162 255 63
FAT32 at 0/1/1
FAT1 : 32-47705
FAT2 : 47706-95379
start_rootdir : 95380 root cluster : 2
Data : 95380-195366387
sectors : 195366402
cluster_size : 32
no_of_cluster : 6102219 (2 - 6102220)
fat_length 47674 calculated 47674
set_FAT_info: name from BS used

FAT32 at 0/1/1
     FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT32, 100 GB / 93 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * FAT32 LBA                0   1  1 12160 254 63  195366402
     FAT32, 100 GB / 93 GiB

interface_write()
 1 * FAT32 LBA                0   1  1 12160 254 63  195366402
================================================
================================================

---

### Post by quixote on 2010-02-19
Ouch.  I'm almost positive that if you told it (even if by mistake) to install the operating system, it reformatted, which means the old partition table isn't there for testdisk to use.

Your only option is to use direct disk reads, which is generally a big pain, but it'll get really important files back for you if they haven't been overwritten. The usual program for that is photorec. [Aysiu's comment #28]("http://ubuntuforums.org/showpost.php?p=8231923&postcount=28") in this thread mentions it and has a link to more info at psychocats.de, which is always a useful site.

Losing data always turns hair gray.  You should see mine! :D

---

### Post by eaglemystic69 on 2010-02-19
Thank you Quixote for your reply,

Hmmm, now I have a stomach ache too. . . "she" wont be too happy!

So your saying it doesnt matter whether one USB drive got the OS and the other just the BOOT folder;  because they both were reformatted the "map" to all the files is gone, thus no easy way ti search in the dark?  If Im correct, photorec is a file-by file extraction, that will be tedious. . . .

OK, I'll look over the links

---

### Post by quixote on 2010-02-21
As I say, I *think* both would be reformatted.  When you installed, before it started, there's a screen that summarizes which operations will be performed, and there are check marks next to the partitions that will be formatted.  Can remember how that screen looked and which partitions had check marks?

Photorec is tedious.  No question about that.  But it is a nice feeling when you finally have a critical file back.

Hope you can get what you need off the drive!

---

### Post by eaglemystic69 on 2010-02-21
Thsnks for your replies.  Well photorec found my info on one drive better than the other . . .  Oh what fun, I now have 968 folders with 500 files in each.  Luckily only the last third is critic. . . time to get clicking!

---

### Post by asktoby on 2010-03-10
A note of thanks to the OP Higgo for helping me out of a sticky spot.

---

### Post by Fryphax on 2010-04-13
I'm trying to run this, with a lot of outdated commands and a pretty weak tutorial on the Testdisk site. I have Testdisk downloaded and extracted but can't figure out how to run it.

---

### Post by nitstorm on 2010-04-13
> **Fryphax said:**
> I'm trying to run this, with a lot of outdated commands and a pretty weak tutorial on the Testdisk site. I have Testdisk downloaded and extracted but can't figure out how to run it.

elucidate. did u download the rpm package? or did u download the deb package.

if u downloaded the rpm package, look the first post on this thread, you will have to install alien to change the rpm package to deb then u can use dpkg to install the software

the first post i think has all the info  or so i think, follow up the link on it. maybe that would help???

---

### Post by quixote on 2010-04-14
If it's an rpm, I would suggest just deleting all the extracted files start over with the deb.  Why make things harder than they have to be? :D  For a deb: download, then run: ```
sudo gdebi testdisk-downloaded-file.deb
```  If gdebi is not on your system, install via synaptic.

If testdisk is correctly installed, the rudimentary instructions on the testdisk site are at least enough to get you started.  If you still get nowhere, then you can give us the exact step where the problem arises.

---

### Post by woodslanding on 2010-06-12
I have a problem that doesn't seem to have been addressed here.

I wanted to repartition my main drive on a windows laptop, to install a second OS.  I've backed up all my data.  Partition Magic gave an error, so I looked at the drive with Testdisk.

It suggested I might have the wrong head geometry, so I changed it from 240 to 255.  Well, that is clearly wrong, but now I can do nothing to change it back.  I'm using a parted magic disk to run testdisk.  

Every time I startup, the disk head count is 255, and no partitions are found.  I change it in geometry, all the partitions are found, everything looks great, and I WRITE.  Then I restart.  And am right back where I was.

What am I doing wrong??  How is this head count being stored that rewriting the partition table doesn't affect it?  Or why would the table not be getting written??  

Testdisk seems to have written it fine.  It asks me to reboot.  The parted magic OS shuts down normally.

What gives?????

Any help greatly appreciated!!

-eric

testdisk.log attached

---

### Post by quixote on 2010-06-14
Yikes, I've never had the guts to change geometry!  I'm not sure what, exactly, that's done to your drive.  I'm thinking it's really good you made a backup!

Just for future reference, use gparted for partitioning rather than Partition Magic.  I've never had any issues with gparted in some five years of repartitioning drives.  Not that it does any good right now.

---

### Post by woodslanding on 2010-06-14
well, I gave up on getting the geometry changed back....

Interestingly enough, I did a low-level reformat on my drive, and the windows install disk couldn't recognize the drive!!

It's a hitachi travelstar in a Lenovo R61 laptop.

Gparted recognized it, and partitioned it.  I wiped the boot sector, and repartitioned with Partition magic.  Both programs have had no problem recognizing the other's partitions, and report no errors....

And I just put the drive in my desktop, which sees it, and I'm restoring my OS to it.  But neither of my xp disks (sp1 and sp3) can even tell I have a harddrive at all!!!

Has anybody heard of this problem?

Well I should post it in an XP forum, I suppose ;)

---

### Post by quixote on 2010-06-14
I'm pretty sure winxp can't see anything not formatted in its own filesystems, dos or vfat, or for sp3 maybe also ntfs(?).  I don't remember if win7 & vista are more broadminded.

(By the way, this is actually a quite different question than the topic of this testdisk thread, and in that case it's better to start a separate thread.  The tip-off is "that doesn't seem to have been addressed here" :D.  If you find yourself thinking that, start a new thread.)

---

### Post by mahela007 on 2010-06-21
Hullo.. I've tried using TestDisk to recover data from a flash drive. For some reason, the flash drive was corrupted after I plugged it into Ubuntu. (probably, I forgot to unmount it before pulling it out). Anyway, with testdisk, I was able to recover only 19 files about of about 300. Now, with another freeware application I was able to recover many more.. at least 150 files. Why is it that testdisk didn't do so well? Are there any setting that I should tweak?

---

### Post by noyz on 2010-06-24
i have a problem
i've used dd and do some damage to my hdd

so i've copied 1 hard info to another after 10 mb i realize i forgot count=1 and bs=...
and i cancel the proces..
now.. i'm trying to recover my data using testdisk
one partition - second one - extended.. is viewed ok 
but the first partition doesn't work and i have an error :
warning incorrect number of head/cyl 16 != 255
now at the geometry is correct.. 255
but the disc from where i used dd was 16..
my question is how do i force to set 255 to this partition ?
i forgot to say.. the second partition has 255 and there is no warning .. or smt 
like that

i have a fdisk -l before i broke the partition table and after

before :

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x374d0c22

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 41432 332802508+ 7 HPFS/NTFS
/dev/sdb2 41433 77826 292329324 f W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb5 41433 77826 292329292+ 7 HPFS/NTFS

after :

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Randymanme on 2010-07-14
[FONT=Times New Roman][SIZE=1]I did have windoze xp professional on sda1, windoze data on sda2; sda 3 (I think) was as extended partition that included sda4-sda11, of the which sda6 was c. a 4.x GiB swap, there was another swap partition of less than 1 GiB.  Sda5 (c. 23 GiB) held Linux Mint 9 and sda 11 held Ulltimate Edition 2.6.  The other partitions had been shrunk to make more space for sda5 and sda11, which at various times held various operating systems.     Two days ago, I booted a PCLinuxOS Gnome 2010 live CD and deleted Ultimate Edition with Gparted with intentions of installing PCLinuxOS Gnome 2010 on sda11.  But when I proceeded to install PCLinuxOS Gnome 2010, the wizard informed me that the hard drive was so corrupted that it could not  read it.  

The wizard offered to wipe the entire disk and start afresh.  I'd rather it not.

Let me clarify that I don't know what I'm doing.  It took me a lot of Googling to find out how to get a testdisk /list to give up data on System Rescue CD.  Please assume that I know nothing.  I would, however, like to restore things to how they were before (minus Ulltimate editon -- but things how they were with Ultimate Edition  would be better than how they are now).  I need some directions.  Any and all help will be much appreciated.

I was thinking that perhaps if I tried to install some distro, that it's installer would recognize the operating systems already written to disk and let me install to free space (i.e. sda 11), but all (Linux Mint 8 and 9, Ubuntu 10.04, Super OS 9.11 PCLinuxOS Gnome 2010) say that there are no operating systems on the disk.  Gparted said that the whole 250 GiB disk was unallocated.  However the disk utility packages on all of them (live CDs) did identify the presence of windoze as a bootable operating system (54 GiBs),  all recognized the presence of sda2 as a windoze data partition (135 GiBs), but nothing for Linux showed up, just a 61 GiBs block of &#8220;unallocated&#8221; space.  The disk utilities all said that the 61 GiB of unallocated space couldn't be formatted because no more partitions could be created.[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]Just for the record, Testdisk isn't installed on Isadora or Lucid live CDs, but I found it on Systemrescue CD and on PCLinuxOS KDE 2010 live CD.  I'm finding the latter easier to use.[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
root@sysresccd /root % testdisk /list
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <[EMAIL="grenier@cgsecurity.org"]grenier@cgsecurity.org[/EMAIL]>
[http://www.cgsecurity.org]("http://www.cgsecurity.org/")
Please wait...
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512
Disk /dev/sr0 - 258 MB / 246 MiB - CHS 126011 1 1 (RO), sector size=2048

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition         Start        End    Size in sectors
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  6527  14 63  104857137 [Windoze]
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 2 P HPFS - NTFS           6527  15  1 22901  65 36  263051496 [Data]
 3 E extended             22943   2  1 30400 254 63  119812644
 4 P Linux                22908   0  1 22942 254 63     562275

test_logical: 
Partition sector doesn't have the endmark 0xAA55
Disk /dev/sr0 - 258 MB / 246 MiB - CHS 126011 1 1 (RO)
     Partition         Start        End    Size in sectors

Partition sector doesn't have the endmark 0xAA55
root@sysresccd /root %  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]Finally, I  found out how to run Testdisk (somewhat), but it kept saying that the number of heads was incorrect.  Using the geometry menu, I tried 255, 240, 128, 64,32, and 16.  None worked. 255, 128, 64,32, and 16 all suggested 240.  240 suggested 255.  Frustrated over having spent hours and hours searching the forums and googling only to end up at this impasse. I highlighted the w(rite) option for what  Testdisk did find with the incorrect geometry.[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]As a result of that incorrect (w)rite and still using the PCLinuxOS KDE live CD, I opened Gparted and, viola!; Gparted no longer showed 250 GiBs of unallocated space.  Now, it showed the windoze partition, the windoze data partition and 61 GiBs of unallocated space.  I was disappointed over seeing nothing Linux other than some 7 GiB piece of some old partitiion, but was encouraged by some progress.  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]Next, I went to the disk utility and now it allowed me to format the 61 GiBs of unallocated space as ext4, and one extended partition (sda4 &#8211; 50.08 GiB) with two logical partitions (sda5 and 6 &#8211; 23.37 GiB and 22.76 GiB, respectively) and a swap (sda7 &#8211; 3.95 GiB).  On sda6, I've installed Linux mint 9 Isadora so that I can have a base to work from while still learning about how to use Testdisk (Firefox Sync and Siphon Sync come in handy here).[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]From what I gather thus far, Testdisk and/or Photo Rec are fully capable of recovering and restoring my lost partitions even though I've done some reformatting.  Which brings up a question:  where is the &#8220;paranoid&#8221; selection on the Options Menu of Testdisk 6.11-1?[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
                    [SIZE=1]
[/SIZE]                                [FONT=Times New Roman][SIZE=1][COLOR=#00407f]TestDisk             6.11, Data Recovery Utility, April 2009
Christophe GRENIER             <[/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=1][EMAIL="grenier@cgsecurity.org"]grenier@cgsecurity.org[/EMAIL][/SIZE][/FONT][FONT=Times New Roman][SIZE=1][COLOR=#00407f]>
[/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=1][http://www.cgsecurity.org]("http://www.cgsecurity.org/")[/SIZE][/FONT]
             
             [FONT=Times New Roman][SIZE=1][COLOR=#00407f]







Expert             mode : No
Cylinder boundary : Yes
Allow partial last             cylinder : Yes
Dump : No
[ Ok             ]








                                       Done with changing options[/COLOR][/SIZE][/FONT]
                  
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]randymanme@randymanme-desktop ~ $ fdisk -l  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]randymanme@randymanme-desktop ~ $ sudo fdisk -l  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]Disk /dev/sda: 250.1 GB, 250059350016 bytes  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]255 heads, 63 sectors/track, 30401 cylinders  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]Units = cylinders of 16065 * 512 = 8225280 bytes  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]Sector size (logical/physical): 512 bytes / 512 bytes  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]I/O size (minimum/optimal): 512 bytes / 512 bytes  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]Disk identifier: 0xffffffff  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]   Device Boot      Start         End      Blocks   Id  System  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda1   *           1        6528    52428568+   7  HPFS/NTFS  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda2            6528       22902   131525744+   7  HPFS/NTFS  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda3           22902       23863     7724032   83  Linux  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda4           23864       30401    52516454+   5  Extended  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda5           23864       26914    24507126   83  Linux  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda6           27431       30401    23864526   83  Linux  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]/dev/sda7           26915       27430     4144738+  82  Linux swap / Solaris  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]Partition table entries are not in disk order  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]randymanme@randymanme-desktop ~ $  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1]According to a post in  [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=1][[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=387922&page=2#")  [Ubuntu Forums]("http://ubuntuforums.org/index.php") > [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130") > [Other Community Discussions]("http://ubuntuforums.org/forumdisplay.php?f=125") > [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")  [[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=387922&page=2")**How to: Recover data with testdisk!  March 6th, 2009   #[21]("http://ubuntuforums.org/showpost.php?p=6850029&postcount=21") **[/SIZE][/FONT] 
      [FONT=Times New Roman][SIZE=1][noesiseon]("http://ubuntuforums.org/member.php?u=785034")[/SIZE][/FONT]
 
 [FONT=Times New Roman][SIZE=1]The testdisk log tells me  what the correct CHS is; but it's kind of complicated for me.  Could one  of my colleagues take at look and advice me?  It's ten (OOo) pages  long, so I'll just post a couple of pages here &#8211; hopefully they contain  the needed info.  As always, any and all help is deeply appreciated.   Thank you.

[/SIZE][/FONT]Wed Jul 14 04:18:01 2010 Command line: TestDisk  TestDisk 6.11, Data Recovery Utility, April 2009 Christophe GRENIER <grenier@cgsecurity.org> [http://www.cgsecurity.org](http://www.cgsecurity.org) OS: Linux, kernel 2.6.32-21-generic (#32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010) Compiler: GCC 4.4 - Jun 23 2009 17:11:34 ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none /dev/sda: LBA, LBA48, DCO support /dev/sda: size       488397168 sectors /dev/sda: user_max   488397168 sectors /dev/sda: dco        488397168 sectors Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512 Hard disk list Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - ATA ST3250820AS  Partition table type (auto): Intel /dev/sda: Device Configuration Overlay (DCO) present. Disk /dev/sda - 250 GB / 232 GiB - ATA ST3250820AS Partition table type: Intel  Analyse Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63 Geometry from i386 MBR: head=255 sector=63 NTFS at 0/1/1 heads/cylinder 240 (NTFS) != 255 (HD) NTFS at 6527/15/1 heads/cylinder 240 (NTFS) != 255 (HD) get_geometry_from_list_part_aux head=255 nbr=11 get_geometry_from_list_part_aux head=8 nbr=3 get_geometry_from_list_part_aux head=16 nbr=3 get_geometry_from_list_part_aux head=32 nbr=1 get_geometry_from_list_part_aux head=64 nbr=1 get_geometry_from_list_part_aux head=128 nbr=1 get_geometry_from_list_part_aux head=240 nbr=3 get_geometry_from_list_part_aux head=255 nbr=11 Current partition structure: Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)  1 * HPFS - NTFS              0   1  1  6527  14 63  104857137 [Windoze] Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)  2 P HPFS - NTFS           6527  15  1 22901  65 29  263051489 [Data]  3 P Linux                22901  68 16 23862 220 38   15448064  4 E extended             23863   0 62 30400 254 63  105032909  5 L Linux                23863   1  1 26913 254 63   49014252    X extended             27430   0  1 30400 254 63   47729115  6 L Linux                27430   1  1 30400 254 63   47729052    X extended             26914   0  1 27429 254 63    8289540  7 L Linux Swap           26914   1  1 27429 254 63    8289477 Computes LBA from CHS for Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63 Allow partial last cylinder : Yes search_vista_part: 1  search_part() Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63 NTFS at 0/1/1 heads/cylinder 240 (NTFS) != 255 (HD) filesystem size           104857137 sectors_per_cluster       8 mft_lcn                   4369047 mftmirr_lcn               6841572 clusters_per_mft_record   -10 clusters_per_index_record 1      HPFS - NTFS              0   1  1  6527  14 63  104857137 [Windoze]      NTFS, 53 GB / 49 GiB NTFS at 6527/15/1 heads/cylinder 240 (NTFS) != 255 (HD) filesystem size           263051489 sectors_per_cluster       8 mft_lcn                   786432 mftmirr_lcn               23970869 clusters_per_mft_record   -10 clusters_per_index_record 1      HPFS - NTFS           6527  15  1 22901  65 29  263051489 [Data]      NTFS, 134 GB / 125 GiB  recover_EXT2: s_block_group_nr=0/58, s_mnt_count=8/23, s_blocks_per_group=32768, s_inodes_per_group=8192 recover_EXT2: s_blocksize=4096 recover_EXT2: s_blocks_count 1931008 recover_EXT2: part_size 15448064      Linux                22901  68 16 23862 220 38   15448064      EXT4 Large file Sparse superblock, 7909 MB / 7543 MiB  recover_EXT2: s_block_group_nr=0/186, s_mnt_count=2/33, s_blocks_per_group=32768, s_inodes_per_group=8192 recover_EXT2: s_blocksize=4096 recover_EXT2: s_blocks_count 6126781 recover_EXT2: part_size 49014248      Linux                23863   1  1 26913 254 59   49014248      EXT4 Large file Sparse superblock, 25 GB / 23 GiB      Linux Swap           26914   1  1 27429 254 42    8289456      SWAP2 version 1, 4244 MB / 4047 MiB  recover_EXT2: s_block_group_nr=0/182, s_mnt_count=9/23, s_blocks_per_group=32768, s_inodes_per_group=8160 recover_EXT2: s_blocksize=4096 recover_EXT2: s_blocks_count 5966131 recover_EXT2: part_size 47729048      Linux                27430   1  1 30400 254 59   47729048      EXT4 Large file Sparse superblock Recover, 24 GB / 22 GiB get_geometry_from_list_part_aux head=255 nbr=7 get_geometry_from_list_part_aux head=8 nbr=3 get_geometry_from_list_part_aux head=16 nbr=3 get_geometry_from_list_part_aux head=32 nbr=1 get_geometry_from_list_part_aux head=64 nbr=1 get_geometry_from_list_part_aux head=128 nbr=1 get_geometry_from_list_part_aux head=240 nbr=3 get_geometry_from_list_part_aux head=255 nbr=7  Results    * HPFS - NTFS              0   1  1  6527  14 63  104857137 [Windoze]      NTFS, 53 GB / 49 GiB    P HPFS - NTFS           6527  15  1 22901  65 29  263051489 [Data]      NTFS, 134 GB / 125 GiB    P Linux                22901  68 16 23862 220 38   15448064      EXT4 Large file Sparse superblock, 7909 MB / 7543 MiB **   L Linux                23863   1  1 26913 254 59   49014248** 

 
 [FONT=Times New Roman][SIZE=1]
[/SIZE][/FONT]

---

### Post by Randymanme on 2010-07-14
Sorry about that ending block of text from the Testdisk log.  That's not the way I cut and pasted it.  I've tried to edit it so it appears as it was printed out, but when I hit the save or submit buttons, it gets garbled again.

---

### Post by cheezburga on 2010-12-09
Just a quick point out, the first post seems to regard data recovery, if I dont want to recover the data but want to recover my partition table, can someone help me with that?

---

### Post by dandoz on 2010-12-17
Thank you for this simple tutorial!  This helped me save a 750Gb data disk I had stored all my user files on in attempting to harmonize a dual-boot between Windows and Ubuntu.

---

### Post by GoBears2011 on 2011-01-17
New user - in need of help!

Here's the story - my NHD/NAS stopped working.  Hoping it was a problem w/ the network card I pulled the hardrive out of the NHD case and mounted it in an external case.  Windows 7 won't mount it, neither will XP, neither will a Mac.  The drive shows up in the device manager but won't mount.  It sounds fine spinning.  Quiet and no different than before.

The NHD was a 250GB Iomega black series.  The actual drive inside is a Western Digital.

After searching a while I came across some threads here.  I've been planning on trying Ubuntu for a while on an older laptop that really slowed down with XP SP3.  Loaded ubuntu up - all went very smoothly.  I'm quickly becoming a huge fan of the OS.

Now back to my problem - I plugged in the drive on my new Ubuntu system and it MOUNTED!!!  Well sorta..........see the 1st screen shot.  The drive shows up as 3 drives which I'm assuming are partitions.  I can actually access the middle 66 MB drive.  It contains what I suspect is the Linux operating system for the NHD.

If I try to access the other two I get a pop-up per:
For the 66 mb I can't access - "Error mounting" mount /dev/sdc2: can't read superblock"
For the 250 gb I can't access - "Error mounting" mount /dev/sdc4: can't read superblock"

I then tried to run the testdisk utility on the 250 gb drive.  I'm running it with the "NONE" option for the partition type b/c that is what testdisk defaults and with the Linux partition I can see I think that may be right??? It runs for about 4 hours and returns a screen shown in the 2nd shot - which is only a partial run screen shut b/c unfortunately I clicked something wrong and the testdisk returned me to the main menu.  When finished the list was 2x the size as shown.  Are these partitions?  Seems like an excessive number.  I have the scan running again and will update the post w/ a new screen shot when it finishes.  I don't recall the exact verbiage - but basically it said there were no partitions to recover.  

Any tips/ideas on what I'm doing wrong with testdisk or how I should proceed?  I really think the platters of the drive are probably fine.

If testdisk can't fix it - does anybody have a professional service they can recommend? I really need this drive recovered.

Stupid me - I had a 2nd drive ready to back up this 250 GB NHD.  Never did it.  That is a mistake I'll only make once!

Thanks in advance!

Dave

---

### Post by GoBears2011 on 2011-01-17
Here are some more screen shots after a complete scan.  My concern/issue is all the partitions found.  That can't be right can it?  On the green screens I'm scared to proceed to the next step b/c I may screw something up?

---

### Post by wilee-nilee on 2011-01-17
> **GoBears2011 said:**
> Here are some more screen shots after a complete scan.  My concern/issue is all the partitions found.  That can't be right can it?  On the green screens I'm scared to proceed to the next step b/c I may screw something up?

Start your own thread if you want help.:)

---

### Post by quixote on 2011-01-17
Hey, Wilee, give the guy a break.  He's a new user and he's just lost a drive!  Sheesh.

---

### Post by quixote on 2011-01-17
GoBears: I haven't had time to read your post properly yet, but first thing to try: instead of "none" for the partition type use "intel". I.e. back out of whatever point you've reached and start over from the beginning.  "Intel" should be the default and is generally the right answer for common and garden variety PCs.  The "can't read superblock" can be fixed by pointing it to another superblock on the system, assuming that's an ext3 or ext4 formatted linux drive.  I'll come back later with a bit more on that.  Try using "intel" first.  The problems may become a lot clearer.

Wilee's right that in general, it's a good idea to start a new thread for a new problem.

---

### Post by GoBears2011 on 2011-01-18
I'll kick it off in Intel mode and then start a new post with the results.  This drive never was in a computer BTW - it was an external drive w/ a network connection (NHD/NAS).  This combined with testdisk defaulting to NONE prompted me to try it that way.

Sorry for the gaff.....most of the car forums prefer updates to existing posts.

Big fan of ubuntu thus far.  Should have tried it years ago.

Here's the other post -
[http://ubuntuforums.org/showthread.php?p=10371472#post10371472](http://ubuntuforums.org/showthread.php?p=10371472#post10371472)

---

### Post by maxchock on 2011-02-21
wow!! great info. After install and I plug in my NTFS 1TB drive and it just work as expect!! Thanks for saving my time.

---

### Post by Aaron Peterson on 2011-08-31
Thanks for sharing this recovery tools. It is a little bit hard to recover deleted data if you don't have any software or tool to be use.

[how to restore recycle bin]("http://www.undelete-freeware.com/how-to-restore-recycle-bin/")

---

### Post by Alkestis on 2011-10-02
This thread just quite literally saved me years of work. Thanks a lot!
:D:D:D

---

### Post by connellc on 2012-03-09
"testdisk" is included on the Ultimate Boot CD ("testdisk" resides within the Parted Magic 6.6 Linux kernel that will load in RAM).

[www.**ultimatebootcd**.com  ]("http://ubuntuforums.org/www.ultimatebootcd.com")

   :D

---

