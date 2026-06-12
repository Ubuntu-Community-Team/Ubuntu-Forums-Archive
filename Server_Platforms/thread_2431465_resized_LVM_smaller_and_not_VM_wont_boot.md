---
title: "resized LVM smaller and not VM wont boot"
date: 2019-11-16
forum: Server Platforms
---

### Post by Heeter on 2019-11-16
Hi all,

This is for a Ubuntu18.0.3 with KVM. I have a VM Ubuntu18 running on it.

I resized the LVM from 150 to 50 using the "lvreduce" command but I forgot to resize the ext4 afterwards. Then I rebooted.

So now I got this:

[https://i.postimg.cc/NFqjhJkq/Screenshot-from-2019-11-16-16-54-14.png](https://i.postimg.cc/NFqjhJkq/Screenshot-from-2019-11-16-16-54-14.png)

Can someone assist me on getting this up and running again please?

Regards

---

### Post by darkod on 2019-11-16
When resizing you should resize the filesystem FIRST, and then resize the partition (or the LV).

When extending you first extend the partition/LV and then the filesystem after.

If you have the option to attach an ISO to the VM and boot from it, try booting with the ubuntu 18.04 iso and go into rescue mode. Try to extend the LV to 150GB again so that you go back to how it was before.

---

### Post by Heeter on 2019-11-16
I have is  a "Live" iso. went to ubuntu website to download different version, but all available for 18.0.4 is live versions. there is no rescue mode in the live iso. :(

---

### Post by Heeter on 2019-11-16
Is there anything else I can do?

---

### Post by TheFu on 2019-11-16
```
lvreduce -r
```

a very helpful option.

---

### Post by Heeter on 2019-11-16
> **TheFu said:**
> ```
lvreduce -r
```

a very helpful option.

Normally that is helpful, but not in this case, I can't get into the OS.

Regards

---

### Post by darkod on 2019-11-17
I don't know what exactly do you mean with "live" iso. The -live-server- or the desktop iso that has Try Ubuntu live mode. It all got confused when they released this "additional type" of server image and I hate it!!!

Anyway, you have the standard -server- iso here: [http://cdimage.ubuntu.com/releases/18.04.3/release/](http://cdimage.ubuntu.com/releases/18.04.3/release/)

And you can also use the Desktop iso by booting into Try Ubuntu and then working in terminal. You don't need to mount anything from the OS, just to activate the LVM and extend the LV you need. NOTE how I said ACTIVATE, not creating new LVM over the old one!!!

PS. Basically you could even use the System Rescue CD, anything that allows you quick boot into live terminal with LVM tools available, will do the job. [http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/)

---

### Post by TheFu on 2019-11-17
> **Heeter said:**
> Normally that is helpful, but not in this case, I can't get into the OS.

Regards

Actually, it isn't helpful NOW.  It would have resized the file system at the same time for ext4 file systems.

---

### Post by Heeter on 2019-11-17
Thank you for that, Thefu

I do appreciate it, didn't know about that command actually.

This is still very new to me. Please bear with me. 

Had to walk away from this last night as I was just overwhelmed with this LVM stuff.

And the saving a server install is really new to me as well.

Regards

---

### Post by Heeter on 2019-11-17
> **darkod said:**
> I don't know what exactly do you mean with "live" iso. The -live-server- or the desktop iso that has Try Ubuntu live mode. It all got confused when they released this "additional type" of server image and I hate it!!!

Anyway, you have the standard -server- iso here: [http://cdimage.ubuntu.com/releases/18.04.3/release/](http://cdimage.ubuntu.com/releases/18.04.3/release/)

And you can also use the Desktop iso by booting into Try Ubuntu and then working in terminal. You don't need to mount anything from the OS, just to activate the LVM and extend the LV you need. NOTE how I said ACTIVATE, not creating new LVM over the old one!!!

PS. Basically you could even use the System Rescue CD, anything that allows you quick boot into live terminal with LVM tools available, will do the job. [http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/)

Thanks a million for the explanation, everytime I booted from the server-live iso that I have, it keeps telling me that there is no rescue mode in the iso. Thanks for the link to the regular install iso.

I am going to try the systemrescue iso right now. Please wish me luck. will report back immediately.

Regards

---

### Post by Heeter on 2019-11-17
Well

I activated and resized the LVM back to 100% full, the way it was, but it still isn't cooperating.

[https://i.postimg.cc/ncjKTByB/Screenshot-from-2019-11-17-17-18-06.png](https://i.postimg.cc/ncjKTByB/Screenshot-from-2019-11-17-17-18-06.png)

I am at a loss as how to proceed.

The original size was 150G, resized to 60G before I forgot to resize the partition.

Regards

---

### Post by TheFu on 2019-11-17
Dude, every time use use lvresize to make an LV larger, please add the -r switch so the file system gets resized at the same time!

If you want to increase the size from the current size, use a 
```
sudo lvresize -L +20G -r  {LogicalVolumeName}
```
This assumes the VG has some free space - 20GB more. 

BTW, the OS LV should be 25G at most.  Then create other LVs for other needs, like a place for /home/ and a place for /var/ if that will be of non-trivial size.

And please post text, not images.  Copy paste the text and put it inside *code tags* so it lines up as expected.
I've posted my VG/LV layouts in these forums a number of times the last few months if you need example setups.  The error in the command is pretty clear.  Don't confuse extents with MB/GB. They aren't easily related.  Use the -L option to work in whatever unit you want - MB, GB, TB, ... whatever.  The lvresize **manpage** explains all of this.  Get used to checking the manpage when you don't know a command well.

HowToForge has an LVM2 tutorial, if you need it.  LVM is the same on all Linux systems, so don't worry if you find a guide for Redhat, Cent, Arch, Debian, Ubuntu ... it doesn't matter. The command and options are all the same.

To get an overview of everything LVM on a system, run
```
sudo pvs
sudo vgs
sudo lvs
lsblk
```

There are some handy options for lsblk which provides lots-o-good information, but without a wide terminal, it is best to start with just the simple one.  **lsblk -o name,size,type,fstype,mountpoint** is handy as an alias.

---

### Post by Heeter on 2019-11-17
Hi, TheFu, Thank you for your response. Thank you for being patient with me too.

The reason I am posting screenshots is because virt-manager is refusing to let me highlight and copy the text, because I normally do post ssh text only. The printscreen function of virt-manager doesn't seem to do anything either. It also failed the vm clone that I created before I started this. It looked like it created the clone but it was corrupt when I reached for it after.

I did use the Howtoforge guide. it was how I was up and running with no issues when I first started this project replacing the old server.

Well I tried it again with the -r command. I still can't get around the superblock issue

---

### Post by Heeter on 2019-11-17
Hi again, 25G the most for the OS LVM? 

Maybe I should step back and rethink this whole setup. Lost 11 years of emails, don't want to lose anymore stuff.

---

### Post by TheFu on 2019-11-17
We can redirect output to files.  We all forget that from time to time.
```
sudo lvs | tee /tmp/lvs.stuff
```
then take those files somewhere else and post the data.  Sometimes stderr needs to be redirected into stdout .... 2>&1 will do that.

For a refresher on CLI stuff and rediction ... [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

If things get really bad, I'd blow away the VM, then do a fresh install with the sizes I want, restore the data, settings and lastly, the programs. From the versioned backups.  The programs will see the data and previous settings will be used.  Takes about 30 min for basic restore then add in the time for non-trivial, huge, data to be restored.  This assumes you have solid backups, of course.

---

### Post by Heeter on 2019-11-17
I am going to start over with this VM setup.

Definitely sounds like I need to rethink this setup better, starting from the hardware up again. Sounds like I have done everything wrong from the ground up.

Regards and thank you.

---

### Post by TheFu on 2019-11-17
> **Heeter said:**
> Hi again, 25G the most for the OS LVM? 

Maybe I should step back and rethink this whole setup. Lost 11 years of emails, don't want to lose anymore stuff.

Er .... backups?

The way that I setup storage is to solve most issues BEFORE they can happen.  By using LVM, we have all sorts of flexibility, but adding storage to an LV is 100x easier and safer than removing it.

[LIST]
[*]Keep the OS and OS settings in an LV.
[*]Keep /home in a different LV.
[*]If /var/ will get big - perhaps it has DBMS files or websites or virtual machines, then add LVs to the specific places needed.
[*]Keep massive file data in other LVs, or better, on network storage.
[*]If you use virtual machines, perhaps using 1 or 2 LVs for each of those is a good idea? Block storage is faster than file storage
[/LIST]
By keeping different types of files in different storage areas, I can better handle backups, system upgrades, problems, and selective restores, if needed.  

My restores aren't 1 click.  For some people, having a 1-click restore is critical, but to make a useable backup for that purpose breaks lots of my other needs, like efficient networking and efficient storage use.

For example, the way I backup the OS and OS settings is different from the way I backup huge media files.  Backing up DBs is different from /home/.  For me, it is about backing up what is needed to recreate the system quickly, with minimal-to-zero downtime due to the backup process, using a small amount of network bandwidth and storage. All the backups must be automatic, versioned, and "pulled" by the backup server.  At one point, we were overrunning our overnight backup window because I didn't care enough about being efficient. Ended up reworking the entire backup solution.  Now most backups complete in 1-4 minutes for each system.  I don't backup programs, just a list of manually installed packages. Everyone has different backup requirements.  LVM can help make zero-downtime for backups the rule, not the exception.

Don't allocate all the storage to LVs in the beginning.  If you do, you've just taken away most of the flexibility.
```
$ sudo pvs
  PV                     VG        Fmt  Attr PSize   PFree  
  /dev/mapper/sda3_crypt ubuntu-vg lvm2 a--  464.54g 260.08g
```
That's a 500G drive, with 260G unused.  Flexibility.  It happens to be encrypted.

I've posted my layouts in these forums a few times. They might be helpful, if you find them.  
Don't go crazy making LVs for everything trivial.  If /var/ will be just a few GB at most, no need to have an LV for it. It is a judgement call.

---

### Post by darkod on 2019-11-18
It's probably too late, but for simple LV extend I like the lvextend more than lvresize. If you shrinked from 150GB to 60GB all you needed to do to begin with is:

```
lvextend -L +90GB /dev/ubuntu-vg/ubuntu-lv
```

Then check if the filesystem has woken up with any luck. Not to try and resize it right away, first to check if only extending the LV back to original size helped you. It is easy to run resize2fs at any time, don't rush with it in rescue operations.

But like I said, judging by other comments it might be too late for this now...

---

### Post by LHammonds on 2019-11-18
I don't think I can add to anything that has already been said to try and revive the system.

But I can reassure you that expanding a file system is MUCH safer than ever contracting it.  With that in mind, you have to be careful when you initially create the file systems.  I do so by giving it the least amount of space possible and expanding it manually to fit my needs.

I have covered this in how I setup an Ubuntu Server for production use over a long period of time...along with step-by-step instructions/examples on how to do so.  You can find it [here](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p614).

LHammonds

---

### Post by Heeter on 2019-11-18
> **LHammonds said:**
> I don't think I can add to anything that has already been said to try and revive the system.

But I can reassure you that expanding a file system is MUCH safer than ever contracting it.  With that in mind, you have to be careful when you initially create the file systems.  I do so by giving it the least amount of space possible and expanding it manually to fit my needs.

I have covered this in how I setup an Ubuntu Server for production use over a long period of time...along with step-by-step instructions/examples on how to do so.  You can find it [here](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p614).

LHammonds


WOW, what a tutorial! I am going to follow that one definitely upon my reinstall right now.

Regards

---

