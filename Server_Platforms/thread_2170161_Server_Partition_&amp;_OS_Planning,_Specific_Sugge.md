---
title: "Server Partition &amp; OS Planning, Specific Suggestions Welcomed"
date: 2013-08-25
forum: Server Platforms
---

### Post by Azaling on 2013-08-25
Greetings.  I'm new to the forums and to administering Linux, although I'm not new to being a *nix user in general.  I am currently building a new machine and would like the forum's advice on making a partition plan that might best suit this particular machine.  I've read several partitioning guide articles already, but without experience on what's "really" needed, I'm still feeling uncertain.  The following paragraphs explain what I have and what I'm looking to do.  Specific suggestions and reasoning are welcome and encouraged!

  **Role**: Server for Home use, with normally 2 but occasionally up to 4 simultaneous users.  File server for mixed-client environment, DNS, RADIUS, LDAP, squid, NTP, possibly additional services in the future.  Will almost always be accessed remotely.  Might be nice to have a GUI available to start up occasionally for programming work and testing, but this GUI wouldn't need to be running most of the time.

**Hardware**: 2TB platter HDD x2.  Intended for RAID1 complete mirroring, including the OS if possible.  8GB RAM since it's hard to buy less than that nowadays.

**Desires**: I want to use as much of the 2TB space as possible for file storage, so I don't want there to be a lot of wasted space in partitions dedicated to the OS.  (For instance, no need to make a 1GB /boot partition if it only needs 1/10th that much space or less - assuming that's a true statement).

**Cuurently-Planned OS**: Ubuntu Server 12.04 LTS

**Proposed Partition Plan** ("Educated guess"):
/ : 2GB
/tmp : 1GB
/swap : 1GB
(total dedicated to OS = 4GB)
extended
/export/backups : 300GB [cron backups of other computers]
/export/installers : 20GB
/export/fileserver : remaining 1676GB

**Questions**:
 -Is that OS a reasonable choice for the desired machine role?  I read that Server Edition doesn't come with GNOME; how do I make GNOME available for the infrequent times I might want to start it up?

-Is that a reasonable partition plan for the desired roles?   Or what would you do differently?  And how much space will each of your suggested partitions really need, based on what the OS will typically install to it?  I have no preference on making few partitions or tons of partitions, so be as creative as you like with your suggestions.  But please do explain why you chose what you did - I'm interested in learning the whys from your point of view!

Please really dig into those ideas if they warrant it and help me improve them.

---

### Post by TheFu on 2013-08-25
"Really needed" can mean lots of things.  You didn't mention any performance needs - 2TB HDDs will probably be slow.  2GB is not enough for the OS and making the OS RAID adds complexities that someone new to being a sysadmin just isn't ready for.  I've been doing it for 20+ yrs and don't have software RAID for my OS installs - Data - hell, yes, but not for the OS. I have good backups.  RAID is never a replacement for good backups.  If you are not planning to have a backup disk - I'd strongly, very strongly, suggest you NOT use RAID and make the 2nd HDD a backup disk instead.

Ok - onto the partitioning.[LIST]
[*]Use GPT, not MBR partitioning. Lots of reasons, including greater safety. Read the wikipedia page on that.
[*]/ - 20GB - this will hold /usr, /var, /tmp ... plus all the garbage GUI crap you seem to want. 10G would be the smallest, but with small partitions, you'll be screwed out of inodes and might run out with 5G of storage available. Trust me. 20G - do not RAID this. You can manually make a similar partition on the 2nd HDD of the same size and us rsync to mirror the data over every week, month or so. That will be enough protection. Do not let them have the same UUID.
[*]/home - 300G - probably want this to be network storage for the different users on the network and mounting private areas by login there is easier; Use software RAID on this.
[*]/export - Why call it export? I use "/Data" or "/D." Shorter is better for a few reasons that you won't believe - shorter typing is always good too.  /export is an old-school name left over from NFS. Use software RAID on this.
[/LIST]
12.04 is what I run. I don't bother with non-LTS releases. Check my signature and the links for why.

