---
title: "Need to build &quot;cheap&quot; Hi-Perf Tera-Byte server for a school"
date: 2008-03-01
forum: Server Platforms
---

### Post by HW_Hack on 2008-03-01
Hi all -

I work as a tech specialist for a large high school (that covers the $$ cheap requirement) --- we want to start an advanced film making class where a student project file (all the clips + music + effects) could easily average 10 - 20GB file size. And consider 20 or more students hitting the server during a class period.  

The primary need for the server is fast file transfers to Mac based clients. Students arrive in class - login - then copy their current project from the server to the mac - edit / work on the project - then save back to the server as class ends. Again we need to minimize "wasted class time" waiting for file xfers. The server could be located either in or near the classroom to minimize  part of the network xfer time. 

I have little direct experience in this area so I'm asking for input / comments. I would like to keep the cost of the server under $1200 --- things I would assume:
- Either a Dual Pentium or Core Duo  CPU
- Minimum 2GB SDRAM
- Hardware RAID card (Ubuntu Friendly)
- Using 300GB drives for the RAID 
- GB LAN --- some questions here as a good part of our main NW is 100MB
But I'm hopeful I could have the server local and keep the "local network" at GB level ?


But those are just guesses -- anyone have direct experience with a server in a similar environment / function ?

THANKS !!!!!!

---

### Post by farruinn on 2008-03-01
> **HW_Hack said:**
> - GB LAN --- some questions here as a good part of our main NW is 100MB
But I'm hopeful I could have the server local and keep the "local network" at GB level ?

I'm pretty sure all modern Mac desktops have Gigabit ethernet, and it wouldn't be hard to get a Gigabit  card for your server, but to keep the entire network at that bandwidth wouldn't your intervening switches and routers have to be Gigabit capable?

Do you plan on still having the students copy their work back and forth between the file server each class period or set up NFS/AFP/SMB shares?

---

### Post by HW_Hack on 2008-03-01
> **farruinn said:**
> I'm pretty sure all modern Mac desktops have Gigabit ethernet, and it wouldn't be hard to get a Gigabit  card for your server, but to keep the entire network at that bandwidth wouldn't your intervening switches and routers have to be Gigabit capable?

Do you plan on still having the students copy their work back and forth between the file server each class period or set up NFS/AFP/SMB shares?

The idea in my mind is to have the server in the room - it will connect to a 32 port GB switch (main switch) - all the Macs in the room will connect either directly to the main  switch (or thru another 8-16 port GB switch to the main switch) ----- lastly one port of the main switch would go to our 100MB backbone to provide a connection to the internet.

So I would hope that all "local" xfers to the "local server" would be at GB speeds .... and of course if the students need to go "out to the internet" they would then be throttled by the 100MB backbone connection. 

Does that make sense ???????

---

### Post by HW_Hack on 2008-03-01
""Do you plan on still having the students copy their work back and forth between the file server each class period or set up NFS/AFP/SMB shares?""

Well I'm ignorant here ---- I would like to have the model of each student having their own personal login / share. Need to make sure Billy can't accidentally wipe-out Joe's project. 

Its not clear to me if its better (for iMovie) to have the kids be working  "locally" meaning they have copied their project to the Mac ..... or have them work off of their files off of the server.  I don't have a feel for this  - although working off of the server should work ok.

---

### Post by farruinn on 2008-03-01
Seems to me that's exactly how it would work.

Good luck.

---

### Post by tubezninja on 2008-03-01
> **HW_Hack said:**
> 
Well I'm ignorant here ---- I would like to have the model of each student having their own personal login / share. Need to make sure Billy can't accidentally wipe-out Joe's project.

For something like that, I think you're going to need a server that has OpenDirectory Services installed:

