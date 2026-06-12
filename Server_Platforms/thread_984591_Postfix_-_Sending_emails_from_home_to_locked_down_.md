---
title: "Postfix - Sending emails from home to locked down mail host"
date: 2008-11-16
forum: Server Platforms
---

### Post by spectre_25gt on 2008-11-16
I've got a Postfix mail server out on the net that I've got locked down quite well. It looks for forwards and reverse DNS entries, etc. and checks RBLs before it will accept mail from anyone. This is great, except that I'm setting up monitoring at a home location with a dynamic ip address and I need to get mail out to my server. I can't rely on my_networks because my home IP is dynamic and I can't do reverse look-ups, because my ISP won't set up my reverse DNS info. 

Has anyone else got a recommendation for a situation like this? I've got Postfix running on a server at my house, so I suppose I could use my ISP's server as a smart host, but I'd really like to keep to my own networks as possible. I looked into using TLS with a smart host, but it doesn't appear to be possible with Postfix.

---

### Post by MJN on 2008-11-17
Err.. client authentication (SMTP AUTH in particular).
 
Or have I misunderstood your question?
 
Mathew

---

### Post by spectre_25gt on 2008-11-17
The problem is that some of the clients I wish to use (my apc ups, for instance) are incapable of authenticated SMTP traffic. My thought was to set up a relay at home and have them talk to it, but I can't get the relay to speak to my main server via authenticated session. I guess postfix doesn't have that capability.

---

### Post by MJN on 2008-11-17
> **spectre_25gt said:**
> The problem is that some of the clients I wish to use (my apc ups, for instance) are incapable of authenticated SMTP traffic.Ah, okay.

> My thought was to set up a relay at home and have them talk to it, but I can't get the relay to speak to my main server via authenticated session. I guess postfix doesn't have that capability.It does. Check out the smtp_sasl_auth_enable, smtp_sasl_security_options and smtp_sasl_password_maps directives.

You will need set your relayhost to your offsite server and specify a username/password for that server in the password map referenced above.

Mathew

---

### Post by spectre_25gt on 2008-11-17
Excellent. That's exactly what I was looking for. Thanks!

---

### Post by MJN on 2008-11-18
No problem. Do post back if you need specific guidance with the implementation.
 
Mathew

---

