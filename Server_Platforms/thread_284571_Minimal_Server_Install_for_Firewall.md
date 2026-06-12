---
title: "Minimal Server Install for Firewall"
date: 2006-10-25
forum: Server Platforms
---

### Post by compucoder on 2006-10-25
I am working on setting a Linux firewall for our company network that needs to do this:

Handle 5 public I.P.'s on 1 Network Interface and do IP Forwarding from one NIC to one of these IP's for our Internal LAN. I then want to do static NAT for the 4 remaining IP's to our servers. I already tried a test install of Ubuntu Server and using Shorewall I was able to accomplish what I need I think. I don't know if there is a better way of doing this - is Shorewall the best option? I am looking for speed especially for the One NIC connected to our LAN and using IP Forwarding to the outside world. We have 20 client machines which will be using this interface through the Linux Server. I also went out on a Limb and told the boss that I could build a better and faster firewall using Linux than what we could buy. We were looking into a Nortel router/firewall which started at $5000 - I bought the hardware for my Linux firewall for only $1000 - big savings already. I hope I am right that Linux can easily do the job a Nortel can do if not better.

I would also like to do these things on the Linux Firewall as well:

Have graphs for network usage. I would really like to have a graph breakdown for all users on the LAN so I can see what usage pertains to each computer

Have a transparent web proxy

Scan any mail coming into the company before it hits Exchange and scan it for viruses and Spam if possible.

Have a VPN server which will authenticate users against our Windows domain and if they are permitted to come in they get access to the LAN network.

Can anyone offer suggestions on what I should setup.Should I be using Ubuntu Server for this or would another distro be better?

If I use Ubuntu Server is there a way to install the utmost minimum as I only want a firewall with the features listed above.

Thanks for any input you can offer.

---

### Post by nix4me on 2006-10-25
Use ipcop or m0n0wall.  They are perfect for what you want and they do everything you need.

nix4me

---

### Post by compucoder on 2006-10-25
> **nix4me said:**
> Use ipcop or m0n0wall.  They are perfect for what you want and they do everything you need.

nix4me

I tried IPCop and wasn't very impressed. It didn't seem to be geared towards use in a corporate environment. I tried it at home first and it did the job nut the graphs were weak, the support for using 4 NIC's and segregating our network into zones didn't seem possible. I also didn't see anything in it for doing DNAT. I was thinking a Ubuntu firewall would give a lot more power and customizability. I may be totally wrong on this but IPCop uses an old Kernel tree - isn't the 2.6 Kernel with IPTables much faster and more advanced? 

What is your opinion on a home brewed Linux firewall against a solid state device like a Nortel product? The server I bought for this purpose is a 3.2 Ghz P4 with 160 GB Raid 0 SCSI drives. 1GB Ram and 4 Gigabit Nic's. I know a device like Nortel doesn't have anything close to these specs so I was thinking my server should outperform it in virtually everyway. I might be totally wrong, I hope not, but I might be. 

I have no worries about building this all from scratch and just need to know what the best packages are to do what I mentioned in the first post. I am always up for a challenge. :)

---

### Post by NewbieNik on 2006-10-26
I went out on a limb and purchased the Smoothwall Corporate server which is an enterprise Linux firewall using iptables and many others.
Its a pretty good product and a fraction of the cost of hardware solutions with just as much functionality with some good bolt-ons. Takes some configuring to get it to do what you want and, obviously you're paying for it, but it beats lost time and hassle of trying to configure Linux yourself!!

---

