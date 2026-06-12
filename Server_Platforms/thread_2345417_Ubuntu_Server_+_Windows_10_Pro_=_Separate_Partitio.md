---
title: "Ubuntu Server + Windows 10 Pro = Separate Partitions + RAID"
date: 2016-12-04
forum: Server Platforms
---

### Post by kc_2 on 2016-12-04
I'm building a new computer, will do the following:
M2 SSD x1 = Windows 10 Pro (NTFS)
SATA SSD x1 = Ubuntu Server (EXT4 (or another?))
HDD x2 = storage, RAID, with Windows 10 partition (NTFS) & Ubuntu Server partition (EXT4 (or another?))

I'm just going to do RAID 1 with the two HDDs. I'll set up an external backup solution.

How can I pull off having the 2 file systems, each its own partition, both contained within the same RAID?

Quick edit - here's the mobo:

Asus Z170-PRO ATX LGA1151 Motherboard

---

### Post by Graham_Willis on 2016-12-04
Do you want to have RAID with two (independent) partitions, one NTFS, second ext4?
If what you want to have is mirror consisting of two disks and one of the disks being ext4, second NTFS, then forget about it - you create file system on the array (not on particular disks), and it would break the concept of the mirror. And even if by highly unusual means it was possible make such a setup real, it'd be better not to use RAID at all.

Having said that - why do you want to do that in first place? If the concerned computer's going to be used as a server, then I really can't see why you'd like to install two systems on it. If you want to be able to access one system from the level of the second in case of trouble, then just use bootable CD/DVD or pendrive.
But setting up RAID consisting of NTFS partition and ext4 partition (NTFS mirrored to NTFS on the second drive, ext4 mirrored to ext4 on the second drive) should be possible I think - RAID can hadle whole disks as well as partitions. Ask more questions if you want to go this route and more help's needed.

---

### Post by darkod on 2016-12-04
Because you want the raid to be shared between windows and linux your only option is using the board onboard raid (so called fakeraid). You will create the raid1 array of 2x disks and then both OSs will see that array as one single disk.

Then inside windows create the NTFS partition with the size you want, leave the rest as unpartitioned.

After that in ubuntu you can create the ext4 partition from that unpartitioned space. Windows will be able to use the ntfs, ubuntu will be able to use both the ntfs and ext4 if you want to...

But I agree that dual boot for a server is highly rare. I really can't see in what situation you would need it. If you want ubuntu server that will run only periodically you might consider Virtual Box in windows or something similar. Then just start the VM when you need it and power it off when you don't.

Anyway, you have the answer to your question so if you really want a dual boot, go for it.

---

### Post by kc_2 on 2016-12-04
> **Graham_Willis said:**
> Do you want to have RAID with two (independent) partitions, one NTFS, second ext4?

Yes. That's exactly what I want.

Basically:

[IMG]http://i.imgur.com/UtTcYCZ.png[/IMG]



> If what you want to have is mirror consisting of two disks and one of the disks being ext4, second NTFS, then forget about it - you create file system on the array (not on particular disks), and it would break the concept of the mirror. And even if by highly unusual means it was possible make such a setup real, it'd be better not to use RAID at all.

I don't want 1 disk to be one fs and another disk to be another fs, I want to take the 2 disks, make "one disk" out of them, then split that back into 2, like in the diagram above. Sorry if it was unclear before.

>  it'd be better not to use RAID at all.

I want to use RAID 1 because of what RAID 1 offers. I want to use separate partitions, each with their own file system, because of what they offer. I want to use both combined. I also want to use backups, so I will then send those through to an external backup source. (I'm only mentioning the backup part because so often people immediately assume that when someone asks about RAID that they think that it means it's for backups, when it is obviously not.)

> Having said that - why do you want to do that in first place?

It has always puzzled me as to why people care to ask why someone wants to use a technology when that person was simply asking for assistance on how to use it in the first place, but, having said *that*:

"So why use RAID 1? The primary reason is the member drives in a RAID 1 array essentially produce a mirror of each other. Hence, if 1 of the member hard drive fails, no data loss is suffered as the other member is a mirror of the lost drive."

"Why choose RAID 1? Simple (literally!) - RAID 1 is a simple technology that is a popular choice on dedicated servers because of the additional protection from data loss along while affording some increased read performance."

Of course, the server aspect of my build is not truly dedicated, but I will leave it running when I'm not using it for other purposes.

I did consider other RAID options and, really, I'd be okay with using another or none at all. I simply chose to go with RAID 1 for now. I used RAID 5 in the past, I won't do that again, even though it's not a horrible choice.

RAID 1 has its purposes, if I had a choice I'd do RAID 10, but I also am on a budget, and just want a quick and simple mirror of data on the storage drives, and I want the partition / file system setup that I mentioned, and I will then push that data through to backups.

Heck, I might later switch this to RAID 0, then grab the backups and pull that data back onto the freshly formatted drives.

