---
title: "Another &quot;lost 2 disks in a raid5&quot; thread"
date: 2008-12-12
forum: Server Platforms
---

### Post by shoe on 2008-12-12
Greetings all!

I have just finished a 4h session with Google and these here great forums finding out various ways of solving my problem.
However there is still something missing and I hope that someone is able to provide me with the information I need.


The thing is this: A few weeks ago I lost 2 of 7 disks in a RAID5 array. I was however able to restore it thanks to help from this thread [http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136)

What I did not get from the beginning was that the disks had to be specified in the exact same order as the first time I created the array. And at this point in time the disks were hosted in another server all together.

After I realized that I could find the "original order" by issuing an mdadm --examine on the disk I specified as "missing" I recreated the array. And it worked fine.

I recreated the array with the following command:
```
mdadm --create /dev/md0 --assume-clean --level=5 --verbose \
--raid-devices=7 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 missing \
/dev/sdg1 /dev/sdh1
```

But before I could add the last missing disk a few days later two disks lost connection again! It's probably the same disks, they're sitting on a bad SiI 3114 SATA2-card. I will replace it asap.


But to my new problem:

Now it seems I cannot find out the original order of my disks, since it now thinks the array was created with the above command. And the disk (sdf1) missing above tells a totally different story then the other disks :(

An --examine of all partitions except sdf1 gives,
```
   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       0        0        4      faulty removed
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1

```

And sdf1 gives,
```
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       0        0        3      faulty removed
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8       17        5      active sync   /dev/sdb1
   6     6       8       81        6      active sync   /dev/sdf1
```

Note two things, 1) this disk thinks it is sdc and 2) it also thinks sda is part of the raid. It's been ages since this was the case. And it was because my previous system probed the disks differently. sda1 today is my root partition.


So the burning question is - is there a way for me to find out what order I should specify the disks when recreating the raid with --assume-clean ??


Sorry for a lengthy post and thanks for your time,
/Stefan

---

### Post by fjgaude on 2008-12-12
Look, AFAIK, mdadm doesn't use drive names in assessing what drives go with which array. It uses the UUID created, which is the same for each drive in an array, to assemble an array.

The drive names can change all over the place and mdadm does not care.

A way to tell which drives are good or not is to rename the /etc/mdadm/mdadm.conf file or delete it, remove mdadm, reboot. Then re-install mdadm which will recreate a new mdadm.conf file and you are good to go, mount the good arrays.

Take a look at the mdadm.conf file and see that auto created ones do not have drive names, only the UUID of each array, which is what the -D command will show for each drive, as will the -E command.

---

### Post by shoe on 2008-12-12
Hi Frank thanks for your reply.

I really wish it's as simple as you describe it although I kind of doubt it. Will try it later today and report back.

Cheers,
/Stefan

---

### Post by shoe on 2008-12-13
> **fjgaude said:**
> Look, AFAIK, mdadm doesn't use drive names in assessing what drives go with which array. It uses the UUID created, which is the same for each drive in an array, to assemble an array.

Good morning,

I have read your post again and I am not sure we are talking about the same thing. I have to recreate my array, not just assemble it. My mdadm.conf does not contain any ARRAY statements (it did, but I commented it out since it was the old one which was wrong). I dont think reinstalling mdadm will go any difference, even if I recreate my mdadm.conf it will still contain the ARRAY statement and UUID of an array with the disks in the wrong order.

My understanding is that all mdadm.conf does is configure assemble and start the array at boot time. Without it all I have to do is mdadm --scan --assemble , and this will work just as fine.

Please correct me if I'm wrong here.

Thanks,
/Stefan

---

### Post by fjgaude on 2008-12-13
Well, something is not right here... the mdadm.conf file as created automatically doesn't have the drive names in it, just the UUID of the array which is the same for each drive, as shown with:

```
sudo mdadm -D /dev/md0
```

or 

```
sudo mdadm -E /dev/sd[nn]
```

Simply try what I've suggested and see what your .conf looks like. I've been doing this for many years and usually know what I'm talking about. <smile>

---

### Post by shoe on 2008-12-13
> **fjgaude said:**
> Well, something is not right here... the mdadm.conf file as created automatically doesn't have the drive names in it, just the UUID of the array which is the same for each drive, as shown with:

```
sudo mdadm -D /dev/md0
```

or 

```
sudo mdadm -E /dev/sd[nn]
```

Simply try what I've suggested and see what your .conf looks like. I've been doing this for many years and usually know what I'm talking about. <smile>

Hehe, I'm not questioning your logic. I'm just saying that I don't think that my problem is related to assembling the array, the problem is that I have to re-create it with the drives in the correct order as I once had when I originally created it. Before the two drives crashed.

But anyway, I am about to try what you said.

Thanks,
/Stefan

---

### Post by shoe on 2008-12-13
O.K. So here's what I did as per your suggestion.

```
aptitude remove mdadm
mv /etc/mdadm /etc/mdadm_old
```

reboot

```
aptitude install mdadm
```
This regenerated the mdadm.conf just as you said. However, as I suspected it put two ARRAY's in there with two different UUID's, both named md0. Which makes perfect sense since at the moment I actually have UUUU_UU disks which makes up my newly created md0 array (with disks in the wrong order!) And the old disk which I have kept as "missing" when creating the new arrays. I did this to keep what I thought was the correct order of the disks somewhere.

So still it's a no go. And since I have backups of the most important files I think I'm going to go with the new array and leave the old one to rest. Kind of sad cos I think or rather know that it can be created correctly since I did it before.

Anyway, thanks for your assistance. I appreciate it.

edit:
p.s. I too kind of know what I'm doing, been working as a Linux sysadmin for over 10 yrs (RHCE), although admittedly software raid is not my strongest side. <smile>
:)

Cheers,
/Stefan

---

### Post by fjgaude on 2008-12-14
I think there is something else wrong with your array... it has nothing to do with drive ordering... I've pulled drives out of one box and put them in another with the array assembling just fine.

With two UUIDs indicated in the .conf file such means that **mdadm** sees two sets of arrays made up of two sets of drives, each set having its unique UUID. That's the way it works.

Have fun with software raid.

---

