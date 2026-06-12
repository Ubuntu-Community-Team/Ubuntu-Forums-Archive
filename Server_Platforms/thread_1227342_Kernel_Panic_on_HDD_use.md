---
title: "Kernel Panic on HDD use"
date: 2009-07-30
forum: Server Platforms
---

### Post by vladk2k on 2009-07-30
Hi
I have an Ubuntu 9.04 server setup at home, which panics its kernel from time to time. Other than putting it to auto-reboot after 20s, I can't find any fix for it. Here's the setup:

3 HDDs (64, 78, 80 GiB) connected via Parallel ATA.
The 64 GiB HDD is split into 10 GiB (for /), 53 GiB (/media/volatile) and 512 MiB for Swap.
The 80 GiB has a 2 GiB swap partition in the beginning, and the rest (78 GiB) is used in a software RAID 1 array with the whole of the 78 GiB HDD (the array is mounted on /home).

The motherboard uses a VIA KM400 NB with a VIA VT8237 SB. Temperatures are normal, memory is OK.

I think I've somehow pinned it to a possible cause for the panic. Thing is, I have a backup script which dumps the first partition (/) with dd on the second partition. If all is successful, the image is moved to the RAID array for storage. Somewhere in this process (either the dump, or the moving of the image) something fails, causing the kernel to panic. This doesn't happen all the time, and sometimes it panics without the process taking place.

It's happened on 2.6.28-13 and 2.6.28-14 as well. No extra software is installed other than the basic Ubuntu Server with LAMP, DNS, DHCP and CUPS.

It might be worth mentioning that the 80 GiB HDD (the one with 2 GiB of swap in the front) has failed once with bad sectors in the first 1 GiB. The sectors were repaired with a tool from Hiren's Boot CD, and in order to avoid them, I've set up the swap partition. You might say that this is unsafe, but the server rarely uses swap space (it's a home server, used for file and printer sharing, remote access from work to local files etc.) and so I don't think that is the problem (the sectors were fixed, and I regularly scan for new bad sectors using badblocks. Also, its priority is -2, which (hopefully) means that it'll be used once the 512 MiB in the first HDD get filled up.

Here's a pic of the offending panic:
[[IMG]http://img24.imageshack.us/img24/4945/kernelpanicg.th.png[/IMG]](http://img24.imageshack.us/i/kernelpanicg.png/)

Feel free to ask me any questions.

LE: I just ran the script without problems - or so I thought!
During the dd phase I got an error (on the screen attached to the server, not through the ssh session):
```

ata1.0: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata1.00: cmd 35/00:00:d9:47:49/00:04:01:00:00/e0 tag 0 dma 524288 out
         res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
ata1.00: status: {DRDY}

```
After that was done (apparently without error) and the moving phase began, everything got stuck on ssh and now the server is outputting the following line every 65 or so seconds:
```

BUG: soft lockup - CPU#0 stuck for 61s! [mv:5593]

```
SSH doesn't work, the local terminal doesn't work (keyboard would light up even NumLock LED), but strangely it responds to pinging.

Even later edit
I've removed the said drive from the system and I get the same error.
However, prior to that, the system became unstable upon resyncing the RAID array with lots of **ata2.00** errors, some of which had ```
status: { DRDY ERR }
```. It even interfered with the normal shutdown procedure, which took considerably longer.
I think there might be something fishy about the motherboard - I hope it doesn't mean I have to scrap the PC.

---

### Post by vladk2k on 2009-07-31
wow, already on the second page...

**bump** for anyone who might know something

---

### Post by cariboo on 2009-07-31
Why are you running a single disk as a raid 1 array? I would suggest you change the raid 1 to jbod and see if that makes a difference.

---

### Post by vladk2k on 2009-07-31
Maybe I wasn't clear enough. I have the following partitions:
sda1, sda2, sda3, sdb1, sdc1, sdc2
sda1 is 10 GiB and holds /
sda2 is 53 GiB and holds "volatile" data
sda3 and sdc1 are swap space
sdb1 and sdc2 are the same size, and joined in a raid1 array, so that if one disk gets fubared, I don't lose the data

---

### Post by samosamo on 2009-07-31
You claim the "memory is OK."  How can you prove that?

Reason I ask is, every time I've come across a problem such as this, it was bad memory.

---

### Post by vladk2k on 2009-08-01
First, because I used the memory from my desktop computer (I upgraded it some time ago) and it's fairly new.
Second, because I ran memtest on it for a whole day without any problems encountered.

So far the problem seemt to have subsided, but I wonder for how long...

---

### Post by vladk2k on 2009-08-28
The problem lingers on. Today I've had about 2 lockups (ata something problem) and a panic, which I've managed to photograph. I've switched to framebuffer, so I've got a bit more info available:
[[IMG]http://img22.imageshack.us/img22/3670/dsc00570x.th.jpg[/IMG]](http://img22.imageshack.us/i/dsc00570x.jpg/)

Note: This panick happened while I was investigating /dev/sdc with badblocks -nsv. It had already gotten through more than 75% of the disk. I'm getting worried if this might not actually be a problem with the ATA controller rather than the disk itself.

---

### Post by hessiess on 2009-08-28
How old are the drives?

---

### Post by vladk2k on 2009-08-30
> **hessiess said:**
> How old are the drives?
Well, they're P-ATA, so they are quite old, but I would say not older than 5 years

---

