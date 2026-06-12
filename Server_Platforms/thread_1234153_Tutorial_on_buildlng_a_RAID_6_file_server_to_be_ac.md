---
title: "Tutorial on buildlng a RAID 6 file server to be accessed by a Mac?"
date: 2009-08-07
forum: Server Platforms
---

### Post by Zorrorrorro on 2009-08-07
Hi there,

My sister has about 600 GB of data that she desperately needs to be backed up as it contains her portfolio and life's work (she's an artist / designer). To add to the complexity, she uses a Mac and she's not very technical at all. 

I'm thinking of building a RAID 6 server with 5 1 TB hard drives. 

I'm not exactly sure what hardware i will needs, but an old Duo Core with 4 GB RAM and around 8 SATA slots should be more than enough, right?

But anyways, are there any tutorials / links that you can provide for building an Ubuntu / linux file server that a Mac can connect to? 

I really appreciate your help!!!

Zorrorrorro

---

### Post by fjgaude on 2009-08-07
How will the Mac access the backup data on a raid array? Through a LAN connection, router, wireless?

I use **mdadm** for a raid5, four drive array. For 600GBs of data you could have a single drive for the backup storage.

---

### Post by samosamo on 2009-08-07
Okay let me take a swing at this.  You say she needs to back up 600GB but then you go on to say that you're ready to build a fileserver with 6TB worth of drives.  That's about ten times the desired storage space. Not only that, but you go on to say that this poor girl is a "Mac user that is not very technical" (whatever that means). So you decide to build her a linux server rather than buy her a 1TB external hard drive for like $100?

---

### Post by windependence on 2009-08-08
I don't see what the problem is here. I use a Mac, and like always, it just "works" with a linux file server. You don't even have to run NFS, but it's nicer if you do. It will also see a SAMBA share just fine. The drive will show up in her network in Finder. No issues.

-Tim

---

### Post by Zorrorrorro on 2009-08-10
@fjgaude: Sorry I should clarify further. I'm thinking of having my sister accessing it through WAN so that I can maintain it for her (I don't live with her) and also use it as a file server myself. 

@samosamo: Actually, with a RAID 6 configure it would end up being 3 TB total with 5 1 TB hard drives. The reason I wish to build a WAN file server is 1) Having an automated process of creating duplicate sets of data and 2) that if her house ever burns down (God forbid), then she won't lose 6 years worth of digital portfolio work. But, yes getting her an external HD would be good to have a duplicate of the data in two different locations and for portability's sake. 

@windependence: That's good to know. I didn't know if Linux and Mac would live happily together.

New question: Is it possible for a WAN file server to show up as a network folder in her Network Finder? If so, what's a good way to configure this?

---

### Post by samosamo on 2009-08-10
<snip>

I'll give you a general outline of how I would handle this.  You are building a light duty linux fileserver to be accessed via WAN by a Mac. Fault tolerance will be provided by RAID6.  How do you go about this?

You build a box, any combo will do.  You should concentrate on a good enclosure with proper cooling, and on the SATA controllers.  I would go for any motherboard with Intel ICHx.  6 SATA ports for your RAID6.  Buy another controller for two OS drives in RAID1.  Do your research.

You install Ubuntu Server.  You will setup a linux softraid using mdadm, adjust this tutorial for RAID6: [http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/]("http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/").  You also install netatalk via this tutorial: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") and OpenVPN: [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")

OpenVPN will allow you to safely and securely route traffic over an insecure link on the internet. Some networking knowledge is necessary. The easier way to go is "routed" but, if you're up for it, try to go "bridged" and it will almost be like you and your sister are at the same place.

Netatalk will allow you to use AFP to share files to your sister, Apple's preferred method.  Much MUCH faster than Samba, and more features than NFS.

Advertising your AFP share with "avahi-daemon" is covered in the tutorial posted above.  However, it does not tell you how to get it to work across two subnets, as you may be doing with your "routed" VPN.  It's difficult.  You will need to look into "bonjour proxying" but you will probably trash the whole idea and have her just access it via a DNS hostname.  If you decide to go bridged you will not be faced with this problem.  Multicast traffic will pass right through it allowing the server to appear in her Finder window.

