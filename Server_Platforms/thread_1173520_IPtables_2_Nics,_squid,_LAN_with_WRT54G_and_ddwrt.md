---
title: "IPtables 2 Nics, squid, LAN with WRT54G and ddwrt"
date: 2009-05-29
forum: Server Platforms
---

### Post by pwebguy on 2009-05-29
I am wanting to create a firewall/proxy on an ubuntu server box with 2 nics. I read through several forum posts and tutorials, but I can't find procedures specific to what I am wanting to do.

So far here is what I have come up with:

1. Internet is provided by isp from a router.
2. I am connecting to the router with my server on eth0 configured with a static IP 192.168.1.200, manually configured DNS, all working fine.
3. eth1 is set to 192.168.2.1

I want to plug a linksys wrt54g router running ddwrt into eth1 with a static IP, and allow it to do DHCP for my local LAN. This way I can "plug 'n' play" easily the devices on the LAN without messing with the firewall rules.

So, I configure the router IP as 10.1.1.1, with a gateway 192.168.2.1

Is that correct procedure? Assuming I am correct so far:

Once the Lan can get through the ubuntu server to the internet, I want the ubuntu server to act as a firewall using IPTables; the posts/tutorials I have found specify IPTables to do NAT; is that to translate from one nic to the other? I assumed that there should be a simpler rule since I am using 2 static IPs, not one static (WAN) and then DHCP for eth1 to output to a switch? so how should I set the rules?

Once I get this working, I want to install squid and forward all the LAN traffic through it (on the same box, if the traffic as allowed through the firewall) The installation and configuration of squid seems straightforward, but what IPTables rule(s) would work for allowing allowed traffic through to the proxy? (maybe that should be the subject of a complete new post?)  :)

Thanks for any pointers or suggestions.

---

### Post by samosamo on 2009-05-30
what the hell. damn this post is confusing.  why would you need 3 routers and all these subnets!?!  what are you doing???

i read this post 10 times just to make sure and it seems to me you want to me that if you were just to connect your WAN link to eth0 on your ubuntu box, and then connect eth1 to a switch, that is all you need.  one router.  one private subnet.

why not use the WRT54G for all your routing/dhcp/firewalling/etc?  you already own them, right?  no extra money to be invested?  why not separate the services from your ubuntu box and let it handle all the heavy stuff?  i recommend Tomato firmware over dd-wrt.

---

### Post by pwebguy on 2009-05-31
Sorry, didn't mean to be confusing.

> why not use the WRT54G for all your routing/dhcp/firewalling/etc? you already own them, right? no extra money to be invested? why not separate the services from your ubuntu box and let it handle all the heavy stuff?

Aside from the firewalling and squid, that is exactly what I am wanting to do; The goal is to use the server only as a firewall and proxy to be able to monitor/shape traffic on the local LAN which has 20 computers.

My thinking is that if I set the server to firewall/filter for one LAN IP adderess (the WRT54G) then I don't have to configure the server to do DHCP/NAT, instead letting the wrt54g handle those tasks.

Here is what the network would look like:

