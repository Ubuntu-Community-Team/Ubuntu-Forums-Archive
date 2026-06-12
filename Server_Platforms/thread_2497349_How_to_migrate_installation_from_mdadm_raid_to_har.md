---
title: "How to migrate installation from mdadm raid to hardware raid"
date: 2024-05-01
forum: Server Platforms
---

### Post by wb6vpm on 2024-05-01
Forgive me as while I have many years of IT experience, I am not fully versed in Linux, so I hope this makes sense, and my apologies if my questions are obviously retarded, or inappropriate to this forum.

I have an NVMe SSD partition set up in RAID 1 using mdadm, with the EFI partition on the first drive of the array. What I am looking to do is to figure out how to move the EFI partition to the new hardware RAID, GRUB as needed (maybe thats part of the EFI partition?) as well as the RAID partition. I do not want to have to reinstall the entire OS, as well as deal with reinstalling and reconfiguring all of the software that is currently on the server.

System Info:

OS: Ubuntu 22.04 LTS
Current RAID: mdadm RAID 1
New RAID: LSI Hardware RAID Controller with BBU

Let me know if you need any further information, and I will gladly post it, TIA!

---

### Post by MAFoElffen on 2024-05-01
I too have many decades of IT experience. (over 36 years) Since I know you have experience at least in the concepts... No matter what OS that might be, let's talk like adults.

Your first question, how do you migrate from one RAID type, Volume Manager, or filesystem to another? ...You probably know this already: 
[LIST=1]
[*]Backup. 
[*]Setup the framework of what you want to end up on. 
[*]Restore within that framework. 
[/LIST]
In Linux, you have many, many, many ways to do that.

Yes. I do consider LSI RAID Controllers as being the industry standard for hard raid controllers... Now let's talk a bit more before going into the details of that.

Why the choice of going from mdadm to hardware RAID? Because to me, that, at least for me, and my experience, is a step backwards. Is this for your machine or  commercial production machine?

My own decisions for going from hard-RAID to mdadm, was because with Hard RAID, you are locked into that config, below the OS level. To recover, you are locked into correcting things at the RAID Controller BIOS level first. 

My disaster recovery strategies have evolved greatly in the past 36 years. Especially if your mission is uptime, and to be online, and where your priorities lie on getting back up in a timely manner.

RAID (of any type) is not a replacement for good backups.

I could talk volumes here... I used to teach CS, and i was an IT Consultant. I'm sure that would bore you. So to pair that down to "you", and what you "need", let's hear about your server, and it's job.

---

### Post by darkod on 2024-05-02
My opinion is also that going from mdadm to hardware is step backwards. If you want to use LSI card or similar HBA, no problem and go ahead, but use the disks in pass-through directly managed by the OS. No hardware raid active.

Let me give you a current example from work (true, not with LSI card).

We have a long running rebuild process of an array on a Dell PERC H730P Mini adapter. At the same time we needed to set up another array from different set of disks. Well, surprise, the adapter says it can only run one process at the same time.

With mdadm I would be able to create new array while I am also rebuilding another one.

---

### Post by MAFoElffen on 2024-05-04
+1 darkod --- 

Disclaimer: "Remember that RAID is not a replacement for a good backup strategy."

My follow on to the info I asked about...

The name of the game in Server Services is "uptime".

The following has adapted over decades of Disaster Recovery Plans, and Strategies: (other may have other differing experience)

Staying up is one angle. Here, replication and some type of RAID Array (where striping is involved), and a Volume Manager can help with that. But where my RAID Arrays lie, in what layer of the architecture, related to the bootable OS, has changed drastically over the years.

The other is: If a disaster does happen, how long does it take to get back up (recovery time), and what is the accepted risk factor.

If you keep an OS isolated to it's own layer in the architecture of the system, and keep it generic, then layer on the the config's, isolating the data and services...

Restoring just that OS and the basic configs can be done in minimal time. The service configs layered on top of that are the same for me as for recovery or migrations. This is where I found that over time, it isn't as important to keep an OS on a RAID array, as, say "your data".

