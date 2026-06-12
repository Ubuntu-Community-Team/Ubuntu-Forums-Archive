---
title: "OpenVPN certificate creation / revocation"
date: 2015-11-03
forum: Security
---

### Post by Drenriza on 2015-11-03
Hi all

I am setting up my own OpenVPN server with easy-rsa to get more knowledgeable of how OpenVPN works and is administrated.
[I]Please not that i am not a OpenVPN / VPN / certificate master and are on the learning curve.

[/I]These are very open questions that i havent quite found a answer to or is very vague on the WWW.
Any and all feedback that answers the questions directly, or which can  point me in the right direction for an answer is very welcome!

After working a bit with OpenVPN i have a few questions that i hope to get some feedback on.
When we create a new certificate with easy-rsa
```
/etc/openvpn/easy-rsa/build-key-pass
```

**When we create a new certificate what exactly is created and done?**
From what i have gathered and figured out so far the following files are created

[LIST=1]
[*]user.csr 
[*]user.crt 
[*]user.key 
[*]xx.pem 
[/LIST]


[LIST]
[*]CSR file
[LIST]
[*]From what i understand the CSR file is the Certificate Signing Request file used to create the .crt file from the .key file (from the client) by asking the CA to sign it and return the crt file.
When running OpenVPN locally, when installing OpenVPN a Certificate Authority is also installed / created / setup? So i locally can sign my own certificates?
[LIST]
[*]When the .csr file is signed locally and returned as a .crt file, should i delete the .csr file? And is it considered a secret? Its not shown at [https://openvpn.net/index.php/open-source/documentation/howto.html](https://openvpn.net/index.php/open-source/documentation/howto.html) key files section. 
[/LIST]
     
[/LIST]
  
[*]xx.pem
[LIST]
[*]What is this file and what is its purpose? /etc/openvpn/easy-rsa/keys/xx.pem 
[/LIST]
  
[*]Certificate Authority (maybe redundant)
[LIST]
[*]When we install OpenVPN and make it sign certificates locally, who is the Certificate Authority? Is it handled as a independent package or is it the openssl service / something else? 
[/LIST]
     
[/LIST]

**Revoking certificates**
When we want to revoke a certificate the process as i understand it is as follows

[LIST=1]
[*]issue /etc/openvpn/easy-rsa/revoke-full client-name
[LIST=1]
[*]The client name is the name of the local user or some name created with the certificate? 
[*]You want an error 23 which means that the certificate (now revoked) could not be verified. 
[/LIST]
  
[*]/etc/openvpn/easy-rsa/keys/index.txt will be updated with a beginning "R" for revoked. 
[*]This will remove / or indicate the certificate (.pem file) from / as revoked openssl? 
[*].pem file for the associated revoked certificate needs to be removed to /etc/openvpn/
[LIST=1]
[*]Why? 
[/LIST]
  
[*]When a certificate is revoked it stands as revoked "R" in /etc/openvpn/easy-rsa/keys/index.txt. Is this the entire normal procedure?
Or would you also delete all associated certificate files? Or is their a reason you wouldnt want to delete all the associated certificate files? 
[/LIST]
 
Thanks on advance all!

---

### Post by bashiergui on 2015-11-05
This site explains the way certificates work overall, which will probably answer several of your questions
[http://www.networksolutions.com/SSL-certificates/how-ssl-works.jsp](http://www.networksolutions.com/SSL-certificates/how-ssl-works.jsp)

This one goes into detail about the various technical parts (like .pem files) of certificate generation, and will probably answer a few more of your questions.
[http://serverfault.com/questions/9708/what-is-a-pem-file-and-how-does-it-differ-from-other-openssl-generated-key-file](http://serverfault.com/questions/9708/what-is-a-pem-file-and-how-does-it-differ-from-other-openssl-generated-key-file)

---

### Post by gordintoronto on 2015-11-05
Your OS version might affect how successful you are. I connect to my office, which has OpenVPN running on the pfSense "firewall." (pfSense also does all the routing activities for the network.) When I connect from Linux Mint 13 (equivalent to Ubuntu 12.04) it all works as it should. I have been unable to connect from 14.04 or 15.04. Xubuntu 15.10 works nicely.

---

### Post by Drenriza on 2015-11-09
Thanks for the feedback guys!

---

