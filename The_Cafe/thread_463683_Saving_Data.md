---
title: "Saving Data"
date: 2007-06-03
forum: The Cafe
---

### Post by Naralas on 2007-06-03
Hehehe, I have this friends computer. Basically, the deal is, I save her data, and then I force her to use Linux for a month as payment.

The problem:
Recovering the files.

I have the computer booted to Kubuntu (good start)

the bad:
1) No internet connection, would take a lot of hard work to get it to a place in my house that I can hard wire it. (a lot!)
2) Filesystem (while known to me to be ntfs) is broken enough that linux goes "i dont know" and bitches when I try mount it /w
mount -t ntfs /dev/sda2 ~/Desktop/ntfs
```
wrong fs type, bad option, bad superblock, on dev/sda2
```
3) I know how to run file recovery windows-to-windows but my only method of doing that at this point is:
get a hard drive (i have one 8 gig free...) install XP, run file recovery, and pull the files one by one. IF that works...

i would rather wait out 20-30 minutes to see if anyone gets back with a method on how to do it with just kubuntu/command line. I do have a portable 40 gig hard drive to back up the data too... if she has more than 40 gigs of pictures then its gonna be a looong night

---

### Post by Lucifiel on 2007-06-03
Maybe you can backup her drive with norton ghost or some other imaging software so that if any of the data goes awry, you can just restore it.

---

### Post by Naralas on 2007-06-03
Pardon?

I don't have much Windows stuff available to me. I still fix windows, but beyond that, I am not gonna touch it again until my new PC, just for the games.

and also, I don't really understand you. You data needs to be recovered, then the rest can die

---

### Post by Lucifiel on 2007-06-03
Oh, I was just thinking that having some backup of the entire Windows partition would be better. 

That way, if anything gets screwed up, hey, you can just restore it. Seriously, it's too easy to toast everything.  

But I dunno. It's up to you and hey, you probably know better. ;)

---

### Post by FuturePilot on 2007-06-03
Maybe you should try Knoppix. It will mount all the drives automatically.

---

### Post by Naralas on 2007-06-04
Two and a half hours left on knoppix

can anyone PLEASE tell me a nice freeware recovery tool for windows? I can put this hard drive into another windows PC and try use it that way...

---

### Post by Lucifiel on 2007-06-04
Try PC Inspector File Recovery. When I used it, it was okay but still... I wouldn't know. Some of these file recovery software tend to be bork up all your data instead of recovering it. :p 

[http://www.pcinspector.de/file_recovery/uk/download.htm](http://www.pcinspector.de/file_recovery/uk/download.htm)

---

### Post by starcraft.man on 2007-06-04
Well it sounds to me since your having trouble mounting that theres errors on the partition/disk itself that need fixing (i'm feeling doubtful that knoppix will mount it with bad errors). I got two options for you.

First option, I think is the surefire one that will get you up and running. The product is called [spinrite]("http://www.grc.com/spinrite.htm") (great app, saved me twice already). It isn't free nor open source, in fact I think it costs around 90 dollars now. It is one of the best hard disk recovery utilities I've ever had the pleasure of using. It runs from a live CD (or bootable floppy) using FreeDOS, and gives you a GUI to manage your tasks. The program while its booted will have direct access to the lowest level of data on your drives (I assume the drive is an internal one your trying to save). It has multiple levels of effectiveness 1-5, your case seems very serious so I'd recommend going straight to recovery level 5.

Now, since I am thinking the price is probably bothering ya... I will just say this. The author doesn't really mind people using his product without paying (I've heard a lot find it work so well they go pay for a license after, he doesn't mind), there are numerous copies around on sites such as... [isoHunt]("http://isohunt.com/") (*wink*) I'm sure if someone were to search for "spinrite" he may find something.... he could then see there were iso's inside and burn one, boot and set it to "recovery level 5". All hypothetically of course ;).

The other option is[TestDisk]("http://linuxappfinder.com/package/testdisk"). I don't really have any experience with it, so your on your own if you choose that route. I have heard good things about it though :)

Thats my two cents, good luck with it. Oh and level 5 will take a **long** time (if you go that route, be patient and leave it running for hours alone), it will actually read/rewrite every bit of data on the partition multiple tiimes/passes (from 1 to 0 to 1), it is also almost full proof because its that thorough.

Hope ya get it fixed, make sure the friend keeps their end of the bargain :D.

---

### Post by Bigbluecat on 2007-06-04
I have used TestDisk twice to recover borked windows partitions. Did a good job both times. Turns out that the hard drive was failing and that was causing the windows errors. 

I believe you will find TestDisk on the Knoppix CD. Just open a terminal and type Testdisk to run. It is certainly on the GParted Live CD if you have that.

If not it can be downloaded from most repositories.

---

### Post by mips on 2007-06-04
> **Bigbluecat said:**
> I have used TestDisk twice to recover borked windows partitions. Did a good job both times. Turns out that the hard drive was failing and that was causing the windows errors. 

I believe you will find TestDisk on the Knoppix CD. Just open a terminal and type Testdisk to run. It is certainly on the GParted Live CD if you have that.

If not it can be downloaded from most repositories.

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by az on 2007-06-04
Use foremost from linux

[http://ubuntuforums.org/showthread.php?t=401093&highlight=foremost+recover](http://ubuntuforums.org/showthread.php?t=401093&highlight=foremost+recover)

---

### Post by Naralas on 2007-06-04
Well I tried to install TestData on Ubuntu live. Dependancies not satisfied. So lets HOPE you guys were right and its on Knoppix. If not, well... then ill be spending the rest of the night pulling out my hair.

Anyway, I ran it on knoppix, I am not sure how it works or what im doing, but I turned on "paranoid" and told it to run slowly. Hopefully it will show me the files afterwards, but even if it shows them, how do I recover it? (remember its running CLI)

---

### Post by Bigbluecat on 2007-06-05
If we are lucky TestDisk will be able to analyse and reconstruct a broken partition table. If it manages this then you will be able to read the disk in any file manager like Nautilus or MS Explorer.

You can find a few help pages here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can also use TestDisk to locate and I think copy files. See here:

[http://mirror.href.com/thestarman/testdisk.html](http://mirror.href.com/thestarman/testdisk.html)

---

### Post by mips on 2007-06-05
> **Naralas said:**
> Well I tried to install TestData on Ubuntu live. Dependancies not satisfied. So lets HOPE you guys were right and its on Knoppix. If not, well... then ill be spending the rest of the night pulling out my hair.

Anyway, I ran it on knoppix, I am not sure how it works or what im doing, but I turned on "paranoid" and told it to run slowly. Hopefully it will show me the files afterwards, but even if it shows them, how do I recover it? (remember its running CLI)

Read the test disk documentation/site as there is a issue with the knoppix version, you have to type a line of code into the cli to get it working if I recall correctly.

---

### Post by Polygon on 2007-06-05
+1 for test disc / PhotoRec

There are different situations on when to use test disc and when to use photorec, but they are both written by the same guys, and i know that PhotoRec was able to recover files from my hard drive that had is partition table COMPLETELY wiped. I could not even format the drive in ubuntu it was so bad. I had to plug it in to my bro's macbook and have it format to HFS+ and then reformat it as ext3.

i was able to use those tools from the live cd

---

