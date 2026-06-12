---
title: "Password on a firewall?"
date: 2007-01-29
forum: Server Platforms
---

### Post by kenquad on 2007-01-29
Hi all:

Pardon any ignorant ramblings of one who does not fully understand the purpose of firewalls.  I am wondering if, as well as IP filtering, NAT and all that other good firewall stuff, there is a package one can add to simply password-protect access to the connection itself from the outside.  In other words, NONE of your packets get through unless you can supply the super-unbreakable password, like an ever-vigilant sentry, sort of.  Any thoughts?

Ken Quad

---

### Post by scrooge_74 on 2007-01-29
Noy an expert, but what exactly you want to do? Limit other users access to internet or sites?

You can make rules in your firewall manager (Firestater is what I use).

---

### Post by kidders on 2007-01-29
Hi there,

Unfortunately, the kind of behaviour you're referring to is very application-level. Firewalls are low-level services that block or accept packets without any particular knowledge of what they mean. You can only really start to worry about passwords & things once you've layered tens of other protocols on top of IP. HTTP, for instance, supports authentication.

The comparative "stupidity" of a firewall (when compared to a filesharing app, etc.) is quite deliberate though. It makes them extremely fast, and almost impervious to exploit. Since I mentioned it, consider HTTP for a moment. In order to deny a user access to something, quite a large number of packets may need to be exchanged. If a firewall were to behave like this, it would be terribly vulnerable to DoS attacks.

Perhaps what you're after is a firewall that admits certain kinds of connections ... say HTTP (again!) data. You could run an application like Webmin over HTTP, which would allow you to remotely control various aspects of your system's operation, including the firewall. You could use *that* to alter the behaviour of your firewall, subject to a password. I suppose the end result could be what you're looking for ... even if the underlying concepts are different.

Take a peek at Webmin. See what you think. :-)

---

### Post by kenquad on 2007-01-30
Kidders:

Thanks for your thoughts.  I've looked at Webmin and it seems rather interesting, *but*, since the machine in question is also my firewall, isn't opening Port 10000 and putting an administrative interface on it a rather blatant security risk?  It puts me just one password away from total system destruction!  Am I mixed up?

Ken Quad

---

### Post by scrooge_74 on 2007-01-30
I rather use a firewall interface than Webmin

---

### Post by kenquad on 2007-01-30
Because of the security questions I just brought up or some other reason, Scrooge_74?

---

### Post by scrooge_74 on 2007-01-30
Webmin is a nice tool, but I prefer to learn what I am doing instead of letting the program  to things.  As an example, by using Firestarter in the long run I learned which ones where the config files where things got store when I use the interface so I can do it manually from the command line.

But that is just me, if you configure Webmin properly it should not accept any conections from outside the lan or that particular PC.  But then again it those make me a little uneasy to have ports open for that kind of services.

EDIT: I just read this article with some information that has to do with this thread [http://apcstart.com/node/4690](http://apcstart.com/node/4690)

---

### Post by kidders on 2007-01-30
> **kenquad said:**
> I've looked at Webmin and it seems rather interesting, *but*, since the machine in question is also my firewall, isn't opening Port 10000 and putting an administrative interface on it a rather blatant security risk?  It puts me just one password away from total system destruction!

Yep... it would be a bit crazy... but it's effectively what you asked for in your o/p. By disabling every Webmin module except the firewall management, you get password-protected, externally accessible control over your firewall. Tbh, I would very strongly recommend against doing anything of the sort though ... a firewall you can turn off from the outside is no firewall at all!

Scrooge_74 already asked, but I'm curious too... why would you want to be able to selectively open and close ports from *outside* your firewall?

---

### Post by kenquad on 2007-01-30
Hmm.... I'm afraid remote administration of the firewall has sneaked into this thread and been confused with the topic...  I really don't care whether I can administer the firewall remotely or not - and I agree that would be a huge security risk anyway - you had just mentioned Webmin earlier in the discussion.  The main point is to make this site as secure as possible.

---

### Post by Brazen on 2007-01-30
> **kenquad said:**
> Hmm.... I'm afraid remote administration of the firewall has sneaked into this thread and been confused with the topic...  I really don't care whether I can administer the firewall remotely or not - and I agree that would be a huge security risk anyway - you had just mentioned Webmin earlier in the discussion.  The main point is to make this site as secure as possible.

I know this is (continuing) off topic, but port 10000 could be configured to only allow connections from the local LAN, and maybe also from your home IP (assuming this is a work network) in case you need to do something from home.

For the original question (in this thread :)) you want a VPN.  Do I need to explain a VPN to you?  I'm thinking maybe it just slipped your mind :)  OpenVPN is the de facto standard.  However for your firewall appliance, I would suggest using a firewall linux distro such as pfsense (my recommendation), m0n0wall, or ipcop which will come with built in VPN software (based on OpenVPN).

