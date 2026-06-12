---
title: "Missing swap after reboot"
date: 2015-12-23
forum: Server Platforms
---

### Post by ch6574 on 2015-12-23
Hi, my swap is missing after the system reboots!

```
root@server:~# free
             total       used       free     shared    buffers     cached
Mem:      16295404    2044796   14250608     190976       5936     995624
-/+ buffers/cache:    1043236   15252168
Swap:            0          0          0
```

If I manually type "swapon -a" it comes back.

```

root@server:~# swapon -s
root@server:~# swapon -a
root@server:~# swapon -s
Filename				Type		Size	Used	Priority
/dev/dm-1                              	partition	16775164	0	-1
root@server:~# free
             total       used       free     shared    buffers     cached
Mem:      16295404    2077336   14218068     186168       5940    1047492
-/+ buffers/cache:    1023904   15271500
Swap:     16775164          0   16775164
```

So I figure the underlying mount points are correct at boot time.

"lsblk" at boot:

```
sdc                                                                   
&#9500;&#9472;sdc1        crypto_L           68a9aabc-7b86-4f7b-a33f-0d1e152874f9 
&#9474; &#9492;&#9472;cswap     swap               dcde8777-35c8-48f1-8e3b-785200ea74a8 
```

and again after "swapon", only now the mount point is shown as [SWAP]

```
sdc                                                                               
&#9500;&#9472;sdc1        crypto_LUKS                    68a9aabc-7b86-4f7b-a33f-0d1e152874f9 
&#9474; &#9492;&#9472;cswap     swap                           dcde8777-35c8-48f1-8e3b-785200ea74a8 [SWAP]
```

and this is what is in fstab and crypttab (which mount up OK at boot - I get the password prompt for LUKS, which then unlocks OK).

```
root@server:~# grep swap /etc/fstab /etc/crypttab 
/etc/fstab:/dev/mapper/cswap                         none            swap    sw                0       0
/etc/crypttab:cswap UUID=68a9aabc-7b86-4f7b-a33f-0d1e152874f9 none swap,luks,timeout=10

```

So I'm at a bit of a loss as to why the swap doesn't mount unless I manually do it?

The only change I made recently was (1) I grew sdc1 from 8G to 16G, (2) I then grew the LUKS container to fill that new space, and (3) a "mkswap" on the now larger "/dev/mapper/cswap" device. The latter step #3 meant the swap itself got a new UUID, which I wonder is what is causing the issue?

**Edit: My problem was having swap defined in both fstab *and* GPT partion type, which caused problems for systemd mounting it twice and failing**

---

### Post by darkod on 2015-12-23
Yes, I think it should be the UUID issue. Whenever a partition gets a new UUID you have to modify it in fstab or in this case maybe crypttab since you are using encryption.

The swapon -a finds all swap partition and activates them I believe, so that command is not showing if auto mounting is good or bad. In fact it has to be bad otherwise swap would mount on boot.

PS. For future reference, the mkfs command accepts an option for you to specify which UUID to use when formatting. I'm sure mkswap accept something like that too. So, before formatting you can check "current UUID" and make the new UUID match. That would avoid the need to fix the UUID in all related config files.

mkswap man page: [http://linux.die.net/man/8/mkswap](http://linux.die.net/man/8/mkswap)

Command example: mkswap -U <uuid> /dev/etc...

---

### Post by MAFoElffen on 2015-12-23
Is your swap on the same disk or on another? Just thinking, depending on the disk and your system, the cypto might need more time on your system. Maybe in your fstab, if you adjust/tune your timeout to longer... You could verify this might be the problem by using dmesg and filtering to see if there was a timeout problem during boot on that...

Just an idea.

EDIT-- Unlike Darko, I could be wrong, but I think the UUID in fstab is correct, because -a uses the same UUID from the fstab in the remount. (but is not competing with other resources in that process). It looks like it is mounting eventually, but the device is not mounting during boot, because of a timeout problem. I sometime run into this same problem mounting older RAID towers, when it takes a bit to spin up 20 or so disks...

Correction-- Darko noticed that the UUID [COLOR=#ff0000]WAS[/COLOR] wrong. My bad. I missed that.

---

### Post by ch6574 on 2015-12-23
Thanks for the tips. I double checked the UUID values, and they all matched.

I figured I'd then check how swap is mounted, and I believe it's via systemd these days (???), which [uses the partition's type code]("http://www.freedesktop.org/software/systemd/man/systemd-gpt-auto-generator.html") (which I found was set to 83 - i.e. a regular Linux file system), along [with fstab]("http://www.freedesktop.org/software/systemd/man/systemd-fstab-generator.html").

So I blew it away, and created a new partition with type 82 (i.e. swap), put LUKS and did an mkswap on that, and rebooted and all was well.

```
root@server:~# sgdisk -p /dev/sdc
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2399B32C-C41E-44E6-824C-02D3998CF5E0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        33556479   16.0 GiB    8200  SWAP                             <-- this is now 82
   2        33556480      1953523711   915.5 GiB   8300  
```

Then after it came back up, I could see the swap was mounted automatically, and was active in systemd:

```
root@server:~# systemctl --type swap
UNIT                  LOAD   ACTIVE SUB    DESCRIPTION
dev-mapper-cswap.swap loaded active active /dev/mapper/cswap

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.

1 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
```

---

### Post by darkod on 2015-12-23
Ah, ok. Depending how you created the partition, some tools make it 83 by default. I usually prefer parted which doesn't do 82 or 83, it simply creates a partition. You do your own filesystem afterwards...

---

### Post by ch6574 on 2015-12-24
Just thought I'd close out this thread as I believe the root of my problem was having a GPT partition defined as swap (type 82) **and** having an entry in /etc/fstab for ultimately the same device. Systemd tried to mount it twice, which failed the second time (as the partition itself isn't swap, it's housing a LUKS container), so I believe it's only valid to have either one or the other (I saw errors in the systemd journal about swap dependency issues).

I decided to stick with the fstab approach as it is what I know best (and I think the only way today for encrypted swap). So first I set the GPT partition back to regular filesystem type 83.

```
root@server:~# sgdisk --typecode=1:8300 /dev/sdc
```

Rebooted. Everything now reliably comes up.

Then checked the swap status, which says /dev/mapper/cswap is active (good, this is my LUKS container sitting on the above - now regular - partition).

```
root@server:~# systemctl --type swap
UNIT                  LOAD   ACTIVE SUB    DESCRIPTION
dev-mapper-cswap.swap loaded active active /dev/mapper/cswap

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.

1 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
```

And for confirmation of where this came from, I look at the status of the above swap systemd unit

```
root@server:~# systemctl status dev-mapper-cswap.swap
&#9679; dev-mapper-cswap.swap - /dev/mapper/cswap
   Loaded: loaded (/etc/fstab)
   Active: active since Thu 2015-12-24 08:55:12 EST; 29s ago
     What: /dev/mapper/cswap
     Docs: man:fstab(5)
           man:systemd-fstab-generator(8)
  Process: 1290 ExecActivate=/sbin/swapon -o sw /dev/mapper/cswap (code=exited, status=0/SUCCESS)
```

Which shows it was loaded from /etc/fstab.

Hopefully this might be of use to someone else in future!

---

