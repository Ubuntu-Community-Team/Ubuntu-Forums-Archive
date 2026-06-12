---
title: "Need to Confgiure working Mail System on Ubuntu, Pleas Help!"
date: 2018-05-02
forum: Server Platforms
---

### Post by ganelot on 2018-05-02
Hi.
Let me tell You what i want to achieve and with what I need help.
I have 20 old laptops. I want to connect them all thru WiFi, i have 2 routers that will help me to do that.
Main goal is to create a mail system between them. They wont be connected to internet. 
On each laptop there will be one or more accounts, and I need an working email adrress that can send email to everybody else.
Secondary goal is to create a storage space shared betwen them (but I thikn my coworker managed to to that)
Lets say that i`ll create a network say 10.0.0.0 first laptop will be the server one 10.0.0.1 rest .2 .3 .4 .5 .6 and so on.

I know that i need MTA, MDA, and something like Thunderbird to get it all running.
MTA - postfix?
MDS - dovecot?
Thunderbird to get it all working for users that have verry limited knowlege about computers. All they need to know is the addresses of other users.

I`ve found many, many guides how to get it all working bot not a single one that tells you from start to end how to get it all working.
Moste of them said i need a domain but thats not an option - no internetSo if there is anyone who can help me I`ll be glad!

---

### Post by LHammonds on 2018-05-02
Getting a mail server running is one of the more advanced admin tasks you can perform.  I've run many different types of servers and operating systems for many years and have only ever been able to get one mail server running successfully by myself (cause I'm not the sharpest tool in the shed).  The mail server I got running was a complete package called NethServer but I still needed to know the various networking/domain stuff to get it working.  That is one server I never documented step-by-step because honestly, I surprised myself when I got it running and didn't have the time to trash it and build it all again from scratch to document the steps.  Wish I did though.

LHammonds

---

### Post by rsteinmetz70112 on 2018-05-02
Installing postfix and dovecot on one machine should do what you need. It's fairly easy. dovecot doesn't require much configuration. postfix is fairly easy.

There are a number of guides for postfix around. The basic automatic postfix configuration does most of the work. If I recall correctly there is an option for a stand alone server. You will need to add all user accounts to your server then configure networking  and a mail client on each machine. Thunderbird works well and is installed by default in Ubuntu. If you are using Windows clients it is available for them as well.

As for a domain name you do need one for mail to work but you can just make one up if you aren't connected to the Internet. FreeDNS has shared public domains you could use or You can even get a real one for a few bucks or possibly free if you want.

Good luck.

---

### Post by SeijiSensei on 2018-05-02
You might consider a webmail system like [Roundcube]("https://roundcube.net/").  Then your users just need a browser.  

[https://www.linode.com/docs/email/clients/install-roundcube-on-ubuntu/](https://www.linode.com/docs/email/clients/install-roundcube-on-ubuntu/)

You'll still need a mail exchanger like Postfix and an IMAP server like dovecot.

Citadel, I believe, handles a lot of the installation process for you, but I've not installed it myself: [https://www.maketecheasier.com/citadel-email-collaboration-suite-linux/](https://www.maketecheasier.com/citadel-email-collaboration-suite-linux/)

---

