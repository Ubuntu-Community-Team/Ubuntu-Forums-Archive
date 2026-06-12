---
title: "Domain name+webserver?"
date: 2006-12-10
forum: Server Platforms
---

### Post by haxer on 2006-12-10
Hello im intressting i registred an domain name haxer.eu or im on my way doing it ... my only question is how to set up an little webserver on ubuntu? 
Not big project just easy acces server with ftp i guess? ;) :-k appache?

---

### Post by Cyberflunky on 2006-12-10
You will need to look into setting up Apache to get started. Also you will not want to use FTP its old and insecure. Try looking into SFTP and SCP.

---

### Post by technodigifreak on 2006-12-11
> **haxer said:**
> Hello im intressting i registred an domain name haxer.eu or im on my way doing it ... my only question is how to set up an little webserver on ubuntu? 
Not big project just easy acces server with ftp i guess? ;) :-k appache?

HowtoForge is right up your alley.  Here are 2 tutorials that should help you out.  Both are for Dapper, but you can find versions for Edgy on the same site also.

This one is most usefull for the firewall and SSL configuration.
[http://howtoforge.net/ubuntu6.06_firewall_gateway](http://howtoforge.net/ubuntu6.06_firewall_gateway)

This shows you how to install a full ISP server.  I recommend that you do not host your own DNS unless you really know what you are doing.
[http://howtoforge.net/perfect_setup_ubuntu_6.06](http://howtoforge.net/perfect_setup_ubuntu_6.06)

Hope these put you in the right direction.  Let us know how it progresses!

---

### Post by haxer on 2006-12-11
will the first guide damage my system in any way? Will i still have an Desktop? :-k

---

### Post by technodigifreak on 2006-12-11
> **haxer said:**
> will the first guide damage my system in any way? Will i still have an Desktop? :-k

You want to do this on a desktop? ummm, OK, neither of those guides were designed for a desktop machine.  I'm going to assume that you're not planning on having much traffic to the website, right?

This link will probably be more helpful then. [http://help.ubuntu.com/community/ApacheMySQLPHP](http://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by haxer on 2006-12-11
Thanks just as you say "not an big homepage" ;)

---

### Post by az on 2006-12-11
See: [https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by max.diems on 2006-12-11
A quick ```
sudo aptitude install apache2
``` will get the webserver bit.

---