The factor in "real-time data" is what is important. That starts to fall under what is the "acceptable risk" in what you can afford to lose. That comes into if you can afford hours, a couple minutes, or a few milliseconds of transactions, and how they are processed as confirmed transactions. That also depends on the type of service you provide. Financial gets into real-time, where milliseconds can mean a very big difference.

My own home datacenter, which deals with mostly testing and code, I can accept a lot more risk than some of my customers that I consult to.

Layers:

With Hard RAID, if a disk is down, or other hardware error, the whole system is down, below the OS level. You're screwed. Everything is at the RAID card BIOS level to make your fixes and corrections. You are limited to what you can do, and what you can do concurrently, as darkod mentioned. This is what pushed me from Hardware RAID to mdadm. I was using my hardware RAID cards as HBA's and passing them through to the OS...

Just doing 'that', opens many more possibilities.

mdadm is more flexible and adaptable than hardware RAID. There are things that you can do concurrently. You can make changes with mdadm, that you cannot do with hardware RAID, such as sizing and transformation of Array RAID types. I was using mdadm, with LVM2 on top of that, with my OS installed into that. But there was still a layer problem for me, if I had the OS on top of mdadm, within an array (in tht layered order)... If a disk was down, it didn't always come up. And then it took awhile on a reassemble, done offline, from a LiveUSB. It took awhile to learn. I was te project lead for gui-mdadm, which was to be a GUI wrapper for mdadm. That one command, mdadm, has so many options for that one utility, that makes it do different things. Picking the wrong option made it dangerous for the unaware, unless they understood what those options meant, and what they did. Where I was using it in my layers... That is what pushed me further to explore more possibilities.

Enter LVM2 RAID. LVM2 is a Volume Manager. LVM2, can be layered, with mdadm above it's Volume manager Layer, and the filesysem above that. It makes it more flexible and user friendly. It interprets mdadm and adds it's own flexibility, and command interpretation in doing that. My choice for the filesystem is Ext4. There are a lot of things that you can change, while still on a live filesystem. This is a big plus, when your mission is to stay online, and available. There are ways to tell it, that if degraded, start it as degraded. With LVM2, there are some warnings if things start to fail, instead of just: surprise, you have a problem. So you could be a little proactive. Then you have the ability to do snapshots. But there was still room for improvement, in how that worked, and what it takes to keep it up, and the time to recover.

In 2005, I supported Solaris & OpenSolaris. That is when I started using ZFS. ZFS is a Volume Manager, which has it's own filesystem that is Copy-On-Write (COW), and then has RAIDZ & dRAID. That is my current choice. It is very flexible. It has a fairly high ramp up in learning the skills, and maintenance of, but simplifies so many things, is very dependable, and performs very well. I don't recommend it to everyone. It takes some commitment to learn to be able to be proficient with it, by understanding how it works... Once you learn that, that opens a lot of doors of what is possible with it.

Like LVM2, a lot of things are online, and with a Live Filesystem. You get a lot of warnings before a failure. I can lose 2-3 disks, and not even notice a performance loss, telling me something is wrong, until I look at my reports. LOL. And repair it while still live.

Another thing that changed was how to segregate the system architecture into interchangeable 'pieces' that can be interchanged, and are replaceable at different layers, but appear as a single system, when put together. This is a concept, I started to push as distributed processing back in the early 90's... Based on experience from JPL in the Late 80's. This is something I learned from the Unix system model... This is a concept that I implement into system architecture design, whether it be hardware or software. If you plan on and make the pieces interchangeable, then it can grow, adapt, and be recovered simply.

If your separate your OS from other things, it is easy to replace. Usually much faster from a straight backup, or fresh install than a rebuild/assemble from if it where loaded on top of RAID. Then restore from your backups. If things are separated, and put into a storage container, chances are lower/less that a disaster affects other areas of the system. Things can be checked out, repaired or restored once that is diagnosed and assessed. 

