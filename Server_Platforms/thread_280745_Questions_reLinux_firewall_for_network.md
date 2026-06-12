---
title: "Questions re:Linux firewall for network"
date: 2006-10-19
forum: Server Platforms
---

### Post by jstrubberg on 2006-10-19
Ok, my wife and I operate a small buisness with 97 employees.  I want to set up a firewall/spamblocker/antivirus server for our network.  I would also like to run file sharing services for our windows client machines.


LAMP seems like overkill, but maybe that's the way to go.  Anyone got any suggestions?  I have a month or so before I need to get this off the ground, so there's plenty of time to research.

---

### Post by kidders on 2006-10-20
Hi there,

Starting with a LAMP server is fine ... it's little more than a skeleton, really.

My software choices would be as follows, but just because *I'd* pick them doesn't mean you have to :-)

[LIST]
[*]Firewall: iptables
[*]SMTP: postfix
[*]Antivirus (Email): clamav + amavis
[*]Antispam (Email): spamassassin
[*]Filesharing: samba
[/LIST]

In terms of filesharing, what I usually do for Windoze clients is set up a samba PDC with LDAP authentication, giving you a Microsoft domain (security policy, etc.) with one of those "active directory" things. Real-time (server side) virus protection is a bit of a problem though ... it's a killer performance-wise, so I tend to just forget about it.

Additionally, you might want to consider squid (a www proxy), so you can control (and speed up) internet access. Also, courier-imap-ssl is a nice IMAP server, if you need one.

Hope that helps.

---

### Post by JustDave on 2006-10-31
Here's an article on howtoforge that may be of some interest. I'm thinking of doing something similar for my home network.

[http://www.howtoforge.com/perfect_linux_firewall_ipcop](http://www.howtoforge.com/perfect_linux_firewall_ipcop)

---

### Post by hkgonra on 2006-10-31
Second vote for IPcop , I love it.

---

### Post by jimm on 2006-10-31
Hi,

I realise this probably isn't that helpful (you being a small business and all!) however if you can avoid it, I would split the firewall and file server functions. Running Samba on your firewall system opens up a few holes and makes the management of your firewall rules a bit more complex. Also, if your firewall gets compromised you will expose your employee's data straight away...

That said, I realise that having an abundance of equipment to deploy all manner of servers is not always an option! In any case here is what I would do to make your life easier... I would install a barebones ubuntu server, then put WebMin on it (sheesh all of my solutions seem to begin and end with webmin these days!) then use one of the many WebMin based firewall management interfaces (Shorewall, Turtle Firewall etc) to setup and manage your FW rule base. 

Then you can also use Webmin as the basis for managing whatever email / AV solution you choose. Clam+amavis, spamassasin, Postfix or EXIM etc etc these can all be managed via Webmin plugins. This will make your admin tasks and setup a lot easier!

Thanks,
James

---

### Post by hkgonra on 2006-10-31
If you are in the US you can get hardware strong enough to do what he wants to do on a seperate box for under $100. 
In fact if you are anywhere near me I will give you a box that will do it for free.

---

### Post by jimm on 2006-10-31
Hi,

What a cool offer! I was really more referring to the management overhead and the hassle of running multiple machines for a smaller organisation than the hardware cost, but its very cool to see folk willing to help out like that... I am impressed!

Anyway if multiple boxes is not an issue, I have been using mono-wall for my firewall for a while now and it is really nice! Not Ubuntu though (BSD) but a very good little firewall appliance distro. 

Thanks,
James

---

### Post by hkgonra on 2006-10-31
I have heard good things about monowall. Never used it myself but I bet it would be fine.

---

### Post by hkgonra on 2006-11-01
As far as the overhead I wouldn't worry about it. 
In fact I like the idea of having mulitple boxes doing different things. Why keep all your eggs in one basket ?

---

### Post by kidders on 2006-11-01
> **hkgonra said:**
> As far as the overhead I wouldn't worry about it. 
In fact I like the idea of having mulitple boxes doing different things. Why keep all your eggs in one basket ?

Hi there,

You should be a little wary of this policy. Take RAID as an example. When a filesystem spans multiple devices, this doesn't *spread* your hardware failure risk ... it *increases* it. Multiplies it, in fact. Similarly, by spreading critical network services across, say, 3 machines, you *triple* the probability that your network will break.

In RAID's case, checksumming & mirroring solve this problem. You should try to build your network with a similar attitude.

This observation may be blatently obvious to you already, but when I saw your last post, I though I should just make sure. Imagine you had DNS on one PC, filesharing on another, and postfix on a third. Your network is useless without them, but you'd have tripled the likelihood that you'll lose one, when compared to running them all off the same box. A "better" rephrasal of your last post might be "I like the idea of having mulitple boxes doing **the same** things".

If this isn't news to you, please forgive the intrusion. :-#

---

