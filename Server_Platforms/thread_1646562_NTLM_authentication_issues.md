---
title: "NTLM authentication issues"
date: 2010-12-16
forum: Server Platforms
---

### Post by waringt on 2010-12-16
Hi,
 
I am in the process of building a filter for our internal office network. Specs are as follows:
Ubuntu 10.10
DansGuardian 2.10.1.1-2
Samba 3.5.4
Squid3 3.1.6-1
 
I have installed and configured the server to a tutorial showing how to setup dansguardian, as well as setup NTLM authentication to create multiple groups with different levels of the filter.
 
i am having issues with getting those groups to work, as NTLM authentication seems to be failing. we have a W2K8R2 DC, which upon researching has been causing some issues with NTLM authentication.
 
i get the following when trying to test the authentication:
plaintext password authentication succeeded
challenge/response password authentication failed
could not authenticate user administrator with challenge/response
 
the server has successfully been joined to the domain.
 
any suggestions will be appreciated.
 
thanks,
Tim

---

