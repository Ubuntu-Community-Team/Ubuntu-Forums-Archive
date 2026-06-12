---
title: "Add device to RAID?"
date: 2010-01-16
forum: Server Platforms
---

### Post by knutz on 2010-01-16
Hi everybody!


I have three WD 1.5 GB harddrives. 2 of them already in a linear RAID also called Concatenated i think. (the same as JBOD).
Can i add the third drive to the RAID without losing data?

Update "Using mdadm software raid."

Thanks


knutz

---

### Post by Cheesemill on 2010-01-16
What do you mean by linear RAID?

If it's RAID0 or RAID1 then I don't think it's possible. It can be done with RAID5 although it's highly unlikely you have a 2 drive RAID5 setup.

---

### Post by knutz on 2010-01-16
> **Cheesemill said:**
> What do you mean by linear RAID?

If it's RAID0 or RAID1 then I don't think it's possible. It can be done with RAID5 although it's highly unlikely you have a 2 drive RAID5 setup.

You know. Like JBOD. Just in linux.

Is it possible to do?

---

### Post by Cheesemill on 2010-01-16
If it's JBOD then yes, it should be possible.
JBOD isn't technically RAID though.

How did you set up the original disks?

---

### Post by knutz on 2010-01-16
> **Cheesemill said:**
> If it's JBOD then yes, it should be possible.
JBOD isn't technically RAID though.

How did you set up the original disks?

Well yeah. But i think it should be possible. 
When i try adding them with the command:
```
sudo mdadm --manage --add /dev/md0 /dev/sdd1
```

It gives med the error:
```
mdadm: add new device failed for /dev/sdd1 as 2: Invalid argument
```

I created them with something like this:
```
mdadm --create --verbose /dev/md0 --level=linear --raid-devices=2 /dev/sdb1 /dev/sdc1
```


knutz

---

### Post by falconindy on 2010-01-16
I think your arguments are out of order. From the manpage:

```
mdadm [mode] <raiddevice> [options] <component-devices>
```
And you've got your <raiddevice> and [option] switched. Should be:
```
mdadm --manage /dev/md0 --add /dev/sdd1
```

edit: just tried this one a VM. This doesn't work. While the grow command **does** work, the newly allocated drive is used as a spare. The man page leads me to believe that linear arrays don't support growing of this type.

---

### Post by knutz on 2010-01-17
> **falconindy said:**
> I think your arguments are out of order. From the manpage:

```
mdadm [mode] <raiddevice> [options] <component-devices>
```
And you've got your <raiddevice> and [option] switched. Should be:
```
mdadm --manage /dev/md0 --add /dev/sdd1
```

edit: just tried this one a VM. This doesn't work. While the grow command **does** work, the newly allocated drive is used as a spare. The man page leads me to believe that linear arrays don't support growing of this type.

Well I did it!

What I did:

```
sudo mdadm --grow /dev/md0 /dev/sdd1

sudo e2fsck -fvp /dev/md0

sudo resize2fs /dev/md0
```

This added the device to the Linear array and then detected that the filesystem is to small and then I resized the filesystem to the entire array.
On the /dev/sdd1 I had already created a ext3 filesystem. I don't know if that has anything to say.

I hope this helps some other dude with this same problem.


knutz

---

### Post by falconindy on 2010-01-17
Yeah I completely forgot that you'd be able to grow the FS to fill the newly extended array. It came to me late last night and I meant to post here about it. Good job.

For future reference, you should run e2fsck on the array again after the resize operation when doing this manually.

---

