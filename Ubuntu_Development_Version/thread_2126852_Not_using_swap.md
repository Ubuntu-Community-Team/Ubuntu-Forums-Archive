---
title: "Not using swap"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by Chelidze on 2013-03-18
Ok yesterday I was ruining games under wine and editing videos in kdenlive at the same time but what I noticed that I was getting serious lag that I did not get before, today I started ubuntu and I noticed that system is not using swap at all what I mean by this is that swap file size is written ,,0" in "free -m" and in system monitor "not available" how do I mount swap partition ??

Thank you in advanced

---

### Post by zika on 2013-03-18
> **Chelidze said:**
> Ok yesterday I was ruining games under wine and editing videos in kdenlive at the same time but what I noticed that I was getting serious lag that I did not get before, today I started ubuntu and I noticed that system is not using swap at all what I mean by this is that swap file size is written ,,0" in "free -m" and in system monitor "not available" how do I mount swap partition ??

Thank you in advancedDid You try (first) with```
sudo swapon -a
```...?

---

### Post by Chelidze on 2013-03-18
Thank you for the reply 
this is what I got

```
cannot find the device for UUID=237fafd6-9284-44d4-b7c5-a253846a7288
```

what happened before yesterday everything was working ??

---

### Post by cariboo on 2013-03-18
What does:

```
swapon -s
```

tell you?

---

### Post by Chelidze on 2013-03-18
> **cariboo907 said:**
> What does:

```
swapon -s
```

tell you?

```
Filename				Type		Size	Used	Priority



```

this is what I got 

I have a question what is SpeedStor ??

---

### Post by dino99 on 2013-03-18
check the swap uuid inside /etc/fstab

list uuids:
sudo blkid

---

### Post by schragge on 2013-03-18
If you've installed another Linux distribution that shares  the swap partition with your Ubuntu, the installation program could reformat the swap partition thus assigning it another UUID. In this case Ubuntu cannot find it anymore as it is referenced in /etc/fstab by the old UUID. Compare the output of the commands:
```
sudo blkid -t TYPE=swap
``` and ```
findmnt -st swap
```

---

### Post by Chelidze on 2013-03-18
> **dino99 said:**
> check the swap uuid inside /etc/fstab

list uuids:
sudo blkid

