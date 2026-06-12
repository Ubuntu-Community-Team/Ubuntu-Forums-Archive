---
title: "Mdadm raid 5 help"
date: 2009-11-21
forum: Server Platforms
---

### Post by santhony on 2009-11-21
Just when you think you have it all going pretty good.....

Frank -- Pls help...

My System:

Ubuntu Karmic64 with all latest patches and updates
Mdadm Raid 5 set 7x500.

I do have a week old backup of ALL files on my RAID 5 set.


I'm not sure what exactly happened, or why it happened.. But, my 7x500 Raid5 all of a sudden will not assemble.

In order to not muddy up this thread.. I'm attaching three files of

1. mdadm -E /dev/sd[abdefgh]1
2. system mail messages in reguards to mdadm
3. mdadm fdisk

The Disk Utility sees everything as fine..

Could I have actually lost all 3 drives at once??

---

### Post by fjgaude on 2009-11-21
What does this show:

```
sudo mdadm -D /dev/md0
```

or whatever your array is named.

And what does /etc/mdadm/mdadm.conf show for the UUID of the array?

From your post you could actually have two failed drives... we will have to find out.

---

### Post by santhony on 2009-11-22
Thanks for taking a look ...  

You have it right, my raid array is the default /dev/md0.

santhony@ubuntu:~$ sudo mdadm -D /dev/md0
[sudo] password for santhony: 
mdadm: md device /dev/md0 does not appear to be active.
santhony@ubuntu:~$ 

attached is my mdadm.conf file.

This probably doesn't mean much, but the new Disk Utility in Karmic Palimpsest shows all the drives ok and intact for the raid.. 

Earlier this week, I did fail out one of the drives because of errors on it, and had it up and running several days with several reboots, no issues at all...


I've never lost a Raid 5 set before, either using Windows or MDADM in the past 10 years..

My heart is set on recovering this...just for peace of mind to know that it is that resilient.

My primary stations at home are all running Ubuntu.. No more windows for me and definitely not looking back...  I do have a PVR set, Snapstream that is my household media server, both live tv and movies...  I'm on the verge of rolling that over to MythTV, after perfecting it the past month.
That system has another set of 5 Terabytes of movies, that I want to incorporate.. somehow into my file server..

I'm getting ready to re-engineer a new raid set... fewer disks... I'm not set on the configuration tho... 

Any good tips or tricks/suggestions are greatly appreciated.


Thanks as always!

---

### Post by fjgaude on 2009-11-22
Well, the UUID in the mdadm.conf file is the same as it is in the -E results for one of your drives, so... you might have had two drives fail. Thus you are screwed and will have to re-create a new array and use your backup data to start over.

I tell you, with them huge drives I'd consider raid6 or just raid1 or 10. Haven't given it much thought though. I don't do movies!

Good luck!

---

### Post by laluz on 2009-11-23
#reassemble raid
sudo mdadm --assemble --force /dev/md0 --uuid=use_your_uuid_from_config /dev/sd{a,b,c,d,e}1 #put here your disk names   
sudo mdadm --query --detail /dev/md0
sudo fsck.jfs -v /dev/md0 # use here what is appropriate for your filesystem
sudo mount /dev/md0
sudo watch cat /proc/mdstat

when you have your array back (even if you have to start again from scratch)
#add internal bitmap to reduce rebuild time
sudo mdadm --grow --bitmap=internal /dev/md0

---

### Post by laluz on 2009-11-23
also check this message 
[http://ubuntuforums.org/showpost.php?p=8060525&postcount=16](http://ubuntuforums.org/showpost.php?p=8060525&postcount=16)

---

### Post by santhony on 2009-11-24
Great!!!

Laluz... This worked like a charm!!!!!

Thank You sooo much..

Frank - now we have another tool in the box..
Thanks for all your help.

Just to reiterate what I did.  

Here's the command I used for Laluz's recommendation:
sudo mdadm --assemble --force /dev/md0 --uuid=use_your_uuid_from_config /dev/sd{a,b,c,d,e}1 #put here your disk names.

I had to put my drive order in place of "/dev/sd{a,b,c,d,e}1, my drive order is /dev/sdf1 /dev/sde1 /dev/sdg1 /dev/sdh1 /dev/sdb1 /dev/sdd1 /dev/sda1

Here's what I typed in the console.

sudo mdadm --assemble --force /dev/md0 --uuid=67350c39:89f0ac91:0f5b4e61:2c17f314 /dev/sdf1 /dev/sde1 /dev/sdg1 /dev/sdh1 /dev/sdb1 /dev/sdd1 /dev/sda1



santhony@ubuntu:~$ sudo mdadm --assemble --force /dev/md0 --uuid=67350c39:89f0ac91:0f5b4e61:2c17f314 /dev/sdf1 /dev/sde1 /dev/sdg1 /dev/sdh1 /dev/sdb1 /dev/sdd1 /dev/sda1
[sudo] password for santhony: 
mdadm: forcing event count in /dev/sdf1(0) from 2395551 upto 2395554
mdadm: forcing event count in /dev/sde1(1) from 2395551 upto 2395554
mdadm: /dev/md0 has been started with 6 drives (out of 7).

My set is now resyncing to add the 7th drive... I'll let it settle down and finish before I do anything else..

---

### Post by fjgaude on 2009-11-24
We're thankful you got everything up and running again. I think the --force is likely what permitted the array to assemble again. As stated many times, mdadm uses the UUID of the array, which is in the superblock of each drive of the array, to assemble.
So be it.

---

### Post by santhony on 2009-11-25
All is great and happy again.

Thanks Eveyone.

---

### Post by laluz on 2009-11-27
> **santhony said:**
> Great!!!

Laluz... This worked like a charm!!!!!

Thank You sooo much..

I had to put my drive order in place of "/dev/sd{a,b,c,d,e}1, my drive order is /dev/sdf1 /dev/sde1 /dev/sdg1 /dev/sdh1 /dev/sdb1 /dev/sdd1 /dev/sda1

Here's what I typed in the console.

sudo mdadm --assemble --force /dev/md0 --uuid=67350c39:89f0ac91:0f5b4e61:2c17f314 /dev/sdf1 /dev/sde1 /dev/sdg1 /dev/sdh1 /dev/sdb1 /dev/sdd1 /dev/sda1


First of all, you are welcome :-)

Here is how your command could be also written:

sudo mdadm --assemble --force /dev/md0 --uuid=67350c39:89f0ac91:0f5b4e61:2c17f314 /dev/sd{a,b,d,e,f,g,h}1

it is called shell expansion, I believe.

---