You didn't talk about clients. Which OSes will those run?  For sharing storage, NFS is best for UNIX-based systems. You'll have full file permissions control that way. Samba is a poor choice in comparison, but we live with it for Windows clients.  Also, don't backup the backups for other machines, but don't forget to backup data only on THIS machine to storage somewhere else, especially the installed packages and settings.

Under /Data, make the directories you want.

Why have different partitions for backups, ISOs, installers at all? Just use file permissions to prevent unwanted viewers. KISS - Keep It Simple S....
A 2TB HDD will provide 1.9TB of available storage after formatting - 1912523780 is the number I'm seeing here.

If you must have a GUI, no that system stability will be impacted just by loading the libraries. Not to mention that GUIs are huge.  Use LXDE or XFCE - avoid Unity or any solution that needs compositing.

It is a best practice to have 1 system do 1 thing. All those services that you've listed will make this box complex, harder to maintain, very hard to secure, nearly impossible to upgrade. Have you considered using virtual machines for each service? In that way, you can segment the risks, segment the upgrades - good things.  I have a 10.04 box running lots of services - I've lost track how many and which ones. I also run lots of VMs.  Upgrading VMs is relatively easy, since if I make a mistake, I know exactly what is unavailable. It is also easier to try new things out on VMs ... like OS upgrades without risk to the "production" system.

BTW, if this is your first server, you will make lots and lots of mistakes. I have and I still do from time to time and I've been doing this since 1993.  I hope your mistakes never lead to data loss. Good luck and have fun!

---

### Post by gordintoronto on 2013-08-25
Don't bother with tmp or swap partitions. Do assign 20 GB for /, as TheFu suggested. +1 for 12.04 and XFCE.

You will be running lots of processes, and sometimes a process runs amok and starts pumping out log entries. If root is tight for space, your server falls over, and it's difficult to get it running again.

---

### Post by Azaling on 2013-08-26
Thanks for your detailed reply and your follow-up questions, TheFu!   I'll address your last question first, and then all the rest from top to  bottom.  Let me fill in the holes I hadn't realized I left in my OP. :)

*Yes,  this is my first server build, so I expect both questions and  mistakes.  I'm hoping to ask the former to avoid at least some of the  latter!  This server is going to be a replacement for an aging NAS  appliance in my home network.  Rather than get a new consumer NAS  appliance, I wanted to build something with a bit more oomph that could  provide more services.  All the hardware is built (relatively  inexpensive Core i3 IvyBridge based), so now I'm asking questions to  learn the best way to build the right software suite on top of it.  I'm  interested in doing things well wherever possible - security, best  practices, and such - and respect folks' expert and experienced  opinions.

*I meant "really needed" in terms of disk space, and  that phrase was a reaction to some of the partitioning articles I had  read.  The outlook of the authors sometimes seemed to be that if we only  expect to ever write 100MB of data to a given partition, we should make  it 5GB just because we have oodles of disk space and can do so.  That  works, but I get the feeling we can allocate space more efficiently.  I  recognize the need for a healthy amount of wiggle-room in disk space  allocated, no worries there, but at the same time I am hoping to avoid  the aforementioned style of overkill.  So I want to allocate Enough, but  not Too Much to each partition for the OS.  'Tis an art I suspect.

*I  don't think I have any stringent performance needs for this system, at  least that I know of.  It will be providing a set of basic network  services to just two users, from a single-port GbE Intel NIC and over an  infrastructure of unmanaged home-grade switches.  The HDDs are brand  new 6Gbps SATA ones plugged into a compatible controller (mainboard), so  I would think that in a heavy data transfer scenario the network  connection would get saturated before the HDDs would.  So, I'm thinking  it's probably OK that the 2TB consumer platter HDDs are slower than SSDs  or high-RPM enterprise-level HDDs.  Unless I'm misunderstanding what  you were commenting about for this aspect?

