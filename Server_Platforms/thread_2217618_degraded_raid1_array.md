---
title: "degraded raid1 array"
date: 2014-04-18
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-04-18
I am gradually working my way towards perfection. I have just set up my email server - works now with no errors.
I just got this system message.

A DegradedArray event had been detected on md device /dev/md127.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid1 sdc3[0]
      310472064 blocks [2/1] [U_]
      
md0 : active raid1 sda1[0] sdb1[1]
      96244 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sdb5[1] sda5[0]
      15623096 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sda6[0] sdb6[1]
      472660856 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

how do I fix it?

---

### Post by TheFu on 2014-04-18
How to fix it depends on what is bad.  
* Replace a bad cable
* Replace a bad HDD
* Replace a bad disk controller
* Replace a bad power connecter/PSU

---

### Post by astarmathsandphysics on 2014-04-18
i dont think it is any of those things. It is a remote server anyway

---

### Post by TheFu on 2014-04-18
Those are the only reasons that I know for mdadm to "degrade an array".  I think you'll be surprised when you finally figure this out.

In 2006 when I first started using mdadm, I had an external 4disk array that had a loose SATA cable. The vibrations from the PSU caused it to loosen over time ... monthly.  For the first 6 months, it would degrade and I'd get a warning.  Eventually, I swapped out the single SATA cable with a 90-deg plug version and that array as been working flawlessly ever since - except for the few hours when I swapped out the 320G HDDs for 2TB HDDs last year.

Just sayin'.  Remote or local - how does that matter at all?  Talk with the on-site people.

Our "beliefs" don't impact what is really happening. ;)

---

### Post by astarmathsandphysics on 2014-04-18
Surprising what you learn. I will talk to my host.

---

### Post by SeijiSensei on 2014-04-18
> **astarmathsandphysics said:**
> i dont think it is any of those things. It is a remote server anyway

I dumped my physical servers a while back and now use virtual machines at [Linode](http://www.linode.com/).  For a modest monthly fee I've delegated the hardware maintenance problem to them and get large Internet pipes and well-regulated power as well.  The only downside is that extra storage can be expensive, but unless you have lots of accounts, an e-mail server doesn't require much in the way of storage.  For [$20/month]("https://www.linode.com/pricing") you get a machine with 2 GB of memory and 48 GB of SSD disk storage.  Since the OS only occupies a couple of those 48 GB, you have lots of space to store mail.

---

### Post by TheFu on 2014-04-18
$20/month is $240/yr.

In 2010, I swapped out the MB, CPU, RAM in an existing machine to a gen-1 Core i5-750 8G RAM for $380 - that was 4 yrs ago.  That machine runs 8-10 business VMs 24/7. For a simple email server, a VM only needs 384MB of RAM and 5-10G of storage, so a cheaper VPS could be used. There is a Core2Duo as failover ... uh ... older. That was provided by a client so $0.

We run Zimbra, so it needs 1.5+G of RAM and 20G of storage. For email, bandwidth doesn't really matter after "broadband" is provided, just having an open port 25 does.  We all "need" broadband anyway, so that isn't an extra expense. My electric bill is about $7/month more running 6 extra machines than I would otherwise have running.  Right now, under 190W is being drawn by 3 machines, VoIP, phone, and network equipment.  These run email, CRM, wikimedia, project management, file server, remote desktops, development code control (git), and a few others - all for the same, single price in 2010.

If you only want/need 1 VM, putting it remote can make perfect sense.  If you really want to control the number of VMs and avoid getting charged extra for more IPs, more SSL certs, more disk on a monthly basis ... then running those things on your own premises almost always makes more sense from a cost standpoint. Dropping a micro Amazon EC2 instances as an email gateway for $175/yr is an easy choice. [https://aws.amazon.com/ec2/pricing/](https://aws.amazon.com/ec2/pricing/)  The only time storage is needed there is when your premise email is down. For me, that happens during nightly backups for less than 4 minutes and for about 2-4 hrs per year when the broadband connection has some issue - it is actually much less than that - 2 hrs every 3-5 yrs here.  Power doesn't really go out more than the UPS devices handle.

Neither solution is a bad choice, but if you don't use "servers" in the solution at home, power draw and noise really becomes very unimportant. Being a system admin for stuff like this may not be something interesting. It certainly has periods of "suck."  Hardware never fails when it is convenient, but it hardly ever fails.  With good planning, great backups, almost all these things are mitigated.  Putting stuff on someone-elses-computer does NOT mitigate all problems. It just redirects the responsibility to fix hardware to someone else. Data corruption, backups, security, configuration are still yours.

That linode price could be great - in 2G of RAM, I bet 5 useful LXC instances would run great!

---

### Post by SeijiSensei on 2014-04-19
I switched to Linode in part for financial reasons.  I was paying over $100/month to Verizon for a business FiOS connection just to run the server in my house.  Now I pay about the same amount for Internet/CATV/phone over a residential connection, and about $50/month to Linode for two VMs, one in NJ and one in CA.  With an OpenVPN tunnel back to my home office, I can deploy services on this end, too, without paying for business Internet.
> Putting stuff on someone-elses-computer does NOT mitigate all problems. It just redirects the responsibility to fix hardware to someone else. Data corruption, backups, security, configuration are still yours.

Of course, but those problems would arise no matter where the servers reside.  As for backups, I pay the $5/month additional fee for nightly snapshot backups of my VMs.  I also make off-site backups with rsync, but being able to spin up last night's backup as a new VM can be a life-saver (been there, done that).  Linode only charges for the time your server is running.  I've spun up a test server and deleted it the same day for no cost whatsoever.

You can also log into the host and mount your VM as a filesystem.  That came in handy once when I accidentally broke the OpenSSL implementation on one machine and a whole host of necessary apps like SSH failed as a result.  I mounted the VM from the web-based terminal, installed the missing OpenSSL libraries, and spun it back up.  "Priceless."

Linode is also pretty pro-active about maintenance.  If they were a public company, I'd buy stock.

---

