---
title: "Installing Ubuntu Server on a laptop, compared to NAS, and a bunch of other questions"
date: 2013-06-07
forum: Server Platforms
---

### Post by Cubytus on 2013-06-07
Hello there, 

after much discussions on different forums and personal experience with general unreliability of cloud-bases services, I came to the conclusion that it could be actually a good idea to have my own server at home to fullfill some **tasks** that need to be run in the background, namely:

[LIST]
[*]SFTP server, accessible from the LAN and Internet. Would be used to backup local copies of SpiderOak blocks to improve recovery time if one machine dies down
[*]AFP server for Time Machine backups
[*]the usual torrents seeded
[*]Videosurveillance: motion detection, H264 recording, storage, remote storage of recordings, based on ZoneMinder, if this damn suite can, at last, start working.
[*]BitCoin and Freenet nodes.
[*]1Gbps wired connection, for decent file transfers.
[/LIST]

I can't think of any other interesting use at the moment, considering the upload bandwidth available is a major limiting factor, and absolute priority must be given to surveillance recordings, although in H264 and given aggressive cutting clips can be quite small. Mail server is excluded (side for the strictest necessary for ZoneMinder to send alerts) as I already rent that on a shared hosting in a datacenter, and most mails coming from homebrew servers have an increased chance of getting rejected at the receiving end, especially with a dynamic IP. Otherwise, this would be the first time I ever set up a significant home server and dedicate a perfectly working laptop to any task that would imply non-mobility, no GUI, effectively sacrificing a machine I sometime use for mobile work where the Mac Book Pro may not suffice.

The **machine** would be a LG R510 laptop, as I have it already and it sucks relatively few juice, is reasonably quiet though not silent by any way, has a battery in case of accidental or malicious power-down, external USB HDDs, both in 3.5" (problematic) and 2.5" (OK) form (2x500 GB, 2x250 GB). Power is 2GHz Core2Duo and has 4GB of RAM. A 250GB sits inside, and would be used to run the system and applications, storage would be external. I am not sure that I would be able to convert the local Time Machine backup in a networked one as Ubuntu, to my knowledge, doesn't have any HFS+ driver. It would be the best if this 1.5TB drive would be usable both on the server and locally. This far, this machine has been used as my only Windows machine for applications that run only on that OS, and a physical Ubuntu Desktop machine for those few use that can not run properly in virtual machines (OsmocommBB and Nokia maintenance applications), both of them currently irreplaced. 

I could repurpose the other MacBook for the same purpose, but it is a bit less powerful (white, pre-unibody).

The **software** would be Ubuntu Server. Although there may be other servers out there, I have experienced that ZoneMinder being so difficult to run that it may not be the right time trying to run it on "exotic" software, but rather rely on a distro with an extensive base of users.

The goal is to spend the least amount of money possible, including in maintenance (electricity).

**First**, would there be another interesting, background use I haven't thought about, and compatible with sub-Mbps upload speed?

I understand this may not be the most optimal setup to have, but after having a look at, say, Synology's line of beautiful and silent NAS, I could see that price range was not at all in line with what I would be able to shell out.

**Second**, I think ZM gave weird bugs when running from an encrypted disk, I think because the symbolic link permissions were not exactly the same as the folders they pointed to. Totally transparent to the OS and other applications, though. Have there been any progress regarding whole-disk encryption? I don't want anybody to be able to read the content of the disk if server is stolen. If not, I fear that it may add yet another layer of complexity if I were to virtualize an unencrypted Ubuntu inside, if the machine ever has enough power for that.

**Third**, would the intended machine be strong enough to handle it all, considering that, out of noise concerns, it may well end up in a pantry? Would it stay cool enough, considering this has to be considered a very dusty environment? More important, this machine is currently not able to gracefully wake up from sleep with Ubuntu 12.04 Desktop. Would it be able to do so with only minimal configuration on a server OS? If the current gets cut, I want it to gracefully disconnect clients and go to sleep, and gracefully recover from it. Adding to the complexity is that the machine is likely to run screen closed.

**Fourth**, how would I replace the current physical machines I need, considering a test of Ubuntu desktop on the MacBook yielded very mixed results, sluggishness and very poor trackpad response?

¡Uf!, this was a long post, and the only things I can think of at the moment. Feel free to ask questions, I will try to keep this post updated from your insights.

---

