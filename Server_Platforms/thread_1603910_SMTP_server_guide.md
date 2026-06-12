---
title: "SMTP server guide"
date: 2010-10-23
forum: Server Platforms
---

### Post by canoemoose on 2010-10-23
Hi all,
I'm in need of some kind of SMTP solution.  My ISP's SMTP server is only accessible if I'm connected to one of "their" connections - fine for when I'm at home or at a friends' who uses the same ISP, but pretty hopeless for when I'm travelling or for my Android phone.
I have a server on my home network, currently running OpenVPN for remote access to my network + some internal Samba shares, local DNS, DHCP etc.  I'd like to add some kind of SMTP functionality to it, so I can use it as my SMTP server, wherever I am.  As the server is always going to live in the same place, it could just pass the mail along to my ISP's server.
sSMTP seems to do this.  However, nothing seems to explain how to set this up so I can access it externally and using TLS encryption between me and my server.  Any ideas/other suggestions?

---

### Post by SeijiSensei on 2010-10-23
I'd just install Postfix (the default Ubuntu "mail transfer agent") on the server and connect to it over the VPN.  You needn't worry about TLS or other secure systems for email since you're already encrypting the traffic with OpenVPN.

However this may not work at all if your ISP blocks outbound SMTP connections using port 25.  If so, you can have Postfix forward all mail to the ISP's server for final delivery by adding the entry

relayhost = isp.smtp.server.name

to /etc/postfix/main.cf.  You'll probably need to add the VPN's network address to the "mynetworks" list in that file as well.

Does the ISP filter out mail with From addresses outside the ISP's domain? If the ISP accepts all mail from the networks it serves regardless of the addressing format, this should work for you.

Good starting point for Postfix: [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

---

### Post by paulsp on 2010-10-23
If you just want a universally accessible SMTP server, you can also get a subscription from a company that offers just that. Quick Google search yields:

[http://www.authsmtp.com](http://www.authsmtp.com)
[https://www.smtp2go.com/](https://www.smtp2go.com/)
[http://www.smtp-server.com/](http://www.smtp-server.com/)

Costs a few dollars a month, but might be the fastest and easiest solution.

---

### Post by canoemoose on 2010-10-24
@SeijiSensei:
That config guide looks like what I'm looking for, thanks!

I've set up Postfix, and the syslog shows that mail is being routed correctly and then removed from Postfix's queue.  However, it never reaches its recipient.  How can I troubleshoot this further?

@paulsp:
Free is good - I'm a student :P
That's why I run my own server.

EDIT: Relaying the mail via my ISP's SMTP server solved the problem, despite the fact they claim not to block traffic on port 25.

Now I need to work out how to set up SMTP-AUTH and TLS so I can send mail without having to be logged on to my VPN (eg from my phone).

---