---

### Post by Zorrorrorro on 2009-08-10
Cool, thanks for the tip samosamo! I'll definitely try it out!

---

### Post by samosamo on 2009-08-10
*Ahem* aren't you forgetting something?

Crap, edited by a mod.  Forget it.

---

### Post by windependence on 2009-08-10
Netatalk would be nice but definitely not necessary, and frankly, Apple supports all the standard ways of connecting anyway over a TCP/IP connection. I just use NFS shares on my business network and I am very pleased. 

@samosamo, what "features" am I missing with netatalk? I don't seem to lack anything using NFS. Clue me in. ;-)

-Tim

---

### Post by samosamo on 2009-08-10
Please don't compare NFS to Netatalk.  NFS has it's purposes, Netatalk has it's purposes.  In fact, we use NFS for home directories, and Netatalk for the "workflow" volumes. You can compare Netatalk with Samba but I'm not sure you want to get into that right now.

If you have Mac's on your network you should look into it.  Bonjour advertises my Netatalk server so it appears in Finder's sidebar, very easy for users to just click on and choose their share.  Shares have custom names based on variables in the config file.  I also use it for TimeMachine (Not allowed by default, but I posted the tutorial above). That's all I can think of, and I'm not even getting into anything complicated. My setup is as simple as it gets.

Not that it matters much to me but I should also mention that AFP is "The Apple Way.

---

### Post by charliebrownau on 2009-08-12
I am looking into upgrading my 7.0 TB file server
which currently runs in JBOB (Non Raid)
to a mix of Raid 5 and Raid 6

I will be getting two WD GP RE4 2TB Drives
to see how they run in Raid 1 in a few days
time .

I am currently looking around for a new 
Motherboard , RAM and CPU for my server
as its currently socket 478 and all the Raid 6
controllers are PCIe or PCIx .

I don't trust software raid as far as you can throw it
so it has to be all hardware based .

At this point the controller I am Interested for an Raid 6 setup is the 3ware 9650SE-8LPML (Eight port) and 3ware 9650SE-12ML (12 port) .

I want to use Raid 6 since it allows me to have two drives fail and I've still got the data , with all these 1TB, 1.5TB and 2TB drives now its very important .

I will be running Duel Boot with Nlited Windows 2003 and either Ubuntu Server or Debian Server.

I don't come across that many Mac OSX users but the ones that have needed to access the data I have asked to use DC++ Mac Ports . Most users access the data from the server using DC++ fine .

I won't be setting up my file server for outside Internet WAN useage but it does travel to Lan Parties as its a "file server"

---

### Post by windependence on 2009-08-15
> **samosamo said:**
> Please don't compare NFS to Netatalk.  NFS has it's purposes, Netatalk has it's purposes.  In fact, we use NFS for home directories, and Netatalk for the "workflow" volumes. You can compare Netatalk with Samba but I'm not sure you want to get into that right now.

If you have Mac's on your network you should look into it.  Bonjour advertises my Netatalk server so it appears in Finder's sidebar, very easy for users to just click on and choose their share.  Shares have custom names based on variables in the config file.  I also use it for TimeMachine (Not allowed by default, but I posted the tutorial above). That's all I can think of, and I'm not even getting into anything complicated. My setup is as simple as it gets.

Not that it matters much to me but I should also mention that AFP is "The Apple Way.

Hmmmm..... I guess I don't "get it" because I'm not a rabid mac addict :-)

My NFS shares show up just fine in the finder sidebar. I haven't tried using Time Machine  to any of my NFS shares as I use an external firewire drive for that.

This actually wouldn't be a problem for me as I am using the latest RC of FreeNAS (I AM a FreeBSD addict!), and it supports AFP as well as tons of other protocols. I might just try creating an AFP share just to see what the differences are.

Thanks Samo!

-Tim

---

