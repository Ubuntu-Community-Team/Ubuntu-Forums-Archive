---
title: "Need help determining server(s) configuration (what on which box)"
date: 2008-06-16
forum: Server Platforms
---

### Post by tuproxy on 2008-06-16
I'm in the process of setting up a whole new Linux network.  

I want to have the following:
Router
Firewall
NAT
QoS
DMZ (Maybe)
IDS 
Tripwire
DHCP
DNS
LDAP
FTP server
Samba server
backup server (bacula)
Squid
Apache
MySQL
PHP
Email (what is the best for industry/business)
VMWare Server (maybe on a lone PC)
PBX of VoIP
OpenVPN

I'm planning on making all of this a major learning experience for learning Linux administration.  I can't think of anything that I missed here.  What server/service did I miss, lol?  Did I get most of the popular services that could be run in a business/production enviornment?

I have 3 boxes that I can use and want to see how you guys would break up the installations.  I think the router/firewall should be left alone on one PC (maybe add squid too?)
So here they are:

Box 1 - P3 1ghz  384mb ram 80gb HD in RAID1
Box 2 - P3 1ghz  256mb ram 40gb hd in RAID1
Box 3 - P4 2.53ghz, 2gb ram (5 500gb hd's), 2 36gb Raptors, 2 76 GB   Raptors, the raptors can be raided, mirrored and striped?

So what would you put on which box?  THANKS A LOT!

---

### Post by HalPomeranz on 2008-06-16
Box 2 becomes your firewall/router running: IP Tables (firewall and NAT), Snort (IDS), Squid, OpenVPN, and whatever you want to do QoS-wise (though QoS is probably unnecessary for your Internet connection)

Box 1 can be your web server: Apache, MySQL (though I'd recommend Postgres instead), PHP, and FTP if you insist

Box 3 becomes the "infrastructure server" for your network and runs everything else.  You can run some of the services inside of VMware Server if you want to get the hang of that.

You also asked which email server is best to learn in terms of getting industry experience.  I'd recommend Sendmail-- though it's complicated and cantankerous it's also the most flexible once you understand how to configure it and it's what large enterprises with serious email problems use.  If you want something easy for your first brush with email, then stick with Postfix.

If you decide to go with Sendmail, there's a tutorial available from my web site:

[http://www.deer-run.com/~hal/dns-sendmail/Demystifying-Sendmail.pdf](http://www.deer-run.com/~hal/dns-sendmail/Demystifying-Sendmail.pdf)

Good luck!

---

### Post by tuproxy on 2008-06-17
Thanks for the response!  I think you are on the same page that I am.  

Do you know anything about PBX's?  I only need 2 lines, so ~64K of bandwidth, which I'm guessing isn't much CPU power.  

Does sendmail have a webmail interface? Does it allow for quota sized email accounts?  How is it compared to Exchange?

---

### Post by HalPomeranz on 2008-06-17
> **tuproxy said:**
> 
Do you know anything about PBX's?  I only need 2 lines, so ~64K of bandwidth, which I'm guessing isn't much CPU power. 


I haven't played with Asterisk at all, so I don't have any guidance for you here.  Sorry. 

> **tuproxy said:**
> 
Does sendmail have a webmail interface? Does it allow for quota sized email accounts?  How is it compared to Exchange?


Sendmail is purely a "Mail Transfer Agent" (MTA for short)-- it routes email around your network and across the Internet using a protocol called SMTP (Simple Mail Transfer Protocol).

If you want webmail, that's a separate package and there are many to choose from.  The "old reliable" is a package called Squirrelmail.  Some folks I know have been playing around with a newer webmail package called Roundcube and it looks pretty good.  There are plenty of others to choose from.

You'll also probably need to set up a POP/IMAP server to allow the webmail interface (and other mail clients like Evolution and Thunderbird) to access user mailboxes on your mail server.  The current de facto standard is Dovecot.

---

