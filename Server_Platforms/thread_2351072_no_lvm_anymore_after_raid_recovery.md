---
title: "no lvm anymore after raid recovery"
date: 2017-01-30
forum: Server Platforms
---

### Post by Schorschimact on 2017-01-30
Hi everybody,
I'm new here and need some expertise now. Hope you can give me a hint:

Since many years I have a local file server with 6 harddrives as raid 5 (with mdadm). On this raid is a lvm with many lvs. 
Yesterday, I accidentely unconnected two harddrive cables. The raid stopped immediately, as 4 out of 6 devices is too little for a raid 5.

I didn't figure out what is was immediately, so I rebooted a few times, as ubuntu tried to mount some devices I could only boot up in recovery mode.
When reconnected back the devices I tried mdadm --assemble and mdadm --assemble --force .... not working.

After googleing a while I tried mdadm --create ...
there was a message with a difference of more than 1%. I accepted and it started to recover. One disk was down.

it seems that was not such a good idea...

I cannot detect my lvm on the raid anymore. 

Even copying the metadata (dd if=/dev/md0 bs=512 count=255 skip=1 of=/tmp/vg.txt) does not offer me a config file as it should (only binary stuff till the end of the file)

I have a separate SSD keeping my OS so I can navigate currently, But I'm afraid to do something now. 

For me some light at the end of the tunnel it the fact, that even if I destroyed the raid by the mdadm --create, only the data on one disk should be bad. 

Any hits what I should do now?

Here are some details:

```

root@ubuntu-georg:/etc/lvm/backup# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdc2[0] sdd2[1] sde1[2] sdb1[6] sdg1[4] sdf1[3]
      7319720960 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      bitmap: 0/11 pages [0KB], 65536KB chunk

unused devices: <none>
root@ubuntu-georg:/etc/lvm/backup# pvscan
  PV /dev/sda3   VG ubuntu-georg-vg   lvm2 [118,50 GiB / 28,68 GiB free]
  Total: 1 [118,50 GiB] / in use: 1 [118,50 GiB] / in no VG: 0 [0   ]



```

---

### Post by darkod on 2017-01-31
You did mdadm --create without --assume-clean? Or with?

---