I might even, later later, abandon RAID on the internals entirely and simply use separate drives. Why? Because.

Before I re-purpose the computer into a gaming-only computer, I choose to use RAID 1 (at least for now). I might use RAID 0 later on when it's a gaming computer.

I'm not building 2 computers. Budget. I will build a dedicated server later, then re-purpose this one.

> If the concerned computer's going to be used as a server, then I really can't see why you'd like to install two systems on it.

Again with the why... {sigh}... I have my reasons, my purposes, for a hybrid computer.

"Why Bother Dual-Booting?Different operating systems have different uses and advantages. Having more than one operating system installed allows you to quickly switch between two and have the best tool for the job. It also makes it easier to dabble and experiment with different operating systems."

"For example, you could have both Linux and Windows installed, using Linux for development work and booting into Windows when you need to use Windows-only software or play a PC game."

"You could use virtual machine software instead of setting up a dual-boot system, but a dual-boot system lets you actually use both operating systems on your hardware at full, native speed. You don&#8217;t have to deal with the overhead of a virtual machine, which is especially bad when it comes to 3D graphics."

Why install 2 systems? I am going to use Windows exclusively for gaming. Linux for everything else. I'm not asking anybody to try to convince me otherwise.

All I'm asking in this thread is how to set up the separate partitions, each with its own file system, both contained within a RAID.

> If you want to be able to access one system from the level of the second in case of trouble, then just use bootable CD/DVD or pendrive.

That's not what I want.

> But setting up RAID consisting of NTFS partition and ext4 partition (NTFS mirrored to NTFS on the second drive, ext4 mirrored to ext4 on the second drive) should be possible I think - RAID can hadle whole disks as well as partitions. Ask more questions if you want to go this route and more help's needed.

Do you know how to set up separately partitioned file systems within RAID? That's all I want to know. I've googled it. It looks like it might only be possible with either a raid card or fake raid, that soft raid may not be an option.

> **darkod said:**
> Because you want the raid to be shared between windows and linux your only option is using the board onboard raid (so called fakeraid). You will create the raid1 array of 2x disks and then both OSs will see that array as one single disk.

Thank you! That's exactly what I want. So, basically I get into the BIOS (or UEFI in this case) and set the disks to the RAID, and that's it? Would I still have to do anything with any software, like mdadm or dmraid in linux and something else in windows? I read somewhere something about someone using fake raid along with dmraid.

> Then inside windows create the NTFS partition with the size you want, leave the rest as unpartitioned.

After that in ubuntu you can create the ext4 partition from that unpartitioned space. Windows will be able to use the ntfs, ubuntu will be able to use both the ntfs and ext4 if you want to...

That makes sense, thank you.

> But I agree that dual boot for a server is highly rare. I really can't see in what situation you would need it. If you want ubuntu server that will run only periodically you might consider Virtual Box in windows or something similar. Then just start the VM when you need it and power it off when you don't. Anyway, you have the answer to your question so if you really want a dual boot, go for it.

I've already given the "why". As for why boot between a server and gaming, because I am on a budget and I want a lab-based server, not a dedicated one, and a gaming computer, and so I am setting up both within one. Anyway, thank you for the info.

---

### Post by Graham_Willis on 2016-12-04
kc_2, I was asking why you'd like to set up a mirror with both NTFS partition and ext4 partition on it** and** you'd like to have Windows/Linux dual boot because I'd thought that you were perhaps attempting to whatever problem you had by a method which wasn't best fitted to it, so I wanted to present (not convincing you to anything, not saying that it's what you should do) you a better solution and point the complications that can arise from the one you described. I respect people's right to make their own choices, so if you want what you want because you just want it, then it's fine.

Why you want to use RAID1 as opposite to the other levels of RAID was out of the question, BTW. I was only interested in why you would like to set up dual boot Windows/Linux server.

---

### Post by darkod on 2016-12-04
About the question whether you set up raid in the main BIOS/UEFI, check your board manual for more detailed instructions. On many boards there is separate RAID BIOS where you enter with a specific key combination during boot. So it might be inside the main bios or in separate one.

In linux usually mdadm is only for linux software raid so it proably would not be used for fakeraid. The dmraid package handles the fakeraid, and whether it will do it automatically in your case or you will need to set it up, I really don't know because I have never set up fakeraid dual boot. Only linux servers with mdadm raid.

In your case it helps a lot that the OS in fact will be on separate disks outside the raid, so you will be able to install it regardless of whether it sees the raid immediately during installation or not. When installing the server version I do think it detects fakeraid and asks you if you want to activate it. Saying yes will make the array visible for ubuntu server OS...

---

### Post by kc_2 on 2016-12-05
Got it. :)

Had to disable unused drive bays and now, with raid enabled on the motherboard, the M2 SSD Windows drive and SATA SSD Linux drive both boot and recognize the raid. I went ahead and set half of the raid aside for windows and the other half for linux.

---

