---
title: "How to increase raid performance?"
date: 2011-01-15
forum: Server Platforms
---

### Post by mogie on 2011-01-15
Hayio folks,

I got a raid5 array running mdadm x 3 1TB disks. Trouble is:

- I get 110++MB/s transfering writing TO the server through samba
- I get maximum 41MB/s READING.

...should be the other way. Gigabit, full dulpex both ways.

```
hdparm -Tt /dev/md1

/dev/md1:
 Timing cached reads:   9128 MB in  2.00 seconds = 4568.73 MB/sec
 Timing buffered disk reads:  128 MB in  3.03 seconds =  42.20 MB/sec
```

```
  description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7dff400-f7dff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=8) ioport:a800(size=4) ioport:a480(size=16) ioport:a400(size=16)

```

It then seems that the raidarray/drivers is the bottleneck here. 

Is there anything I should try here?

---

### Post by rubylaser on 2011-01-15
How big is the file you're transferring, I'm guessing your seeing  110 MB/s with SAMBA because of caching.  I would never expect those speeds via SAMBA with only 3 disks.  Can you paste the results of both reading and writing a file that's 4 times larger than the amount of RAM you have in the system to wherever you have your array mounted.  Something like this with bonnie++
```
sudo apt-get install bonnie++
```
```
bonnie++ -u root -d /storage/test/ | bon_csv2html > /storage/test/bonnietest.html
```

When you're done, if you open the bonnietest.html file in a webbrowser, it will show you your stats.

And then, a bigger dd write to the array too...
```
time dd if=/dev/zero of=/storage/10g.img bs=1k count=10000000
```

***NOTE: /storage is where I have my md0 mounted, your is likely different.**

---

### Post by elico on 2011-01-15
try to test first each of the phyzical drives
hdparm -Tt /dev/sda
hdparm -Tt /dev/sdb

if you are using samba and windows you can try two nice things:
[http://www.nirsoft.net/utils/download_speed_tester.html](http://www.nirsoft.net/utils/download_speed_tester.html)
try to test the download speed with this tool ^^
and also try to install basic apache and link a file from the raid to the apache directory
and try to download the file using also this tool and see the diffrent.

it's an approach that goes to another place...

---

### Post by mogie on 2011-01-16
Here we go with the Bonnie++ test: ... I think the output looked like crap... (then I mean the showing of the HTML site), but you probabbly can say more about it than I do :)

[HTML]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0//EN" "http://www.w3.org/TR/REC-html40/strict.dtd">
<HTML>
<HEAD><TITLE>Bonnie++ V1.03c Benchmark results</TITLE>
<STYLE type="text/css">
TD.header {text-align: center; backgroundcolor: "#CCFFFF" }
TD.rowheader {text-align: center; backgroundcolor: "#CCCFFF" }
TD.size {text-align: center; backgroundcolor: "#CCCFFF" }
TD.ksec {text-align: center; fontstyle: italic }
</STYLE>
<BODY>
<TABLE ALIGN=center BORDER=3 CELLPADDING=2 CELLSPACING=1>
<TR><TD COLSPAN=2 class="header"></TD>
<TD COLSPAN=6 class="header"><FONT SIZE=+2><B>Sequential Output</B></FONT></TD>
<TD COLSPAN=4 class="header"><FONT SIZE=+2><B>Sequential Input</B></FONT></TD>
<TD COLSPAN=2 ROWSPAN=2 class="header"><FONT SIZE=+2><B>Random<BR>Seeks</B></FONT></TD>
<TD COLSPAN=1 class="header"></TD>
<TD COLSPAN=6 class="header"><FONT SIZE=+2><B>Sequential Create</B></FONT></TD>
<TD COLSPAN=6 class="header"><FONT SIZE=+2><B>Random Create</B></FONT></TD>
</tr>
<TR><TD></TD><TD>Size:Chunk Size</TD><TD COLSPAN=2>Per Char</TD><TD COLSPAN=2>Block</TD><TD COLSPAN=2>Rewrite</TD><TD COLSPAN=2>Per Char</TD><TD COLSPAN=2>Block</TD><TD>Num Files</TD><TD COLSPAN=2>Create</TD><TD COLSPAN=2>Read</TD><TD COLSPAN=2>Delete</TD><TD COLSPAN=2>Create</TD><TD COLSPAN=2>Read</TD><TD COLSPAN=2>Delete</TD></TR><TR><TD COLSPAN=2></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-</B></FONT></TD><TD class="size">Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-</TD><TD>Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-</TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--</B></FONT></TD><TD class="size">                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--</TD><TD>                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--</TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP</B></FONT></TD><TD class="size">Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP</TD><TD>Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP</TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>myserver.domain.com 4G 66660  98 114886  15 22326   5 32802  42 46934   5 214.7   0</B></FONT></TD><TD class="size">myserver.domain.com 4G 66660  98 114886  15 22326   5 32802  42 46934   5 214.7   0</TD><TD>myserver.domain.com 4G 66660  98 114886  15 22326   5 32802  42 46934   5 214.7   0</TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>                    ------Sequential Create------ --------Random Create--------</B></FONT></TD><TD class="size">                    ------Sequential Create------ --------Random Create--------</TD><TD>                    ------Sequential Create------ --------Random Create--------</TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--</B></FONT></TD><TD class="size">                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--</TD><TD>                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--</TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP</B></FONT></TD><TD class="size">              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP</TD><TD>              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP</TD></TR>
[/HTML]

