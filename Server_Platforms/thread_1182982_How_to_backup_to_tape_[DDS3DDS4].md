---
title: "How to backup to tape [DDS3/DDS4]"
date: 2009-06-09
forum: Server Platforms
---

### Post by marc22 on 2009-06-09
Hello,

I move from 2k3 server to Ubuntu platform.

I have problem with backup to tape device.

We want buy a DDS4 streamers, but before that i want to test how Ubuntu work with streamers, so i got old DDS3 (24GB compressed).

First i format tape

```
mt -f /dev/st0 erase
```

Next i start a copy
test file (backup of my  virtual mail server 13 GB zip file )


```
tar -czf /dev/st0 home/administrator/Desktop/backup/mail
tar: /dev/st0: Can't write: No space left on device
tar: fatal error: end
```
 

1) how to enable hardware compression  - i want use 24 GB.
Why it can't put on my tape this 13 GB.
What does mean hardware compression. Is this hardware compressed data less secure for errors than not compressed ?


2) Why it's say "fatal error" !!!
Why don't say "please repleace tape, mark following as 1/2.

It can't split data into feew tapes ?


I wan't to try everything on my desktop before i bought a production DDS4 for my server.

Please help me, maybye my question is stupid but i just move from Windows, where i use NT Backup.

---

### Post by HermanAB on 2009-06-09
Howdy,

Unless you enjoy the DIY method, use Bacula, Amanda or Zmanda.

---

### Post by lensman3 on 2009-06-09
I'm really digging here.  It has been 10 years since I have fooled with a tape drive.  I don't even have the "mt" stuff on my install any more.

Once you format the tape (which probably isn't necessary). Do a

"mt -f /dev/st0 rewind"

I would do the tar without the -z option.  I think this DDS3 automatically does a compression of the data stream as it writes it.  

Make sure you know the difference between /dev/nst0 and dev/st0 and how the tape interface handles rewinds and leaving tape to write the next file.

<FLAME ON>  My personal experience with a tape drive is that they make wonderful boat anchors.  With cheap disk, I would move the whole backup scheme to a HD and use the program "star" for super-tar.  <FLAME OFF>

You also might look at the pair of programs call "backup/restore".  These backup entire partitions to tape (or disk). They have dump levels and the two programs also maintain an index that is written to the tape.  With the index, files can be restored selectively.  But it requires the entire tape to be spun through to restore the files.

Old tape drives require blocking factors to get efficient writing densities on the tape.  Though blocking factors disappeared in the '90's.

Remember to that there is no "stretch tape" command.  In other words, write in the middle of a tape file and the data from there to the end of the tape is gone......

---

### Post by marc22 on 2009-06-10
Hello,
Thank you for reply.


1) Can you give me any examples of usage Bacula ?
I find a community docs[ https://help.ubuntu.com/community/Bacula]("https://help.ubuntu.com/community/Bacula") but it don't explain how to change tapes, and many other things.
I would like show a live example what i can try on my desktop computer.
I have try everying.

2) My DDS is auto rewind hardware.


Can you show me any software what allow me "backup" a folder to tape ?
When extend avabile space call "Please add new tape".

But it must be a console / web gui (on my servers i don't use x.org).


Feew years i'm doing backup to tape under Windows platform, many times i had to restore backup or single files. So i think this device is great. Better than HDD.  You can just move "read only" switch and nothing will destroy your backup, any virus or bug. You remove tape, put next. And that before put into safe ;)


On my desktop i try to load a "bat" software what allow to manage Bacula. But it won't start.
```

"administrator@administrator-opzsgu:~$ bat
/home/administrator/.themes/cochix-vista1.4/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/administrator/.themes/cochix-vista1.4/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/administrator/.themes/cochix-vista1.4/gtk-2.0/gtkrc:317: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/administrator/.themes/cochix-vista1.4/gtk-2.0/gtkrc:360: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
10-cze 10:16 bat: ERROR TERMINATION at parse_conf.c:829
Config error: Cannot open config file "./bat.conf": No such file or directory
"
```

I don't know why, i just install this. Don't change anything :/

---

### Post by HermanAB on 2009-06-10
Hmm, this is the 21st century and USB disk drives are way easier and faster for backups.
;)

---

### Post by shizakapayou on 2009-06-12
Read the manual for Bacula:

