---
title: "Citadel outgoing mail setup"
date: 2008-08-08
forum: Server Platforms
---

### Post by njschwartz on 2008-08-08
So after failing miserably with postfix I decided to go the all in one route and installed citadel.  All went well and I am able to receive mail without issue.  However, I am unable to send mail to anyone except other local citadel users.  All messages sent to external e-mail seen to time out in the outgoing SMTP que. I assume I have some sort of routing setup incorrectly but I cannot find a good tutorial for citadel and I don't personally understand enough about how e-mail works to solve this one on my own.  Any suggestions on where to go from here would rock.  Also, one other quick question.  Is there a web based option accessible from any computer anywhere for accessing my e-mail?  Any recommendations?  Thanks all for the assistance. 

Nate

---

### Post by windependence on 2008-08-08
You may have to open port 25 on your firewall or router or both.

As I understand it, Citadel has a web mail client built in. I would have to read the documentation to see how to enable it though. There is a user here by the name of HermanAB I think who is really good at Citadel.

-Tim

---

### Post by devonps on 2008-08-09
Hi,

I've just completed a succesful build of Citadel and this is what I did:

There are 2 parts to this:

First make sure the following ports are open:

25 - SMTP
110 - POP3
143 - IMAP
80 - HTTP (used for webcit - read webmail)
995 - POP3 - secure
993 - IMAP - secure
443 - HTTP - secure

Secondly,

1. log on as your mail administrator
2. click on the Administration button
3. click on the link Domain names and Internet mail configuration 
4. under the smart hosts option add in your SMTP server.
5. click on the add button
6. Restart the Citadel server using the Restart Now link

BTW: I used my ISP's SMTP server

Finally - I've assumed you've setup your A & MX records with your Domain Registrar.

Hope that helps,

Steve.

---

### Post by njschwartz on 2008-08-09
Ahh~there is the step I think I was missing.  Adding my ISP's SMTP server to the citadel setup.  I am at work, but I will try it when I get home.  I am guessing that will solve my sending problem.  The last thing I need to figure out is how to get the webmail part working.  I can get to webcit using localhost:2000 (that is the port I setup when I installed since I use Apache is using 80, I need another server :) lol)  Wen I try to access webcit outside the network it just times out.  I am forwarding port 2000 to my servers internal ip but to no avail.  I will keep trying.  Thanks for the advice!

---

### Post by windependence on 2008-08-09
Well, I guess you could do that but then what is the point of having a mail server? It should work with it's own smtp.

-Tim

---

### Post by njschwartz on 2008-08-09
Hmm, that is a good point.  So I assume then the reason mine isn't working it likely do to a DNS issue correct?  I will recheck my settings.

---

### Post by windependence on 2008-08-09
I just set one up today on a VM. I'm still playing with it so if I come across any ideas, I'll let you know. Good luck!

-Tim

---

### Post by artcancro on 2008-08-09
> **njschwartz said:**
> Hmm, that is a good point.  So I assume then the reason mine isn't working it likely do to a DNS issue correct?  I will recheck my settings.

njschwartz: there's a step-by-step troubleshooting guide on the Citadel web site for nailing down problems with outbound delivery:

[http://www.citadel.org/doku.php/faq:troubleshooting:outbound_mail](http://www.citadel.org/doku.php/faq:troubleshooting:outbound_mail)

Citadel doesn't rely on any special integration to get outbound mail working -- it just opens up SMTP connections and fires away.  So when there's a problem getting mail to the Internet it's *usually* a problem with either DNS resolution or completing outbound connections to port 25 on remote servers (often due to ISP's that block port 25).   Follow the above guide and you'll either zero in on the real problem, or at least rule out most of the usual culprits.

As for inbound connections to your WebCit service -- as someone suggested above, that's probably an issue with getting the port forwarded to your Citadel system.

---

### Post by njschwartz on 2008-08-09
Well I am pretty certain it is my BIND DNS server that is the problem.  I know that my ISP isn't blocking port 25 so I am good there.  That guide btw appears not to work.  Here is a really really stupid question for everyone.  I have a server and a few other computers connected to a router.  The internal ip of the server is 192.168.11.200  the external provided by my ISP is 203.82.115.213  When creating my bind zone files and lookups etc., which IP address am I using for things like the server and the reverse lookup?   I realize that is probably a complete noob question but I just want to be sure I have it right. Thanks!

Nate

---

### Post by devonps on 2008-08-10
> **windependence said:**
> Well, I guess you could do that but then what is the point of having a mail server? It should work with it's own smtp.

-Tim

Forgot to mention - my ISP blocks outbound mail - so that's why I've chosen to use their SMTP.

---

### Post by artcancro on 2008-08-10
> **devonps said:**
> Forgot to mention - my ISP blocks outbound mail - so that's why I've chosen to use their SMTP.

In that case you need to add their SMTP server as a smart-host.  Go to the Internet Mail Configuration screen and put its name in the smart host box.  If it requires authentication, you can do user:pass@host syntax.

---

### Post by jamesrfla on 2008-08-11
For some odd reason today I was using webcit and sending mail to a @gmail.com address and it didn't work. I have already port forward port 25. So I try to send mail to my @embarqmail.com address and it worked and then I tried my @gmail.com again and it worked. I am not sure what I changed or did. Dose anybody know what a Masqueradable domains is?

---