Internet
ISP Provided Router(192.168.1.1, I can't configure anything)
Ubuntu Server1 eth0 (192.168.1.200)
[INDENT]<firewall rules>[/INDENT]
[INDENT]<squid (eventually)>[/INDENT]
Ubuntu Server1 eth1 (192.168.2.1)
WRT54G: WAN: (192.168.2.200) LAN(10.1.1.1,Gateway:192.168.2.1)

Is there a better way to accomplish my goals?

> i recommend Tomato firmware over dd-wrt. 

I have been using ddwrt for several years; why do you recommend tomato over it?

---

### Post by samosamo on 2009-05-31
This is not a WRT54G forum so I won't go into that.  Use dd-wrt if you like.  It was just a suggestion in case you couldn't get dd-wrt to do what you needed.

I believe you need to take an introduction to networking course or read a bit more on this subject.

---

### Post by pwebguy on 2009-05-31
Well, ok, thanks for the RTFM.

I have always learned by doing, in this case I am supplementing what I have learned so far with 'Administering Data Centers' by Kailash Jayaswal, as well as a pile of Linux Journal back issues (on pdf) and of course Google.

I have built IPTables firewalls for specific servers many times and for many configurations (email servers, web servers, VOIP servers, IM servers etc), but never as a standalond firewall with 2 network interfaces.

Now, I have the opportunity to rebuild our corporate network 'from scratch', on a shoestring, and I want to do it right. The above scenario is an idea put together of a ton of sources, but I have never come across this exact setup.

So, at the very least I was expecting someone to tell me if I was completely doing this wrong, or give some pointers on how to keep with best practices.

> This is not a WRT54G forum so I won't go into that. Use dd-wrt if you like. 

You brought it up. Not me.

Maybe I am asking in the wrong forum. If you do not know or cannot qualify your answers with anything other than RTFM, do not waste my time.

---

### Post by samosamo on 2009-05-31
Just remember not to get frustrated and make angry posts just because people won't hold your hand on an internet forum.

I already told you. You're completely going about it the wrong way. **3 router's and 4 subnets are completely unnecessary for your situation.**

Are you seriously in charge of "rebuilding a corporate network from scratch?"

---

### Post by pwebguy on 2009-06-01
I apologize, but what makes me angry are statements like:

> I believe you need to take an introduction to networking course or read a bit more on this subject. 

If I am wrong, then tell me why I am wrong. Maybe I am just not explaining myself clearly?

I am learning on the job; I do not want anyone to hold my hand or do this for me - I want to learn. I had an idea on a way to solve my problem, and can't find a similar solution online, that is why I posted here.

So, all I am asking is that instead of RTFM, please tell me where I am going wrong so I can learn and correct it. That is the purpose of a forum, yes? What is wrong with the scenario I describe? Do you need more information - I'll be glad to provide it.

BTW, Yes I am in charge of rebuilding a corporate network from scratch. I have been at the same company for 6 years. They started with one office, a single website on a shared host, which I was hired to manage, in addition to 'maintaining' their office computers.

They now have 3 local branches and 2 international offices. Instead of hiring from outside I created my own job by learning what was necessary. Now I am the 'IT guy'; There are now multiple websites, all offices are connected by multiple asterisk servers and IM software. We migrated from the shared host to leased servers and colocos. Now management wants all the servers in-house for web, email and VOIP.

My current task (the reason for this post) is to take the main office internet access and firewall and/or proxy it so that I can monitor employee traffic and prevent bandwidth abuse. This internet line starts with a router provided by the ISP, which I cannot change or configure. The wrt54g in my scenario will feed lines connected to switches on 3 floors, where all the equipment is hard-wired save one wireless access point.

The web/voip/email servers are all set up on a separate access with a firewall appliance so they do not come in to the picture. - I thought that with a spare ubuntu box and my router I could accomplish basically the same thing as the firewall appliance  and save the company money (and make the accountants happy). :)

So please tell me what is wrong with my scenario; you mentioned that the extra subnets were not necessary; are you meaning the IP addresses for the nics? Should they be on the same subnet? If the ISP router is providing 192.168.1.0\24 should I instead put the 2 nics on 192.168.1.200 and 192.168.1.201 instead?

---

### Post by wirelessmonkey on 2009-06-01
You need to configure your routes on "Server1"
Would you post the output of
```

route

```

---

### Post by Pnuts on 2009-06-01
I think samosamo is mainly trying to ask you why you are going to have 3 subnets and 3 routers.

It appears based on your posts the ISP modem is a router itself providing addresses on the 192.168.1.0 subnet. Your then sticking a 2nd router (the Linux box) providing a subnet of 192.168.2.0. Finally your sticking a 3rd router (wrt54g) on this subnet to provide a 3rd subnet of 10.1.1.0.

Ideally, it should go Internet<->ISP Modem\router<->Linux Box<->Computer network. your just adding in un needed extras basically.

---

### Post by samosamo on 2009-06-01
This is gettin ugly

I'm not sure what you meant by this so I cannot comment on it: The web/voip/email servers are all set up on a separate access with a firewall appliance so they do not come in to the picture.

Now about the proxy. If me, being me, were to set up a proxy server at a small office such as yours, I would do it like so:

Internet provided by modem -> wrt54g -> all other devices

The WRT54G is your gateway, firewall, DHCP, DNS,etc etc server. Let's call it 192.168.0.1. Enable access rules to block ALL internet traffic except 192.168.0.2, which you will give to your ubuntu box.  Install squid proxy server and dans guardian or whatever on the ubuntu box, and set all your clients to use proxy 192.168.0.2:3128.

Now if anyone tries to get outside they will get denied by the firewall. To get outside they will be forced to use the proxy, which you control the policies on.  You can block ports, protocols, domain names, whatever you want.

One subnet. One router.

---

### Post by pwebguy on 2009-12-13
I thought I would post a reply to show my final solution. 

I must give kudos and thanks for patience because, you were right, samosamo, I needed to RTFM. Several books and many re-worked VirtualBox testing servers later, I now reread the OP and cringe a little.

After more studying I learned that what I was needing was a 'gateway' scenario, not only a 'firewall' (that was the initial epiphany anyway), and that confusion in terms (along with a wee bit of ignorance) lead me down the path of the convoluted setup idea I had.

Currently, I have a pfsense box acting as a firewall for this local office, which provides access to my ubuntu gateway and a DMZ for the servers. My humble ubuntu box is acting as a gateway for the local LAN, behind pfSense, providing DHCP, DNS and squid for (at last count) 52 devices.

The subnet idea was over-thought and misunderstood (by me).

So, again - thanks samosamo for the kick in the right direction.

---

