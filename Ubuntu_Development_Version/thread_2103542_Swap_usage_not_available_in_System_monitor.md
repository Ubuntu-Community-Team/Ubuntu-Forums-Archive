---
title: "Swap usage not available in System monitor"
date: 2013-01-10
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-01-10
I was just wondering why this is not showing swap usage in Raring.
Conky shows the same thing - no usage.

[IMG]http://ubuntuforums.org/picture.php?albumid=1580&pictureid=8557[/IMG]

---

### Post by dino99 on 2013-01-11
mine works on RR i386 logged as gnome-classic

---

### Post by zika on 2013-01-11
RR amd64 (currently in awesome) works fine, shows 0 usage of existing (and in use) swap...
(to use a moment when something do work, audacious [COLOR=#2D4038][COLOR=Black]effrontery on my side...[/COLOR] ;))[/COLOR]

---

### Post by plucky on 2013-01-11
Check your swap partition is active and mounted.

Post output for```
free -m
sudo blkid
cat /etc/fstab
```


Good Luck

---

### Post by VinDSL on 2013-01-11
Working OK here, too...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-jan-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-jan-2013-1.png")[/INDENT]


Maybe the "trick" is to have 1 GiB RAM.  LoL!  :D

---

### Post by zika on 2013-01-11
> **VinDSL said:**
> Working OK here, too...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-jan-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-jan-2013-1.png")[/INDENT]
Maybe the "trick" is to have 1 GiB RAM.  LoL!  :DNo, there is difference between "0 used" and "not available"...

---

### Post by Cavsfan on 2013-01-11
> **plucky said:**
> Check your swap partition is active and mounted.

Post output for```
free -m
sudo blkid
cat /etc/fstab
```Good Luck

```
cavsfan@cavsfan-MS-7529:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       1265       2688          0         64        567
-/+ buffers/cache:        633       3320
Swap:            0          0          0
cavsfan@cavsfan-MS-7529:~$ 
``````
cavsfan@cavsfan-MS-7529:~$ sudo blkid -c /dev/null -o list
[sudo] password for cavsfan: 
device                                       fs_type         label            mount point                                      UUID
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                    ntfs            C:               (not mounted)                                    1CFC7A8DFC7A60C6
/dev/sda2                                    ext4            Lucid            (not mounted)                                    a162dc8a-e4df-4b79-b4c3-524761ff7ae1
/dev/sda3                                    swap                             (not mounted)                                    2a80f59e-e7c3-418e-aab2-ab5d19255a2f
/dev/sda5                                    ext4            Precise          (not mounted)                                    3b8b1954-24e6-4a5e-9074-70a1a94ed4be
/dev/sda6                                    swap                             (not mounted)                                    82c51b29-023f-4964-99b6-67b45a49527f
/dev/sda7                                    ext4            Quantal          (not mounted)                                    b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
/dev/sda8                                    swap                             (not mounted)                                    69ac3efc-8a8a-4056-89e0-59bb81c2f468
/dev/sda9                                    ext4            Raring           /                                                a6b7ac97-488f-4e87-b6af-247fcbf6df77
/dev/sda10                                   swap                             (not mounted)                                    d7f4c67e-2630-421d-af03-f1f2294d14fe
/dev/sdb1                                    ntfs            Fantom           /media/cavsfan/Fantom                            78B8D1A1B8D15DE6
cavsfan@cavsfan-MS-7529:~$ 
``````
cavsfan@cavsfan-MS-7529:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=a6b7ac97-488f-4e87-b6af-247fcbf6df77 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=3b1bb9db-4c8f-439a-b02a-f38a5f6ee573 none            swap    sw              0       0
cavsfan@cavsfan-MS-7529:~$ 
```First of all thanks for all of the replies! :D

I see that fstab is correct (sda10) but, the swap file is not mounted according to blkid.

In Gparted I turned swapon and it mounted. It is only one GB but, it shows 0 used of 1GB.
I'll try rebooting and see if it stays mounted.

---

### Post by cariboo on 2013-01-11
You really don't need a different swap partition for every different install. I use the manual partition option, and the swap partition is always detected even if it's own a differen thard drive.

---

### Post by deadflowr on 2013-01-11
Your swap UUIDs don't match. 
I'd simply edit the fstab file and remove the swap UUID and replace it with the one for sda10.

---

### Post by Cavsfan on 2013-01-11
> **cariboo907 said:**
> You really don't need a different swap partition for every different install. I use the manual partition option, and the swap partition is always detected even if it's own a differen thard drive.

Duh! (me) I edited the fstab to get rid of all the other swapfiles it pulled in when I re-installed Raring and only paid attention to sda10.
I did not look at the UUID which was wrong. I corrected it, rebooted and now it is mounted. 
I wondered why I kept getting a quick error at bootup about UUID d7f4c67e-2630-421d-af03-f1f2294d14fe not being mounted!
It was because it was the wrong UUID! D'oh!

I like your approach **cariboo907**, is there anything I need to do to use the manual partition option? I setup 4 GB on a primary partition for my first Ubuntu install which is now Lucid.
Could I just edit each installations fstab and point them all to that one making sure I get both the sdax and the UUID correct?

Thanks to all of you! :D

---

### Post by Cavsfan on 2013-01-11
> **deadflowr said:**
> Your swap UUIDs don't match. 
I'd simply edit the fstab file and remove the swap UUID and replace it with the one for sda10.

You guys are good! I also noticed that and fixed it and it mounted.
Thanks! :D

---

### Post by Cavsfan on 2013-01-11
I hate having to learn the same lesson more than once. But, at least I had fun. ;)

I got rid of my other swap files and trimmed the swap on the primary partition from 4GB to 1GB. I have never seen 2k used on any of my Ubuntus.
I have 4GB of memory and it suspends and wakes just fine.

Then I reboot. Whoops! I'm looking at grub rescue because I had my grub installed on Raring. ):P I hate when that happens: I forget to install my grub on my main Ubuntu.

Luckily I have been there before and used my Lucid install disk to recover. It worked better than my Quantal disk which kept giving me errors about something missing.

So I gained a little disk space and reduced the number of partitions.

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid -c /dev/null -o list
[sudo] password for cavsfan: 
device                 fs_type   label      mount point                UUID
-----------------------------------------------------------------------------------------------------------
/dev/sda1              ntfs      C:         (not mounted)              1CFC7A8DFC7A60C6
/dev/sda2              ext4      Lucid      /media/cavsfan/Lucid       a162dc8a-e4df-4b79-b4c3-524761ff7ae1
/dev/sda3              swap                 <swap>                     2a80f59e-e7c3-418e-aab2-ab5d19255a2f
/dev/sda5              ext4      Precise    (not mounted)              3b8b1954-24e6-4a5e-9074-70a1a94ed4be
/dev/sda6              ext4      Quantal    (not mounted)              b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
/dev/sda7              ext4      Raring     /                          a6b7ac97-488f-4e87-b6af-247fcbf6df77
cavsfan@cavsfan-MS-7529:~$ 

```

Makes me wonder if we even need swap files any more.
Guess I'm cured now. Thanks!

---

### Post by Cavsfan on 2013-01-11
> **VinDSL said:**
> Working OK here, too...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-jan-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-jan-2013-1.png")[/INDENT]Maybe the "trick" is to have 1 GiB RAM.  LoL!  :D

That must be it! LoL! I see you are using swap and I have never seen any swap used here. :D

---

### Post by VinDSL on 2013-01-11
> **Cavsfan said:**
> I see you are using swap and I have never seen any swap used here. :D

You can always play around with your swappiness settings, so called.  :)

I run the following, at the bottom of my sysctl.conf file (/etc/sysctl.conf)...

```

# For Avast!
kernel.shmmax=100000000
#
# Cannot leave things alone
[B][COLOR="DarkRed"]vm.min_free_kbytes = 65536
vm.overcommit_memory = 1
vm.overcommit_ratio = 100
vm.dirty_background_ratio = 5
vm.dirty_ratio = 5
vm.swappiness = 99[/COLOR][/B]
#
# Cannot leave these alone either
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
#

```

That should make your swap meter move...  ;)

**EDIT**

Er... I suppose it goes without saying, but...

You'll need to do a restart, after editing this file, in order for the changes to take affect.

---

### Post by Cavsfan on 2013-01-12
> **VinDSL said:**
> You can always play around with your swappiness settings, so called.  :)

I run the following, at the bottom of my sysctl.conf file (/etc/sysctl.conf)...

```

# For Avast!
kernel.shmmax=100000000
#
# Cannot leave things alone
[B][COLOR=DarkRed]vm.min_free_kbytes = 65536
vm.overcommit_memory = 1
vm.overcommit_ratio = 100
vm.dirty_background_ratio = 5
vm.dirty_ratio = 5
vm.swappiness = 99[/COLOR][/B]
#
# Cannot leave these alone either
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
#

```That should make your swap meter move...  ;)

**EDIT**

Er... I suppose it goes without saying, but...

You'll need to do a restart, after editing this file, in order for the changes to take affect.

I added that to /etc/sysctl.conf, rebooted and still no action in the swappiness. 
Surfed a few websites, played a song on Banshee, played a youtube video and still nothing. 
Am I finding that swap files may not be necessary if you have like 4GB or more?

[[IMG]http://ompldr.org/taDFycw[/IMG]]("http://ompldr.org/vaDFycw")

You think? Shirley not! :D

---

### Post by zika on 2013-01-12
I can still clearly remember times when we were complaining about swapping (hence the name of EMACS (Eight Megabytes And Constantly Swapping))... Nowadays complaints are because swap is not (yet) used...

---

### Post by Cavsfan on 2013-01-12
> **zika said:**
> I can still clearly remember times when we were complaining about swapping (hence the name of EMACS (Eight Megabytes And Constantly Swapping))... Nowadays complaints are because swap is not (yet) used...

That's a good one! LOL! :D

I wonder if anyone can verify with certainty that a swap file is indeed needed in 2013.

---

### Post by VinDSL on 2013-01-12
> **Cavsfan said:**
> Am I finding that swap files may not be necessary if you have like 4GB or more?
That's probably the case.

I have a Linux laptop with 4 GiB RAM, and a Linux netbook with 2 GiB RAM, and I've never seen the swap meter move, regardless of what I'm doing.

This 1 GiB desktop machine is constantly swapping.

I occasionally max it out.  It doesn't crash, per se, but gets horribly slow and unresponsive, until I start closing programs down.

So, yes, for some of us, swap is paramount.  For others, it's left as an exercise in the second-order coefficient.  LoL!  :D

---

### Post by zika on 2013-01-13
> **Cavsfan said:**
> That's a good one! LOL! :D

I wonder if anyone can verify with certainty that a swap file is indeed needed in 2013.I have 4GB... Occasionally I can see swap usage. Since I'm most of the time in awesome, fvwm, spetrwm, I do not use so much memory... But when I fire up GS, Unity or such, I'm able to provoke that... I also have vm.swappiness=0 most of the time, so...
Also, there is no proper hibernate without proper swap...

---

### Post by Cavsfan on 2013-01-13
> **VinDSL said:**
> That's probably the case.

So, yes, for some of us, swap is paramount.  For others, it's left as an exercise in the second-order coefficient.  LoL!  :D

I'd have to agree! :D So, I'll leave all my 'Buntus using the same 1GB as swap just because...

> **zika said:**
> I have 4GB... Occasionally I can see swap usage. Since I'm most of the time in awesome, fvwm, spetrwm, I do not use so much memory... But when I fire up GS, Unity or such, I'm able to provoke that... I also have vm.swappiness=0 most of the time, so...
Also, there is no proper hibernate without proper swap...

I have no problem "suspending" the PC but, I never cared about using the hibernate option.
Suspend is exactly like "sleep" in Windows 7 and that is what I want, although Ubuntu (all versions) go to sleep in less than 10 seconds while windows takes 2-3 times that amount of time.
Windows has what is very similar to a swap file called a *pagefile*.
If you let the PC control how much it needs it can become gargantous but, I found I can get by with giving it 300MB and it goes to sleep just fine.

BTW, while I was resizing and moving partitions with Gparted the other day it was almost as slow as windows defragmenting, which is slooooooooooow!
Glad Ubuntu doesn't need to be defragmented. ;)

Oh, if you have a windows OS and have to defragment, that User Journal file ($UsnJrnl$) will get very huge and fragmented and will not defragment at all. 
This will greatly speed that process up if you do this before hand.
To open a terminal window, press the "Windows key" and the letter &#8220;R&#8221;.
You will see the "Run Dialog Box". Type "cmd", and press "OK".
Delete the $UsnJrnl$ by entering **fsutil usn deletejournal /n C:** and wait until the prompt comes back.
Then defragment (hopefully using Defraggler instead of what comes with windows).
Instead of taking 2 days and not really finishing defragmenting the whole drive, it will complete pretty fast in comparison and do it well.
The user journal file will just rebuild itself after a reboot.

I know a tab more about windows than I do about Linux/Ubuntu but, learning is fun. \\:D/

---

### Post by VinDSL on 2013-01-13
> **Cavsfan said:**
> BTW, while I was resizing and moving partitions with Gparted the other day it was almost as slow as windows defragmenting, which is slooooooooooow!
I defrag winders machines (dual booters) with Auslogics Disk Defrag -- been using it for years:

[INDENT][http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)[/INDENT]

It actually moves along fairly fast. ;)

---

### Post by Cavsfan on 2013-01-13
> **VinDSL said:**
> I defrag winders machines (dual booters) with Auslogics Disk Defrag -- been using it for years:[INDENT][http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)[/INDENT]It actually moves along fairly fast. ;)

They are both rated about the same. I have used defraggler for a few years. It is made by Piriform.
Do you also use CCleaner (made by Piriform too) to clean cache, cookies, temp files and many other stuff too numerous to name here.
I used to hate how the program list in Windows is just random and not in alphabetical order but, on CCleaner there is an option to sort the program list. 
There is also a good registry cleaner that finds obsolete entries and will delete them if you give it the OK.
I have looked at friends windows computers that were slow and found like 5,000 or more invalid/obsolute registry entries. 
Cleaned them up and the other stuff and they were very thankful. :D
As a matter of fact I have seen brand new computers with that many invalid/obsolute registry entries.
I run CCleaner daily on any one's profile that is/has been logged on.

It used to be called crap cleaner and they changed it to CCleaner. Works like nobody's bizness! :wink:

---

### Post by cariboo on 2013-01-13
This thread is starting to drift off course, even though it's marked as solved can we please keep it on topic.

---

### Post by Cavsfan on 2013-03-19
> **cariboo907 said:**
> You really don't need a different swap partition for every different install. I use the manual partition option, and the swap partition is always detected even if it's own a different hard drive.

This was great advice **cariboo907**! I have one 1GB swap file now and it's still unused but, that makes installations easier and fstab doesn't pull in 4 swap UUIDs any more. :D

---