LVM2, that opens new doors and possibilities. Trusting it changed my thoughts on how things could work. With ZFS, with RAIDZ... More. If a disk is degraded, it may just be from checksum errors when writing, which a quick clear & scrub fixed while online. I used hardware disk caches fro reads and writes, so if there is a disk failure, I have a larger area, where the I/O transactions are on disk somewhere. If a disk needs to be removed and replaced, i can still do that remove/add/resilver online and live.

---

### Post by wb6vpm on 2024-05-20
> **MAFoElffen said:**
> I too have many decades of IT experience. (over 36 years) Since I know you have experience at least in the concepts... No matter what OS that might be, let's talk like adults.

Your first question, how do you migrate from one RAID type, Volume Manager, or filesystem to another? ...You probably know this already: 
[LIST=1]
[*]Backup.
[*]Setup the framework of what you want to end up on.
[*]Restore within that framework.
[/LIST]
In Linux, you have many, many, many ways to do that.

Yes. I do consider LSI RAID Controllers as being the industry standard for hard raid controllers... Now let's talk a bit more before going into the details of that.

Why the choice of going from mdadm to hardware RAID? Because to me, that, at least for me, and my experience, is a step backwards. Is this for your machine or  commercial production machine?

My own decisions for going from hard-RAID to mdadm, was because with Hard RAID, you are locked into that config, below the OS level. To recover, you are locked into correcting things at the RAID Controller BIOS level first. 

My disaster recovery strategies have evolved greatly in the past 36 years. Especially if your mission is uptime, and to be online, and where your priorities lie on getting back up in a timely manner.

RAID (of any type) is not a replacement for good backups.

I could talk volumes here... I used to teach CS, and i was an IT Consultant. I'm sure that would bore you. So to pair that down to "you", and what you "need", let's hear about your server, and it's job.

> **darkod said:**
> My opinion is also that going from mdadm to hardware is step backwards. If you want to use LSI card or similar HBA, no problem and go ahead, but use the disks in pass-through directly managed by the OS. No hardware raid active.

Let me give you a current example from work (true, not with LSI card).

We have a long running rebuild process of an array on a Dell PERC H730P Mini adapter. At the same time we needed to set up another array from different set of disks. Well, surprise, the adapter says it can only run one process at the same time.

With mdadm I would be able to create new array while I am also rebuilding another one.

To both of you, thank you very much for taking the time to respond, and I will try to respond to your questions as best I can. Yes, I am 100% aware that RAID is not backup :), but it does help protect from stupid things like drive failures, which no matter how carefully I try to account for them, seem to enjoy biting me in the rear end :P.

[LIST]
[*]This is a personal server (Plex etc) that I can't afford to have much downtime on (happy wife, happy life, HAHA)
[*]To the question of why hardware vs mdadm, it's actually a bit of a few things:
[LIST]
[*]I know how hardware RAID works, and how to work with it, whereas, with mdadm, if/when something goes wrong, now I am scrambling to figure out how to fix it. Don't misunderstand, I'm not saying that I'm not willing to learn new things, I do all the time, it's just where I'm comfortable at right now
[*]I actually like the fact that it is "above" the OS, as it allows things like EFI partitions to be included in the protection
[/LIST]
[/LIST]
Sorry for the delay in responding, I just realized that I never actually clicked on the Post button!

---

### Post by MAFoElffen on 2024-05-20
LOL. Understood. And I have my Plex Server for the same reasons. LOL

Look at my first post... Migration.

With a few more specifics... 

Backup your data (media files), configs, UserData. Run the UbuntuForums 'system-info' report in my signature line. Near the end of that report is a section that will list all the user installed packages. You can use that to reinstall what was beyond the basic install.

Zero the disks that were there.

Create your RAID Array(s)

Install a fresh OS. <-- Why new/fresh? Very clean, and easier than removing the mdadm defines that will no longer be there, and having to change the mountpoints, that will no longer be there.

Reinstall your services, and applications. 

Restore your UserData and data

In Plex, recreate the Libraries to point them to where everything is located. On the refresh of the libraries, once those are in place, it should find everything that was there. For instance, I have a lot of edits that affect how the media files sort in the libraries, and the artwork I found to my media files.

---

