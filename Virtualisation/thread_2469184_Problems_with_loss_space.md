---
title: "Problems with loss space"
date: 2021-11-22
forum: Virtualisation
---

### Post by rl-cr on 2021-11-22
Hello

I have a problem that I don't understand. When I use the disk usage analyzer I can see that the drive on which I have Ubuntu 18 installed has a total capacity of 52.6 GB and that I only have 5.4 GB available.
When I click on that drive to see where the files that occupy the space are located, the system tells me that there is only 16.1 GB used of the root.
I don't know where the 36.5GB is and what is occupying it.

If I use the command "df -h" in the terminal. It shows me that /dev/sda1 is 49GB in size and 95% used. But I can't find the files that occupy it. I do not understand what's happening.
The system is mounted on a virtual drive with VirtualBox with a size of 50GB.

Greetings and thanks for the help.

---

### Post by TheFu on 2021-11-22
Less attempts at describing and more facts, please.

**df -Th**  Post that wrapped in 'code-tags' so the columns line up.  
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)   _ <--- fixed line - _thanks deadflowr

And **lsblk -e 7 -o name,size,type,fstype,mountpoint** posted, also in 'code-tags' will be helpful.

---

### Post by rl-cr on 2021-11-22
```
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           395M  1.6M  393M   1% /run
/dev/sda1        49G   44G  2.6G  95% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop0       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop1       56M   56M     0 100% /snap/core18/2246
/dev/loop2       62M   62M     0 100% /snap/core20/1169
/dev/loop3      1.0M  1.0M     0 100% /snap/gnome-logs/100
/dev/loop4      640K  640K     0 100% /snap/gnome-logs/106
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop6      219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop7       62M   62M     0 100% /snap/core20/1242
/dev/loop9      100M  100M     0 100% /snap/core/11743
/dev/loop8       56M   56M     0 100% /snap/core18/2253
/dev/loop10     2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop11     141M  141M     0 100% /snap/gnome-3-26-1604/100
/dev/loop12     141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop13     218M  218M     0 100% /snap/gnome-3-34-1804/60
/dev/loop14     244M  244M     0 100% /snap/gnome-3-38-2004/39
/dev/loop16     768K  768K     0 100% /snap/gnome-characters/726
/dev/loop15     100M  100M     0 100% /snap/core/11993
/dev/loop17     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop18     243M  243M     0 100% /snap/gnome-3-38-2004/76
/dev/loop19     2.7M  2.7M     0 100% /snap/gnome-system-monitor/174
/dev/loop20     2.5M  2.5M     0 100% /snap/gnome-calculator/884
/dev/loop21     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop22     2.7M  2.7M     0 100% /snap/gnome-system-monitor/169
/dev/loop23     128K  128K     0 100% /snap/bare/5
/dev/loop24     768K  768K     0 100% /snap/gnome-characters/761
VB_Ubuntu       200G  156G   44G  79% /media/sf_VB_Ubuntu
tmpfs           395M   28K  395M   1% /run/user/121
tmpfs           395M   48K  395M   1% /run/user/1000


```

---

