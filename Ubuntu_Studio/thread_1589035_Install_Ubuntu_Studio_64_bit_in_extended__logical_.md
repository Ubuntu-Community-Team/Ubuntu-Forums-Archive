---
title: "Install Ubuntu Studio 64 bit in extended / logical partition(s)"
date: 2010-10-05
forum: Ubuntu Studio
---

### Post by Ventai on 2010-10-05
Hi there,

I already have 3 primary partitions with a Windows installation being used on my drive.

I'd like to add an Ubuntu Studio 64 bit installation to remaining  extended / logical partitions, if possible. 

The plan is as follows: - 

Grub Boot partition 128MB	- 	formatted as ext3	
Swap partition 6GB 		-	formatted as linux-swap?
Ubuntu install 20GB		- 	formatted as ext4? 
Logical partition 25GB		-	formatted as ext3 or ext4 for linux storage
Logical partition 25GB		- 	formatted as FAT32? (Not NTFS?) for Windows and Linux storage


Can anyone please confirm if this is viable, and would I need to do this in GParted before hand, or would the Unbuntu Studio installation handle all these partitions / filesystems?

---

### Post by cchhrriiss121212 on 2010-10-06
Seems viable to me, but I have never understood the benefit of a separate boot partition. I take it you have installed Ubuntu before and know that GRUB will write over the Win boot loader?

I would do things like this:
12GB as root ext4 (I have never needed more than 8GB with studio)
30GB as /home ext4
30GB as shared ntfs (Ubuntu can write and read to this)
4GB swap (you probably don't even need 4GB if you have enough RAM)

A separate root and home makes new installs easy. And yes, the installer can handle as much partitions as you like.

---

### Post by Ventai on 2010-10-06
Thanks for the reply. . 


I did do a test installation of Ubuntu Studio on the blank drive before installing Windows, however didn't have to worry as used the whole drive. 


Would that cause an issue then? Overwriting the Win boot loader. 

I was gonna have the (root?) Linux install partition as 20GB because my test install was about 5GB and I wanted room for manoeuvre. 

As I have understood; FAT32 operates better under Linux than NTFS. I'd need to confirm this. . 

Looking at this tutorial: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot), in the section 'Manual partitioning', it indicates that you should have a swap at least the size of your RAM. 

And lastly; would the Ubuntu Studio installer be able to format partitions as FAT32 and NTFS?


Any advice would be greatly appreciated. .

---

### Post by cchhrriiss121212 on 2010-10-06
> Would that cause an issue then? Overwriting the Win boot loader.
Not really, it is just something to be aware of if you want to remove Ubuntu and use only windows. The windows boot loader will need to be reinstalled if you want it back.
Why does it have to be overwritten? Because GRUB will recognise every OS, but the Windows boot loader will only show Windows.

If you have a spare drive then just use that, it will save you much dual boot config.

To clarify how linux partitions work:
root (shown as /) - holds the OS and all installed packages and programs, 20GB is fine but I would prefer a larger home to hold stuff like raw audio
home (shown as /home) - holds your files and settings
swap - I have 4GB RAM and have 4GB swap with an xp/'buntu dual boot, but I've never used more than 100MB swap, the official guides tend to be on the safe side

Installing a new Linux OS is easy as you can select to use the same home and overwrite your old root with a new one. There are more partition options like /mnt, /tmp and so on but I like to keep it simple.

> As I have understood; FAT32 operates better under Linux than NTFS. I'd need to confirm this. . 
I have only use NTFS, and had no issues reading and writing from my main disk or USB flash drives. Speed differences are minimal when I have compared them. Don't know how else it could be considered better.

---

