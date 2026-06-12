---
title: "multiboot"
date: 2011-05-07
forum: Ubuntu Studio
---

### Post by fantab on 2011-05-07
I am new to Linux and Ubuntu. It has only been a couple of months since I am using Ubuntu Lucid Lynx_amd64  [LTS].

I have my LUCID installed on a separate HDD. I also use Windows 7 - X86 [only because of my familiarity with Graphics and Multimedia Software for Windows], which has its own dedicated HDD (dev/sda)

I want give Ubuntu Studio a try. I want to install Ubuntu Studio along with Lucid on the same HDD (dev/sdb).

My question to the forum is:

**Can I Install Ubuntu Studio 11.04_amd64 [Natty] along with Lucid [10.04.2 _amd64 LTS]? **

**If yes, then will there be any issues with GRUB because of different Ubuntu versions and different version numbers?**

In the same breath, can the forum be so good to tell me **what is the Ubuntu alternative to Window's _AutoPlay Media Studio_ (which is use to make CD/DVD Menus and Burn them)?**

Thanks.

---

### Post by jejeman on 2011-05-07
I have that setup Ubuntu 10.04 and Ubuntu Studio 11.04. Instaled on separate hdd. Each hdd have its own grub.
If you are using one hdd than just make separate partition for ubuntu studio instalation, use same swap, and don't install grub. Boot 10.04 and update grub, and you will have 11.04 on the list.

---

### Post by fantab on 2011-05-07
> **jejeman said:**
> 
If you are using one hdd than just make separate partition for ubuntu studio instalation, use same swap, and don't install grub. Boot 10.04 and update grub, and you will have 11.04 on the list.

Okay... So I make one Primary Partition (one logical for "/" and one for "/home" and no SWAP), is that correct?

and how do I NOT install GRUB and also how do I update it?

---

### Post by jejeman on 2011-05-07
> **fantab said:**
> Okay... So I make one Primary Partition (one logical for "/" and one for "/home" and no SWAP), is that correct?

and how do I NOT install GRUB and also how do I update it?

If you want separate home and already have swap partition from 10.04, than yes.
Ubuntu studio instaler will ask you, when time comes, do you want and where to instll grub. You just say no.

To update grub, boot 10.04 and issue folowing command
```
sudo update-grub
```

---

### Post by Pablo_F on 2011-05-07
> Okay... So I make one Primary Partition (one logical for "/" and one for "/home" and no SWAP), is that correct?
Sorry, no.

Please, can you show the terminal ouput of the following informative commands from your current ubuntu? Then we will see. Be patient.

**df -h**

**sudo parted**

(wait...)
**print**

(to quit parted: )
**quit**

Don't bother to use parted to actually partitionate the HD, imho gparted is much easier and the ubuntu installer also can do it. 

Cheers, Pablo

---

### Post by fantab on 2011-05-07
> **Pablo_F said:**
> Sorry, no.
Please, can you show the terminal ouput of the following informative commands from your current ubuntu? Then we will see. Be patient.
**df -h**
**sudo parted**
(wait...)
**print**
(to quit parted: )
**quit**

Okay I will be patient.. :)

I am attaching the ScreenShot of what you requested, please take a look. 

*NB : I want to Install Studio on /dev/sdb where I already have Lucid installed.*

---

### Post by Pablo_F on 2011-05-08
Hi, 

Sorry, I meant:

sudo parted /dev/sdb
print

Don't bother to attach a screenshot, just copy-paste the text. 

Cheers, Pablo

---

### Post by jejeman on 2011-05-08
> So I make one Primary Partition (one logical for "/" and one for "/home" and no SWAP), is that correct?
Sorry, I didnt read carefuly. It depends of your partition table setup, if it will be primary or logical partitions. You should know that / partition does not need to be primary.
you can list partitions also like this
```
sudo parted -l
```
and than copy just hdd of interest.

---

### Post by fantab on 2011-05-08
> ******@******-desktop:~$ **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              33G  3.3G   28G  11% /
none                  967M  348K  967M   1% /dev
none                  972M  332K  972M   1% /dev/shm
none                  972M   84K  972M   1% /var/run
none                  972M     0  972M   0% /var/lock
none                  972M     0  972M   0% /lib/init/rw
/dev/sdb6             162G  3.2G  151G   3% /home
******@******-desktop:~$ **sudo parted /dev/sdb**
GNU Parted 2.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) **print **                                                           
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

