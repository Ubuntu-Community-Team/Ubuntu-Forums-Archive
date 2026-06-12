---
title: "Ubuntu on old hardware - getting hold of old packages"
date: 2016-07-19
forum: Server Platforms
---

### Post by phdfox on 2016-07-19
Hi all

I know how long it's been LTS but I need the following packages for Ubuntu Lucid (10.04).    build-essential libopenmpi-dev openmpi-bin libssl-dev 


Is it simply the case that as Lucid is LTS, I can't get them anywhere or is there an archive somewhre for people who are prepared to use them even though they're old?   My only alternative to using these old packages is to upgrade a lot of very old hardware to a newer version of Ubuntu server (which would cause me problems configuring from the command line) - hence I'd like to try this solution first.

Thanks

---

### Post by howefield on 2016-07-19
Thread moved to the "*Server Platforms*" forum.

EOL Ubuntu repositories are moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

---

### Post by mörgæs on 2016-07-19
Out of support means out of security. 
Though it takes time I recommend that you install 16.04.

---

### Post by mastablasta on 2016-07-20
at least move to 14.04 (old LTS). 16.04 brings systemd which might need some changes and tweaks made. the 14.04 uses the old upstart system so any scripts and such that refer it it will continue to work.

---

### Post by MAFoElffen on 2016-07-20
> **phdfox said:**
> ...
Is it simply the case that as Lucid is LTS, I can't get them anywhere or is there an archive somewhre for people who are prepared to use them even though they're old?   My only alternative to using these old packages is to upgrade a lot of very old hardware to a newer version of Ubuntu server (which would cause me problems configuring from the command line) - hence I'd like to try this solution first.
...
I would hate for you to take offense. Not meaning this in that manner. There is a hole in your reasoning (that I quoted from your original post). 

You said you have old hardware. You know that 10.04 LTS is long out of support... But that (alone) does not mean that your old hardware is out of support by the newer versioned LTS'es that are still supported. (And by the way, 12.04 LTS is still supported.) 

The first question would be "What is you hardware? (Brand. Model, CPU, RAM, HDD and controllers, etc...)

Here is why the above really does not wash: There is only a few exceptions where old hardware has lost support, but there are workarounds for most of those. If you have some of the older Pentiums... I still have some 2 x Pentium III processor'ed  test servers here on Ubuntu Server 32 bit. I keep wanting to retire them, but they are paid for and just keep wanting to do something. The challange is going to be if your have a 32 bit proc that does not support PAE. But that is only just a "challenge."

So other questions are:
What is your vision of what you want to accomplish?
Is it going to be connected to the outside world?
Since "old hardware" is not a valid reason for not upgrading, why do you think you need to stay with a 6 year old OS that is long since been past it's due date?

---

### Post by phdfox on 2016-07-22
> The first question would be "What is you hardware? (Brand. Model, CPU, RAM, HDD and controllers, etc...)

I have 4 Dell PowerEdge 860's (max 2Gb RAM in each) running Lucid.   They're configures to be a parallel cluster which means a specific network configuration.   Security wise is not such an issue as they're on a LAN which is not connected to the web (unless via a one machine gateway that's often switched off - hence no security worries).

I do appreciate I could install a much newer version of Ubuntu - but I'm not very good at configuring via the command line - especially as regards networking so I would need to install a desktop OS - and this is where the problems arise - I've tried them with newer versions and the desktops crash.

Thanks anyway - I will look at old-releases.ubuntu.com

---

### Post by MAFoElffen on 2016-07-24
You are good through 12.04... Beyond that, you have to choose some other cluster packages to get to 14.04. The older cluster packages were deprecated between 12.04 and 14.04. 

Your spec's are actually better than you said.
```

Dell PowerEdge 860 Specs:

Brand: Dell.
Product Line: PowerEdge.
Product Type: Rackmount Server.
Form Factor: 1U Rack.
Processors: 1x Dual Core Intel Xeon 3000 or Intel Pentium D Processor.
Processor Cache: Up to 2MB L3.
Memory: Fully expandable up to 8GB PC2-5300 NON-ECC UDIMM.
Hard Drives: Up to 2x 3.5" SAS / SATA hard drives.

```
You would be good through 16.04 supporting your hardware, but the services you are running would need migration to get you there.

---