*You hit this one  right on the head - I wasn't planning to have a dedicated backup HDD  since I have just two drives in the system.  So I'll bite - if I have  two identical drives available, what type of improvement would your  suggestion of having a cron'd backup from one drive to the other bring  over having a RAID1 mirror create a second copy of everything on the  fly?  I'd certainly consider the suggestion.

*I'm interested in  having an Ubuntu GUI available in general, but I suppose it doesn't have  to be on the server system now that I think about it.  I didn't realize  that a GUI was as big of an extra or troublemaker in this context as it  must be from how you reacted!  Using a different machine/VM to interact  with the fileserver would work just as well.  I'm happy to go that  route.  So, scratch the GUI.  Check.

*/export defintely doesn't  have to be named that - 'twas a suggestion that I read in the  probably-old articles on Ubuntu partitioning.  I'm just as happy with  /data or /d.  Since less typing and shorter names are better (I believe  it if they bothered to shorten "temp" to "tmp"), let's go with /d.

*Clients  for this server will be Win7, WinXP, OSX, and several flavors of  Linux.  As a result I expect a Samba service will be required.  Would it  be desirable to have NFS share the same files as well?  (I know SMB  well, but know only a little of NFS so far).

*I hadn't considered  making this box host multiple VMs.  If any of the services were going  to be publicly available or exposed to the internet, using VMs would be  the first way I'd want to go.  But yeah, since this is for small home  internal use, I hadn't given that route any thought in this situation.   The hardware is certainly powerful enough to run multiple lightweight  VMs, so it is indeed an option.  What would you suggest for this  approach - an ESX underpinning with multiple Ubuntu Server VMs?  Or  could Ubuntu be both host and guest OS in the same manner?  I don't know  if I'll end up making it one box or a bunch of VMs, but I'm open to  exploring both approaches.

Thanks again for your comments and suggestions.  That's the kind of honest and direct feedback I was looking for!

Ah, I see gordintoronto has also replied since I started typing my reply (but took a break to go to work).  Roger that.  Thanks for your advice.  So you're suggesting a set of {root, /home, /d} only, like TheFu did?

---

### Post by TheFu on 2013-08-26
Great dialog here, thanks!

* GigE vs HDD performance.  For burst transfers, the HDD will seem to keep up with the network, but that falls off as soon as all the RAM for disk cache is used, then the spinning disks can only handle about 40MB/s.  I see 75+MB/s for most transfers on my network ... until the cache fills up.  The SATA 3Gps or 6Gps specs mean next to nothing on spinning disks.  It won't be the network holding back your large transfers, trust me.


* RAID vs Backup - Having a RAID 1 system means that if one of those disks fails, the other should still work, just in a slightly slower mode for reads (proper RAID systems read data from both HDDs to make reads faster). That's great, but you still need a backup to different media/physical disks.  
** RAID will write the same corrupted file to both disks, without a backup, how do you correct that?
** RAID will spread an infected file to both disks, without a versioned backup, how do you correct that?
** RAID systems are more complex than single disk mounts - extra complexity, add in LVM, add a new admin, add an unknown failure - they are always unknown failures initially - mistakes can happen. These mistakes lead to data loss.  Without a backup, how do you recover without lots of manual labour, hard work, and remembering everything you did 1, 2, 3, 4, 5 years ago?
Versioned backups are really easy to do these days, really fast, and highly space efficient. See my signature links.  If you don't have backups, you have no business having RAID.  Most of my systems have 30 days of daily backups written to a server on the networks. It takes about 10% more storage than just having a mirrored backup (1 day).  So if a box is 100G, then 30 days of nightly backups for that box is 110G. How cool is that?
Oh - and RAID for a backup storage at home is a complete waste. How many failures do you want to protect against?  BTW, anything over 1 becomes a crazy attempt a redundancy, IMHO.

