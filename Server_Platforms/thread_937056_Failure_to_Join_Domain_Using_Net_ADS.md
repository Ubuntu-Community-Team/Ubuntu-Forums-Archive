---
title: "Failure to Join Domain Using Net ADS"
date: 2008-10-03
forum: Server Platforms
---

### Post by vegas588 on 2008-10-03
When I issue the command below I get an error when trying to join the domain using the details from this document: [http://www.ccs.neu.edu/home/battista/articles/winbind/domain.html](http://www.ccs.neu.edu/home/battista/articles/winbind/domain.html) PAGE 8

jamesc@ubuntuserver1:/$ sudo net ads join -U ADMINISTRATOR
Host is not configured as a member server.
Invalid configuration.  Exiting....
Failed to join domain: Invalid domain role

Thanks,

---

### Post by HermanAB on 2008-10-03
Here is something that may help you debug it:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by vegas588 on 2008-10-03
I have tried a few things as suggested in the article, but no success. 

"Host is not configured as a member server. Invalid configuration. Exiting....Failed to join domain: Invalid domain role"

Would the winbind log file tell me anything? Where is that file?

---

### Post by vegas588 on 2008-10-03
When I issue sudo kinit "myusername@mydomainname.com" it prompts me to enter my password and repleis 

kinit (v5): KDC reply did not match expectations while getting initial credentials

Does that help narrow down the problem for anyone?

---

### Post by 1024260608 on 2011-05-09
[http://en.todaynic.com/](http://en.todaynic.com/)
$6.71  net/org     $7.45 .com    $6.26 .cn
CNNIC,ICANN and HKDNR accredit registar

---

