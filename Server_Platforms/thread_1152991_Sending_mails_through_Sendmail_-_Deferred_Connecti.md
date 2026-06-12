---
title: "Sending mails through Sendmail - Deferred: Connection refused by [any_host]"
date: 2009-05-08
forum: Server Platforms
---

### Post by liko2k on 2009-05-08
Hi, 

I own a server and it is set up on public IP address. I have problems with sending emails wit sendmail. Im getting error like this one:

example error from logs:
 
 May 8 12:27:36 UTS sendmail[23120]: n45JUemL016426: to=<xxx@xx.xx>, delay=2+15:56:56, xdelay=00:00:00, mailer=esmtp, pri=35319380, relay=mx4.xxx.xx., dsn=4.0.0, stat=Deferred: Connection refused by mx4.xxx.xx.

I can add SPF entry for my domain. I did this: 

v=spf1 a mx ptr include:smtp.secureserver.net ~all

What should be the sendmail server config to take advantage of this?

maybe I have to do something in order to my server was identified by other mail servers (smtp) as a sever using my domain...


I have also this set up in my DNS control panel :

MX (Mail Exchange)           
    Priority     Host     Goes To     TTL     Actions
    10     @     aspmx.l.google.com     1 Hour
    
    20     @     alt1.aspmx.l.google.com     1 Hour
    
    20     @     alt2.aspmx.l.google.com     1 Hour
    
    30     @     aspmx2.googlemail.com     1 Hour
    
    30     @     aspmx3.googlemail.com     1 Hour
    
    30     @     aspmx4.googlemail.com     1 Hour
    
    30     @     aspmx5.googlemail.com     1 Hour

thanks for help!

---

### Post by liko2k on 2009-05-13
Any one can help me with it?:-k

---

### Post by a9k3d on 2009-05-14
You might want to run your domain through an online DNS checker. Also check reverse lookup of your IP returns either your domain or something reasonable. Anything that says dsl or dynamic in the domain name may get blocked.

---

### Post by TwiceOver on 2009-05-14
Forgive me if I am wrong...  It looks like you are hosting your email with google and sending from your server.  If this is the case, your SPF record needs to contain google.com instead of {yourdomain.com} even if you are using {yourdomain} with google.

Also you will need to forward your mail through the google smtp servers.  There is a guide that I used to do this, unfortunately I didn't bookmark it.  Do some google searching for postfix through gmail.

What is happening is the servers are doing a reverse MX lookup for your domain and seeing that it should be google, but instead is the IP you set up for your server... Which isn't part of google's network.

Again, maybe I'm wrong.  But your DNS MX records suggest you are using google domains for your email host.

---

