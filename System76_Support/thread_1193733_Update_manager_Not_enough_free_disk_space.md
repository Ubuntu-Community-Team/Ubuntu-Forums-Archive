---
title: "Update manager: Not enough free disk space"
date: 2009-06-21
forum: System76 Support
---

### Post by solotwit on 2009-06-21
When I tried to dl updates with update manager, it said not enough free disk space on drive '/'.

I have 161 gigs available on hd.

I have had this issue recently for some other dl's too.

---

### Post by thomasaaron on 2009-06-22
How much space do you have in your root dir?
And is your trash empty?

---

### Post by xtjacob on 2009-06-22
Sounds like your APT cache is full.
Run ```
sudo apt-get clean
```
and
```
sudo apt-get autoclean
```

---

### Post by solotwit on 2009-06-22
It looks like my root folder has 0 bytes free space. I emptied my trash.

I ran those commands in terminal.

root file still says 0 bytes available and I can't dl updates. It says I need 322M of free space. Maybe if I just restart?

---

### Post by xtjacob on 2009-06-22
Go to the terminal and type in df -h and report the output.

---

### Post by Derath on 2009-06-22
Had the same problem on different boxes here. Here's how I got around it. my /home directory is massive free space, so I moved /var/cache to ~/temp/cache and created a symlink in /var to point to ~/temp/cache.

I know, probably not the safest idea, but after the upgrade you might be able to move it back.

Also before doing all that, check /var/log for massive log files, that may help as well (anything over 1-2M in size)

---

### Post by solotwit on 2009-06-22
Here's what I get from df -h


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   14G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  164K  1.5G   1% /dev
tmpfs                 1.5G  460K  1.5G   1% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6             213G   39G  163G  20% /home
overflow              1.0M   12K 1012K   2% /tmp

---

### Post by xtjacob on 2009-06-22
All your important files and programs are stored under your root folder, and your root folder is full. So what you have to do is either make the partition bigger or remove some unnecessary packages.

---

### Post by solotwit on 2009-06-22
Okay, I'll check on how to do that in the forums. I just got this computer a month ago and don't feel like I've added very much to it. Is this something that happens regularly? Do I need to create a partition to avoid this in the future?

---

### Post by xtjacob on 2009-06-22
What you should do is expand the root partition, but you should try what Derath said because that moves it to your home directory, but like he said it's not the safest idea.

---

### Post by Derath on 2009-06-23
I've done that a few times, after I move the directory, I'll run the update and after the update is done, I'll do apt-get clean, apt-get autoremove, and then try to move everything back.

I'll be honest, I'm not sure about the complete security ramifications when moving that directory into a /home folder, but I'm pretty sure that if you move it back once done, everything should be alright.

---

### Post by solotwit on 2009-06-23
I don't know man. Sounds kinda janky to have to do that everytime I want to update. I would like to know how my root folder got full so quickly. I used the system janitor, and deleted residual config files in synaptic. Root folder is still full. I can't find any tutorials on making he partition bigger yet. Thanks for the tip.

---

### Post by Derath on 2009-06-23
Hmm... check /var/log you might have some large log files...

Also I don't have to do that for normal updates, I usually only need to do it for upgrading versions.

Does sound like there's something a little more massive on your root partition though.

---

### Post by solotwit on 2009-06-23
I just figured out where var/log is.

I have something in var/log called "lastlog" that's like 8 mb. Delete it eh?

How do I delete it?

---

### Post by Derath on 2009-06-23
lastlog probably not, but I think rebooting cuts that one down...

