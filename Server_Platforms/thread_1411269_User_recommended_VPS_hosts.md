---
title: "User recommended VPS hosts"
date: 2010-02-19
forum: Server Platforms
---

### Post by bakegoodz on 2010-02-19
I want to find a good VPS host provider in the Western United States.
I'm looking $30 or less of the spectrum, but greater than 256 MB of RAM would be nice. Obviously they need to have Ubuntu server as an option. I don't need anybody to hold my hand. I can manage my own firewall, and would prefer if it has iptables root access, unlike Vserver based VPS. At lest have some way to manage the firewall my self.

Who do you recommend and why?
Thank you to all that take the time to reply

---

### Post by windependence on 2010-02-19
I recommend myself because I can give you whatever you want and I have Dual UPS, Backups, and enough bandwidth. :-)

-Tim

---

### Post by acroporas on 2010-02-19
My recommendation is Linode.com

---

### Post by bakegoodz on 2010-02-19
your funny windependence, your own site is hosted on Godaddy
And Linode.com is in the UK, I want a good pipe and latency back to my neck of the woods.

---

### Post by volkswagner on 2010-02-20
> **bakegoodz said:**
> your funny windependence, your own site is hosted on Godaddy
And Linode.com is in the UK, I want a good pipe and latency back to my neck of the woods.

Actually Linode has several data centers.

You can check Linode availability [here]("https://www.linode.com/avail/").

I would recommend Linode, as they have a great feature set, especially ability to backup VM's.

For the budget conscience (such as myself), Fivebean is worth exploring.  They even give [forum members a discount]("http://ubuntuforums.org/showthread.php?t=1128094&highlight=fivebean").  The data center is in TX.  They give you a download test and ping url [here]("http://fivebean.com/vpshosting/").

Other relevant [thread]("http://ubuntuforums.org/showthread.php?t=1369928").

Moving my home server to a VPS, had made me very happy.  :P

---

### Post by bakegoodz on 2010-02-22
Thanks volkswagner. I signed up with Fivebean, and I have been happy with them so far, the price with the forum discount is awesome too.

---

### Post by i.r.id10t on 2010-02-22
One more vote for linode.com

---

### Post by tmilam on 2010-02-22
I have been using [Virpus]("http://virpus.com/unmanagedvps/") for two weeks and love them. The prices are very low and their servers have been in my experience reliable. And of course any VPS provider MUST have Ubuntu as an option.

---

### Post by 77bond on 2010-02-23
I have account with [http://onexenvps.com]("http://onexenvps.com/") superb cheap and stable.

---

### Post by 77bond on 2010-02-23
they use xen which rocks and have ubuntu 9.10 32 bit.

---

### Post by windependence on 2010-02-23
> **bakegoodz said:**
> your funny windependence, your own site is hosted on Godaddy
And Linode.com is in the UK, I want a good pipe and latency back to my neck of the woods.
FYI, my site is PARKED at GoDaddy. I host all my stuff and always have. I also host quite a few others. It's OK, let me know when you run out of bandwidth with the 300 other servers on the same machine. I have no more than 10 on each of my Vmware servers.

-Tim

---

### Post by bakegoodz on 2010-02-27
Fivebean always seems sluggish, like the processor is being over provisioned. I even have a VM with 1.5 GB of RAM. How is the performance of Linode?

---

### Post by Fliggerty on 2010-02-27
VPS.net is a favorite of mine.  They are a relatively new brand of the UK2 Group, being managed by a lot of the same techs who run WestHost.  While the technology is essentially the same between most of the VPS providers I've looked at, it's the support and service that VPS.net provides that has made the difference for me.  Those guys are nice, and definitely know what they are doing.

---

### Post by tubezninja on 2010-02-28
> **bakegoodz said:**
> Fivebean always seems sluggish, like the processor is being over provisioned. I even have a VM with 1.5 GB of RAM. How is the performance of Linode?

For what it's worth, I've used both fivebean and Linode, and Linode is miles ahead in terms of performance.  Yes, their pricing is somewhat higher, but their VPSes are just way more responsive in my opinion and experience.  

I started out with Linode about a year and a half ago, and then heard about Fivebean.  The pricing was very attractive and the features looked good, so I migrated several projects over.  Performance was okay, but not nearly as fast as on Linode, and ultimately I ended up moving those projects back.

I will stress that fivebean's customer support is **top notch** and have always been very courteous and helpful.  However, I tend to think the problem with performance isn't fivebean so much as the datacenter they're located in.  During my tenure there, I experienced a change in IP address without any advance notification (a glitch on the datacenter's part for which fivebean was profusely apologetic for, and I appreciated that); a couple months later that same IP address somehow got re-assigned to another server and wasn't caught until I noticed I couldn't log in and my site wasn't loading (again fivebean rapidly resolved the issue and was very courteous); later on some sort of hardware failure with the storage array caused a failure and necessitated a forced reboot; and then weeks after that some instances where other customers were experiencing DDoS attacks that affected people's ability to access my server.  All of these resulted in some downtime.

By comparison, Linode's record during my use of their services has been spotless, and I've seen zero downtime.  This is with linodes scattered far and wide between their Newark, Dallas and Fremont datacenters.  Looking at my Linode support requests, the only ones I have logged are routine requests to upgrade service plans or migrate to other datacenters (the need for these requests were recently eliminated by the ability to "self serve" upgrade/migrate in the control panel).  And the only "forced" reboot I ever had to make on a linode was when they upgraded the storage capacities of all their plans, and the reboot to take advantage of the additional storage was optional and entirely at user discretion.   

Linode's customer support is also very responsive and helpful, as evidenced by their [twitter feed]("http://twitter.com/linode").

Don't get me wrong, for the value conscious fivebean is great, and I would continue to recommend  them to the cost sensitive.  But if you intend to stick with a project for a significant length of time and it will grow or requires a certain measure of extreme reliability, then it's likely you will eventually "outgrow" fivebean, and Linode is the way to go.

---

