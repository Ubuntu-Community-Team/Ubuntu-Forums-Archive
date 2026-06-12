---
title: "[SOLVED] Can't reboot with faulty RAID-1"
date: 2008-11-10
forum: Server Platforms
---

### Post by dbyrne on 2008-11-10
I have four drives in my 7.10 server, with the first two (/dev/sd[ab]) running four raid arrays, and the second two (/dev/sd[cd]) running two more arrays. I have a failed RAID drive, which I've marked as failed, and removed from the array.

My problems:
1. I'm not sure which physical drive to remove, it's definitely on either SATA port 3 or 4: I assume that it's the one on the third SATA port, as its /dev/sdc - ideas ?
2. When I halt the system, disconnect either drive on port 3 or 4and try to reboot, it hangs at the point where it (I think) is assembling the RAID arrays. The message reads "Loading, please wait ...".

Details:

The last array on the first pair and the first one on the second pair are combined into an LVM volume group:

/dev/md0: /dev/sda1 + /dev/sdb1          /
/dev/md1: /dev/sda5 + /dev/sdb5          swap
/dev/md2: /dev/sda6 + /dev/sdb6          /home
/dev/md3: /dev/sda7 + /dev/sdb7  |__     data-vg
/dev/md4: /dev/sdc5 + /dev/sdd5  |
/dev/md5: /dev/sdc6 + /dev/sdd6          /backups

Now /dev/md5 has failed, and continually re-syncs. Errors in /var/log/messages show bad blocks on /dev/sdc6, so it looks like that disk is on its way out. It's a new disk, so it's going back for replacement.

Here's what I did:

```
$ sudo mdadm --fail /dev/md4 /dev/sdc5
$ mdadm --fail /dev/md5 /dev/sdc6
$ mdadm --remove /dev/md5 /dev/sdc6
mdadm: hot removed /dev/sdc6
$ mdadm --remove /dev/md4 /dev/sdc5
mdadm: hot removed /dev/sdc5
```

All looks OK:

```
$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md5 : active raid1 sdd6[1]
      683790528 blocks [2/1] [_U]

md4 : active raid1 sdd5[1]
      292969216 blocks [2/1] [_U]

md0 : active raid1 sda1[0] sdb1[1]
      9767424 blocks [2/2] [UU]

md1 : active raid1 sda5[0] sdb5[1]
      2923712 blocks [2/2] [UU]

md2 : active raid1 sda6[0] sdb6[1]
      292969216 blocks [2/2] [UU]

md3 : active raid1 sda7[0] sdb7[1]
      292969216 blocks [2/2] [UU]

unused devices: <none>
$
```

Any ideas really appreciated, as I need to get the faulty drive out of the server before the courier arrives to take it away on Wednesday !

---

### Post by fjgaude on 2008-11-11
You can find the SN of a physical drive using this:

```
sudo hdparm -i /dev/sd[nn]
```

and from there find the hardware that has that serial number.

---

### Post by dbyrne on 2008-11-11
Great tip, thanks Frank. Got the right drive first time.

I solved the other problem by rebuilding the arrays from scratch:

$ sudo mdadm --stop /dev/md4
$ mdadm --stop /dev/md5
$ mdadm --manage --create /dev/md4 --level=1 --raid-devices=2 /dev/sdc5 /dev/sdc5
$ mdadm --manage --create /dev/md4 --level=1 --raid-devices=2 /dev/sdc6 /dev/sdc6
$ mdadm --fail /dev/md4 /dev/sdc5
$ mdadm --fail /dev/md5 /dev/sdc6
$ mdadm --remove /dev/md5 /dev/sdc6
$ mdadm --remove /dev/md4 /dev/sdc5

Whatever the problem was before was now all fine. Pulled the drive, rebooted, both arrays running degraded successfully.

Case closed (no pun intended :))

---

### Post by fjgaude on 2008-11-12
Very good... now when you get a new drive you can add it back into the arrays.

Let us know how it goes.

---

### Post by dbyrne on 2008-11-20
To follow up, when the replacement drive arrived yesterday, I again halted the system, put the new drive in and connected it up, then restarted the system. The arrays came up degraded as expected.

I then:

[LIST]
[*]used *cfdisk* to partition */dev/sdc *exactly the same as the working RAID on */dev/sdd*
[*]stopped the daemons that were using /dev/md4 (mysql and apache)
[*]umounted the filesystems on */dev/md4* and */dev/md5*
[*]added the new drive partitions into the relevant RAID arrays (e.g. *mdadm --add /dev/md5 /dev/sdc6*)
[/LIST]

Once they had re-sync'd, a quick *mount -a* to remount everything, re-start mysql and apache and everything's back to normal :)

---

### Post by fjgaude on 2008-11-20
Wow, takes a lot of knowledge to do what you did successfully. Congratulations.

There are so many things that have to be known to handle all the issues that come up with software raid... sure wish there was a good book out to study, one covering most of the issues.

Happy that all worked out as you planned.

---

