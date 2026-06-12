---
title: "Authentication against Kerberos and Windows AD"
date: 2011-08-22
forum: Server Platforms
---

### Post by ranjithmurugan on 2011-08-22
I am trying to setup an kerberos server and authenticate with Windows AD. 

Environment: Kerberos in Ubuntu 10.10
AD: Windows 2003 R2
The DNS has be configured correctly, Clock sync has be done. 

While trying to login to the system using the kerberos server, there is an error msg.

NEEDED_PREAUTH: Additional pre-authentication required.

Has anyone face this issue while setting up kerberos? 

Regards,
Ranjith.

---

### Post by Fiddler_Wins on 2011-08-22
You've got two options. You can install samba, set it to use Security=ADS or you can manually create a keytab file and add it to the server.

As an alternative you can remove the requirement for pre-auth on the user accts that will need to log into the server - go to ADUC, select the user and on the account tab check "Do not require Kerberos preauthentication"

---

