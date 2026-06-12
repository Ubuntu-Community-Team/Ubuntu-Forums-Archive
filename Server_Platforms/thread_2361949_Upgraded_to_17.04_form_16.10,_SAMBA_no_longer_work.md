---
title: "Upgraded to 17.04 form 16.10, SAMBA no longer works with XP Pro x64."
date: 2017-05-22
forum: Server Platforms
---

### Post by Michael_McKenney on 2017-05-22
I was on Ubuntu 16.10.   Samba was working great with Windows 7 x64 and XP Pro x64.   My tape backup is XP Pro x64 using Symantec Backup Exec 2010.   I have var, www, and topology as SAMBA links.  I can see them after the upgrade on my Windows 7 x64 workstation with no problem.   I can't log into them with XP Pro x64.   I have 4 web sites on this box that I backup to tape.   Any suggestions on how to fix it?  I was thinking of uninstalling SAMBA,  Rebooting,  Reinstalling SAMBA with a clean conf.

---

### Post by wildmanne39 on 2017-05-22
*Thread moved to **Server Platforms**.*

---

### Post by Michael_McKenney on 2017-05-22
Thanks.

---

### Post by Michael_McKenney on 2017-05-23
Anyone have any ideas?   Do I try removing and recreating SAMBA?

---

### Post by darkod on 2017-05-23
Are you talking about ubuntu server or desktop? And you are using non-LTS releases?

Always stick to LTS even for basic home server. The rest have only 9 months support, basically as soon as you configure your setup, you have to upgrade...

I would say the samba version got upgraded, and maybe XP doesn't like that. It's an ancient OS anyway.

