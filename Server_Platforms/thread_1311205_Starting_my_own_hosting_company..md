---
title: "Starting my own hosting company."
date: 2009-11-02
forum: Server Platforms
---

### Post by melsen on 2009-11-02
Alright... having worked in IT for god knows how many years, I figured I'd try to start up a small business on the side. Hosting and website development... 

I'm so lucky I have a 50/50 mbit full duplex fiber connection to my home.. and I have the posibility to upgrade that to 100/100


Anyways.. This all brings some questions to my mind.. but first, let me try to enlighten you on some of the plans...

For infrastructure, I have planned to purchase a NAS that supports ISCSI.

I plan on installing servers that boot directly off the NAS, rather than having a local harddrive.

On these machines, I figured I'd create virtual LAMP servers running from KVM.


Then my first question comes up. Should I go for a cloud configuration using eucalyptus, rather than just setting up 3-5 virtual servers on each physical server?

If yes: What will I get out of that. Is there anything else I would be able to offer my future customers through running a cloud that I wouldn't be able to provide otherwise? or will it easen my own administration - and in what way?

I'm a bit hazy when it comes to the cloud concept... 


For a semi-simple hosting company.. which software could you guys recommend? My own eyes have fallen upon IspCPOmega... the interface seems very easy to understand..

---

### Post by Lars Noodén on 2009-11-03
I would recommend you plan a pilot first with old or borrowed hardware.  Just give a few configurations a try see how they handle different loads.  
Most importantly figure out how to create and identify bottlenecks in CPU, disk access, and network components like isci, dns, etc.  

Also, take a look at sparc-based hardware.  

If you are loading the VMs directly from the NAS, then you may want to consider building your own.  Speed might be a problem with the LAN and you may want one >= 1Gbps switch for just the NAS connections.

---

### Post by i.r.id10t on 2009-11-03
Check out what linode.com does with VPS (they use a customized user mode linux) and do something similar... perhaps pre-configure with ispconfig

---

### Post by melsen on 2009-11-03
> **Lars Noodén said:**
> I would recommend you plan a pilot first with old or borrowed hardware.  Just give a few configurations a try see how they handle different loads.  
Most importantly figure out how to create and identify bottlenecks in CPU, disk access, and network components like isci, dns, etc.  

Also, take a look at sparc-based hardware.  

If you are loading the VMs directly from the NAS, then you may want to consider building your own.  Speed might be a problem with the LAN and you may want one >= 1Gbps switch for just the NAS connections.

Actually - it is interesting you make that point. I've thought about that myself. Let me try to elaborate on my own personal conclusions - see if they make sense.

1) The NAS's I've been looking at have 2 x 1gbit connections that handles load balancing, if you have a switch that supports it... I think it's 802.11as or something it's called. So that is naturally one thing I'm planning on acquiring.

2) I agree that load speeds of the servers will be impacted. The NAS's I've looked at benchmark around 80-100mb/sec... so boots/reboots will be impacted of course.. load balancing will hopefully remedy the impact a bit on the remaining servers that is running.

3) Speed on the NAS in general. Since we are talking websites - they will be developed with caching in mind.. xcache and so on. So in general, the speed should be fairly acceptable in most aspect once they are loaded.. right?


Doesn't that make sense? or am I way off... ?

---

### Post by melsen on 2009-11-03
> **i.r.id10t said:**
> Check out what linode.com does with VPS (they use a customized user mode linux) and do something similar... perhaps pre-configure with ispconfig

Linode... I'll keep that in mind at check it when I get home from work...

I was actually considering either ispconfig or ISPCP Omega... I just don't like the GUI of ispconfig, and with a target group of small companies that may not be too IT savvy, I would like to present a hosting GUI that is somewhat more simple to look at. ISPCP Omega seem to fullfill that pretty nicely..

---

### Post by epsolon77 on 2009-11-03
I am a little fuzzy on the difference between virtualized systems and cloud systems so I may be on the wrong track here.  

I think that using a virtualized system like ProxMox or VMWare coupled with your server PXE boot would make for an extremely hard to break system that would be easily expandable.  I mention ProxMox and VMWare because I know they have the ability to live migrate VM's.

---

### Post by Lars Noodén on 2009-11-03
> **melsen said:**
> Actually - it is interesting you make that point. I've thought about that myself. Let me try to elaborate on my own personal conclusions - see if they make sense.

