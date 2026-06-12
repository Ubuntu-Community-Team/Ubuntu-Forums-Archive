---
title: "Before I hit reset, server maxed out of resources"
date: 2009-01-18
forum: Server Platforms
---

### Post by volkswagner on 2009-01-18
I was in the middle of uploading a .tar.gz file of about 350Megs.  Using Webmin file uploader, the system maxed out Ram, Swap, and CPU cycles.  I am not sure what to do.  I don't want to hard reset the server.  

The system is not mission critical.  It is an under powered Pent2 400Mhz, 384Meg RAM, and 1Gig swap.

I was able to run top, while uploading, see results below.

As can be seen I started a second webmin session to see if I could verify file was downloaded.  

I am currently logged in via ssh.  The terminal response is painfully slow (several minutes before keystrokes show on screen). At the moment it seems unresponsive.  I tried ctrl+c, to no avail.  Is there anyway to "refresh" the session? 

If I were to successfully issue a command what should it be?  Should I try to stop Webmin, networking, apache2, or something else?

Is there anything else I can do, if ssh becomes unresponsive?


```
top - 09:42:43 up 53 days, 16:48,  1 user,  load average: 10.38, 6.92, 4.03
Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.9% us,  7.7% sy,  0.0% ni,  0.0% id, 89.5% wa,  0.9% hi,  0.0% si
Mem:    320832k total,   316756k used,     4076k free,      156k buffers
Swap:   923696k total,   651372k used,   272324k free,     3152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   65 root      15   0     0    0    0 D  2.4  0.0   1:23.67 kswapd0            
 5739 eric      17   0  2192  856  668 R  0.4  0.3   0:00.91 top                
 3782 nobody    16   0  4632  652  568 S  0.2  0.2   0:40.75 proftpd            
 4856 postgres  17   0  9440  296  276 S  0.1  0.1   0:03.76 postmaster         
  324 eric      17   0  7524  692  616 D  0.1  0.2   0:00.92 sshd               
 3964 eric      18   0  739m 281m  956 D  0.1 89.9  15:34.85 miniserv.pl        
 5774 root      18   0 10360  816  720 D  0.1  0.3   0:00.09 miniserv.pl        
    1 root      17   0  1568  332  324 S  0.0  0.1   0:03.34 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   66 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
  656 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
```

---

### Post by electrogeist on 2009-01-18
Maybe it is just taking longer than you expected to write the 350MB file to disk?

look at the line
Cpu(s):  1.9% us,  7.7% sy,  0.0% ni,  0.0% id, [COLOR="Red"]89.5% wa[/COLOR],  0.9% hi,  0.0% si

from the top man page:

[I]wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.[/I]

The high memory usage for this process:```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3964 eric      18   0  739m 281m  956 D  0.1 89.9  15:34.85 miniserv.pl        
```

may be because it copied the file into RAM from the network before it finishes writing to disk?


Now some thoughts on disk performance on old P2 systems.  I am not sure what kind of drive you have in there...drives from that era were slow.  Even if you plugged in, say a newer faster 120GB drive, the controllers on those old P2 motherboards (chipsets like 440LX/GX/maybe BX too) usually only support ATA/33 at best.  Usually you won't notice a performance difference between say ATA/66 vs ATA/100 vs ATA/133, the speed is mainly limited by the drive itself.  I always considered those speeds to be a crock of sh!t because for many years even the fastest drives were <50MB/s.  **However, there is a *huge* difference in performance between ATA/33 and ATA/66 controllers**.  You do not want to use a ATA/33 controller...with the mode it will run in you will not get anywhere close to the theoretical 33MB/s with ATA/33...it'll be way under 20.  An easy way to increase performance is to get a at least a Promise ATA/66 PCI controller, and if you want to support a drive >128GB a ATA/133 or later model ATA/100.  Note that if you are using the original drive that came with the system the controller prob won't make a diff, but if it is 20GB+ you will prob see a huge diff!
 
There may be issues aside from the disk performance but this pops out at me as being a likely culprit.

