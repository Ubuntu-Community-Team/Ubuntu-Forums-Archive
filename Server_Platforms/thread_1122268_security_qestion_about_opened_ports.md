---
title: "security qestion about opened ports"
date: 2009-04-10
forum: Server Platforms
---

### Post by Lori700698 on 2009-04-10
I'm having all kinds of headaches and fun getting my first server set up, I'm almost done, I have a few more wrinkles to iron out so my train of thought today went in a different direction.  What kind of security should I be doing?  Good security articles I should be reading about servers?
I started thinking about how many ports I opened up to get all this stuff running and now I'm a tad freaked that I should be doing something. I have all these ports opened from my router to the server to do different things.  I do want to mention that I'm still very new so please don't beat me up if I'm going about this all wrong, this is my home server nothing for production of any sorts.

FTP   		TCP 21     
SMTP 		TCP 25  
POP3 		TCP 110  
HTTP 		TCP 80  
DNS 		UDP 53 
Citadel Mail-ht TCP 8504 
HTTPS 		TCP 443 
Citadel-push 	TCP 504 
funambol 	TCP 8080 
POP 		TCP 995 
webmin 		TCP 10000 
ssh 		TCP 22 

Thanks for the advice!
Lori

---

### Post by Peasantoid on 2009-04-10
If it's just going to be a local sort of thing (no access to the outside world), I wouldn't worry. On the other hand, if it's public...
What servers/services are you actually using? Disable the ones you don't need and that will greatly harden your installation.

---

### Post by Lori700698 on 2009-04-10
I'm using almost all that stuff, I'm taking webdesign classes so I'm using the ftp and 80 ports for that.  I put in dns server so I'm using that, I also put in an email server with the funambol sync so I really am using almost all of it.  The 22, 1000 I will close up because I only needed them for a few days when I was away from home and working on the mail server.  I don't remember why I opened the 443 port and I'm may not need the 995 one open either, I will have to try that one again.

Lori

---

### Post by benanzo on 2009-04-10
Hi Lori,

In general you should run as few public services as possible.  The main concerns here are your MTA on port 25 and Webmin on 10000.  Make sure you configure Exim (if that's your mail server) to ONLY relay mail from systems on the local network or from pre-defined IP addresses.  Otherwise you'll be running an 'open relay' which means you'll soon be discovered and your server will start sending spam like nobody's business.  You can configure Exim's basic settings pretty easily with:

```

$ dpkg-reconfigure exim4-config

```

I wouldn't run Webmin all the time.  When I've used it, I just SSH in, start the Webmin service, connect over HTTPS, do my thing, then stop it when I'm done.  I've never had any problems with Webmin but I seem to recall there being some security issues in the past (which I'm sure have been fixed.)

I think the same goes for the rest of the services as well.  If they're not meant to serve some ongoing need then I would just leave them off and start them via SSH only when needed.

This reduces your attack surface thus reducing your exposure to external threats.

Good luck and have fun!

Ben

---

### Post by Lori700698 on 2009-04-10
I may not need 25 open, I'm not sure.  I had to relay my smtp to what citadel calls a smart host, that would be smtp.comcast.net (my internet service provider)  I couldn't send anything out by my own [email]from@mydomain.com[/email], comcast kicked it back with an error that said not with out a business account.

---

### Post by Lori700698 on 2009-04-11
I do need 25 open, I can send but not get mail with it shut.  I don't have exm4 installed.  citadel has it's own MTA, should I do something with it?  Now I'm really curious...Thanks for the eye-opener!

Lori

---

