---
title: "Server install - using VMs or go native"
date: 2014-07-21
forum: Server Platforms
---

### Post by npinn001 on 2014-07-21
So I've been using Debian on my sever for a while now, and I've got a KVM setup working where I have 2 or 3 virtual machines for different uses. So far, its been ok, however, I'm about to move over to a clean install and will be putting Ubuntu server LTS on there for the 5 years support.

My basic requirements are as follows:

Serve media files around the house - plex media server will do this for me.
Shared folders on the network - Samba and NFS will do nicely.
Downloads - Torrent files, Isos for testing etc.
Remote access via SSH outside the network.
Backups of my PC (windows 8). - ?
Experiment with hosting a website - I'd like to create an index of all my files on a site so that my parents can remotely log on to the website and download bits.

So, I'm pondering 2 setup types:

1) Install Ubuntu, and install all the other services on here natively.

2) Install Ubuntu, and then install KVM (or other) and install something like freenas or openfiler on top in a VM. This would then handle the storage, the Samba and NFS shares and backups. Add another VM for the website.

What do you guys think? Is the VM route 'overcomplicating' things, or is it making the setup more secure in the long term, ie, no clean installs?

Thanks

---

### Post by TheFu on 2014-07-21
Every externally-facing service should be in a different VM for security.

Your parents should use sftp to connect - don't use passwords, only key-based authentication and security the service following the normal ssh-security-best-practices.

Can't help with Windows backups. I do an image (boot off partimage monthly) and daily data-only backups from a Linux machine that can access the data partition on Windows (CIFS mount). I know - I'm weird.

I have a dedicated, low-end Atom-class, XMBC+Plex server. It is also an NFS server for the house and GigE connected to the network. It cannot transcode any videos in real-time for other devices, but other systems on the network can through the NFS connection. My setup is ideal in many way and less-than good in others. ;)

So ... yes, go with KVM and be happy.  No question to at all.  Also, use virt-manager to manage it easily. It is very similar to vbox, VMware Player VM management, but it can work securely over  ssh from anywhere in the world, provided ssh-keys are used.

---

### Post by npinn001 on 2014-07-21
Thankyou. That really helps, appreciate the advice.

Hadnt considered sftp but I will now!

Thanks again

---

### Post by TheFu on 2014-07-21
Great Windows - sftp tool is winscp.

For a secure, remote desktop, check out x2go. It goes over ssh and uses keys, plus it is 2-3x more efficient than vnc and rdp tools which don't include a secure tunnel.

I should point out I am considering moving the media and plex server to a faster machine, inside a VM. The other machines here that would be good as a plex server just don't have an internal drive bay available.  About 8 months ago, pre-plex, I did use CIFS connections to the XBMC machine for playback and recall being frustrated during weekly system maintenance while watching some content, having the access dropped because I'd forgotten the remote machine was part of that content delivery and rebooted it. ;(  Not THAT big of a deal, but still a consideration.  Being able to transcode video for all the devices here would be a plus. Your situation may not require transcoding at all.

---

### Post by npinn001 on 2014-07-21
Yeah i do need to transcode so thats a good point.

Ha ha, the rebooting issue would be frustrating in the middle of a film say!

Sounds like you have some fun coming up re-jigging the plex server!

---

### Post by gordintoronto on 2014-07-21
How much memory does the machine have? Bear in mind that FreeNAS, all by itself, is a dreadful memory hog. There's nothing wrong with Ubuntu Server's file server capability.

---

### Post by bulrush2 on 2014-07-26
I have Win 7 and plan on using VirtualBox to use Ubuntu Server (probably 13.10) as a VM so I can learn linux admin skills.

---

### Post by TheFu on 2014-07-26
> **bulrush2 said:**
> I have Win 7 and plan on using VirtualBox to use Ubuntu Server (probably 13.10) as a VM so I can learn linux admin skills.

13.10 is a bad idea - support ended for that a few weeks ago.  14.04 or 12.04 are the only choices for a "server."  For a desktop, 14.04 is it.

---

### Post by bulrush2 on 2014-07-28
Why did they end support for 13.10 but not 12.04? 12.04 would be older. And 13.10 should have bug fixes for 13.04 IIRC. And 14.04 would be too new to have much support or have most of the bugs worked out. **I'm most concerned with getting a stable version with the bugs worked out. **

Aren't the first release of a major version ".04"? I can't find the link where I read that right now.

---

### Post by TheFu on 2014-07-28
> **bulrush2 said:**
> Why did they end support for 13.10 but not 12.04? 12.04 would be older. And 13.10 should have bug fixes for 13.04 IIRC. And 14.04 would be too new to have much support or have most of the bugs worked out. **I'm most concerned with getting a stable version with the bugs worked out. **

Aren't the first release of a major version ".04"? I can't find the link where I read that right now.

LTS - Long Term Support - releases happen every other year in April.  8.04, 10.04, 12.04, 14.04 are all LTS releases. With 12.04 and later, 5 years of support.

[Why most Ubuntu users should only run LTS Releases.]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release")  Basically - only core library devs should run non-LTS releases, IMHO. Newer is NOT usually better.

All other releases get 6-13 months of support only.  The [official dates]("https://wiki.ubuntu.com/Releases") for support.

---

### Post by elico on 2014-07-28
I would recommend you to use another solution rathern then KVM unless needed.
Some do prefer virtual machines but it's not always a good practice.
It will might help you on live migration but you would probably will not use it.

Indeed you will need to use some sort of raid-1 as a basic redundency for your system.

---

