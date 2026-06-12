---
title: "Is this a great system for dual boot win and ubuntu??"
date: 2018-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by mawil10132 on 2018-04-30
[B]Would this be a GREAT machine for dual boot windows and ubuntu! I'm about to drop the money down, but really don't know if this is a great system of not.

Processor[/B]                 7th Generation AMD A12-9700P Quad-Core Processor with Radeon™ R7 Graphics
             
         
                                                                                                                              **Memory[SUP]i[/SUP]**                 12GB, DDR4, 2400MHz, up to 16GB (additional memory sold separately)
             
         
                                                      **Hard Drive**                 1TB 5400 rpm Hard Drive
             
         
                          
                                                                            **Display**                 15.6 inch LED Backlit On-cell Touch Display with Truelife and FHD resolution (1920 x 1080)
             
         
                                                  
                                                                            **Video Card[SUP]i[/SUP]**                 Integrated graphics with AMD APU
             
         
                                                      **Wireless**                 802.11ac + Bluetooth 4.1, Dual Band 2.4&5 GHz, 1x1

---

### Post by Claus7 on 2018-04-30
Hello,

ubuntu won't have any problem with these specs. The issue is, 
what you need the computer about:
games?
spreadsheets?
math?
programming?
e.t.c.

I would suggest you 16GB memory without any regrets even if you start using gedit (it's memory usage is barely noticeable).

Also, my suggestion is: dual boot at the beginning. Then stick to one operating system and if you need anything extra use virtual box instead.

I give advice to my friends about sdd's, even though I do not have one. Your system will be much faster, yet it will be costly especially if you want to tally the size of the one you mention.

Regards!

---

### Post by thenailedone on 2018-04-30
I do not know the state of Linux with the latest AMD CPU's / onboard graphics but as far as hardware goes (and as has been alluded to above this post) a faster HDD will go a long way in giving you a better experience regardless of the OS you are using.

---

### Post by Geoffrey_Arndt on 2018-04-30
The "weak link" in the chain is the 5400 rpm HDD.    Get a fast SSD (read up about them first).   Even a slower SSD is faster than a fast HDD.   You can get a small one (like 120 GiB or 256 for the OS files) and use 512 GiB or 1 TB HDD just for storing things like media and so on.   I also prefer "All Intel" systems over AMD . . . all Intel meaning cpu and graphics and wireless.   Makes for a much smoother install and future maintenance.   AMD graphics can still be problematic for Linux.

---

### Post by oldfred on 2018-04-30
Some other AMD threads.
 MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)
Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[https://ubuntuforums.org/showthread.php?t=2380798](https://ubuntuforums.org/showthread.php?t=2380798)
Asus ROG Zenith & AMD Threadripper 2 SSDs
[https://ubuntuforums.org/showthread.php?t=2380617](https://ubuntuforums.org/showthread.php?t=2380617) 

I find SSD boot drive great for booting, loading files and even faster writes. But my typing speed or accuracy has not improved.

      
 Newer system
fred@Z170N:~$ sudo hdparm -t /dev/sdb2
/dev/sdb2:
 Timing buffered disk reads: 402 MB in  3.01 seconds = 133.44 MB/sec
fred@Z170N:~$ sudo hdparm -t /dev/sda4
/dev/sda4:
 Timing buffered disk reads: 1580 MB in  3.00 seconds = 526.41 MB/sec 


 fred@Z170N:~$ sudo lshw -C Disk -short
[sudo] password for fred: 
H/W path               Device     Class          Description
============================================================
/0/100/14/0/2/0.0.0    /dev/sdc   disk           30GB SCSI Disk
/0/1/0.0.0             /dev/sda   disk           250GB Samsung SSD 850
/0/2/0.0.0             /dev/sdb   disk           1TB HGST HTS721010A9
HGST Travelstar 2.5-Inch 500GB 7200RPM SATA III 32MB Cache 

My USB3 flash drive is faster on reads than 10 year old 160GB hard drive (but not writes). but also different systems, so not exactly comparable. 

 Older 160GB 5400 rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec
USB2 flash drive
/dev/sde1:
 Timing buffered disk reads:  50 MB in  3.07 seconds =  16.26 MB/sec 
   fred@Z170N:~$ sudo hdparm -t /dev/sdc4 #USB3 flash drive
/dev/sdc4:
 Timing buffered disk reads: 260 MB in  3.02 seconds =  86.18 MB/sec

---

### Post by Tadaen_Sylvermane on 2018-05-01
I run my server and pxe machines on the AM1 25w tdp APUs. Nothing but good to say about them. However they are older so they are more supported. Not sure how the latest and greatest will do. +1 on the ssd idea. I put an ssd in my laptop and never looked back. I've learned to live with less storage space. The speed is worth every thing and more that I've supposedly sacrificed.

---

### Post by monkeybrain20122 on 2018-05-02
Well no system is "great" for dualbooting Ubuntu and Windows 10 simply because it is a tricky configuration to set up and maintain 

Even if you read all those links by oldfred with all the caveats and system specific implementations and workarounds and then jump through the hoop to set up a dualboot successfully, maybe all of a sudden a Windows update arrives then poof the Ubuntu side doesn't work anymore, or though less likely, vice versa. This is an intrinsically fragile configuration mostly because MS (and the OEMs) makes it so,

If the question is whether the machine is great for running Ubuntu then it is much easier to give a straight forward answer

---

