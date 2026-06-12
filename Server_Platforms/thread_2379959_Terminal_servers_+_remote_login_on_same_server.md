---
title: "Terminal servers + remote login on same server?"
date: 2017-12-11
forum: Server Platforms
---

### Post by samden on 2017-12-11
This is a very basic question, I just can't see a clear answer elsewhere.

**Question:**
*Is it possible to have a single server both running thin clients (via LTSP), and allowing the same users to remote login via VNC or similar? In other words, could the one user sit down at a terminal server and log in, or later pick up a laptop and then remote in to the same account from that? Can there be multiple users on thin clients and multiple other users via VNC at the same time?*

**Reasoning:** (feel free to skip this, but if you've got time I'd appreciate any additional thoughts) 
I have a number of children whom we homeschool, and I work from home. The kids are getting into Blender, video editing etc, and none of our machines are really powerful enough for it, we have an eclectic array of recycled machines at present. Most of the time their requirements are very modest (web browsing etc), just occasionally someone will want to render something. I also occasionally want to do large statistical computations for work. And documents keep getting scattered across multiple machines. Also, we're living off-grid and need to minimise power consumption, so I'm not keen on having a large number of powerful computers all running at once, but one efficient one is fine. 

I'm keen to consolidate everything by investing in a single powerful server that will easily handle rendering etc, and make it accessible from every machine in the house. Then anybody, from anywhere on the local network, can log into their central account and do whatever, knowing that the machine will be able to handle it. The children can then have the freedom to work on what they like without struggling against the limits of their individual machines.

Terminal servers are very attractive for administrative and power consumption reasons. However, I don't want to have everyone tied to fixed clients, I do want the flexibility to use laptops, and there are locations around our property where I cannot practically run ethernet cabling for a terminal server network. Hence my question. 

I'm an experienced Linux user (desktops and laptops), but have little experience in running servers. I want to be certain I am on the right track, so I don't invest many hours figuring out how to do something that wouldn't work anyway! Thanks for any advice or suggestions you can offer.

---

### Post by volkswagner on 2017-12-11
I'm no expert in this area, but I'd like to get the ball rolling.

Questions:
How many users are you looking to manage?
Will users travel with their laptops outside the local network? 
Will client machines act both as thin client and stand alone workstation?
How tech savvy/capable are users?

Things to consider/research:
EdUbuntu (seems 14.04 is latest release) or DebianEDU
LTSP with LDAP
Maybe LTSP is overkill. If you have small group of users, it may be "easier"/less complex to allow ssh login to the server with X forwarding for things like blender. You can create scripts/shortcuts to act as launchers for ease of use.

---

### Post by samden on 2017-12-11
Initially 7 users on about 4 machines (taking turns), but with the ability to expand to about 10 users on around 10 machines.

We'll have a couple of laptops that will get taken off-site, but no need to access the server remotely, any necessary files can be copied to local storage. I'd prefer not to deal with the added complexities and security issues of remote access at this stage.

Most users are young children (<10), so not tech savvy (yet!).

It's the thin client vs standalone workstation question that I am trying to decide. We will need a couple of laptops to remain able to be used as standalone workstations (one for my work, one for general family use). I don't know whether to keep all clients like that, or to run thin clients for most purposes. My first question is simply, is such a mixed environment reasonably practical to setup, or is it unusual and therefore complex? 

I don't know whether to give the kids cheap "netbook" style laptops they can use for web browsing and then remote in to the server for anything more demanding, or just give them fixed thin clients to use. The second sounds simpler for them, less for them to think about as they do everything in one place, and whatever machine they log into all their files and software are just there - but it may be more complex for me to set up.

My first thought was Edubuntu, it's just unfortunate it's so dated, I'd prefer to ensure access to fairly recent versions of software. 

I will look into DebianEDU - my gut reaction is to stick with Ubuntu or Mint for desktop users in the hope that things are more likely to "just work", whenever I use Debian there's always more to configure. But I will investigate it, thanks.

What I was envisioning was an Ubuntu or Mint install, served to multiple users in whatever way was most practical - thin clients (e.g. ltsp), remote desktop, or both.

Unfortunately I haven't set up anything quite this complex before. Thanks.

---

### Post by samden on 2017-12-13
Thankyou @volkswagner, on further investigation DebianEDU looks near-ideal for my purposes, thankyou for pointing this out to me, I didn't know it existed before you mentioned it.

I still don't have a clear answer to my initial question - can a user log into their account on an LTSP server via VNC, allowing them to run server-side apps from any machine on the network - not just access their files from some. However your suggestion that I could use scripts with X-forwarding for particular programs may well be a better solution though. I'd appreciate further clarification on what is possible here from anyone.

---