### Post by deadflowr on 2021-11-22
I fixed the code tags for you.
Not sure why TheFu posted a sort of half link which only points to the smiley/emoji section of the forum.
Proper code tag is here: [https://ubuntuforums.org/misc.php?do=bbcode#code]("https://ubuntuforums.org/misc.php?do=bbcode#code")
Quick and easy howto and why use code tags are found in this thread here:: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by rl-cr on 2021-11-22
**lsblk:**

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  65.1M  1 loop /snap/gtk-common-themes/1515
loop1    7:1    0  55.5M  1 loop /snap/core18/2246
loop2    7:2    0  61.9M  1 loop /snap/core20/1169
loop3    7:3    0   956K  1 loop /snap/gnome-logs/100
loop4    7:4    0   548K  1 loop /snap/gnome-logs/106
loop5    7:5    0  65.2M  1 loop /snap/gtk-common-themes/1519
loop6    7:6    0   219M  1 loop /snap/gnome-3-34-1804/72
loop7    7:7    0  61.9M  1 loop /snap/core20/1242
loop8    7:8    0  55.5M  1 loop /snap/core18/2253
loop9    7:9    0  99.3M  1 loop /snap/core/11743
loop10   7:10   0   2.5M  1 loop /snap/gnome-calculator/826
loop11   7:11   0 140.7M  1 loop /snap/gnome-3-26-1604/100
loop12   7:12   0 140.7M  1 loop /snap/gnome-3-26-1604/104
loop13   7:13   0 217.9M  1 loop /snap/gnome-3-34-1804/60
loop14   7:14   0 243.9M  1 loop /snap/gnome-3-38-2004/39
loop15   7:15   0  99.4M  1 loop /snap/core/11993
loop16   7:16   0   704K  1 loop /snap/gnome-characters/726
loop17   7:17   0 164.8M  1 loop /snap/gnome-3-28-1804/161
loop18   7:18   0 242.4M  1 loop /snap/gnome-3-38-2004/76
loop19   7:19   0   2.5M  1 loop /snap/gnome-system-monitor/174
loop20   7:20   0   2.5M  1 loop /snap/gnome-calculator/884
loop21   7:21   0 162.9M  1 loop /snap/gnome-3-28-1804/145
loop22   7:22   0   2.5M  1 loop /snap/gnome-system-monitor/169
loop23   7:23   0     4K  1 loop /snap/bare/5
loop24   7:24   0   704K  1 loop /snap/gnome-characters/761
sda      8:0    0    50G  0 disk 
&#9492;&#9472;sda1   8:1    0    50G  0 part /
sr0     11:0    1  1024M  0 rom  


```

---

### Post by Holger_Gehrke on 2021-11-22
To see what uses your space you wouldn't use df (disk free) but du (disk used). More specifically you'd start at the root and use 
```

du --max-depth=1 --one-file-system /

```
Discarding the various errors about directories you don't have access to (/root,/lost+found,some subdirs of /tmp and /var; you can either hide these error by adding a redirection of standard error with '2>/dev/null' at the end of the command to get cleaner output or run the command with 'sudo' so it can access all the directories it complains about) you'll get a good idea what is taking up space. You can refine this by using the same command but giving another directory instead of '/', for example 'du --max-depth=1 --one-file-system /usr/share/' would show you how much space is taken up by the various directories full of shared data of various programs. For dirs with lots of subdirs adding a pipe to 'sort -g' at the end of the command might be helpful ('du --max-depth=1 --one-file-system /usr/share|sort -g') ...

Holger

---

### Post by grahammechanical on 2021-11-22
I am uneducated about many things but there are a few things that I do not understand about this problem. Knowing the answers might shed some light on the situation allowing others to solve the mystery.

Have you installed Ubuntu Core 18? That would explain why you have snap apps without having snapd or snap-store installed. I am comparing the printout of lsblk on my Ubuntu 20.04 install.

Have you installed Ubuntu 18 in a VM? What OS is hosting the VM? Are you running Disk Analyzer from the OS that is hosting the VM or from the OS installed in the VM?

Regards

---

### Post by rl-cr on 2021-11-22
Thanks for the information.

---

### Post by rl-cr on 2021-11-22
If I use: 
```
 
sudo du --max-depth=1 --one-file-system /

```

Then i get the following:

```
64    /snap
4    /cdrom
232    /root
911940    /lib
4955388    /opt
3364884    /var
11252    /sbin
4    /mnt
149560    /boot
12416    /bin
4    /srv
12    /media
12880    /etc
16    /lost+found
4    /lib64
31365412    /home
5208    /tmp
3166504    /usr
46052948    /

```

---

### Post by rl-cr on 2021-11-22
The version of ubuntu I have installed is```

ubuntu18@ubuntu18-VirtualBox:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

```

It's a Virtual Machine in VirtualBox. My PC has installed Windows 10.
I don't really understand the last question: "Are you running Disk Analyzer from the OS that is hosting the VM or from the OS installed in the VM"

Thank you

---

### Post by TheFu on 2021-11-22
> **deadflowr said:**
> I fixed the code tags for you.
Not sure why TheFu posted a sort of half link which only points to the smiley/emoji section of the forum.
Proper code tag is here: [https://ubuntuforums.org/misc.php?do=bbcode#code]("https://ubuntuforums.org/misc.php?do=bbcode#code")
Quick and easy howto and why use code tags are found in this thread here:: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

My link above was a mistake.  Seems my "wiki" software decided that needed to be an internal link and added the [[]] for me. I didn't notice it. Thanks for pointing out my mistake so I'll be aware next time.

I posted specific commands, with specific options, to see some important information that we still don't have. Specifically, the file system AND never show loop devices, since those are completely irrelevant for space allocations (loops point to space counted in other areas already included).  
Would be good to see the exact commands provided run and the output. Please.  Some file systems lie to du and df.  They can't help it, as it is part of their core features.  If any of those other file systems are being used, then other commands have to be used to get the information.

Only 18.04.0 (the initial release 18.04) and 18.04.6 are supported still. I know Canonical wanted to simplify how many kernels each release needed for support, but I don't remember exactly which LTS release that all started.  Also, Canonical used to have a nice release vs kernels table which I haven't seen in months this showed that information in a graphic.  Found it:  [https://wiki.ubuntu.com/Kernel/Support#A18.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/Support#A18.04.x_Ubuntu_Kernel_Support) See how it is required to either stay on the base install (.0) or move to the point release .1 --> .2 --> .3 every time the next point release happens?

---

### Post by grahammechanical on 2021-11-22
> I don't really understand the last question: "Are you running Disk  Analyzer from the OS that is hosting the VM or from the OS installed in  the VM"

Disk Analyzer is a Ubuntu app and you are running Ubuntu in a VM hosted by Windows 10. That means that Disk Analyzer is running on Ubuntu inside the VM. That is information that I was not clear about. I do not know if the analysis is affected by being run on a VM so-called drive.

Regards

---

### Post by slickymaster on 2021-11-23
*Thread moved to **Virtualisation**.*

---

### Post by MAFoElffen on 2021-11-23
From you output in post #9: (sorted and formatted)
```

Directory      Used
/              46052948
/home          31365412
/opt           4955388
/var           3364884
/usr           3166504
/lib           911940
/boot          149560
/etc           12880
/bin           12416
/sbin          11252
/tmp           5208
/root          232
/snap          64
/lost+found    16
/media         12
/srv           4
/mnt           4
/lib64         4
/cdrom         4

```
"/" includes all used from everything. The "total" of space used and available that is going to show is always going to be less, you have some space used for partition tables... then with ext4 filesystems use a portion of that for the filesystem itself for tables, journaling, etc. So in 50G, you have about 49G of storage.

The home directory is using a lot of space. You have 31.3G used in that one directory, leaving 14.6G out of that 49G for everything else. Everything else adds up to 12.5G, leaving a little less than 2.5G... 

So yes, about 95% full.  Just the Math.

---

### Post by TheFu on 2021-11-23
There are 50 different answers for getting sorted output.  I like
**du -sh * | sort -h**
Then I'm not having to figure KB, GB and TB by counting columns and sort -h understands that 1TB is lager than 900GB. It does the right thing.

---

### Post by MAFoElffen on 2021-11-23
LMAO... So many ways...

Since he didn't sort is ouput.. I used sed, to convert the white space into comas, then imported it into LibreOffice 'Calc' as a CSV file. That way i could easily convirt to 'data' analyze his storage as I wanted.

---

