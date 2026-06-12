---
title: "Configure a mail trasfer agent server only to run php mail()"
date: 2015-09-08
forum: Server Platforms
---

### Post by dam034 on 2015-09-08
Hello everyone,


I have a VPS and I installed Webmin, and I need this VPS to make a LAMP server.


I installed the LAMP server with no problems with this command:
```
[COLOR=#333333]tasksel install lamp-server[/COLOR]
```
And everything went as planned. Now what I need is to configure PHP for sending email through its mail() function. I have read [this page]("http://wiki.ubuntu-it.org/Server/Mail") in my language and to tell the truth I did not understand what to do.


I do not need a program to store the emails then will download on my client, but just the minimum program to run PHP mail().


I have to install only the server MTA? And then how do I proceed?


Thanks,
dam034

---

### Post by TheFu on 2015-09-09
Generally, you need an MTA to send email. There are many options.  ssmtp is popular if a single userid will be used to send. Postfix is normally used for full email operations.

Email will be refused from most DHCP IPs on the internet, so an email gateway from a service provider will need to be configured. The details are different based on the ISP and/or server VPS provider.

---

### Post by dam034 on 2015-09-09
I also read elsewhere that Postfix is the right program for me, but I have not yet installed it because then I would not know how to configure it to work in PHP mail().


Could you do for me a stepladder or show me examples of configurations of LAMP server with sending emails (even the server of this forum)?

Then could you explain in more detail the rejection of emails from DHCP IPs?




Thanks,
dam034

---

### Post by TheFu on 2015-09-09
> **dam034 said:**
> I also read elsewhere that Postfix is the right program for me, but I have not yet installed it because then I would not know how to configure it to work in PHP mail().

Could you do for me a stepladder or show me examples of configurations of LAMP server with sending emails (even the server of this forum)?

Then could you explain in more detail the rejection of emails from DHCP IPs?

We don't use php or apache or mysql here, so I can't help with those things.

As always ... 
* what have you tried? (posting a config would be helpful)
* what are the errors? (copy/paste any **RELEVANT** errors)
* what do the log files show? Log files are full of information. Almost every server process will log something for errors and warnings. Many also log information. Log files are in /var/log ... somewhere below there. Please do not post entire log files unless specifically asked. Only RELEVANT parts, usually 15 lines or less.

Those are common troubleshooting steps for all Linux server issues. 

**Why block DHCP subnets?**
There is much spam in the world. Before email admins world-wide started blocking emails from DHCP subnets, it was 20x worse.  If mail originates from a domain hosted on a DHCP subnet, email admins of the world will block delivery. I do.  The way around that is to have a static IP if you want direct delivery or to use the service provider's email gateway - this is how big ISPs do it.  This is for server-to-server email - pure SMPT. 

Authenticated client email is different - that's why people use their gmail/ISP/yahoomail/hotmail account to send email from home (most homes are on DHCP subnets).

I don't know what you mean by stepladder.  Running an MTA is trivial. It is the easiest of the old-school protocols.  The hard part is making it talk with the rest of the world, thanks to spammers.  Yesterday, my front-end email server blocked over 600 emails to just my account which were from spammers trying to send from DHCP and other known spammer subnets. 

In Windows, any program that wants to send email has always had that email code included.

In Unix, 98% of programs that want to send email uses the system MTA already on the box.  That assumes the admin setup an MTA. Otherwise, no email can be sent. There are 5-10 popular MTAs, each have a different purpose. Decide which fits your needs and install, then configure that system following the instructions. MTAs can
* send
* receive
* forward
* relay
* alias support and
* manage queues
A few other things are possible too. If you just want to send email, from 1 account thru some external email, like [gmail, then ssmtp]("https://wiki.archlinux.org/index.php/SSMTP") is probably the program you want.

I did a web search for "ssmtp php_mail". It found some stuff. Have you tried it already? There have been a few sSMTP questions in these forums which might help too. Review those.

Good luck!

---

### Post by dam034 on 2015-09-10
> **TheFu said:**
> We don't use php or apache or mysql here, so I can't help with those things.
All right, thanks anyway.
> **TheFu said:**
> As always ... 
* what have you tried? (posting a config would be helpful)
* what are the errors? (copy/paste any **RELEVANT** errors)
* what do the log files show? Log files are full of information. Almost every server process will log something for errors and warnings. Many also log information. Log files are in /var/log ... somewhere below there. Please do not post entire log files unless specifically asked. Only RELEVANT parts, usually 15 lines or less.
I just installed postfix without setting him or PHP for the proper functioning of mail(). This is because I don't know how to move and I don't want to combine damage, in fact why I wrote here because I want to know how to proceed now. I want to set postfix to only send emails from PHP mail().
> **TheFu said:**
> 
**Why block DHCP subnets?**
There is much spam in the world. Before email admins world-wide started blocking emails from DHCP subnets, it was 20x worse.  If mail originates from a domain hosted on a DHCP subnet, email admins of the world will block delivery. I do.  The way around that is to have a static IP if you want direct delivery or to use the service provider's email gateway - this is how big ISPs do it.  This is for server-to-server email - pure SMPT. 

So if I use the VPS in my home, the emails will be blocked? And if I use the VPS of a hosting company (with static IPs) in my country?
> **TheFu said:**
> 
A few other things are possible too. If you just want to send email, from 1 account thru some external email, like [gmail, then ssmtp]("https://wiki.archlinux.org/index.php/SSMTP") is probably the program you want.

I did a web search for "ssmtp php_mail". It found some stuff. Have you tried it already? There have been a few sSMTP questions in these forums which might help too. Review those.
So you're telling me that if I need an MTA only for PHP mail(), I can use ssmtp instead of postfix?


Anyway thaks for all the time you're dedicating for me.



Thanks,
dam034

---

### Post by TheFu on 2015-09-10
Linux is flexible. There are 50-500 different ways to solve any problem. How to do it best is up to the admin. There are subtle differences in each solution and only you can pick the best one for your situation - especially over a forum.

I don't know anything about your "home" network or about your the "VPS of a hosting company in my country", so I cannot say whether emails will be allowed or not.

MTAs on Unix do not work for just 1 program. They are system services that any program can use. There may be ways using SELinux or apparmor to limit which programs can send messages to the MTA - that I don't know how to do.

Only 1 MTA can be active on any machine. sSMPT is usually  what people use who only want to send outgoing mail.  Postfix is usually what people use who want to send AND receive email. I use postfix in "send-only" mode as a "satellite email server" which sends all emails to a central email server that I run. If you don't run a full email server and don't intend to, then postfix might be more effort than desired. That is your decision.  

Improperly configured email servers are a good way to get hacked. Do your research before setting up an email server. There are lots of example config files for accomplishing different tasks on the internet.

I know you are fixated on php-mail - but that isn't how Unix email works.  OTOH, I have ZERO idea how php-mail works. What do other people in the php community use for this?

---

### Post by dam034 on 2015-09-10
> **TheFu said:**
> Only 1 MTA can be active on any machine. sSMPT is usually  what people use who only want to send outgoing mail.  Postfix is usually what people use who want to send AND receive email. I use postfix in "send-only" mode as a "satellite email server" which sends all emails to a central email server that I run. If you don't run a full email server and don't intend to, then postfix might be more effort than desired. That is your decision.

[...]

Improperly configured email servers are a good way to get hacked.
When I installed postfix, I chose the Internet option because I want to use the program in "send-only" mode, but without the support of another mail server. Well, could you help me configure postfix (main.cf and others) to make it work well and without hacking issues?




Thanks,
dam034

---

