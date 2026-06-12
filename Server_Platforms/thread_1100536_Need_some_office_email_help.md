---
title: "Need some office email help"
date: 2009-03-19
forum: Server Platforms
---

### Post by sgtbug on 2009-03-19
Hi guys

Ok, here is the problem.

I have a hosted IMAP server (like Gmail and GMX). I wish to retrieve emails from it for my office network on computers that do not have Internet access. That I managed to accomplish with RoundCube and Squirrel.

Now, I need to cache that email for offline access, along with the login, so that even if the server is not connected to the Internet, the employees can access their old email. I cannot give them Internet access. I just wish to cache their email offline in MySQL or whatever (and they should be able to log in, which isn;t possible right now since they are actually logging in directly to the IMAP.

Can this be done? If yes, how?

Thanks in advance. Any kind of help is appreciated!

Regards.

PS: I'm sorry if I sound lame, but I am very new to servers.

EDIT: Also, if someone can help me. The default apache2 package in the repositories is not executing my PHP files (I get a Save as dialogue when I try to open it like [http://localhost/phpmyadmin](http://localhost/phpmyadmin). It says it is a PHTML file). I had to use XAMPP instead. Any solutions for that? Is XAMPP reliable?

---

### Post by koenn on 2009-03-19
sounds to me you should be running an IMAP server on your office LAN, have your clients use that instead of internet access, and have mail delivered to that server, possibly through a relay in DMZ or on your perimeter firewall.

---

### Post by HermanAB on 2009-03-19
It sounds like you really need to run your own email server.  Get a server account (costs about $10 more per month) and install Citadel or Zimbra.

It takes about 20 minutes to install Citadel, an hour if you add SpamAssassin and ClamAV.
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

Cheers,

Herman

---

### Post by sgtbug on 2009-03-20
is it really necessary to run a full online mail server in this case? i have a 3rd part ssl ready imap.. is there a way to direct their imap requests to the online servers? that way i can just hook it up with thunderbird and be done with it.. is it possible with courier?

is there nothing that can cache the mail for offline use in mysql or anything of the sort? another option i am considering is fetchmail.. will that do the trick?

and what abt the apache2+php5 problem? do u think xampp/lampp is good enough?

---

### Post by koenn on 2009-03-20
> **coolaks said:**
> is it really necessary to run a full online mail server in this case? i have a 3rd part ssl ready imap.. is there a way to direct their imap requests to the online servers? that way i can just hook it up with thunderbird and be done with it.. is it possible with courier?

is there nothing that can cache the mail for offline use in mysql or anything of the sort? another option i am considering is fetchmail.. will that do the trick?

You can build a solution around having a server pulling mail from your externally hosted IMAP server server. Fetchmail is one of the tools that can do that. I remember this being not uncommon for small businesses who got residential internet access but wanted 'enterprise style' email. The only benefit is you don't need a server that is permanently online with a fixed IP address. The downside is that 
a/ you're replacing smtp, which was designed for mail delivery, by POP or IMAP, which weren't designed for mail delivery at all.
b/ you make mail delivery intermittent, i.e. you get scheduled deliveries 

I honestly don't see the benefits, but it's possible

As for using mysql or some other contraption as a mail solution while tools designed for the task  are readily available, is beyond me.

> **coolaks said:**
> 
and what abt the apache2+php5 problem? do u think xampp/lampp is good enough?
you better start a separate thread for this, otherwise this thread is going to be a mess of apache, php, imap, ... posts piled up.

---

### Post by hyper_ch on 2009-03-20
Kontact has a disconnected IMAP option. That means all mails are mirrored between the local computer and the IMAP server. You'll have then a local copy on your local computer in Maildir format.

---

### Post by sgtbug on 2009-03-31
> **koenn said:**
> You can build a solution around having a server pulling mail from your externally hosted IMAP server server. Fetchmail is one of the tools that can do that. I remember this being not uncommon for small businesses who got residential internet access but wanted 'enterprise style' email. The only benefit is you don't need a server that is permanently online with a fixed IP address. The downside is that 
a/ you're replacing smtp, which was designed for mail delivery, by POP or IMAP, which weren't designed for mail delivery at all.
b/ you make mail delivery intermittent, i.e. you get scheduled deliveries 

I honestly don't see the benefits, but it's possible



Thanks for your reply. I'm sorry for not replying earlier. There were some problems.

I do not wish to replace smtp. A Squirrelmail like solution is what I need but with offline caching of the email messages.

I could have hosted my own dedicated mail server as well, but the Internet solutions in India are not fit to run a mail server. The downtime is high, speeds are low. This seems to be the best solution (to me at least), because here the email server is more reliable and faster with no downtime. I'm trying to save time here, not money ;-)

I am using roundcube atm, but i need centralized offline caching to save time and avoid re-downloading of old mail.

@hyper
thanks for the suggestion, but I need a web based solution.

---

### Post by HermanAB on 2009-03-31
Citadel will cache your mail for you in a BerkeleyDB.  It can save up to 256 Terabytes of mail.

---

