---
title: "Cups web admin has me FUMING!!"
date: 2006-04-13
forum: Server Platforms
---

### Post by fredbear7232 on 2006-04-13
Hi all, hopefully I'm overlooking something really dumb. For some odd reason, I can NOT get the web admin page to come up. My cupsd.conf is below:

AccessLog /var/log/cups/access_log
DataDir /usr/share/cups
DefaultCharset utf-8
DefaultLanguage en
ErrorLog /var/log/cups/error_log
MaxLogSize 10485760
LogLevel info
Printcap /etc/printcap
RequestRoot /var/spool/cups
ServerBin /usr/lib/cups
ServerRoot /etc/cups
User lp
Group sys
Listen 127.0.0.1:631
Listen 192.168.1.10:631

<Location />
      Order Deny,Allow
      Deny From All
      Allow From 127.0.0.1
      Allow From 192.168.1.0/24
</Location>

<Location /admin>
      AuthType Basic
      AuthClass Group
      AuthGroupName shadow
      Order Deny,Allow
      Deny From All
      Allow From 127.0.0.1
      Allow From 192.168.1.101
</Location>

Browsing Off
BrowseProtocols cups
BrowseOrder Deny,Allow
BrowseAllow from @LOCAL
BrowseAllow from @IF(eth0)



The allow directive in the /admin section is for my workstation pc. the 192.168.1.10 is my server IP. I added cupsys to the shadow group. But for some darn reason, when I browse to [http://192.168.1.10:631/](http://192.168.1.10:631/) It gives me page cannot be displayed, like it's not even broadcasting out the cups web admin stuff. Maybe there's a package I'm forgetting or something?  

Any help would be greatly appreciate... ](*,)

---

### Post by fredbear7232 on 2006-04-14
So I'm assuming nobody's seen this issue? roger that..

---

### Post by peanut butter on 2006-04-14
it is disabled by default

[http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/](http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/)

tell me if that helps

---

