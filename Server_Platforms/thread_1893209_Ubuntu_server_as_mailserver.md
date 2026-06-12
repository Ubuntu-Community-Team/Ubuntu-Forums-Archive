---
title: "Ubuntu server as mailserver"
date: 2011-12-09
forum: Server Platforms
---

### Post by Teslafan on 2011-12-09
Hi there guys.

I'd like to have your guidance on a project i'd like to build in the company i work for.

Currently we are using an email service that is directly tied to our ISP, however i think that internal emails traffic should be kept inside the intranet and not travel to our ISP mailserver and then sent back to the computers in our offices. On top of that, some of our administrators are abroad most of the time, and for them to be able to send emails a special password was issued by our ISP so they can bypass the "no relay allowed" feature.

I also would like to keep a copy of every emailbox in the server. I want this because most (if not all) of the users dont perform backups and because once we got an important laptop stolen losing all the emails it had.

So, given this, i'm thinking about setting up an ubuntu server 11.10 x64 as a mailserver that would allow:
- external/internal connections/access to send and receive emails to all users
- emails to external domains would be relayed to our ISP email service
- periodic access to all accounts in the ISP server to download emails sent by external domains
- all company emails wharehouse (act as)


I've been trying to install postfix according this [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) , but i've been running into some problems. The lastest was that i could not issue the "sudo mv cacert.pem /etc/ssl/certs/".

But, for now i'd like to ask you if postfix is all need or if is needed other piece(s) of software?

Could you please help me on setting this up?

Thank's for your help.
Teslafan

---

### Post by lisati on 2011-12-09
If you want to enable access to the mailboxes using email clients, you might find something like [Dovecot]("https://help.ubuntu.com/community/Dovecot") or [Courier]("https://help.ubuntu.com/community/Courier") useful.

When you want to switch into "The boss wants archived copies of all email" mode, Postfix's "[always_bcc]("http://www.postfix.org/postconf.5.html#always_bcc")" setting might be useful - alternatives might be the "[recipient_bcc_maps]("http://www.postfix.org/postconf.5.html#recipient_bcc_maps")" or "[sender_bcc_maps]("http://www.postfix.org/postconf.5.html#sender_bcc_maps")" settings.

---

### Post by lisati on 2011-12-09
I forgot to mention spam filtering and antivirus. Have a look [here]("https://help.ubuntu.com/community/PostfixAmavisNew") and [here]("http://spamcop.net/fom-serve/cache/349.html"). There's more you can do, but that should help get you started.

---

### Post by Teslafan on 2011-12-09
Hi Lisati.

Thank's for the prompt replies.

I'm now trying to install postfix. 
From there I'll try to enable relaying. And from there I'll try to get email from the email account hosted by ISP (i'll be using gmail.com for testing purposes).

If all that goes well, I'll move on to Dovecot/Courier and the other features.

Regarding your last message; my ISP runs both spam filtering and antivirus. Since i'll be using their service to send messages to (and get them from) external domains, do i really need to install spam filtering? (Antivirus is an obvious addition)

---

### Post by collisionystm on 2011-12-09
First of all your mail server should be an LTS not 11.10. Secondly just install zentyal and save yourself headaches and time.

---

### Post by Teslafan on 2011-12-09
> **collisionystm said:**
> First of all your mail server should be an **LTS** not 11.10. Secondly just install zentyal and save yourself headaches and time.

Thanks for the tip. :)

---

### Post by SeijiSensei on 2011-12-10
Just a couple of quick points:

First, if you want to retrieve mail from remote accounts and deliver it to local accounts, you should take a look at [fetchmail]("http://www.fetchmail.info/").  

> **Teslafan said:**
> I'll try to get email from the email account hosted by ISP (i'll be using gmail.com for testing purposes).

[This tutorial]("https://help.ubuntu.com/community/GmailPostfixFetchmail") is specifically about using fetchmail with gmail.

Next, I'm wondering about remote access.  How will your staff members retrieve their mail if they are not inside the organization?  Presumably you have a firewall between your business network and the Internet.  Do you just intend to forward mail ports like 25, 110, 143, 587, etc. through the firewall and back to the server?  Perhaps you should look into setting up a webmail client like [Squirrelmail]("http://squirrelmail.org/") on a publicly-visible server that people can use from outside the office.

---

