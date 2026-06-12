---
title: "need to build home server"
date: 2014-08-02
forum: Server Platforms
---

### Post by t873sm on 2014-08-02
I would like to find some information about recommended hardware and instructions / guide on how to set everything up for a server.  I have a QNAP ds412.  It is too slow with the ARM processor and 256 RAM.   I would like to keep cost for the hardware < $1000US.  I am thinking of a RAID1 consisting of 2 128GB SSDs for system and a 4 disk RAID5 for storage.  I would like to be able to host websites, (ISP is Comcast, they have told me that is okay, but I cannot get a static IP).  So I would need to know how to overcome that as well.  I would like to have an email server, and host media.    I have tried to find the information and can only find outdated hardware information and pieces of the software requirements and setup.  I want to make sure that everything will work together.  I need to know if I should use Ubuntu or Ubuntu Server and what other applications to use and avoid.  I know that this is kind of a large question.  Any help would be appreciated, even if it is just links that will get a majority of this done.  If I have omitted any pertinent information, please let me know.  If this issue has been recently addressed, please send me a link.  Thanks for your time.

---

### Post by ljbade2 on 2014-08-03
What sort of web site are looking to run? How many requests to you expect?

You probably don't need a very fast CPU, you can use Intel Celerons, Pentiums and Core i3's in server motherboards.

I would recommend a server board if you can afford it as you can use ECC RAM which will reduce the chance of data corruption when you have a machine running 24/7. 
Otherwise any low end Intel chipset desktop motherboard will do - as long as it has plenty of SATA plugs.

I recently built a small mini-ITX home server using a Intel Celeron on a server motherboard. I use it for email and it is more than fast enough.

Most important piece of hardware for you will be the computer case, you will want one with lots of hard drive slots. Some good ones I have seen reviewed:
SilverStone DS380 -  designed for NAS, takes 8 hard drives with quick release acess
Fractal Design Node 304 - takes 6 hard drives
Fractal Design Node 804 - takes 10 hard drives
Fractal Deisgn Array R2 - designed for NAS, takes 6 drives + 1 SSD
Bitfenix Phenom Micro-ATX - takes 5 hard drives
Bitfenix Phenom Mini-ITX - takes 6 hard drives
Lian Li PC-Q25 - takes 5 hard drives, has quick release

All of these cases are very small too which is nice as it does not take up much space.

As for software this is what I have used:
Ubuntu Server 12.04
LVM storage - makes it easy to add and remove drives and can do RAID very easily
Postfix + Dovecot for emails - standard set up reccomended by Ubuntu, plenty of How-Tos available is you Google
Apache + PHP + MySQL for web server
Roundcube is the web-mail service

Works very well.

Finally - I would avoid RAID 5 as it is very bad when you have large (terabyte) drives and can cause you to lose data. RAID10 is the recommended setup for 4 drives now.

EDIT: About the static IP - you can use a system called dynamic DNS to get a domain name that always points to your current IP. Note however this is fine for web server and remote SSH, but will not work very well on an email server and you may find your emails get marked as spam (since most spam comes from computers on dynamic IPs).

If you can look at getting a business class Internet plan as these often come with static IP.

---

### Post by ljbade2 on 2014-08-03
As for choosing the hardware, I am not familiar with US prices as I am in Australia, however I quick check of NewEgg (which seems to be the de facto US store for PC parts) shows you can definitely build a good system for $800-$1000.

First thing you need to decide is which hard drives are you going to use? Are you going to re-use the drives from your current NAS? What capacity do you want if getting new ones?

Current NAS drives are 1TB, 2TB, 3TB or 4TB. In your RAID10 you would then get 2TB, 4TB, 6TB or 8TB total storage.

I would only pick certified NAS drives as standard desktop drives are not designed for 24x7 running or use in RAIDs or servers. In fact the manufacturer will not cover use of normal drives in a server, RAID or NAS under warranty.

Basically this leaves WD Red, Seagate NAS and Hitachi NAS (owned by WD). There are also more expensive options but they are overkill for home NAS. So basically choose your favourite brand or pick the one that you believe is fastest based on reviews (they are all similar to be honest).

Also what speed SSD do you want? Fastest are Samsung 840 EVOs. Other good ones are other Samsungs and Intels. I have also heard good things about the Kingston, SanDisk, and Corsairs but I am still new to SSDs. (I currently have a 120GB Samsung 840 EVO).

