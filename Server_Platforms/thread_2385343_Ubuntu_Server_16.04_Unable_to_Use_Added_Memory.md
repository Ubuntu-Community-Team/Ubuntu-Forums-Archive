---
title: "Ubuntu Server 16.04 Unable to Use Added Memory"
date: 2018-02-19
forum: Server Platforms
---

### Post by thufirhawat2 on 2018-02-19
I have an Ubuntu Server that formerly had 2X512MB sticks, and 1X2GB stick and ran that way for about a week. I had previously ran a 14.04 server for about 3 years with that same hardware, but I completely formatted the drives and started over with 16.04 because doing a release upgrade crashed the system every time. 

Someone gave me a bunch of compatible 2GB sticks the other day, so I figured I would throw them in my server box so I could spin up some additional VMs on it. Upon booting back up, the free -h command reported only 3.2GB available, but as I have 4 slots each with 2GB sticks, this should 8GB available. Here is the pertinent info:

uname -a command output:
```
Linux VHOST 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

This should mean I am 64 bit as I understand it.

free -h command output:
```
              total        used        free      shared  buff/cache   available
Mem:           3.2G        952M        1.5G        9.9M        732M        2.0G
Swap:          2.8G          0B        2.8G

```

sudo lshw -short | grep 'System\ Memory' command output:
```
/0/24                      memory         8GiB System Memory
```

sudo lshw | grep -A 8 bank command output:
```
*-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: Kingston
             physical id: 0
             serial: 23289683
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: Kingston
             physical id: 1
             serial: 2533333A
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: Kingston
             physical id: 2
             serial: C0CC155A
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: Kingston
             physical id: 3
             serial: 25333B3A
             slot: DIMM4
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
```

This presumably means the OS is aware of exactly what is actually in the machine as reported by BIOS, correct?

sudo dmesg | grep -i memory command output:
```
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Early memory node ranges
[    0.000000] Reserving Intel graphics stolen memory at 0xcf800000-0xcfffffff
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] Memory: 3287012K/3396788K available (8499K kernel code, 1309K rwdata, 3988K rodata, 1508K init, 1316K bss, 109776K reserved, 0K cma-reserved)
[    0.014653] Initializing cgroup subsys memory
[    0.015158] Freeing SMP alternatives memory: 32K
[    0.832563] Freeing initrd memory: 37088K
[    0.832791] Scanning for low memory corruption every 60 seconds
[    0.849609] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.752876] Freeing unused kernel memory: 1508K
[    1.756533] Freeing unused kernel memory: 1728K
[    1.758323] Freeing unused kernel memory: 108K
[    2.093724] [drm] Memory usable by graphics device = 512M
```

I feel like the answer may lie in this output, but I am not quite savvy enough to feel confident that I am fully grokking what this is telling me, which is why I am asking you smart people!

And one last thing as far as info is concerned; I do use Logwatch on this server, and this morning's report contained this somewhat disconcerting tidbit that may be relevant: 

```
--------------------- Kernel Begin ------------------------


 4 Time(s): *BAD*gran_size: 128K        chunk_size: 2G  num_reg: 8      lose cover RAM: -1G
 4 Time(s): *BAD*gran_size: 128K        chunk_size: 512M        num_reg: 8      lose cover RAM: -256M
 4 Time(s): *BAD*gran_size: 1M  chunk_size: 2G  num_reg: 8      lose cover RAM: -1G
 4 Time(s): *BAD*gran_size: 1M  chunk_size: 512M        num_reg: 8      lose cover RAM: -256M
 4 Time(s): *BAD*gran_size: 256K        chunk_size: 2G  num_reg: 8      lose cover RAM: -1G
 4 Time(s): *BAD*gran_size: 256K        chunk_size: 512M        num_reg: 8      lose cover RAM: -256M
 4 Time(s): *BAD*gran_size: 2M  chunk_size: 512M        num_reg: 8      lose cover RAM: -255M
 4 Time(s): *BAD*gran_size: 4M  chunk_size: 512M        num_reg: 8      lose cover RAM: -253M
 4 Time(s): *BAD*gran_size: 512K        chunk_size: 2G  num_reg: 8      lose cover RAM: -1G
 4 Time(s): *BAD*gran_size: 512K        chunk_size: 512M        num_reg: 8      lose cover RAM: -256M
 4 Time(s): *BAD*gran_size: 64K         chunk_size: 2G  num_reg: 8      lose cover RAM: -1G
 4 Time(s): *BAD*gran_size: 64K         chunk_size: 512M        num_reg: 8      lose cover RAM: -256M
