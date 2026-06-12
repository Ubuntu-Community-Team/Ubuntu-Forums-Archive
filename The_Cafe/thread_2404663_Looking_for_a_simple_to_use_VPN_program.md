---
title: "Looking for a simple to use VPN program"
date: 2018-10-26
forum: The Cafe
---

### Post by eaterofcrisps on 2018-10-26
I'm looking for a VPN that's simple to set up. I really can't make heads nor tails of technical jargon or long lists of terminal commands. I've already downloaded a number of VPN programs but just can't figure out what I'm supposed to do with any of them. One of them, called Riseup-VPN, starts up and just closes. Other ones I've downloaded are far too technical. 

I'd like a VPN program that I can just select a location from a list or failing that one with simple instructions. Does anything like this exist for Ubuntu? 

I have a paid subscription to Avast SecureLine VPN for Windows by the way. I know it's a long shot but is there any way of using that on Ubuntu?

---

### Post by DuckHook on 2018-10-26
> **eaterofcrisps said:**
> I'm looking for a VPN that's simple to set up. I really can't make heads nor tails of technical jargon or long lists of terminal commands. I've already downloaded a number of VPN programs but just can't figure out what I'm supposed to do with any of them. One of them, called Riseup-VPN, starts up and just closes. Other ones I've downloaded are far too technical. 
I'm afraid that there aren't any I'm aware of that are just: download &#8594; click a button &#8594; install. They all require a greater or lesser amount of fussing with the command line.

I use Private Internet Access (PIA) which has good step-by-step instructions on their website for installation into Linux. It's a paid subscription, though.
> I'd like a VPN program that I can just select a location from a list or failing that one with simple instructions. Does anything like this exist for Ubuntu? 
This is how PIA works. You will need to sign up to their services first. I have no complaints about their throughput, but you may need to experiment before selecting the best gateway.
> I have a paid subscription to Avast SecureLine VPN for Windows by the way. I know it's a long shot but is there any way of using that on Ubuntu?
Best to ask Avast. If they have a Linux client, then they can best advise you about detailed installation instructions.

---

### Post by DuckHook on 2018-10-26
BTW, since this is not a technical support request, I've moved the thread to *The Cafe*.

---

### Post by henryshaw on 2018-11-19
I usually do Browsac VPN extension with my Google Chrome browser. It is good and free.

---

### Post by TheFu on 2018-11-25
> **henryshaw said:**
> I usually do Browsac VPN extension with my Google Chrome browser. It is good and free.

Many "free" VPNs are provided by agents of different govts around the world. What better method to gain access to all traffic from people seeking encrypted security?  [https://www.theregister.co.uk/2018/11/19/vpn_app_investigation/](https://www.theregister.co.uk/2018/11/19/vpn_app_investigation/) Check the "Bootnote" at the bottom of that article.

And this: [https://www.howtogeek.com/396747/why-you-shouldnt-trust-free-vpns/](https://www.howtogeek.com/396747/why-you-shouldnt-trust-free-vpns/)

---

### Post by Skaperen on 2018-11-27
i have been using OpenVPN.  it has as *lot* of configuration options so i have writing scripts to automate it as much as i can.  one thing that needs to be known at one end of a tunnel is where the other end is.  another is an agreed-upon addressing inside the tunnel.  and of course the encryption needs to set in a way both ends understand.

what i have long want to do is have encryption where both ends can work it all out without the user (the admin) having to configure anything.  i finally figured out how to do that. the "trick" is that only does this in the cloud.  i implemented this on AWS in the form of a AMI you launch as an instance in the VPC an region you want to connect to others.  once it is running. it examines the account to find other instances like itself and thus, knows where to connect to find other ends.  keys are shared-keys that are randomly generated and exchanged over tags.  a voting scheme chooses which of 2 keys per node pair will be used.  the tunnel addressing is statically defined based on which pair of regions are being connected.  because most users just use their default VPC numbered as 172.31.0.0/16 i added NAT configuration on OpenVPN to make each region appear at a specific IP address range different from other regions regardless what IP addresses the VPCs actually use.  i have tested the extreme case of running one in each of the 15 AWS regions (all address as 172.31.0.0/16) and watched them all connect to each other and set up the NAT and routing and begin world-wide tunneling.

i'm working on a new version that supports more than one VPC per region.  i'm also looking at ideas to scale up capacity when traffic increases in specific VPC pairings.  i also want to add a console that lets account owners control specific connections, rescale, disable, enable, and log them.  i'm also thinking about how to make tunnel connection between accounts.

---

