---
title: "ssl is not working"
date: 2012-07-18
forum: Server Platforms
---

### Post by associates on 2012-07-18
Hi,

I have been spending hours trying to figure out why I can't telnet my mail server (Ubuntu Server 12.04) via port 443 remotely. I do have firewall in place using APF from R-fx networks. I'm pretty sure I have opened up Port 443. Here is the snapshot of my APF
apf: {glob} opening inbound tcp port 443 on 0/0
apf: {glob} opening outbound tcp port 443 on 0/0

I have also checked to see if my apache2 is configured with ssl_mod enabled by running $ apachectl -M
I received "ssl_module (static)"

Now, what I am not sure of is whether or not that means my ssl mod is enabled.

I'm at a loss at the moment - don't know what else to check.

Any help would be very appreciated.

Thank you

---

### Post by CharlesA on 2012-07-19
Why are you trying to telnet via port 443? That is the port normally reserved for SSL.

If you want to check your mail server, you would normally telnet to port 25.

Check this out:
[http://articles.slicehost.com/2008/8/6/postfix-using-telnet-to-test-postfix](http://articles.slicehost.com/2008/8/6/postfix-using-telnet-to-test-postfix)

---

### Post by sandyd on 2012-07-19
> **associates said:**
> Hi,

I have been spending hours trying to figure out why I can't telnet my mail server (Ubuntu Server 12.04) via port 443 remotely. I do have firewall in place using APF from R-fx networks. I'm pretty sure I have opened up Port 443. Here is the snapshot of my APF
apf: {glob} opening inbound tcp port 443 on 0/0
apf: {glob} opening outbound tcp port 443 on 0/0

I have also checked to see if my apache2 is configured with ssl_mod enabled by running $ apachectl -M
I received "ssl_module (static)"

Now, what I am not sure of is whether or not that means my ssl mod is enabled.

I'm at a loss at the moment - don't know what else to check.

Any help would be very appreciated.

Thank you
Apache is not a mailserver, nor is 443 the standard mailserver port.

---

### Post by richpri on 2012-07-19
Is your mail server outside of the firewall?
Are you using a form of web mail?
If not then what mail client will you be using? [Telnet is not a mail client.]
What mail protocol are you using [SMTP, IMAP or POP]?
In general please provide as much information as you can.

---

### Post by associates on 2012-07-19
Thank you folks for your replies.

Why are you trying to telnet via port 443? That is the port normally reserved for SSL.

I just want to check if my port 443 is actually open or not. Yes, I know it's reserved for SSL connection. I have been trying to get my postfix TLS to work but have no luck so far.

If you want to check your mail server, you would normally telnet to port 25.
Yes, it is connecting fine when telneting port 25.

Is your mail server outside of the firewall?
I have installed APF - advanced Policy Firewall from Rxfn networks on my Ubuntu Server 12.04.

Are you using a form of web mail?
If not then what mail client will you be using? [Telnet is not a mail client.]
No, I use roundcube as my webmail. I am only using telnet to check if the port 443 is open. Don't know if this is the right way of checking a port.

What mail protocol are you using [SMTP, IMAP or POP]? IMAP and POP3.

I'm running postfix, dovecot (dovecot SASL) and roundcube.

Thank you very much

---

