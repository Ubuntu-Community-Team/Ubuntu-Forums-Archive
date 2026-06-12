---
title: "Apache &amp; SSL"
date: 2006-06-08
forum: Server Platforms
---

### Post by Ronbo on 2006-06-08
I am running a Dapper Lamp server with SSL for an intranet site at work, there are multiple departments in the county but want only one department to be able to access the site. I have setup SSL, so each time someone accesses the site it issues the certificate to them to encrypt the traffic over the network, if they don't already have it. I kind of want to have it work in reverse, I want to have the certificate already on the client computer in order to gain access, and if the certificate is not there I don't want it to be issued just to deny the connection to the directory and site. After a bit of searching I have added the following to my 'httpd.conf' file:

SSLVerifyClient require
SSLVerifyDepth 1
SSLCACertificateFile /etc/apache2/ssl/apache.pem

But even if the certificate has been saved on the computer from a previous connection it still won't allow access. Does the certificate have to be saved in another location on the client and if so whereabouts? 95% of the clients are XP computers and at least half of them use IE and the others use Firefox, so I actually am looking for how to configure each. Any help or direction of where I may find some help would be greatly appreciated.  Or if you have any other ideas on how to accomplish something similar that would also be good.

---

### Post by MJN on 2006-06-09
I've no experience of client authentication (only server side certs) however the HowTo at [http://www.vanemery.com/Linux/Apache/apache-SSL.html]("http://www.vanemery.com/Linux/Apache/apache-SSL.html") has been very useful for me and I see it includes client authentication section too so it might be worth a look?

EDIT: I see that it looks like you've configured Apache fine and you're looking more for help with configuring the actual clients? If so, perhaps the HowTo won't be of use after all however I'll keep it in in case it provides anything...

Mathew

---

### Post by Ronbo on 2006-06-09
I read the HowTo and it looks like what I needed.  I am going to give it a shot tommorrow or Monday when I get to work.  I'll post how I make out.  Thanks I appreciate the link.

---

### Post by LordHunter317 on 2006-06-10
Client side SSL certification means you've generated a SSL cert unique to the client and you authenticate off of that.  It doesn't mean you've downloaded the server's SSL cert to the client.  The server's SSL certificate has nothing to do with client SSL auth ever.

---

### Post by MJN on 2006-06-11
Indeed. I was assuming that we were talking about client-side authentication given that denying a client access based on it having a copy of a *public* server cert makes no sense.

Perhaps I've misread the OP's question? Rereading it now, it's starting to look like this is indeed the case - perhaps the OP can explain the rationale behind the desire?

Mathew

---

### Post by LordHunter317 on 2006-06-11
Well, what he wanted to try to do is allow access based on having a preexisting copy of the server certificate.  But you can't do that, that's impossible.

Indeed, he wants to do client SSL certification, and that's a fine solution to his problem.  But my statement was that it doesn't (nor can it, it's unpossible) work the way he thought it did.

---

### Post by Ronbo on 2006-06-13
I could generate an SSL certificate on each client, that would not be a problem, there are less than 20 computer that will have access to the site.  Do you know of any sites or documentation that would allow me to read up on this.  I was unaware that it would have to be done this way, and I couldn't use the servers certificate.  The reason for this is that there are going to be confidential reports on this server, we have several different units in several different locations and about 110 Officers who all need acces to this system.  The county has probably close to 50 different departments on the same intranet, each with there own domain server, I am trying to avoid the whole windows domain thing.  The site is done in PHP, where the reports are created, edited and viewed (PDF's).  The site is password protected, uses SSL (server issues the certificate) and I will be setting it up behind a firewall, hopefully.  I just figured that client side authentication would just provide one more level of security being that if the clients did not have the certificate installed, and it would not be issued by the server, then they wouldn't even get to the point of entering the username and password.  I am kinda new to the whole SSL thing so I figured someone here might have a better handle on this and give me some direction.

---

### Post by MJN on 2006-06-13
It sounds to me like you're already there. There's no additional security from denying a client access if it doesn't already have a copy of the server's public certificate - that's the whole idea behind the public cert, it's freely distributable and there's nothing stopping someone from copying this cert off one client to another. So, again, there's no security benefit in trying to enforce this (as LH says, there's no configuration that'll do this - it's simply not designed to).

You say the site is username/password protected and the server only delivers the content over SSL (encrypted) - is this not sufficient security? If not, then issuing individual client (/user) certificates is the only next step - but as you say it will mean an additional administrative overhead.

Security is all about risk assesment and managing/mitigating those risks. Nothing can be 100% 'secure'. Ask yourself how secure this data needs to be and then build the security around it - username/password over SSL is pretty darn good. Sure, no use against a keylogger, hidden camera, blackmail etc etc but then that's where the risk assessment comes in - what are the risks and how much do you need to do to mitigate them to an acceptable level?

Mathew

---

