---
title: "Intermediate certificate issues"
date: 2013-06-23
forum: Server Platforms
---

### Post by chinny on 2013-06-23
Am hoping someone can help me. 
I have an issue with intermediate cert and apache ssl config - I have installed the intermediate cert and run update-ca-certificates. 
IE and chrome work fine but firefox is missing the intermediate cert. I thought the config was correct and have specified the intermediate cert with SSLCertificateChainFile. 
Running openssl s_client -connect server.tld:443 -showcerts fails but if I add -CAPath /etc/ssl/certs/ it passes.

---

