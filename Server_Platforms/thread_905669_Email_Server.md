---
title: "Email Server"
date: 2008-08-30
forum: Server Platforms
---

### Post by kornyam on 2008-08-30
This is my first post here, but reading these forums has always helped me in the past.
I've been setting up a home server with Xubuntu Feisty Fawn, and I want to put a mail server in. I don't have a static IP, but im using DynDns. I followed [this]("https://help.ubuntu.com/community/MailServer") tutorial, and I've read a few others that I found on Google, but i cant figure out what's gone wrong, or if I'm just missing something completely. 
I set up the server using Postfix, Dovecot, and Squirrelmail, and I set up a few accounts. They work fine for sending and receiving mail to each other, but not for sending to any other addresses. I've tried sending messages to my Hotmail and university email accounts, and it looks as though it sends fine, but the message never gets there. When I try to send a message to an account on the server, I get a message from the postmaster (a few hours later) saying:

This is an automatically generated Delivery Status Notification.
THIS IS A WARNING MESSAGE ONLY.
YOU DO NOT NEED TO RESEND YOUR MESSAGE.
Delivery to the following recipients has been delayed.

Everything I've done seems to match the tutorial, so I don't know what I've done wrong, or if I'm just missing something completely. Any help would be greatly appreciated.

---

### Post by HermanAB on 2008-08-30
If you want to run a mail server, then you have to have a 'server' account with a fixed IP address from your ISP and you need a proper DNS setup with A, PTR and MX records.

Otherwise, you can try forwarding via your ISP mail server (smart host).

Cheers,

Herman

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by tuskenraider on 2008-09-01
man i dont wanna be a buzz kill... but i had a windoze server 2003 r2 mail server... and every day... 3 or 4 times a day people would try to hack it or send spam through it...  granted having your own mail server is super fantastic... its just worth the security risk IMHO... but then again it was windoze...  just be carefull and watch out for those pesky spammers...

---

### Post by schettj on 2008-09-01
I'd agree with both of the posters above

a) dynamic IPs - some/most/any sane ISP will block inbound port 25 traffic on dynamic IPs as those are the source of 99% of all spam email from zombied machines

b) you'll want to harden your install using lots and lots of readmes and whatnot. Postgrey is helpful, as are spamassassin, clamav, and lots of other things - run postfix over sendmail, it's a lot easier to harder. Run fail2ban with postfix enabled as well. 

c) you'll eventually want a real domain name with correct MX and SPF records, as most mail servers will reject mail from yours (or as in the case of mine, will flag it as SPAM and dump it into a spam bucket) if you don't. 

But first, check with your ISP and see if running an email server is possible/conforms to your TOS. For my ISP, I'd need to be on the more expensive static IP service to run one (which I am.)

---

