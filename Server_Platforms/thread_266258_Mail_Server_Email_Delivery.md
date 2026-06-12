---
title: "Mail Server Email Delivery"
date: 2006-09-27
forum: Server Platforms
---

### Post by jameso on 2006-09-27
Hi everyone,

A year ago I set up an email server (server1.mydomain.com.au) with postfix, courier IMAP, etc following the [HowToForge](http://www.howtoforge.com/perfect_setup_ubuntu_5.10) tutorial.

I have since changed the MX entry for my domain (mydomain.com.au), as I now want a different server (server2.mydomain.com.au) to handle the emails for my domain. I have also transferred all my emails to this new server.

I still host my web site on the server1 machine, which is almost working fine.

Everything email related is working fine (emails are delivered to server2), except that emails generated from server1 (eg php mail() or any cron job outputs) are delivered locally with this machine and delivered to my old inbox (on server1).

How can I change the config on server1 so that emails generated on this server are delivered to the mailbox on server2. 

The problem seems to be that the server1 machine assumes that it is the mail server for my domain, even after changing my mx records where my dns is hosted.

Any suggestions would be appreciated.

Regards,

James

---

### Post by jimm on 2006-09-27
Hi,

I am not sure, but I would suspect your server1 generated mails arent even hitting SMTP and are all being delivered via the local delivery mechanism OR the SMTP instance on server1 still has the mail server configured to deliver mail for your local domain and it is matching your local users so it can just deliver them locally.

If you have DNS working you can just cheat and change your cron and phpmail jobs to send mail to USER@SERVER2 that way it will always try the other system. OR you need to reconfigure the mail server on  server1 to not think it can deliver mail for your domain. i.e. reconfigure postfix (I am not a postfix expert so I dont know the config for it at all) so that server1 doesnt think it is the MTA for your local domain.

Let me know how you get on!

Thanks,
James

---

### Post by jameso on 2006-09-27
Hi James,

Thanks very much for your reply.

I would agree that the server1 emails are being sent via the local delivery mechanism.

I somehow need to tell postfix (?) to use my ISPs SMTP server, which would then deliver the mail (correctly) to server2.

Does anyone know how I can reconfigure postfix to do this?

Thanks!

---

### Post by darrenm on 2006-09-27
Change myorigin to be something other than the domain you want server2 to get mail for.

or just transport map to the other server.

---

### Post by jameso on 2006-09-27
I have had a look around in the postfix configuration, and made a few changes to /etc/postfix/main.cf:

I replaced the line:
myhostname = mydomain.com.au
with
myhostname = localhost

I also replaced the line:
mydestination = /etc/mailname, localhost.localdomain, localhost.localdomain, localhost
with:
mydestination = localhost.localdomain, localhost.localdomain, localhost

Then restarted postfix.

This seems to have convinced postfix that emails destined for mydomain.com.au should not be routed locally.

Thanks for the help!

---

### Post by darrenm on 2006-09-27
Just for info. A perhaps nicer way is to transport map the server. Edit /etc/postfix/transport and put 
```
mydomain.com smtp:ip.address.of.remoteserver
```
then
```
postmap /etc/postfix/transport
```
and check transport_map is 
```
transport_map = hash:/etc/postfix/transport
```

Which will force all mail for that domain to the other server.

---

### Post by jameso on 2006-09-27
> **darrenm said:**
> Just for info. A perhaps nicer way is to transport map the server.Thanks for that darren! I have reverted my config file and have set up the mapping as per your instructions, and everything seems to work fine!

Thanks very much.

---

