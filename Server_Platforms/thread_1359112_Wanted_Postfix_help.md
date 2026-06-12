---
title: "Wanted: Postfix help"
date: 2009-12-19
forum: Server Platforms
---

### Post by kadeous on 2009-12-19
Good Morning,

 Before I pull out all of my hair, I wanted to try this again. I posted a few days ago but waited the full 72hrs for DNS propagation. Also I had my ISP setup the PTR record to point to my domain. No ports are blocked, and firewall is setup to allow those ports. 

So my issue now is that I still can't get e-mail from the internet. I've tested everything from this site and it all checks out ok: [http://www.mxtoolbox.com/SuperTool.aspx](http://www.mxtoolbox.com/SuperTool.aspx) it shows stmp working fine, and that I'm not a relay.

Solved: My broadcast setting was incorrect for the static IP.

---

### Post by linuxfrance on 2009-12-19
Hi 
first of all check your , /var/log/mail.log you may have some info there
here is a way to test your email server from outside or even inside 

you will use telnet to verify if everyting is working good 

```

telnet yourdomain.com 25  //you may use your public IP also 
HELO toto.com // normaly this the domain but I think it will be ok whatever you write
MAIL FROM:<user@anydomain.com>
RCPT TO:<existing_user_account_on_your_server@yourdoamin.com>
data
some text here

.   // type a point to send tha mail 


```

le me know  the result of this test

---

### Post by kadeous on 2009-12-19
Thanks for the reply.

I checked the mail logs and they don't show any external connections. Except from the website I tested smtp from, it shows that and denies the relay. As for telnet I've done that and it all worked out fine.

---

### Post by linuxfrance on 2009-12-19
when you checked the smtp or when you did the telnet test did you use the public IP or the DNS name ?? to be sure that the MX , DNS is working you must not use the public IP

---

### Post by kadeous on 2009-12-19
I used the domain name and connected fine.

I called the register and confirmed all settings and they are all also propagated.
I called the ISP to check the gateway/firewall and all is clear on that side.
PTR record was setup and propagated.

 I'm just puzzled now.

---

### Post by linuxfrance on 2009-12-19
your are right the DNS is ok , I just checked it now
can you give me a vaild test mail address I will try to send it using telnet 
and post me the log file .

becarfull ; don't post password if they included in the log file

---

### Post by kadeous on 2009-12-19
[email]test@speakyourtoon.com[/email]

Try that one

---

### Post by kadeous on 2009-12-19
removed information for log

---

### Post by linuxfrance on 2009-12-19
OK , I sent you 2 email 
one from Houssam ,another from linuxfrance 

could you post the last 5 min of the log file please

---

### Post by linuxfrance on 2009-12-19
yes it is normal to be detected as spam as the IP Is is not the same as the one of hotmail
did you get the second mail 
do u have any linuxfrance in the log ???

---

### Post by kadeous on 2009-12-19
nothing from linux address in the log

---

### Post by linuxfrance on 2009-12-19
ok , I will send you another mail , but pls dont post the log here , just tell me if you get something from houssam 
give me 2 min I will send it from my server to see the log

---

### Post by kadeous on 2009-12-19
Just wanted to let you know, my logs are showing no activity. So if you sent it recently I haven't received anything.

BTW - I really appreciate your help with this.

---

### Post by linuxfrance on 2009-12-19
you are welcome , I will modify my server to config , for the moment I send email using the smtp of my provider 

the first test show that it send the mail 
give me 2 min pls

---

### Post by linuxfrance on 2009-12-19
hummm , I think I found it :P let me check one thing more 
BRB

---

### Post by kadeous on 2009-12-19
NP take your time :) *cross fingers*

---

### Post by linuxfrance on 2009-12-19
Ok here we go 
it is a mater of DNS and MX 
the public IP address for mail.speakyourtoon.com is not the same as what mail server search 
I will PM you with the LOG .
Could please edit your previous post and put XXXX for my public IP frtom the telnet test

---

### Post by linuxfrance on 2009-12-19
this is agood tool to test sfp dns mx , cname , ...

[http://www.checkdns.net/powercheck.aspx](http://www.checkdns.net/powercheck.aspx)

I can help you with ur MX if you want  
let me Know

---

### Post by kadeous on 2009-12-19
sent ya a PM

---

### Post by linuxfrance on 2009-12-19
ok 

if you log to the host provider , you must have something like DNS setting or Advanced settings , you must have a field called MX 

the MX field must have an ip equal to the public IP of your mail server 

let me know if this is clear

---

### Post by kadeous on 2009-12-19
I changed all of that around, they had A records pointing to their server so that was messing things up, rechecked with the site you provided and everything passed. Now to see if I can get some mail.

---

### Post by linuxfrance on 2009-12-19
I can help you with a remote session if you want , like teamviewer or spark angles 

but here is whu you have to know  about the record 

the MX is for the mail server
the A record is for your web server 
you can define different proirity for the mx or the record
ex 
you can config 2 MX with 2 different public IP  , when an incoming mail happen 
it will try the first , if it did not work it will try the scond

---

### Post by linuxfrance on 2009-12-19
Glad to hear this , notic that it can take up to 2 hrs to be know by some DNS server

---

### Post by kadeous on 2009-12-19
Linuxfrance solved my problem, thank you so very much.

---

