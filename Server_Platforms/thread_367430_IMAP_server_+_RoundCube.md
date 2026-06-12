---
title: "IMAP server + RoundCube"
date: 2007-02-22
forum: Server Platforms
---

### Post by dboot on 2007-02-22
Hey all,

I have had the hardest time setting up an IMAP mail server using RoundCube as the webmail interface. I followed countless guides for setting up portions of the mail server and different guides for setting up RC.

Does anyone have any experience setting up an IMAP server with Roundcube?

I'm a moderate linux user so I can follow in depth guides.

Thanks for any help!

---

### Post by dboot on 2007-02-22
I even installed ISPConfig so I could follow this guide:

[http://www.howtoforge.com/roundcube_webmail_ispconfig](http://www.howtoforge.com/roundcube_webmail_ispconfig)

even though I don't especially like ISPConfig...

---

### Post by jmacdonagh on 2007-02-22
What portion are you having difficulty with? I have a working Postfix + Courier IMAP + Roundcube install going on my Edgy server. Do you have a working IMAP server?

---

### Post by dboot on 2007-02-22
I actually don't know if my IMAP server is working properly. I've installed the following:

apt-get install courier-authdaemon courier-base courier-imap courier-imap-ssl courier-pop courier-pop-ssl courier-ssl gamin libgamin0 libglib2.0-0

from [here]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p5").

I've also edited a few imap config files. I know the processes are running but I'm not sure if the server is working.

Any suggestions?

Thanks!

---

### Post by jmacdonagh on 2007-02-23
The first thing to try is to make sure your IMAP server is working ;)

Just some questions. What MTA are you using (Postfix, etc...)? How do you have the mailboxes set up (UNIX accounts, virtual users, etc...)?

Most tutorials are for setting up your MTA with virtual users. If you do that, you'll need the courier-authmysql package (the package name is probably something different, but I'm not at my box right now). That way, Courier can authenticate requests based on your MySQL database of users.

---

### Post by dboot on 2007-12-10
I finally tried again to install a mail server on my simple ubuntu server. I was successful after installing [citadel]("http://www.citadel.org"). Then I setup RoundCube to see my IMAP server on localhost and presto it worked without any trouble.

On my old PC I use as a server:

Citadel running all of it's services for email (from mail to webadmin using https)
Webmin (to admin most other services)
SSH
Lighty (for my own website on port 80)
RoundCube (as an IMAP webmail server)
proftpd
PHP
mysql
Ruby on Rails
and more for setup...

I'm loving it! It all works perfectly together on such an old PC!

---

