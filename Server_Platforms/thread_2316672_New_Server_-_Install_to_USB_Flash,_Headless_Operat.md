---
title: "New Server - Install to USB Flash, Headless Operation, Webmin, Future stuff"
date: 2016-03-09
forum: Server Platforms
---

### Post by YeongMin on 2016-03-09
Wanting to do a new install of Ubuntu Server 14.04LTS.  Would like some feedback, pointers, opinions, warnings, etc., please.

Download **iso **and create installation on **USB**. Disconnect the** two SATA **and the** USB3 drive **and** install to 32GB Samsung USB3 Flash Drive**.
Q: Would it benefit to use** USB3 over USB2** for the OS?

After install, shutdown, remove installation media. Reboot. Set Static IP. **Install Webmin**. Shutdown.

**Reconnect** all drives, **remove **video card &** replace with **4-port NIC. Tuck the box in the corner.** Reboot headless.** Connect to Webmin.
Q: I'm assuming at this point I can fully administer Ubuntu Server via Webmin. I was thinking about using **nomachine;** but read something about X-server not starting due to no vidcard...correct?
Q: I realize Webmin won't let me config specific Ubuntu environment stuff, doesn't matter; but I'll be looking to** run DHCP and File Server**, along with setting it up as the **Gateway Router **in the near future and I'm hoping Webmin will work for that. The biggest task is being able to [B]run this Ubuntu server box as headless.
[/B]
Format the drives. Set up **Raid1 **between the two SATAs. Create Samba shares. Create Users/Groups, etc.
Q: I have mixed clients: Linux, Windows, & Macintosh. Should I just** use SMB or use NFS too **and whatever Macintosh uses?

I hope this gives an idea of what I'm trying to accomplish and will help in giving the necessary instructions.

---

### Post by CharlesA on 2016-03-09
You would be better off running something like [FreeNAS]("http://www.freenas.org/").

