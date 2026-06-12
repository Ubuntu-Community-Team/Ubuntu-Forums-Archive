---
title: "Ubuntu server - Nextcloud, firewall questions and some other stuff"
date: 2021-12-29
forum: Server Platforms
---

### Post by uipojehdx on 2021-12-29
Hi there,

I have just installed ubuntu server (20.04.3) for the first time and I am gradually learning the basics of managing a headless user, I am a home user. I have managed to mount my NAS shares and installed Roon and HQPlayer (music software) but thats about it so far.

I noted when going through the install that I could include check Nextcloud, which I did, but I have not managed to find any instructions what to do post server setup - does anyone have a link to a guide or similar?

The server sits on my home network behind a hardware firewall (Netgear Orbi in router mode, you can't actually see or adjust the firewall I believe), I note the firewall is not enabled initially on the Server, and I find conflicting information about the necessity of doing so, however coming from microsoft I am hardwired to wanting a firewall, so should I set up? I have confused myself previously with firewalls and I know I will need to configure to get the music software working with it on, indeed I believe HQ Player will need a stateful firewall, any tips or guides would be really helpful.

Any other stuff I should do at this early stage?

Thanks.

---

### Post by slickymaster on 2021-12-29
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2021-12-29
NextCloud is a PHP web application so it needs a web server and also a database server.  I have used Apache and MariaDB.

I tend to not utilize "apt install nextcloud" because that always installs an outdated version and it packages/installs Apache/MariaDB along with it which is not typically what I like to do.

I like configuring my web server (with Apache) and tailor it how I want to use it...which typically will host multiple sites/applications.

I also make use of a single, separate, dedicated MariaDB database server which also houses multiple application databases.  However, you could host the web and database services on the same machine if you like.

Here is a list of steps I take when setting up a [NextCloud server](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=282).  This might be way more information than you want but you can take it with a grain of salt along with a slew of other how-to guides out there.  I also have a guides for [Apache](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=278) and [MariaDB](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=279) but make sure you are installing the latest stable version of MariaDB.

LHammonds

---

### Post by schragge on 2021-12-29
> **uipojehdx said:**
> I noted when going through the install that I could include check Nextcloud, which I did, but I have not managed to find any instructions what to do post server setup - does anyone have a link to a guide or similar?
[How To Install and Configure Nextcloud on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04) @DigitalOcean
[Example installation on Ubuntu 20.04 LTS](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html) @docs.nextcloud.com

---

### Post by uipojehdx on 2021-12-29
Thanks for the replies, before I launch into trying to install Nextcloud, quick question - I sort of cobbled the machine together with a new case but various bits and pieces I had 'left over'. This included a very cheap 240GB SanDisk ULTRA II PLUS SSD, and I wondered if I should grab a nvme as a faster alternative - my gigabyte Z390 UD motherboard supports them (something like a 250g samsung evo??). Would I see much performance increase if I did this?

---

### Post by TheFu on 2021-12-29
> **uipojehdx said:**
> Thanks for the replies, before I launch into trying to install Nextcloud, quick question - I sort of cobbled the machine together with a new case but various bits and pieces I had 'left over'. This included a very cheap 240GB SanDisk ULTRA II PLUS SSD, and I wondered if I should grab a nvme as a faster alternative - my gigabyte Z390 UD motherboard supports them (something like a 250g samsung evo??). Would I see much performance increase if I did this?

NVMe for stuff like nextcloud is overkill, IMHO, especially at home.  But it is your money.  I wouldn't use any SSD for nextcloud. That storage is just too expensive for making 5TB of stuff available.

I've been running Nextcloud inside a virtual machine for years. It was installed manually and gets upgraded about every month.  I leave the Ubuntu supported version of php or mariaDB alone.  Most of the storage that Nextcloud can access is over read-only NFS mounts.  I just don't trust the webapp.  Also, I will never, ever, allow it to be accessed over the internet without either an ssh SOCKS5 proxy or full VPN like wireguard or openvpn.  These all work well.

For what might be slowing down the system, you'll need to look at CPU, RAM, networking, disk and other I/O issues.  Typically, 1 will jump out as the problem to be fixed. Once that is fixed, then next problem will jump out ... to be corrected.  Keep doing that until you run out of money or are happy with performance. ;)   Monitoring tools like SysUsage, Nagios, Cacti, and 50 others capture all the data you need to watch.  Usually, we have to look at all the data over weeks of time to see patterns and the true bottleneck for any system.

I am looking to pull Nextcloud out of a virtual machine and move it into an LXD container - or perhaps some other container - to get lower overheard.  It is currently running on a 4TB Gold WD drive (the VM storage is there) and has been about 18 months.  The system has a Samsung EVO NVMe inside it, but I won't be putting a DBMS onto that - not ever. I want longer lifetimes for my storage devices. A DBMS isn't really something I'd place onto SSD storage, unless it is trivial with very low transaction rates.

My nextcloud VM storage:
```
$ df -Th
Filesystem                  Type      Size  Used Avail Use% Mounted on
/dev/vda1                   ext4       19G   13G  4.7G  74% / 
romulus:/raid/media/Music   nfs4      1.8T  1.7T   12G 100% /M
istar:/d/D1/ebooks/Library  nfs4      3.5T  3.5T   18G 100% /B
romulus:/export/gallery     nfs4      151G  108G   36G  76% /P
```

The VM storage I'm using is qcow2 for this system. Not exactly the fastest. I really should correct that in the new setup. It will be a logical volume provided to the VM as a block device ... unless I move to a container, then it will probably be a ZFS device since LXD really wants ZFS storage.

---

### Post by uipojehdx on 2021-12-31
Thanks for the reply. I have read it quite a few times and I am still not sure I understand all of it as a novice. I have used it to go off and read up on various bits and pieces though so its really helpful. I think I might pause the nextcloud implementation for the time being untill I understand it a bit more and the advantages it might bring. 

I think I need to understand more on the UFW really and whether to turn it on or not. I don't believe its stateful, which will hinder the HQ Player software, however I don't know this definitively yet.

---

### Post by TheFu on 2021-12-31
> **uipojehdx said:**
> Thanks for the reply. I have read it quite a few times and I am still not sure I understand all of it as a novice. I have used it to go off and read up on various bits and pieces though so its really helpful. I think I might pause the nextcloud implementation for the time being untill I understand it a bit more and the advantages it might bring. 

I think I need to understand more on the UFW really and whether to turn it on or not. I don't believe its stateful, which will hinder the HQ Player software, however I don't know this definitively yet.

UFW is just an interface into the kernel firewall - actually, it creates iptables rules which interface with the kernel firewall. It is fine for simple setups.  The typical use is for desktops that block all incoming connections not from the same LAN and allow any outbound connections at all.  If you don't allow nextcloud naken on the internet, that would be fine. 
Should you do like  LHammonds and I by manually installing nextcloud as compared to using a package installer?  I cannot say.  We like to control things and don't trust some random person on the internet to do it well.  Also, the nextcloud project is constantly updating - at least a few times each month, so I'd be loath to go with any method that doesn't originate directly from the team behind the webapp. I'd avoid Canonical's package, just like  LHammonds does. It will always be a security risk and out of date.  

The real power of Nextcloud is in the addon modules.  Not running a recent, supported, version of Nextcloud will preclude access to updates for those addons, many of those updates will be security related.  With any sort of all-in-one package solution, how to get addons installed and working will be a question.  I don't know the actual answer about it. I just know that I barely use the file sync aspects of Nextcloud and use it the vast majority of the time through addons.

As usual, the choice becomes, do something easy now that required huge effort going forward
or
spend more time now and hope that the future effort isn't too bad.
You could go with a 3rd solution .... go with the quick answer now, knowing that in 2 months it will need to be wiped and started over.  However, lots of people do stuff like that and there are over a million Wordpress blogs that have been hacked on the internet right now.  All because someone took the easy solution.  If you don't put nextcloud naked on the internet - i.e. always require a VPN to access it, then it is very likely NOT to get hacked, but there are lots of other risks in running any network service on the internet that sits on the same LAN as other typical home computers and devices.  IoT stuff gets hacked all the time due to this. Things that people think cannot be hacked because it is behind a router+firewall get hacked all the time.   [https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices](https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices)

Off topic: BTW, don't use UPnP er ... ever.  That's the way that gaming consoles open firewall ports on routers to make things easier, but 1,000,000x less secure.  Disable UPnP in the router settings.  This is an FBI and NSA recommendation. [https://krebsonsecurity.com/2018/05/fbi-kindly-reboot-your-router-now-please/](https://krebsonsecurity.com/2018/05/fbi-kindly-reboot-your-router-now-please/)  Home routers almost always have security related bugs.  A few brands try to stay patched and provide support for more than 3 yrs, but most do not. Home routers aren't designed to be hammered on the internet by attackers. An edge router is the first like of defense for most users and we need to have the right tool for the job. I wouldn't suggest that people get a Cisco router ($$$$) for their homes, but neither should they be using the $50 home internet router from 4+ yrs ago with the stock firmware delivered in the box.

---