---

### Post by mogie on 2011-01-16
These are the all the 3 raid-TB disks:

/dev/sdb:
 Timing cached reads:   7154 MB in  2.00 seconds = 3579.45 MB/sec
 Timing buffered disk reads:  308 MB in  3.01 seconds = 102.32 MB/sec

/dev/sdc:
 Timing cached reads:   6870 MB in  2.00 seconds = 3437.45 MB/sec
 Timing buffered disk reads:  300 MB in  3.00 seconds =  99.90 MB/sec

/dev/sdd:
 Timing cached reads:   6266 MB in  2.00 seconds = 3134.87 MB/sec
 Timing buffered disk reads:  260 MB in  3.01 seconds =  86.39 MB/sec

---

### Post by mogie on 2011-01-16
time dd if=/dev/zero of=/mnt/tera/10g.img bs=1k count=10000000
10000000+0 records in
10000000+0 records out
10240000000 bytes (10 GB) copied, 112,573 s, 91,0 MB/s

real    1m52.731s
user    0m1.450s
sys     0m26.220s

---

### Post by mogie on 2011-01-16
time dd if=/dev/zero of=/mnt/tera/10g.img bs=1k count=10000000
10000000+0 records in
10000000+0 records out
10240000000 bytes (10 GB) copied, 112,573 s, 91,0 MB/s

real    1m52.731s
user    0m1.450s
sys     0m26.220s

---

### Post by rubylaser on 2011-01-16
Yeah, your Bonnie results are useless, there's no data in what you pasted.  Can you run the command like this 
```
bonnie++ -u root -d /storage/test/
```
and copy the results here without piping to bon_csv2html.  That should show the read speeds.  That's what I'm interested in.  All of these other tests are writing all the local machine, so I'd expect them to be fast on the local machine.

I'd like to see the results of bonnie++ run from another machine via the SAMBA share.  That will show us true read/write speeds via SAMBA.

Hope that helps.

---

### Post by disabledaccount on 2011-01-17
Software Raid5 is highly vulnerable to commonly ignored settings, such as chunk size and partition alignment, but also FS and journal configuration. FS_block_size/chunk_size factor can be critical under some types of load, mainly due to read-modify-write operations and controller bandwidth - it's very easy to loose 50%+ performance.

Additionally, integrated controllers are using built-in SATA splitters, what means that there are more ports than physical channels (usually 2x). To reach max performance each hdd should be connected to separate channel and ICHx chipsets are not exception.

oh, I forgot to mention about stride and stripe size - see ext3/4 manpages :)

---

### Post by mogie on 2011-01-18
Thanks for that :) 

Here's the output in raw:

```

Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
lnx.studby.ntnu. 4G 72004  93 101662  13 21514   4 39971  52 45058   5 210.4   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  2660  14 +++++ +++  2554  12  1914  10 +++++ +++  1165   6
lnx.studby.ntnu.no,4G,72004,93,101662,13,21514,4,39971,52,45058,5,210.4,0,16,2660,14,+++++,+++,2554,12,1914,10,+++++,+++,1165,6

```

---

### Post by mogie on 2011-01-26
bumpy jumpy :)

---

### Post by YesWeCan on 2011-01-28
You get 91MB/s writing to the RAID5 using dd. What do you get when you read? eg:
dd if=/dev/... of=/dev/null etc
I have a RAID10 and get 240MB/s reading. I understand RAID 5 is inherently slower due to the checksum calculations.
But as an earlier poster said, your slow Samba performance may not be due to your RAID array.

---

### Post by mogie on 2011-01-28
Mygod! Thank YOU for that post. 

Yeah, it really seems the RAID-array is the cause of it all. :D

I'm very stable reading at 42MB/s after in all my test now with dd, which is the same I get with SMB. I'm on googling for other threads about increasing performance now. But here are some info bout my fs if you got any ideas.

Is it possible to "convert" my fs to another one in Ubuntu btw?

Is there any "tags" or anything I should change that would help?

```

From my /etc/fstab: (using XFS on my raid 5 array)
UUID=83d287e4-0b19-470d-8f2a-3563cc07f443  /mnt/tera       xfs rw 0 0

```

Some MDADM info about the array:
```

# mdadm --misc -D /dev/md1

/dev/md1:
        Version : 00.90
  Creation Time : Wed Feb 18 17:17:21 2009
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Jan 28 23:07:15 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 4K

           UUID : 67ba08c5:1f23c5ac:8f867148:a67b3d53
         Events : 0.203176

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
       2       8       17        2      active sync   /dev/sdb1

```

---