[http://developer.apple.com/opensource/dirservices/](http://developer.apple.com/opensource/dirservices/)
 
The good news is that the components you need are provide by Apple under an open-source, free license.  The BAD news is, I don't know of anyone installing them on ubuntu specifically for production work.  Theoretically, it would work.  But you'd have to get the ubuntu server installed and working, and then compile the relevant binaries.  Then set up a domain and get your Macs associated with it.

Getting OpenDirectory going is probably the best way to not have students confused.  That way they're spending time actually working on their projects (which is what you state the priority is) and not learning linux.

I don't mean any offense, but I'm a little concerned.  I've worked in the same situation you're in now, and I now supervise and consult on the creation of multiple installations like this.  I'm also brought in (as my time permits) to FIX installations that I wasn't involved in, that went horribly wrong.

The source of my concern is that, if you're admitting ignorance on SMB, AFP and NFS, I'm worried that you're going to be in over your head when it comes to compiling the needed services from source code and getting them to run under a non-Darwin kernel.  If you have money in your budget to buy Macs, then I would very strongly recommend finding a way to budget in an [Xserve]("http://www.apple.com/xserve/") or Mac pro, running OS X server.  That way the stuff you need is already set up, and easy to configure, and the learning curve is dramatically lessened for both you and the students who will be using this lab.  You don't have to worry about compiling anything or setting up NFS shares or whatnot with OS X server.  I love ubuntu, and I even just wrote a lengthy post to a Mac user about why they shouldn't bash ubuntu, but in this case, I really don't think you should mess with it unless you or someone on your staff is very experienced in setting it up in the enviornment you want it in.

I realize the pressure is on to save money for an edu environment, but cutting corners on the server is not the way to do it.  Especially if students are going to rely on it to store multiple gigabytes of their classwork, and their grades are riding on this network being reliable.

Failing that, I would ask for more time so that you can really brush up on linux and be comfortable with setting up a production linux server, compiling binaries, and getting some intimate knowledge on what Open Directory is and what it does.  that way you can do this with confidence.  I just feel very uneasy giving someone a crash course on production Mac-based file sharing networks (on a non-Mac server, no less) in a forum thread.

> Its not clear to me if its better (for iMovie) to have the kids be working  "locally" meaning they have copied their project to the Mac ..... or have them work off of their files off of the server. 

Working off the server is a bad idea, especially for video files.  If theses students are editing DV video, the source files are easily going to be 18-20GB per hour of footage, and there's going to be a lot of disk thrashing going on when they export the final output to Quicktime or other formats.  Even on a gigabit network, you're just asking for trouble having multiple people work off a single networked file system for this.  Always have them transfer the files to a local file system first, then transfer back when they're done.

---

### Post by mrsteveman1 on 2008-03-01
I definitely think you should familiarize yourself with the protocols before you decide what to do, but thats not the real problem anyway. SMB and NFS are both very capable of doing per file locking so people can work on files over the network instead of locally etc. I'm not fond of NFS but it does work in situations like this. SMB can be configured so that depending on the username supplied to the server at login, the fileserver serves a different share to the user.


OpenDirectory is just LDAPv3 + Kerberos v5, which Linux already supports natively, in fact OS X just uses the OpenLDAP package from Linux anyway. The one thing OS X server does have is good GUI admin tools for LDAP, but if that is something you need there are plenty of real enterprise Linux tools available, redhat and suse both have excellent server tools available for stuff like this, including authentication and directory services. Even the free opensuse distro has GUI tools for configuring authentication and network services like you want. LDAP is probably a good idea though given the number of students involved.


I would advise you to find a good way to let the students work locally to minimize network traffic. Working on large files over a network isn't a HUGE problem but it will never be as fast as a local setup.  In cases like this, where you have large files being worked on over a network, typically you have a SAN with fibrechannel etc, but thats extremely expensive for something like this and probably not necessary. 


 If you do decide to let students work directly over the network you might be better off doing 10GigE between the switch and the server, because thats your bottleneck in this case, and you want it to be faster than the individual links for the students machines. 20 students working on 10gb files over a single 1GigE is going to allocate around 25mbps to each student when you account for overhead and such, which is pretty slow considering the sort of work you're talking about.  To do this though, you need to make sure the switch has an expansion port you can put a 10GigE transceiver in, and most of the newer switches do.


An Xserve is going to run you $3000+. The Mac Pro is cheaper but you still need a raid card, pushing the cost close to 3k anyway. For something this important softraid (like linux mdraid or OS X softraid) is not fast enough or reliable enough, so a hardware raid card is essential. Something you might also consider, the motherboard in this case is going to be more important than the processor, fileservers don't have all that much processing to do, but they need to be rock solid stable and have LOTS of ram, so pick your motherboard carefully. For the raid card 3ware is a good choice and well supported in Linux.

---

### Post by koenn on 2008-03-02
> **HW_Hack said:**
> The idea in my mind is to have the server in the room - it will connect to a 32 port GB switch (main switch) - all the Macs in the room will connect either directly to the main  switch (or thru another 8-16 port GB switch to the main switch) ----- lastly one port of the main switch would go to our 100MB backbone to provide a connection to the internet.

So I would hope that all "local" xfers to the "local server" would be at GB speeds .... and of course if the students need to go "out to the internet" they would then be throttled by the 100MB backbone connection. 

Does that make sense ???????
It makes sense, if you keep in mind mrsteveman1's remarks that the students will be sharing the throughput, i.e. if all students access the server simultanously, the available 1Gbps of the server NIC will be shared among them. Also, the GB uplink from a 2nd switch to the main swith will be shared among all computers using that switch. 
Guestimating : saving a 10G file at 25 mbps ~ 54 minutes ?
(may be wrong by factor 8, I never was good at this)

you may solve this either by increasing network capacity (10G), or let students work on a local file on their mac (allowing them to frequently save their work without network delays) and copy / rsync their work to the server at the end of the period - more a backup-type sollution than actually working on a remote file. 

I'd probably prefer NFS in a situation like this - it's pretty straightforward, is transparent to users and applications and probably  has less overhead than samba.

On firts sight, the network will always be the bottleneck, but it wouldn't hurt to consider disk I/O of the server as well. A (hardware) RAID will defenitly help - you'll have to look into what RAID level suits you best in terms of READ and WRITE characteristics

---

### Post by koenn on 2008-03-02
I don't see the point of bringing a directory service (Open Directory or any other LDAP / Kerberos implementation) into this. 
This is a plain 'workgroup" setting : 20 users, 1 server.
all it takes is a user account on the server for each user, possibly a group to hold them all, and you can manage file access simply through file system modes and ownership (chmod, chown, ...) 

single sign-on and centralized account management (the business case for directory services) only make sense when (lots of) users need to access multiple servers and you don't want them to have to remember logons for each individual server (and you dont want to have to set up a seperate account for each user on each server)

---

### Post by mrsteveman1 on 2008-03-02
LDAP would simplify things a bit by giving you central control over the user accounts. For instance, if the users don't always use the same machine, you now have to maintain 20 different user/password combinations in 21 different places. And if you end up using NFS with permissions, you now either have to make sure the UIDs are identical on every machine, or use a mapping server somewhere, in which case you might as well be using LDAP anyway.

Samba and NFS both have their share of problems, neither are really meant to be used as a SAN for video editing, but for simple backups and file transfer either one will work ok. Samba does seem to have more overhead but I typically see close to wireline speeds with it when transferring large files over a link, so it's not a huge problem if you do decide to use it.

---

### Post by HW_Hack on 2008-03-02
> **koenn said:**
> I don't see the point of bringing a directory service (Open Directory or any other LDAP / Kerberos implementation) into this. 
This is a plain 'workgroup" setting : 20 users, 1 server.
all it takes is a user account on the server for each user, possibly a group to hold them all, and you can manage file access simply through file system modes and ownership (chmod, chown, ...) 

single sign-on and centralized account management (the business case for directory services) only make sense when (lots of) users need to access multiple servers and you don't want them to have to remember logons for each individual server (and you dont want to have to set up a seperate account for each user on each server)

**THANKS TO ALL FOR YOUR COMMENTS !!!**  

I should note that I have built a few Linux servers for testing / learning - successfully set up Samba to both a PC and a Mac. I need to look at NFS for sure. 

But I feel in this very limited environment:
- six staff as permanent users
- every 5 months delete 150 student accounts - then add the same number of new accounts 

Using the standard single sign-on should work fine -- every student is assigned a unique 6 digit number they already use to access the district main servers. I then use that for their ID and use a common password for each class.

So I'm having some difficulty with the whole open directory concept. 

But then I am no NW engineer ---- I do feel the students need to move their project files locally - edit - then save back to the server at the end of class.  This is basically what we recommend when they use the district servers (located 8 miles away -- accessed via fiber lines). 

Any comments on which RAID type would be best ??

Also need input a good RAID card that is Ubuntu proven

---

### Post by mrsteveman1 on 2008-03-02
3ware raid cards, no question.

As for which raid level (which is what you're asking i think), since this is going to be quite a bit of data flying back and forth you definitely want to use raid 5, which will give you a lot of performance and also allow for one of the disks to fail without causing a serious problem.

In this case the best solution is probably going to be 3 or 4 500gb disks connected to the raid card.

The 3ware 9650 series seem to be pretty good cards, just pick carefully, you need 4 sata ports and raid level 5 for sure.

---

### Post by HW_Hack on 2008-03-02
koenn
""It makes sense, if you keep in mind mrsteveman1's remarks that the students will be sharing the throughput, i.e. if all students access the server simultanously, the available 1Gbps of the server NIC will be shared among them. Also, the GB uplink from a 2nd switch to the main swith will be shared among all computers using that switch. 
**Guestimating : saving a 10G file at 25 mbps ~ 54 minutes ?**
(may be wrong by factor 8, I never was good at this)""


Yeah the whole bits to bytes thing can be tricky ... for a 10GB  file on a 100Gb network .......   I get 80 seconds ..... of course thats theoretical best case - no NW interrupts etc.  

1Gbit/sec  becomes    125MByte/sec   

then    10GB / 125MB   = 80 seconds

  If the wait time can be less than 5 minutes  than thats acceptable

---

### Post by koenn on 2008-03-02
> **HW_Hack said:**
>  .......   I get 80 seconds ..... of course thats theoretical best case - no NW interrupts etc.  
But that is assuming every student can use the full 1GB. If users access the server concurrently, the total available throughput will be shared amongst them. I went by mrsteveman1's estimation for concurrent use of the available 1GB & including network overhead : 25 mbps

10 GB file = 10240 MB
10240 x 8 = 81920 Mbit
25 mbps per student 
81920 / 25 = 3276.8 sec
3276.8 / 60 = 54.6 minutes

if we guestimate 40 mbps per student  (1024 mbps x 80% (network overhead) / 20 students ), I get 34 minutes. 
Quite long. 
That means that eg copying the files to the local machines when class starts, would take half an hour. Am I overlooking something ?

---

### Post by mrsteveman1 on 2008-03-02
The 25mbps figure is what each student gets out of a single 1GigE pipe on the server: 

```
(1000mbps/20 students) = 50mbps * 50% to account for overhead = 25mbps 
```

 So yea, on a 1GigE link on the server, an hour is correct for a 10gb file at 25mbps. Very slow and unacceptable.

In a normal network situation, you'd have statistical multiplexing to help out, not everyone uses the entire pipe at the same time. But here, since each student is going to be pulling files from the server at the start of a class, and pushing them back at the end, its quite likely that you will have 20 students all maxing the server line at the same time.

With 10GigE instead of 1GigE for the server <--> switch connection you would get closer to 250mbps per student, which amounts to around 5 minutes of transfer for a 10gig file.

---

### Post by HW_Hack on 2008-03-02
> **koenn said:**
> But that is assuming every student can use the full 1GB. If users access the server concurrently, the total available throughput will be shared amongst them. I went by mrsteveman1's estimation for concurrent use of the available 1GB & including network overhead : 25 mbps

10 GB file = 10240 MB
10240 x 8 = 81920 Mbit
25 mbps per student 
81920 / 25 = 3276.8 sec
3276.8 / 60 = 54.6 minutes

if we guestimate 40 mbps per student  (1024 mbps x 80% (network overhead) / 20 students ), I get 34 minutes. 
Quite long. 
That means that eg copying the files to the local machines when class starts, would take half an hour. Am I overlooking something ?


YIKES !!  Yes I like MrStevemans derating method as it is pretty conservative. And YIKES at the price of a 10GbE switch !

**What if I pushed more work back on to the server by using 2 1GB PCI-E cards (and 2 IP addresses)  with each card serving 10 - 12 machines again thu a 1Gb switch ??**

MrSteveMans number is worst case ... from my observations of actual HS classes / students .... all 20 kids will not hit the "return key" to start copying files at the same time ... there is always a little social chit-chatting at class start - role is taken - some class discussion - etc. During all of this some of the eager beavers will login and xfer files ... then some others -- followed by the last of those who can't stop (or are forced to stop) chit-chatting. 

If I assume activity in bursts of 5 - 8 students I get down to 5 - 6 minutes  ... and on the save at class end - not all files will have changed (video clips being cut into the main project file. 

Maybe there is hope .... but of course hope does not lead to a solid solution.

---

### Post by mrsteveman1 on 2008-03-02
What equipment is already in use on the network? What model switches etc?

I do know there are ways to aggregate traffic over multiple ethernet ports with Linux, but it gets very complicated when you do that unless you divide the traffic into separate subnets.

You might be able to get away with dividing the class into, for example, 3 vlans, and use 3  1GigE cards in the server, one per vlan. Your router would have to handle vlan trunking to do this (or use 3 separate router ports) but it would work, you could then just have the server listen on all 3 cards and respond etc. This would give you approx 6 students per 1gig link, or around 90mbps, working out like this:

```
 (1000mbps/6) = ~180mbps * 50% overhead = ~90mbps per student
```

That works out to around 20 minutes per 10gig transfer worst case.

Definitely see what your hardware supports, there isn't any real reason that everything has to be on one single link, VLANs would work well in a case like this, especially since vlans are cheaper than 10GigE copper equipment.

---

### Post by The Cog on 2008-03-03
It's fine splitting the students into small groups on different network cards to share the traffic load out, but don't forget to account for the disk bandwidth. I have no idea where that might become the bottleneck, but it needs to be considered.

---

### Post by mrsteveman1 on 2008-03-03
With disk bandwidth, you might hit some problems without raid for sure. 

From some quick calculations, most hard drives sold right now can handle upwards of 60MB/s or 480mbps read/write in a continuous stream. Some disks can even hit 90MB/s or around 720mbps and up. So if you have multiple disks in a raid5 array, you can probably count on being able to read at the aggregate of the disks speeds.

With writes you have overhead due to parity calculations and writes, so perhaps more like:

```
480mbps * number of disks * 70% 
```




Raid5 array usable size can be calculated like this:

```
s * (n - 1)/n
```

Where S is the total size of all disks, and N is the number of disks.

If you use 4 disks you can probably get high performance while staying away from the expensive 8 port raid cards etc. So perhaps, if you need 1TB of usable space you should consider using 4 400gb disks, which would give you 1600gb * (4 - 1)/4 = 1200gb. This would then also give you upwards of 1920 mbps reading and around 1440mbps writing over the whole array.

---

### Post by uberlinux on 2008-03-04
If the fileserver is talking to macs, why can't the admin just get ssh keys set up on all the clients, and use a bash script to hit each workstation in sequence?  That should help with contention.

---

### Post by sciurus on 2008-03-13
> I work as a tech specialist for a large high school (that covers the $$ cheap requirement) --- we want to start an advanced film making class where a student project file (all the clips + music + effects) could easily average 10 - 20GB file size. And consider 20 or more students.

I think you're overengineering. The solution isn't a server and new network infrastructure, the solution is to make sure the video workstations have large enough hard drives to store the students' work. A 500GB hard drive is $100.

---

### Post by koenn on 2008-03-13
> **sciurus said:**
> I think you're overengineering. The solution isn't a server and new network infrastructure, the solution is to make sure the video workstations have large enough hard drives to store the students' work. A 500GB hard drive is $100.

 - I had the impression from the OP that there was some kind of free seating, while your sollution requires students to always take the same workstation.

 - You're suggestion lacks an proposal for an adequate backup sollution

so, if you can work that in to what you're proposing, and you may have a point.

---

### Post by mrsteveman1 on 2008-03-13
The network and server storage are pretty much a requirement due to the backup problem. Perhaps just assign students to a machine and backup all of them in sequence at night to their own folder on the server, so that you at least have a backup of their work, but no need to tax the network to 10Gbps+ every single day.

---

### Post by NateMan on 2008-03-13
Isn't harddrive space measured in GigaBytes and data transfer speeds measured in GigaBits? If so that would put your math off by a factor of 8. Besides, it also seems that your math is based on your network getting advertised speeds, which from experience I can tell you won't happen. If you want to do this cheaply and fast, you might want to to consider trunking multiple ports to increase speeds. Those are very large files for transferring every class period, so something would have to be done to speed this up.  I'll do some math if your interested in what would actually be necessary. What is the exact filesize and how long do you want the transfers to be?

---

### Post by koenn on 2008-03-14
you can find the data you ask for and some calculations in post 13 and following - network overhead included (20-50 %)

---

