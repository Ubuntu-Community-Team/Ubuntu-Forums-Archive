---
title: "Basic File/HD management issue"
date: 2011-02-07
forum: Server Platforms
---

### Post by mcarrara on 2011-02-07
OK this should be simple, but I don't know where to look.  My server has two Hard drives.  On one I have the system root (/) mounted.  on the other I have a folder /backups mounted.  The first hard drive is full.  I need to moves some directories to the other hard drive.  How do I do that? (I don't want them to be sub directories of /backups).

Mark

---

### Post by vanadium on 2011-02-07
One way is to partition the drive with backups and mount these partitions to some of the linux system directories.

For several linux system folders, symlinking these to a directory on your backup partition would also work.

---

### Post by trundlenut on 2011-02-07
What do you have on the root drive which has taken up all the space?

Both of my servers use a lot less than 10Gb for the root drive.  I have separate partitions for data and backups.

---

### Post by mcarrara on 2011-02-07
I wish I knew.  With Windows I know what the different folder contain and what I can and can not delete.  While I have been using Ubuntu for a few years I still don't have that knowledge.  My fault I know, I wish I could go through the drive and remove extra crap.

Mark

---

### Post by trundlenut on 2011-02-08
How much disc space are we talking about.  You could have a problem with has cuased a log file to become huge.

Assuming your using the server version of Unbuntu and you access to a machine running the desktop version you could use the tool for looking at discspace to find out what's hogging all the space.  Sorry I can't remember what the program is called, I have only windows machines to hand at the mo.

---

### Post by LightningCrash on 2011-02-08
cd /
du -x -m --max-depth=2|sort -n

This will tell you the disk usage of your root disk, summarized to two folders deep, in MB, and sorted.

---

### Post by LightningCrash on 2011-02-08
> **trundlenut said:**
> Assuming your using the server version of Unbuntu and you access to a machine running the desktop version you could use the tool for looking at discspace to find out what's hogging all the space.  Sorry I can't remember what the program is called, I have only windows machines to hand at the mo.

Baobab

Under Applications->Accessories->Disk Usage Analyzer

---

### Post by oldfred on 2011-02-08
A few more commands to try.

Partition sizes:
df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by trundlenut on 2011-02-09
> **LightningCrash said:**
> Baobab

Under Applications->Accessories->Disk Usage Analyzer

That's it!

Thanks...

---

### Post by mcarrara on 2011-02-10
I found out that there was 90gb of mail.  I thought I had mail turned off, but I guess processes still were emailing me and I never checked email on the server so it just piled up.  That's why my 100gb system drive was full.  Thanks for the help.

Mark

---

