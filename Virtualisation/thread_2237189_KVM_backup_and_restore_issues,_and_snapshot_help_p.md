---
title: "KVM backup and restore issues, and snapshot help please"
date: 2014-07-31
forum: Virtualisation
---

### Post by npinn001 on 2014-07-31
_**First Part**_

Ok, so I have a KVM install on top of Ubuntu 14.04 which i manage remotely with Virt-manager.

I set up a 40GB LVM partition for a windows VM, and isntalled Windows on it. I then turned it off, and used dd to make a copy (with compression using gzip) to another partition on the drive called say vm1.gz. I was able to restore this fine.

I then did a load of work on the windows VM, and decided to create another backup. So i turned it off and repeated the backup, but gave it another name, so say vm2.gz.

When I tried to restore this backup, I got errors that there was insufficent space, and I noticed that the restored backup was 43GB, not 40GB, so larger than the LVM partition. How could that be?

I then deleted the LVM partition of the VM, and set up a new one at 45GB size, and tried to restore my backup to that. It again failed due to lack of space.

Dont know whats going wrong here?

Feels like a compression error. Next time i might back up without compression.

_**Second Part**_

Surely there must be a better way to backup my setup. Snapshots seem like the key. On my desktop I use Virtualbox, and you just click snapshot and thats it. If it goes wrong, delete the snapshot.

Is there a similar function for KVM and how do I do this easily?

Thanks in advance

---

### Post by sudodus on 2014-07-31
I have done this kind of backup many times. It works. ***dd*** as well as ***gzip*** are very old and well debugged. In order to get a small compressed image, I overwrite unused disk space with zeroes before cloning with dd. It takes time, but makes a tremendous difference in size. ***Clonezilla*** can do this in a more efficient way, it copies only used blocks, so it is faster than  dd, and the compressed image size is as small as with dd after  overwriting unused disk space with zeroes.

I think you did something wrong, when you made the backup, or something else went wrong, disk error, memory error or something like that. Maybe you made the backup in a different way, for example made a backup of the whole virtual drive, not the partition, but tried to restore it as a partition. My experience is that backing up / cloning a whole drive is better than backing up partitions. From a Clonezilla image of a whole drive you can also select to restore only a partition (after some fiddling around).

-o-

You can do the backup both from 'the inside' backing up the partition as seen by the virtual machine, and from 'the outside' backing up the file, which contains the virtual disk, as seen by the host machine. Maybe you mixed those methods.

Anyway, I think VBox snapshots are operating 'the outside', and you can do something similar, but 40 GB is a lot of data, so unless you use some efficient way to skip virtual disk space that is not used, it will be rather slow.

-o-

