---
title: "iFolder Admin Login Issues"
date: 2011-03-11
forum: Server Platforms
---

### Post by rbeier1221 on 2011-03-11
I followed the instructions [here]("https://help.ubuntu.com/community/iFolderInstall") for installing iFolder on Ubuntu. I am currently running Ubuntu server 10.04.1 64bit. I can access the admin area just fine, but when I try to log on it fails and tells me the username and password are incorrect. I have looked at simias.config to verify the information, yet it still will not work. If anyone can help point me in the right direction it would be greatly appreciated! 

Here is the information pulled from Simias.log: (if you need the entire log let me know)

service started. 2011-03-11 15:44:33,430 [Simias Manager Start] INFO  Simias.Service.Manager - Services started. 2011-03-11 15:44:38,995 [-1125591296] DEBUG Simias.Security.Web.AuthenticationModule - In verify[rincipalfromrequest: soapmethod is GetAuthenticatedUser 2011-03-11 15:44:38,999 [-1125591296] DEBUG Simias.DomainProvider - domainID f586a03d-cc4c-4119-be93-55985d2488b2 2011-03-11 15:44:39,000 [-1125591296] DEBUG Simias.Server.Authentication - OwnsDomain called 2011-03-11 15:44:39,000 [-1125591296] DEBUG Simias.Server.Authentication -   with domain: f586a03d-cc4c-4119-be93-55985d2488b2 2011-03-11 15:44:39,001 [-1125591296] DEBUG Simias.Server.Authentication -   returning true 2011-03-11 15:44:39,003 [-1125591296] DEBUG Simias.Server.Authentication - Authenticate called 2011-03-11 15:44:39,037 [-1125591296] INFO  Simias.Server.Authentication - InvalidCredentials : admin 2011-03-11 15:44:39,042 [-1125591296] DEBUG Simias.Server.Authentication - id.Auth : localhost ip is :[http://sos-ubuntu1:80/simias10](http://sos-ubuntu1:80/simias10) 2011-03-11 15:44:39,043 [-1125591296] DEBUG Simias.Server.Authentication - id.Auth : this persons homeadd ip is :[http://sos-ubuntu1:80/simias10](http://sos-ubuntu1:80/simias10) 2011-03-11 15:44:42,490 [-1291204864] DEBUG Simias.IdentitySync.Service - No registered identity sync providers - disabling sync service

---

### Post by stmiller on 2011-03-13
I tried to get ifolder going with much headache and never got it to work. 

Here is another promising alternative that works like dropbox:

[http://sparkleshare.org/](http://sparkleshare.org/)

:/

---

### Post by druhboruch on 2011-03-13
Try this link:
[http://ubuntuforums.org/showthread.php?t=1678600&highlight=ifolder](http://ubuntuforums.org/showthread.php?t=1678600&highlight=ifolder)

---

### Post by sourn on 2011-07-07
Hi,
I have issue with installation ifolder server whit LDAP...
I've install ifolder like this [https://help.ubuntu.com/community/iFolderInstall#Installing](https://help.ubuntu.com/community/iFolderInstall#Installing) Simias
And then install and configure my LDAP server. When I try to login from [http://mydomain/admin](http://mydomain/admin) (real domain change to mydomain)
in log files from ifolder I have next error
```

2011-07-07 19:33:35,614 [-1247569040] DEBUG Simias.Security.Web.AuthenticationModule - In verify[rincipalfromrequest: soapmethod is GetAuthenticatedUser
2011-07-07 19:33:35,615 [-1247569040] DEBUG Simias.DomainProvider - domainID f9b95974-f906-472d-a4d9-f08972d12941
2011-07-07 19:33:35,615 [-1247569040] DEBUG Simias.SimiasException - The specified domain does not exist.
Simias.Storage.DoesNotExistException: The specified domain does not exist.
2011-07-07 19:36:18,686 [-1240077456] DEBUG Simias.Security.Web.AuthenticationModule - In verify[rincipalfromrequest: soapmethod is 
2011-07-07 19:36:18,689 [-1240077456] DEBUG Simias.DomainProvider - domainID f9b95974-f906-472d-a4d9-f08972d12941
2011-07-07 19:36:18,690 [-1240077456] DEBUG Simias.SimiasException - The specified domain does not exist.
Simias.Storage.DoesNotExistException: The specified domain does not exist.

```

Have any ideas how to fix it?

---

