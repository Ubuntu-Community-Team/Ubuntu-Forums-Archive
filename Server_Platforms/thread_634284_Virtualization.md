---
title: "Virtualization"
date: 2007-12-07
forum: Server Platforms
---

### Post by TheGameAh on 2007-12-07
I'll keep this brief.  :)  Looking to see if I'm not completely crazy with an idea here.

Here's my problem:

3 XP computers all sitting on the floor in my server room.  Just takes up space.  They all do different things (credit card software server, blackberry, time clock collecting machine).  They can't sit on the same hardware (database issues).

Could I setup an Ubuntu 64 edition with tons of ram, and virtualize each machine?  What are the drawbacks?

---

### Post by homegrown on 2007-12-07
Nothing crazy about it, makes perfect sense. One thing though, why 64bit?

---

### Post by TheGameAh on 2007-12-07
I wanted to give 512 to each virtual machine, maybe more for the blackberry server.  (although only 20 users or so).

So my idea was to take a server I wasn't using, put 8 gigs of memory in it, and put a 64 bit OS on it to take advantage of extra memory.  (I know 32 bit OSes have a problem going beyond 4 gigs of memory).

---

### Post by homegrown on 2007-12-07
if you're going to assign 512MB of memory to each machine, you shouldn't need the 8G for the host. There appears to be patches to address the the memory issue, but I'd be nervous about making the host unstable. 
I'd go for a 2 or 3G host with the three vm's on top.

---

### Post by HermanAB on 2007-12-07
I run lots of virtual machines, mostly VMware Server (free) some on VMware WorkStation (couple hundred bucks).

WinXP and Win2003 both run perfectly on VMware Server. The only reason I have WorkStation is for RHEL5, which won't work on Server.

I even run VMware server on my Xubuntu laptop, with WinXP in a VM for some Windoze only apps, since that works better than Wine/CxOffice.

So, go ahead, it works like a charm.  You won't regret it - in fact, you'll wonder why you haven't done it years ago already!

Cheers,

Herman.

---

### Post by MystaMax on 2007-12-07
I'm running VMware server on a Dell PowerEdge 2850 running 64-bit Dapper LTS. Its currently running our intranet (joomla), inventory management software (belarc), and our DMS (knowledgetree). Just ran uptime and heres what I got:

17:45:05 up 486 days, 23:58 - Thats awesome. 

I also run vmware Workstation on my gutsy laptop, w/ a XP VM, so I can manage our AD Domain, and use Adobe CS3.

---

### Post by sciurus on 2007-12-07
> **MystaMax said:**
> Just ran uptime and heres what I got:

17:45:05 up 486 days, 23:58 - Thats awesome. 
.

Have there really been no kernel updates for dapper in 486 days?

---

### Post by TheGameAh on 2007-12-10
This is all great to hear  :) I imagine it was something people had done, just wanted to check.

Regarding Homegrown's idea of just staying with 32 bit.  I was thinking 64 bit for another reason.  I wanted to leave just a little room for growth.  I really don't want to add another virtual machine, but if I did, I'd be getting close to that 32bit memory limitation.

Would there be any issues with 64bit OS and VMWare?  I assume as long as the host sees it, the guests can be 32bit, correct?

---

### Post by MystaMax on 2007-12-12
We all know there's been updates to the Dapper kernel.... :)

I haven't had any problems running it on 64-bit, yes my guess are 32-bit.

---

### Post by rsw686 on 2007-12-12
I would go with the 64bit host OS as well. You can run 32 and 64 bit guests under it. VMWare is a nice application and what I use. You can use their Converter to convert your XP machines to virtual machines.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by TheGameAh on 2007-12-13
A few more tiny questions.

I've recently started all of this on a test server.  (Just using Linux Mint.  It was there  :)  )  So far, so good.  

When I get the 64 bit OS running, can I just copy the VM files over and pick right up?  (a little new at 64 bit stuff).

Also, I'm just using the VMWare server from the Repos.  And it's working quite fine.  Would there be any reason to pay for the "official" server software from VMWare?

---

### Post by rickyjones on 2007-12-13
> **TheGameAh said:**
> A few more tiny questions.

I've recently started all of this on a test server.  (Just using Linux Mint.  It was there  :)  )  So far, so good.  

When I get the 64 bit OS running, can I just copy the VM files over and pick right up?  (a little new at 64 bit stuff).

Also, I'm just using the VMWare server from the Repos.  And it's working quite fine.  Would there be any reason to pay for the "official" server software from VMWare?

I believe that you can just copy the files over and open them with VMWare Server without issue.

I don't believe there is any solid reason to purchase VMWare server products if the free server product is working, aside from possibly receiving official support from VMWare if anything goes wrong.

-Richard

---

### Post by rsw686 on 2007-12-13
Yep the VMWare guests can be copied between machines without issue. That is th great thing about VMWare.

---

### Post by MystaMax on 2007-12-13
Yep. I'm in process of rebuilding my main vmware server, and just copied the VMs from the linux server to a tmp windows vmware server (of course I shut the VMs down beforehand). So far, its been a painless process.
 
My main VMware server uses VMware Server from vmware.com, but I'm rebuilding it to use the one in the Ubuntu repositories. This way, updating vmware server is more automated as oppose to me going to their site, downloading the tgz file, extracting, and running the install.
 
VMware has ESX server 3 (paid) and VMware Server (Free). 
 
ESX runs on bare metal, and VMware Server needs to run atop an operating system, which equals more overhead.
[quote=Wikipedia]
ESX Server, an enterprise-level product, can deliver greater performance than the freeware VMware Server, due to lower system overhead. In addition, ESX Server integrates into [VMware Virtual Infrastructure]("http://en.wikipedia.org/wiki/VMware_Virtual_Infrastructure"), which offers extra services to enhance the reliability and manageability of a server deployment.
[/quote]
 
Good luck!

---

### Post by HermanAB on 2007-12-13
Actually, ESX is a customized Linux.  They just don't call it that, to placate clients that are hell bent on Windows, e.g. all North American Government departments.

Cheers,

Herman

---