Browse through some of the files and folders in /var/log, the ones that are safe to delete are those not in use (usually archived logs, they will have something like *.0, *.1, or even *.1.gz). Others like kern.log, messages, syslog without numbers are files are still monitoring the system, and deleting them won't necessarily cause an error, they can make troubleshooting difficult. 8 Megs isn't much, but definitely look for large ones (15+ meg or so, I've even had one that was 2 gig due to a card reader and microSD to SD adapter).

Also, in order to delete them, you must be logged in as root, or use sudo.

The last option that xtjacob mentioned might be worthwhile as well, look through the add/remove programs and remove apps that you don't use, then use apt-get clean and apt-get autoremove then try again.

---

### Post by solotwit on 2009-06-23
thanks for the tips. I removed apps, did the clean, autoclean, autoremove, everything but make the partition bigger. Nothing in var/log file is biger than 1mb other than "lastlog". So, I got gParted, we'll see what happens. I guess I'll go to 20gb.

---

### Post by osx424242 on 2009-06-23
Might help you find the problem:
```
du -k / --max-depth=2 | sort -n | tail -20
```
will give you the top 20 directories by usage (/home/yourname and /home will probably be the top 2, but the next most will probably point you in the right direction).  If you want to drill deeper either replace '/' with the directory name or increase max-depth.

I know there's a GUI tool to show directory usage graphically (e.g. in a pie chart) but I don't remember what it's called.

---

### Post by thomasaaron on 2009-06-24
Applications > Accessories > Disk Usage Analyzer

---

### Post by solotwit on 2009-06-25
Thanks for the ideas/tips. I dl a live cd version of [gParted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779"), burned it to cd. Then I restarted my computer and in the system76 screen hit f2 for sys utilities. In sys. util. I went to the BOOT menu and selected the cddvdrom drive as number one. Then the computer finished booting into the cd, and it went straight into gParted. In here, it was fairly self explanatory on how to resize/move the partitions. I **shrunk** my home partition, **moved** the swap over, then **grew** the root partition. 

But, I did this the wrong way, I entered numbers instead of just dragging the *image* of the root partition to the right, filling the available space. So I had to switch things up to get everything filled up and leave no unallocated space on the drive. Then I hit apply.

Huge mistake. I think that at this point a giant WARNING! box should have come up saying, "Every step you made to get your partitions to this point, beginning from the original setup of the patitions, is now going to be done. And if you stop it, your filesystem may have SEVERE damage. So look at the list of steps, and decide if you want to do all of them, or go back to square one and do it correctly the first time." Or something like this. But it doesn't, it just starts to do it and says something like "depending on the amount of steps this may take a very long time." And if you try to cancel at this point you are told you may cause SEVERE filesystem damage."

So basically, my computer got hijacked for about 5 hours as it shrunk partitions, moved partitions, grew partitions, then moved, grew, and shrunk some more. And if you have a 250GB HD or higher, it will take, as it says, a *very* long time. Poorly designed program I would say. I've never partitioned a HD before. I hope to never have to again. The next day, I was able to dl my 32MB of system updates. :-?

---

### Post by xtjacob on 2009-06-25
Just for future reference I think there is a partitioner on the Ubuntu live CD.

---

### Post by solotwit on 2009-06-26
Any idea what's going on here? My root is full again. After dl only some sys updates. I don't get it.

[FONT=monospace]
11720    /usr/sbin
14296    /etc
27664    /boot
30804    /usr/include
33504    /opt/google
35228    /opt
66184    /var/cache
146392    /usr/lib32
155620    /usr/src
155660    /usr/bin
227832    /lib/modules
233188    /var/lib
256932    /lib
316060    /var
1050832    /usr/share
1247556    /usr/lib
2801644    /usr
39341672    /home/lucas
39341692    /home
42822688    /

[/FONT]

---

### Post by drewbenn on 2009-06-26
I'm confused by that output.  It shows only about 3.5 GB being used in your root directory.  I'm afraid I don't understand what is happening or why the partition is being reported as full by df but doesn't seem to actually be full, per du.

Okay I did a little searching and it's not uncommon for du and df to report different numbers... but a difference of 10+ GB still seems odd.  Maybe take a look at:
[http://forums.vpslink.com/howtos/2271-when-df-du-dont-match.html](http://forums.vpslink.com/howtos/2271-when-df-du-dont-match.html)
[http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html](http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html)
[http://sysunconfig.net/aixtips/df_du_diff_out.txt](http://sysunconfig.net/aixtips/df_du_diff_out.txt)

The first suggests running 'lsof +L1'.  My best guess is that something has allocated some space and not let go of it... but I'm hardly an expert here.  Someone with a bit more knowledge and experience will have to step in, because I'm just grasping at straws here.

---

### Post by thomasaaron on 2009-06-26
solowit, do you have a virtual machine installed? When you create one, they allocate a certain amount of disk space, but I'm not sure it shows up with du, etc...

Also, is your trash empty?

Also, this kind of sounds a lot like the bug that causes huge log files. Try running...

sudo rm /var/log/syslog
sudo rm /var/log/messages
sudo rm /var/log kern.log

Then reboot and see how much free space you have.

---

### Post by solotwit on 2009-06-26
Thanks drewbenn, I checked those out. I didn't really see a fix, just an explanation. If the reading is incorrect, then shouldn't I still be able to dl updates and whatnot? 

thomasaaron, Im not sure what a virtual machine is but I'm pretty sure I don't have one. Trash is empty. I ran the commands and rebooted ( all except the last one, couldn't figure out what goes between log kern) and still the same issue. Here's what came out of some commands

**lsof +L1**

COMMAND  PID  USER   FD   TYPE DEVICE SIZE NLINK   NODE NAME
firefox 4001 lucas   51u   REG    8,1    0     0 754792 /var/tmp/etilqs_KZxVWjcubK2eVHd (deleted)

**DF**

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             28834744  28179916         0 100% /
tmpfs                  1525524         0   1525524   0% /lib/init/rw
varrun                 1525524       112   1525412   1% /var/run
varlock                1525524         0   1525524   0% /var/lock
udev                   1525524       164   1525360   1% /dev
tmpfs                  1525524       448   1525076   1% /dev/shm
lrm                    1525524      2560   1522964   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6            208658228  40188456 157870492  21% /home
overflow                  1024        12      1012   2% /tmp

**DU -s**

40057224    

**DU**

came out with a large list of things and the number *40057196* at the end. I can post if helpful.

Thanks for any ideas.

thanks jdb. I'm not sure what to do with these results (delete the largest 5 directories?) so I'll post the results hoping somebody might see something.

sudo du -SB 1M /  | grep -v "/home" | sort -n | tail -20
 du: cannot access `/home/lucas/.gvfs': Permission denied
du: cannot access `/proc/6589/task/6589/fd/4': No such file or directory
du: cannot access `/proc/6589/task/6589/fdinfo/4': No such file or directory
du: cannot access `/proc/6589/fd/4': No such file or directory
du: cannot access `/proc/6589/fdinfo/4': No such file or directory
25    /usr/lib/thunderbird/components
27    /boot
28    /opt/google/chrome
30    /var/lib/dkms/nvidia/180.44/build
31    /usr/share/midi/freepats/Tone_000
36    /usr/lib32/dri
36    /usr/lib/dri
43    /var/lib/apt-xapian-index/index.1
45    /usr/share/myspell/dicts
45    /var/lib/apt/lists
46    /var/lib/dpkg/info
63    /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib
64    /usr/lib/jvm/java-6-openjdk/jre/lib
78    /usr/lib32
153    /usr/bin
168    /usr/lib/openoffice/basis3.0/program
318    /usr/lib
4343    /var/backup/2009-06-18_13.21.29.020432.system76-pc.ful
5874    /var/backup/2009-06-17_12.33.49.982185.system76-pc.ful
13805    /var/backup/2009-06-25_22.02.11.363133.system76-pc.ful

---

### Post by jdb on 2009-06-26
> **solotwit said:**
> Thanks drewbenn, I checked those out. I didn't really see a fix, just an explanation. If the reading is incorrect, then shouldn't I still be able to dl updates and whatnot? 
...

Thanks for any ideas.

This will give you the 20 largest directories not on your home directory.

The numbers are in Megabytes.

```
sudo du -SB 1M /  | grep -v "/home" | sort -n | tail -20
```

jdb

---

### Post by osx424242 on 2009-06-26
> **solotwit said:**
> 13805    /var/backup/2009-06-25_22.02.11.363133.system76-pc.ful

That is the cause, right there: a nearly-14 GB directory.  Deleting that should fix your problem.  But:
- what caused it?
- is this going to happen again?
- is there anything important in there?

There are two more, in the 4-6 GB range, dated June 17 and 18.  But you just expanded your partition a couple days ago, right?  Is your system clock off by a week?  If so, those new ones were probably created after you resized your partition, which is why it filled up again.

---

### Post by solotwit on 2009-06-26
Hey thanks. I think that /var/backup stuff is from my system backup. I do have a program for that. My clock is ok. I agree, I can find where the info is, but how to keep it from doing this again. That would be ideal. I will try some things this weekend. Thanks again.

---

### Post by jdb on 2009-06-27
> **solotwit said:**
> Hey thanks. I think that /var/backup stuff is from my system backup. I do have a program for that. My clock is ok. I agree, I can find where the info is, but how to keep it from doing this again. That would be ideal. I will try some things this weekend. Thanks again.

You need to change where the backups are stored.
/var or anyplace on the root partition is not the place for backups.
An external drive is the best place.
If you can't find an option in your backup program to change the location, you might need to find another backup program.

jdb

---

### Post by solotwit on 2009-06-27
Thanks, I'll do that. That was the default option with the program. I think it's called Simple Backup.

---

### Post by solotwit on 2009-06-30
So I had to delete the /var/backup files with terminal, they weren't showing up in the filesystem view. I deleted all backup files in /var and now have plenty of free space on root.

This seems to have fixed youtube streaming videos as well.

[http://ubuntuforums.org/showthread.php?t=1191461](http://ubuntuforums.org/showthread.php?t=1191461)

I should also add the Applications - Accesories - Disk Usage Analyzer program shows my / drive as being beyond full. The Partition Editor program under System - Administration says I'm using about 1/5 of my / drive, which seems to be correct.

---

### Post by epicflux on 2009-07-09
I heart sudo du -SB 1M /  | grep -v "/home" | sort -n | tail -20

I have been out of space for a week now and doing all kinds of newbie dumb stuff to try to fix it.

It was also related to "simple" backup. I was backing up to an external usb drive, but I guess when the usb drive wasn't connected the file got created in a /media/USB1 directory.

So while I may have seen that it was a big file before, I just assumed it was on the USB drive, so it couldn't possiblely be the culprit, I didn't figure out that it was causing the issue till I disconnected the drive and ran the command, and it still showed up, I was able to delete it using sudo rm -rf /media/yada-yada

I think way to many people are out there telling newbies to boot-up with gparted and go to town. I also lost five hours of work time, with the benefit of creating a couple new useless partitions. Thank God I was too scared to start messing with that linux-swap thingy.

So here's my advice for a person dealing with the out of space issues.

Disconnect all external drives, remove storage cards, then run this command: sudo du -SB 1M /  | grep -v "/home" | sort -n | tail -20

Whatever big file shows up in that list should be suspect.

---

### Post by iliev on 2009-07-14
I had the same problem - in my case it was caused by the 'Simple Backup' program. When set on automatic backups to an external drive it does them (in /media/usb, or whatever is set) even if the external drive is not connected, which of course fills the / partition very quickly. This is easily fixed by deleting those backups, but finding them could be tricky - disconnect all your usb devises first and then search for large files as given above.

---

