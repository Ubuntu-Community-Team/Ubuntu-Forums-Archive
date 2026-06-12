---
title: "Have I confused myself...local domain and hosted domain?"
date: 2013-04-04
forum: Server Platforms
---

### Post by KillerKelvUK on 2013-04-04
I'm slowly building up my linux knowledge but have a home ubuntu server running 12.04.2 now and use it as a samba server, web server, media server, DVB-S server and now I'd like to set up email and have a mail server.

I play around in Virtualbox setups before rolling into production and have gotten myself a working Postfix/Courier server but in the keystrokes to minor success I've now challenged my current thinking and wonder whether I've blurred the line between a local domain and hosted domain.

_NOTE: I've no DNS Server on my internal network_, I'm looking about the merits of setting one up but at this moment in time this is purely out of interest than necessity.

I purchase a domain from 123 Reg which I'll call from now on *mydomain.co.uk*, this has a DNS entry with 123 Reg that resolves to my static IP address issued from my ISP and the appropriate firewall rules on my own router allow in the services I desire.

However I've configured the hostname of my server as *myhostname.mydomain.co.uk* and my /etc/hosts file looks like this...

```

127.0.0.1       localhost.localdomain   localhost
127.0.1.1       *myhostname.mydomain.co.uk*     *myhostname*

```

I've had no issues at all with this config/approach and my web server is fully operational for my needs, its when I've reviewed the postfix documentation however that I'm now unsure.

**What caused me to question the above...**

My working mail server in a Virtualbox was sending mail out with the FROM address as *user@FQDN* which in my case was *user@myhostname.mydomain.co.uk.*  Reading the postfix documentation everything after the @ in the FROM address is populated by default using the contents of /etc/mailname which by default is the FQDN.  I corrected the issue in my test virtualbox by simply editing /etc/mailname to just contain *mydomain.co.uk *and as such emails now show they are FROM *user@mydomain.co.uk*.  I suspect the resolution in the case was the correct approach but this prompted me to revisit the postfix documentation and review what the Postfix *myhostname, mydomain* and *mydestination* values in /etc/postfix/main.cf should be.

If I've understood correctly the approach I need to take with Postfix is to follow the *Virtual Mailbox* route, I'll be purchasing an additional domain soon from 123 Reg and I'd like to have email from both domains on the one mail server.  As such using the *Virtual Mailbox* approach I can achieve this with Postfix, yet when I read the documentation for *mydestination* it very clearly states that you DO NOT put the names of the virtual domains in this parameter, they are specified elsewhere.

So what should I specify in the Postfix config for *mydestination ([http://www.postfix.org/postconf.5.html#mydestination](http://www.postfix.org/postconf.5.html#mydestination))?  *This is what confused me and what caused me to re-evaluate my internal hostname and hosts file configuration.

Should my localdomain be named just that to save the confusion...*localdomain, *thus my hostname would be *myhostname.localdomain*?
[LIST]
[*]If this is so then wouldn't my /etc/mailname default be incorrect and either need manually editing again or the value coded directly into /etc/postfix/main.cf?
[*]So my /etc/hosts file now look like this...
[/LIST]
```
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       *myhostname.localdomain*     *myhostname*
```

Think I'll stop waffling here and let those who actually know about this give me some guidance. :confused:

Thanks,

K

---

### Post by smtp on 2013-04-04
Hello,

There is no problem to host additional domains on the same Postfix system.
A very good explanation could be find here: [http://www.postfix.org/VIRTUAL_README.html#virtual_alias](http://www.postfix.org/VIRTUAL_README.html#virtual_alias)
E-mail is complex. Please be careful to not become an open relay or any other spam source.

---

### Post by KillerKelvUK on 2013-04-04
> **smtp said:**
> Hello,

There is no problem to host additional domains on the same Postfix system.
A very good explanation could be find here: [http://www.postfix.org/VIRTUAL_README.html#virtual_alias](http://www.postfix.org/VIRTUAL_README.html#virtual_alias)
E-mail is complex. Please be careful to not become an open relay or any other spam source.

Hi smtp, thanks for confirming, I'm reasonably comfortable that Postfix with the correct configuration will deliver all my requirements  it was more in my exploration of its configuration that I started 2nd guessing my local host/domain config and its validity based on my needs.

---

