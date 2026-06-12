---
title: "Unbunto Server 12.04"
date: 2013-01-30
forum: Server Platforms
---

### Post by nightfly13 on 2013-01-30
I already setup an server with ubuntu server 12.04...
 
Like i have an dinamic Ip i setup an no-IP account and everything works fine when i install and configure my sites, now i have my site working properlly...
 
The only think it's not working is the email, for example, if i install, for example, osCommerce, when one customer made an order, the customer must receive one email with the order, this is not happening... I Add an MX Record on my domain registar pointing to my no-ip account, on my home router i forward the smtp port to 25 and pop port to 110, even if i configure the outlook i can send and receive emails... But for any reason the site itself (oscommerce) it's not sending email's using php function mail() or smtp...
 
I use for this server instalation, the perfect ubuntu server 12.04 ...
 
 
 
Anyone can tell me what, or suggest what is the issue, and what i can do to solve this????
 
 
 
Best Regards
João

---

### Post by volkswagner on 2013-01-30
You need to check your mail logs for errors, even /var/log/messages may contain help.

OS commerce has a couple settings:
[LIST]
[*]How to send mail (smtp or sendmail)
[*]Send mail (true or false)
[/LIST]

Please run a sendmail test from the command line.  Are you sure sendmail is installed?  Please post link of actual how-to that you followed.

---

