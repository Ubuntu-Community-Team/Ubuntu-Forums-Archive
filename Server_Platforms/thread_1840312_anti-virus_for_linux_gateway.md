---
title: "anti-virus for linux gateway?"
date: 2011-09-07
forum: Server Platforms
---

### Post by jewfromdahood on 2011-09-07
I have a linux gateway server for the company and want to know whats a good anti-virus program for the network traffic flowing through it? I have Winblows behind them and I need to protect it.

---

### Post by haqking on 2011-09-07
> **jewfromdahood said:**
> I have a linux gateway server for the company and want to know whats a good anti-virus program for the network traffic flowing through it? I have Winblows behind them and I need to protect it.


[http://www.kaspersky.com/anti-virus_mail_gateway](http://www.kaspersky.com/anti-virus_mail_gateway)

[http://wiki.untangle.com/index.php/Virus_Blocker#About_Virus_Blocker](http://wiki.untangle.com/index.php/Virus_Blocker#About_Virus_Blocker)

[http://www.untangle.com/Kaspersky](http://www.untangle.com/Kaspersky)

[http://www.eset.com/us/business/products/gateway-linux/](http://www.eset.com/us/business/products/gateway-linux/)

depends if you want free or purchase

---

### Post by jewfromdahood on 2011-09-07
I prefer the ESET one but every time I install the gateway security IT screws up the Ubuntu install. And then I have to completely reinstall the Ubuntu OS.

---

### Post by haqking on 2011-09-07
> **jewfromdahood said:**
> I prefer the ESET one but every time I install the gateway security IT screws up the Ubuntu install. And then I have to completely reinstall the Ubuntu OS.

bit vague ;-)

how does it mess things up ? error messages ?

at what stage ? what problems are caused ?

---

### Post by jewfromdahood on 2011-09-07
I'll try Virus Blocker... Looks promising

---

### Post by SeijiSensei on 2011-09-07
For email, I recommend [MailScanner]("http://www.mailscanner.info/").  It will use any commercial virus scanner as well as the free ClamAV.  It also has an interface to SpamAssassin to tag likely spam messages.  

For web traffic, I've been looking into [SquidClamav]("http://squidclamav.darold.net/"), which is an add-on for the [Squid]("http://www.squid-cache.org/") proxy server.  We push all the web traffic through a transparent Squid proxy which enables the use of ACLs to control what kinds of objects may be downloaded and which may not.  For instance, a simple ACL that blocks files that end in .exe, .com, and .bat keeps out a lot of potential malware.

---

### Post by jewfromdahood on 2011-09-07
> **haqking said:**
> bit vague ;-)

how does it mess things up ? error messages ?

at what stage ? what problems are caused ?

It just gives me the the text boot and says something like "daemon not running" or similar. I'll make a VM of Ubuntu within Ubuntu and see what I get as I am not doing that again

---

### Post by michaelb28 on 2011-09-08
Some years ago, I used the AVG Linux server edition.  I'm not sure if it'll be suitable for your purposes, but you can check it out.

---

