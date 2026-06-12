---
title: "If you use Windows XP or 2000 at work, what's the security practice there?"
date: 2007-11-16
forum: Windows
---

### Post by aysiu on 2007-11-16
Every school I've worked in where I've had to use Windows XP or 2000, I've been given administrative privileges. I've also seen a lot of malware infestation at each of these places.

It seems that some IT departments would rather deal with cleaning up malware / reinstalling Windows than being bugged to train people on good security practice or install software for them every time it's needed.

What have been your experiences in the workplace with Windows security policy? I guess, for the poll's sake, just answer for your current workplace or school. But within the narrative of the thread, you can talk about former places of employment or former schools.

---

### Post by RebounD11 on 2007-11-16
My school is also using XP and 2000, and the staff has administrator accounts while student have limited one. But getting an administrator password isn't at all that hard. I've managed to do that on several occasions, I know it's not nice but Iif I said anything to anyone in the school staff they would've treated me with sth like "What do you know about this?" (mind you it's a University that has a computer science faculty, I believe that the students aren't all that ill prepared). So I thought if I show them, they will fix it.

First of all, the school offers a wireless access point for students who have a capable laptop, and you can access the whole school network from your laptop. Then, most professors have a laptop, and use it to browse this network or the web. Some of them have only one account and it has administrative powers, and most of those don't have a password, and more you're allowed to change files and folders in their share folder, so I cut some of their work files that they share on the network and pasted them on my computer. 

Need I say more about the security... Most of the schools computers aren't even up-to-date or don't have a firewall active (not even the Windows default).

Not to mention that even the computers that have some protection are fairly easy to hack. 

However, for a while now, there's a MAC filter on the school's net and at any time they know who is doing what on the network, they've even encrypted the Wireless, and you have to get a password from an admin after you give him you network card's MAC address. However, the encryption is not unbreakable, and the approved MAC addresses are easy to steal... so I let you judge how they treat the security issue.

PS: I sometimes have a feeling they're using a cracked version of Windows, can't prove it but I have this feeling...

---

### Post by markp1989 on 2007-11-16
at my school, all students had limited accounts, 1 day i loged in an i was an administrator, i could do everything. cept all my files were gone, so they had to make another limited account, even thou they never deleted that admin account in my name

---

### Post by -grubby on 2007-11-16
At my school the older P3s run Windows 2000 while the newer ones(P4s) run Windows XP. I don't exactly know about limited or administrator accounts because the school uses some sort of Novell (hit me like a month ago that the login thing said Novell and I realized they were a Linux company) login client although I would guess they are limited accounts because I tried to change the time once and couldn't

---

### Post by Frak on 2007-11-16
We don't let any of our students have administrator access, and teachers can only install with permission. We use websense and Avast AV, while we have a dedicated blade to scan all workstations once per week (different workstations on different days). These blades run Debian w/ NT-based Windows in a Virtual Server client (customized version from Microsoft to run on Sparc, ARM, MIPS, and PPC processors; in this case Sparc) running around 10 different commercial anti-virus (via x86_64 JIT compiler) and ClamAV.

---

### Post by LaRoza on 2007-11-17
At my school, only 2 people (that are there) have the admin passwords. The passwords are randomized, and long. 

All users, staff and students, have limited accounts. The account passwords must be changed every so many weeks (5 I think), and cannot be repeats.

All this helps reduce the spread of malware, however, I have crashed the network (for the entire building) by accident, when I used XAMPP portable on my flash drive to demonstrate sites I had written. Little did I know it would take control from the Windows Server that the schools uses. The network admin hates Windows, but gets money for working with it. He even mocked the Windows network when my little flash drive brought down an enterprise server...

---

### Post by Frak on 2007-11-17
That has happened to our severs before also. A block has been administered since then for internal servers. It's pretty sad though, how such a "classy" server OS will fail miserably from the inside.

---

### Post by darksidedude on 2007-11-18
we use fedora for our workstations and windows server 2003 enterprise edition ( shouldnt it be the other way around):lolflag: I happen to be the admin for server 2003:guitar: so i use avast server, moon secure AV and clam win, with windows firewall

---

### Post by atlfalcons866 on 2007-11-18
my middle school had all Dell gx150 all the same specs. pentium 3 933Mhz 128MB ram 20GB harddrive running windows 2000. I messed up a couple on my last of 6th grade =) My old high school had windows xp and they were slow dell gx110. They were pentium 3 500Mhz 128MB ram 5Gb hard disk.

---

### Post by Erdaron on 2007-11-19
University-owned computers connected to the network have to be run under limited accounts. In my lab we have a computer that controls some hardware, and the software has to run in administrator mode. We had to take the computer off the network for that.

Personal computers brought onto campus can be whatever, though you do have to register your MAC addresses. Some departments have additional security measures.

Wireless network is encrypted (WPA2), has a MAC filter, and users have to authenticate themselves using school email logins. Also, when you registered on the network, they checked to make sure you had a firewall (I use Comodo) and antivirus (I use AVG) running.

I think, overall, they take it fairly seriously without making too much of a hassle to use.

Pretty much everything runs XP. I haven't seen a Win2k box on this campus.

---

### Post by inversekinetix on 2007-11-20
At the schools I work at everyone is on a limited account, all computers have complex passwords, all computers have realtime virus scanners running, all computers have limited net access.  Its really well locked down.

---

### Post by baqai on 2007-11-21
The company i work for is affiliate of Verisign, we follow strict VTN (Verisign Trust Network) guide lines, few of the rules (combination of Verisign and Internal policies) we follow

1. usb are disabled
2. camera phones not allowed inside tier 3 onwards (we have 7 tier data center)
3. Password policies (annoying)
4. Login based on digital certificates and smart cards
5. Laptops using bio matrices 
6. No external connections (remote desktop etc) allowed, including IT department
7. Entry to premises based on biomatric's 

We recently got ISO 27001:2005 certification (Information Security Management)

Yet we are running desktops on Windows hehe! All servers are Sun Solaris though

---

