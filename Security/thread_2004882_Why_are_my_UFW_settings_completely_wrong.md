---
title: "Why are my UFW settings completely wrong????"
date: 2012-06-16
forum: Security
---

### Post by zozza on 2012-06-16
Here are my ufw rules:

sudo ufw status
Status: active

To                             Action           From
--      ------             ----
128.100.22.22                 ALLOW       93.101.128.0/18

93.101.128.0/18               ALLOW OUT   128.100.22.22



128.100.22.22 is my IP

93.101.128.0/18 is the range for my VPN.

My impression is that I am saying: allow from my IP to the VPN range and then allow from the VPN range to my IP.

However, this is obviously not the case because I cannot connect to anything.

See the attachment for how it looks in GUFW.

What am I doing wrong?  Thanks!

---

### Post by darkod on 2012-06-16
I am not sure also, but even if the VPN connection is working fine, how do you expect to connect to anything with Outgoing set to Deny? Wouldn't it block all outgoing traffic?

With the current settings, can you at least establish the VPN connection successfully?

---

### Post by zozza on 2012-06-20
If the outgoing is set to 'allow' then it will connect to any IP.

My impression was that you 'deny all' then set exceptions.

Clearly not.

---

### Post by sammiev on 2012-06-20
I run over a VPN but over the net. Here are my settings I have been using.

---

### Post by zozza on 2012-06-22
I'm sorry but I do not understand your rules at all.

I realise that you are restricting outgoing access to certain ports.

However, as far as I can tell, you can connect to any IP providing that you only connect to the certain ports.

I don't understand how that means that you will only connect to the VPN?

If it fails then, with your settings, you could connect to any IP, right?

---

### Post by darkod on 2012-06-22
I am not 100% sure, but I think your understanding of VPN connecting trough the firewall might be wrong. Or mine is... :)

With your current rules you posted in the first post you can connect to the VPN, right? It works.

But after that, you still need rules to allow you connections to the outside. Just connecting to your VPN doesn't give you access to everything. It's only making it "virtually" like you are connecting from the place where the VPN is.

For example, how do you expect to open websites when port 80 is blocked? Everything is blocked except the VPN IP. You seem to think that you need to deny everything else and allow only the VPN to make sure you are using the VPN. But that is not done with the firewall, that's done with the VPN client. Once you establish a connection with the VPN server, that's it. From that point on you are working like within that network. And if you have a Deny All rules in your firewall, that would actually block you from connecting to anything. Which is exactly what is hapenning to you.

That is why the rules posted by the other posted have Allow 80, Allow 443, etc. They are not restricting access, they are allowing access to the outside (ALLOW OUT). Because the output policy is Deny, like in your case, you need ALLOW OUT rules for the traffic (ports) you want to allow. You still need them.

Do a quick test.
With the current rules from post #1 you can connect to the VPN right? Then connect to it.
Try to open any website. It fails right?
Open GUFW and allow port 80 to all destination IPs. Try to open any website. Is it working?

---

### Post by Ms. Daisy on 2012-06-22
A trouble-shooting technique: You can enable ufw, attempt to connect to the VPN, then look at the auth.log or ufw.log to see what specifically is being blocked.  Write rules to allow whatever is being blocked until you can successfully connect.

---

### Post by darkod on 2012-06-22
Do the test suggested in my previous post, I'm sure it will work.

To add my understanding. You think allowing only the VPN server IP is enough for everything, and here is where you are wrong in my humble opinion.

Don't forget, when accessing [www.google.com]("http://www.google.com"), with or without VPN, the destination IP is not the VPN server IP, it's the google server IP. At this point your own firewall is killing you.

You are saying to it: Allow only if the destination is the VPN IP. So it kills everything else. Which is everything.

Your VPN is only a means to access the internet, not the destination. The destination will be other servers.

At least that's what is logical to me. :)

---

### Post by sammiev on 2012-06-22
You can also run the test above and test your VPN as well and it will tell you what your IP address is at the time. :) Here's the [Link]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by Ms. Daisy on 2012-06-22
> **darkod said:**
> Do the test suggested in my previous post, I'm sure it will work.

To add my understanding. You think allowing only the VPN server IP is enough for everything, and here is where you are wrong in my humble opinion.

Don't forget, when accessing [www.google.com]("http://www.google.com"), with or without VPN, the destination IP is not the VPN server IP, it's the google server IP. At this point your own firewall is killing you.

You are saying to it: Allow only if the destination is the VPN IP. So it kills everything else. Which is everything.

Your VPN is only a means to access the internet, not the destination. The destination will be other servers.

At least that's what is logical to me. :) I agree. I suspect that if you look at the ufw.log you'll see just this kind of thing getting blocked.

---

### Post by zozza on 2012-06-23
deleted

---

### Post by darkod on 2012-06-23
I don't think so. I am not aware of any way to do that (not that I have looked for it).

I understand the VPN as only a one step more. When accessing a website for example, the server will never be directly connected to your home ISP router. It will need 6-7, sometimes 10-15 hops from router to router, to reach it.

The VPN is just one hop more. You are first directed to your VPN network, and you actually start going out from there.

You can't kill the internet outside the VPN totally, because you need the internet to connect to the VPN first of all.

I don't see a way to do that. But maybe I just don't know how to do it. :)

Why would you want to do this? You are worried about the security/protection when not connected to the VPN? So you want all internet to go through the VPN only?

One solution for that could be a router with built in VPN capability. That way you connect the router to the VPN network, and connect your computer to the router normally like to any other router. But in this case, all traffic goes through the VPN because your router is routing it like that. And since no one can have internet without being connected to your router at home, no one can have internet outside the VPN network. Something like that should be possible.

---

### Post by zozza on 2012-06-23
I think I've got it.

In GUFW:

From VPN IP range Action ALLOW OUT To 443 / 80 / 53 / etc.

If the VPN fails then the connection dies.

The only thing I can't get working is Deluge.

Normally I set the outbound and inbound ports to random.

Setting the outbound to a specific number e.g. 15000 then ALLOW OUT to 15000 doesn't allow any Deluge traffic.

Any ideas?

---

### Post by darkod on 2012-06-23
I'm not sure. Maybe it is going out but the incoming reply is getting blocked. Are you allowing back all the Established and Related traffic, as would be normal?

Look in the ufw log var/logs/ufw.log and it will say like [UFW BLOCK] so you can see if it's blocking the outgoing or incoming traffic, from which IP and on which port.

---

### Post by zozza on 2012-06-23
I have set GUFW to "Incoming Allow".

Ufw.log shows my SRC (the VPN IP) trying to connect to the seeders but getting blocked.

The GUFW ALLOW OUT from the VPN range to port 12000 and in Deluge I have set the outgoing port to 12000.

---

