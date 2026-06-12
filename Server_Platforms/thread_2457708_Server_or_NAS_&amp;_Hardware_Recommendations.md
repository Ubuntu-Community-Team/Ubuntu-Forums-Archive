---
title: "Server or NAS &amp; Hardware Recommendations"
date: 2021-02-07
forum: Server Platforms
---

### Post by rucker222 on 2021-02-07
Hi guys,

I'm chasing advise and suggestions on which way I should go, Server or NAS? 

Other than the obvious reason for wanting either of these at home (storing my own data etc.) I want to remove myself and my families data from Google and other big tech oligarchs.

The main things I want to achieve are below:
- Backup/sync other laptops and phones etc.
- Host my own emails 
- Network storage
- Media streaming
- Have all external traffic encrypted through a VPN 
- I have young kids whose internet usage I want to manage and monitor until they're old enough to protect themselves from online danger.

I feel myself leaning towards server for flexibility but assume a NAS would be a far simpler option and maybe do everything anyway... 

I don't know much about what options are out there and assume I'd be restricted with a NAS to only have access to tools and capabilities the chosen brand of NAS had available.

Then there is the hardware, I don't have a big budget and not sure what's better value for money, micro server or NAS, or is a NAS running server software possible and worthwhile... and which makes and models should I be looking at...

I understand this is very subjective but looking for Ideas and suggestions.

Cheers.

---

### Post by TheFu on 2021-02-07
A NAS capable of 4k video transcoding will cost $600+, so why not just build/get a "server" that can to both?  Avoid custom setups like a micro-server too. Use a microATX or ITX motherboard if you care about size, just beware that those sometimes have limited support for SATA connections.

My NAS is a $126 ($50 CPU+$50 motherboard + $26 8G of RAM) setup with 10 HDDs connected.  6 via SATA and 4 via eSATA-pm. The external array was $100 and each 4TB disk was about $130, though I did get a used 4TB enterprise "Gold" SATA HDD for $42 last summer to replace a dead Hitachi HDD.  Avoid USB storage for the primary storage (1st, active copy). USB is fine for a 2nd copy/backups.

Media streaming requirements change. What are the current and future playback devices? Will the NAS need to transcode 4k AV1 videos to 720p h.264 for some devices?  Transcoding requires a beefy CPU almost always - 3000 passmarks for each concurrent stream.  My $50 Pentium G3258 can't transcode 4K in realtime, but it does handle 1080p --> 720p transcoding fine.

Hosting your own email server isn't about the CPU, but you'll want a virtual machine for added security. This assumes you can even get SMTP sent to your location.  Most residential ISPs will block inbound SMTP and few will allow direct outbound SMTP.  SMTP is the protocol used by all email-server-to-email-server communications.  But you can get a business connection, if you like. Be certain to get a static IP.  Any DHCP internet addresses are blocked from in/out SMTP too.  I've been running company email servers since the mid-1990s and host my own since the late 1990s. It used to be easier until around 2005, when spam exploded and all reputable ISPs took massive steps to prevent spam originating from their networks.

VPN - that's easy enough. I use a separate VM for it, due to security considerations. The bandwidth available will be very dependent on the CPU performance. I'm not sure I understand what you mean by 'Have all external traffic encrypted through a VPN ' ... this would block running SMTP and external access to your LAN.  I suspect you want to access your LAN using a VPN, but still allow other services to be accessed without the VPN? That would make more sense.  You can't force all external traffic through a VPN if you also run services on the internet (unless those services are specifically designed for it, say like a .onion service).

For about $300, you should be able to build a very capable Ryzen or Core i5 system using some parts you already have - case, PSU, HDDs. Just need new CPU, RAM, Motherboard and a CPU cooler. Unfortunately, the availability for many computer parts is limited now, so CPUs aren't as cheap as they were last Sept. Damn bitcoin.

