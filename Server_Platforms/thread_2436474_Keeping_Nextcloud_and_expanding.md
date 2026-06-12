---
title: "Keeping Nextcloud and expanding"
date: 2020-02-07
forum: Server Platforms
---

### Post by masteralienhead on 2020-02-07
I am using server 18.04. Currently I use it as a backup for about 10 computers + phones as well as a club access cloud for distributing important information to club members (they access via DDNS.net). I want to add the ability to host websites and video chat/conferencing. 
Currently the install is on a HP Proliant Micro server with 16TB and 32gb mem.
My question is can I add the needed ability of website and chat/video conferencing without disturbing the access to the Nextcloud and its content? If so can some one direct me to a guide to read up on this process or list the process.

Thanks!

---

### Post by wildmanne39 on 2020-02-07
Hello and welcome to the forum.

*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by masteralienhead on 2020-02-07
Thanks and Thanks for the move to the appropriate place. It may help with getting the appropriate answer. :D

---

### Post by LHammonds on 2020-02-07
You might want to consider turning it into a virtual server and host multiple, separate virtual machines.  Creating an all-in-one solution AND connecting it to the Internet is asking for trouble....not from your club members so much as being exposed to the automated cyber warfare.

Isolating internet-facing systems is a good idea and be sure to design it such that if/when the machine is compromised, that they have a hard time compromising any other systems.  Meaning, separate the servers and use different accounts/passwords.

You can use vmware ESXi installed onto the server or you can use Ubuntu with KVM for the host OS.

Also, doesn't NextCloud have video chat capabilities?

[Jitsi Meet](https://www.howtoforge.com/tutorial/how-to-create-your-own-video-conference-using-jitsi-meet-on-ubuntu-1804/)
[Signal](https://www.ubuntupit.com/signal-fast-secure-and-encrypted-messaging-app-for-linux/)
[Apache OpenMeetings](https://www.howtoforge.com/tutorial/how-to-install-openmeetings-on-ubuntu/)

LHammonds

---

### Post by TheFu on 2020-02-07
+1 for using virtualization.  I use KVM/QEMU.  Previously used Xen, Virtualbox and ESX/i.  We used to support ESX deployments for clients, but switched to KVM and 10 yrs later don't have **any** regrets.  KVM is faster and not as picky about hardware as VMware ESXi.

Nextcloud has videochat - called "Talk".  The setup is a little more than 1-click, but not too bad. It was pretty simple.  My family hops onto it with 4 clients whenever I'm travelling.  

I consider nextcloud to be a huge target, so only allow access to it over a VPN. Using a VPN from android is easy, before opening any nextcloud client apps.  I've deployed about 15 addons to our nextcloud environment. Most are fine, only the photo gallery options kinda suck.  The hostOS has only a G3258 CPU with 8G total RAM. The nextcloud VM gets 1GB vRAM and 1 vCPU.  

If I needed to provide nextcloud for a club, I would put it on a VPS alone somewhere like vultr. No way would I have it on a subnet with anything else important.

I host websites in different VMs to mitigate risks.  Nextcloud is complex enough that I don't want to mix those settings with anything else.  I also have daily, automatic, versioned, "pulled", backups.  I keep the backup server behind a router without any open ports.  None of the backup clients can directly access the backup server. That's for risk mitigation too.

---

### Post by masteralienhead on 2020-02-08
Thanks for info. I found the video and chat add on. So what I am hearing is that if I want to be safe. I need to wipe and restart the process. Start with an install of Ubuntu with VM. Create however many virtual machines and have the club access one of them via the ddns and i do backups via another. And have my website hosting on a third?

---

### Post by TheFu on 2020-02-08
> **masteralienhead said:**
> Thanks for info. I found the video and chat add on. So what I am hearing is that if I want to be safe. I need to wipe and restart the process. Start with an install of Ubuntu with VM. Create however many virtual machines and have the club access one of them via the ddns and i do backups via another. And have my website hosting on a third?

Seem oversimplified compared to what was written.  

Each of 200 risks has a mitigation strategy.  Hackers use automatic tools to find 1 issue in 5000 on our systems, then exploit that issue as much as possible.  Just because something works, that doesn't mean it is secure.  When running any internet-facing service, best to be paranoid, expect to be hacked, and have plans for what we'll do when that happens.  The internet isn't like it was in 2002 anymore.

---

### Post by masteralienhead on 2020-02-09
Oversimplified, yes. Nothing is solid. I am hoping for path of least resistance to achieve my end goal. My history goes way back beyond the 2000's. I was a Mitnick contemporary back in the day. I am not saying I am that "cool" Just saying I am that old and have a grasp on THAT process of discovery. I moved away from the DOS process to the more lazy Apple and windows GUI process. I am now getting back into the terminal world with this server and a laptop running Ubuntu. Anyways the first VM is up and running. 

So I will run Nextcloud from a VM.  I still plan on the DDNS because the club won't pay for a VPN. I know because I am the president and steady income is not part of a "not for profit" business model. Is there a program to help mitigate attacks on the VM?

---

### Post by TheFu on 2020-02-09
> **masteralienhead said:**
> Oversimplified, yes. Nothing is solid. I am hoping for path of least resistance to achieve my end goal. My history goes way back beyond the 2000's. I was a Mitnick contemporary back in the day. I am not saying I am that "cool" Just saying I am that old and have a grasp on THAT process of discovery. I moved away from the DOS process to the more lazy Apple and windows GUI process. I am now getting back into the terminal world with this server and a laptop running Ubuntu. Anyways the first VM is up and running. 

So I will run Nextcloud from a VM.  I still plan on the DDNS because the club won't pay for a VPN. I know because I am the president and steady income is not part of a "not for profit" business model. Is there a program to help mitigate attacks on the VM?

A paid VPN won't help. Run your own VPN server. That is free. Either IPSec or OpenVPN are common, but there are others these days. How many members of the club?  Is this server running from a home network?  Why DDNS?  With DDNS, sending emails to the club members will be next to impossible.  Using a VPN is the only way I know to reduce attacks.  The other methods I use are having all traffic go through a reverse-proxy which selectively allows specific traffic from specific subnets. If the club is just family, generating 50 VPN client-keys wouldn't be too hard, but if the club is 2000 members (like my LUG has), it would be better to just put nextcloud onto a VPS for $5/month.

---