After choosing that then you can work out how much budget remains for the rest. The SSDs are the parts that varies in price the most.

A total system would look like this:
Micro ATX (or mini-ITX) case with 6+ hard drive slots (at least 4 x 3.5" and 2 x 2.5").
Good quality power supply with 6+ SATA power connectors (avoid no name, very cheap or generic makes - only get trusted good quality brands otherwise your system will get damaged)
Server micro ATX (or mini-ITX) socket 1150 motherboard with at least 6 SATA ports (2 of these should be SATA 6Gbps for the SSDs)
Intel socket 1150 Celeron, Pentium or Core i3 (speed depends on what you can afford)
2 x DDR3 ECC RAM (size depends on what you can afford)
4 x HDDs
2 x SSDs

---

### Post by cj13579 on 2014-08-03
I do everything that you have specified using an old Dell machine running 1 CPU (Pentium 4 2.66 GHz) and 1 GB ram. I run 2 public facing sites from this machine (total hits ~500 per month) and I run a Dynamic DNS client because I also don't have a static IP from my ISP. This machine also serves media via Samba and Squeezebox Server to my home (2 XBMC clients, and a Squeezebox). I have 2x 80Gb disks internally have have about 5TB connected via USB. The only thing I don't run is an email server (I relay everything via GMail).

You don't need top of the range hardware for what you are talking about. My box has a CPU load average of <5% and memory average of about 10% (most of which is the Squeezebox server). Depending on where you are going to keep it though, I suggest you take care about the fans/cooling system. Mine is in the corner of my living room and could do with being a little quieter!

Take a look at [this website]("http://www.havetheknowhow.com") - it's excellent and has hardware stuff on it.

---

### Post by TheFu on 2014-08-04
Lots of great data above. Thought I'd add mine too.

You've asked 15+ questions - EACH SHOULD BE A DIFFERENT THREAD here, iMHO.

Your comcast rep is lying. Not unusual, since they are trained in that way.  You can get a static IP, but if you are on a residential subnet, very few email servers will allow you to send email to them.  There are ways around this using email proxy servers, but that is more complex than I think your current skills support. I'm not trying to be rude, just saying that email sounds simple and it is, until you have to add in all the antispam stuff that you and every other email server admin is forced into on the internet.  Get the cheapest VPS you can and run email on that instead, then you can grab/forward email to/from your internal server as you like.  Plus when comcast goes down, you don't lose emails.  I've been running email servers for companies for 15 yrs and currently run Zimbra for my personal domain and a few companies. I love the "enterprise calendaring" facility - if we weren't addicted to that, postfix and dovecot IMAP would be the solution.  I stopped using POP3 around 1996 - IMAP is so much more convenient and lets every email client see the same view of the folders - smartphones, webmail, thick email clients - all see the same stuff on the server. It is addicting.

Running a web server is easy. Securing a web server is hard.  Expect to be hacked if you do anything wrong.  I run a few different websites out of my comcast business connection. My blog gets about 20K unique visitors monthly and if it wasn't RoR, a minimal server with 1 CPU could handle it if it were python/perl instead.  Dynamic DNS providers will let your router handle any change in your IP address - just sign up with one of the providers that your router supports.  Or look into ddclient - I think that handles more providers.

You didn't mention virtualization (or I missed it), but if you want to run all those services on 1 piece of hardware, I highly recommend that VMs be used. That means the lower-end CPUs can't/shouldn't be used -you'll want something that support VT-x - a Core i5 (any generation) would be amazing.  If you go low-end, that won't be possible.  I have a silent PC with an AMD E350 APU that works fantastic for large NFS storage (not RAID) and plex and XBMC - it is NOT internet accessible - have to hop in through different systems to get there over the internet. That total system (minus HDD) was US$150. Check out pricewatch.com and watch slickdeals/bensbargains for amazing deals every few months.

Storage servers are different than other sorts.  I would NEVER mix a storage server with any internet accessible server processes - just wouldn't do it. Things available on the internet are too likely to be hacked and risking all your storage seems like a bad idea to me. Lots of people do it and I used to do it too - before I got hacked.  The best place I know to learn about storage hardware is the freeNAS forums.  They are ZFS-centric, which is fine, but ZFS is a memory hog, so I don't use it at home.  That doesn't mean their hardware ideas aren't fantastic.

