---
title: "Forwarding traffic on a specific port (SMTP) through an SSH tunnel using iptables"
date: 2013-03-05
forum: Server Platforms
---

### Post by nonentity133742 on 2013-03-05
I asked this a few days back in  the networking section of the forums, but realized this is a more apt place to find an answer. Alright, the question of why I would want to do this is probably going to be the first to come up, so I'll answer that first. I am a casual Ubuntu user and a few months back started hosting my own email server for personal and home use by. Comcast, being the wonderful ISP that they are, decided to block all of my incoming and outgoing SMTP traffic over port 25 without any kind of notification whatsoever! I hadn't had an issue with them for the past six months, so I spent about 3 days troubleshooting my configs, routing, port forwards, etc. and came up with nothing. When I finally decided to call them, I was bounced all around the "tech support" department. Of course nobody knew anything and they all told me to use my "@comcast.net" address or to talk to my service provider. At this point, I just said screw it and got myself a VPS to be a mail relay. Now the reason I'm here on the forums is that, while I was able to route mail traffic from the remote ports on the VPS (back to my locally hosted mail server through SSH forwards) I have not been able to find a way to tell postfix to either send through my VPS (preferred) or send using a different port. I've literally spent hours on google for this one, but have not been able to come up with a decisive answer. What I have found is that the best solution would be to use iptables to forward traffic to the VPS, which would act as a "gateway" (MASQUERADE) to the outside world. Other solutions involve smarthosts (I really don't want to set one of these up because I have no clue how and don't want to spend the time making another whole mail server just to route outbound traffic) and proxies, which seem to be able to relay conversations between mail servers (But the one's I've seen seem to just be extentions of postfix for processing mail and not actually sending it). If anyone is able to come up with a real solution please do post. I would appreciate it if people could refrain from posting things telling me that my VPS solution is overly-complex or to scrap i and try something else as well.

---

### Post by SeijiSensei on 2013-03-05
Look at the description of the "relayhost" parameter [here](http://www.postfix.org/postconf.5.html).  You'll need to run postfix on the remote server as well.

Have you asked Comcast about using their server as a mail relay?  I believe they offer that service, though I don't know whether it extends to residential users.  I'd bet servers in general are forbidden by their Terms of Service.  Most residential contracts ban servers.

You might want to consider using OpenVPN to set up a point-to-point tunnel between the two machines.  It's pretty easy to do if you use the [static-key method]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  If you take this method, you can set up iptables forwarding rules that would route traffic intended for remote port 25 over the tunnel to the VPS. 

I'd use a relayhost, though.  It's easier to set up.

---

### Post by nonentity133742 on 2013-03-06
Thank you, SeijiSensei, for the quick reply. It does seem that a smarthost would be a quick and easy setup, I only have two issues with using one:   1. I cannot find a tutorial on how to set postfix (or really any other mail server, for that matter) up as one, everything out there is about configuring a server to use an existing smarthost.  2. I think this is easily solvable by using postfix as you said, but I would like to configure the smarthost to use my SSL certificates and keys as well as any other configurations on the main server.

---

### Post by SeijiSensei on 2013-03-08
I suspect it will all "just work" if you choose the "Internet" option when installing Postfix on the relay host.

I don't really see any need for certificates and the like if you're simply passing mail through the relay.  You can restrict the relay to only accept mail from your server with the "mynetworks" directive or appropriate iptables rules on the relay.

If you really want a secure channel between the machines, install OpenVPN as I suggested before.

---

### Post by nonentity133742 on 2013-03-13
Thanks for your help, I was finally able to set it up yesterday; just a basic postfix server running on port 26 with a local forward to the server works as an excellent smarthost.

---

### Post by brookiemonsta on 2013-08-22
You can actually achieve your original goal without having to configure another smarthost on your vps.

Configuring a multi-homed shorewall firewall on your email server which routes all outgoing traffic on port 25 via your tunnel to the vps, and then SNAT/masquerading on your vps works very well. This has the advantage that if you have encrypted smtp configured on your home server then your ssl keys cannot be read by anyone with access to your vps instance.

Edit: to clarify which firewall goes where.

---