### Post by Teslafan on 2011-12-11
> **SeijiSensei said:**
> Just a couple of quick points:

First, if you want to retrieve mail from remote accounts and deliver it to local accounts, you should take a look at [fetchmail]("http://www.fetchmail.info/").  



[This tutorial]("https://help.ubuntu.com/community/GmailPostfixFetchmail") is specifically about using fetchmail with gmail.

**Next, I'm wondering about remote access**.  How will your staff members retrieve their mail if they are not inside the organization?  Presumably you have a firewall between your business network and the Internet.  Do you just intend to forward mail ports like 25, 110, 143, 587, etc. through the firewall and back to the server?  Perhaps you should look into setting up a webmail client like [Squirrelmail]("http://squirrelmail.org/") on a publicly-visible server that people can use from outside the office.

Hi.

Honestly i haven't really thought about that problem in particular, but yes, the first option (port forwarding) seems the best one for the system I envision. Neverthless, the squirrelmail is a good plan B.

So, i now have to install and configure:
- postfix
- dovecot/courier (so users can have access to their inbox through email clients)
- fetchmail (so the system goes to the remote accounts and collect the messages)
- Antivirus

I have now installed postfix, created 2 accounts, installed alpine (i got used to this client) and tried to send email between those accounts... but no success 'til now... I'm gonna keep trying... Any info would be greatly appreciated.

Peace.

---

### Post by collisionystm on 2011-12-11
> **Teslafan said:**
> Hi.

Honestly i haven't really thought about that problem in particular, but yes, the first option (port forwarding) seems the best one for the system I envision. Neverthless, the squirrelmail is a good plan B.

So, i now have to install and configure:
- postfix
- dovecot/courier (so users can have access to their inbox through email clients)
- fetchmail (so the system goes to the remote accounts and collect the messages)
- Antivirus

I have now installed postfix, created 2 accounts, installed alpine (i got used to this client) and tried to send email between those accounts... but no success 'til now... I'm gonna keep trying... Any info would be greatly appreciated.

Peace.

Use Zentyal! it has a web interface for the mail and can remote retrieve email. it is 10.04 LTS with extra modules. Its a beast and you will be up in minutes instead of hours

---

### Post by Teslafan on 2011-12-12
> **collisionystm said:**
> Use Zentyal! it has a web interface for the mail and can remote retrieve email. it is 10.04 LTS with extra modules. Its a beast and you will be up in minutes instead of hours

Downloading...

---

### Post by mosaic2s on 2011-12-12
else try citadel from [www.citadel.org](www.citadel.org)

i had given up on using ubuntu as a mail server - tried postfix, sendmail etc etc - then gave a shot to citadel.

it is good and scalable. works very different from how we think it should. but then thats the fun in learning it.

and yes, stick to 10.04 LTS for all such applications.

---

### Post by collisionystm on 2011-12-12
> **Teslafan said:**
> Downloading...


you will be glad you did. trust me.

---

### Post by Teslafan on 2011-12-12
> **collisionystm said:**
> you will be glad you did. trust me.

I can not validate the account i created in Zentyal with thunderbird installed in a vMachine. It comes with the invalid passord or username error. Everything is correctly typed...

Any ideas?

Regards.

---

### Post by collisionystm on 2011-12-13
> **Teslafan said:**
> I can not validate the account i created in Zentyal with thunderbird installed in a vMachine. It comes with the invalid passord or username error. Everything is correctly typed...

Any ideas?

Regards.


I need to check my settings..in the mean time, if you go to 

zentyalserver/webmail 

in your browser, can you login to the web interface for email?

the username is the full email address of your user

---

### Post by collisionystm on 2011-12-13
i created a virtual mail domain. lets pretend its ubuntu.com

so in zentyal, on the left side, way bottom, under Communication and then MAIL

create a virtual domain

now go to users and groups

click on your user

add their mail alias

[email]user@ubuntu.com[/email]

I have a DNS record under host name for my server


When I setup a user in thunderbird

the email address is [email]user@ubuntu.com[/email]

choose manual config

server is, servername

username is just the username without the domain

in your smtp settings, remove secure connection unless you have installed an SSL certificate to use

thats what I just did and it works fine... sorry for the bad explanation

---

### Post by Teslafan on 2011-12-13
Hi.

Ok, I managed to logon using thunderbird. Thanks for your help.
Moving on to enable relaying...

---

