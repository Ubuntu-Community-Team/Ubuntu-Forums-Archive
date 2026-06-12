---
title: "Replacing windows server 2003 and isa server 2004 with Linux / Ubuntu"
date: 2009-08-26
forum: Server Platforms
---

### Post by shakeel.ahmad215 on 2009-08-26
Hello

I am Shakeel from Pakistan. I am a network administrator providing internet services to more than 80 clients through local area network.

I am using Windows Server 2003 and ISA server 2004 on my server machine.

I want to use Linux on my server machine to provide and control the internet service to my clients.

From where should I start. I dont know much about linux but I have intalled red hat on my pc and tried to get familiar with its commands and I know many basic commands now. But I dont know to configure linux as a server to replace the windows server 2003 and isa server 2004.

I have come to know that it works better than Winserver.

We have a electric power shortage problem in Pakistan now a days and we have to face un scheduled electric load shedding. So we could not propely shutdown the windows server due to which its services get corrupted and it gives error on next boot after the load shedding.

I have come to know that linux is safe in this regard that we dont have to face crashes.

Please guide, I am new to this forum.

Shakeel Ahmad.

---

### Post by cariboo on 2009-08-26
A bump for the move

---

### Post by jocampo on 2009-08-26
> **shakeel.ahmad215 said:**
> Hello

I am Shakeel from Pakistan. I am a network administrator providing internet services to more than 80 clients through local area network.

I am using Windows Server 2003 and ISA server 2004 on my server machine.

I want to use Linux on my server machine to provide and control the internet service to my clients.

From where should I start. I dont know much about linux but I have intalled red hat on my pc and tried to get familiar with its commands and I know many basic commands now. But I dont know to configure linux as a server to replace the windows server 2003 and isa server 2004.

I have come to know that it works better than Winserver.

We have a electric power shortage problem in Pakistan now a days and we have to face un scheduled electric load shedding. So we could not propely shutdown the windows server due to which its services get corrupted and it gives error on next boot after the load shedding.

I have come to know that linux is safe in this regard that we dont have to face crashes.

Please guide, I am new to this forum.

Shakeel Ahmad.

Hold on my friend! ... MCSA/MCTS SQL 2005 here... and Ubuntu lover since February.

Os crashes, disk corruptions because power failures are two differents things. So, let me talk about my experience about Windows, which is much more and stronger than linux.

1st, I want to remove the idea that Windows Server ( and I said Server) crashes all the time. I've worked for a major IT company in USA (with worldwide branches) and I've seen not many Os crashes in my life. They usually happen in Windows because you install crappy drivers or third party applications which have not been fully tested. So.. I'll give Micro$oft credit on that ;-) That being said, how secure the Windows Os is and how well it manages disk and memory is another topic. Agree that Linux and Unix do a better job.

Now, regarding power failures, not Linux, not Micro$oft (event with Data Center edition) can not fully prevent a disk crash if you do not have battery backups or redundant power on all your systems; that's highly true for MS-SQL and Oracle servers, because everything goes to RAM, if you lost power in a middle of a transaction, you can corrupt the database. Something similar can occur to Linux or Windows if you cut power without notice.

Finally, ext3 and ext4, the Linux file system partition, does a better job than NTFS. I could spend the rest of my day explaining, is a long topic, but in a few words, ext3 and ext4 handles information better inside the disk and you can safely say the fragmentation is zero on Linux.

You can replace some functions of a Domain Controller via Samba, but right now, you can not fully replace an Active Directory domain. So, if your company depends of that, do not move to Linux and keep your current AD.

By the way, welcome to the forum and Ubuntu world! :-) ... I really love Ubuntu and it's really a nice and strong operating system. I'm sure you'll love it too.

---

