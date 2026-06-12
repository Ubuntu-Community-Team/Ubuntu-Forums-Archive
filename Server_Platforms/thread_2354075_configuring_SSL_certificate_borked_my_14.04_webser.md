---
title: "configuring SSL certificate borked my 14.04 webserver"
date: 2017-02-27
forum: Server Platforms
---

### Post by Drone4four on 2017-02-27
I was initally trying to establish https, I kinda messed up my webserver accidentally by following [this Digital Ocean tutorial on SSL certificates]("https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04").

People on irc recommended that the tutorial I really needed was [this one]("https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-14-04").

The homepage for one of my two vhosts should parse index.html in /var/www/html/[$DN].com/public_html/, right? That's how it usually works.  But now it shows the attached image. ugh

How do I fix this?

The only configuration file I created and customized was default.ssl.conf inside /etc/apache2/sites-available: [http://pastebin.com/smxHbEEV](http://pastebin.com/smxHbEEV)

I have stopped the apache service temporarily while I am troubleshooting this issue with my server.

---

### Post by Drone4four on 2017-02-27
My issue was resolved by a kind soul in #digitalocean on FreeNode.  DocumentRoot at line 7 in that config file is set to ```
/var/www/html/
``` which is incorrect. I changed that line to: ```
/var/www/html/[$DN}/public_html
``` and my issue was resolved.  Easy.

---

### Post by bearlake on 2017-02-27
Hi,

You really need to mark this thread as solved. I'm sure others will run into the same problem.

Glad you are back up and running. :)

---

### Post by DuckHook on 2017-02-27
> **Drone4four said:**
> My issue was resolved by a kind soul in #digitalocean on FreeNode.  DocumentRoot at line 7 in that config file is set to /var/www/html/ which is incorrect. I changed that line to: /var/www/html/[COLOR="#FF0000"][[/COLOR]$DN[COLOR="#FF0000"]}[/COLOR]/public_html and my issue was resolved.  Easy.

@Drone4four

I have added code tags to your original post for clarity. But your second code sample has mismatched brackets. Posterity would greatly appreciate a correction, then your marking thread *Solved*.

---

### Post by CharlesA on 2017-02-28
> **DuckHook said:**
> @Drone4four

I have added code tags to your original post for clarity. But your second code sample has mismatched brackets. Posterity would greatly appreciate a correction, then your marking thread *Solved*.

Pssst... you can mark threads as solved too. :)

---

