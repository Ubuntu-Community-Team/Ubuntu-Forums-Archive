---
title: "Multi Function Home Server"
date: 2019-12-16
forum: Server Platforms
---

### Post by dirtyelf on 2019-12-16
I'm retiring an old PC and have plans to turn it into a home server. I currently use a few raspberry pis and some other random machines that I'd like to consolidate into one. The machine specs are an [ASUS P7P55D-E PRO]("https://www.asus.com/us/Motherboards/P7P55DE_PRO/"), Intel Core I7-870, 16G ram... and I'll have a 500G SSD boot drive along with some various HDDS for storage. There are a few things I'd like this server to accomplish for me and they are listed below in a semi prioritized list.



[LIST=1]
[*]Storage. I have a 1TB drive in my machine now along with two or three other various external HDDs and they are starting to fill up. My real concern here is data loss. Some of these drives are fairly old and I would like to get some sort of redundancy going instead of just ignoring the issue. I am thinking some sort of RAID? I would like this to be expandable in the future by throwing another disk in occasionally, and not have to buy a whole bunch of disks if possible.
[LIST]
[*]NAS. I'm not sure if this is obvious but I would like the storage to be accessible across my network and potentially outside of the network.
[/LIST]

[*]Web Server. I run two small websites, currently from raspberry pi's which I would like to migrate over to a more powerful machine. If it matters I run nginx/mariadb.
[*]E-mail Server. I also have a small email server on the pi's for my wife and I tat I would like to migrate.
[*]Minecraft Server. My brothers and I enjoy playing minecraft from time to time. I'm not talking 100's of players at a time.
[*]Media Server. Most of what I have spread out across the drives currently is media (photos, home videos, music, etc...) I would like a way for the whole family to stream, view, etc... from wherever.
[*]VPN. Not exactly sure what options exist here and if this is strictly necessary - I think this would essentially be the way I would access from outside my network?
[*]Code repo, sftp, vms, mqtt, ssh...
[*]Tinkering and learning...
[/LIST]


That last point is a good way to explain why I am asking for it to do so many things. I definitely enjoy learning and playing around with different things.


Am I asking too much of one server? Right now the pi's are handling all of the web duties and this machine, even at 10 years old, blows them out of the water. I know storage and media serving can be taxing, but it is just my wife and I (soon to be my daughter) that will be using this. What sort of internal networking upgrade (if any) would I want to make this worthwhile? Currently on a Netgear Nighthawk X4 router.

My plan as of now is to go with Ubuntu Server installed on the SSD. Then grab a few (maybe 5?) HDDS and setup a raid, possibly a ZFS setup? Then I can dockerize the rest of the things I want to use. I was also thinking I would make one of the Pi's run openVPN instead of running that on the main server box.

I am comfortable in ubuntu, but this would be my biggest project by far. Does this setup sound reasonable? The biggest question mark for me is setting up the storage. I have never done that before. The rest of the items I have setup and have running in one way or another. 

