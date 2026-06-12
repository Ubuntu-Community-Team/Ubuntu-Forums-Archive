---
title: "Lync on Ubuntu"
date: 2015-09-23
forum: Ubuntu/Debian BASED
---

### Post by timonoj on 2015-09-23
Hi guys,

I'm trying to set up Lync running on my Ubuntu (well, Elementary OS) machine. So far Evolution syncs mail perfectly fine using the OWA address, so there's that, but I have questions plenty regarding Pidgin and sipe (is there any alternative?):

My office server uses OWA access, and that's how Evolution connects. Should I use that OWA address for the Lync settings? Or should I use the SERVER.domain.local? If so, how do I set where to establish the connection? Setting the http proxy to the OWA url?

So far I tried not typing any server and leaving only [email]user@domain.com[/email] as login. This times out. I also specified OWA.domain.com, and still times out. I can see it uses port 5061, but not sure if this is the standard one.

Huh...seems I'm getting closer. I used the exchange troubleshooter at testconnectivity.microsoft.com with the Lync option, to see whether my settings were validating. I got to see the port is 5061, and seems the address is sip.domain.com. It uses an SSL connection, which in piding I'm setting as TCP with TLS-DSK. If I set SSL instead of TCP it attempts to use port 443 and fails because it's blocked. 

> (10:47:39) sipe: transport_input_common: new buffer length 4096
(10:47:39) sipe: Read error: Connection reset by peer (104)
(10:47:39) connection: Connection error on 0x7fbe047b3a70 (reason: 0 description: Read error)
(10:47:39) sipe: Server has disconnected
(10:47:39) account: Disconnecting account [email]user@domain.com,user@domain.com[/email] (0x7fbe043038d0)
(10:47:39) connection: Disconnecting connection 0x7fbe047b3a70
(10:47:39) sipe: SIP transactions count:0 after removal
(10:47:39) sipe: sipe_schedule_remove: action name=<transaction timeout><BD3CgD8D7aE0F5iB548m31E6t76DAb91B4x14B7x><1 REGISTE

---

### Post by pmon on 2015-11-05
I have Lync working with Pidgin.  The steps I needed to take were:

Ensure corporate root certificate is in place.  I managed to achieve this using tutorials on the web.  TBH, this was the hardest part.
Used my company email address as the user name and my Active Directory login as the login.
Next tab, Server - entered the relevant Lync server FQDN.

I was fortunate in that our company messaging team were willing to assist by providing a copy of the root certificate and details such as the Lync server hostname.  Hope that helps...

Just as an aside, I am currently seeing odd behaviour with Pidgin.  It works fine when I remote onto my desktop Ubuntu machine using XRDP.  When I try to start it up logged in 'locally' it errors with an ssl handshake error.  I'm at a loss as to why that would be...

---