To get a rough estimate of drive speed try a "sudo hdparm -t /dev/hda" for whatever your drive is, and remember that in the real world it is probably writing your file slower than that

---

### Post by volkswagner on 2009-01-19
Thank you so much for the comprehensive response.  You hit the nail on the head.  I just needed to wait it out.  Odd thing is I don't know where the file landed, must have failed.  

I need to check logs, where do I look?

You also answered many questions I had about this box.  I have new hardware for a new/replacement server.  I was wondering about converting the pent2 to a NAS.  I was concerned about disk performance.

The hard disk is the original 9gig (actually warranty replacement cir. 1999).  I ran hdparm for an earlier thread.  Ironic it was for 6.06 vs 8.xx disk performance.

If you are correct about writing to memory first, it becomes clear.  When I upload much smaller files, the performance is acceptable.  I was trying to save some user input by creating an archive of multiple files.  The archive was actually 368Megs, was too close to real RAM capacity.

This should really prompt me to invest more time in the new server.

I am so happy I did not have to hit the reset.

Patience _is_ a virtue.

---

### Post by volkswagner on 2009-01-25
Well I just wanted some opinions here.

I am considering purchasing a disk controller card (raid/non-raid not a big issue).

I am weighing the cost of adding hardware to an old box to see if it is worth it.  Since SATA drives seem to be less expensive per gig, I am looking at SATA/PCI controllers.  I need compatibility with ver. 2.1 slots, so this limits choices.