```
/dev/sda1: UUID="A274AD5474AD2BCB" TYPE="ntfs" /dev/sda2: UUID="1A0293A402938383" TYPE="ntfs" 
/dev/sda3: UUID="BEEA60D8EA608E89" TYPE="ntfs" 
/dev/sda5: UUID="70015310-a958-4b94-9469-51a314962984" TYPE="ext4" 



```

 I think I know the cause of this problem I think two month ago I took out my second ntfs hdd I do not remember what happened I installed something or did something but I remember that I had to use  [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair") from live ubuntu 12.04 cd  to use my pc, yesterday ubuntu asked me if it was ok to update grub mane or something I always press keep the old one but yesterday I pressed yes replays or something . 
now I started Gparted 
this is what it is telling me on the start 
```
Invalid partition table on /dev/sda -- wrong signature 3839.
```
if I press ignore this pops 
```
Invalid partition table on /dev/sda -- wrong signature 3839. 
```
if I press ignore this is what it tells me 
```
Error informing the kernel about modifications to partition /dev/sda4 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda4 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
```

and then when It starts the software it shows the swap space as uneducated space 

should I press new and create swap if this is possible at all ??

---

### Post by dino99 on 2013-03-18
inside gparted, select the faulty partition, and from the menu, select to repair the table (but dont format that partition, otherwise backup first)

note: a new uuid is created each time a device is plugged/unplugged, so you need to update grub also, otherwise it cant know the new uuid.

---

### Post by Chelidze on 2013-03-18
> **dino99 said:**
> inside gparted, select the faulty partition, and from the menu, select to repair the table (but dont format that partition, otherwise backup first)

note: a new uuid is created each time a device is plugged/unplugged, so you need to update grub also, otherwise it cant know the new uuid.

Sadly I can not find that option "repair"

---

### Post by dino99 on 2013-03-18
Third tab : devices (or so)
First line: create a partition's table (or so)

---

### Post by Chelidze on 2013-03-18
> **dino99 said:**
> Third tab : devices (or so)
First line: create a partition's table (or so)

 Still can not find it 

[IMG]http://i.imgur.com/xYXOW5S.jpg[/IMG]

[COLOR=#ff0000]**I think I managed to fix this**[/COLOR] I created a new swap partition and then edited the [COLOR=#ff0000]**[FONT=Ubuntu Beta]fstab[/FONT]**[/COLOR]

---

### Post by dino99 on 2013-03-18
i can see "Create Partition Table..." on the screenshot above (5th); so you might see it too i suppose  ;)

---

### Post by Chelidze on 2013-03-18
> [COLOR=#000000]inside gparted, select the faulty partition, and from the menu, select to [/COLOR][COLOR=#ff0000]repair[/COLOR][COLOR=#000000] the table (but dont format that partition, otherwise backup first)[/COLOR]

[COLOR=#000000]note: a new uuid is created each time a device is plugged/unplugged, so you need to update grub also, otherwise it cant know the new uuid.[/COLOR]

I was looking for [COLOR=#ff0000]repair, [/COLOR][COLOR=#000000]&#8203;mixed communication i guess :) 
any way I would like to thank every one for the help :)
 
[/COLOR]I want to mark this thread as solved but can not find this in thread tools did they change something in policy

---

### Post by ronacc on 2013-03-18
in gparted rt click on help then lt click on contents then recovering partition tables , there is a link ther that will take you to the site for testdisk , see the step by step instructions .

---

### Post by Chelidze on 2013-03-18
[**[COLOR=#000000]ronacc[/COLOR]**]("http://ubuntuforums.org/member.php?u=80744")[COLOR=#000000][/COLOR]

Thank you for the reply but I think I fixed it already :)


** Admin Can you mark this thread as solved **

---

### Post by ronacc on 2013-03-18
if you didn't have anything important in swap , the way you did it ( create a new swap and edit fstab ) is the easiest way . On my box with 4 gb mem I have NEVER seen swap used , I have multiple installs and use one swap for all of them .

---

### Post by AndersAA on 2013-03-19
Slightly off topic, but if you ever hit the swap, install zram-config. It'll compress things in memory before hitting the swap, MASSIVLY improving performance (as swap is very very slow).

(Side note, I got 16gb ram, and regularly hit swap. It all depends on what your doing.. in my case, machine learning ;) ).

---

### Post by Chelidze on 2013-03-19
> **AndersAA said:**
> Slightly off topic, but if you ever hit the swap, install zram-config. It'll compress things in memory before hitting the swap, MASSIVLY improving performance (as swap is very very slow).

(Side note, I got 16gb ram, and regularly hit swap. It all depends on what your doing.. in my case, machine learning ;) ).


wow really did not know any thing about this so thank you for the information I might give it a go one day

---

### Post by zika on 2013-03-19
Did ZSwap (not to confuse with ZRAM) enter 3.9 kernel?

---

### Post by rrnbtter on 2013-03-19
Greetings,
Not related to original OP but with 4gig of RAM less alloted video I don't use my swap anyway. Since $Home is encrypted my swap didn't setup properly during installation. As a solution I set my swapiness to 10 instead of the default 60 and just don't use a swap file.  Results, smooth, fast system. I don't know where the limits are but my wife has half the ram at 2gig less video, I set it to the same swapiness of 10 and it runs fine without the swap file. I do acknowledge that she doesn't put the demand on the system that I do. FYI

---

### Post by jerrylamos on 2013-03-20
Just put SSD solid state hard drives in a netbook and a notebook.  For what I do, I didn't see much memory constraint when running the command free.
Flash memories do wear out with high write activity.  So not knowing if the SSD are as sensitive to write so I'm not running a swap partition.  In the past some linux's seemed to do a lot of fussing with swap whether they needed to or not.  In contrast the small distro puppy seems to rn in memory altogether writing optionally at shutdown.  Haven't run puppy lately.

---