[Webmin has terrible security and isn't recommended.]("https://help.ubuntu.com/community/WebMin")

---

### Post by YeongMin on 2016-03-09
FreeNAS is what I currently have installed and running. I think there's a DHCP service I can install; but wasn't aware FreeNAS being able to run as a Router?

Researching now...

---

### Post by CharlesA on 2016-03-10
You really shouldn't be using the same machine as a file server and router. If it is compromised, you are totally screwed.

I also have to ask - why do you seem set on using a USB stick as the OS drive? You would more than likely have atrocious transfer speeds.

---

### Post by YeongMin on 2016-03-10
Ok. Thanks for the info and concerns. Can you address any of my questions:

Q: Would it benefit to use USB3 over USB2 for the OS?

Q: I was thinking about using nomachine; but read something about X-server not starting due to no vidcard...correct?

 Q: The biggest task is being able to run this Ubuntu server box as headless.

Q: I have mixed clients: Linux, Windows, & Macintosh. Should I just use SMB or use NFS too and whatever Macintosh uses?

---

### Post by CharlesA on 2016-03-10
> **YeongMin said:**
> Ok. Thanks for the info and concerns. Can you address any of my questions:

Q: Would it benefit to use[B] USB3 over USB2 for the OS?
[B][B][B][B][B]
Q: I was thinking about using [B]nomachine; but read something about X-server not starting due to no vidcard...correct?

 Q: [B][B]The biggest task is being able to [B]run this Ubuntu server box as headless.
[B]
Q: I have mixed clients: Linux, Windows, & Macintosh. Should I just** use SMB or use NFS too and whatever Macintosh uses?**[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]

1. Using a USB3 external enclosure rather than a USB stick would be better for the OS drive imo.
2. I have not used a GUI on any of my servers in a long time, so I cannot answer this question. Most boxes should at least have video out to get to a console.
3. Should run headless fine, but I would strongly advise against putting a GUI or Webmin on it - use SSH to manage it.
4. SMB should be fine - but you can use NFS too - I believe the latest Windows releases support it natively.

You really should take a step back and evaluate what your goal is and the method you want to use to accomplish it. If you are deadset on having all these services running off of one machine, you really should look into virtualization so you have at least some sort of separation of services. That way, if one of your machines gets compromised, you can reinstall that machine rather than having to reinstall the whole server and restore your data from backups. Also, keep in mind that you will need to read up on and implement a variety of configuration based on best practices. A good place to start is here: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Now, I have a few questions:
1. What are you using as your current gateway/router? Why do you want to replace it?
2. How much experience do you have with administering a linux server?
3. Will this server be accessible from the Internet as a whole? If you do go ahead with creating a gateway with this machine, it will have to handle serving content as well as keeping the network safe. Not an ideal combination.

---

### Post by QIII on 2016-03-10
A USB 3.0 flash drive may run on a USB 3.0 interface, but you won't get USB 3.0 speed out of it.  Flash memory is slow.  Rather than the theoretical USB 3.0 speed of 5Gbps, you will be doing well to get 200Mbps with a top of the line, expensive model.  More likely 100Mb/s.  Faster than a USB 2.0 flash drive, but far, far slower than a traditional mechanical drive over USB 3.0.

Why not just use a traditional SATA rev III drive at (theoretically) 6Gbps?

---

### Post by mastablasta on 2016-03-10
> **YeongMin said:**
> Ok. Thanks for the info and concerns. Can you address any of my questions:

Q: Would it benefit to use USB3 over USB2 for the OS?

It is a bit faster I guess.
> 
Q: I was thinking about using nomachine; but read something about X-server not starting due to no vidcard...correct?

why do you need to install x-server? webmin doesn't needit. furthermore have you explored other options for webgui?:
Zentyal (free SBS replacement)
Ajenti - very light webgui, works on Ubuntu
Openmediavault - Debian based, kind of like FreeNAS

CentOS based, easy to install and use:
Nethserver
ClearOS

there are more out there...

> 
 Q: The biggest task is being able to run this Ubuntu server box as headless.

that's the easiest task: you install server edition (no GUI), install SSH and unplug the monitor. You are then done. headless server will be running and you can start configuring it.

> 
Q: I have mixed clients: Linux, Windows, & Macintosh. Should I just use SMB or use NFS too and whatever Macintosh uses?

How about installing something like owncloud or seafile? otherwise SMB is fine. I use sFTP since some users are remote.

> **QIII said:**
> A USB 3.0 flash drive may run on a USB 3.0 interface, but you won't get USB 3.0 speed out of it.  Flash memory is slow.  Rather than the theoretical USB 3.0 speed of 5Gbps, you will be doing well to get 200Mbps with a top of the line, expensive model.  More likely 100Mb/s.  Faster than a USB 2.0 flash drive, but far, far slower than a traditional mechanical drive over USB 3.0.

Why not just use a traditional SATA rev III drive at (theoretically) 6Gbps?

I am running it like that. though the boot is not stellar once it's up I can't say I have any complaints. it is serving only 6 users, data is on wd red disks, but OS is on USB stick. bigger problem is USB sticks die (get corrupted) without warning and can die fast. otherwise they are cheap to replace.

---

### Post by YeongMin on 2016-03-10
Good stuff. Lots of new ideas to try out, theorize and learn from for educational purposes. Thank you.

The hardware is what I have for FreeNAS and was wondering if I could go to a multi-purpose Server on the same hardware. USB2/3, SATA - yup, good info. Will research the other webgui. The x-server option was about using nomachine for remote desktop. Hmmm, didn't consider internal cloud/ftp instead of SMB. Will look at that.

Currently using Netgear X6 R8000 as the gateway/router. Configuration is really limited. I had an ASUS RT-AC68R and the configuration was a little more open. Both are experiencing service issues and was theorizing that it was due to one machine trying to do too much or network saturation. So just wanted to separate some of the tasks and do some testing and troubleshooting. So, this is good info. I have little experience with Linux servers; but moderate experience with Unix servers. Wanted to mess with firewall stuff too.

Anyhow, thanks again for the answers and info. Got some stuff to do. Kahmsamnida.

---

### Post by mastablasta on 2016-03-11
regarding firewall - there are distros designed specifically for such things (routers, firewalls etc.). check distrowatch for a few. if you have money you could cobble together small and strong PC (e.g. with small Celeron or Atom) for doing that. I am not sure if any of specialised distros run on these small boards such as RPi and similar. surely they have some kind of ARM support?! I think some of those use BSD.

depends on data and traffic your issue might not be router related. this could be investigated using network monitoring software.

---

### Post by CharlesA on 2016-03-11
> **mastablasta said:**
> regarding firewall - there are distros designed specifically for such things (routers, firewalls etc.). check distrowatch for a few. if you have money you could cobble together small and strong PC (e.g. with small Celeron or Atom) for doing that. I am not sure if any of specialised distros run on these small boards such as RPi and similar. surely they have some kind of ARM support?! I think some of those use BSD.

depends on data and traffic your issue might not be router related. this could be investigated using network monitoring software.

Definitely. I've looked at pfSense and Smoothwall before, but haven't had the time to actually get an appliance set up to work with them yet.

It might also be worth looking into OpenWRT or DD-WRT for the routers they already have - the stock firmware is usually pretty bad overall.

---

