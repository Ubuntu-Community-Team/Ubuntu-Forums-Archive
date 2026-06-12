---
title: "Need to encrypt mail server traffic"
date: 2012-06-12
forum: Server Platforms
---

### Post by freakinjonathan on 2012-06-12
I setup my mail server. It's all good to go.

However my only issue is that I did a 

tcpdump -i eth0 -w output.pcap

And when I sent an email I was able to capture the whole email. 
this means that it's not secured properly right? 

What does one do?

I was following these instructions so I guess it should be useing dovecot for encryption?

---

### Post by SeijiSensei on 2012-06-12
Standard email is always in plain text.  Your server can use TLS to communicate with other servers that support it, but if you want to encrypt the actual message you need to use something like OpenPGP.  This is a client-side issue, not something to implement on the server.  Here's a [solution for Thunderbird]("http://enigmail.mozdev.org/home/index.php.html").

Be aware that any solution like this requires that the recipient has your "public key" and compatible software to decrypt the message.  Encrypted email requires support from both the sender and the recipient.

---

### Post by freakinjonathan on 2012-06-12
Thank you. That helps

---

### Post by freakinjonathan on 2012-06-12
Alright, well for now I want to be able to make an https connection to squirrelmail


Okay so this might sound kinda silly 
But in this part of the tutorial, I don't know which files he is talking about. sooo uh can you explain where are these files I have to edit.


It is this part 

```

If you want to use a /webmail or /squirrelmail alias that you can use from your web sites, this is a bit more complicated than for Apache because nginx does not have global aliases (i.e., aliases that can be defined for all vhosts). Therefore you have to define these aliases for each vhost from which you want to access SquirrelMail.

To do this, paste the following into the nginx Directives field on the Options tab of the web site in ISPConfig:

```
From this page:[http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p6](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p6)

---

### Post by Habitual on 2012-06-12
> **SeijiSensei said:**
> Standard email is always in plain text.  Your server can use TLS to communicate with other servers that support it, but if you want to encrypt the actual message you need to use something like OpenPGP.  This is a client-side issue, not something to implement on the server.  Here's a [solution for Thunderbird]("http://enigmail.mozdev.org/home/index.php.html").

Be aware that any solution like this requires that the recipient has your "public key" and compatible software to decrypt the message.  Encrypted email requires support from both the sender and the recipient.

As a side-note: email Subject lines are not and cannot be encrypted.

---

### Post by freakinjonathan on 2012-06-12
I guess technically this thread is solved. I'll mark it.

---

