---
title: "A new mail server"
date: 2007-12-05
forum: Server Platforms
---

### Post by xzased on 2007-12-05
Hiya all. We are trying to setup a mail server at work. This is the first time I try to setup a server, so I have no clue on how to. I have read all the documentation, and feel comfortable doing it, but I still have some basic questions:

1.- What type of connection do I need? Do I need a public IP? 

2.- I want to setup a firewall, but cant decide between shorewall or firestarter.. I dont have enough experience with both.

3.- Should I name my machine [www.domainx.com](www.domainx.com) or can I use a generic name like cat or something.

Sorry, I know these are pretty much dumb questions. Thanks

---

### Post by crouton on 2007-12-05
1) You may already have a public IP if you host your webserver, FTP, etc in your office or wherever the mailserver is going to be installed.  You can update your DNS records so that mail will go to this public IP address, or you could get another public IP.  Your choice.  

2) You may have a firewall already if you are using a router/dedicated firewall device (Cisco, Watchguard, etc).  

3) You will want an externally resolvable name if you intend to have people outside your business send emails to you.

There's a lot of information missing from your introduction that would help us help you.  Do you have a domain and control DNS for it, are you the network administrator or just an employee wanting to setup a mail server, etc.

---

### Post by mellowd on 2007-12-05
You don't have to have a public IP address, as long as your company firewall can either have some sort of VIP or MIP pointing to your mail server.

Also, you'll need to set up MX records through DNS as well as possibly reverse DNS entires.

For extra secutiry you can also set up PTR records through DNS

---

### Post by xzased on 2007-12-05
Thanks for your reply Mr. Crouton. 

Well, things go like this:
Im the new IT guy for a small law firm. The owner has another business. About 6 months ago he acquired a building for the other business and the IT guys moved there. They hold our mail server but not our webserver... so they hired me, an illiterate, to maintain the windows server. But since our mail server receives little attention, we are trying to put up our own.

"3) You will want an externally resolvable name if you intend to have people outside your business send emails to you."

Sorry, is that a yes or a no? :(

---

### Post by crouton on 2007-12-05
It sounds like your mail server is owned by the other business, and you want to bring that into your law firm instead?  If this is the case, you will need to setup your mail server, make sure it can get to the Internet, update your MX record like *mellowd* suggested above, and that should do it.  

#3 means: because your mail server is intended for emails to other people outside your business, you want to make sure that other servers can talk to it with a minimum amount of trouble.  You could name your server 'cat' but it'd cause a lot of problems.  Naming it 'mail.domain.com' or anything with a Fully Qualified Domain Name (FQDN) will make any potential troubleshooting much easier.  

DNS is your primary concern after getting the server set up; without it, mail will not know that it should be delivered to your new mail server.

---

### Post by xzased on 2007-12-05
I see... Thank you guys for your help. Im all set now :guitar:

---

### Post by HermanAB on 2007-12-05
Here you go: [http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

---

