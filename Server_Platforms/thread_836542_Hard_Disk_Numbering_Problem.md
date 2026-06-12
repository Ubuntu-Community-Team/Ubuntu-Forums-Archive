---
title: "Hard Disk Numbering Problem"
date: 2008-06-21
forum: Server Platforms
---

### Post by cmwilliams on 2008-06-21
Hi

I have a slight problem with the way my drives are numbered (sda, sdb, etc)

I have 4 drives a 'main' boot drive with a small partition on which is marked as SDB and on the motherboard IDE primary master channel which has ubuntu server 8.04 on

a SATA/IDE PCI card with a SATA drive as SDA

a USB hard drive SDC

all works fine until i add an IDE hard drive to the SATA/IDE PCI card

then for some reason during boot (after the boot loader has loaded the first part of the OS) it stops working because my linux install is on SDB which for some reason when adding an additional drive to the SATA/IDE PCI card has become SDC, the additional drive is now SDB and the USB drive is SDD, therefor most of the OS cannot be found as its on SDC not SDB

my question is how do you re number the drives so i can continue adding drives on external cards and still have linux on a drive that isnt going to move names

also there is no real data on this system so a re format is ok if necessary

hope i explained myself fully

Cheers

Chris

---

### Post by doogy2004 on 2008-06-21
I have the same problem, i have a SCSI card with one disk on it.  I've learned to live with it, and change my configuarions to suit.  However when and application updates grub, it changes my hd(0,0) to hd(1,0).  So before I reboot I have to change all the grub entries to hd(0,0).

---

### Post by windependence on 2008-06-21
I don't believe there is any "graceful" way to solve this. It's hard to predict when you add hardware what the new detected config will be. You could change it manually but that requires booting from a boot disk and editing your fstab.

BTW, why are you switching hardware so often?

-Tim

---

### Post by Ng Oon-Ee on 2008-06-22
Actually, there IS a graceful way, involving editing the /boot/grub/menu.lst file.

Firstly, to explain, the sda/sdb/sdc labels depend on the order the drives are detected in BIOS (this I do not know for certain but have read in various threads), as such, they are not reliable (may change as you add drives, as you have already seen) in a system where drives are being added/removed on a regular basis.

Fortunately, when mounting your filesystem there are TWO ways to refer to the partition (not hard disk, the difference is pretty big, even if your hard disk only has one partition. /dev/sda refers to a hard disc, /dev/sda1 refers to the first partition on that hard disc) you are going to use. The first is to use /dev/sda1 which won't work if you add another disk that the bios recognizes as sda, which pushes your disk to /dev/sdb1.

The second method is using UUID (Universally Unique Identifier), which, as its name implies, is unique for a certain partition. When booting, we want our root ( / ) partition to be uniquely identified.

First, we have to find out what the UUID of the partition is. To do this, you need to identify the /dev/sd?? of our root partition. There are several ways, one of the easiest is to type in the terminal:-

```
mount
```

Quite a few lines will result, you're looking for the line that looks like this:-

```
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
```

Specifically, you're looking for the backslash ( / ) before the type, and after the name. Take note of that name (in my system, it is /dev/sda6);

Next, you need to find the UUID corresponding to that name, using:-

```
blkid
```

Once again, you'll get a bunch of lines, the one you're interested in starts with /dev/sda6 (or whatever your root partition's label is), as in this example:-

```
/dev/sda6: UUID="2bc9b814-818f-461c-9c33-0bc9ce584c52" TYPE="ext3" 
```

Copy out the line UUID="some number here" (from the letter U till the inverted commas. Easiest way is to select the test you wish to copy and use Ctrl-Shift-C (or go to the menu and click copy).

Next, you need to open menu.lst, the file responsible for the boot options you see in grub. First, make a backup, then open it in gedit for editing, as follows:-

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst
```

In the resulting file, scroll down till you see the following:-

```
## ## End Default Options ##

title		Linux Mint, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic

title		Linux Mint, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro single
initrd		/initrd.img-2.6.24-19-generic
```

So what we have to do there is replace the kernel location (the part following root=) with the UUID we found previously. I'd recommend first replacing the root location for the recovery mode as I show below here.

```
## ## End Default Options ##

title		Linux Mint, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic

title		Linux Mint, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=2bc9b814-818f-461c-9c33-0bc9ce584c52 ro single
initrd		/initrd.img-2.6.24-19-generic
```

The reason for doing that is so that your main boot is unaffected. Now go ahead and restart with your IDE drive plugged in (the condition which previously would have prevented you from booting). Select recovery mode. If you manage to reach the recovery mode menu (4 options if I remember correctly) with no errors, it means you've done everything right! You can then safely apply the same change to your main boot option, as below:-

```
## ## End Default Options ##

title		Linux Mint, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=2bc9b814-818f-461c-9c33-0bc9ce584c52 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic

title		Linux Mint, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=2bc9b814-818f-461c-9c33-0bc9ce584c52 ro single
initrd		/initrd.img-2.6.24-19-generic
```

Now, one thing to note is that the section of the menu.lst file that you've edited was created by the kernel itself, and will be over-written whenever you upgrade your kernel. Just reapply the steps here the next time a kernel upgrade comes out (which will replace your UUID with /dev/sda6 again.

---

### Post by windependence on 2008-06-22
While I agree this is great and I am thankful you posted it, I don't know if I could call it graceful. :)

Thanks anyway because I have been looking for a way to do this for quite sometime.

Kudos,

-Tim

---

### Post by cmwilliams on 2008-06-25
Hi All

Thanks for the replies

I will be trying the menu.lst way this weekend hopfully

> 
BTW, why are you switching hardware so often?

I am building a SAN using iscsi-target as I have alot of 3d models and textures, etc, as well as all the usual rubbish on my pc's and want a central point to store them, hence the upgradability 

and have had 2 HDD's stop working in less than a year (both replaced under warrenty and data recovered but still a pain)

Thank you once again - i always get a decent reply and information off this board

---

### Post by Ng Oon-Ee on 2008-06-26
> **windependence said:**
> While I agree this is great and I am thankful you posted it, I don't know if I could call it graceful. :)

Thanks anyway because I have been looking for a way to do this for quite sometime.

Kudos,

-Tim

Ah, yes, I suppose that would be true =).

I was thinking more 'graceful' in the sense of set-and-forget rather than '2 actions and you're done'.

Glad to know it helped. And yes, this board is a veritable mine of information.

---

