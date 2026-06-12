---
title: "VMs over RAIDed CPUs?"
date: 2011-02-11
forum: Virtualisation
---

### Post by neoculture on 2011-02-11
The "search" command has failed me, but it may be I didn't put in the correct search terms - so please excuse me if there already is a thread about it somewhere; I will quite happily move to it if it is pointed out to me.

Anyway, down to business: I am a home enthusiast and have recently built a file server which RAID-5s 9x2TB HDDs and presents the result as a single 14TB (*real* TB) HDD to the network.  Which got me thinking...

I have multiple computers at home - most of them always on, some of them "on" as required - running a series of jobs: FileServer, MythTV, Torrent, WebServer, MailServer, etc..  Most run some sort of Ubuntu flavour, but a couple run WinXP and one runs Win7.

And most of them waste CPU for most of their up-time.

So turning them into VMs was always on the card (if I ever get around to learning how to). But my recent foray into RAID land got me thinking - is it possible to "RAID" physical machines.  Yes, I know about clouds, but as far as I can tell a VM still only runs on one physical box amongst all those available in the Cloud.  What I am talking about is turning (for example) 5 single-CPU machines into a 5-CPU "virtual" machine.  Or maybe 4-CPU to allow for failure, same as RAID. And *then* to run VMs on top of this "virtual" hardware.

Of course, there would have to be some restrictions: the CPUs would have to be of the same architecture/family (or at least close enough that binaries can run across them), and could you give unique identifiers to all the physical HDDs in the set in order to mount various sets of them in VMs?

Is this possible?  Has this been done?  To my non-Virtualisation-educated mind this seems like a logical extension to the cloud - but then again, what do I know?

---

### Post by Hedgehog1 on 2011-02-11
Welcome to the forums!

Also, congratulation on getting a 14tb virtual disk!  I am envious (just a little, around the edges). 

To your question - about 'RAIDing' processors in a similar way to 'RAIDing' disk drives.

The answer is: sorta, yes and no.

First the Sorta:  Render farms used by folks like Pixar do use lots of isolated CPUs.  Each frame that is to rendered is handed by a 'traffic-cop/boss' computer to the next available 'PC' (really a single 'blade' in a blade server nowadays).  It is the digital 'Mongolian Hoard' technique.  By the time the animators arrive at the studio in the morning, their many thousands of frames are rendered.

The Yes: Todays super computers are really thousands of smaller CPUs (or GPUs) all working more like a marching band. A 'conductor' computer keeps them all working on just one project.  A good example of this is the super computer built from thousands of Sony Play-Stations (running Linux!) that appears to an outside human to be one very big, very fast computer.

The No: Render farms and super computers have very specialized 'managing' computers (these take the place of the RAID Controller(s) in your super-sized 14tb RAID array).  They run software that is mostly written in house to do a very specific tasks (like rendering movie frames).

For most folks, your cheapest and most reliable way to get many processors to work together is to have them all on one motherboard.  The home-super-computer of choice is the Mac Pro.  It is the fastest OSX box, the fastest Windows box, and the fastest 'non-commercial' Linux box.

At work we use Linux servers that will take 8 CPUs with 4 cores each.  32 cores with 256gig-512gig of ram.  UMMMMMMM....  If you have to ask what they cost, you cannot afford them...

However, this does not mean you should abandon experimenting with your PCs at home...

:KS

---

### Post by Hedgehog1 on 2011-02-11
Side note on your idea of dealing with a 'CPU' failure concept.

Have you seen the AMD 3-core CPUs?  They are 4-core chips with one CPU failed but the other three are fine.  They use a laser to disconnect (burn the connections of) the bad one, and still get a very nice 3-core CPU.

Granted, it isn't a real time fail-over - but still...

:KS

---

### Post by Hedgehog1 on 2011-02-11
It occurred to me today that some blade servers do actually work like your 14tb RAID array.

A buddy of mine got a demo of a blade server with 'CPU fail-over' a while back.  The demo showed a process running on a specific blade, and he was invited to pull the blade right out of the server, creating a 'fatal CPU' crash.

Within a few seconds, the process was restarted and running on another blade, with no loss of data.

So it is in fact possible (but not cheap) to do a RAID like process with CPUs.

:KS

---

### Post by LightningCrash on 2011-02-12
OP the aggregation you are talking about is effectively Single System Image.
SGI's Altix 4700 does SSI.

The redundancy part, I don't know. X86 theoretically does NUMA hotplug but I have not seen any hardware doing it.
The only thing I've personally seen do true CPU hotplug is Sun SPARC equipment running Solaris.

---

### Post by neoculture on 2011-02-14
So basically, the answer is "yes, but you need specialised hardware", which kinda throws my hope of re-using my current PCs out the window.

Bugger.

LightningCrash:  Cave conventus simiarum - aure nocebit.  ^_^

---

### Post by mciverza on 2011-02-16
You can however use your "idle" CPU cycles for doing stuff like seti@home and similar projects.
Those projects use BOINC which stands for *Berkeley Open Infrastructure for Network Computing*
and is described as* "**BOINC* is an open-source software platform for computing using volunteered resources"
and you can read more about it at [http://boinc.berkeley.edu/help.php](http://boinc.berkeley.edu/help.php) or at ithe wikipedia page *[http://en.wikipedia.org/wiki/Berkeley_Open_Infrastructure_for_Network_Computing](http://en.wikipedia.org/wiki/Berkeley_Open_Infrastructure_for_Network_Computing)*

---

### Post by gtfourdreams on 2011-02-24
> **Hedgehog1 said:**
> It occurred to me today that some blade servers do actually work like your 14tb RAID array.

A buddy of mine got a demo of a blade server with 'CPU fail-over' a while back.  The demo showed a process running on a specific blade, and he was invited to pull the blade right out of the server, creating a 'fatal CPU' crash.


This is probably what most accurately answers his question. 

Although you don't need to physically have all those computers connected together in the same box (like a blade server). You can indeed do it with multiple physical computer boxes sitting in different parts of the world if you want. 

You can achieve this with VMware's enterprise virtualization software. It allows automatic fail-over and redundancy of complete VM's should a physical box go down. ie. You have 5 different servers with 5 virtual machines on each, if one server has a hardware failure it can automatically move the VM's over to another server box without any loss of data and complete transparency. If one whole server needs to go down, you can move all the VM's off and take it down, then bring it up and move the VM's back when completed.

You should be able to do this with any off-the-shelf hardware that's capable of running the appropriate VMware software. Basically anything within the last 5 years should do it. Pretty cool stuff actually.

---

### Post by neoculture on 2011-02-25
> **gtfourdreams said:**
> You should be able to do this with any off-the-shelf hardware that's capable of running the appropriate VMware software. Basically anything within the last 5 years should do it. Pretty cool stuff actually.

Thanks, I'll go have a look... although I fear that any product with the word "enterprise" in the title will be beyond my enthusiast's pocketbook.  ^_^

---

