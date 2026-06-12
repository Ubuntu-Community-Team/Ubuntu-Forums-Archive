---
title: "Home Server Build (Hardware questions and what about FreeNAS?)"
date: 2010-08-22
forum: Server Platforms
---

### Post by ShakeyJake on 2010-08-22
Hey guys,

I'm looking at building a new home server and I have some questions. Currently I'm using an Ubuntu desktop as a server but it's a very simple affair with only one storage disk and the entirety oh /home shared. There's no redundancy, not enough storage space, no administration other than VNC and no web services. This machine is really a media player as it's small and pretty and was never meant to be a server, I'm building a new machine for that purpose effectively from scratch.

Things I'd like my server to be able to do:

-RAID 5 with the ability to add extra disks in time.
-Serve files to desktops and laptops (I would like to map folders on the server so they appear as bookmarks in GNOME)
-Be administered via a web browser.
-Share music via DAAP.
-Torrent (either via web admin or through watched folders)
-Email me status updates.
-Host a (very-low traffic) website.
-Have a web-visible shared folder.

As this is really a slightly more complicated NAS rather than a full-blown server I had originally settled on an Atom build inside a small 4-bay case with FreeNAS as the OS. This way I'd end up with a machine similar to a store-bought NAS. 

But then I got thinking, I have a few suitable components laying around (including a mid tower with 7 HDD bays) and for around the same money I could get something like an 45W Athlon 240e, 2GB low-voltage DDR3 and a MATX mobo with 6 sata ports (compared to the 2 on an atom). It's a much more powerful machine with a higher resale value and more scope to upgrade over time. The added power means that I could use it as a backup desktop or to rip/convert movies and the like. I've also read a few reports that say an Atom doesn't really have the crunch for software RAID.

How easy is it to set Ubuntu to do what I want? I'm not scared of the  command line but I'd be tempted to install the desktop version of 10.04, configure everything the easy way and then stop the GUI. Or would something like ubuntu-server and Webmin get me what I wanted? 

Thanks for any answers, musings, or 'check out my server' posts. All would be very welcomed. Building a desktop was so easy compared to this.

---

### Post by TNHarleyRider on 2010-08-22
Shakey Jake,

First, let me wish you luck with your server project.

I would like to offer my opinion on a few or the points you ask about, even if it is just to say that I agree.  For a point of reference, my home server is on a Supermicro ATOM server motherboard with SATA drives in a software RAID.  My servers at work are IBM xSeries with full hardware RAID and Xeon CPUs.

ATOM CPU:  Yeah, the ATOM isn't a very high end CPU, I'll give you that much.  I built my server on it after reading some articles about Supermicro having an ATOM based server in a 1U rackmount case that was only 11 inches deep.  I think their market was intended to be the builders of appliances such as software firewalls and perhaps lower end NAS devices.  I have a user community here at home of myself and my wife so the overhead isn't that large.   

Ubuntu Server vs Ubuntu Desktop:  "They" say that the server has differences which make it more ideal for use as a server.  If that's the case, and I have no reason to believe it isn't, then that would clearly be the OS of choice in the Ubuntu line.  If you hesitate to give up the GUI then you can also install a GUI desktop once Ubuntu server is installed.  All that said, I know someone who is running a production SMTP server on Ubuntu Desktop using a VMware guest system as the hardware and he claims to have no performance problems.

RAID:  Yep, I agree :) .  I think that RAID is a must for any kind of serious server.  Hard drives will eventually fail and restoring the file system from a backup is a serious PITA.  The motherboard (and some consumer grade) hardware RAID solutions don't have the best of reputations.  Many are told to use processes in the OS to function as compared to a true hardware RAID adapter that does everything inside the hardware.  My level of comfort at home wasn't sufficient to trust the Supermicro RAID adapter on the motherboard so I went with software RAID 1 (mirroring) instead.  So far it is OK and I have survived a HDD failure with a minimum of effort to rebuild the RAID on the replacement drive.  Software RAID 1 (I am told) works much better (performance wise) than RAID 5.  Individual mileage may vary.

If you are using SATA drives then you have a range of large drives to choose from at a reasonable cost.  You may find that you can accomplish your goals without needing to use RAID 5.  Granted, RAID 5 giving you the storage capacity of the sum off all your drives minus one for parity is more cost effective than using mirroring.  That said, RAID 5 was (I believe) developed for server systems using SCSI drives that cost several hundred dollars each.  Either RAID 5 or RAID 1 one will give you fault tolerance which is the name of the game.  The rest is just economics.

File serving:  You're post doesn't say what OS is on the client PCs.  My clients are Windows and SAMBA works well for file sharing.  The SAMBA install on Ubuntu server was easy.  Setup can be assisted by many different tutorials and websites.  Not too difficult, just setup the SAMBA parameters and shares inside a config file, get the Linux access rights setup and away you go.  If you want an environment like SAMBA taking the place of a Windows Domain Controller then you'll need to do a little more reading.  In my case, I manually synchronized user IDs and passwords on all the systems and everything works well for simple file sharing and centralization.

Web Admin:  I haven't used Webmin.  For web based server administration I would suggest eBOX.  If you are willing to take on the learning curve you can install SSH on Ubuntu Server and use something like PuTTY to do an SSH session to the server (command line server session) and it is just like being in front of the machine.  

Web visible shared folder:  Please let me know if you figure out how to do this.  I know of commercial software that does that kind of thing such as Novell iFolder and Sharepoint.  Password protection for access would be even better.

---

### Post by ShakeyJake on 2010-08-22
Thanks for your reply Harley,