So - get more specific on exactly what you seek to get better answers:
How much NAS storage will you want in the next 5 yrs? What sort of disks? What is your backup plan?
Nail down the email server stuff. Almost always, hosting your own email isn't worth your time. You can get a $60/yr VPS and do it there much easier than at home.
Media streaming - local only or do you need to share with friends/family?  Do you care about privacy or not?  What video and audo codecs will be needed and which resolutions?  How many concurrent streams at what resolutions?
VPN - are you running a server or just a client?  Can the client be limited to only desktops?  Servers cannot be VPN clients and require all inbound connections go through the VPN for general internet connectivity. 
Protecting kids ... if they are under 10, use a whitelist DNS.  As they age, you'll want content blocking using keyword filters. These won't be perfect. You'll probably want a way do control times of day for internet access by their devices. That means having a non-consumer router.  So - you'll need an enterprise router and a transparent proxy and a DNS that cannot be bypassed. If the kids are under 10 yrs old, bypassing the DNS isn't probably a concern yet, but 10 yr old kids know how to change their network settings. Basically, you'll need to force their devices onto a network that doesn't work unless your proxy server is used. As they get older, you'll want to relax the content filters until they move out.  By then you'll likely just want the content filters for yourself to speed up the general internet by ad-blocking for the entire network.  Proxy and DNS servers can behave differently based on the client, BTW. The filters for you and the filters for them don't need to be the same.

Each of these things really should be a separate question, since very few people will have the expertise to help with too many of your questions.

---

### Post by scorp123 on 2021-02-08
> **rucker222 said:**
>  Server or NAS? 

I'm a happy owner of both. Both have advantages and disadvantages.

A NAS such as one from Qnap or Synology comes with tons of stuff and they are easy to use. But maybe "too easy"? It's easy to shoot yourself in the foot by accidentally activating some "Cloud sharing" (or similar) feature that will open up your private files to the whole Internet. So you'd still need to read exactly what each feature does... wildly clicking on those beautiful icons without knowing what exactly those icons will do is absolutely not advisable.

A server has the advantage that it offers you total flexibility. It will run what you tell it to run, be that any Linux distribution, Windows, FreeBSD, VMware, Unraid, or whatever other OS you choose to run. But you will have to do everything yourself. You want some kind of hardware monitoring and automatic reporting regarding the status of your disks? While NAS already ship with such things "out of the box" (it's just a matter of clicking on the right icon) on a server you will most likely need to install + configure this yourself. But then again this also offers many opportunities to learn new things. And on a new server with nothing on it there won't be any unwanted bloatware of any kind unless you yourself put it there. No hidden "cloud sharing" service with scary security implications unless you yourself put it there.

> **rucker222 said:**
> assume I'd be restricted with a NAS to only have access to tools and capabilities the chosen brand of NAS had available.

Yes and no. Both Synology and Qnap have an official "App Store" where tons of more apps for their NAS can be installed from. Sure, you'd still have greater flexibility on a server that runs whatever OS you want it to run. And yes, there's always the risk that these NAS vendors might one day decide *"Sorry but we no longer offer App xyz for download on your type of NAS"* ... but even if that were to happen, there are also 3rd party "App Stores" that offer more stuff. Me as a user of a Qnap NAS I could always go e.g. to a website such as [https://www.qnapclub.eu/en]("https://www.qnapclub.eu/en") and install community-supplied apps from there if I wanted or needed to. Also, the better NAS let you run Docker containers and even full VM's. So even if something isn't available for the NAS OS per se, you could probably run it as Docker container like you would on any Linux server.

Yes, running your own server will offer you immense flexibility and freedom of choice. No argument there. But going for a NAS is not like your hands will be tied behind your back... you still have options.

---

### Post by slickymaster on 2021-02-08
*Thread moved to **Server Platforms**.*

---

### Post by ameinild on 2021-02-08
And then there is the hybrid solution of building your own server, but installing a "NAS" distribution on it, like OpenMediaVault or TrueNAS.

Again, each has benefits and drawbacks. The benefits of OMV and TrueNAS are that both have very slick web GUI's for configuring mosts aspects of the system. But they're still running Linux (or FreeBSD for TrueNAS Core) underneath, and can be tweaked as you wish.

I've opted for Ubuntu server, because I like more hands-on control about what I run. But both OMV and the upcoming TrueNAS Scale are based on Debian, and can run docker containers as well, which gives you almost unlimited options, just like an Ubuntu server.

---

### Post by rucker222 on 2021-02-08
Wow! 

There is a lot for me to unpack here and I probably now have 100 more questions I need to ask myself... 

Thanks for your input, I've not had a chance to properly read through these yet but wanted to express my appreciation for the detailed responses and not appear ungrateful.

---

### Post by kevdog on 2021-02-10
I'd look at a NAS (I use TrueNAS right now and when TrueNAS Scale is finally done and finished -- its based on Debian as TrueNAS is based on BSD -- i'll be moving to that).

In terms of VPN -- my personal opinion is this is handled much better at router level with something like OpenVPN.

---

