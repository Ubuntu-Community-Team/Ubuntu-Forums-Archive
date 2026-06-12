---
title: "ESXI, Smoothwall and XP RDP project"
date: 2012-01-24
forum: Server Platforms
---

### Post by mr-woof on 2012-01-24
Hi all,

this isn't particulary a Linux server issue, but does have Linux machines involved, so hopefully that'll be enough :)

I was talking to a guy the other day, who can access a home Windows PC via RDP. Now I work in IT and that would be handy at times, especially to test things, in work especially or if I'm out and about.

Now I have an ESXI server at home, so I can play around with different servers, domains etc, and I've virtualised an old XP laptop to play with for this little project. 

I know RDP is encrypted, but my concern is opening 3389 straight to the Internet and to a machine, vm or not. If someone scanned my range and connected on 3389 they would be staight through to the username and password screen. I was thinking of running smoothwall in front of the vm on a different IP range, with only ports 3389 in and 443 and 80 to be let out.

I'm trying to think of what damage someone could do, if they did get in. What are people thoughts on this? Before anyone says, use a Linux machine with ssh etc, If I did want to try this in work, I'm sure we only allow out 80, 443 and 3389. 

Hope that makes sense? :)

---

### Post by Dangertux on 2012-01-24
> **mr-woof said:**
> Hi all,

this isn't particulary a Linux server issue, but does have Linux machines involved, so hopefully that'll be enough :)

I was talking to a guy the other day, who can access a home Windows PC via RDP. Now I work in IT and that would be handy at times, especially to test things, in work especially or if I'm out and about.

Now I have an ESXI server at home, so I can play around with different servers, domains etc, and I've virtualised an old XP laptop to play with for this little project. 

I know RDP is encrypted, but my concern is opening 3389 straight to the Internet and to a machine, vm or not. If someone scanned my range and connected on 3389 they would be staight through to the username and password screen. I was thinking of running smoothwall in front of the vm on a different IP range, with only ports 3389 in and 443 and 80 to be let out.

I'm trying to think of what damage someone could do, if they did get in. What are people thoughts on this? Before anyone says, use a Linux machine with ssh etc, If I did want to try this in work, I'm sure we only allow out 80, 443 and 3389. 

Hope that makes sense? :)

Well if you do decide you want SSH set SSH to listen on port 3389 or 80 or 443 :-P

In any case RDP is attacked pretty frequently, it would be wise to not only limit the ports allowed in and out but to whitelist IP's that would be using the RDP service. If it were compromised, particularly on an XP system, the impact could be catastrophic. Though if you're virtualizing on ESX , it would be fairly well contained.

Hope this helps.

---

### Post by spynappels on 2012-01-25
I agree that an IP whitelist approach would be a better option, as long as you know the IPs you'll be connecting from. 

You can do this using IPTables if you use some Linux routing solution between the internet and the WinXP box, some routers will also allow this, especially if they run the dd-wrt firmware.

I'm not sure if RDP can be set up with an IP whitelist itself though.

---

### Post by mr-woof on 2012-01-25
Thanks for the input guys, I hadn't considered a whitelisting style approach of IP's. I'm sure I could do that in Smoothwall, I'll have to look at it later on today and report back :)

---

### Post by sandyd on 2012-01-25
> **mr-woof said:**
> Thanks for the input guys, I hadn't considered a whitelisting style approach of IP's. I'm sure I could do that in Smoothwall, I'll have to look at it later on today and report back :)
Create a new vswitch, with Smoothwall on Green.
RED smoothwall interface should be on the port group thats connected to the net.

Create a debian server on RED, and install OpenVPN with bridging.

Thats more secure than just using RDP.

---

