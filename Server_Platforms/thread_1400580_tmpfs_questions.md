---
title: "tmpfs questions"
date: 2010-02-07
forum: Server Platforms
---

### Post by norfolknog on 2010-02-07
Hello! I'm new here, hoping for some help from you knowledgeable people!

I have built what is going to be a quiet music server based on the Intel D945GSEJT Atom motherboard, with 1gb RAM, a 4gb Flash drive for Ubuntu and a 500gb disk purely for my FLACs. I don't need a graphical environment so decided to use Ubuntu server. I read that v9 did not include support for the Realtek NIC on this board , but 8.10 did. So, I installed onto the flash drive from the 8.10 Server image, creating a single ext2 filesystem. My NIC worked and all was fine.

I then read in the server docs about the do_release_upgrade command, which sounded like a good way to go to v9, so I issued the command and that all seemed to go OK, I've now got a Jaunty Jackalope server build with a working NIC. 

However I am puzzled by a few things concerning some filesystems that seem to have appeared since the upgrade (though to be honest I can't be sure they weren't there after the initial 8.10 build). Here is the output from df -hl:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             3.5G  1.2G  2.2G  35% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M   96K  496M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  128K  496M   1% /dev
tmpfs                 497M     0  497M   0% /dev/shm
lrm                   497M  2.2M  494M   1% /lib/modules/2.6.28-18-server/volatile
```
As you can see, there are 6 "filesystems" other than my root filesystem (which is on /dev/sdb1). At first I didn't even know what they were, but having done some investigation I now know that they are tmpfs filesystems, created in RAM. My questions are:

1) Why does df say they are all 497mb in size? This surely cannot be true, as that would add up to more disk space and RAM than I have altogether.

2) How are they created at boot time? They are not mentioned in /etc/fstab, so what is it that causes them to be created?

3) I'm sure I didn't specify them during installation and upgrade, so how/why did they get created? 

4) Is it OK to keep this scheme, given that I have only 1gb of RAM?

Thanks in advance for your help!
Andy

---

### Post by yogesh.girikumar on 2010-02-09
Hi,


       What you are seeing under df are temporary filesystems that are originally present in the RAM. But they are shown as mounted in the hard disk.[INDENT]      > Why does df say they are all 497mb in size? This surely cannot be true, as that would add up to more disk space and RAM than I have altogether.   [/INDENT]    The total is just 497MiB of data. It's shared among all the filesystems. They are shown as mounted but in reality they are present in the primary storage. Sometimes they are swapped to the disk.[INDENT]      > How are they created at boot time? They are not mentioned in /etc/fstab, so what is it that causes them to be created?   [/INDENT]    Since they're not originally present in the hard disk, they are not mentioned in /etc/fstab. But you can find the entries in /etc/mtab which is the mounted filesystems table. These filesystems are dynamically generated during boot time.[INDENT]      > I'm sure I didn't specify them during installation and upgrade, so how/why did they get created?   [/INDENT]    They're dynamically created during system boot. Just like proc filesystem (procfs).[INDENT]      > Is it OK to keep this scheme, given that I have only 1gb of RAM?   [/INDENT]    **QUOTING WIKIPEDIA:**
> Everything stored in tmpfs is temporary in the sense that no files will be created on the hard drive;
 however, swap space is used as backing store in case of low memory situations. 
On reboot, everything in tmpfs will be lost.       It should not be a problem. Since the filesystems are dynamically created and are used only when necessary. They are cleared out on reboot. ( Including /var/run and /var/lock )


       See: [http://en.wikipedia.org/wiki/Mtab](http://en.wikipedia.org/wiki/Mtab)
See: [http://en.wikipedia.org/wiki/Procfs](http://en.wikipedia.org/wiki/Procfs)
See: [http://en.wikipedia.org/wiki/Tmpfs](http://en.wikipedia.org/wiki/Tmpfs)

Hope this helps.

---

### Post by norfolknog on 2010-02-10
Thanks yogesh, that is helpful. :D

---