* VMs; maintenance, upgrades, clearly known services.  As your new server gets more and more services, you'll end up with a box that you are afraid to bring down - it starts as a file server, but there is plenty of RAM and CPU, so you add a few more services and a few more and a few more.  I have a 1 box like that and I've been doing this with a home server since 1996. Every time I change anything on it, I'm afraid. Changing the OS is a huge hassle, full of fear. My box still runs 10.04 for that reason. I lost track of all the custom changes that have been made over the years. It has migrated from 6.06 to 8.04 to 10.04 and been swapped into 3 different physical systems in that time.  A few months ago, the 10.04 package manager became corrupt and has refused any new updates.  The last few months, I've tried to fix those every way that I know how - can't. Until it is patched, it cannot be migrated to 12.04. It is stuck and it is the center of my home network.

I've been running other services on VMs on the network too - these are for clients.  Each VM has a specific purpose. I haven't lost track and I've avoided putting too many features onto a single VM.  Most of these started out as 8.04 VMs and the migration to 10.04 followed by the migration to 12.04 all went smoothly. If there has been an issue with 1 VM, it wasn't the end of the world. I've blown them away completely and rebuilt it ... every build lets me apply new skills that have been learned over the years.  These days I try really, really, really hard to never use source code or .deb files or PPAs for installs. I try to stay with core programs only to keep APT from getting confused, dependency issues to a minimal and overall system stability as high as possible. People depend on these services being available and I honestly don't want to spend a weekend re-building a server.  I have a few major applications that were installed under 10.04 using non-packaged methods. Reading over the required upgrade steps will make your head spin. The entire stack has to be changed, including the OS.  How do you accomplish that on a single physical machine?  With VMs it is still a hassle, but at least it becomes a "how-much-RAM-do-I-have" question for the new VM, not a "where-do-I-get-a-spare-machine" question.

I'm just sayin' - think about the complexities of maintenance. BEFORE you are screwed. No matter how careful you are, you are going to screw this up.  I still do and I see it coming. Sometimes there isn't any choice.

* Samba vs NFS - Samba file permissions suck. You have ZERO control from the client. It is almost a joke how poor the file permissions control is.  NFS OTOH, provides the same file permissions control as being on the box itself (with a few extremely minor exceptions).  NFS is highly efficient - better than FTP (which nobody should use anymore) - way to move data around or just make it accessible to other client machines. If you have some storage available via NFS and a GigE network, accessing that storage for processing and everything else on clients is basically, just like local storage. It really is.  For non-portable client machines, having the same $HOME shared across all your UNIX/Linux machines is extremely convenient. It is hard to explain until you've experienced it.  Remember the old Sun Microsystems commercials - "the network is the computer"?  It has been true for me AT HOME since 1998.  Samba should only be used by MS-Windows clients. OSX and Linux understand NFS.

NFS is about the only service that I'd run directly on the hostOS and not inside a VM. I suppose samba fits there too.  Yes, you can share the same storage with both methods concurrently. 

Obviously, you want the client machines to be GigE connected to the server - if they are wifi, NFS is not a great idea for any storage connection.  WiFi is not as stable as most people think it is - the bandwidth changes constantly from very high to very low.  Just watch a wifi transfer for 5 minutes some time - the rate of transfer varies 80+% from a trickle to whatever the connection speed is.  On wired connections, that isn't an issue.  WiFi sucks when you need steady bandwidth ... like a file server.

---

### Post by mastablasta on 2013-08-26
regarding GUI -  you will be connecting to server from other mashcines and control it like that. server doesn't need it's own monitor, keyboard etc. 

now to make this contorl easier there are a couple of nice programmes out there. there are ofcourse various command line interfaces/terminal such as putty and others. well if you have linux you can just use it's terminal to access the server.