Backing up Windows should be done either with Windows tools or by cloning with dd or Clonezilla. Backing up linux is much easier. It is actually enough to copy the files (and restore them) for example with rsync. On top of that you may need to restore grub, if it was also destroyed, for example by a disk crash, but it is easy with help from Ubuntu wiki pages, for example

 [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by npinn001 on 2014-07-31
Thankyou for the quick reply. I have the VM installed on one partition, so I backed up the whole partition. Do you mean I should backup the entire hdd? 

Next time I will use the windows drive imaging tool to save a clone, but I had hoped KVM would work for me. I just dont get how the restored image could be 3GB larger than the original? Weird!

---

### Post by sudodus on 2014-07-31
Did you do it from "the inside" or from "the outside"?

---

### Post by TheFu on 2014-07-31
sudodus nailed it.

I use windows backup to backup windows, but have used **fsarchive** and partimage which compress it as well. For data only stuff on Windows, I keep that data on Linux systems (network shares) and let Linux handle the backups smarter.

The problem I've seen with snapshots is that true backups become a 2-stage effort, since a snapshot needs to be pushed to a remote system after taken - backups on the same physical hdd aren't really backups.

Of course, with Linux backups we can be much smarter and only need to backup metadata about the install (easily recreated from a specific list of packages), settings and data. That saves about 4-6G per backup and can still be restored in 30 min or less. Plus incremental backups are tiny, so more versions can be retained.  I keep 120 days of backups for some high-risk systems like email gateways. That system doesn't have users or much data, just configuration and settings. Checked last week and all those backups are 26MB (yes, MB, not GB) for that VM.  How cool is that?

---

### Post by npinn001 on 2014-07-31
> **sudodus said:**
> Did you do it from "the inside" or from "the outside"?

I did all the backups from the outside. I thought by simply copying the partition that would be the quickest solution. I might try just unzipping it (although the confusing thing is it was an LVM partition that was assigned to storage for the VM).

I wonder if I can unzip it somehwere and then copy it over, so that I dont lose the work.

If not, I'll try again I guess!

---

### Post by npinn001 on 2014-07-31
Also, The vm was on an LVM partition. In my head I thought it was like virtualbox where it was a disk image you could just delete so I did:

sudo rm vm1     

and it did gdelete
I then realised it was a partition and did

sudo lvremove vm1

And it went through the normal delete process.

I wont have messed anything up will I to do with the partitions?

---

### Post by sudodus on 2014-07-31
> **npinn001 said:**
> I did all the backups from the outside. I thought by simply copying the partition that would be the quickest solution. I might try just unzipping it (although the confusing thing is it was an LVM partition that was assigned to storage for the VM).

I wonder if I can unzip it somehwere and then copy it over, so that I dont lose the work.

If not, I'll try again I guess!

Backing up up a drive (for example device /dev/sda) or partition (for example device /dev/sda5)

device --> dd --> gzip --> file

Restoring a compressed dd backup

file --> zcat --> dd --> device

Reversing the process should work properly, there should be ***no*** change in the size (40 GB --/--> 43 GB).

-o-

Did you use scripts or did you simply type in the commands from the keyboard? If you had (and have) scripts, please post them in a reply! Or if you remember what you did, please show the commands!

---

### Post by npinn001 on 2014-07-31
> **sudodus said:**
> Backing up up a drive (for example device /dev/sda) or partition (for example device /dev/sda5)

device --> dd --> gzip --> file

Restoring a compressed dd backup

file --> zcat --> dd --> device

Reversing the process should work properly, there should be ***no*** change in the size (40 GB --/--> 43 GB).

-o-

Did you use scripts or did you simply type in the commands from the keyboard? If you had (and have) scripts, please post them in a reply! Or if you remember what you did, please show the commands!

I just used commands as below:

dd if=/dev/vg_pool/vm1 | gzip -c | dd of=/backups/vm_backup.gz

And to restore it:

dd if=/backups/vm_backup.gz | gzip -c -d | dd of=/dev/vg_pool/vm1

Does that look ok?

---

### Post by sudodus on 2014-07-31
> **npinn001 said:**
> I just used commands as below:

dd if=/dev/vg_pool/vm1 | gzip -c | dd of=/backups/vm_backup.gz

And to restore it:

dd if=/backups/vm_backup.gz | gzip -c -d | dd of=/dev/vg_pool/vm1

Does that look ok?

I think one of your  dd commands in each line is just piping the data without changing anything (waste of effort)

```
dd if=/dev/vg_pool/vm1 | gzip -c  > /backups/vm_backup.gz
```

```
zcat /backups/vm_backup.gz | dd of=/dev/vg_pool/vm1
```

I don't see anything that would cause it to go wrong, only waste of effort, but it is very easy to make a typing error in such command lines, so it should be tested and after that kept in script files.

-o-

There is another problem that we have not discussed. It is very important that ***the target device, or any device within it is [COLOR=#ff0000]not[/COLOR] mounted*** to avoid things getting mixed up during backup and restore.

-o-

*Edit*: Maybe two calls of dd in the same command line can garble the data, but I don't know. Can someone else help us?

---

### Post by npinn001 on 2014-07-31
> **sudodus said:**
> I think one of your  dd commands in each line is just piping the data without changing anything (waste of effort)

```
dd if=/dev/vg_pool/vm1 | gzip -c  > /backups/vm_backup.gz
```

```
zcat /backups/vm_backup.gz | dd of=/dev/vg_pool/vm1
```

I don't see anything that would cause it to go wrong, only waste of effort, but it is very easy to make a typing error in such command lines, so it should be tested and after that kept in script files.

-o-

There is another problem that we have not discussed. It is very important that ***the target device, or any device within it is [COLOR=#ff0000]not[/COLOR] mounted*** to avoid things getting mixed up during backup and restore.

-o-

*Edit*: Maybe two calls of dd in the same command line can garble the data, but I don't know. Can someone else help us?

Honestly, I think you may have cracked it. I just checked back and I got my syntax from a guide online, however that was talking about backing up a snapshot rather than a mounted partition. 

When I set up an LVM partition I dont mount it, as I choose that as the target device for the VM using Virt manager. 

So its either that the partition is somehow classed as in use even though the VM is off, or the dd command twice is messing things up.

I'll try again tonight, by unmounting the LVM partition first. Hope I havent caused any serious corruption to the file system base (ubuntu) and that if I just delete the partitions and start over it will work!

Thankyou for your help, its a massive benefit that you've taken the time to respond to me, and I just wanted to make sure you know I appreciate the assistance.

---

### Post by npinn001 on 2014-07-31
> **sudodus said:**
> Did you use scripts or did you simply type in the commands from the keyboard? If you had (and have) scripts, please post them in a reply! Or if you remember what you did, please show the commands!

I'm sorry to ask, but a script sounds great but not done one before. For a simple backup script, I assume I could do:

```
#!/bin/bash
clear
nohup dd if=/dev/vg_pool/vm1 | gzip -c  > /backups/vm_backup.gz &
```

That ok?

---

### Post by sudodus on 2014-07-31
Is this in a Ubuntu server or Ubuntu desktop?

It would be OK, but at least in Ubuntu desktop I would simply make it

```

#!/bin/bash
dd if=/dev/vg_pool/vm1 | gzip -c  > /backups/vm_backup.gz

```

and run it ***with superuser privileges*** in a terminal window. So let's say you save the script with the name ***backup-vm1.bash***. Then you can run

```
sudo bash backup-vm1.bash
```

You can run (in another terminal window)

```
ps -A|grep " dd$"
``` to find the process ID (pid) of the dd process and kick on it to get an output of three lines showing how far it has reached,

Say that you find the pid 9495. Then kick on it with

```
sudo kill -USR1 9495
```

See ```
man dd
```

```
       Sending a USR1 signal to a running `dd' process makes it print I/O statistics to standard error
       and then resume copying.

              $ dd if=/dev/zero of=/dev/null& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

              18335302+0  records  in 18335302+0 records out 9387674624 bytes (9.4 GB) copied, 34.6279
              seconds, 271 MB/s

```

I would ***not*** kick on it and after one second kill the process as the example from the manual, but you might like to assign the variable **pid** and use it instead of using the ps command.

---

### Post by npinn001 on 2014-07-31
> **sudodus said:**
> Is this in a Ubuntu server or Ubuntu desktop?

It would be OK, but at least in Ubuntu desktop I would simply make it

```

#!/bin/bash
dd if=/dev/vg_pool/vm1 | gzip -c  > /backups/vm_backup.gz

```

and run it ***with superuser privileges*** in a terminal window. So let's say you save the script with the name ***backup-vm1.bash***. Then you can run

```
sudo bash backup-vm1.bash
```

You can run (in another terminal window)

```
ps -A|grep " dd$"
``` to find the process ID (pid) of the dd process and kick on it to get an output of three lines showing how far it has reached,

Say that you find the pid 9495. Then kick on it with

```
sudo kill -USR1 9495
```

See ```
man dd
```

```
       Sending a USR1 signal to a running `dd' process makes it print I/O statistics to standard error
       and then resume copying.

              $ dd if=/dev/zero of=/dev/null& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

              18335302+0  records  in 18335302+0 records out 9387674624 bytes (9.4 GB) copied, 34.6279
              seconds, 271 MB/s

```

I would ***not*** kick on it and after one second kill the process as the example from the manual, but you might like to assign the variable **pid** and use it instead of using the ps command.

Thanks - followed your advice and I got a lot more feedback on progress with those commands.

It still didnt work, think the archive is corrupted. I think I'm going to switch to qcow2 images instead as I can just move them around.

One question, I have a 250GB hard drive which has an LVM group on it with /root (say 20GB of the 250GB). I added the drive as storage/pool. I just tried to remove the pool using virt manager and it wont let me as the /root partition is in use. Is there a way to remove it, or am i stuck with it now as a storage pool?

---

### Post by sudodus on 2014-08-01
I haven't tried that, so I don't know.

I run KVM and virt-manager within one drive, except that I can connect devices, for example USB devices, and use them as devices in the virtual machine. I do that to test images. KVM is much better managing USB compared to VirtualBox. KVM can boot from USB pendrives without any problems. I may need to remove the configuration in virt-manager when the pendrive is removed.

You have better chances to get attention to this new problem, if you create ***a new thread with a good descriptive title*** in this same virtualisation forum.

---

