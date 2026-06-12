---
title: "cant install 12.04 LTS server edition on Intel server"
date: 2012-08-23
forum: Server Platforms
---

### Post by jchappy65 on 2012-08-23
I just downloaded Ubuntu Server 12.04 LTS.iso and correctly burned the iso using ImgBurn, PowerISO, Alcohol 120%, Nero, and Windows Image Burner. All burns were completely 100% successful with no errors and were all verified, no corruptions of any kind, yet the same error keeps happening.

Server Specs:

Intel Pentium 4T @ 3.0GHz
1GB RAM (2 x 512 MBs)
4 250GB Seagate SATA drives + 1 160GB Seagate (Can only setup to RAID 0,1,10)
ASUS P5GD2 Motherboard
ATI Radeon X300SE 128MB TVO Graphics Card (may swap with a Matrox P690 PCIe x16 Dual DVI Head)

So I put the DVD in, press F4 to setup my RAID, I deleted all previous RAID sets, create a new RAID set consisting of three drives and making it a RAID 0 (I tried to make a RAID 10 but apparently I lack a sufficient amount of drives, because the BIOS only sees three drives only, not sure why).

After the RAID is setup I then proceed to the DVD install, I select English, configure my keyboard, and the install begins, about a minute into the install when it's trying to grab "nic-firmware" it stops and says "installer failed to find file, please check CD/DVDs integrity, for it may be corrupted."

I press continue and click on Check CD/DVD Integrity and about 25% into the check it gives me an error saying: "The ./pool/main/m/manpages/manpages-dev_3.35-0.1ubuntu1_all.deb file failed the MD5 Checksum Verification. Your CD/DVD-ROM or this file may have been corrupted." and fails the test.

I have re-downloaded and re-burned 12.04 LTS 32-bit at least 5 times already and its the same message no matter which burn method I use, I swapped Burners, programs, CDs, DVDs, and even tried the 64-bit (obviously didnt work cause its not AMD).

How in the world can I bypass this check or just force the install to proceed?

---

### Post by darkod on 2012-08-23
1. Burn CDs on very low speed, like 8x or 10x. The verify doesn't always mean all is good since it tolerates certain amount of errors while the installer might be sensitive about it.

2. For a linux only server it might be better to use linux software raid and not the hardware raid. But that choice is up to you.

3. the amd64 images are also for Intel 64bit CPUs. AMD was the first to come up with 64bit and it remained to be called amd64. That's why you don't see Intel 64bit image.

4. No need to redownload the ISO, you can simply check the MD5 sum and see if it's correct. If not I recommend downloading from torrent since it checks for corruption during download.

---

### Post by jchappy65 on 2012-08-23
> **darkod said:**
> 1. Burn CDs on very low speed, like 8x or 10x. The verify doesn't always mean all is good since it tolerates certain amount of errors while the installer might be sensitive about it.

I burned all the discs at 4x, 6x, and 8x, max for me is 20x which i know is too fast. But thanks, I'll keep it at 8x.

> **darkod said:**
> 2. For a linux only server it might be better to use linux software raid and not the hardware raid. But that choice is up to you.

Does the linux software RAID come packaged with the install disc or do i need to setup RAID after the install with another piece of software?

> **darkod said:**
> 3. the amd64 images are also for Intel 64bit CPUs. AMD was the first to come up with 64bit and it remained to be called amd64. That's why you don't see Intel 64bit image.

Oh, I just gave it a try and it just gave me kernel panics, so i guess I have a 32-bit system then...understood.

> **darkod said:**
> 4. No need to redownload the ISO, you can simply check the MD5 sum and see if it's correct. If not I recommend downloading from torrent since it checks for corruption during download.

...Link to recommended torrent?

---

### Post by darkod on 2012-08-23
The Alternate Install CD (image) has the mdadm software raid package included for desktops installs.
The Server image has it included too.

When doing the manual partitioning, on all disks members of the raid you create identical partitions for all your ubuntu partitions that you want to have. Create this partitions as Physical device for RAID, not as ext4. After that you select the Configure Software RAID option above the partitions/disks listing.

That will allow you to create as many /dev/mdX devices as you want. It will ask you for raid level, and which partitions to include. Note that in the text installer, you select with Space, not by hitting Enter.

Once you have the md devices created, they will appear in the partitions listing too. There you select them, and then choose what filesystem you want on them and the mount point.

You have all download links here, including the .torrent ones. Just watch out to select the correct, you seem to want -server-i386 for 32bit.
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by jchappy65 on 2012-08-23
I tried both torrents of the original & the alternate Images and the MD5 checksum was correct for both and I still get the same error!

It always hangs up when loading "nic-firmware" in the "Load installer components from CD" stage.

---

### Post by sandyd on 2012-08-23
Have you tried swapping in another cdrom drive?

Damaged CD/DVD-ROM drives can produce some weird results ;)

---

### Post by Random20210831 on 2012-08-23
Have you tried to replace ODD? Maybe it is a problem (may be incorrectly)? You can check if the ODD is fully functional. It is also possible that the DVD that you burned system is damaged.

---

### Post by jchappy65 on 2012-08-23
the DVD drive was the problem, swapped out an IDE CD drive with a SATA DVD Drive and it worked.

Now this server will act as my web server, connecting and transferring files between Windows and Ubuntu Machines, which file system should I choose? does it matter if I pick Ext4 over Fat32?

---

### Post by jchappy65 on 2012-08-24
Okay So I got the server up and running.

I am primarily using this server as a home media and print server. when I was prompted for what kind of software I would like installed I went ahead with the samba file server. I kind of got a little trigger happy and pressed enter before i selected the print server, now how would i go about installing the print server side of this server?

---

### Post by darkod on 2012-08-24
Log into the server and at any time you can run the task selector with:
sudo tasksel

That should open the same window as during install.

---

### Post by d4m1r on 2012-08-24
> **jchappy65 said:**
> Okay So I got the server up and running.

Cool, mind posting how? It might help other people who have the same issue...

---

### Post by jchappy65 on 2012-08-24
> **d4m1r said:**
> Cool, mind posting how? It might help other people who have the same issue...

sorry, I really didnt connect those last two posts, I fixed my main issue of not being able to proceed with the install by swapping my DVD drives, from IDE to SATA drives.

---

### Post by jchappy65 on 2012-08-24
> **darkod said:**
> Log into the server and at any time you can run the task selector with:
sudo tasksel

That should open the same window as during install.

It actually opened up an even better list of software to install. during installation I was only able to install about 5 or 6 of the items this command brought up.

Which now brings me to a new question: how will the Ubuntu Cloud Image affect my server and what all will it add?

---