and then there are GUI for server where you control the server via a nice web browser interface. there are a couple of them available. popular one is **webmin**, but there is also **zentyal** (which even comes prepackaged in it's own ubuntu based distro) and a few others. check the web and some screenshots.

also there are windows managers available in case you don't really need full desktop, but you would really like some desktop stuff on it. check openbox or icewm. both are really really light. but again they are not necessary on server. i am not sure what you would do with them.

---

### Post by TheFu on 2013-08-26
> **mastablasta said:**
> ...  there are a couple of them available. popular one is **webmin**, but there is also **zentyal** (which even comes prepackaged in it's own ubuntu based distro) and a few others. check the web and some screenshots.

Any mention of running a web-based admin tool of any sort should include a few extra statements:
* These have been hacked in the recent past allowing attackers administrative access to the servers AND networks.
* If you must use one of these tools, please, please, please prevent access from any IPs that shouldn't have access **AND**
* use a non-trivial account over an encrypted SSL connection.

Don't trust anything on your LAN - don't trust anywhere on the internet.

---

### Post by Azaling on 2013-09-02
I wanted to follow back up with this thread to report in.  I read all the comments in this thread as well as the related links in TheFu's signature, and this is what I came up with as a result.

*You sold me on doing cron'd backups with the second HDD rather than RAID.  Accidental deletion and file corruption were risks I wasn't protecting against with the original plan, and ones that I was indeed always worried about in the back of my mind over the years.  I should have thought of that but didn't, so I'm glad someone was there to point it out to me!

*You also sold me on limiting the amount of services the base OS provides, and instead making it extensible using VMs.  The hardware to do this is available, so let's do it.  The base OS will just do files, printers, SSH for management, and VM hosting.  Anything else can each get its own VM.  Well, in the past I've made VMs just using vmware and a GUI, so it will be a learning experience figuring out how build new VMs from the command-line only that the server now has.

The server's built on its hardware now, though I just finished installing the OS so there's no real data on there yet (and thus is changeable easily if I did anything TOO terribly dumb).  I ended up using LVM throughout (ext4 standard on each volume) so that all choices can be easily adjusted in the future as hardware and needs dictate.

disk1 (primary): LVM containing:
 -40G : / for OS & future VMs
 -50G : /home
 -8G : swap (just in case it's needed with VMs running)
 -1.9T : /data (for everything else)

disk2 (backup): LVM containing:
 -2.0T : /backups

Now I need to find a good backup scheme for this; I read the links from TheFu, but I have both big 2GB files as well as small little files so I'm a bit uncertain which rsync-like tool would work best for this application.  There's always more reading to do!

Anyway, thanks again to all contributors here for their input.  You had some great suggestions that I think will improve both the reliability and maintainability of this server.  I appreciate all the time you took to write them out and help educate me!  This'll probably always be a work in progress, but all indications are that it's off to a good start.

---

### Post by Bucky Ball on 2013-09-02
*Thread moved to **Server Platforms**.*

This is its rightful home. 

Excellent and enlightening dialogue. Carry on, I'm listening. ;)

---

### Post by TheFu on 2013-09-02
Fantastic.  Some good choices in there ... even if they are different from what I'd do. You are "on the ground" and know what you need better than anyone else.

Virtualization - no need to do everything at the CLI for this.  Load KVM + virsh, then you can use virt-manager from any remote client to create, manage, destroy VMs. virt-manager is like the GUI for any of the VMware or VirtualBox tools. Easy.  I stopped creating VMs at the CLI when I stopped using Xen a few years ago. KVM + virt-manager makes me happy.  The virt-manager connection goes over ssh - on the VM host side, just make certain that your normal userid is in the libvirtd group. Then you will connect using your normal non-root credentials and will be able to manage all the VMs safely from everywhere in the world.

ssh - fail2ban should be installed with it.

At this point, I think you'll just be trying stuff to see how it goes.  If you have VM bloat/sprawl ... like we all do, you might want to look into automating the setup and maintaining the configuration using a tool like Ansible. Alas - that is for another thread. ;)

Almost forgot - 
For media files (audio/video), I would use straight rsync to mirror those directories.
For non-media files, I'd use rdiff-backup to get versioned backups.  To do these things, you'll want to split the files into different subdirectories.  Most media playback tools have a specific directory structure, which is probably fine. Don't worry about the .nfo or .xml or image files - the mirror is good enough for those things.  Versioning really pays off for emails, productivity app documents, setting files and stuff in your HOME.

Make sense?

---