```

But once again, in trying to understand this, I am a bit out of my depth, and would greatly appreciate some help!

[SIZE=4][B]What I have tried to fix it:
[SIZE=1][/SIZE][/B][SIZE=1]
[SIZE=2]So far, I have tried the obvious stuff: 

-I have rebooted several times.

- I entered BIOS and looked at every single option, but found no memory cap option, or any option that looked like it had to be set differently in order to report added memory to the OS. The options are very basic as it is an old dell vostro desktop from 2006/2007.

-Even though the commands I ran seem to show that the OS can see the memory hardware just fine, I tried re-seating the memory sticks, but nothing changed.

Any help/suggestions would be much appreciated, sorry for the length of the post, but wanted to make sure everyone had all the info I could think to give![/SIZE][/SIZE][/SIZE]

---

### Post by TheFu on 2018-02-19
Please use normal fonts. Other fonts, beyond a few words for emphasis, are distractions.

At boot, you should be able to choose memtest. Run that for 12+ hrs. Any issues?
Not all RAM is compatible with all MBs.  Mixing RAM from different batches can cause issues too.  I've been burned a few times adding new RAM that didn't completely replace old stuff.

---

### Post by thufirhawat2 on 2018-02-19
> **TheFu said:**
> Please use normal fonts. Other fonts, beyond a few words for emphasis, are distractions.

At boot, you should be able to choose memtest. Run that for 12+ hrs. Any issues?
Not all RAM is compatible with all MBs.  Mixing RAM from different batches can cause issues too.  I've been burned a few times adding new RAM that didn't completely replace old stuff.

Hmm, the memtest is a good idea, I forgot that existed. I will try to run that overnight tonight I guess.

The memory all came from a single machine that is identical to the one I am using, and seemed to work fine in it, and is all of the same make, so I would have a hard time believing it is a compatibility issue. But I guess I have seen stranger things in 11 years of IT!

---

### Post by thufirhawat2 on 2018-02-20
Alrighty, so last night I tried defaulting the BIOS just in case, and that did not seem to do anything, so I left the memtest running overnight. I apparently cannot insert images into posts on this forum, but I let it run for 12 hours and 1 minute.

"Under Memory SPD Informations" it lists each memory slot in the machine and accurately reports the make/type/size of each stick of RAM I have in there. It passed 11 tests over the night, and reported 0 errors. I have never really used Imgur before, but here is a link I uploaded a screenshot of the memtest results that I am hoping works just in case I am missing something, because I can't honestly say I fully understand the results. 

So does anyone else have any ideas or suggestions? Thanks again!

[https://imgur.com/jWtCDQP](https://imgur.com/jWtCDQP)

---

### Post by TheFu on 2018-02-20
So you are mixing 666 and 800 DDR2 RAM?  The tests don't appears to see that as an issue. Interesting.  I'd move on and look elsewhere.
Showing only the logs with 'ram' in the line left off the lines just before and after, which are probably just as important.  Any mention of MTRR nearby?  Showing a few lines above and below logs would be helpful.

Is the system completely updated? Currently patched?  Did a little research (google) [https://www.linuxquestions.org/questions/linux-kernel-70/what-is-mtrr-cleanup-spare-reg-num-about-814410/](https://www.linuxquestions.org/questions/linux-kernel-70/what-is-mtrr-cleanup-spare-reg-num-about-814410/)
and
[https://velenux.wordpress.com/2014/01/02/badgran_size-in-dmesg/](https://velenux.wordpress.com/2014/01/02/badgran_size-in-dmesg/)

---

### Post by LHammonds on 2018-02-20
To bypass any installed OS issues, try booting with a LiveCD to see if you get different results from the "free" command.

If you get different results, it is likely something in the configuration of the system but it is VERY odd that anything you do normally would limit the amount of RAM available in the system.

If you installed 32-bit server, it will never see anything above 3GB.  But your output from the 1st post looks like the 64-bit version to me.

Here is the output of mine that is 64-bit:
```
Linux srv-smellyturd 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Since I see x86_64 in mine and yours as well that means you are also using 64-bit version.  And since you are running the 4.4.0-112 kernel, you have also done the apt-get upgrade command too so you should be current with your patches.

