---
title: "Gradually decreasing performance"
date: 2009-04-18
forum: System76 Support
---

### Post by glacialfury on 2009-04-18
[SOLVED]: Apparently the culprit was excessive IOWait cpu usage due to Transmission.

I'm running Ubuntu Intrepid on a serp4.  I've had the laptop for a year now, and in the context of experimenting with Linux I've installed and uninstalled many things, changed configuration files I didn't understand (rarely), and I've started to notice a decrease in performance.  This is particularly the case with loading applications, especially Firefox.

I know that Linux does not need to be defragmented.  I would love any advice though on where one starts to look for performance degradation in a Linux system.  What are the usual culprits?  What are the usual remedies?  How can I objectively gauge performance?

---

### Post by Lee_Machine on 2009-04-18
Here is a good place to start.

[http://www.chinwong.com/index.php?/site/comments/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php?/site/comments/ubuntu_speed_up_tips/)

I usually go into Synaptic and clean out the broken, orphaned packages. 

In Januty there is a new program called computer janitor that does this.

---

### Post by leandromartinez98 on 2009-04-18
The most likely reason for degrading performance is to be running
services that you don't need. You can check your

System -> Preferences -> Startup applications 

(this last was called Sessions before, I think)

To see if there is something that you do not use and is being started.

You may be starting services on boot that you don't need. I don't
know if there is a GUI for administering that.

If the performance seems severely degraded, you may have a software
problem. Try the "top" command, and see if, when doing "nothing", there
is some applications taking up your cpu significantly.

---

### Post by eyecreate on 2009-04-18
also, if you have installed alot of extensions in Firefox, it tends to be slower too. I've also experimented with Swiftfox, which is firefox optimized for linux and for your processor, and I've seen firefox become a bit snappier in such cases.([http://getswiftfox.com/](http://getswiftfox.com/) ) I've also messed around with preload on my user to load things before hand into memory on boot.(a little complicated if you are not familiar with terminal access)

---

### Post by TheBuzzSaw on 2009-04-18
My machines lose performance speed regardless of hardware or operating system (though Windows XP suffers worse than Ubuntu by a long shot).

I just make it a point to reinstall everything fresh every 6 months to a year. Personally, I find joy in redoing everything (and backing stuff up is easy with an external hard drive), but I can see how it would be a hassle for normal users.

---

### Post by val67 on 2009-04-18
Installing everything every 6 mths is not feasible for the vast majority of us.

Too bad s76 does not sell the 3 yrs (Long time support) Ubuntu releases with the new machines.

---

### Post by Supersquirrel on 2009-04-18
Believe it or not EXT3 does suffer fragmentation over time. So that could be a reason.

---

### Post by Mulenmar on 2009-04-18
> **Supersquirrel said:**
> Believe it or not EXT3 does suffer fragmentation over time. So that could be a reason.

I've never seen that, since I'm very much a distro-hopper, but I've heard that before. In anycase, it's far, far less than any of the Microsoft filesystems (FAT12, FAT16, FAT32, NTFS) I've used.

Ubuntu Jaunty has ext4, which has a defragmentation tool, either done or on the way.

---

### Post by thomasaaron on 2009-04-20
> Ubuntu Jaunty has ext4, which has a defragmentation tool, either done or on the way.

If you do a fresh install of Jaunty, you can manually partition and set up ext4. By default, though, it is ext3. 

They've pushed ext4 out to the next version of Ubuntu (karmic koala?).


Also, I'd have a look at what process are running when your machine is going slow. I've upgraded through two or three versions with no slowdown caused by file-system fragmentation. But, I'm sure it is possible.

---

### Post by 3Miro on 2009-04-20
Every file system fragments, it is physically impossible to make it otherwise.

Unix systems are set up so that every 30 reboots they perform a system check which is equivalent to defragmentation (and is much faster than on windows). So effectively, the systems fragments and defragments, but you don't have to worry about it.

For a slow down, check processes + services + info from top. Possibly clean the fans and such (the computer might be dusty and somewhat overheating). Check the installed programs to see if you don't use some, then remove them.

---

### Post by jdb on 2009-04-20
> **3Miro said:**
> Every file system fragments, it is physically impossible to make it otherwise.

Unix systems are set up so that every 30 reboots they perform a system check which is equivalent to defragmentation (and is much faster than on windows). So effectively, the systems fragments and defragments, but you don't have to worry about it.

For a slow down, check processes + services + info from top. Possibly clean the fans and such (the computer might be dusty and somewhat overheating). Check the installed programs to see if you don't use some, then remove them.

The system check does not do defragmenting.

jdb

---

### Post by 3Miro on 2009-04-20
> **jdb said:**
> The system check does not do defragmenting.

jdb

So how do you defragment? I don't think it is possible not to fragment.

---

### Post by jdb on 2009-04-20
> **3Miro said:**
> So how do you defragment? I don't think it is possible not to fragment.

Before you do any of the steps below make sure you completely understand each step.
This could completely blow your system away if you make a mistake.


The best way is to boot to another partition or a live CD.

Mount the partition in question, eg:

sudo mount /dev/sda1 /mnt

Mount something to back it up on, maybe a USB:

sudo mkdir /back
sudo mount /dev/sdb1 /back

Make a tar backup:

cd /mnt
sudo tar czf /back/mybackup.tgz .

Unmount the partition in question:

sudo umount /mnt

reformat the partition in question, eg:
THIS WILL COMPLETELY & IRREVOCABLY ERASE THE PARTITION

sudo mkfs.ext3 /dev/sda1

Remount the partition:

sudo mount /dev/sda1 /mnt

Restore it from backup:

cd /mnt
sudo tar xf /back/mybackup.tgz

The partition now has no fragmentation & you have a backup.

jdb

---

### Post by 3Miro on 2009-04-20
So the only way to defragment is to overwrite everything?

Basically the steps involve: save everything (and that means absolutely all files). Reformat the partition and then restore all the files.

I don't have a need to do it, but this is puzzling. I will have to do some reading on the subject.

---

### Post by jdb on 2009-04-20
> **3Miro said:**
> So the only way to defragment is to overwrite everything?

Basically the steps involve: save everything (and that means absolutely all files). Reformat the partition and then restore all the files.

I don't have a need to do it, but this is puzzling. I will have to do some reading on the subject.

That's the method that's been used since the early days of Unix.

With an ext2 or ext3 partition new files are scattered all over the disk so they have plenty of room to grow, that's why you don't get much fragmentation in Linux.

With windows they are jammed together and when they need to grow the new stuff has to go somewhere else on the disk, that's why fragmentation is such a problem with windows.

Edit: An additional thought.  If I remember correctly, windows defragmenting takes a while.
Backing up, reformating & restoring is a lot faster.

jdb

---

### Post by Supersquirrel on 2009-04-20
NTFS fragments because there is no block groups like most linux filesystems. In NTFS there is the MFT and than free space. In ext3 there is 128MB block groups seperated by Inodes.

---

### Post by jdb on 2009-04-21
> **Supersquirrel said:**
> NTFS fragments because there is no block groups like most linux filesystems. In NTFS there is the MFT and than free space. In ext3 there is 128MB block groups seperated by Inodes.

Wow, windows is even worse than I thought!!

jdb

---

### Post by glacialfury on 2009-04-27
Many, many good suggestions here.  I did find the major cause of the problem.  I had been running Transmission and noticed in the system monitor that IOWait was using nearly all the processor, all the time.  I hadn't noticed it before because a) I'd never heard of IOWait, and b) the default color was so dark I could barely see it. 

I adjusted the torrent settings and it doesn't seem to be a problem anymore; the system is much snappier now that it has its cycles back.

Thanks to all, especially jdb, who continually confounds me with his wizardry.

---

