---
title: "Apache2 cannot start with default-ssl.conf included"
date: 2014-04-03
forum: Server Platforms
---

### Post by Castea_Min on 2014-04-03
My apache2 cannot start with default-ssl.conf included, but if it's not included, apache2 can start normally.
Heres my default-ssl.conf: [http://pastebin.com/MDPMtBgN](http://pastebin.com/MDPMtBgN)

My apache2 error.log: [http://pastebin.com/xFMAfSmd](http://pastebin.com/xFMAfSmd)

Any help would be appreciated? Thank you very much. :confused:

---

### Post by Catalys on 2014-04-03
Try setting the ServerName in the .conf to match the url the Certificate is created for.

---

### Post by Castea_Min on 2014-04-03
Thank you for your reply, now the second ssl warning has been disappeared. but the first one still show. 
[Thu Apr 03 07:55:48.432173 2014] [ssl:warn] [pid 16 543] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
Apache still failed to start.

Are there any other parts i must check/modified?

---

