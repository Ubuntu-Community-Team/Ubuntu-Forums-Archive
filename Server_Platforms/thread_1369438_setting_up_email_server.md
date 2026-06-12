---
title: "setting up email server?"
date: 2010-01-01
forum: Server Platforms
---

### Post by rebeltaz on 2010-01-01
I am, and have been for a couple of years, running Ubuntu 7.10 Server to host my web site, which is registered through 1&1. Since this same computer also hosts two other web sites (one for me and one for a friend), I also run ISPConfig. 

As of late, I have become increasingly annoyed with my ISP (AT&T) email server. I would like to host my own email server. 

Can someone provide me with the steps I need to take to accomplish this? My first step, after backing up my current system, is to upgrade the server's distro. After that, I will require as much help as possible! :)

Thanks...

---

### Post by HermanAB on 2010-01-01
Howdy,

The absolutely easiest mail system to set up is Citadel.  It is a full featured system and is self contained, with an excellent Easy Install script.  There are three Citadel howtos on my web site at [http://www.aeronetworks.ca/linuxhowtos.html](http://www.aeronetworks.ca/linuxhowtos.html) but the best place to go is to the [http://www.citadel.org](http://www.citadel.org) web site, go to the download page and run the eay install script.

However, before you can set up a mail server, you got to have your DNS configured with A, MX and PTR records!

---

### Post by rebeltaz on 2010-01-01
> **HermanAB said:**
> 
However, before you can set up a mail server, you got to have your DNS configured with A, MX and PTR records!

Yeah... that's the part that I am going to have problems with. Most things I can figure out, but I'm having problems with that part. 

I will check out Citadel though.. Thank you.

---

### Post by HermanAB on 2010-01-01
One of the easiest ways to get a DNS and domain name configured is with godaddy.com.  Their online service is pretty fool proof.  The most difficult part is clicking past all the additional crap they want to sell you ;)

---

### Post by rebeltaz on 2010-01-01
> **HermanAB said:**
> One of the easiest ways to get a DNS and domain name configured is with godaddy.com.  Their online service is pretty fool proof.  The most difficult part is clicking past all the additional crap they want to sell you ;)

I've been with 1&1 for three years and it just renewed until 11-2010... Wow - 2010! Seems so odd...

---

### Post by volkswagner on 2010-01-01
Early steps to running mail server.

Hope you have a static IP address from your ISP.  If not, you may need to relay outgoing mail via your ISP's SMTP server.

Verify standard mail ports are open, via [canyouseeme.org]("http://www.canyouseeme.org/").

Check you IP against [Blacklists]("http://whatismyipaddress.com/staticpages/index.php/is-my-ip-address-blacklisted").

---

### Post by steven.jones on 2010-01-01
Check with AT&T that they allow incoming to port25 and outgoing to 25...you maybe able to smarthost off them for outgoing, but they may block other options.

regards

Steven

---

### Post by steven.jones on 2010-01-01
If you get this going do check you have not setup an open relay as that will chew your bandwidth, get you blacklisted & annoy AT&T.

Sendmail isnt that hard to setup...which is what I use, Ubuntu seems to install Postfix by default, that isnt hard either.

Once you do this you will also need (I asume) an Imap(s) server, I'd go with Dovecot, its very easy (at least in Debian, I wouldnt think Ubuntu is any worse). Then maybe webmail, squirrelmail uses Sendmail and Dovecot setup ssl self certs to do https: in apache2.

regards

 



regards

Steven

---

### Post by rebeltaz on 2010-01-01
Alright... I think I'm more confused now than when I started! :confused:

First, I _do_ have a static IP (hence the web server I run) which is not blacklisted as reported by the web site listed. 

I did a test on the canyouseeme site for ports 25, 110 and 145. Those came up as blocked, but is that because the ISP is blocking them or because I do not have a server serving those ports? 

What is an "open relay"?

---

### Post by noway2 on 2010-01-03
An open relay is an unsecured mail server that will allow anyone as a recipient.  An MTA like postfix works by receiving incoming mail on the SMTP server portion.  If the recipient of the message is for local delivery, it is then handled accordingly.  If the message is for a different domain, it is forwarded to the next hop, such as your service providers SMTP server.  So to prevent an open relay, you need to be sure that your SMTP server requires proper authentication.  This is handled in the configuration settings in main.cf.  There are any number of howto documents that will guide you through the process and ensure that you don't create an open relay.

---

