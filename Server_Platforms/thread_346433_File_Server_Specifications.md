---
title: "File Server Specifications"
date: 2007-01-25
forum: Server Platforms
---

### Post by JamieC on 2007-01-25
There's a few forums this thread could've been posted to but I thought this one would be most appropriate, feel free to move it if it is better suited elsewhere.

I plan to build a file server for:-
[list]
[*] Nightly backups of home server, rotated over 30 days for 2 sites.
[*] File backups from three computers.
[*] Possible remote backups from College and such.
[/list]

So, I'm thinking of two hard drives. One for server operating system (20-40GB) and one for files (250GB), this should improve access speed as well as ensure if the drive with the operating system fails, the data is still present.

I could use RAID 1 to mirror the data hard drive for further protection, but this would be quite expensive and is it really necessary? How much more would RAID controllers cost me on top of a basic set up?

So, let's talk specifications. I plan to use a combination of FTP and rysnc to backup, the server software required to run is therefore hardly intensive. I guess 512MB of RAM would be fine, what about the processor?

What would be a realistic figure to accomplish this build? What specifications would you recommend (from the ground up, PSU, motherboard, the lot)?

Here's a brief recap of the questions:-
[list=1]
[*] RAID or not? How much would it cost me?
[*] What would be the optimal specifications?
[*] How much would this cost me?
[/list]

Thanks, Jamie.

---

### Post by jtc on 2007-01-25
If you are only going to use it for your personal backups I don't think you'll have that intense load which would make performance an issue. Pretty much any processor P2 or above would do fine, and it might just as well work with an older one as well. When it comes to the RAM I'd say you ought to go for something above 128mb to be on the safe side, but it would probably work with less.

Generally Linux-servers themselves hardly require any computerpowers at all. It is first when you have a high load on the server with lots of simultaneous connection you need new fancy hardware.

Again, performance probably not being critical, it should do just fine to have RAID1 using software-RAID. The only thing which will cost you then, using RAID, is another harddrive. Don't forget that the drives in the RAID ought to be the same size, since you'll only the get the size of the smallest one.

When it comes to the actually backup I'd suggest you take a look at [Rsnapshot]("http://www.rsnapshot.org/"). If I understood you plan correctly, it might just be the thing for you.

---

### Post by JamieC on 2007-01-26
Thanks for that, here's what I've put together so far:-

[list]

  [*] **Motherboard**:
    [list]
      [*] [P5vd2-mx S775 P4m890 Matx - Vga+snd+lan+u2 Fsb1066 Sata In](http://www.ebuyer.com/117611)
      [*] £37.02
    [/list]

  [*] **Processor**:
    [list]
      [*] [Intel Celeron D 331 (2.66Ghz) Socket 775 FSB533 256kb Cache Emt 64 Retail Boxed Processor](http://www.ebuyer.com/093116)
      [*] £24.95
    [/list]

  [*] **Memory**:
    [list]
      [*] [Ebuyer 256MB DDR2 533MHz PC2-4200 240pin Extra Value Ram](http://www.ebuyer.com/082222)
      [*] £15.00
    [/list]

  [*] **Drive**:
    [list]
      [*] [LITEON DVD8900/DW1670 16x DVDRW/RAM Bare Black - OEM](http://www.ebuyer.com/119566)
      [*] £18.21
    [/list]

  [*] **Case**:
    [list]
      [*] [Casecom KL-700ATX Black Midi Tower Case - With 20pin 350W PSU and Thumbscrews](http://www.ebuyer.com/090874)
      [*] 014.99
    [/list]

[/list]

The total cost of the build is £110.17 (about $197.78). I'd also need fans, cables and the like. I'll buy the hard drives separately, too.

What do you guys think of that?

---

### Post by aPello on 2007-01-26
That will more than fit your needs.

---

### Post by thornomad on 2007-01-27
> **JamieC said:**
> 
**Motherboard**:
    [list]
      [*] [P5vd2-mx S775 P4m890 Matx - Vga+snd+lan+u2 Fsb1066 Sata In](http://www.ebuyer.com/117611)
      [*] £37.02
    [/list]


Does that motherboard come with hardware RAID built-in ?  Pretty good deal, it seems.  

I would like to build a file server as well, thanks for asking the questions.  Although, I plan not to use mine for backup, but for active file serving.  I want to get all my files in a central location instead of on so many different machines.  The file server would also automatically backup to another machine as well as serving the files for myself and girlfriend.

Haven't take the time to really put it together yet, and to answer all my security concerns.  Would like to be able to access my files via SSH over the net; and mount drives on my local machines (as well as from afar).  Still a little paranoid but will get there.

D

---

### Post by JamieC on 2007-01-27
> **thornomad said:**
> Does that motherboard come with hardware RAID built-in ?  Pretty good deal, it seems.  

I would like to build a file server as well, thanks for asking the questions.  Although, I plan not to use mine for backup, but for active file serving.  I want to get all my files in a central location instead of on so many different machines.  The file server would also automatically backup to another machine as well as serving the files for myself and girlfriend.

Haven't take the time to really put it together yet, and to answer all my security concerns.  Would like to be able to access my files via SSH over the net; and mount drives on my local machines (as well as from afar).  Still a little paranoid but will get there.

D

It sure does according to the [official page](http://www.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=1200&modelmenu=1) for the motherboard:
> 
  **Storage/RAID**
  
  ***VIA 8237A South Bridge:***
  [list]
    [*]  2 x UltraDMA 133/100/66/33
    [*] 2 x Serial ATA with RAID 0, 1, JBOD function
  [/list]

  ***JMicron JMB363 SATA controller:***
  [list]
    [*] 1 x Internal Serial ATA 3 Gb/s
    [*] 1 x External Serial ATA 3 Gb/s  (SATA On-the-Go)
    [*] supports RAID 0, 1 & JBOD
  [/list]


---

### Post by thornomad on 2007-01-27
Neat - would be interested to hear how your venture goes.  I may test some hardware/network setups on an older laptop before I go ahead and buy a new system.  Am particularly curious about the remote access piece and how fast gigabit ethernet transfer speeds end up being (if for regular data files and mp3 and pictures it is even noticeable as compared to a physical hard drive in the box).

---

