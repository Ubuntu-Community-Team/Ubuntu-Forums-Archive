---
title: "Vlan tagging, Nextcloud and Containers"
date: 2022-01-16
forum: The Cafe
---

### Post by DuckHook on 2022-01-16
After almost a year, I finally summoned the verve to follow up on an intriguing suggestion from TheFu and kevdog in the following two threads:

[https://ubuntuforums.org/showthread.php?t=2458084&page=3&p=14022550#post14022550](https://ubuntuforums.org/showthread.php?t=2458084&page=3&p=14022550#post14022550)
[https://ubuntuforums.org/showthread.php?t=2457747&page=3](https://ubuntuforums.org/showthread.php?t=2457747&page=3)

I've chosen OPNSense, installed it in a Qotom router, and have successfully mirrored my old WAN/LAN layout. Even succeeded in hiving off one NIC as a DMZ for untrusted devices. So far, loving it. OPNSense is awesome.

I'm going to try setting up a VLAN next and, using VLAN tags, isolate one of my servers in the basement (the one running Nextcloud) to the OPNSense router upstairs. A managed switch is already on the way.

Does anyone know any good, simple tutorials or howtos for VLAN tagging? That would be very useful. I've found plenty of tutorials for physical LAN segmentation and even setting up VLANs but they all treat VLAN *tagging* as something mentioned only in passing; few details.

Directions to more info would be greatly appreciated.

---

### Post by kevdog on 2022-01-17
Lawrence systems has some great videos on VLAN tagging.  The problem with VLAN tagging is not the specifics -- it's the hardware since everyone's interface does it a little different.  You need managed switches to pass the VLAN tags along.  Also the Cisco standard is VLAN 1 untagged, and everything else tagged -- however not everyone's system actually do this.  It also depends on the end range device -- for example your server running Nextcloud -- does the tagging information end at the last managed switch or do you want to carry it over to the actual network card on the device.  Some devices are dumb (TV's, etc) and can not interpret VLAN tagging information, whereas others can be configured to receive and interpret the VLAN information.  I think that's why you don't see any specific information on this topic.  Easy topic to understand, but usually hardware specific on how to "actually" configure the trunk and access ports.

---

### Post by DuckHook on 2022-01-17
Thanks again kevdog.

Was hoping you would poke your head in here. You and TheFu are the big reasons I now have even better security.

I have a managed smart switch on the way. Should be here by end of week, at which point, I will take the next steps. It's this one: [https://us.dlink.com/en/products/dgs-1100-08v2-8-port-gigabit-smart-managed-switch](https://us.dlink.com/en/products/dgs-1100-08v2-8-port-gigabit-smart-managed-switch)

I'm kinda sorta hopeful it will work. Awfully cheap for something hyped up as so powerful/versatile. We shall see.

I intend to reconfigure my Nextcloud instance to bind to one physical NIC. I'm going for simplicity rather than versatility. One hop from router to managed switch, then directly into a NIC dedicated to Nextcloud. I intend to stick to the KISS principle. Don't need the aggravation from trying to get too fancy.

BTW, you are absolutely right: OPNSense is amazing. The only drawback is having to learn BSD, but the web interface takes care of almost everything and I am not averse to slowly plugging away at a new OS.

---

### Post by DuckHook on 2022-01-17
> **kevdog said:**
> Lawrence systems has some great videos on VLAN tagging…
Found their videos. Mind-boggling stuff. Lots to learn. Almost too much, but thanks again.

---

### Post by DuckHook on 2022-01-21
Happy to report that this project has been successful. Nextcloud is now segmented and firewalled into its own little VLAN. It took a while to wrap my head around the network concepts involved, but kevdog's gracious advice and the pointer to Lawrence Systems were invaluable. Thanks, kevdog!

As an aside, the D-Link managed switch is quite the beast. Punches WAY above it's weight class. I had my doubts with something that cheap, but so far, it's been running like a champ. My pessimistic side says it will last a few months before dying on me, but if it goes the distance, then it will be an awesome value proposition for anyone else trying a similar setup.

---

### Post by annekeh on 2022-02-16
Woah! Thanks for this.

---

### Post by kevdog on 2022-02-16
@DuckHook.  You probably learned alot doing it the way you did. I guess I just went the expensive way and overtime just converted all my switches and Access Points to Unifi -- which does VLAN tagging a little bit differently than DLink but concepts are the same.  I needed to setup VLAN tags also on my pfSense router but that was pretty simple.  Seriously considering moving to opnSense however it kind of like when you get everything running and it's worry free -- its really hard to justify change just for change sake (as long as the CE edition of pfSense is still supported).  

I'm also running a separate FreeNAS server on bare metal and have virtualized a few Ubuntu/Arch installations withinN FreeNAS.  Getting FreeNAS to pass the VLAN tag information was actually very difficult.  For me I ended up having to tag every network (even VLAN1) and pass no untagged traffic. I then had to setup separate bridges each assigned a different VLAN tag number, and associate each VM with whatever bridge/VLAN I wanted.  I believe I actually have Nextcloud running within a FreeNAS jail with the jail associated with a specific bridge/VLAN.  

I'd actually be curious how you setup your Nextcloud instance however I'm guessing you dedicated your dedicated Nextcloud NIC connects to your managed switch via an access port (as compared to a trunk port).  Tell me if I'm wrong since I'm always curious.  Are you running Nextcloud with natively within a machine running Ubuntu? I'm a big fan of virtualization and docker and containerization, so I guess if I were going to do it all over, I'd probably run Nextcloud either in a LXC container (like those available in ProxMox), or I'd run Nextcloud via the docker images.  I'm running TrueNAS Core (FreeBSD based) however TrueNAS Scale (Linux based) has ability to run containers directly -- bypassing need for LXC container or VM -- so I'd be apt to try something like that -- if I ever get around to it.

---

### Post by DuckHook on 2022-02-16
Hi kevdog,
> **kevdog said:**
> You probably learned alot doing it the way you did.
Understatement of the year thus far. My head was ready to explode. Networking was a new game to me. I had never set up anything but the most rudimentary networks before—I'd managed to fence off a guest network with an old access point with firewall rules, but that was by following an online recipe, and it was the extent of my networking knowledge. The concept of vlans, tagging, managed switches and, above all, a sophisticated enterprise&#8209;level routing platform like pf/OPNSense was too much above my old pay grade.

But an enforced convalescence (and your previous advice/encouragement) has recently given me the opportunity to climb the learning curve. I'm happy that I did it. I have a far more secure network now, not to mention a wealth of new knowledge. Still learning though.
> Seriously considering moving to opnSense however it kind of like when you get everything running and it's worry free -- its really hard to justify change just for change sake (as long as the CE edition of pfSense is still supported).
Don't know why you would move to another platform that's almost a twin when your current one is just as powerful/versatile. My choice of OPNSense came down to a coin toss. I remembered TheFu saying that it was updated more frequently.

One drawback that I'm wrestling with is that OPNSense has less documentation and tutorials than pfSense. I can usually adapt a pfSense howto because the two platforms are so similar, but not always. If you are used to pfSense online help/strategies, that is one limitation to consider before deciding to migrate.
> I'm also running a separate FreeNAS server on bare metal and have virtualized a few Ubuntu/Arch installations withinN FreeNAS.  Getting FreeNAS to pass the VLAN tag information was actually very difficult.  For me I ended up having to tag every network (even VLAN1) and pass no untagged traffic. I then had to setup separate bridges each assigned a different VLAN tag number, and associate each VM with whatever bridge/VLAN I wanted.  I believe I actually have Nextcloud running within a FreeNAS jail with the jail associated with a specific bridge/VLAN.
I am hopeless with FreeNAS or any of the BSD&#8209;based platforms. I'm still dipping my first little toe into that big ocean and OPNSense is more than enough to start with without getting overwhelmed.
> I'd actually be curious how you setup your Nextcloud instance however I'm guessing you dedicated your dedicated Nextcloud NIC connects to your managed switch via an access port (as compared to a trunk port).  Tell me if I'm wrong since I'm always curious.
Exactly so. Once again following TheFu's advice, I bought a new server which has 4 NICs and dedicated one of them to Nextcloud. So even though my Nextcloud instance runs in a LXD container, as far as it is concerned, it runs on an isolated LAN with no other LAN visible to it.

I did have it running with a vlan initially. That was my initial set up, but I made the change to bind it to its own dedicated physical NIC based on TheFu's cautionary advice.
> Are you running Nextcloud with natively within a machine running Ubuntu? I'm a big fan of virtualization and docker and containerization, so I guess if I were going to do it all over, I'd probably run Nextcloud either in a LXC container (like those available in ProxMox), or I'd run Nextcloud via the docker images. I'm running TrueNAS Core (FreeBSD based) however TrueNAS Scale (Linux based) has ability to run containers directly -- bypassing need for LXC container or VM -- so I'd be apt to try something like that -- if I ever get around to it.
My Nextcloud education has been an evolving one. Since you asked, I'll risk going into a bit more detail. Skipping all of the painful learning curve history, after many false starts, I've arrived at the following setup:

[LIST=1]
[*]I run Nextcloud in a LXD container in a standard Ubuntu Server setup. The server itself is not so simple, but not especially difficult either. All data and LXD is on a ZFS RAIDZ 1 with a striped array of five HDDs. The OS is on a mirrored LVM array on two small SSDs. It has been a long road getting here, but now that I've got it set up, it's phenomenal.
[*]I was initially tempted by Proxmox. It "simplifies" a lot of the setup. Just install Proxmox, download a preconfigured Nextcloud Docker instance, and Bob's yer Uncle. But this made me uneasy. I like to know how things are running under the hood. It's a quirk/failing of mine. If I don't set it up from scratch, I'm always suspicious about what isn't configured properly. That's why I like rolling my own. Over the years, I've found that many types of "simplicity" carry an unacceptable price in terms of security holes, sloth, ignorance, privacy exploitation and data slurping.
[*]So my Nextcloud instance is self configured, running in a LXD container, with every aspect under my control because I rolled it from scratch. I know how Nginx, Apache and PHP have been configured. I know how I have fail2ban set up. I know how often certbot refreshes my letsencrypt certificate. That more atomic level of knowledge/control was what I gained from rolling my own Nextcloud. (For those not as obsessive&#8209;compulsive as I am, Nextcloud can be set up more easily than I've described. It even comes as a self&#8209;contained snap.)
[*]As part of my de-Googling mission, I have always wanted to offer my Nextcloud instance to other family members. However, I didn't feel that I could do so responsibly until I had good resiliency, redundancy and availability set up. To achieve this, I replenished another old server I had lying around to act as a mirror. It doesn't really have the horsepower to run Nextcloud properly, but it's a fallback server, so it will do in a pinch.
[*]This is where LXD really shines. Once both servers are set up properly, it's incredibly easy to mirror my Nextcloud instance. It is literally a short one-liner and the entire primary Nextcloud instance is copied to the backup:```
lxc copy nextcloud backup:nextcloud --refresh
```The process is wickedly efficient because, like rsync, it copies only the changes. I do it every night, but one could run it hourly using a simple cron job. It copies everything, and I mean everything, including profiles, aliases, configs… everything. If my main server goes down, it is literally as easy as unplugging the ethernet cable from the failed machine and plugging it into the backup and I'm instantly up and running.
[*]It is so easy that I'm thinking of placing a third backup server off site at my son's house. If I get catastrophically flooded out at my place, it's simply a matter of redirecting my DNS resolver to my son's IP and everything is up and running again in less than 24 hrs.
[*]I've already migrated my photos, calendars, contacts, storage and mapping functions out of Google (email has been with a separate secure paid provider for some time). I didn't feel quite safe doing so until Nextcloud had the appropriate resiliency/redundancy/availability. It now has. So, bye&#8209;bye Google.
[*]I'm happy to learn that TrueNAS has moved to Linux. Thanks yet again for that little tidbit. I'm reluctant to get too involved with FreeBSD (it's not fair to ask Mrs DH to deal with the mess from an exploding head), so the comfort of a known OS is a big deal for me. When I get up the energy, I'll look into that too. However, it's not a priority. I'm happy enough with Ubuntu Server running LXD that further changes are now quite low on the list.
[/LIST]
There you have it. More than you every wanted to know about my setup.

---

### Post by kevdog on 2022-02-17
With the LXC containers -- are you backing up the Nextcloud configuration and setup -- or the actual database and data?  I like your backup plan as I have no redundancy for my Nextcloud.  I'm running an nginx frontend and have different ZFS datasets mounted for data/config/etc.  I really set my Nextcloud using this guide which made it really easy: [https://www.samueldowling.com/2020/07/24/install-nextcloud-on-freenas-iocage-jail-with-hardened-security/](https://www.samueldowling.com/2020/07/24/install-nextcloud-on-freenas-iocage-jail-with-hardened-security/).  Although my data is snapshotted with ZFS, I don't as of yet have a second NAS to zfs send/receive to the backup server.  Honestly I don't actually know how much space the data is taking up, however I guessing its a few TB of data so its actually kind of hard to move this around.  I'm not sure what your take is but I find Nextcloud to be --- ehhhh!.  Yea it works but it's pretty slow.  It could be my hardware but sometimes its frustrating.  Upgrading Nextcloud seems always to be a pain, particularly when upgrading php versions which I done twice.  Honestly a few years in I really find it to be a pain.  

If you're looking for another project, I suggest either getting Bitwarden (Vaultwarden) server and also getting wireguard setup.  Those are fairly easier projects to get up and running particularly if you have have the knowledge you've already acquired.  I took a long run down reverse proxy lane -- a lot of messing around with nginx, HA proxy and then finally settling on Traefik.  I'm not sure if you've gone down that rabbit hole yet.

---

### Post by DuckHook on 2022-02-17
> **kevdog said:**
> With the LXC containers -- are you backing up the Nextcloud configuration and setup -- or the actual database and data?
Both. The beauty of LXD is that the whole container is copied. As stated: absolutely everything. The config, setup, the entire LAMP stack, certbot & certificate, fail2ban config, database, data—the whole enchilada. I'm sure you already know this, but for any lurkers out there, please do note that this is a mirroring strategy; not an incremental backup strategy. I will be using a different implementation for that.

To further clarify:

[list=1]
[*]I get resiliency from the striped zpool. If one disk goes down, I can still operate from a degraded pool until I replace the disk and it rebuilds.
[*]I get redundancy from the mirrored server.
[*]I get high availability from having both. This would be further enhanced if I manage to get an additional backup server offsite.
[/list]
> I like your backup plan as I have no redundancy for my Nextcloud.
I should reiterate that it's not really a backup strategy. For that, I have another implementation. I periodically hook up a usb drive to the nextcloud container and use duplicity to do an incremental backup. I learned this the hard way, after losing my first few Nextcloud instances (during my self-education phase) to a bad HDD. The thing about incremental backups (versus mirroring) is that I don't always want to restore a whole instance. Sometimes, I just want a file that was accidentally deleted a few weeks ago. Mirroring won't restore that file, whereas a backup will.

It is worth noting that it's far easier to mirror using LXD than it is to backup. Mirroring can be done with that one&#8209;line command; backing up requires the binding of a disk device, then finding all the right directories, then running the backup, then checking the restore. It's involved enough that I frankly don't do it that often. Roughly once a week. I figure that the loss of a week's data is not a disaster.
> I'm running an nginx frontend and have different ZFS datasets mounted for data/config/etc.  I really set my Nextcloud using this guide which made it really easy: [https://www.samueldowling.com/2020/07/24/install-nextcloud-on-freenas-iocage-jail-with-hardened-security/](https://www.samueldowling.com/2020/07/24/install-nextcloud-on-freenas-iocage-jail-with-hardened-security/).
That's a great resource. Thanks for sharing. Just skimming it, I learned a few interesting things that I might try. I'll read it more thoroughly later.

The key difference that I can see is that this installation is on bare metal whereas I learned the hard way to use a container. I initially installed on bare metal too, but can say from personal experience that a container is the way to go. It doesn't have to be LXD. Docker is not only more prevalent, but better documented as a result of its larger prevalence. I'm not familiar with Docker, but it has to have an equivalent to LXD's copy function, and that's the key to an easy mirror.
> Although my data is snapshotted with ZFS, I don't as of yet have a second NAS to zfs send/receive to the backup server.
A ZFS clone would also achieve similar results, but it requires the extra steps of importing the dataset at the destination and then reconfiguring for whatever HW differences there may be between source and destination. I found that cloning from *within* the container platform (whether LXD or Docker) is so much easier.
> Honestly I don't actually know how much space the data is taking up, however I guessing its a few TB of data so its actually kind of hard to move this around.
Now that I've offered it to family, I expect my datasets to grow quickly, so this is a big consideration. However, I've noticed that LXD copy with the --refresh flag makes mirroring possible without too much pain as only the deltas move over the network. Of course, if your daily deltas run into the hundreds of gigabytes, then all bets are off, but such volumes would imply enterprise level usage.

BTW, it is also worth noting that LXD was designed with remote copying in mind. Remotes are designated by URL. This means that, so long as my son's IP address has a URL, I can sync the datasets across town or even cross country as if the two machines are local. The data is encrypted using self signed TLS. This requires an initial key exchange (which can be done when the two machines are first set up and physically proximate), and everything after that is transparent. I love LXD!
> I'm not sure what your take is but I find Nextcloud to be --- ehhhh!.  Yea it works but it's pretty slow.  It could be my hardware but sometimes its frustrating.
Somewhat similar experience here. That's why I relegated my initial server to backup duty and invested in a new machine. Nextcloud is a heavy implementation that's frankly designed for serious HW. Home servers are often built to be glorified file servers. I don't know what you run it on, but some have tried using a RPi. Running Nextcloud on an ARM&#8209;based MOBO is bound to be slower than a slug in molasses. Sorta like trying to mount a jet engine on a tricycle.

My server is an 8-core Atom with 64 GB of ECC RAM and a dedicated SSD for ARC caching, which seems to be sufficient. The Atom is underpowered, but I didn't want a monster server gulping kilowatts of electicity, so it was a compromise between performance and power efficiency. My HDDs are small 2.5" slow 2 TB models that I salvaged from another project. It was put together with cost consciousness in mind, so yet another compromise. Had I splurged for high end SSDs and a Godzilla CPU, I'm sure that the thing would run much faster. As it is, I'll live with the reduced performance.

I've been running it for about a year now and it's been fine. Oddly, the slowest access has been locally through the browser. My Android apps run well without perceptable lag. Thunderbird also updates the calendar and contacts with acceptable speed. It's only when I log in through my browser that it takes a while for the dashboard to load. Once in, file uploads/downloads are okay. But then, I don't have terrabytes of data on mine like you have. I don't really know how much it will slow down once it starts getting filled up.
> Upgrading Nextcloud seems always to be a pain, particularly when upgrading php versions which I done twice.  Honestly a few years in I really find it to be a pain.
Interesting, in a depressing sort of way. I'm still in the first bloom of romance with it, so I'm loving it, but your experience is resetting my expectations a bit more realistically. That may be a good thing. It may spur me to look at eventual alternatives.
> If you're looking for another project, I suggest either getting Bitwarden (Vaultwarden) server and also getting wireguard setup.  Those are fairly easier projects to get up and running particularly if you have have the knowledge you've already acquired.
Great minds thinking alike and all that…
I've used keepass for two years now (thanks, TheFu), and just successfully set up Wireguard a month ago. They are both awesome and will be a regular part of life for me and Mrs DH going forward.
> I took a long run down reverse proxy lane -- a lot of messing around with nginx, HA proxy and then finally settling on Traefik.  I'm not sure if you've gone down that rabbit hole yet.
Yet another great tip. I have much to thank you for. So far, the only thing that I have open to the outside world is Nextcloud, so I have no need for reverse proxy yet, but I have indeed been curious for awhile. 

So you found Traefik to be an easier implementation than the spin&#8209;your&#8209;own nginx+haproxy? I see a lot of online guides for the latter, but if I can use a FOSS solution that is easier and prebuilt, I'm game. OPNSense taught me a lot, especially about how slick and professional these tools can be.

Just visited the Traefik website. Way beyond cool. I will definitely look at this solution if I ever decide to, say, try hosting my own Wordpress site.

Wow. it's late and this post is WAY too long. Thanks so much, kevdog. I have so much to chew on. Hope I've somewhat answered your questions as well.

---

### Post by kevdog on 2022-02-17
@DuckHook

Thanks for all the details.  I don't know anything about LXC containers other than they exist.  From what you've been saying -- they sound great.  Nice replication abilities with deltas.  I suppose if I ever get around to installing ProxMox I'll use some of these containers as I believe LXC containerization is native to ProxMox.  Thanks for the overview -- I really enjoyed it.

In terms of Reverse Proxies -- pick your poison.  I probably learned the most by just configuring nginx reverse proxy by hand -- built all the vdomain files myself -- and it taught me a lot about headers and what not.  Honestly it's probably still the most versatile proxy out there, however its a little intimidating just starting from scratch.  A lot of examples out on the web regarding how to use nginx so I was never at a loss of looking at a lot of examples.  I'm aware you like to know how things work -- so this might be up your alley.   The one thing I didn't like about nginx however was there wasn't any graphical interface to check configuration.  Honestly it was a lot of looking at log files and googling trying to find out why things didn't work.  Super time consuming.  Some developer made a graphical front end known as Nginx Proxy Manager - however for really simple stuff its fine, however I would highly recommend staying away from this product.  The GUI is super simple and honestly it teaches you nothing about how a reverse proxy works.  If you need to do anything with a little complexity -- NPM isn't going to cut it.  

With Traefik -- dang -- it honestly took my head about 2 days to comprehend what they were talking about with the dynamic and static configuration files, and the term providers.  They use a little bit different terminogies for similar things in nginx -- they just use different words to mean the same things.  If you are in to just learning about reverse proxies, Hussain Nasser ([https://www.youtube.com/c/HusseinNasser-software-engineering](https://www.youtube.com/c/HusseinNasser-software-engineering)) does a great series where he reviewed like 3-4 reverse proxies.  I thought he did a great job just showing some basics.  Check out those videos if interested.  I wouldn't say Traefik was any easier -- in fact transitioning from Nginx to Traefik was like really difficult b/c of the terminology -- but once the light bulb kind of turned on -- I was like wow!! Really cool.  I like Traefik since it has a nice GUI (not for configuration but for giving you feedback on your rulesets).  Its really good for debugging and seeing if your rules are correctly written.  I'm not really ready to take the jump to either K3s or K8s or Consul, however I'm aware these high availability solutions use something called an ingress controller and I believe Traefik can be used for this purpose.  I don't think nginx can be used (or at least I haven't found any examples of people using nginx in this manner).  I'm just slowly overtime building my knowledge base which helps when finally wanting to take a bigger step.  The other reverse proxy I've never tried which people say is really easy is Caddy.  I'm aware this has a loyal following.  Haproxy seemed a little limited to me, however it is built into pfSense directly -- so yea I definitely am sacrificing some ease of use by not implementing this since I already have pfSense installed.  The version of HaProxy offered by pfSense however is like super super old, and many of the examples I found on the web were not applicable to such an older version of the program.  I eventually just moved onto another reverse proxy.  Unless you want to take the long slow painful slide  -- but learn a ton of things by setting up nginx manually -- I'd suggest you start with either Caddy or Traefik.  Just my two cents.

---

### Post by DuckHook on 2022-02-17
Thanks for even more info.

Though LXD has been very good to me, I do have a few beefs with it and may as well alert you to its drawbacks:

[list=1]
[*]Poor documentation: This is a real and frustrating limitation. There are no man pages, the official web docs are arcane, overly general and lacking in useful examples, community help is constrained to various developer blogs and the sparsely populated forums, but is otherwise mostly of the rumour variety. Unless one is retired like I am and has a penchant for sleuthing, finding info is an exercise in obscurantism.
[*]LXD is a Canonical product: It *is* FOSS, so some other distros have adopted it, but its origins have made it secondary to Docker. You will be relying on a smaller set of devs and maintainers to fix or enhance it. My use cases are pretty simple, but those with more complex requirements may find its obscurity to be a drawback.
[*]Overreliance on ZFS: If you are already using ZFS then you are in luck. Otherwise, you will have to learn a new file system concurrent with the new LXD platform. It's a double learning curve. While LXD states that it can run on BTRFS, LVM and even EXT4 (with severe limitations), these are not realistic alternatives. All howtos assume ZFS as a backend and the official docs do to. Frankly, the platform is built with ZFS as its backend and, in practice, ZFS is a dependency.
[/list]
It's taken me three years to get LXD working to my liking. I may be a slow learner, but I'm not *that* slow. It's more likely that my slow progress is a result of the obscurity enumerated above.

I will say this though: once you've conquered its learning curve, it is ultra powerful (and liberating). I now use it not only for its intended server functions but also on my desktop. Its sandboxing capabilities mirror the best features of VMs without the performance hit. And I can port apps and data between different desktops with ease. This brings to my desktop the same redundancy features that I enjoy with Nextcloud.

This thread has long since departed from its initial subject. I've altered the thread title to reflect our discussion.

---

### Post by kevdog on 2022-02-17
Ohh --- ZFS -- I love it.  Coming from TrueNAS where it runs on ZFS I'm very familiar with how that works -- and frankly that explains how you are able to backup -- its all through snapshots.  Totally get it.  I love learning new things.  I know this is an Ubuntu forum and I use Ubuntu for most of my VMs, however there is nothing like installing Arch Linux with zfs on root.  You have to familiarize yourself with everything in terms of partitioning (Solaris Root type) and then creating your datasets within a chroot, and then adding zfs as a kernel module when building the initramfs.  It all works very well once you totally mess things up like 10-12 times.  ZFS likes to have access to the underlying hardware -- so thinking out loud here -- I wonder how something like Proxmox handles ZFS.  Usually you have to pass disks through to the virtualized instance running ZFS so they have direct access to the hardware.  I wonder if they do this with LXC containers -- or is it Proxmox itself that is responsible for the snapshotting.

---

### Post by DuckHook on 2022-02-17
> **kevdog said:**
> …ZFS likes to have access to the underlying hardware -- so thinking out loud here -- I wonder how something like Proxmox handles ZFS.  Usually you have to pass disks through to the virtualized instance running ZFS so they have direct access to the hardware.  I wonder if they do this with LXC containers -- or is it Proxmox itself that is responsible for the snapshotting.
[https://pve.proxmox.com/wiki/ZFS_on_Linux](https://pve.proxmox.com/wiki/ZFS_on_Linux)

So, it is possible to use ZFS as Proxmox root filesystem. I would suspect that to be the preference. At any rate, the data needs ZFS.

It would surprise me if Proxmox went to the time and trouble of reinventing the wheel to take snapshots when a tried and true method already exists. I'm sure that they just leverage the power of ZFS.

---

