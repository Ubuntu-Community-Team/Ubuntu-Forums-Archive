---
title: "Trust New Verisign Root"
date: 2011-05-09
forum: Server Platforms
---

### Post by Lloyd_mcse on 2011-05-09
Hi guys,
I need to trust a new Verisign Root cert, I have uploaded it to the /etc/ssl/certs store but I am still getting the Handshake failure error when WorldPay call back to my site..
 
>  
[Mon May 09 11:32:56 2011] [error] SSL Library Error: 336068931 error:14080143:SSL routines:SSL3_ACCEPT:unsafe legacy renegotiation disabled

 
I believe I still need to create a sym link? So I followed [this]("http://www.madboa.com/geek/openssl/#verify-new") article but I get an error..
 
>  
user@host:~# certlink.sh /etc/ssl/certs/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.pem
-bash: /usr/bin/certlink.sh: /bin/sh^M: bad interpreter: No such file or directory

 
I have also tried update-ca-certificates.
I'm using Ubuntu 8.04 LTS I'm hoping someone knows what I need to do.
Thanks in advance for any help
Kind regards
 
Lloyd

---

### Post by Lloyd_mcse on 2011-05-09
I checked and the cert is also in /usr/lib/ssl/certs as it should be.

---

### Post by Lloyd_mcse on 2011-05-11
Can anyone help with this?

---

### Post by hawkmage on 2011-05-11
I assume that you have SSLCACertificatePath /usr/lib/ssl/certs/ in your Apache config.  

I also assume you put the VeriSign pem file in the /usr/lib/ssl/certs/ directory before running the update-ca-certificates command.  

However that error may not indicate a certificate validation issue.  It sounds like the client is trying to do an SSL renegotiation that has been found to be insecure so recent versions of Apache disables this.  You can reenable it by adding "SSLInsecureRenegotiation on" to your mod_ssl config.

---

### Post by Lloyd_mcse on 2011-05-12
We actually use a COMODO EV SSL for our domain, which is fine, but WorldPay use a Verisign SSL which is signed by a root ca that we don't have installed on the server so when worldpay calls back to the server it can't verify them and refuses connection.
 
This root ca has been istalled on our Ubuntu 10.04 LTS server but not on 8.04.
 
I'm not sure if "SSLInsecureRenegotiation on" would affect our PCI compliance, I think it probably would?
 
Thanks for your help

---

### Post by hawkmage on 2011-05-12
I had assumed that you did put the new VeriSign cert on your web server since you said: "I have uploaded it to the /etc/ssl/certs".  

However the error one the WorldPay connection mentions "unsafe legacy renegotiation disabled".  A while back there was a vulnerability found in SSL connection renegotiation so by default this is disabled in recent SSL implementations.  If one side is expecting to renegotiate the connection and the other doesn't the connection can fail.  That is why I mentioned the "SSLInsecureRenegotiation on".

---

### Post by Lloyd_mcse on 2011-05-14
I've found the issue now - there was a cipher string in the .htaccess and server wide. Once I removed the one from the htaccess it was fine - D'OH
 
Thanks for the help,

---