[COLOR=black]Number  Start   End     Size    Type      File system     Flags
 1      1049kB  35.8GB  35.8GB  primary   ext4            boot
 4      35.8GB  215GB   179GB   extended
 6      35.8GB  212GB   176GB   logical   ext4
 5      212GB   215GB   2449MB  logical   linux-swap(v1)
 [COLOR=Blue]2      215GB   429GB   215GB   primary   ext4[/COLOR]
 3      429GB   1000GB  571GB   primary   ext4[/COLOR]

(parted)     
Okay... I guess this is the Info you requested for the /dev/sdb. Please take a look. And it is the Partition in [COLOR=Blue]BLUE[/COLOR] where I intend to install Studio if it is all right to do so.

[Also be so kind to explain to me what the EXTENDED PARTITION means and how did it come to be there because I did not create it.]

---

### Post by jejeman on 2011-05-08
You can instal ubuntu studio on that partition (sdb2), but i dont see how you can make separate home partition. You realy dont need to do so, partition is big enough (215GB) to have both / and /home on it.

Well you did created extended partition, or instaler did, in order to have logical partitions. Extended partition is special type of primary partition in which one can make logical partitions. So, you can imagine it like a container for logical partitions.

---

### Post by fantab on 2011-05-08
> **jejeman said:**
> You can instal ubuntu studio on that partition (sdb2), **but i dont see how you can make separate home partition.** You realy dont need to do so, partition is big enough (215GB) to have both / and /home on it.

Are you, my friend, suggesting that I should NOT create a separate "/home" partition for Studio and instead use the existing '/home', just as your suggestion to use the same existing SWAP?

If that is the case then I will reduce the size of the Partition to 25%... 50Gb approx.

---

### Post by Pablo_F on 2011-05-09
Don't share homes. He is suggesting that you can install the whole system in /dev/sdb2, without a separate partition for /home in the ubuntustudio system.

If you want a separate partition for /home, you could change /dev/sdb2 from primary to extended, and create two logical partitions for ubuntustudio, one for / and the other one for /home. 

Cheers, Pablo

---

### Post by jejeman on 2011-05-09
I didn't said that you should not create home partition, but that i cant see how you would pull it off.
Your partition table looks like this (it's a little bit messy):
sdb1
sdb4 < sdb6 sdb5 >
sdb2
sdb3

well on second thought it looks that you can, because sdb2 and sdb4 are neighbours. You can resize sdb2 to max. 25GB and than resize sdb4 on the rest unallocated space and make sdb7 logical partition out of it. 

So your partition table would look like this:

sdb1
sdb4 < sdb6 sdb5 sdb7>
sdb2
sdb3

Don't use exiting home partition for the new instalation.
Backup all your important data before resizing and moving partitions.

In my former post I just wanted to say that it's easyer not to make separate home, to avoid all partition resize/moving stuff, (because you can loose data) and only have /. Your home folder will be on the same / partition. Ubuntu needs only / and swap to work. /home partition is optional.

---

### Post by fantab on 2011-05-10
> **jejeman said:**
> 
Your partition table looks like this (**it's a little bit messy**):
sdb1
sdb4 < sdb6 sdb5 >
sdb2
sdb3

well on second thought it looks that you can, because sdb2 and sdb4 are neighbours. You can resize sdb2 to max. 25GB and than resize sdb4 on the rest unallocated space and make sdb7 logical partition out of it. 

So your partition table would look like this:

sdb1
sdb4 < sdb6 sdb5 sdb7>
sdb2
sdb3

Thank you **jejeman  & Pablo_F** I will follow your instructions. And let you know here. You've said in your previous post that my Partioning is "little bit messy", could you then please tell me **what is the ideal or not messy partitioning of HDD?** Because when partitioning my HDD (/dev/sdb) I have only followed what has been said on these forums.
Please understand that I am new to Linux-Ubuntu and I am learning as I go along, so any help is more than Welcome.

---

### Post by jejeman on 2011-05-10
Partition is "messy" baecause the partition numbers are not in disk order. It's not a funcionality issue. If you list partitions with fdisk it will report you that. I really don't know if it afects anything.
Not "messy" one will look like this in youre case:
sdb1
sdb2 < sdb5 sdb6 sdb7>
sdb3
sdb4

I think that you don't need to worry about that.

---

