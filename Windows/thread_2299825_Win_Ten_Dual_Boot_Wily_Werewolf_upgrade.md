---
title: "Win Ten Dual Boot Wily Werewolf upgrade"
date: 2015-10-21
forum: Windows
---

### Post by MikeMecanic on 2015-10-21
If this can help those who try it.

Try to dual boot 10240 with Ubuntu many times in the past 4 months and I succeed most of the time.  Got the best result (fully stable) by creating only 3 partitions in something else: Root/Swap/Home.   Running Win 10.0.10240 Pro dual boot Vivid Vervet since almost 2 months now.  Got the upgrade to Wily at the end of September there (a 40 minutes one):

[http://itsfoss.com/ubuntu-15-10-beta-upgrade/?utm_source=newsletter&utm_medium=email&utm_campaign=linux_stories_this_week_at_its_foss](http://itsfoss.com/ubuntu-15-10-beta-upgrade/?utm_source=newsletter&utm_medium=email&utm_campaign=linux_stories_this_week_at_its_foss)

Grub is the main switch and is stable.  Wily is also stable.  

Under Win Ten, I split the HDD in 2 using Mini Tool Partition Wizard.  I created an ext4 partition of 233.33 GB that I split in 3 (Something Else).  This ext4 partition was seen by the Ubuntu installer.
I created an ISO Image of Vvid Vervet using Rufus 2.4.  It was not working with previous version.

Final partition result.  Left a 1 Gb partition (free space) just in case.  But you don't have to.

Wily@hp:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for wily: 
NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           698.7G            
&#9500;&#9472;sda1 ntfs     500M            System Reserved
&#9500;&#9472;sda2 ntfs   494.8G            
&#9500;&#9472;sda3 ext4    23.3G /          
&#9500;&#9472;sda4            1K            
&#9500;&#9472;sda5 swap     3.8G [SWAP]     
&#9492;&#9472;sda6 ext4   175.3G /home      
sr0            1024M            
wily@hp:~$ 

Got only one bug under Wily:  Was not able to import firewall profile in GUFW firewall (not 600 error).  Report the issue to the GUFW web site and they answer me immediately.  The solution was this terminal command (the .profile file was in the document folder)

```
sudo chmod 600 /home/wily/Documents/firewall17.profile

```

---

