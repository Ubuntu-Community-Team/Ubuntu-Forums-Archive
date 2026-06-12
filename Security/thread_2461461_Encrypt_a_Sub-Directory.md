---
title: "Encrypt a Sub-Directory"
date: 2021-04-30
forum: Security
---

### Post by dddman on 2021-04-30
I wish to create a encrypted folder within my Home Directory for storage of text/pdf files.  I do this in Windows with Axcrypt (Free), but it is not Linux compatible.  So after a long google search I have come full circle back to the Ubuntu Community Wiki.

eCryptfs
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

This sounds like it will do the job.
Anyone have some thoughts or comments about this or other encryption products?

Thanks

---

### Post by dddman on 2021-05-01
I not so quickly determined a GUI was needed.

VeraCrypt was easy to install and setup, I'm liking it so far.

[ATTACH=CONFIG]288399[/ATTACH]

PS
Has a nice help section built into app

---

### Post by dddman on 2021-05-01
Hummm  No bites  VeraCrypt it is  Solved; no contest

---

### Post by TheFu on 2021-05-01
There are security considerations for any encryption that isn't the entire OS. That probably doesn't matter if you are trying to protect cat videos from family members, but if you work for an NGO or are a target by a real attacker, then please, please, use whole drive encryption as provided by default using LUKS in the Ubuntu installers.  Please.

---

### Post by dddman on 2021-05-01
Hello

My thinking is LUKS is not needed.  I could be wrong, but Ubuntu is a virtual system inside win10 which has full disk encryption.

VeraCrypt lets me leave Ubuntu open without worries of sensitive info laying around.

Is my thinking right?

---

### Post by TheFu on 2021-05-01
Encryption only protects data that cannot be accessed, while it is closed, unavailable, and at rest. Once unlocked, it is at risk.
When it comes to encryption, process details matter.

---

### Post by dddman on 2021-05-01
Yes, I hear what your saying.  My encryption tend to be open more than closed.

Right now all projects go on hold.  I broke it.  If I can't fix it, I'll have to "back the truck up" two days.  Thats my last snapshot :(

---

### Post by TheFu on 2021-05-02
Reinstalling is 10 minutes. 
Putting your data back from the last daily, automatic, versioned, backup should be 10-15 minutes.
Putting back the system configurations for any tools you've installed, might take 3-7 minutes.
Reinstalling any manually installed packages from the list you made BEFORE taking the versioned backups - 3 minutes.
Most of these things are really 1 minute to cause and the rest of the time waiting around.

30-45 min to restore a system so it "feels" like it did before, except it could be restored to completely new hardware, if needed.
What's the big deal?
I used to copy entire VM images as backups.  Then I was taught by an old, wise, gray-beard, to do daily, versioned backups instead. Backing up each system is basically the same whether it is a VM or a physical install. Takes 2 - 10 minutes each.
```
=== Time for Backups to regulus === 
StartTime 1619932504.00 (Sun May  2 01:15:04 2021)
EndTime 1619932621.95 (Sun May  2 01:17:01 2021)
ElapsedTime 117.95 (**1 minute 57.95 seconds**)
TotalDestinationSizeChange 3546286 (3.38 MB)


=== Time for Backups to hadar === 
StartTime 1619933705.00 (Sun May  2 01:35:05 2021)
EndTime 1619934209.52 (Sun May  2 01:43:29 2021)
ElapsedTime 504.52 (**8 minutes 24.52 seconds**)
TotalDestinationSizeChange 75838493 (72.3 MB)
```
Those run nightly. Not a big deal. What's really crazy is how little storage actually gets used since I don't backup the OS.

**Hadar** is a VM host running KVM. The daily backup summary for it:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May  2 01:35:05 2021         2.00 GB           2.00 GB   (current mirror)
Sat May  1 01:35:05 2021         64.6 MB           2.07 GB
Fri Apr 30 01:35:05 2021         96.9 MB           2.16 GB
...
Mon Jan  4 01:35:25 2021         70.6 MB           10.1 GB
Sun Jan  3 01:35:29 2021         59.3 MB           10.2 GB
Sat Jan  2 01:35:05 2021         49.6 MB           10.2 GB
```

Here's the real storage on the system:
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   17G   14G  54% /
/dev/sdb1                         ext2  720M  162M  522M  24% /boot
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  127G   38G  78% /var/lib/libvirt
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
```

10.2G to have ... 120 days of versioned backups?  Why wouldn't people do that?  
The libvirt and lxd areas are for VMs and LXD containers. Because each VM is backed up itself, I don't need to worry about either of those places. Basically, only specific parts of / get backed up - mainly settings, lists of programs - about 2G of stuff.
**Regulus** is a desktop Summary:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May  2 01:15:04 2021         5.92 GB           5.92 GB   (current mirror)
Sat May  1 01:15:04 2021         2.22 MB           5.92 GB
...
Tue Feb  2 01:15:04 2021         2.44 MB           7.35 GB
Mon Feb  1 01:15:03 2021         1.98 MB           7.35 GB
```
That's more typical for the storage needed - about 20-25% more storage for 90 days than the amount inside the initial backup area.  Because it isn't as high risk as hadar, I don't keep as many versioned backups.  No down-time for these backups, BTW.

In the last year, I've tested the regulus recovery twice.  I have new NVMe SSD for hadar - so that will use either the recovery method or ... I might just use LVM's **pvmove** command while the system keeps running.

Backups on Windows are so hard/big in comparison.

---

### Post by dddman on 2021-05-02
Wow, that's some serious backup.  I had to switch to xorg and then updated my snapshot.  Wayland has not been an issue until yesterday.  I really should do a nightly snapshot.  Automate the process.

I have 256G primary storage and a 256G SD card in my tablet that could be used to hold a clone.  I can boot from SD card, but this could be turned off in BIOS.

LXD container is something I have not tried.  Maybe I should.  Although I am quite happy with virtualbox.

LVMs are a interesting read.  Snapshot built in.

Things are coming together nicely in ubuntu, I don't think I will ever be able to stop tweaking it.  Its addicting

---