Any tips and things to watch out for or other suggestions for setup would be greatly appreciated. I definitely prefer to run ubuntu (hence why i'm here) and not freeNAS or unraid or another NAS specific OS.

---

### Post by aljames2 on 2019-12-16
A lot for 1 server.  I would separate the internet facing server(s) (web & email servers) from the storage server.  combining servers may seem more efficient but can be more problematic.  Having servers spread out diversifies potential downtime risk.  If a Pi blows up running your OpenVPN, no big deal to fix.  If your consolidation of servers on the same hardware blows then you have bigger problems involving more downtime of multiple services.

I don&#8217;t do raid, but a lot of people do.  I do my own backups using various backup tools instead of raid.  Raid is not a backup so be sure to understand its purpose which is primarily to buy you a little time to swap out a bad drive in the array.  But mirroring will also mirror the bad stuff across your drives.  Have backups of your data, even if you deploy a Raid array.

---

### Post by SeijiSensei on 2019-12-17
My server, a [Dell T30]("https://www.amazon.com/Flagship-Dell-PowerEdge-Business-Quad-Core/dp/B07S4FXPNG/"), runs BIND9, openssh, sendmail, dovecot, nfs, Samba, PostgreSQL, ntpd, and Apache. It hardly breaks a sweat.  It has four internal drives, and two mdadm RAID1 arrays. There's also an external USB drive for backups.  It's not exposed to the public Internet though.  My public web and mail servers are VMs at [Linode]("https://linode.com/").

---

### Post by LHammonds on 2019-12-17
I would not recommend RAID for a home server.  I might be inclined to do so if you had a server machine that shows the status of each drive in the array (red/green lights) and an extra set of unused / identical drives laying around on standby when a drive fails.  But since this is a home environment (and RAID is NOT a backup), I would recommend two machines to hold the data.  One would be the primary machine that everyone on your LAN accesses via a mapped network drive (mount) and another that will be your backup server that sync the data from the primary network share to the backup machine.  This means you need to have double the space on two physically separate machines.  To go one step further, I would also make sure I had a 3rd copy of my precious data in an offsite location.  I do this by copying to an encrypted external drive and taking it to work and letting sit in my desk in case something like a fire/flood/tornado happens.

As aljames2 recommended, I would keep the Internet-facing machines (website and email Raspberry Pi machines) separate.  If you are seeing performance issues, determine "what" the bottleneck is.  There usually isn't a high demand on a web server.  If your MariaDB is tapping out the processing power, you might want to offload that to a different machine but make sure the performance issue is the Pi and not your upload limit for your Internet connection.

If the amount of services you want to run are more than the machines you have, you should look at virtualization.  You said the new server is 10 years old.  You might want to install Ubuntu server and do a check to see if your hardware will support virtualization.  If it can, then you can run multiple virtual machines on a single host and better utilize the hardware you have.

```
egrep -c '(vmx|svm)' /proc/cpuinfo
```

If the result is "0" then your hardware does not support virtualization or virtualization is disabled in your BIOS.  If the result is "1" or greater, then your hardware does support virtualization.

LHammonds

---

### Post by dirtyelf on 2019-12-17
> **aljames2 said:**
> A lot for 1 server.  I would separate the internet facing server(s) (web & email servers) from the storage server.  combining servers may seem more efficient but can be more problematic.  Having servers spread out diversifies potential downtime risk.  If a Pi blows up running your OpenVPN, no big deal to fix.  If your consolidation of servers on the same hardware blows then you have bigger problems involving more downtime of multiple services.

I don&#8217;t do raid, but a lot of people do.  I do my own backups using various backup tools instead of raid.  Raid is not a backup so be sure to understand its purpose which is primarily to buy you a little time to swap out a bad drive in the array.  But mirroring will also mirror the bad stuff across your drives.  Have backups of your data, even if you deploy a Raid array.

It does seem like a lot for one server, however my expected loads are very low. Perhaps in the future as my needs grow I can expand to improve fault tolerance and performance. None of these services *require* 100% up time.

I definitely understand RAID is not a backup solution. For me it would be a step in the right direction towards total data security. Right now I just have a bunch of hard drives and external disks. I also want to take this opportunity to learn. Along with purchasing the internal drives I plan on picking up a large external drive to backup all of the data in cold storage (hard drive left unplugged).

> **SeijiSensei said:**
> My server, a [Dell T30]("https://www.amazon.com/Flagship-Dell-PowerEdge-Business-Quad-Core/dp/B07S4FXPNG/"), runs BIND9, openssh, sendmail, dovecot, nfs, Samba, PostgreSQL, ntpd, and Apache. It hardly breaks a sweat.  It has four internal drives, and two mdadm RAID1 arrays. There's also an external USB drive for backups.  It's not exposed to the public Internet though.  My public web and mail servers are VMs at [Linode]("https://linode.com/").

Like I mentioned above I don't think my use case will be overwhelmed. Whats your reasoning for having the web/mail servers elsewhere?

> **LHammonds said:**
> I would not recommend RAID for a home server.  I might be inclined to do so if you had a server machine that shows the status of each drive in the array (red/green lights) and an extra set of unused / identical drives laying around on standby when a drive fails.  But since this is a home environment (and RAID is NOT a backup), I would recommend two machines to hold the data.  One would be the primary machine that everyone on your LAN accesses via a mapped network drive (mount) and another that will be your backup server that sync the data from the primary network share to the backup machine.  This means you need to have double the space on two physically separate machines.  To go one step further, I would also make sure I had a 3rd copy of my precious data in an offsite location.  I do this by copying to an encrypted external drive and taking it to work and letting sit in my desk in case something like a fire/flood/tornado happens.

As aljames2 recommended, I would keep the Internet-facing machines (website and email Raspberry Pi machines) separate.  If you are seeing performance issues, determine "what" the bottleneck is.  There usually isn't a high demand on a web server.  If your MariaDB is tapping out the processing power, you might want to offload that to a different machine but make sure the performance issue is the Pi and not your upload limit for your Internet connection.

If the amount of services you want to run are more than the machines you have, you should look at virtualization.  You said the new server is 10 years old.  You might want to install Ubuntu server and do a check to see if your hardware will support virtualization.  If it can, then you can run multiple virtual machines on a single host and better utilize the hardware you have.

```
egrep -c '(vmx|svm)' /proc/cpuinfo
```

If the result is "0" then your hardware does not support virtualization or virtualization is disabled in your BIOS.  If the result is "1" or greater, then your hardware does support virtualization.

LHammonds

I do plan to implement some sort of deep cold offline storage for backup of precious data in case of natural disaster. The reasons for wanting to implement some sort of a RAID, possibly ZFS, is for the performance benefit, short term fault tolerance, and honestly - the chance to learn something new. 

The two websites are personal sites, nothing business related. The expected loads are very low and I doubt I will notice any performance issues. As things grow perhaps I will but that will be another learning experience for down the road.

I was planning on using Docker, which as far as I know is similar but slightly different than true virtualization. My thought is with the lower-ish amount of RAM (16GB) for a server that Docker is able to make better use of available resources by sharing instead of virtualization requiring me to slice off chunks at a time. I am new to this and still learning. Any insight you have is helpful! Right now the server-to-be machine is still my daily and running windows 7. I have all of the parts for my new ryzen 9 rig sitting on the table ready to be built. Once that is up and running I'll get ubuntu server installed and start poking around.

---

### Post by SeijiSensei on 2019-12-17
> **dirtyelf said:**
> Like I mentioned above I don't think my use case will be overwhelmed. Whats your reasoning for having the web/mail servers elsewhere?
I don't want anyone connecting to a server behind my firewall.  Mail and web are public services and live on machines on the public Internet. Besides I use one virtual server to handle a couple dozen listservers for a client. They defray the cost of the server. My own mail goes through that machine and is delivered to the server in my home.  My web services are pretty secure, since I wrote most of the code myself, but I do use WordPress and would prefer it be isolated from my own network for security reasons. I connect from my home network to the virtual servers over an OpenVPN virtual private network.

In addition, I got tired of worrying about whether my power or Internet connection would go down, or whether a drive on my server might fall over. Linode provides all that for me now including a much bigger Internet pipe than I could possibly afford myself. 

Every night I run a backup script that uses rsync to suck down the important files on the virtual machines. (I also have Linode create daily snapshot backups of my machines as well.)

> I would not recommend RAID for a home server.
I don't understand this argument myself. Most of the stuff on my RAID drives are music, photographs, and videos, all of which are backed up elsewhere.  All of the transitory files on this server are also backed up to the external drive each night.

---

### Post by TheFu on 2019-12-17
16GB of RAM is huge for a Linux server.  This ain't Windows!

This isn't really much for that server.  I've run 20 virtual machines on a Core2 Duo 6600 in less RAM.  I've cut back a little, but still have 15 VMs running on a single machine.  It is mostly idle if there aren't any Windows VMs.  I'm working to get it down to just 6 VMs.

Don't do RAID, unless you have backups nailed down. As others have said, RAID isn't a replacement for backups. When offering any services over the interent, versioned backups are mandatory.  A mirror is NOT sufficient.  Be certain to test the restore of the backups so you know they actually work.  These forums have far too many posts by people who have been creating backups for a long time, but when they finally need them, turns out it wasn't working.

**Docker isn't virtualization**.  It is a logical separation only using kernel sandboxing.  It is NOT the same as a full VM.  If you treat a docker container like a VM, you've failed security.  The best practice for any Linux containers is to run them in a separate VM, not on the hostOS.  You can run multiple containers under the same VM, but I'd separate those by risk factors and network connectivity requirements.  

1 docker container should have 1 service and nothing else.  This is a key aspect to the container security model.  If someone breaks out of the single service, there shouldn't be a shell, ssh, nothing else for them to launch.  Don't treat docker like a VM.  When people do, they've left the tools on the system to break out of the container and hack the host, all other VMs and all other containers.

Never mix an email server with any other sort of server. Ok, 'avoid' mixing an email server with others.  Single physical machine or single-purpose VM, is up to you. dovecot and postfix are pretty light.  512MB of RAM should be overkill.  I run an email gateway VM that blocks over 90% of all SMTP stuff inbound and forwards the remaining 10% to a Zimbra communications server (which is a HOG!).  Keeping the gateway patched is easy. Keeping Zimbra patched is significantly harder. Zimbra isn't directly on the internet and never will be.  Outbound email from zimbra goes through the gateway.  Client access requires being at home on the correct LAN segment or use of the VPN.  I didn't always do it this way, but then saw 100,000 daily login attempts coming from eastern Europe and thought through the problem.  Requiring a VPN isn't really too much to ask.

I keep internet-facing websites in a single VM using nginx as a reverse-proxy. They can contact different back-ends as needed which are not available directly to the internet.  Call it a web-gateway reverse proxy.  A few non-internet-facing internal-only websites like wallabag and nextcloud and calibre also use this reverse proxy with micro-caching.

Use different subnets with firewalling between each to mitigate risks for when you get hacked.  You will be hacked. Expect it.  Have a plan of action, mitigation, recovery.  Hopefully, you'll never need it, but you probably well, eventually.  If my blog gets hacked, I have a static version of the site read to go on a read-only NFS mount.  Change the backend IP - done.  Have a plan for when bad things happen.

If you don't allow direct internet access to most of your services, security becomes much easier. Use either wireguard or openvpn. There are clients for both VPNs on android, windows and Linux.  I've used openvpn for a long time and it is easier for other end-users to understand.  Been thinking about switching to wireguard, but it has some limitations which might not work for my needs.  Being easy and fast are definitely great, but not if I'm in a hotel that blocks all UDP traffic.  wireguard is UDP only.

You can use ZFS if you like.   I like more control over the storage so LVM+ext4 is my poison.  lxd, the Ubuntu Linux Container offering, uses ZFS pools to manage container storage.  Regardless, use storage that supports real snapshots so you can get clean backups.  

ssh should be loaded on every system that isn't a docker container.  Load fail2ban too.  Block password logins over the internet.  With ssh, you get sftp, rsync, scp, and about 50 other connection tools.  ssh can be used to provide a SOCKS proxy from anywhere in the world to your home network.  Poor man's VPN that sorta "just works", provided you understand the limitations (tcp-only).  The lack of UDP support only matters if you aren't already using a DNS-proxy-over-https.  The biggest limitation I have with ssh-socks is Android setups are a hassle, so I just use the VPN instead.  On a full Linux laptop, the SOCK proxy is quick, secure-enough, and easy.  Very comfortable to access any resources in the /etc/hosts file when anywhere in the world.

Media server is a completely separate task.  I don't have mine on the same hardware that serves the internet.  Risk mitigation strategy.  I can access the media over that ssh-socks connection using a web browser and it works.  The rest of the family cannot.  It doesn't work on the VPN subnet I drop them onto either.  They'd never come home if I did that.  ;)  Of course, the subnet I get dropped onto over the VPN does have access to the media and can hop into other subnets here.  The easiest answer for a home media server is to use something with DLNA.  If you need transcoding of the stream for weaker playback devices, then plex media server is the easy option.  I hate the plex clients, so use the DLNA part with bookmarks to skip over the multiple extra layers that DLNA insists we have.  Try out miniDLNA first. Perhaps it will do what you need?  There are lots of DNLA renderers, controllers, so that isn't really an issue.  VLC is one.

Subnetting is the first line of security.  I don't know how well any home router can do it.  I've been using pfSense for a long time and assign different subnets to each port, then use dumb $15 switches to connect the systems to the correct subnet where they are needed.  Please, don't use a flat network for a setup like you are planning.
* internet servers
* internal servers + safe desktops (all wired)
* Kids + wifi + media players + IoT (assumed unsafe)

What are the plans for access controls, SSO-logins, DHCP, DNS on the LAN?  

Do you have any U2F or FIDO2 keys that need support?

And never forget, just because something might be possible, it is up to you to decide if it is actually a good idea.

---

### Post by dirtyelf on 2019-12-19
> **SeijiSensei said:**
> I don't want anyone connecting to a server behind my firewall. Mail and web are public services and live on machines on the public Internet. Besides I use one virtual server to handle a couple dozen listservers for a client. They defray the cost of the server. My own mail goes through that machine and is delivered to the server in my home. My web services are pretty secure, since I wrote most of the code myself, but I do use WordPress and would prefer it be isolated from my own network for security reasons. I connect from my home network to the virtual servers over an OpenVPN virtual private network.


I see the security benefit of not having anyone connecting to servers behind your firewall. I don't have clients, the sites I run are personal. I wrote all of the code myself for my sites as well.. but in my case that likely means there are flaws. It's nearly impossible to write fully secure code. I definitely need more in depth knowledge here but my understanding is the risk I am exposing myself to by hosting my web/email servers inside my own network is that there could be a security flaw in my code, or in the server code that would allow a malicious person to get access inside my network and steal my files or install software that logged my traffic to steal bank info, etc...? Is there anything else I should be concerned about?


> **SeijiSensei said:**
> In addition, I got tired of worrying about whether my power or Internet connection would go down, or whether a drive on my server might fall over. Linode provides all that for me now including a much bigger Internet pipe than I could possibly afford myself. 


I do not need 100% reliability. I certainly will strive for it, but if my power or internet goes out I'll be OK until things are restored. No clients will be calling and complaining. I do have a UPS I'll run the modem, router, and server off of.


> **SeijiSensei said:**
> Every night I run a backup script that uses rsync to suck down the important files on the virtual machines. (I also have Linode create daily snapshot backups of my machines as well.)




I don't understand this argument myself. Most of the stuff on my RAID drives are music, photographs, and videos, all of which are backed up elsewhere. All of the transitory files on this server are also backed up to the external drive each night.


> **TheFu said:**
> Don't do RAID, unless you have backups nailed down. As others have said, RAID isn't a replacement for backups. When offering any services over the interent, versioned backups are mandatory. A mirror is NOT sufficient. Be certain to test the restore of the backups so you know they actually work. These forums have far too many posts by people who have been creating backups for a long time, but when they finally need them, turns out it wasn't working.


> **TheFu said:**
> You can use ZFS if you like. I like more control over the storage so LVM+ext4 is my poison. lxd, the Ubuntu Linux Container offering, uses ZFS pools to manage container storage. Regardless, use storage that supports real snapshots so you can get clean backups.


I understand that RAID/ZFS (or any filesystem for that matter) is not a backup plan. I would like to give it a go, just to learn if nothing else. I am planning on instituting backups to an external drive and storing it in a waterproof, fireproof, blastproof safe. As well as backing up photos, etc to offsite cloud storage. For my needs I believe this is a reasonable starting point. If I find I need something with easier access, more robustness, etc... I'll adjust as my needs grow. Very good tip about actually checking the backups. Now that you say it it seems obvious but I would definitely have been one of those people that never checked until I needed it.


> **TheFu said:**
> 16GB of RAM is huge for a Linux server. This ain't Windows!


This isn't really much for that server. I've run 20 virtual machines on a Core2 Duo 6600 in less RAM. I've cut back a little, but still have 15 VMs running on a single machine. It is mostly idle if there aren't any Windows VMs. I'm working to get it down to just 6 VMs.


Yeah, I forget how little RAM is actually required for many of these things. With workstations shipping with 64+ GB of RAM now it just felt like a small amount.


> **TheFu said:**
> Docker isn't virtualization. It is a logical separation only using kernel sandboxing. It is NOT the same as a full VM. If you treat a docker container like a VM, you've failed security. The best practice for any Linux containers is to run them in a separate VM, not on the hostOS. You can run multiple containers under the same VM, but I'd separate those by risk factors and network connectivity requirements. 


1 docker container should have 1 service and nothing else. This is a key aspect to the container security model. If someone breaks out of the single service, there shouldn't be a shell, ssh, nothing else for them to launch. Don't treat docker like a VM. When people do, they've left the tools on the system to break out of the container and hack the host, all other VMs and all other containers.


Yes. I am still learning, but I understand that Docker is definitely not virtualization. I don't intend to treat the containers like a full VM. My idea was to have a container for the minecraft server, a container for the webserver, a container for the media server, etc... It makes sense to leave no other tools within the container. My thought here is to learn a new tool like Docker. I have run VM's before, and know I could accomplish it that way. I have yet to find a real definitive reason to go one way or another... I guess the security aspect is one thought. An attacker with access to a VM would have a much more difficult time getting to the host OS than breaking out of a container. Is that true?


> **TheFu said:**
> Never mix an email server with any other sort of server. Ok, 'avoid' mixing an email server with others. Single physical machine or single-purpose VM, is up to you. dovecot and postfix are pretty light. 512MB of RAM should be overkill. I run an email gateway VM that blocks over 90% of all SMTP stuff inbound and forwards the remaining 10% to a Zimbra communications server (which is a HOG!). Keeping the gateway patched is easy. Keeping Zimbra patched is significantly harder. Zimbra isn't directly on the internet and never will be. Outbound email from zimbra goes through the gateway. Client access requires being at home on the correct LAN segment or use of the VPN. I didn't always do it this way, but then saw 100,000 daily login attempts coming from eastern Europe and thought through the problem. Requiring a VPN isn't really too much to ask.


I keep internet-facing websites in a single VM using nginx as a reverse-proxy. They can contact different back-ends as needed which are not available directly to the internet. Call it a web-gateway reverse proxy. A few non-internet-facing internal-only websites like wallabag and nextcloud and calibre also use this reverse proxy with micro-caching.


I currently have my email and webserver running on a single pi. The reason you suggest not mixing email servers with anything is because of the large attack surface? Is this related to having unknown users? This email server is only for myself and my family, no one I don't trust or know personally would be a user. I'm not familiar with email gateways or zimbra servers. I assume you are blocking 90% based on some spam or IP filtering and only 10% of connections are legitamite? Other than the scary amount of connections (100,000+) what is the issue here?


> **TheFu said:**
> Use different subnets with firewalling between each to mitigate risks for when you get hacked. You will be hacked. Expect it. Have a plan of action, mitigation, recovery. Hopefully, you'll never need it, but you probably well, eventually. If my blog gets hacked, I have a static version of the site read to go on a read-only NFS mount. Change the backend IP - done. Have a plan for when bad things happen.


If you don't allow direct internet access to most of your services, security becomes much easier. Use either wireguard or openvpn. There are clients for both VPNs on android, windows and Linux. I've used openvpn for a long time and it is easier for other end-users to understand. Been thinking about switching to wireguard, but it has some limitations which might not work for my needs. Being easy and fast are definitely great, but not if I'm in a hotel that blocks all UDP traffic. wireguard is UDP only.


...


Subnetting is the first line of security. I don't know how well any home router can do it. I've been using pfSense for a long time and assign different subnets to each port, then use dumb $15 switches to connect the systems to the correct subnet where they are needed. Please, don't use a flat network for a setup like you are planning.
* internet servers
* internal servers + safe desktops (all wired)
* Kids + wifi + media players + IoT (assumed unsafe)


I hadn't thought of using different subnets. I like the idea but as you mention I'm not sure it's possible to do with my Netgear Nighthawk X4. I will certianly look into it. As far as expecting to be hacked, well yes I guess given enough time it is inevitable. But so is the heat death of the universe. I'm not as worried about my personal sites being hacked, I am worried about sensitive - banking, etc... - info being compromised. My plan would essentially be to blow it all up and start over trying to learn what happened and get better so that it doesn't happen again. I'll have backups, etc... If my site is down for a week or a month, it's really not a big deal. 


I read somewhere that openVPN uses an extremely old linux kernel in openVZ, and has a massive list of security holes. Not sure how this applies here, or if it does at all. 


> **TheFu said:**
> ssh should be loaded on every system that isn't a docker container. Load fail2ban too. Block password logins over the internet. With ssh, you get sftp, rsync, scp, and about 50 other connection tools. ssh can be used to provide a SOCKS proxy from anywhere in the world to your home network. Poor man's VPN that sorta "just works", provided you understand the limitations (tcp-only). The lack of UDP support only matters if you aren't already using a DNS-proxy-over-https. The biggest limitation I have with ssh-socks is Android setups are a hassle, so I just use the VPN instead. On a full Linux laptop, the SOCK proxy is quick, secure-enough, and easy. Very comfortable to access any resources in the /etc/hosts file when anywhere in the world.


I have ssh installed and use it to manage the Pi's which are all headless. The first thing I do is disable any password login as well as remote root login. I only allow logins with my ssh key. I'm not familiar with fail2ban, but it sounds like I should be, I'll do some research. I have heard about ssh-SOCKS, but have never used it. I have been SSH'ing directly into my machines from outside of my network through my domain, which is kept updated with a DDNS service. Based on what you have been describing so far I'm guessing this is not a secure way of accomplishing this task? To be honest I don't do alot of remote work, but it is nice to have the ability if needed.


> **TheFu said:**
> Media server is a completely separate task. I don't have mine on the same hardware that serves the internet. Risk mitigation strategy. I can access the media over that ssh-socks connection using a web browser and it works. The rest of the family cannot. It doesn't work on the VPN subnet I drop them onto either. They'd never come home if I did that.   Of course, the subnet I get dropped onto over the VPN does have access to the media and can hop into other subnets here. The easiest answer for a home media server is to use something with DLNA. If you need transcoding of the stream for weaker playback devices, then plex media server is the easy option. I hate the plex clients, so use the DLNA part with bookmarks to skip over the multiple extra layers that DLNA insists we have. Try out miniDLNA first. Perhaps it will do what you need? There are lots of DNLA renderers, controllers, so that isn't really an issue. VLC is one.


I was thinking of running plex in a docker container. My TV has a plugin, phones, etc... all have the plugins. That seemed to be the easiest option. I'm not familiar with DLNA, a quick google search later.. it seems as if it is a protocol for communicating with media devices, and is supported by Plex. Ideally my media would be available on any device, from anywhere. I'll look into miniDNLA.


> **TheFu said:**
> What are the plans for access controls, SSO-logins, DHCP, DNS on the LAN? 


Do you have any U2F or FIDO2 keys that need support?


And never forget, just because something might be possible, it is up to you to decide if it is actually a good idea.


Not planning on any SSO login or U2F keys at this time. I was assuming all access would be via keys, but now that I think about it that might be cumbersome. Access control would only be necessary if accessing from the outside, right? I do hope to have DHCP functional, what other considerations should be made here? Perhaps limiting it to a specific range? For DNS I have two domains that are setup with a DDNS updater. If I go the subnet route would it make sense to run something like BIND9 locally so I dont have to use the IPs all the time?


I do agree with your last statement. I'm trying to strike a balance here. I really appreciate your insights, this was a lot to unpack and has given me direction to go and research a few things.

---

### Post by Tadaen_Sylvermane on 2019-12-19
You may not need a full blown VM solution btw. I do quite well for separating services with LXD containers. They aren't near as secure as a separate vm but for my purposes at home they are wonderful things. If I need to bring my main server down I can send them across the network with minimal downtime to another machine. Basically LXC on steroids.

I know that lxd is a capable enterprise level container. i however am not open to the internet so my risk is minimal. i use them for convenience mainly, and they serve that purpose splendidly.

---