1) The NAS's I've been looking at have 2 x 1gbit connections that handles load balancing, if you have a switch that supports it... I think it's 802.11as or something it's called. So that is naturally one thing I'm planning on acquiring.

2) I agree that load speeds of the servers will be impacted. The NAS's I've looked at benchmark around 80-100mb/sec... so boots/reboots will be impacted of course.. load balancing will hopefully remedy the impact a bit on the remaining servers that is running.

3) Speed on the NAS in general. Since we are talking websites - they will be developed with caching in mind.. xcache and so on. So in general, the speed should be fairly acceptable in most aspect once they are loaded.. right?


Doesn't that make sense? or am I way off... ?

3. Caching almost always a good idea, but will help only on the second and subsequent load.  The first request of any given object, either static or dynamically generated, or a request made after the cache has expired will incur the overhead of both retrieval and caching.  The latter is probably negligible.  

2. I'm thinking more document retrieval speed or database access speed (since LA always gets turned into LAMP whether it is needed or not.)  In that case it's usually the bus that is the main limiter.  I'm not a hardware enthusiast and only learn when forced to, but maybe you know someone who can tell about getting actual scsi, sas, or sata drives or arrays that can be connected to and used by more than one machine at the same time.  If you plan on hosting any streaming audio or video (say with icecast or ffmpeg or vlc) then you'll need to worry about that a lot.  RAID with striping (raid 10, 50, 60) might be an option.  Maybe ZFS or Hammer?  

1.  A lot of the networking references I've been using for the last few years, and others, suggest that network saturation is about 80% of the advertised speed.  So if you have the two ethernet connections plugged straight in to one machine, you might get 1.6 Gbps transfer max or somewhere around 177 - 200 MBps using very crude guesstimates.   Also, that just for the webserver connecting to the 2x1Gbps NAS, each junction will use some of that for overhead.


Again these are reasons to do a pilot, even on paper, to see what should be prioritized and to see what is cost effective and what isn't or what is a must-have and what isn't.  

If you're going to try to saturate the bandwidth, then some network tuning is in order, too.

---

### Post by melsen on 2009-11-03
> **Lars Noodén said:**
> 3. Caching almost always a good idea, but will help only on the second and subsequent load.  The first request of any given object, either static or dynamically generated, or a request made after the cache has expired will incur the overhead of both retrieval and caching.  The latter is probably negligible.  

2. I'm thinking more document retrieval speed or database access speed (since LA always gets turned into LAMP whether it is needed or not.)  In that case it's usually the bus that is the main limiter.  I'm not a hardware enthusiast and only learn when forced to, but maybe you know someone who can tell about getting actual scsi, sas, or sata drives or arrays that can be connected to and used by more than one machine at the same time.  If you plan on hosting any streaming audio or video (say with icecast or ffmpeg or vlc) then you'll need to worry about that a lot.  RAID with striping (raid 10, 50, 60) might be an option.  Maybe ZFS or Hammer?  

1.  A lot of the networking references I've been using for the last few years, and others, suggest that network saturation is about 80% of the advertised speed.  So if you have the two ethernet connections plugged straight in to one machine, you might get 1.6 Gbps transfer max or somewhere around 177 - 200 MBps using very crude guesstimates.   Also, that just for the webserver connecting to the 2x1Gbps NAS, each junction will use some of that for overhead.


Again these are reasons to do a pilot, even on paper, to see what should be prioritized and to see what is cost effective and what isn't or what is a must-have and what isn't.  

If you're going to try to saturate the bandwidth, then some network tuning is in order, too.

Definately some good points, and they are all valid as well.

I do however think I might need to scope it in several phases. 

1) Launching phase - what would an affordable infrastructure be able to handle customer/load wise based on the target customer groupa

2) Future expansion... 


I have to be upfront and honest to myself about taking these in steps and build a customer based as well as finances to get the 'golden' setup.

Until then I need to think about the most affordable and safe/solid environment.

---

### Post by Lars Noodén on 2009-11-05
> **melsen said:**
> 
I do however think I might need to scope it in several phases. 

1) Launching phase - what would an affordable infrastructure be able to handle customer/load wise based on the target customer groupa

2) Future expansion... 


Back when Mac, Linux, BSD and Solaris were the main university systems #1 used to be taught as 'scalability'  Different options are suitable during different stages of growth.  

For the initial phase, what two or three things about hosting are absolutely the most interesting for *you*?

---

