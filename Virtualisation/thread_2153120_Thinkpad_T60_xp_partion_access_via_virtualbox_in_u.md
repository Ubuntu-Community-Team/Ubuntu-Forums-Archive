---
title: "Thinkpad T60 xp partion access via virtualbox in ubuntu 12.04 Desktop"
date: 2013-06-10
forum: Virtualisation
---

### Post by chendke on 2013-06-10
Hi Guys,
 Before you stone me to death for violating the cardinal rule of posting a new thread for an existing topic namely 

[http://ubuntuforums.org/showthread.php?t=769883]("http://ubuntuforums.org/showthread.php?t=769883")

Let me explain the situation.

I have a T60 with an xp installation which I am not supposed to modify as much as possible for policy reasons. That means no installation of software on xp including changing the bootloader. There was however some empty space in the hard disk. So I installed ubuntu 12.04 in an ext4 partion with a small swap using the ubiquity -b option which did not install the bootloader. I searched several forums and based on what little I understood, I created an ubuntu install on a small 4GB pendrive whose Grub can see my disk and I can boot into the ubuntu partition by changing the bios boot sequence and using the flashdrive as a key. If I do not change the boot order, The machine loads XP as usual with no challenge.

The reason this history is significant is that I have no Grub on my sda with winxp on sda1 and ubuntu on sda7.
The grub resides on my sdb[flash drive]

I need to use the exchange mail configured on my xp so I decided to open my physical partition of XP in a virtualbox in Ubuntu. I had done this previously [2008 ] with VMware server on ubuntu in an MSI wind machine but it had grub as the bootloader. And it worked well except I could never get the sound to work.

Now I followed the instructions mentioned in the link previously [sans grub related part] with and without the option of using the fake MBR, playing with sda and sda1 partition in the createvmdk command even doing the painful modification of hardware profiles in xp, But I was stuck 

```
MBR

A disk read error occurred
Press Ctrl+Alt+Del to restart
```

I saw a similar issue on the 20th page of the thread where they modified the vmdk file as follows

>  Originally Posted by borikru  
I had the same problem with my Thinkpad t60p.
1) After trying many solutions, I noticed that disk geometry reported by fdisk before Windows is installed is different from geometry reported after Windows XP was installed *running fdisk from LIVE CD). This led me to investigate how disk geometry might cause problems, and as a matter of fact, most posts on this matter say geometry should not be an issue. However, I tried to tweak geometry setting in the .vmdk file and it worked. Windows XP booted from physical partition on Thinkpad T60p.

Entries that I changed in the .vmdk file:
ddb.geometry.biosCylinders="12921"
ddb.geometry.biosHeads="240"
ddb.geometry.biosSectors="63"

The numbers correspond to how Windows discovered the geometry (same as reported by fdisk after windows overwrites the MBR). 
I believe this has something to do with LBA mode, which I cannot change in the BIOS on Thinkpad T60p.
It seemed to have worked for them but its a nogo for me.

I checked with fdisk and got the biosCylinders value and used 240 for biosHeads: still stuck with the same error. 

The only difference I found was when I use the Fake MBR I get the error mentioned above and when I do not use the fake MBR in CreateVMDK statement and give it SDA I don't get the first line just 

```
A disk read error occurred
Press Ctrl+Alt+Del to restart
```

Is grub a must for me to be able to use vbox ?  I figured not installing grub would actually benefit me as the windows MBR on sda would not direct the boot to ubuntu   partition even inadvertently as the ubuntu is in an extended partition with ext4 which is practically invisible to xp. Please guide me to understand  what I should be doing

Thanks in advance

Andy

Couple of things I missed in the initial post :
the settings in the vmdk file seem to revert to biosheads = 16 everytime the virtualbox is run 
 tried changing the ide settings as well. Do I need to create a sata storage connecter if so how ?

---