LHammonds

---

### Post by thufirhawat2 on 2018-02-20
> **TheFu said:**
> So you are mixing 666 and 800 DDR2 RAM?  The tests don't appears to see that as an issue. Interesting.  I'd move on and look elsewhere.
Showing only the logs with 'ram' in the line left off the lines just before and after, which are probably just as important.  Any mention of MTRR nearby?  Showing a few lines above and below logs would be helpful.

Is the system completely updated? Currently patched?  Did a little research (google) [https://www.linuxquestions.org/questions/linux-kernel-70/what-is-mtrr-cleanup-spare-reg-num-about-814410/](https://www.linuxquestions.org/questions/linux-kernel-70/what-is-mtrr-cleanup-spare-reg-num-about-814410/)
and
[https://velenux.wordpress.com/2014/01/02/badgran_size-in-dmesg/](https://velenux.wordpress.com/2014/01/02/badgran_size-in-dmesg/)

I had not had my coffee when I looked at the results so I didn't even notice that, but that is interesting, it is showing some as 666 and some as 800 in the memtest. The really weird thing is that the sudo lshw | grep -A 8 bank command showed all 666mhz if you look at its output in my original post.

Here is the output I get from the cat /proc/mtrr command:

reg00: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg01: base=0x200000000 ( 8192MB), size=  512MB, count=1: write-back
reg02: base=0x220000000 ( 8704MB), size=  256MB, count=1: write-back
reg03: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg04: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg05: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg06: base=0x0cf700000 ( 3319MB), size=    1MB, count=1: uncachable
reg07: base=0x0cf800000 ( 3320MB), size=    8MB, count=1: uncachable 

The BIOS version is 1.0.3, and it looks like there is a 1.0.15 version listed on Dell's website for the vostro 200, but the one they have shown doesn't look like mine, so I am going to have to get the service tag number from it when I get home and try to make certain that I am getting the right downloads page.

Funnily, after searching for an update, one of the first things I got was this link: [https://ubuntuforums.org/showthread.php?t=1317269](https://ubuntuforums.org/showthread.php?t=1317269) 

So it looks like if I do need to update BIOS, it is going to be a bit of a nightmare.

[https://velenux.wordpress.com/2014/01/02/badgran_size-in-dmesg/](https://velenux.wordpress.com/2014/01/02/badgran_size-in-dmesg/) - This article looked like it could be promising, but I am not super confident about modifying my GRUB configuration, that makes me a little nervous! 

I guess my best bet is to try to verify BIOS is truly updated, then consider modifying my grub config. Might try to see if I can find some more sticks of RAm from this old machine and try to get all 666mhz just in case as well!

---

### Post by TheFu on 2018-02-20
> **LHammonds said:**
> ... 
If you installed 32-bit server, it will never see anything above 3GB. ...

Before PAE, that was true.
Things are different.
[https://unix.stackexchange.com/questions/12054/what-is-the-difference-between-32-bit-pae-and-64-bit-kernels](https://unix.stackexchange.com/questions/12054/what-is-the-difference-between-32-bit-pae-and-64-bit-kernels)
and 
[https://askubuntu.com/questions/60155/does-32-bit-pae-with-more-than-4gb-ram-improve-speed](https://askubuntu.com/questions/60155/does-32-bit-pae-with-more-than-4gb-ram-improve-speed)

Though it doesn't matter here with a 64-bit kernel.

A system with 4G or more RAM, having a 64-bit OS install is the easy, standard answer, today. It wasn't always so clear when many programs weren't ported to 64-bit versions. WINE was known to have issues with 64-bit anything for a long time. I don't know the status for WINE anymore.

---

### Post by thufirhawat2 on 2018-02-21
Well, I managed to get some more 800 RAM from the old box I was re-purposing parts from, and I got all 4 2GB 800mhz sticks in the server, then updated the BIOS after I got the DELL service tag and verified I was looking at the right thing. 

I wish I would have had time to do one at a time and see which thing fixed it, but my wife was working in the office, and I was going to get the boot if I stayed in there too long, so I just did both at the same time! 

All is now working as expected. For anyone else having a similar problem, I keep a windows 7 HDD loaded just to boot to and flash BIOS since most manufacturers make the windows exe files. It makes me feel dirty to have to use Microsfot products, but we do what we must! 

Thanks TheFu and everyone else who helped me talk myself through it!

---

