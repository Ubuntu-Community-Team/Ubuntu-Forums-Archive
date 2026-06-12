---
title: "postfix or any other MTA to limit connections by client?"
date: 2017-01-24
forum: Server Platforms
---

### Post by mrredhat on 2017-01-24
I have a website that has a form submission webpage. Someone enters some info and it e-mails it off to the person specified in the webpage. I decided to setup a mail server with postfix and it works fine. Now, naturally, spammers like to hack those websites to spam other people. What I would like to do is setup postfix to limit the amount of connections that the client makes per day, hour, or whatever. 
 
You would think this would be a simple thing. I looked at policyd, but that seems like I need to install MySQL and bunch of other crap to get that working.  I just want a simple way to limit a host to sending e-mails through my one little server to about 25 e-mail messages a day.

I did see smtpd_client_connection_rate_limit the problem with that is that is as far as I can tell it doesn’t activate if you have the host in mynetworks. – Go Figure.
I’m not married to using postfix, but is there any simple MTA that I can use to limit the amount of connections per day by an IP address that doesn’t require everything and including the kitchen sink to be installed?

---

### Post by raja.genupula on 2017-01-25
Have you tried managing it directly from your code ?

I mean, once you received a request from a particular host place some temp counter for it and when host reaches it counter you can display a warning message. 

I have tried looking for it but no success. If you dont like above method , I hope others will help you. 

If you want to continue with finding client address from PHP it self , you can use below links

[http://stackoverflow.com/questions/3003145/how-to-get-the-client-ip-address-in-php](http://stackoverflow.com/questions/3003145/how-to-get-the-client-ip-address-in-php)


Thank you.

---

### Post by SeijiSensei on 2017-01-25
> **mrredhat said:**
> I have a website that has a form submission webpage. Someone enters some info and it e-mails it off to the person specified in the webpage. I decided to setup a mail server with postfix and it works fine. Now, naturally, spammers like to hack those websites to spam other people. What I would like to do is setup postfix to limit the amount of connections that the client makes per day, hour, or whatever.
If you have a page where a random person can specify a recipient address, you've given spammers a gift.  Trying to manage that situation with connection limits or whatever is just ignoring the fundamental problem.  Web forms should mail all their content to a fixed address, one that's hidden from the person using the form.  (I don't mean "hidden" HTML fields here which are exposed in the HTML code. The recipient address should only exist in the script code that processes the form.)

You need to rethink what you want to accomplish here so that you don't provide a tool for spamming.

---

