---
title: "Add new SSL certificate Ubuntu 18.04"
date: 2021-10-26
forum: Server Platforms
---

### Post by coolit2 on 2021-10-26
Hey Guys,

I have been running a home server (Ubuntu 18.04 // Apache/2.4.29 // OpenSSL 1.1.1j)
Had a 2 year certificate which worked perfect. It was about to expire so I bought a new one.
I was able to buy a new one without problems, so far so good :)
But I'm no expert.
So the question, how do I replace the old cert with a new one?
Last time I had to make the following folder:
/etc/apache2/ssl/
Within this folder there are 4 files:
-IntermediateCA.crt
-mydomain.com.crt
-mydomain.com.csr
-mydomain.com.key
Then I had to navigate to /etc/apache2/sites-enabled/default-ssl.conf and add the following:
SSLCertificateFile   /etc/apache2/ssl/mydomain.com.crt
SSLCertificateKeyFile /etc/apache2/ssl/mydomain.com.key
en
SSLCertificateChainFile /etc/apache2/ssl/IntermediateCA.crt

But what to do with the new files? I received the following:

-dv-ssl.pem
-dv-ssl-rsa.pem
-mydomain_com.pem

1) Do I replace the old files with the new ones and adapt the "/etc/apache2/sites-enabled/default-ssl.conf" file?
2) Whats a "pem" file? can I replace the crt/csr files with these pem files?
3) If yes to the above questions, do I then restart Apache and I'm done?

Thanks in advance for the help

---

### Post by MAFoElffen on 2021-10-27
Well:
[https://www.digicert.com/kb/csr-ssl-installation/apache-openssl.htm](https://www.digicert.com/kb/csr-ssl-installation/apache-openssl.htm)
[https://www.digicert.com/kb/csr-ssl-installation/apache-openssl.htm#create_csr_open](https://www.digicert.com/kb/csr-ssl-installation/apache-openssl.htm#create_csr_open)
[https://www.thesslstore.com/knowledgebase/ssl-install/whm-ssl-installation/](https://www.thesslstore.com/knowledgebase/ssl-install/whm-ssl-installation/)

Or... Where you ordered and purchased the cert, should have at least some kind of support on how to apply their SSL cert to your env...

---

### Post by coolit2 on 2021-10-28
HiMAFoElffen

First, thank you for taking the time to respond to my question. 
For you this will no doubt be a trivial thing. For a hobbyist like me its not.
The "official" help from the seller was the same as you  provided.
But it does not help me. 

[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")[I]**1) Do I replace the old files with the new ones and adapt the "/etc/apache2/sites-enabled/default-ssl.conf" file?**
[/I]From what I can read in the quide I think i'm on the right path? Replace the path of the current files to the path of the newly received files?
***2) Whats a "pem" file? can I replace the crt/csr files with these pem files?***
This, I cant find info on "pem" files. Does openssl support "pem" files?

Thx again for the help.

---

