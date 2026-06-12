---
title: "Max RAM supported with Ubuntu gutsy/hardy server for VM host"
date: 2008-03-04
forum: Server Platforms
---

### Post by kaginken on 2008-03-04
Anyone know what the maximum supported memory is for ubuntu server?  We're thinking of using ubuntu gutsy or possibly hardy to host a slew of VM's.  The hardware we're considering has 8 Gigs of RAM, but we want the ability to add more RAM in the future to 16G, possibly even up to 32G of RAM.

From what I've read in the forum, about all I can find is that some guy with very limited knowledge seemed to think that this would take a 64bit processor running the 64 bit Ubuntu server.  Is this a fact?

In addition, as this will become a vital part of our infrastructure, is there some affordable support from canonical?

Also, does VMWare support this configuration?

Any help would be appreciated...thanks ahead of time,

Ken

---

### Post by Ptero-4 on 2008-03-04
The 32-bit architecture (this applies to all OS's that run on x86 CPU's) supports only up to 3GB of RAM. So yes, anything more than that (even your server's base config) needs a 64bit ubuntu (or OSX/Windoze for that matter).

---

### Post by vpsville on 2008-03-04
You can run 64GB of RAM with a 32bit processor, you just need to compile the kernel with memory mapping features enabled.  A 64bit processor running a 64bit OS does not need any mapping features so it accesses large amounts of memory faster.

Windows XP is limited to 3GB on 32bit which is where a lot of confusion comes from.  Linux does not have this limitation.

The kernel of the server version of Ubuntu has support for PAE ([http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)), which is a trick to make a 32-bit system be able to use up to 64 GB RAM.

---

### Post by bonezie121 on 2008-03-04
Actually its a processor problem that cannot see more than 3.4 GB of ram.  Its called PAE (Physical Address Extension)  If you want to see more that the 32 bit brocessor with have to be the PAE enabled processor.  But its actually cheaper and les configurations to just get the 64 bit processor to see all of yoru ram.  I think that can make it see like 1 Tb after that.  Then they are comming out with an extension ontop of that for 4 petabytes of ram.  But the tweaks in the software are harder than getting vmware or others to work on ubuntu 64bit.  Just some info and my 2 cents.

---

### Post by kaginken on 2008-03-04
Thanks for all the info guys!  The consensus so far is 64 bit...

Anyone got an argument for 32 bit?

---

### Post by igknighted on 2008-03-04
Do you need flash?  Or the java plugin?

Actually, if you want to run Fedora Directory Server or RH-DS and need to open the browser-based control panel on the server itself (ie, in firefox), you may be in trouble as it is java-based.  But thats about it.

---

### Post by kaginken on 2008-03-04
So there are java and flash known problems with the 64 bit version?

---

### Post by steveneddy on 2008-03-04
> **kaginken said:**
> So there are java and flash known problems with the 64 bit version?

You should go to the 64 bit forums and check out what they are saying there.

I run 64 bit and java and flash run very well for me.

No issues with either.

If you have a 64 bit processor, just run the 64 bit version of Ubuntu.

You will be much happier.

---

### Post by igknighted on 2008-03-04
> **kaginken said:**
> So there are java and flash known problems with the 64 bit version?

Flash and java are fine on the server end in 64bit.  It is the client-side where there are no (current) native plugins for web browsers.  If you are running a server this is almost certainly of no concern to you.

---

### Post by kaginken on 2008-03-04
Steveneddy,

We haven't yet purchased the hardware for this yet - but we're leaning towards trying to make a go of running this on Ubuntu and it's sounding like we'll need the 64 bit setup for large memory.  

Red Hat has this support, but their prices have more than tripled since last year.  

I've been touting ubuntu at my company for months now and am starting to be heard.  We just stood up two small ubuntu servers albeit VM machines, nevertheless, our first ubuntu presence!  Any my manager was pleased with the ease of installation and subsequent application installs that followed.  We had actually started out trying to use centos and ran into dependency hell, and decided to use ubuntu.  It was painless from that point on!

Now we want a big beefy setup (Dell PE 6950) with gobs of memory.  If I can persuade the powers that be to give Ubuntu a shot - this will be a giant step.  But I first need to be sure it will do what we need.

Can anyone sing praises to VMWare 1.0.4 running on Ubuntu 64 bit?  I sure hope so, I really want this to work.

Thank again, for all your help!

---

