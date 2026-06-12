---
title: "Setting up a home server????"
date: 2010-09-12
forum: Server Platforms
---

### Post by purvis on 2010-09-12
I had looked into and even began installing Ubuntu Server on a machine currently running W7-64. As the installation process proceeded it appeared it would not automatically set up dual boot on the machine, something I would like to have. As I began to search the web and this forum it looks like I may be better off installing a standard version of Ubuntu and add the necessary server add ins. Here is what I am wanting to accomplish:
-provide a central location for all computers to store and retrieve files
-provide a central location for all computers to back up configurations
-provide a central location for software installations
-compatibility across multiple platforms, Windows 7 64bit, Windows Vista 32 bit, Ubuntu 32 & 64 bit, Windows CE (U-Verse TV set top boxes), Wii, PS3
-ability for all systems to recognize media folders on server

My questions are:
-Can I do what I want using a standard version of Ubuntu?
-Would I be better off using Ubuntu Server?
-Should I use a 32 or 64 bit version?
-If I am using Ubuntu Server can I and how do I dual boot the machine?

---

### Post by CharlesA on 2010-09-12
You can use PS3mediaserver to stream stuff to the ps3. It'll do transcoding on the fly too.

To share files with Windows, you need to use samba.

64-bit Ubuntu would work fine for what you want. I serve files to a mix of Windows machines (XP, Vista, 7) using Ubuntu Server 10.04.1 x64 without any problems. :)

Normally you'd want this on a dedicated machine, since if you are dual booting with Windows, how is it going to serve files when you are booted to Windows? Unless you want to have the machine on all the time and run the server in a VM, that's not possible.

---

### Post by 1serveyou on 2010-09-12
Will you be streaming HD(1080p or 720p) content to your PS3? I have a Dual G5 Mac(looks like mac pro, but is a powerpc), 2.0gh and 7gb of ram, and I couldn't stream 1080p content, but 720p was fine. 

Also how much time do you have to learn, as with the server interface it's all command line.

But, yes, ubuntu can do all that you have mentioned.

---

### Post by arrrghhh on 2010-09-13
1080p streaming you'd need a better processor... Quad-core is a minimum.  RAM doesn't really have much factor in transcoding on-the-fly.

To the OP, CharlesA is right about the dual-boot thing... you wouldn't want to shut down your server to run Win7 would you...?  Then you'd lose all the services that are running on your Ubuntu Server, preventing clients from sharing files, stream to your PS3, etc.

---

### Post by CharlesA on 2010-09-13
Even if you do run it in a VM, you'd bog the crap out of your main OS if you are doing transcoding.

Having a dedicated machine is better imho.

---

### Post by perspectoff on 2010-09-13
> **purvis said:**
> I had looked into and even began installing Ubuntu Server on a machine currently running W7-64. As the installation process proceeded it appeared it would not automatically set up dual boot on the machine, something I would like to have. As I began to search the web and this forum it looks like I may be better off installing a standard version of Ubuntu and add the necessary server add ins. Here is what I am wanting to accomplish:
-provide a central location for all computers to store and retrieve files
-provide a central location for all computers to back up configurations
-provide a central location for software installations
-compatibility across multiple platforms, Windows 7 64bit, Windows Vista 32 bit, Ubuntu 32 & 64 bit, Windows CE (U-Verse TV set top boxes), Wii, PS3
-ability for all systems to recognize media folders on server

My questions are:
-Can I do what I want using a standard version of Ubuntu?
-Would I be better off using Ubuntu Server?
-Should I use a 32 or 64 bit version?
-If I am using Ubuntu Server can I and how do I dual boot the machine?

Been there, done that. All you want / need is a network-compatible NAS hard drive (i.e. a hard drive with built-in server). Much less hassle and in the long run less expensive than what you are proposing.

A RAID drive is nice if you have the money and need reliability, but two hard drives is usually enough for most people (a primary one and one for backups, mainly). 

For example, I have used an inexpensive Buffalo 500 Gb LinkStation on my home LAN that any computer on the network can access (nowadays 1 Tb and 2 Tb drives are available for about the same price). I store recorded movies there, OS files, and just about everything there. I stream from that drive to any computers that are hooked up to my HDTVs, etc. It doesn't matter if those computers are running Windows or Linux.

I then have a similar-size hard drive that the NAS backs up to, for safety (it isn't actually a NAS hard drive, so it is dirt cheap).

I have been doing this for years and it is the most versatile and easiest solution for home. Having done all the other things you are looking at, I wouldn't bother with anything else. You'll spend too much time and money for little gain.

I think the Buffalo used Windows 2003 as its server platform. Newer NAS hard drives use Linux servers and are faster and more secure, and Synology has made an excellent one for years (but is slightly pricey). Netgear NAS drives have been excellent, but also expensive. Shop around and read reviews for NAS drives and then select one.

---

### Post by junke1990 on 2010-09-13
if you want to make it fun you can install ubuntu server and equip it with ushare which supports upnp DLNA service for ps3, xbox (and wii?) and equip it with samba for the windows computers to share info.

If you would like to make it really fun you could install lighttpd (or apache) and put torrentflux on it, a web based torrent client.

And ssh if you want easier remote access.

That's basicly my home server setup.

---

### Post by spynappels on 2010-09-14
Have a look at QNAP NAS boxes too, from memory they have all the services you need. I run one of these and an ESXi host with an assortment of VMs and that does everything I need it to.

---

