---
title: "apache ssl error"
date: 2006-03-13
forum: Server Platforms
---

### Post by gmclachl on 2006-03-13
Hi, 
     I am trying to set up apache ssl. I have the cert and the key and have added 

SLCertificateFile /usr/local/apache/conf/ssl.crt/domainname.crt
SSLCertificateKeyFile /usr/local/apache/conf/ssl.key/domainname.key

to my httpd.conf but when i try to restart i get 

'-----BEGIN', perhaps mis-spelled or defined by a module not included in the server configuration

Thanks 
George

---

### Post by MJN on 2006-03-13
For a start you're missing an 'S' from the first directive... however I suspect that typo appears only on here...
 
Regarding the actual error, have you grep'd for -----BEGIN in your config files?
 
Mathew

---

### Post by gmclachl on 2006-03-13
Hi Matthew,
                  Yeah, you are right it is a typo. 

SSLCertificateFile /usr/local/apache/conf/ssl.crt/domainname.crt
SSLCertificateKeyFile /usr/local/apache/conf/ssl.key/domainname.key

both point to the key and the cert. 
  
               The -----BEGIN 

  is the first line of the certificate.

 George

---

### Post by MJN on 2006-03-13
Okay. If noone can help in the meantime I'll check my config tonight (7pm GMT) and take it from there.
 
Mathew

---

### Post by gmclachl on 2006-03-13
Managed to solve it. I moved the ssl dir's from conf.d up one level, restarted and it worked. 
Thanks for the help. 

 George

---

### Post by gmclachl on 2006-03-13
EDIT
Fixed

---