[http://www.bacula.org/en/rel-manual/index.html](http://www.bacula.org/en/rel-manual/index.html)

It takes a while, but Bacula is VERY well documented, and done so in a way that doesn't come down on you at all.  Plenty of examples included as well.

To install Bacula on Ubuntu 8.04, skip the repositories and download and install from source.  Google around a bit, there are some guides to installing it with MySQL.  I love it - it's been running my 16-tape LTO-4 autochanger for 6 months now.

---

### Post by jbcola on 2009-06-30
Hi,

Here is a quick and dirty script to backup the whole system on tape, and change the media as soon as the tape is full and create a full backup once every week.
It works great with a quantum SuperLoader series:
(backup.sh)
#!/bin/bash
exec > /var/log/backup.$(date "+%Y%m%d").log 2>&1
echo Backup start : $(date)
MAILTO=root@mysys
TAPE="/dev/tape/by-id/scsi-1QUANTUM_ULTRIUM_3_JN0746AME50228-nst"

renice 10 $$

# Full backup every Sunday
if [ "$(date +%a)" = "Sun" ]
then
        rm -f /var/log/usr.snar
fi

set -x
tar -cMvpf $TAPE --exclude=/proc --exclude=/lost+found --exclude=/var/spool/squid --exclude=/mnt --exclude=/dev --exclude=/sys / /boot/ --multi-volume --new-volume-script=/usr/local/bin/changetape --label "Daily backup for $(date +%Y-%m-%d)" --listed-incremental=/var/log/usr.snar
echo Tar RC: $?
set +x
echo backup finished: $(date)

and the tape change script (changetape):
#!/bin/bash
set -x
exec >> /var/log/changetape.$(date "+%Y%m").log 2>&1
MAILTO=root@mysys
echo Tape full, changing tape
TAPEDEV="/dev/tape/by-id/scsi-1QUANTUM_ULTRIUM_3_JN0746AME50228-nst"
CHANGER="/dev/tape/by-id/scsi-3500e09efff0e1607"
/usr/sbin/mtx -f $CHANGER status | grep "Storage Element 16:Empty"
if [ $? -eq 0 ]
then
        echo loading fist tape
        /usr/sbin/mtx -f $CHANGER unload
        /usr/sbin/mtx -f $CHANGER load 1
else
        echo loading next tape
        /usr/sbin/mtx -f $CHANGER next
fi
sleep 60
mt -f $TAPEDEV rewind
set +x



Quite simple, but works like a charm...

Best regards,
Jean-Luc

---

### Post by scorp123 on 2009-06-30
> **marc22 said:**
> First i format tape

```
mt -f /dev/st0 erase
``` Unnecessary.

---

### Post by scorp123 on 2009-06-30
> **HermanAB said:**
> Hmm, this is the 21st century and USB disk drives are way easier and faster for backups.  USB disks may be fine enough for home usage but in professional environments you'd still use tapes. Where I work we use LTO-4 tapes which can store 800 GB; max. data transfer speed is around 100 MB/s ... You can't do that stuff with USB disks :lolflag:

---

### Post by scorp123 on 2009-06-30
> **marc22 said:**
> Please help me  Read here.

[http://ubuntuforums.org/showpost.php?p=5428529&postcount=5](http://ubuntuforums.org/showpost.php?p=5428529&postcount=5)
[http://ubuntuforums.org/showpost.php?p=5428536&postcount=6](http://ubuntuforums.org/showpost.php?p=5428536&postcount=6)
[http://ubuntuforums.org/showpost.php?p=6339495&postcount=8](http://ubuntuforums.org/showpost.php?p=6339495&postcount=8)
[http://ubuntuforums.org/showpost.php?p=6341610&postcount=11](http://ubuntuforums.org/showpost.php?p=6341610&postcount=11)

[http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

In above tutorial it is assumed you're writing to *.tar.gz files on a disk. Just replace the filenames with SCSI device paths for your tape device (e.g. /dev/nst0) and voila, your backup should work.

---

### Post by Vegan on 2009-06-30
It never ceases to amaze me at how many want to cling to obsolete technology. A USB disk is much cheaper and 50x more reliable than any DDS tape will ever be.

If the USB disk is too small, a rack mounted commodity RAID server is common in corporations now.

Save you money/job and get a USB disk.

---

### Post by scorp123 on 2009-07-01
> **Vegan said:**
> It never ceases to amaze me at how many want to cling to obsolete technology. Aside from being false your comment isn't really helpful.

LTO-4 for example is from 2007, LTO-5 is still being discussed. So much for your theory about tapes being "obsolete". They're not. The successors of DDS-4 were launched in 2003 (DAT-72) and 2007 (DAT-160). And DAT-320 apparently will be launched sometime soon as well? 

OP's DDS-4 may not be brand-new but they're a good exercise.

> **Vegan said:**
>  A USB disk is much cheaper and 50x more reliable than any DDS tape will ever be.  Definitely not. A "USB disk" is still that: a disk. So it has mechanical parts moving around: spinning platters and moving heads. Drop it and your data is hosed. On the other hand you can kick a tape across the room and guess what: the data will remain intact.

> **Vegan said:**
>  If the USB disk is too small, a rack mounted commodity RAID server is common in corporations now. That's fine as file server and for a first level of backup. But what if you're required by regulations to store data off-site? You can't have a rack-mounted RAID server in a bank vault, can you? On the other hand it's no problem to rent a storage container somewhere or a safe or a bank vault and then fill them with backup tapes.

And even if OP is "just a home user" ... So what? He wants to use tapes. So instead of belittling his "clinging to obsolete technology" (which is nonsense! Tapes are _NOT_ obsolete!) would those who have no helpful answers to add to OP's question please move on? Thank you.

---

### Post by rapidflame on 2009-12-13
Simple, reliable backup 2 tape on linux servers using intuitive, comprehensive FOSS....
HAHA

doesnt exist.

---

### Post by WinterWeaver on 2009-12-13
I have not read the entire thread, but I thought I'd give my 2 cents anyway O.o

I recently installed, "Back in Time" via the software centre, and have to say that I'm really happy. I have set it to make a backup once a day, to a External USB hard drive I have lying around. It works really well, and I'm very happy with it.

worth a peek I think...

EDIT: Ooops, sorry didn't notice this was for the Server Edition, pls ignore my post >.<

---

### Post by Vegan on 2009-12-14
> **scorp123 said:**
> Aside from being false your comment isn't really helpful.

LTO-4 for example is from 2007, LTO-5 is still being discussed. So much for your theory about tapes being "obsolete". They're not. The successors of DDS-4 were launched in 2003 (DAT-72) and 2007 (DAT-160). And DAT-320 apparently will be launched sometime soon as well? 

OP's DDS-4 may not be brand-new but they're a good exercise.

 Definitely not. A "USB disk" is still that: a disk. So it has mechanical parts moving around: spinning platters and moving heads. Drop it and your data is hosed. On the other hand you can kick a tape across the room and guess what: the data will remain intact.

 That's fine as file server and for a first level of backup. But what if you're required by regulations to store data off-site? You can't have a rack-mounted RAID server in a bank vault, can you? On the other hand it's no problem to rent a storage container somewhere or a safe or a bank vault and then fill them with backup tapes.

And even if OP is "just a home user" ... So what? He wants to use tapes. So instead of belittling his "clinging to obsolete technology" (which is nonsense! Tapes are _NOT_ obsolete!) would those who have no helpful answers to add to OP's question please move on? Thank you.

If you need to maintain off-site backups, install a second file server in another branch office (or residence if needed) and use the network to sync the servers.

SATA disk arrays are now bigger than ever with 8U 50 disk boxes that can hold 100TB of data.

Tape lingers on only because of legacy users. Low cost hard disks are eating into new markets that tape never had a chance.

Back in the 80's tape made sense when disk were expensive. Today disks are dirt cheap.

---

### Post by windependence on 2009-12-16
I'm sorry, but it's quite apparent you have never worked in the enterprise, at least in the last 10 years. Tape is still widely used because it can be stored off site in protected vaults as a last resort for disaster recovery. Newer tape drives are fiber connected and super fast. While co-located backup is a nice idea, for large volumes of data that must be kept up to date, bandwidth is a problem. Online backup services for home users fail to address one of the mist common problems for the home user - viruses and malware. With a simple realtime backup, if your machine is infected your backup is infected - instantly. Incrementals, the type we do with TAPE media, are the solution.

I have seen you on numerous occasions refer to some technologies as "old" or "obsolete". Nothing could be further from the truth here. Tape is very much alive. Why do you suppose a company like IBM still makes their 3592 tape drives. They can hold 900GB on a single tape and they are fiber connected most times. backups can be done in a fraction of the amount of time as before, and guess what? I can stick it in my pocket and put it where there isn't any possibility of fire, or natural disaster. 

Latest and greatest isn't always the best. Bleeding edge is called that because you can get hurt if you use unproven technology all the time without regard to stability. 

Get your facts straight before posting things you have no clue about.

-Tim

---

### Post by Vegan on 2009-12-16
Well larger enterprises can afford OC-12 and faster private networks easy enough and so the internet idea I promulgated is usable.

For a small law shop, the tape and the USB disk are both feasible.

I have put a lot of time in to studying massive data centers where servers are a dime a dozen.

I like LUSTRE where servers are abstract and dead servers/datacenters are not a problem. LUSTRE is one idea.

Given a few branches this would work.

NASA has headaches galore so I like studying their solutions.
:guitar:

---

### Post by windependence on 2009-12-16
> **Vegan said:**
> 
I have put a lot of time in to studying massive data centers where servers are a dime a dozen.


:guitar:
Some of us have put in a lot of time ACTUALLY WORKING in large data centers on the order of 10,000+ computers. I'd say we know what we're talking about.

-Tim

---