Compare the samba version that comes with both distributions, and then google around if XP has some issues with it. You can find any package version here: [https://packages.ubuntu.com/](https://packages.ubuntu.com/)

PS. You might not like it, but my two cents worth... Production linux servers are for stability and long term running. Not to be upgraded or "played with" each 6-9 months. Hence most people use only LTS Ubuntu Server versions. Don't be surprised if things break down, especially when upgrading non-LTS to non-LTS. I am not.... In my personal opinion I see the non-LTS releases as tests for the real one, the next LTS (every two years). So I am not surprised if things break down in non-LTS upgrade.

---

### Post by Michael_McKenney on 2017-05-23
Interesting question.  I was on Ubuntu 16.10 and it prompted me to upgrade to 17.04.   I told it yes.  Anyway to uninstall Samba and send it back to the older version?  I do have the web sites backed up.  I did consider going back to 16.10 but it would take time to restore my main web site that is 240 GB.  The other three would be easy at 50 MB.  

XP Pro x64 is ancient.  It is the only OS that works with my Symantec Backup Exec 2010 with my HP LTO 4 and two Exabyte VXA-320 tape drives.  I have my Windows 7 x64, XP Pro x64 and Ubuntu Web boxes that I backup to tape.  I can take them offsite when I go on vacation.  Tapes don't get viruses like a hard drive does that backs up all the time.   I looked at newer tape backup software.  All of it runs on Windows servers.

```
16.10
master-of-masters for salt, the distributed remote execution system
[samba]("https://packages.ubuntu.com/yakkety/samba") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
SMB/CIFS file, print, and login server for Unix
[samba-client]("https://packages.ubuntu.com/yakkety/samba-client")
virtual package provided by [smbclient]("https://packages.ubuntu.com/smbclient")
[samba-common]("https://packages.ubuntu.com/yakkety/samba-common") (2:4.4.5+dfsg-2ubuntu5.5) [**security**]
common files used by both the Samba server and client
[samba-common-bin]("https://packages.ubuntu.com/yakkety/samba-common-bin") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba common files used by both the server and the client
[samba-dbg]("https://packages.ubuntu.com/yakkety/samba-dbg") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba debugging symbols
[samba-dev]("https://packages.ubuntu.com/yakkety/samba-dev") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
tools for extending Samba
[samba-dsdb-modules]("https://packages.ubuntu.com/yakkety/samba-dsdb-modules") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba Directory Services Database
[samba-libs]("https://packages.ubuntu.com/yakkety/samba-libs") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba core libraries
[samba-testsuite]("https://packages.ubuntu.com/yakkety/samba-testsuite") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**universe**] [**security**]
test suite from Samba
[samba-vfs-modules]("https://packages.ubuntu.com/yakkety/samba-vfs-modules") (2:4.4.5+dfsg-2ubuntu5.5 [amd64, i386], 2:4.4.5+dfsg-2ubuntu5 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba Virtual FileSystem plugins
```
 
 
```
17.04
master-of-masters for salt, the distributed remote execution system
[samba]("https://packages.ubuntu.com/zesty/samba") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
SMB/CIFS file, print, and login server for Unix
[samba-client]("https://packages.ubuntu.com/zesty/samba-client")
virtual package provided by [smbclient]("https://packages.ubuntu.com/smbclient")
[samba-common]("https://packages.ubuntu.com/zesty/samba-common") (2:4.5.8+dfsg-0ubuntu0.17.04.1) [**security**]
common files used by both the Samba server and client
[samba-common-bin]("https://packages.ubuntu.com/zesty/samba-common-bin") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba common files used by both the server and the client
[samba-dev]("https://packages.ubuntu.com/zesty/samba-dev") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
tools for extending Samba
[samba-dsdb-modules]("https://packages.ubuntu.com/zesty/samba-dsdb-modules") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba Directory Services Database
[samba-libs]("https://packages.ubuntu.com/zesty/samba-libs") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba core libraries
[samba-testsuite]("https://packages.ubuntu.com/zesty/samba-testsuite") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**universe**] [**security**]
test suite from Samba
[samba-vfs-modules]("https://packages.ubuntu.com/zesty/samba-vfs-modules") (2:4.5.8+dfsg-0ubuntu0.17.04.1 [amd64, i386], 2:4.5.4+dfsg-1ubuntu2 [arm64, armhf, powerpc, ppc64el, s390x]) [**security**]
Samba Virtual FileSystem plugins
```

---

### Post by darkod on 2017-05-23
I tried searching if XP needs something special with samba 4.5.8 (that comes with 17.04) but I didn't find anything relevant.

You could try:
1. Making a copy of your smb.conf
2. Purge samba (so that it removes the smb.conf too)
3. Install samba again (it will be the same version, you can't tell the ubuntu repository to install you older version)
4. Keep the smb.conf that was created by the new samba install, compare it with your smb.conf and add just the parts you need. DO NOT replace the whole smb.conf file. Samba is usually designed to work out of the box with it's default smb.conf. So just add your necessary settings into it, do not overwrite the whole file with your old smb.conf. These steps worked for me once although it wasn't the same case as yours...

---

### Post by Michael_McKenney on 2017-05-23
I spent 2 days in Google looking for an answer.   Since Windows 7 works and XP Pro does not, I wonder if it is a bug and I need to backup the Web sites and reinstall to an earlier version like 16.04.  

I have done this before.   I know to cut and paste or type in the contents to SMB.Conf.

---

### Post by darkod on 2017-05-23
Sorry I can't help more. If you do decide to rebuild the server using your backups, I suggest you use 16.04 LTS. It has 5yrs support (until 2021) which gives you plenty of time to plan upgrade/migration once the next LTS comes out in 2018. You don't need to rush anything because 16.04 will be supported until 2021.

---

### Post by TheFu on 2017-05-23
For samba, perhaps forcing v1 SMB is necessary for XP?  Just throwing that out. Thought v2 wasn't forced until Win10.

Amanda or Bacula?  Saw that Amanda supports the VXA-320 in the amanda forums. 
Didn't look at the HP drive, but lots of LTO drives are supported.

There are lots of reasons to prefer F/LOSS solutions whenever possible, though not always possible.

---

### Post by Michael_McKenney on 2017-05-24
I would agree with you.   I will probably go back to 16.04 LTS over the weekend after making sure everything is backed up to its external drive and another source.   16.10 fixed a performance issue on the network adapters backing up over a share.  I will see if a clean install of 16.04 resolves it.

I tried Bacula.   It was slow and did not work that well.   Symantec Backup 2010 does all three boxes.   Paid Bacula support was $2500.   I have two Windows workstations to backup too.   

How can I get SAMBA to use v1 SMB?   I am considering backing up and reinstalling 16.04 or 16.10.   I need to find the folders with everything I have setup for the 4 web sites to work.

I can even set the min protocol to the lowest level.

the selected protocol level after protocol negotiation. It can be one of CORE, COREPLUS, 			LANMAN1, LANMAN2, NT1, SMB2_02, SMB2_10, SMB2_22, SMB2_24, SMB3_00 or SMB2_FF.

I would think LANMAN1 would be XP Pro

Where do I add the min protocol = statement in SMB.conf?

---

### Post by Morbius1 on 2017-05-25
If your intention is to set "min protocol" ( which is "server min protocol" ) to LANMAN1 there is no need since it's already set at that level by default:
> tester@vxub1704:~$ [COLOR=#0000cd]**testparm -sv | grep "server min protocol"**[/COLOR]
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Processing section "[Test]"
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE

    [COLOR=#0000cd]**server min protocol = LANMAN1**[/COLOR]
lanman1 pre-dates WinNT. And since the "max" level is SMB3 the samba server will negotiate the level of SMB it will use to communicate with the client from Win98 all the way to Win10.

*Correction: lanman1 actually pre-dates WIn98.*

---

### Post by Michael_McKenney on 2017-05-25
My intention is to get XP Pro x64 to log into UbuntuWeb so I can backup to my tapes.   Something broke upgrading to 17.04.   So I can backup to my external drive all four web sites and reinstall Ubuntu and setup the web site again or find another alternative to get XP Pro x64 to get pasted Access is denied!

---

### Post by Morbius1 on 2017-05-25
I don't know what UbuntuWeb is but if this is a question about WinXP accessing a Linux samba share - which doesn't work - while access from Win7 does I have no idea. Doesn't make much sense on the surface. If it works for one it should work for the other.

Why not post the output of this command so the folks here can see how your machine is set up:
```
testparm -s
```

---

### Post by Michael_McKenney on 2017-05-25
UbuntuWeb is the Ubuntu 17.04 web server.  I can run that tonight and post back.

---

### Post by Michael_McKenney on 2017-05-25
```
michael@UbuntuWeb:~$ sudo su
[sudo] password for michael: 
[EMAIL="root@UbuntuWeb:/home/michael"]root@UbuntuWeb:/home/michael[/EMAIL]# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[var]"
Processing section "[www]"
Processing section "[topology]"
Loaded services file OK.
Server role: ROLE_STANDALONE
# Global parameters
[global]
 server string = %h server (Samba, Ubuntu)
 workgroup = VIPERNETWORK666
 log file = /var/log/samba/log.%m
 max log size = 1000
 syslog = 0
 panic action = /usr/share/samba/panic-action %d
 usershare allow guests = Yes
 map to guest = Bad User
 obey pam restrictions = Yes
 pam password change = Yes
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 passwd program = /usr/bin/passwd %u
 server role = standalone server
 unix password sync = Yes
 dns proxy = No
 idmap config * : backend = tdb

[printers]
 comment = All Printers
 path = /var/spool/samba
 browseable = No
 printable = Yes
 create mask = 0700

[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers

[var]
 path = /var
 read only = No
 valid users = Michael

[www]
 path = /var/www
 read only = No
 valid users = Michael

[topology]
 path = /home/michael/virl/topology
 read only = No
 valid users = Michael
[EMAIL="root@UbuntuWeb:/home/michael"]root@UbuntuWeb:/home/michael[/EMAIL]#
```

---

### Post by darkod on 2017-05-26
So you are publishing your /var/www over the internet as samba share? For backup purposes?

---

### Post by Morbius1 on 2017-05-26
I'm going to focus on the [topology] share. Depending on your answer to darkod's question I don't want to appear to be aiding such activity.

You have no Linux / Samba user named Michael:
> [topology]
path = /home/michael/virl/topology
read only = No
valid users = [COLOR=#0000cd]**Michael**[/COLOR]
It should look like this:
> [topology]
path = /home/michael/virl/topology
read only = No
valid users = [COLOR=#0000cd]**michael**[/COLOR]
You may very well have a Windows user named that however and the way you "map" the two is with another line in the [global] section of  smb.conf:
```
username map = /etc/samba/smbusers
```
If the file doesn’t exist create it first then add the mapping:
```
michael = Michael
```
Save the file and restart smbd.

Of couse all of this assumes you have added michael to the samba password database:
```
sudo smbpasswd -a michael
```

---

### Post by Michael_McKenney on 2017-05-26
I have had this backup server for 15+ years with tape drives.   SAMBA share are for my three workstations.  I do most of my Cisco and Web projects on my Win 7 workstation.   I can get into all four web sites and add and remove content.   I have Adobe Photoshop and other tools on Win 7.    XP Pro is just my Symantec Backup Exec 2010 box.    UbuntuWeb is just the web server.   SAMBA is not allowed past the Fortinet 60E firewall.  

Yes, var/www is being backed up as a share by Symantec Backup Exec 2010.   Symantec does not have a Linux client for this box.  I did setup a Linux backup program to my backup drive.   I use the tape drives to backup the 4 web sites.   My main one is over 240GB, all my vacation and family pictures.  The rest 90MB.   I don't trust backup hard drives.   I replace tapes every few years since I backup once a week or when I make big changes.  Topology is where I keep my Cisco Packet Tracer and Cisco VIRL projects for my CCNP and CCDP.  

I will verify the username and make it match the case on all 3 boxes.   I can see all the partitions on Win 7 with the names like this.

---

### Post by darkod on 2017-05-26
Well, I don't think I can help too much. We already discussed the idea of using 16.04 instead of the non-LTS 17.04. That is one option.

Why I asked about the samba traffic (regardless if it goes over open internet or not, worse if it does), is because you can also consider making a local backup on the web server, then transfer that file using ssh/rsync session. Even if it from a windows box (your XP with the tape drive), cigwyn should be able to perform that operation I think.

I know you are surely used to the system you had until now, but something obviously is not working. Maybe it is only the username thing (don't forget in linux a capital letter is never the same as smallcase), maybe because samba version got upgraded with your upgrade 16.10->17.04, don't know... But if you are willing to explore other options, you have some above...

Honestly I would go with 16.04 because it is LTS and if it works like that, that means you can keep backing up like you were so far. No ssh, no rsync, nothing changes except the ubuntu version. Which should have been LTS for such an important server anyway... I have to say that I don't understand you, you seem to be very interested to protect this server with all sorts of backups, but not interested to stick only to LTS releases for its OS. Even for servers that are not that important, the natural choice is always LTS... For important ones I wouldn't even think about using non-LTS.

---

### Post by Michael_McKenney on 2017-05-26
I run a Microsoft only data center.   I can do anything with Microsoft, firewalls, etc.   Ubuntu is just a new OS I have been playing with for years.   I learned how to do the web site.  Setup NICs and SAMBA.  I got it down to a few hours.   Studying for my Cisco, VMware, and ISC2 certs does not leave much time to learn Ubuntu.  I also have a 20 month old daughter who wants a lot of daddy time.   So I come to this forum when I have time.   I am coming to the conclusion of going back to 16.04 or 16.10.  16.10 fixes a performance issue with the NIC.  I did not do a clean install of 16.04 LTS to see if that fixed the NIC performance.   Copying the smaller web sites is not bad.  It is moving the 240GB site that takes hours.   

So this weekend make sure I have two good copies on hard drives of the web sites and topology and the files I need for configuring the web sites.  Then reinstall Ubuntu from scratch.  I should start with 16.04 LTS.  OK.

Do I do server or workstation?  All it has is SAMBA and Web services.

---

### Post by darkod on 2017-05-26
I would use the server version. But even though I am primarily windows guy, I don't depend on a gui for linux. Your case might be different...

Installing the desktop version will add a number of packages and gui things that have no benefit for the server functions, but they eat up your resources... If you have a monster machine and would like to still do it, go ahead... The choice is yours really.

---

### Post by TheFu on 2017-05-26
> **Michael_McKenney said:**
>  
I will verify the username and make it match the case on all 3 boxes.   I can see all the partitions on Win 7 with the names like this.

No.  Usernames need to be lowercase.  No mixed case.

Same for hostnames.  All lowercase. Same reason.

There are too many reasons for this and really none of them should matter, but ... volunteers don't always make clean code. 

Other thing is to always have a blank line at the end of any config file.  EOF and EOL aren't the same, sometimes volunteers don't handle both situations.

---

### Post by Michael_McKenney on 2017-05-26
I asked you because you know Linux.   I trust your opinion.  I can't find where I can get you points on my posts.  

 My Windows 7 workstation is 1360W AC on a 20A circuit.   It is a server with SAS RAID and 15K SAS drives.  It is fully optimized.  UbuntuWeb was a low power web server that was built to play with.  It is 97W.  A Intel Core 2 Duo, 2GB ram, 1 Gbps NIC.   It is very low end.  I was considering upgrading it to a newer Intel CPU, 4-8 GB of RAM, a doing RAID 1 or 10.  I built it to learn HTML 5.   Since I now host and design my brother's company web site on it.   It might be time to upgrade it.   I think my Win 7 workstation laughed at its micro-ATX motherboard.  

[www.michaelmckenney.com]("http://www.michaelmckenney.com") :   Family web site, vacation pictures,  my daughter's videos and pictures
[www.scsiraidguru.com]("http://www.scsiraidguru.com"):  My technical and resume web site
[www.mylibertarianblogpage.com]("http://www.mylibertarianblogpage.com"):  It was getting a lot of hits during the elections and now that I am working on Term Limits for Congress. 
[www.patrickmckenneylandscaping.com]("http://www.patrickmckenneylandscaping.com"):  He is getting more hits now that he is also on FB

What would you think for the next revision of it?  I would like RAID 1 or RAID 10 on a decent controller not onboard.

---

### Post by Michael_McKenney on 2017-05-26
Downloaded 16.04.02 LTS Server 64-bit and burned it to a thumb drive.

---

### Post by darkod on 2017-05-26
Revision (upgrade) of your ubuntu server?

I wouldn't waste money on raid controller. decent board with sufficient number of sata ports is enough. Linux servers work much better IMHO with its mdadm software raid. And it's HW independent. Your board and raid card burn out, just stick the disks into new machine and it boots up and off it goes... HW raid can be difficult to restore sometimes if your card goes. No one guarantees you 100% new card even of the same model will be able to read the disks without needing to make new clean raid.

As for cpu, ram, etc, linux server doesn't need much. In fact, if you don't see any issues while it's in use now, it can probably stay for a number of years on the Core2 Duo... Maybe small RAM expansion from the 2GB, otherwise it's not so bad...

---

### Post by Michael_McKenney on 2017-05-26
So do software RAID over hardware RAID?   I know about hardware RAID.  My Win 7 workstation has an LSI Logic 8708EM2 battery cached raid controller with 15K SAS drives.   It takes the load off the CPU.   LSI SAS RAID can upgrade RAID controllers with no issues.  It just reads the configuration from the drives.   I have swapped out SAS RAID before with no issues.   Just install the new drivers for it before shutting down.   SATA RAID is a completely different animal.  


You think the current CPU is fine.  Just upgrade the RAM from 2GB.  It does have room in the chassis for hard drives.   The Intel board does have other SATA ports.  If I do a clean install, how hard is it to do software RAID in Linux?

---

### Post by TheFu on 2017-05-26
I agree. For a home server, a C2D is fine.  I run lots of VMs with 512MB of RAM assigned.  Used to run 10 VMs on a C2D with 8G of RAM for 3 businesses.  
Network performance doesn't usually matter much about the CPU. Having an Intel PRO/1000 NIC matters more. The NIC ASICs do all the work, not the CPU, unlike with other NICs.  If you are seeing 650+Mbps, I wouldn't worry either way.  Mine test to 920Mbps, but real-world, using ssh tunnels, I see 650-700Mbps.

Agree that HW-RAID is usually a waste.  Makes sense **only** in a business where the performance is really necessary.  Streaming videos don't need that.  SW-RAID using mdadm works well.  I've moved SW-RAID disks across 3 different servers with very different SATA controllers. Never had any issues.

Don't use Fake-RAID. It has all the limitations of HW-RAID, without the performance, which is the only reason to use HW-RAID over SW-RAID on linux.  Linux SW-RAID is extremely flexible. It just needs access to JBOD.

I wouldn't load 16.04.2.  I'd load 16.04.1.  There are subtle reasons these are different with different kernels and different support periods. The 16.04.1 line kernels have support until 2021.  The .2 line gets about 12 months of support.  [https://wiki.ubuntu.com/Kernel/Support#A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/Support#A16.04.x_Ubuntu_Kernel_Support) has a chart.

---

### Post by Michael_McKenney on 2017-05-26
Spending money on hardware is not a problem up to a certain point.  My wife is not sure about a $1000 for a new tape drive.  

I am used to hardware RAID and performance.  

My backup speed to take is 1650-1680 MB/min in Symantec Backup Exec.   I can't remember if it is an Intel or Dlink Gigabit adapter in it.   It did help with performance.   I did not want to spend $$$ on a server NIC but it might be worth it.  Maybe I need to get a Intel Pro Server grade NIC to improve performance?  I used them in my data center in the past.  

RAM is cheap.  Should I get 4 or 8 GB?  

I have videos of my daughter on it from my Galaxy S6 that sometimes loads slow.  I was thinking RAID 1 or 10 could help with it.  I don't do RAID 5 because of write performance hits.  Even on my SAN at work is RAID 10.   Since I am backing up this box, NIC performance would matter to speed up the backups.   

Any other suggestions?   

I can get 16.04.1 Server.  I will find it now.

---

### Post by Michael_McKenney on 2017-05-26
Looked for 16.04.1.  This is what I get to on alternative downloads.  Where would you get it?  

Select an architecture to install 16.04 with Xenial's 4.4 GA kernel

or

Ubuntu 16.04 LTS (Xenial Xerus) Netboot with HWE kernel

or the version I downloaded?  

Ubuntu Server 16.04.2 LTSThe Long Term Support version of Ubuntu Server, including the Mitaka release of OpenStack and support guaranteed until April 2021 &#8212; 64-bit only.

---

### Post by TheFu on 2017-05-26
RAM isn't that important if you don't use it.  Otherwise, it just becomes disk and network buffers to hide slower disk I/O.

If that is all the performance for the tape drive, I doubt faster NICs would matter.  We live in an age of GigE is GigE for the most part.  It isn't like 2002 when a cheap GigE would provide 200Mbsps, tops.  Definitely no need for a server-class NIC.  The $25 Intel PRO/1000 does fine.

I would expect a SAN to be RAID-10.  Some folks here work in huge class-1A data centers with tens of thousands of servers.

If you want videos to work faster on devices, optimize the file by transcoding it to be smaller.  My Canon camera makes beautiful videos, but they are huge. Transcoding makes then 10x+ smaller without **any** impact to resolution or adding any artifacts.  Plus, the wifi network probably impacts streaming more than anything else.

I'd get 16.04.1 from my ISO server from SW-RAID1 storage. ;)  That doesn't help you. Since I live in Squidbilly-land, I'd pull it from Georgia Tech's mirror.  Doesn't matter where you get it. Just make certain to validate the sha256sums.

You don't want the HWE kernel - that's the part that only gets 9-12 months of support. Basically, you are forced to move to 16.04.2 --> .3 --> .4 --> .5 every 9-12 months to maintain support.  This is a subtle thing that many non-enterprise admins don't understand.

If you want to stay on 16.04.1, be certain to use **apt safe-upgrade**, not *apt dist-upgrade*.

---

### Post by Michael_McKenney on 2017-05-26
I finally found 16.04.1 Server 64 bit.  I will look at transcoding videos.  Never thought about it.

---

### Post by TheFu on 2017-05-26
HW devices that make videos tend to use 'real-time' encoding which wastes lots and lots of space in trade for speed.  That extra size makes extra work for every client and more work on the network.

**Handbrake** is an easy to use transcoder. It is cross-platform. I only use it on Linux.  If you set constant quality to 19.5 and use h.264/vorb/mk4 formats, you'll be amazed.

---

### Post by Michael_McKenney on 2017-05-26
My only concern is corruption and losing my daughters videos.   I have videos from my late mother singing in Rome for Pope John Paul II in 2000 with her church choir.  I would not want to lose them.  

One issue that 17.04 fixed was /boot is much larger.   It seemed that earlier version had a very small /boot and it would get filled constantly.  Anyway to stop Ubuntu from upgrading automatically and filling /boot up?

---

### Post by darkod on 2017-05-26
Use manual partitioning and choose your own /boot size. No need to depend on the automated partitioning methods. I agree, /boot is created very small using them. But even with that smaller /boot you can still be OK. Basically just kernels fill it up. Do regular old kernels removal with 'apt-get autoremove' and /boot fill not get filled up very easily.

But I would still go with the option of bigger /boot, like 2GB or similar.

---

### Post by TheFu on 2017-05-26
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) probably has an explanation.  How partitions are sized is something I don't let automatically happen.  I always "do something else" and handle it based on 25+ yrs of experience.

I don't allow any automatic updates - ever.  And patch all my systems weekly during approved maintenance periods.

If you care about disk corruption, there's only 1 file system - ZFS.  It verifies what was sent to the disk is actually written. **No other FS does that.**  Also, it is strongly recommended to use ECC RAM with ZFS systems.  Don't know if Ubuntu can be boot from ZFS. That is a common thing for Linux file systems - you can use them for anything, but only a few are supported for boot.  ZFS includes an LVM and RAID capability all in one.  When you create a pool, you say the redundancy level.  Adding disks can increase the redundancy. If you add SSDs, they can be designated as cache disks to help overall file system performance.  ZFS has their own CIFS implementation too - at least on Solaris.

ZFS does lots more, for a price, usually more RAM. It likes RAM if you use the advanced features.  I've never used ZFS on Linux, just Solaris.

But we are so far off topic now. Time to open new threads for other questions.

---

### Post by Michael_McKenney on 2017-05-26
I found two 1 TB 3.5" SATA WD Black 5 year drives that I will get to do RAID 1 with.  $80 each.  

I am used to partitioning VMware and Windows Servers.   I started in 1982 with IBM DOS with 32 MB limitations.  I have not done a Linux install creating partitions since the 80s or early 90s.  I have never done Ubuntu partitioning.  Once I setup RAID 1.   How do I partition it.  I might add RAM to the box before I start.

---

### Post by darkod on 2017-05-26
Do you mean HW raid using your raid controller? Or the mdadm SW raid we suggested?

Because your partitioning question has different answers depending on that.

---

### Post by Michael_McKenney on 2017-05-26
I am going to follow your recommendations.  So backup everything x2.  Install two new drives for SATA RAID 1. I might do more RAM. Then, 16.04.01 LTS with software RAID.  I figure software RAID will need to be done before installing.   I also want to check/change partition sizes.

---

### Post by darkod on 2017-05-26
You can setup mdadm raid during the server installer. Note that for mdadm raid you use partitions, not whole disks. So even if you want single raid1 array with whole disk, first create single partition spanning the whole disk, then you create mdadm array from it. And you use that array just as you would use any ordinary partition.

You don't need separate /boot if using raid1, but you can create it if you want to. In such case, create small partitions at front of disk for one /boot raid1 array, then big partitions for the / array, and then swap partitions (swap doesn't need to be in raid but it can if you prefer it).

I usually prefer creating the partitions in advance, using ubuntu desktop live cd/usb for example, and then during the server installer I just tell it how to use the partitions. If creating partitions in advance don't forget that you don't need to format them. They are used for raid md device, and it is the md devices that get formatted and mounted.

As for the sizes, you decide yourself. Check out your current usage and layout, then decide new layout. On 1TB disks you could have for example:
16 or 32GB for /
the rest for big data array, mounted at /data or /var if you prefer
swap (sized as you prefer)

The design of the partitions is up to you, and you can compare how much size you have now in /var for example, if most of your data is there... In the new server you can make it separate partition, mounted at /var.

---

### Post by Michael_McKenney on 2017-05-26
This is what the last clean install of 16.10 did.

Filesystem      Size  Used Avail Use% Mounted on
udev            964M     0  964M   0% /dev
tmpfs           198M  6.8M  191M   4% /run
/dev/sda1       456G  248G  185G  58% /
tmpfs           986M   12K  986M   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           986M     0  986M   0% /sys/fs/cgroup
tmpfs           198M  168K  197M   1% /run/user/1000
/dev/sdb1       932G  496G  437G  54% /media/michael/Backup
tmpfs           198M     0  198M   0% /run/user/0
[EMAIL="root@UbuntuWeb:/"]root@UbuntuWeb:/[/EMAIL]#

With CODE tags:
```
Filesystem      Size  Used Avail Use% Mounted on
udev            964M     0  964M   0% /dev
tmpfs           198M  6.8M  191M   4% /run
/dev/sda1       456G  248G  185G  58% /
tmpfs           986M   12K  986M   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           986M     0  986M   0% /sys/fs/cgroup
tmpfs           198M  168K  197M   1% /run/user/1000
/dev/sdb1       932G  496G  437G  54% /media/michael/Backup
tmpfs           198M     0  198M   0% /run/user/0
[EMAIL="root@UbuntuWeb:/"]root@UbuntuWeb:/[/EMAIL]#
```

---

### Post by darkod on 2017-05-26
Well, that has a single / partition of 456GB. Out of which you have used 248GB.

My point was, if most of those 248GB is in /var, you can maybe decide to have smallish / and separate /var for the big data made up of big partitions.

You can get the /var size by this, for example:
```
sudo du -sh /var
```

Note, it might run longer if you have much data in it, like it looks you have...

PS. If you've decided to handle linux servers, read some basic info about mount points. They are powerful tool, but can be confusing for starters. Windows has something similar (mounting a volume to an empty ntfs folder) but it is rarely used (more or less).

In linux basically any empty folder can be a mount point where you can mount a partition or md array. And the space of that volume is assigned to that folder path.

For example you can have 50GB / partition and 950GB partition mounted at /var. Even though when browsing (and in the structure in general) var is shown as folder inside /, the actuall size you will have assigned for / and its subfolders (but without var) will be 50GB, and for /var and its subfolders you have the 950GB.
You can also create any custom empty folder and use it as mount point, for example /data.

---

### Post by Michael_McKenney on 2017-05-26
243 GB in /var.   My main web site is 240GB.    I cracked open my box.  It is all ATA drives, DVD + HD.   So I might get a new micro-ATX chassis for the Intel DG33TL board and a new power supply along with the drives.   Will 50GB be enough for / ?

---

### Post by darkod on 2017-05-27
50GB is plenty for / if you mount another volume for where your big data will be. In your case that seems to be /var. Take into account that basic ubuntu server install is around 2GB only. What matters is the location of the big data, like www files, mysql databases, KVM files, etc...

In your case you have 248GB used and 243GB of that is in /var. So that means the rest of the "system files" are only 5GB. Even a / smaller than 50GB would work. My home server has a / of 32GB and earlier it was only 16GB and was working fine. I added more when adding bigger disks but didn't really need it. Right now / usage stands at around 7.5GB.

---

### Post by Michael_McKenney on 2017-05-27
So I could do a live boot.  Create RAID 1 and / and /var only?  Do I need /swap or anything else or will it just go under / by itself?   

SATA Two 1 TB WD Black drives
Corsair power supply
SATA DVD drive 

Maybe a newer chassis.   My chassis is an old AT style.

---

### Post by vasa1 on 2017-05-27
Hi,

Please use CODE tags when providing material copy pasted from your terminal or from a log file.

As you can see in [post #42]("https://ubuntuforums.org/showthread.php?t=2361949&p=13649705#post13649705") in this thread, I've added code tags but also left the original for you to compare. With code tags added, thing line up nicely.

Please oblige. Thanks!

---

### Post by darkod on 2017-05-27
swap does not go under /. In linux the swap space are separate partitions marked as swap space. That's how the OS knows to use them... So if you want swap, you should create partition (usually on the end of the disk) on each disk. For example 4GB, which will give you total of 8GB. No need to raid it, the OS will use whole of it.

Another thing you need to consider when using manual partitioning, is whether you plan UEFI boot or not. For legacy boot and msdos table on the disks you don't need anything special. But for UEFI you need the EFI system partition at the beginning of each disk as far as I know. I don't use UEFI so don't have much details about it, you will need to investigate online.

Unless I'm mistaken, for the EFI partition they recommend 250MiB FAT16/FAT32 partition, and the boot flag on it. I don't recall if the filesystem needed to be FAT16 or FAT32. Check it out.

So, depending whether you will use UEFI or not, the partitions you would create as preparation on each disk would be:
250MiB   FAT16/FAT32, boot flag
50GiB   no filesystem
950GiB   no filesystem
4GiB   swap area

Then during the installation in the manual partitioning step, it will show you all these existing partitions. Select one by one all 4 raid partitions, and for them in Use As select physical device for RAID. For the swap partitions select Use As: swap area.

When you are back to the list, in the top section you have the option Configure Software RAID. Create two raid1 arrays from the 2x 50GB and 2x 950GB partitions. After that in the partitions list these two raid devices will show.

Select the 50GB raid1 device and Use As: ext4 (I assume you want to use ext4 filesystem). Mount point /.
For the 950GB raid1 device, Use As: ext4, mount point: /var.

That's it. The rest of the install process is identical.

---

### Post by Michael_McKenney on 2017-05-28
I upgraded the RAM to 6GB.  I did a single 1 TB SATA drive instead of RAID 1.   I put 16.04.1 on a 8GB USB drive to install it. 

50GB /
12GB /swap
rest  /var

It did not ask to pick a partition to install to.   I can always reinstall if it did not choose the first one, /

---

### Post by darkod on 2017-05-29
I didn't understand your last comment. When you install with manual partitioning and for the 50GB partition you select the mount point to be /, that is telling the installer where to install. There is no other specific question that it will ask you. By the mount point it knows where you want it to be installed.

Is that what you meant?

---

### Post by Michael_McKenney on 2017-05-29
Thanks for you help.  I did configure the partitions like you said.   

Sorry for the confusing post.  

Installed 16.04.1 Server.  The web site is back up and running.   Replaced the power supply, hard drive and added RAM.   I added Ubuntu desktop, samba, and apache2.  Made it easier to copy files having desktop. 

/ is 50GB primary.  It did install properly to it.

Add these lines to SAMBA SMB.conf to fix XP Pro x64.    
   ntlm auth = yes
   lanman auth = yes
   client ntlm auth = yes
   client lanman auth = yes
   client ntlmv2 auth = yes

I attached the old ATA hard drive after I installed Ubuntu to new drive and copied over the web sites.   The SATA drive is slightly faster on backups to tape drives.   I have not checked to see if the 6GB of RAM is helping with disk caching.  Not sure if I needed 12GB /swap partition.   It can't hurt with 6GB of RAM.   I might see if Apache2 can be configured to use more RAM or the NIC can use it to cache.

---