From a system architecture perspective, the more things you add to a single server, the more important it becomes to the LAN environment. If it goes down, other systems stop working.  There are also more dependencies when more services get added to any OS installation, so the risk of dependency issues rises if you go outside the core repositories. A few years ago, I ended up with a server that refused to be patched thanks to different java dependencies from different packages. Eventually, wiping the box was necessary to remove the issue.

If you are thinking about USB3 disks for storage - that is fine for backups, but not for online primary storage. USB has queuing issues and can lock up a system for 10-30 seconds at a time if too many requests are made. That doesn't appear to happen with just 1 or 2 requests ... like backup storage sees.  Bus architecture specs mean little when spinning disks are involved - and even SSDs can't get anywhere near USB3 theoretical throughput.

When just starting out, it can be confusing for new "system admins" - best to get your information from as few sources as possible initially.  The **[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Trusty")** website has a desktop and a server book online for free.  Start by skimming the server book over a few hours to get a feel for what is possible and get used to seeing the steps involved. Sadly, this book shows what is possible - not what is a good or bad idea.

The first things to be installed are **ssh-server** and **fail2ban**.  That makes ssh, scp, sftp available and ready to be placed on the internet.  Next setup ssh keys with ssh-keygen from a client, and push the public key from the client to the server with ssh-copy-id. Disable password-based ssh connections on the server now and open the ssh port on your router (might be smart to use port translation and have the internet IP listen on 60022, but redirect to the server's port 22 internally. Not using the standard port on the internet will keep the script-attacks away, mostly.  I was seeing over 1000 attempts daily on port 22 - moved to a different port and those stopped completely.  ssh is the easiest service to secure.  HTTP, SMTP, and others are 1,000x harder.

Remember, just because something is possible, that doesn't mean it is a good idea.

---

### Post by t873sm on 2014-08-04
Thanks for the considered responses.  
Still don't know how I will proceed, but am hopeful that I will have a good outcome.  In answer to the question about websites, I currently host through Bluehost.  I use Drupal and have made websites for local activism, politics and school groups as well as personal.  I would like to be able to host from home and start selling websites.  I would host them locally until I could afford enough power in Linode or another service to be worthwhile. 

ttfn

---

### Post by Tadaen_Sylvermane on 2014-08-05
> **t873sm said:**
> Thanks for the considered responses.  
Still don't know how I will proceed, but am hopeful that I will have a good outcome.  In answer to the question about websites, I currently host through Bluehost.  I use Drupal and have made websites for local activism, politics and school groups as well as personal.  I would like to be able to host from home and start selling websites.  I would host them locally until I could afford enough power in Linode or another service to be worthwhile. 

ttfn

I hope not to ruin your plans here but it must be said.

Commercial hosting is a matter of scale.

Hosting websites commercially at ones house is not exactly feasible. A commercial host has network connections you can only dream of having at home, fully redundant power supplies, an entire backup power generation system for when the power does go down, and I believe most of them are directly connected to fiber backbones instead of going through a regular ISP. Even with all that they don't charge to much to host a basic website (I haven't looked into this much). 

It's like why companies pay for RedHat subs instead of using a CentOS or whatever. They are paying for support because downtime is lost money. Same thing. If you can't provide the features to keep their website up 99.9% of the time then they likely won't host with you. Your prices would have to be so low that you wouldn't make a dime, if anything likely losing money paying for the server / power / internet / whatever cooling costs go up with the furnace you are hosting on... and so forth.

Personal or hobbyist use is perfectly viable, commercially is asking for trouble.

---

### Post by TheFu on 2014-08-05
Tadaen_Sylvermane nailed it.

Don't run commercial websites on a cable or DSL connection.

The cheapesst, quality, web hosting offer that I know is NearlyFreeSpeech.net. They only charge for what you use - small, static websites are 25-50 cents a month. They scale up automatically, so if a site gets hit with slashdot, the viewers don't take down the site and the cost goes up for 1 month only based on bandwidth used.

I run a number of corporate servers off a cable modem connection, but our public website is NOT hosted there. It is at a real hosting provider with great uptime and bandwidth.

---

### Post by mastablasta on 2014-08-06
also why large SSD disks for system? server takes about 2 GB in all if I am not mistaking.

---

