---
title: "Intermittent client issues with Ubuntu Server"
date: 2005-12-10
forum: Server Platforms
---

### Post by DaveBentham on 2005-12-10
Hi

I am getting various network issues on a Win2K PC that connects to my Breezy Server.

My home network is very simple: my Breezy server, my wife's Win2K client and my Breezy laptop client. The Breezy server runs fetchmail/postfix/dovecot email services, ssh server, squid proxy, and shares a couple of directories via SAMBA.

There are times when the ssh client, email and folder shares just do not work from the Win2K; at other times they do work. I have not established any common set of circumstances between the good times and the bad times.

For example, we get 'ssh: ... connection timed out'. On Outlook Express, we get the error:

"Your server has unexpectedly terminated the connection. Possible causes for this include server problems, network problems, or a long period of inactivity. Account: 'Telekon', Server: '192.168.0.1', Protocol: SMTP, Port: 25, Secure(SSL): No, Error Number: 0x800CCC0F"

when trying to send emails. I get a very similar one for receiving emails: just POP3 protocol, port 110 difference.

The squid proxy has never had any problems.

Any guidance?

Thanks
Dave

---

### Post by DaveBentham on 2005-12-12
Hi 

I have now established the difference... I get these problems _before_ I run the Firestarter on the Ubuntu server. Now I thought Firestarter was just a frontend to iptables; but running Firestater seems to open up my network.

So after I run FS, the LAN works. I have no security issues on the home network side and it should always be open - which is how I configured the firewall on FS; why might so much closed before I run FS?

Dave

---

