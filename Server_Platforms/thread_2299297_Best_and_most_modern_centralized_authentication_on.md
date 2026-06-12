---
title: "Best and most modern centralized authentication on Ubuntu"
date: 2015-10-17
forum: Server Platforms
---

### Post by dmytro2 on 2015-10-17
Hi everyone) Currently I'm working on a project for which I need to setup centralized authentication system for multiple users and multiple services. I tried ldap but it is usually treated as outdated protcol, also I heard of shibboleth. I need your opinion on what approach and tools are best for centralized authentication which can be combined with other services like web-servers, mail servers etc. 
Thanks)

---

### Post by TheFu on 2015-10-17
LDAP is the solution normally deployed. The FreeIPA server is what enterprises use if they don't use AD.  Were I work, we were lazy and just used the openLDAP built-into Zimbra. Almost all servers that have authentication will have instructions to connect to an LDAP server.

I've honestly never heard of shibboleth. Looks like some sort  of competition to OAuth2, OTP or FIDO U2F. I know that github, google(properties), dropbox and a number of others are deploying FIDO U2F. Sadly, U2F only works with chrome and chromium browsers today. Some Firefox devs are working on it.  Websites with U2F support: [http://www.dongleauth.info/](http://www.dongleauth.info/)

---

### Post by dmytro2 on 2015-10-17
Thanks for your answer, it made myself confident about chosen approach.

---

### Post by TheFu on 2015-10-17
What did  you select?  This is a common issue with lots of  moving parts.

---

### Post by dmytro2 on 2015-10-18
I have selected ldap (implemented in openLDAP). I have already set it up but was not sure if I should use it. Thanks again)

---

