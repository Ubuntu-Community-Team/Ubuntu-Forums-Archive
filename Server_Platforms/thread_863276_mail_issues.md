---
title: "mail issues"
date: 2008-07-18
forum: Server Platforms
---

### Post by darkorical on 2008-07-18
I am trying to set up a ubuntu server to ... do a lot of stuff and one of them is send email. Now I don't want it to be a mail server (already have windows SBS 2003 running an exchange for that)

alright a break down of what Im trying to do 

Query a data base Via php daily make reports for 5 different people based on the info returned from the query and then email said reports to the people. 

on my WAMP server I simply had to edit the php.ini  for The mail server that we use but I cant seem to get it working on my LAMP

All I keep finding is info on how to set up a mail server in my searches. so here I am again asking for help. 

so any suggestions / what info do I need to provide to get suggestions

---

### Post by darkorical on 2008-07-19
any thoughts from anyone?

---

### Post by ken22 on 2008-07-19
What did you change in php.ini?

Please post your php email code.

What happens when you run these scripts on the lamp?

---

### Post by HermanAB on 2008-07-19
Have a look for a forwarding only mail transport agent.  Nullmailer is a good one.  All it does, is forward mail to another server.
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

---

### Post by darkorical on 2008-07-23
> **HermanAB said:**
> Have a look for a forwarding only mail transport agent.  Nullmailer is a good one.  All it does, is forward mail to another server.
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

that worked perfectly thank you very much

---

### Post by darkorical on 2008-10-06
alright It did work perfectly for a while. but now it randomly stops sending and I don't know how to get it going again.
well I know a way, 
sudo apt-get remove nullmailer
followed by 
sudo apt-get install nullmailer

and that sends EVERYTHING it hasn't sent previously. which seems good but it was down for a week and a half before someone noticed and let me know. 

any advice on how to keep it doing its job better? or at least how to restart without reinstalling

---

### Post by darkorical on 2008-10-14
normally I dont like to bump and beg but I let this sit for a week and it ran back to page 14 and I still havent found a solution can someonoe please offer any advice

---

### Post by darkorical on 2008-10-15
anyone ?

---

### Post by lykwydchykyn on 2008-10-15
Have you checked the mail logs for errors, on both the exchange server and the ubuntu box?

/var/log/mail.log is a good place to start.

---

### Post by darkorical on 2008-10-16
according to the logs when it works it works just fine
but for some reason it suddenly stops pulling the trigger.

---

### Post by HermanAB on 2008-10-16
Why uninstall.  Can't you just restart nullmailer?

---

### Post by lykwydchykyn on 2008-10-16
Maybe try a different MTA.  I usually use postfix for relaying mail from servers, but just about any MTA will work.  Just don't use sendmail.

---

