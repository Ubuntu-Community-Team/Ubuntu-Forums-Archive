---
title: "problem with Apache and HTTP authentication over HTTPS"
date: 2016-02-04
forum: Server Platforms
---

### Post by tomek7 on 2016-02-04
Hi All, to begin with- I want to congratulate you guys on building excellent forum for Linux knowledge. I'm coming for the first time with direct question, as I got stuck on activity that should not cause so much hassle. But let me start with describing a scenario.

I have got a setup with number of apache Virtual Hosts, which are running on port 80- not causing any troubles. Few days ago I decided to have a HTTP authentication, not in the plain text, but over HTTPS and this is where all the troubles started.

I will share some of my findings (and steps) as I already tried few solutions- so some of the people out there with similar problems might benefit (especially that quality of few apache tutorials is just silly):
 
1) I noticed that for https to be enabled by default /etc/hosts file need to contain record of the dns name (even pointing into localhost)- interesting is that the localhost needs to be in the form of local loopback address, otherwise it is not picking up.
2) special attention needs to be given to /etc/apache2/ports.conf file.
Do I need to specify the Virtual Host within that file or simple Name Server = *443 will be enough? I'm guesing it should be enough- afer few different combinations i managed to (finally) start Virtual Host (default on port 443).
3) I struggled with permisssions on cert files- which were resulting in "SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines" error - I did chmod 644 on files which cleared this error (should be helpful).
4) you might think that sorting out the certificates and finally starting default site on 443 will mean problems are over- it got even more strange. I'm seeing the certificates via openssl s_client -connect localhost:443 -showcerts
and same when I run this command using DNS name- however I'm not able to connect to the site from external browser.
5) curl is giving me some strange output (even after creating certificates on different box- the latest Ubuntu BTW), but according to the forums it is something that can be ignored. I ruled out firewall (ufw has been disabled)
6) the most frustrating thing is that I'm not receiving any error message in logs (event log is set to capture everything). My big question is- would that be possible browser is rejecting my certificate? I cannot login into the GUI on affected server as this is headless VM- and the certificate is created using OpenSSL- do you think it might be a problem?
 
I will much appreciate any suggestions from all the knowledgeable people out there.

Kind regards, Tomek

---

### Post by newbie-user on 2016-02-04
Did you generate your own certificate or buy one?

---

### Post by tomek7 on 2016-02-09
Hi, it's a self-signed certificate.

---

### Post by newbie-user on 2016-02-09
Okay, with self-signed certs, you would have to add the cert manually to whatever browser you're using, otherwise you'll get a "connection is not secure" message.

Regarding apache and ssl in general, did you enable the ssl mod? Also, I generally don't touch the ports.conf file. I just make a copy of default-ssl.conf in /etc/apache2/sites-available and edit it for the specific virtual host, then enable that conf file. So my process is this:
1. install apache
2. within /etc/apache2/sites-available, copy default-ssl.conf to new-ssl-site.conf, then edit new-ssl-site.conf
3. set up certs
4. enable ssl mod - sudo a2enmod ssl
5. enable new ssl site - sudo a2ensite new-ssl-site.conf
6. restart apache

---

### Post by tomek7 on 2016-02-10
Brilliant, thanks for that. I will try those steps and see how it will go. What will be your recommendation on redirecting whole http traffic into the https?

---

### Post by SeijiSensei on 2016-02-10
All you need is this:

```

<VirtualHost *:80>
ServerName www.example.com
Redirect / https://www.example.com/
</VirtualHost>

```

---

### Post by matt_symes on 2016-02-10
Hi

You may find this useful at some point.

[https://cipherli.st/](https://cipherli.st/)

Kind regards

---

### Post by tomek7 on 2016-02-10
Thanks guys a lot! Redirect tool worked brilliant- I will send the VirtualHost snipped shortly.

---