Considering [this card, ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132013")due to free shipping and includes the power adapters.  So the price seems reasonable, and has reports of linux support but FreeNAS seems hit or miss.

If I want to build a Network storage box, would this old hardware give me adequate transfer speeds across a 10/100 network?

Hardware: Pent2 400Mhz, 384Megs RAM, on [QS440BX]("http://www.bcmcom.com/tech/QS440bx/QS440BX.htm") MOBO.

So with current on board IDE controller hdparm has poor results.

```
/dev/disk/by-uuid/f53dcd73-f939-4049-8179-740d1972b629:
 Timing cached reads:   456 MB in  2.01 seconds = 226.87 MB/sec
 Timing buffered disk reads:   40 MB in  3.03 seconds =  13.20 MB/sec
```

If I do the upgrade, should I keep the slow old disk on the MOBO for the OS only, with the proposed new controller for network shared data?   Or should I load the OS to the faster newer disk(s) on the PCI controller, along with shared network data?

---

### Post by electrogeist on 2009-01-27
one more thing...

100 megabits per second = 12.5 megabytes per second

add a fast hard drive and the NIC is the bottleneck, add a GigE NIC and the PCI bus is the bottleneck (or CPU becomes bottleneck first)

---

### Post by volkswagner on 2009-01-27
> **electrogeist said:**
> one more thing...

100 megabits per second = 12.5 megabytes per second

add a fast hard drive and the NIC is the bottleneck, add a GigE NIC and the PCI bus is the bottleneck (or CPU becomes bottleneck first)

Thanks for the reply.

I am still learning bits, byte, etc.  From my research it appears I have a 33Mhz PCI bus.

From Wikipedia: > # 33.33 MHz clock with synchronous transfers
# peak transfer rate of 133 MB/s (133 million bytes per second) for 32-bit bus width (33.33 MHz × 32 bits ÷ 8 bits/byte = 133 MB/s)



I found an online bit/byte calculator.  I plugged in the 133MB which yielded a theoretical 1.039 giga-bit.

I theory This old box could support giga-bit speeds on the PCI Bus.  So this is worth the experience.  I am going to throw in the SATA controller and a Gb/NIC and see how well the CPU holds up.  I guess the next thing is the lack of ram.  The original documents say max ram at 384MB.  The MOBO suport site lists 768MB max.  I don't see this as an updated BIOS function.  I wonder if in 1998, they had no idea 256MB sticks would be produced?

@ electrogeist, Thanks again .

---

### Post by Vegan on 2009-01-27
My antique IBM has a Pentium III and I have no problems with it feeding large files. Mind you it has 768MB of RAM after I scrounged up a 512MB SDRAM stick for it. Even before the RAM upgrade I never seen any problems.

If Perl is running slow, then adding RAM will help a lot.

As for disks, the old machines have a 137GB limit, so the boot disk cannot be too big. You can add another huge disk without problem and cure the storage problem.

:guitar:

---

### Post by electrogeist on 2009-01-27
Yes, your calculations are correct - however that 440BX's single PCI bus is shared with every card and integrated component, with exception of AGP graphics. If you do a "lspci" I'm pretty sure you'll notice that everything is listed as 00: except AGP will prob be 01:.  There is some overhead that will subtract from the 130MB/s too, and moving alot of data will tax that P2.  Pulling a # out of my ***, maybe you could sustain up to 30MB/s across a gigabit network to disk. 

Having a seperate data drive from the drive with OS & swap has its performance benefits especially with low RAM.  On the downside though, that old drive is slow and may possibly cause more of a lag than you'd like with web administration interfaces, or anything else on that drive.  But yeah I'd say separate drives is the way to go.

Yes alot of boards originally did spec less memory capacity than they could hold, due to bigger modules not being invented yet.  A problem you may find is some later (and usually less expensive) memory is too high density and will not work.  Look for 256MB PC100 or PC133 modules (not Registered! Probably not ECC! Some BX boards do support both but yours does not state it so go unbuffered non-ECC) that is double sided with 8 chips per side.  That should be pretty much guaranteed to work.  For cost of 768MB of this old RAM you could have a multiple GB of DDR2 :(

Cost in upgrading this system is hard to justify.  I would only want to spend $$ on components I think I may use in the future too.  While the CPU is upgradable to a P3 at twice the speed, and socket370 P3's are a dime a dozen, 100MHz FSB slot1 CPUs that you need tend to cost more.  Ditto with memory.  Watching for cheap used components on craigslist and online forums and ebay is prob the way to go.  Or watch for a free/deal on a broken system or whole used system/server.  Hint: a way to acquire too much older heavy junk is watch ebay for listings X miles from you marked pickup only or huge shipping costs...sometimes noone bids and its almost free.

---

### Post by electrogeist on 2009-01-27
A couple useful utilities for benchmarking are 

iperf to test network performance

bonnie++ is a more realistic drive test than hdparm.  It helps to test both huge file creation (several times your memory size to avoid caching) and a large number of small files of set size ranges - you can also run bonnie over an NFS mounted drive and compare to running it locally.  Some examples of usage (and results that will make you weep): [http://forums.2cpu.com/showthread.php?t=79364](http://forums.2cpu.com/showthread.php?t=79364)

---

### Post by volkswagner on 2009-01-27
Thanks for the info.

```
lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:13.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
```

You are correct, a lot on the bus.  Since the IDE interface is controlled here, I may just as well add the OS to the new controller, perhaps on its own disk.  

I have been picking up Seagate SATA refurbs cheap (only 40Gigs but at $15ea. it's hard not to get a handful when avail.).  Since it is not mission critical, no biggie on the risk of refurb.  I think I would benefit more with the faster disk and say good bye to that ten year old sure and steady sloth.  

I agree upgrades are hard to justify.  I considered $25 for the controller and possibly another $20-25 for an 800MHz PentIII.  That puts me at half the cost of an Intel Atom 330 board/cpu.  The CPU will not be afforded.  The $25 is worth the learning lesson to play with FreeNAS and Raid, etc.

The current PentII rig has sentimental value, since it was my first real PC.  I am still squeaking out the return of my original $650 paid at a PC fair in 1998. ;)  It uses ~35-40 Watts at the wall outlet, pretty green in my book if it is serving the purpose.  Obviously that will increase if I add to the HD count.

Got the drives today, and the controller is on the way from the Egg.  I just need to buckle down and tweak the replacement sever to free up the box (postfix woes).

---

