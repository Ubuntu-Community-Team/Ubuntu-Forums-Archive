---
title: "Supermicro X7DA3 hardware raid 10"
date: 2009-02-17
forum: Server Platforms
---

### Post by alkisx on 2009-02-17
Hello to everyone this is my first post.

I used to install slackware on my servers for years now. Never had any problem with slackware to identify tha raids on them.

Now I decided to install ubuntu server 8.10 64bit on a new server (motherboard stated on topic).

I've setup hardware raid 10 using the bios, using 4 disks 500GBytes for the raid and one more the same as a hot spare disk. Summary: 5 disks (4 on raid and 1 hot spare).

The raid is totally about 945 GBytes in size (on bios).

The controller for the raid I used is the onboard Adaptec.


I boot with the ubuntu server 64bit cd, but when it comes to partitioning I see only on 500GBytes disk available (possibly the spare one?), and nowhere the raid, which as I said is about 945 GBytes, although, before screen goes to partitioning, I get a message that says "raid configuration has been found", and of course I choose yes to enable it.


Maybe I need to point to different kernel image on cd boot? If yes, is there anyone knows?

Also, I don't want to user software raid, only hardware.

Thank you in advance for your help!:)

---

### Post by cariboo on 2009-02-17
Have  a look at the [FakeRaid]("http://help.ubuntu.com/community/FakeRaidHowto") howto.

Jim

---

### Post by alkisx on 2009-02-17
Is this a fakeraid? Althoug I was suspecting this. On booting with slackware 12.2 it sees all 5 disks as separate disks.
If you are sure it is a fake raid please tell me so.

Thank you very much

---

### Post by alkisx on 2009-02-17
Followed your instructions (the link), used the alternate cd, but on the partition section of installation, it still shows me one disk to partition.

Any help please?

---

### Post by fjgaude on 2009-02-17
Did you setup the four drives for raid10 using the BIOS of the motherboard?

---

### Post by alkisx on 2009-02-17
Yes I did.

Actually I started using the 2nd method from the above given link. Booted with the desktop version as live, and when I reach partitioning, I could see all 5 disks (4 + 1 hotspare), but it was saying that only the first disk was in raid. Strange.

Should I disable or delete arrays from the bios?

Also I realized that is the spare drive that it finds as a raid!! This is on more strange thing. It leaves the 4 raid disks /dev/sda ,sdb, sdc, sdd as independent drives (I am sure these are the raid as I did it from bios), and it presents me one disk, the hot spare one (/dev/sde) as being a raid!

---

### Post by fjgaude on 2009-02-17
ASAIK, Linux cannot correctly know about this fakeRAID... the only program that might permit using the array setup in BIOS is **dmraid**.

It's in the repository. Install it using **apt-get** and then read its man pages.

---

### Post by alkisx on 2009-02-17
I followed the instructions and got dmraid already.

Ok, maybe I am missing something. I rebooted again with the live cd, And now I see on the partition manager, one main drive with the size of one of the disks (500GB) as a raid, and below all the five disks I have. 

Something changed here. it is like an extra drive on top of the existing ones. Is this normal? Once installing should I have a total of 945 GBytes available?

I will also check the manual of course, but if you know if this is ok would be a big decrease in my time to set it up.

Thank you very much again

---

### Post by fjgaude on 2009-02-17
AFAIK, Linux cannot correctly know about this fakeRAID... the only program that might permit using the array setup in BIOS is **dmraid**.

It's in the repository. Install it using **apt-get** and then read its man pages.

---

### Post by alkisx on 2009-02-17
As I said, I've already done that

---

### Post by alkisx on 2009-02-17
Well, after searching more deeper, also using some command with dmraid, I realized that ubuntu sees the array created on the bios, with the name I gave (ddf1_MAIN), but the problem is that instead of the array partition to be about 1TByte (4 disks of 500MBytes in raid 10 as mentioned), is the half (500GBytes).

dmrair -r shows me that all the drives are on the array (ddf1). But I cannot understand why it sees the half of the actual capacity.

---

### Post by alkisx on 2009-02-17
More news on my problem. dmraid -s shows the actual size of my raid (ddf1_MAIN) (about 1 Tbyte). But partition editors (gparted,cfdisk) show it as 500GBytes.

any help please?

---

### Post by fjgaude on 2009-02-17
Well, the last time I checked fdisk doesn't understand arrays, so the information it gives is in error. What are you using to show the size of the array, not the drives?

How is the array mounted, what mountpoint?

---

### Post by alkisx on 2009-02-17
I think I made a mistake on the info of dmraid. The 976###### it shows it is sectors not megabytes I think. Forgive it's too late I am already more than 12 hours on this and have to work it out.

The only info I can get on the array drive is that is on /dev/mapper/ddf1_MAIN.

not mounted anywhere yet since I did not create any partitions, because in cfdisk as also gparted shows me the array as 500GB not 1TB.

Any idea on what is happening?

---

### Post by alkisx on 2009-02-19
No sulotion found. I got into bios and changed the controller from the adaptec to the intel one.

Then ubuntu found everything as it should be. Seems ok now.

---

