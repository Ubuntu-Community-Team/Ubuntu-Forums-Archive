---
title: "Why aren't outgoing emails sending? (Ubuntu Server on static Comcast line)"
date: 2014-03-14
forum: Server Platforms
---

### Post by icebox83 on 2014-03-14
I'm running a few WordPress installs on my Ubuntu Server, which is connected to the outside world via my static Comcast line, but outgoing emails aren't working. Backing up a few months I thought something fancy had to be configured, so I just worked around the impending work and set up a WordPress SMTP plugin, passing outgoing traffic through my Gmail account. But this is slow - I would really like to get this outgoing email stuff working natively rather than pay $100 a month for a DV plan with a major host. Here's where I'm at now:

- I'm thinking Comcast isn't allowing traffic through port 25
- Definitely not just a problem with this particular server, as I also tried MAMP and TurnKey Linux VM (I'm fairly certain outbound emails used to work with MAMP)
- I have started reading about Postfix but am having trouble understanding what I need to do and why

Can I just change a setting and having the emails go out via port 587, or do I need to go through a bunch of configuration? Are there log files that will help me pinpoint the exact problem?

---

### Post by SeijiSensei on 2014-03-14
Comcast definitely blocks outbound port 25 and has for a long time now.

I assume you are aware that running a mail server on a Comcast residential account violates your Terms of Service which has an explicit "no-servers" policy:

> prohibited uses and activities include, but are not limited to, using the Service, Customer Equipment, or the Comcast Equipment, either individually or in combination
with one another, to:
[...]
use or run dedicated, stand-alone equipment or servers from the Premises that provide network content or any other services to anyone outside of your Premises local area network (&#8220;Premises LAN&#8221;), also commonly referred to as public services or servers. Examples of prohibited equipment and servers include, but are not limited to, *email*, web hosting, file sharing, and proxy services and servers

From [http://www.comcast.com/Corporate/Customers/Policies/HighSpeedInternetAUP.html](http://www.comcast.com/Corporate/Customers/Policies/HighSpeedInternetAUP.html) (emphasis mine)

---

### Post by icebox83 on 2014-03-14
> **SeijiSensei said:**
> Comcast definitely blocks outbound port 25 and has for a long time now.

Good to know! So...what are my options? Is there any reason to look at logs before proceeding?

---

### Post by SeijiSensei on 2014-03-14
Well I doubt Comcast will help much given the AUP I posted while you were writing your reply.

I have a mail server in my home, but I also have virtual servers at Linode which actually handle all the traffic and forward mail for my accounts to my home over an OpenVPN tunnel.  Before that I had a business-class line on Verizon FiOS.

---

### Post by d4m1r on 2014-03-24
Short of getting access to a linux machine hosted outside your network (such as a VPS mentioned above), often ISPs will have outgoing relay servers that you can use so maybe you should ask?

For example, my ISP blocks outgoing mail on port 25 as well HOWEVER, they have a relay agent set up to accept and pass along emails from any IP on their network. So I set my email client to use their outgoing server instead for example.

---

