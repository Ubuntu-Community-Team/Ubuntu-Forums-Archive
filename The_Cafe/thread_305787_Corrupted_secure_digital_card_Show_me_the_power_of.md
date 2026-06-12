---
title: "Corrupted secure digital card? Show me the power of Linux"
date: 2006-11-23
forum: The Cafe
---

### Post by Dual Cortex on 2006-11-23
[SIZE="4"]**[COLOR="DarkRed"]EDIT: I just need to find a way to be able to format this card and be able to use it again! there were no important files on it.[/COLOR]**[/SIZE]

Hey guys, so here goes the problem (not related to Linux at all):

My dad was messing around with his cell phone, he said he was using some feature  in his to put a password on the his memory card (oh, btw, it's actually a mini-sd card) and then ... well not sure of the details but the problem is that it  got corrupted as I'm not able to access it through his cell phone (doesn't even detect it), nor through Windows or Ubuntu (using a *mini-sd to SD* adapter in a USB 4in1-Combo reader).
On Windows, I cannot format it. Right clicking on its icon freezes the computer for a while, then the menu opens and clicking on "format" doesn't do anything.
I don't really know how to format it using linux or where I could find it on the filesystem... in fact I'm not even able to mount it.

So, anyway, in Ubuntu, double clicking on the ICSI SD Card icon brings up the messagebox you seen in the picture. After waiting for over a min, an following error appears on the messagebox (second picture).

[[IMG]http://img148.imageshack.us/img148/3097/screenshotwm5.th.png[/IMG]](http://img148.imageshack.us/my.php?image=screenshotwm5.png)

[[IMG]http://img291.imageshack.us/img291/7541/screenshot1hn9.th.png[/IMG]](http://img291.imageshack.us/my.php?image=screenshot1hn9.png)

Any ideas on how to fix this? 

Thanks

---

### Post by d3v1ant_0n3 on 2006-11-23
I haven't got an SD card handy (I know there's one floating around somewhere tho!), but does linux handle sd cards the same way it handles USB flash memory?

Is it possible to format the disc in Gparted?

---

### Post by punkinside on 2006-11-23
Formatting it with Gparted is one thing, you can also try:

```

sudo dd if=/dev/null of=/dev/sdb1

```

That should put all 0's in the drive. Its worth a shot since the data is corrupted anyway.

Also, there used to be a disk manager in dapper, I think you can try and format it with it.

---

### Post by Dual Cortex on 2006-11-23
At least Gparted recognizes something, but no, can't seem to format it or 'create' a partition.
[[IMG]http://img247.imageshack.us/img247/1565/screenshot2ek0.th.png[/IMG]](http://img247.imageshack.us/my.php?image=screenshot2ek0.png)

---

### Post by d3v1ant_0n3 on 2006-11-24
Going from that screenshot, it looks like you can make a new partition on the card- can you make a new partition formatted as fat32?

If not I'm all out of suggestions, sorry.

---

### Post by Dual Cortex on 2006-11-24
Trying to make a new partition takes me to a Window to set a disklabel. Clicked create (msdos disklabel), I wait for about 15 seconds, then it refreshes the GParted window and there's nothing different. Clicking on new again will, again, do the same thing as I described above.
Thanks for the help guys, I'm going to sleep... I'll check back tomorrow, see you!

---

### Post by Dual Cortex on 2006-11-24
Any ideas?

---

### Post by ctw on 2006-11-25
Hi Dual Cortex,

I've the same problem as you.
Yesterday I've puted out the SD card of my pocketpc and now not reconise it.

I tried to do the same as you but nothing of nothing.

Please any person with an idea?

TIA

---

### Post by ctw on 2006-11-25
I have the same error in my Sd-card:


catworld@thinkcat:~$ dmesg | tail 
[17180361.244000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180361.244000] sda: Current: sense key: Medium Error
[17180361.244000]     Additional sense: CIRC unrecovered error
[17180361.244000] Info fld=0x0
[17180361.244000] end_request: I/O error, dev sda, sector 64
[17180361.256000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180361.256000] sda: Current: sense key: Medium Error
[17180361.256000]     Additional sense: CIRC unrecovered error
[17180361.256000] Info fld=0x0
[17180361.256000] end_request: I/O error, dev sda, sector 120
catworld@thinkcat:~$

---

### Post by Dual Cortex on 2006-11-25
Searched on google extensively and only 1 person had the same problem with that phone (Nokia 6265i).
Any left over ideas? I'm willing to burn it in a microwave then throw it away... even if it doesn't fix it.
Ok, I'll do that after I really feel I did everything I could to find out a way to format it and use it again.

---

### Post by halocaridina on 2007-06-06
If you still have problems with this card, try the following:

sudo mkdosfs -F16 /dev/XXXX

where XXXX is the the name of the card in /dev

I was able to save a card that I thought was lost.

Good luck and please let post if it helped.

---

### Post by mcduck on 2007-06-07
I have fixed such cards using gParted (and fdisk sometimes). Just turn off automounting of removable drives and it should work fine.

Of course there may be physical damage on the card. In that case there's nothing you can do.

---

### Post by mips on 2007-06-07
[http://ubuntuforums.org/showthread.php?t=463683](http://ubuntuforums.org/showthread.php?t=463683)

Try Test Disc or Photrec

---

### Post by The Soundophiliac on 2007-06-07
I had the same issue and turning off automounting usb drives worked.

---

### Post by Enverex on 2007-06-07
If turning off automounting and using GParted doesn't work, try using FDisk on it and playing with it from there.

---

