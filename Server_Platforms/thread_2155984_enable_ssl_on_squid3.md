---
title: "enable ssl on squid3"
date: 2013-06-20
forum: Server Platforms
---

### Post by sipetron on 2013-06-20
i tray to enable ssl on squid but its didnt work !!!!
how to compile it right ?

---

### Post by Vitsliputsli on 2013-06-20
Are your proxy transparent? If you use transparent proxy you can't work with ssl anyway.

---

### Post by sipetron on 2013-06-20
ok . 
how to make it work ?

---

### Post by Vitsliputsli on 2013-06-20
What are you mean about work? You can't open https-sites or de&#1089;rypt content? 
You can't decrypt https content anyway, it's impossible, if proxy is transparent. Is proxy transparent?

---

### Post by sipetron on 2013-06-20
yes its transparent 
what i need it from enabling ssl on squid to filter https sites not to decrypt it

---

### Post by Vitsliputsli on 2013-06-20
Before client get ssl-certificate, he must connect to server without encryption, squid must see that. You need to check squid options for port 443, squid must listen it. Or redirect port 443 to squid port. 
I can't tell more accurately, I have no suid now.

---

### Post by SeijiSensei on 2013-06-20
You need to read this:  [http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

Squid 3.3 is supposed to support transparent HTTPS proxying.  You'll still need to generate a certificate for the proxy and distribute it to all your users' browsers.  Implementing this is very complex.  I'm going to start testing 3.3 for one of my clients in the next couple of weeks.

Right now we block HTTPS requests with iptables, but that requires knowing the IP addresses for all the hosts/subnets you wish to block.  In some cases that requires many, many rules.  [Here](http://ubuntuforums.org/showthread.php?t=2155259&p=12696710&viewfull=1#post12696710) is the list of addresses required just to block Facebook.

---

### Post by Vitsliputsli on 2013-06-20
Very intresting news. Please, tell results after testing. Thanks.

---

### Post by sipetron on 2013-06-20
> **Vitsliputsli said:**
> Before client get ssl-certificate, he must connect to server without encryption, squid must see that. You need to check squid options for port 443, squid must listen it. Or redirect port 443 to squid port. 
I can't tell more accurately, I have no suid now.



i done redirect 443 port to 3130 on squid but its still give me errors

---

### Post by sipetron on 2013-06-20
> **SeijiSensei said:**
> You need to read this:  [http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

Squid 3.3 is supposed to support transparent HTTPS proxying.  You'll still need to generate a certificate for the proxy and distribute it to all your users' browsers.  Implementing this is very complex.  I'm going to start testing 3.3 for one of my clients in the next couple of weeks.

Right now we block HTTPS requests with iptables, but that requires knowing the IP addresses for all the hosts/subnets you wish to block.  In some cases that requires many, many rules.  [Here]("http://ubuntuforums.org/showthread.php?t=2155259&p=12696710&viewfull=1#post12696710") is the list of addresses required just to block Facebook.


i had many issue with compail squid and i cant use its by compailing it , can you give me the way to compail it right on server 12.04?

---

### Post by SeijiSensei on 2013-06-20
I use CentOS for servers, and squid compiled correctly for me without much trouble.

Did you install the "build-essential" package?  You should also run "sudo apt-get build-dep squid3" to get the libraries and headers for any dependencies.

I also found this: [http://arfanahmedcheema.blogspot.com/2013/04/squid-333-compilation-on-ubuntu-12.html](http://arfanahmedcheema.blogspot.com/2013/04/squid-333-compilation-on-ubuntu-12.html)

---

### Post by sipetron on 2013-06-20
ok 
ill test it and tell you my results :)

---

### Post by SeijiSensei on 2013-06-20
Squid 3.3.5 will not compile for me on CentOS if I use --enable-ssl-crtd with configure.  I get the error described here: [http://www.squid-cache.org/mail-archive/squid-users/201305/0400.html](http://www.squid-cache.org/mail-archive/squid-users/201305/0400.html)

I may try again with an earlier minor version like 3.3.4 or 3.3.3.

Update:  I also cannot compile either of those versions.

---

### Post by sipetron on 2013-06-24
squid compile . 
but when i add this as the site said 
http_port 192.168.5.239:3128 transparent ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=4MB cert=/usr/share/ssl-cert/myCA.pem 
its want start 
and i cant find it on init.d directory or in services to start or restart it

---

### Post by SeijiSensei on 2013-06-24
I'm impressed that you got it to compile.  As I said, 3.3.3-5 have all failed for me.  Squid itself compiles fine, but it fails when it gets to the certificate part.

Did you compile with the "--enable-ssl --enable-ssl-crtd" parameters in configure?  It's that last of these that fails for me and for others as I linked to above.

By default, the daemon will be installed to /usr/local.  You'd have to first install the repository version to get the appropriate entries in /etc/init.d, then edit the startup script to use /usr/local/sbin/squid instead of the repository version.

---

### Post by sipetron on 2013-06-26
> **SeijiSensei said:**
> I'm impressed that you got it to compile.  As I said, 3.3.3-5 have all failed for me.  Squid itself compiles fine, but it fails when it gets to the certificate part.

Did you compile with the "--enable-ssl --enable-ssl-crtd" parameters in configure?  It's that last of these that fails for me and for others as I linked to above.

By default, the daemon will be installed to /usr/local.  You'd have to first install the repository version to get the appropriate entries in /etc/init.d, then edit the startup script to use /usr/local/sbin/squid instead of the repository version.



the compiling done perfect 
but about the start and stop service manual i didnt get it will 
-bash: cd: /usr/local/sbin/squid: No such file or directory

---

### Post by SeijiSensei on 2013-06-26
You really got it to compile with "./configure --enable-ssl --enable-ssl-crtd"?  Hmm.  I'll have to try again.

I don't recall any more exactly where make install puts the binaries, but they are definitely under /usr/local by default.  It might have created a /usr/local/squid directory.  Just browse around in /usr/local; you'll find them.

---

### Post by sipetron on 2013-06-27
configure options:  '--prefix=/usr' '--includedir=/usr/include' '--datadir=/usr/share' '--bindir=/usr/sbin' '--libexecdir=/usr/lib/squid' '--localstatedir=/var' '--sysconfdir=/etc/squid3' '--enable-delay-pools' '--enable-ssl' '--enable-ssl-crtd' '--enable-linux-netfilter' '--enable-arp-acl' '--enable-snmp' '--enable-gnuregex' --enable-ltdl-convenience

---

