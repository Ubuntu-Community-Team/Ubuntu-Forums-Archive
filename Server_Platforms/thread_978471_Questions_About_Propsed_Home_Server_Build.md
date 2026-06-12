---
title: "Questions About Propsed Home Server Build"
date: 2008-11-11
forum: Server Platforms
---

### Post by falconed7 on 2008-11-11
Hey everyone!

I am at the stage where I'm planning for my home server build (Ubuntu server 8.04 LTS) and I have a few questions about the setup stage. The main purpose of this server will be:
[LIST]
[*]General file storage and sharing
[*]Stream media (not transcoding, just sharing) to PS3
[*]Back up certain folders to an external HDD automatically
[*]Access remotely - outside of home network to upload files and manage server
[/LIST]

I'm relatively new to Ubuntu and have only used the desktop version for about 2 weeks. However, I think I can handle the command line only environment with the help of some [guides]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts").

Okay my main questions are:
[LIST=1]
[*]Do I need to setup a static IP even if my internet plan has a dynamic IP? I was told I can use a dynamic IP and use [www.dyndns.com](www.dyndns.com) with an IP updater to constantly keep my IP up-to-date.
[*]Would software RAID be worth it? I was thinking a small HDD for Ubuntu itself and a software RAID1 array. However, I'm thinking it might not be worth it considering I'll be backing up to an external HDD.
[/LIST]

Those two are my main questions and am currently confused with the static IP configuration if my plan is only a dynamic IP.

As for the remote access I've read about webmin, can this upload files to the server?

Any help will be great!
Cheers.

---

### Post by Philio on 2008-11-11
Dynamic DNS does work, it can be unreliable sometimes though, ideally if you have a static IP then you can just setup a nameserver and point your domains at it (as you would on a located server).

Software raid 1 would be ok if you don't have a hardware raid card, I use it on a couple of our cheaper servers as Linux didn't recognise the RAID controller. It works fine and gives you a safeguard should one of the disks fail.

Which software do you plan on using to share video to the PS3 out of interest? I've been meaning to set something like that up myself but never got round to it!

---

### Post by falconed7 on 2008-11-11
> **Philio said:**
> Dynamic DNS does work, it can be unreliable sometimes though, ideally if you have a static IP then you can just setup a nameserver and point your domains at it (as you would on a located server).

Software raid 1 would be ok if you don't have a hardware raid card, I use it on a couple of our cheaper servers as Linux didn't recognise the RAID controller. It works fine and gives you a safeguard should one of the disks fail.

Which software do you plan on using to share video to the PS3 out of interest? I've been meaning to set something like that up myself but never got round to it!

Thanks for the reply!

I have heard about mediatomb for streaming to the PS3 so I'll be checking that out soon.

As for the IP issue, what would be my best option? Am I able to set up a static IP without changing plans?

---

### Post by erwall on 2008-11-11
> **falconed7 said:**
> Thanks for the reply!

I have heard about mediatomb for streaming to the PS3 so I'll be checking that out soon.

As for the IP issue, what would be my best option? Am I able to set up a static IP without changing plans?
FWIW, I've never had a problem w/dyndns.org in 3-4 years.  If your router/gateway supports updating it then it's a piece of cake.

As a side note, I do have the ~$10 a year plan w/dyndns so I can have pretty much as many hosts as I want.  I use it to be able to support my family members' computers without them having to go to [http://www.whatismyip.com](http://www.whatismyip.com) all the time.

+1 for mediatomb, I use it to stream to my XBMC, works great.

As cheap as storage is now, to me it just makes sense to get 2 drives and use them in a RAID1.  I would use a single drive for the OS then 2 large drives in a RAID1 for storage.  I've noticed little to no difference in speed.

> **Philio said:**
> Software raid 1 would be ok if you don't have a hardware raid card, I use it on a couple of our cheaper servers as Linux didn't recognize the RAID controller.

Actually, pretty much all the onboard raid controllers on motherboards use a software raid (unless you have a REAL raid card).  Having the driver for Windows in a Windows install makes it look like a hardware raid but it really isn't.  It's often termed as "fakeraid"

---

### Post by CrucifiedEgo on 2008-11-11
unless uptime is a big concern, raid1 is overkill.  I'd keep two disks, but rsync one to the other every 4/12/24/whatever hours.  This way you have a backup if you lose a disk, and in case you rm -rf /media/storagedisk/.

---

### Post by falconed7 on 2008-11-11
> **CrucifiedEgo said:**
> unless uptime is a big concern, raid1 is overkill.  I'd keep two disks, but rsync one to the other every 4/12/24/whatever hours.  This way you have a backup if you lose a disk, and in case you rm -rf /media/storagedisk/.

Thanks guys.

Yeah I was just thinking having a small HDD for the OS then a larger 640GB drive for everything else and just back up to the ext HDD.

Is it possible to get webmin working with dyndns?

---

### Post by CrucifiedEgo on 2008-11-11
Yeah, dyndns just provides the hostname, so you don't have to type in your IP address, you just use [http://yourname.dyndns.org:10000](http://yourname.dyndns.org:10000)

---

### Post by falconed7 on 2008-11-11
> **CrucifiedEgo said:**
> Yeah, dyndns just provides the hostname, so you don't have to type in your IP address, you just use [http://yourname.dyndns.org:10000](http://yourname.dyndns.org:10000)

Okay thanks for that.

Must I run a client (like this: [http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)) on the server that constantly checks my IP and changes it accordingly? Or do I just need to put the settings in my router for a dynamic DNS service?

Sorry for all of the questions. Is there a guide for setting up webmin with dyndns anywhere?

Cheers everyone.

---

### Post by CrucifiedEgo on 2008-11-12
Either way works.  Ubuntu has a package called ddclient that you can run, but if your router supports it i'd recommend using it, as it's way easier and less hassle.

As far as webmin + dyndns, there's nothing to it. Get webmin working on the box.  setup DynDNS.  Enjoy.  Profit (?).

---

### Post by falconed7 on 2008-11-13
Thank you for the help. 

I should be getting my parts within 2 weeks and will definitely come here for any help!

Cheers.

---