---

### Post by kenquad on 2007-01-30
> 
Pardon any ignorant ramblings of one who does not fully understand...

Hey, I warned you :)

Brazen, I think VPN may be the concept I've been trying to lay a finger on.  I'm afraid my knowledge on the subject, though, could fill a bottle cap halfway.  The only VPNs I have worked with are the ones provided by data link vendors to connect sites.  I became aware of OpenVPN and the technology to connect "Road Warriors" only last night when I first looked at Endian Firewall.  (Incidentally, do you recommend pfsense over Endian?)  I wouldn't want to put you to the trouble of explaining the whole OpenVPN thing to me, but if you can point me to some good online materials I'd appreciate it.

Thanks,
Kenquad

---

### Post by Brazen on 2007-01-30
I'll just give you a rundown on the VPN solution.  You can google if you need more info.  You might specifically try the OpenVPN website.

Basically, what a VPN does is makes your computer act like it was physically plugged in to the local network.  So what you could do is block all incoming traffic from the internet on your firewall.  When you establish your VPN connection, your remote computer will have all the access of a computer inside your network (actually, you can create firewall rules specific to the VPN, if you want).  The VPN connection with OpenVPN is encrypted with SSL to keep your data safe.  You will want to avoid PPTP connections like the plague as they are not encrypted at all.

As for Endian Firewall, I don't remember it ever showing up on my radar, so good or bad, I can't tell you.  The three I mentioned though are definately the most popular, and for good reason.

---

### Post by Brazen on 2007-01-30
What is your existing router?  You might be able to put dd-wrt on it and gain a lot of the functionality of the linux firewall distros (dd-wrt is a firewall distro made to install over the firmware of many cheap home routers).

Otherwise, I would completely replace your existing router and just use your new firewall as the router.

---

### Post by kenquad on 2007-01-30
It's one of those El Cheapo Centavo Speedstreams from Siemens, a 5200.  The phone company sends them out free with DSL :)

---

### Post by Brazen on 2007-01-30
What you MIGHT consider doing then is get a PCI DSL modem to put in your new firewall appliance and ditch the Siemens.  Not sure how pricey those things are, but it would simplify your setup.  There would be nothing wrong though with putting another firewall behind your Siemens.

That firewall would also act as another router though.  There's nothing wrong with that, but just so you know.  Basically you will want to configure the Siemens to forward everything the external IP of the new firewall/router.  Now there will be one subnet between the Siemens and new firewall, and then there will need to be another subnet after the firewall.

The other option is to use a bridging firewall but that is much less supported, and I'm not even sure if the linux firewall distros have gui setups for bridging firewalls.

---

### Post by kenquad on 2007-01-30
Brazen:

Thanks.  I will probably just go with the firewall box behind the router... simpler that way :)

But a disturbing thought just occurred to me: My web application requires bandwidth - LOTS of it :(  So, doesn't openVPN (or any other VPN for that matter) inherently slow you down a good bit?

Kenquad

---

### Post by Brazen on 2007-01-30
In my experience, over a Cox cable broadband internet anyway, I would not say it slows it down a noticeable amount.  Of course, there will be some overhead, and if you are on a dial-up connection that overhead may have more of a noticeable effect, and of course you will be limited by the 56K anyway.

---

### Post by kenquad on 2007-01-30
But the overhead is all in the machines used to encrypt/decrypt the connection, right?  So faster machines = faster connection....?

---

### Post by Brazen on 2007-01-30
> **kenquad said:**
> But the overhead is all in the machines used to encrypt/decrypt the connection, right?  So faster machines = faster connection....?

There is _some_ overhead with the encryption/decryption process, but what I was referring to is the overhead in the transmitted packets.  Basically, every packet you send over the VPN will have the original packet information, plus a little extra for the ssl information, plus a little extra for the vpn information.

---

### Post by kenquad on 2007-01-31
OK, I see now... just have to try it and see what happens.  I think I'll start with Endian, as it looks pretty easy to configure.  Thanks again for all your help.:KS

---

### Post by kenquad on 2007-02-01
Well, I'm up and running with Endian.  OpenVPN is great!  Thanks Brazen and all for the sage counsel.  Talk to you later.:D

---

### Post by Brazen on 2007-02-01
You're welcome :)

---

