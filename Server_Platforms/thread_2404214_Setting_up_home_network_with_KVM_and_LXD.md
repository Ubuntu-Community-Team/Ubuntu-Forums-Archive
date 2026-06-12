---
title: "Setting up home network with KVM and LXD"
date: 2018-10-21
forum: Server Platforms
---

### Post by mdfrg on 2018-10-21
Hello,

I'm looking for guidance in setting my home server. I have a HP Proliant Gen 8 Microserver G1610T box upgraded with 12GB RAM.
I was using it and plan to continue using it with some critical applications AND as a homelab to test an play with new OSes, technologies and solutions.

```
TL;DR
If this post is too long for you, just please look on the diagram and the questions below it.
```

# Background

In short, my plan is to isolate my production environment from testing ground, so I won't mess up with services that should be up and running most of the time. Also, I am occasionally away from the physical box so if I screw up network configuration (which I've done...) or my host won't boot up I'm f.u.b.a.r.. For that reason, I decided to have one VM for all critical applications and others for testing, according to my needs. 

# What I want

1. Separate testing environments from services I don't want to break
2. Have remote access to administer machine, install / reinstall OSes
3. Use snapshots to have point in time backups that I can revert to if something goes wrong


# My plan

To achieve further fail-proof isolation and preserve from config contamination, I want to put those critical application in containers, preferably LXD ones because I then can provision them with ansible without much tweaking (the same way I'd done without any layer of vm / container).
Because my server is in my home behind my home router in order to access it from the internet I have to forward ports to it, so I my solution is as follows

1. Port 80 and 443 for web applications are pointed to a container with nginx serving as reverse proxy (pointing cloud.mydomain.com to container 2, git.mydomain.com to container 3 etc.).
2. All other applications are separated in LXD containers according to their purpose
3. Other services (like XMPP) are forwarded (by router directly to specific container
4. Bare-metal host OS is Ubuntu 18.04 installed on LVM to achieve easy rollback and backup with snapshots. Livepatch and unattended upgrades are setup. Host OS have minimal set of applications installed and all ports except SSH opened. For visualization KVM is used.
5. On VM PROD another Ubuntu 18.04 is installed with latest snap LXD and several per-service containers.
6. Both HOST and VM prod have bridge setup so every new VM and container can have its own IP on my LAN so further configuration will be easier.
7. Each single machine (VM and container) is provisioned by Ansible with separate playbooks. 
8. For snapshots and backups ZFS is used for containers and LVM for VM PROD and HOST
9. Storage consists of 1 SSD for HOST OS with setup and 4x3TB WD RED drives. I have not decided how to set them. 


Below I attach a diagram of what I plan to setup and would like to ear some feedback about it - what are possible pitfalls and drawbacks and what should I do differently. 

[IMG]https://i.imgur.com/KHCvKZc.png[/IMG]

```

```

                                                   .-----------------.
                                                   |      HOST       |
                                                   | (on bare metal) |
                                                   |   __________    |
                                                   |  [_|||||||_°]   |
                                                   |  [_|||||||_°]   |
            .------------------------------------->|  [_|||||||_°]   |-----------------------------------------------------.
            |                                      |-----------------|                                                     |
            |                                      | Ubuntu 18.04    |                                                     |
            |                                      | on LVM          |                                                     |
            |                                      | +br0 bridge     |                                                     |
 .---------------------.                           '-----------------'                                                     v
 |       VM PROD       |                                                                                      .------------------------.
 | production services |                                                                                      |       other VMs        |
 |---------------------|                                                                                      |------------------------|
 | Ubuntu 18.04 on LVM |<----------------------------------------------------------------------------------.  | for testing            |
 | with LXD containers |   |                          |                          |                         |  | and learning purposes  |
 | on ZFS              |   |                          |                          |                         |  | (CentOS, pfsense etc)  |
 | +br0 bridge         |   |                          |                          |                         |  '------------------------'
 '---------------------'   |                          |                          |                         |
            ^              |                          |                          |                         |
            |              |                          |                          |                         |
            |              |                          |                          |                         |
            |  .----------------------. .--------------------------. .-----------------------. .-----------------.
            |  |   LXC container 2    | |     LXC container 3      | |    LXC container 4    | | LXC container 5 |
            |  |----------------------| |--------------------------| |-----------------------| |-----------------|
            |  | nextcloud            | | web applications:        | | XMPP server (prosody) | | SAMBA           |
            |  | (cloud.mydomain.com) | | gitea, wallabag etc      | | (xmpp.mydomain.com)   | | (LAN only)      |
            |  '----------------------' | (git.mydomain.com, etc.) | '-----------------------' '-----------------'
            |              ^            '--------------------------'             ^                      ^
            |              *                                 ^                   *                      |
 .---------------------.   *                                 *                   *                      |      Home PC, 
 |   LXC container 1   |   *                                 *                   *                     L|     laptop etc
 |---------------------|**********************************************************                     A|----- __  _    
 | nginx reverse proxy |                                                                               N|     [__]|=|   
 '---------------------'                                                                                |     /::/|_|   
            ^                                                                                           |
            *                                                                                           |               .-,(  ),-.    
            *                                            access from INTERNET                     Home router        .-(          )-. 
            ************************************************************************************** __________ <*****(    internet    )
                                                                                                  [_...__...°]       '-(          ).-'
                                                                                                                         '-.( ).-'    

```

```


# QUESTIONS

1. How to orchestrate / **administer** it? Since every container / VM is a full separate OS, how do I batch upgrade them? With Ansible?
2. HP Proliant has two NICs - how can I isolate home LAN (samba) with internet?
3. Should I put samba on HOST rather than in LXD for performance reasons?
4. How do I manage **storage**? To expose folders/ disk to containers I have to share it with VM PROD and then with LXD - is there a big penalty in I/O for it? Can I go with ZFS (since HOST is Ubuntu 18.04 which supports it without DKMS)
5. Is there a big performance fall in setting ZFS storage for LXD containers on LVM?

Any additional comments and shared experience would be much appreciated.

---

### Post by TheFu on 2018-10-25
That's a bunch of data.
I can't speak about ZFS. Never used it on Linux.

Most of it is reasonable, but I'd keep test stuff physically separate.  Separate network, separate hardware, separate router.
I'd keep wifi on a "guest" network.  I don't trust wifi networks without using a VPN, even in my own home.

Where's the backup server to hold the versioned backups? You need 60 days of versioned backups and it needs to be on a protected subnet.  Snapshots are not backups.

Sharing a bridge across VMs/Containers means each of those can gain access to the other systems network traffic.  
I think you need more physical networks.

I wouldn't use samba.  Use NFS and don't let that be on a network connected to the internet.

Perhaps you need a VPN server?  I'd never run that on a router. Many people do, but I want VPN software to be constantly maintained and patched.  Most services are only available from the VPN or LAN subnet, not the internet.  Where I've worked, we don't allow php web-apps to be accessed over the internet. A VPN is required. 

And 1 last thing, I don't think 18.04 is ready to trust for production yet and I have concerns about trusting containers for internet-facing services on a network I care about.  Any internet-facing services need to be on a different subnet that is firewalled away from  my "secure" systems on the LAN.

Paranoia is necessary BEFORE you get hacked.  And you should expect to be hacked.

There used to be a website that would accept network designs, then have the other users rate them.  It died and the waybackmachine doesn't deal with dynamic sites like that one at all, so all those diagrams are lost.
[https://www.reddit.com/r/RMND/](https://www.reddit.com/r/RMND/) is the closest I found today.

---

### Post by Dragonbite on 2018-10-26
Handy thing with LXD/LXC is if you SSH into the host, you don't have to SSH or anything to log into the individual container for administering it.

I would not want LXC Container 5, which is internally accessed, thrown in the VM with the externally-accessed web server containers.  Maybe separate VMs for [1] internal-prod, [2] external-prod and [3] testing.  So would be like

[LIST]
[*]host
[LIST]
[*]vm-prod-external
[LIST]
[*]LXC container 1
[*]LXC container 2
[*]LXC container 3
[*]LXC container 4
[/LIST]
[*]vm-prod-internal
[LIST]
[*]LXC container 5
[/LIST]
[*]vm-test
[/LIST]
[/LIST]

Otherwise this looks like an interesting project.  I hope you update on how it goes and what you learn.  I may benefit from your experience when setting up and improving my own network.

---

### Post by TheFu on 2018-10-26
Saw this: [https://www.theregister.co.uk/2018/10/26/infosec_holodeck_network/](https://www.theregister.co.uk/2018/10/26/infosec_holodeck_network/) Seemed related to setting up a lab to mimic enterprise stuff.

---