### Post by YesWeCan on 2011-01-28
I am not expert on RAID 5. I would remark that 41MB/s is dismal. The array ought to be faster than the slowest HD. So something is seriously wrong here. And writing should be slower than reading due to the parity calculations.
Unless, of course, it is busy sync'ing the array. What do you get from 'cat /proc/mdstat'?

---

### Post by tgalati4 on 2011-01-28
Modern, high-capacity disks, with sufficient cache on board don't seem to benefit from software RAID under Linux.  You might get some speed increases with a real, enterprise-class RAID card and enterprise-class drives.  Don't forget the quality of your switches.  Unless you are using enterprise-class gigabit switches, the gigabit rating is a peak value.  Sustained is more like 1/10 of that.  And yes, 100BaseT sustained throughput is more like 1/10 or 10Mbits/sec or 12.5MBytes/sec.

Also, unless your cables are short, shielded, and properly terminated, with high-quality, class-6 wiring, your throughput will likely be less than you think.

---

### Post by mogie on 2011-02-04
My output of cat /proc/mdstat


```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdc1[0] sdd1[1] sdb1[2]
      1953519872 blocks level 5, 4k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>
```

Even though my network equipment is not high-end enterprice, it has been delivering stable transfers reading from the server. I use CAT6, 2m long cable from my client to my server.

Does chuck-size have any effect? I thought i read that 4k should be ok for my system when i set it up some time ago.

---

### Post by rubylaser on 2011-02-04
4k chunks are very small, why did you set your array up with such a small chunk size?  64k is the default. I have mine at 512k, because I'm serving large files.  Having to split your transfers into such small chunks could contribute to a slow down, but I don't believe that is the only problem.  You should try a more modest chunk size of 64k or 128k.

---

### Post by rubylaser on 2011-02-04
It is possible to change the chunk size **[COLOR="Red"]if you have a 2.6.31+ kernel and mdadm 3.1+[/COLOR]**. 

If you just want to change the chunk size, the new mdadm will do that for you 
```
mdadm --grow /dev/md1 --chunk-size=128
```

I have not personally tested this, but this is from the lead developer of mdadm.[http://neil.brown.name/blog/20090817000931-004]("http://neil.brown.name/blog/20090817000931-004")

---

### Post by RoboJ1M on 2011-02-20
I have 2.6.35 (ubuntu server 10.10 x64) and built mdadm 3.1.4 from source but I get:

```
james@hal:~$ mdadm --grow /dev/md0 --chunk-size=512
mdadm: unrecognized option '--chunk-size=512'
Usage: mdadm --help
  for help
```

Tried bleeding edge mdadm 3.2, --help doesn't mention --chunk-size.

How would you install it from scratch with a chunk size of 512? I don't have any data on there at the moment so it doesn't matter.

Regards,

J1M.

---

### Post by rubylaser on 2011-02-20
That's because I didn't look at the man page, I just posted the code from the developer's blog.  It appears that he didn't end up using the --chunk-size option, he used this format instead.
```
mdadm --grow -c 512 --backup-file=/root/md0_512chunk.txt /dev/md0
```

That should work, but as I said, I haven't resized my chunk size.

---

### Post by RoboJ1M on 2011-02-21
Doh! I was just reading the --help, not the man page. I always forget about them.

My entire OS is resident on md0 via LVM.
However I assume it's safe to boot the backup file on /boot/blah.txt as this is a USB stick on /dev/sdd1

I'm trying to get PCI passthrough working at the moment but I shall let you all know how it goes, I'll set it off when I got to bed.

One assumes this is going to take a long, LONG time on 3x0.5tb disks.

Thanks,

J1M.

---

### Post by jimmydorry on 2011-02-22
Not as long as it takes me to do anything on my 6x 1.5tb array. 

:lolflag:


Depending on what kind of files you are hosting, I completely agree with the suggestion of changing the block size. 

4k is far too small if you host movies and music files. If how ever you are hosting many many many small files, then a smaller block size would be recommended... but if this was the case, you would have better performance than you currently have.

As a point of reference, I get around 80MB/s on my RAID 5 array.

I'm thinking of changing my block size to 512 soon, I just need to finish getting it all stable again. I'm going through my array formating 1HDD at a time and letting it rebuild (each rebuild takes about 400mins OR 6.7hours).

EDIT: As a pro tip, forgive me if I miss-read that you have your OS on your array, but try not to host the OS on the array. Not only is your array always going to be working (decreasing the life of the array and performance), if anything happens to your array you won't be able to get some of config files that make life easier when moving the array to another OS. If possible, buy a cheap HDD and put your OS on it.

---

### Post by stevensake on 2011-03-30
> ** said:**
> 
I went with this [[color=black]Auto Meter 1298, Am 3-3/8'' Tachometer 8K[/color]](http://www.fasterthanthem.com/106458.html)

---

### Post by mogie on 2011-06-11
I would gladly announce that a chuck size of 512K increased the transfer-rate to the maximum for my ny 1Gbit-network. I now got write speeds lower than before (125--> ~90) but faster read speeds (42--> 117MB/s). I also, set in an extra hdd in my array, but I think and still hope the chuck size was the cause of the low transfer speed.

Case closed (finally...) thank everyone for sharing!

---