My situation sounds pretty similar to yours. Very little use other than acting a central repository/backup for a handful of pcs belonging to 2 users.  The server will have to play nicely with:

Ubuntu Desktop
Crunchbang Netbook
Windows Server 2008R2 Desktop
Windows 7 Netbook
Windows 7 Laptop
TBC Media Player (Myth maybe, linux at least)

I'd like to have scheduled backups from the Ubuntu desktop, the rest will just need access to read/save files on the nas and stream music/videos from there as well. 

I have it set up currently (using samba) that the /home folder of the server is mapped in Nautilus on the linux machines. Put in a password and you're into the folder. This works well but I'd like to expand on the idea and have less storage on the clients and to for instance the ubuntu desktop would have an unused '/home/Jack/Videos' but there'd be a symlinked folder in there to a videos folder on the server. That's not an issue, that's more of the same as I've already got. 

I'm hoping a modern dual-core such as the Athlon would have enough power for software RAID 5. I'd be getting 3-4 2TB disks atm with a view to adding more later. It looks like the best option so far is to have Ubuntu Server on an OS disk then install webmin on that and use webmin to set up the RAID. That way for torrenting or other 'easy' tasks the server has a /home that isn't on the RAID and the array can spin down when not in use. I'd thought about a RAID 1 array but cannot justify the 'wasted' space, I cant believe I'm considering speniding this much on a server as it is. Even if there is a performance hit with RAID 5 it shouldn't really as it's just a fileserver, nothing too I/O intensive.

Is there anything you'd change about your build? How much storage space do you have?

---

### Post by TNHarleyRider on 2010-08-22
Indeed, our situations and goals do sound similar.  You care about a few things I don't as I'm sure that I'm into a few things that are of no concern to you.  Still, the root structure isn't that different.

For sharing files in a UNIX or Linux environment you should look at Network File System (NFS).  I can't help you much with that, I work with Windows clients.  As a result, my efforts have been with making a Linux server work with Windows clients.  A couple of links that may be useful are [https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html) and [http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29](http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29) .  

There's different ways of putting your My Documents directory and other associated directories on a server.  In an environment where you are running a domain controller the client (user and PC) logs into the domain.  This means that passwords are located in the domain controller (the SAMBA server in this case).  The PC recognizes the domain user accounts and groups as they are added in PC's Users and Groups under the Windows Management console.  This means that you can set things like home directory location and login script at the domain level.  The down side is that requires a fair amount of setup.

A simpler method is to set the location of My Documents to the server directory that you desire.  In your case it sounds like it would be in the Linux home directory.  On Windows Vista you can right click on Documents and select properties from the pop-up menu.  Select the Location tab and enter the new location.  The Move button *SHOULD* move the contents to the new location.  In Windows XP this was easier because all the user files were under My Documents (My Music, My Videos, etc.).  In Windows Vista they broke these out into directories at the same level as Documents so each must be addressed individually.

A different option is to maintain local copies of the documents and synchronize them back to the server.  This results in quicker access as the files are called up from the local HDD vs over your LAN.  You have automatically provided a backup as the individual document files are both on your server and on the local PC or PCs.  The down side is that you have not done anything to reduce the size of the local HDDs which you said was one of your goals.  There are some free software packages out there which do Windows backups to network locations.

Would I change anything if I was building my server over again?  LOL, I think that I would always want to change something.  That said, I have been pretty happy with the performance of my little server.  I have two 500 GB SATA drives in my server which is enough for current needs.  One thing I wish I had done was to build the OS on a separate, smaller HDD (or mirrored pair of HDDs) and then left the large HDD pair for user documents (/home and other user data directories).  This has been a long-standing recommendation from Microsoft and others in setting up servers and is the same philosophy that I follow at work.

If (or I should say when) I build my next server I think I will augment rather than replace.  I have two 500 GB SATA drives in my server which is enough for current needs.  One thing on my wish list is to create a server running VMware Server.  I could then host PCs on it as virtual machines (VMs) as opposed to buying another PC.  LOL, I can't see using an ATOM CPU for that.

---

### Post by quietas on 2010-08-23
For some good home server software ideas, here's a good link: [http://ubuntuforums.org/showthread.php?t=1075599](http://ubuntuforums.org/showthread.php?t=1075599)

---

### Post by ShakeyJake on 2010-08-24
That thread was actually really useful quietas. I'm pretty much settled on Ubuntu Server with Webmin now. I'm also going to go pretty powerful, a 240e and a few GBs of DDR3, that way it can do encoding and stuff rather than just sitting there. Having everything on the mobo turned off and with the scaling down of cpu cores this should idle at a pretty low power usage too.

---

### Post by sanlinhtet on 2010-10-12
Hi
Can you help me plz..
  I want to use 160 GB for Ubuntu Server and anothers two hardisk of 1 TB are as Mirror for only data. So, How can I setup it.
Plz guide me,,,

---

### Post by HermanAB on 2010-10-12
Howdy,

For a web shared folder, you can DIY it with Apache and WebDAV, or you can install Alfresco or KnowledgeTree.

---

### Post by borahshadow on 2010-10-14
One thing that you mentioned several times is the CPU usage of the RAID system. I want to tell you not to worry about that at all. On either an ATOM or the AMD. You could probably run linux software RAID off of a 386. It also will only really use CPU time when there is disk access which won't be all the time. 

What I am trying to say is that with *any* modern CPU software RAID's CPU usage is negligible at best.

Also even though it appears that you have decided on Ubuntu Server I would just like to support that decision. They use the same software repositories (hence why they are called "the same") ,but they have different kernels. I can't remember the exact differences in the Kernels but one is optimized for server environments and the other is optimized for the average Desktop user.

---

