---
title: "LDAP - Windows Login possible?"
date: 2013-03-18
forum: Server Platforms
---

### Post by Bathroth on 2013-03-18
Hey People,

i searched in the Internet and i am not sure about it now.

Is it possible to login with the LDAP-credentials over the LDAP-Domain name with windows or ubuntu, WITH a Standalone LDAP?

So in some words ...
ldap-server
windows client
no samba!!!
domain login

???

I searched in the internet and now im not so sure about it if its possible or not. Like i understood its only possibler with samba in frontend and LDAP in backend?!

Also another question. OpenLDAP is a diffrent 3rd-party service/program like LDAP right? is it possible with OpenLDAP either/neither ... ?

I know this Topic is old. And was answered 10000000 times. But everywhere i read diffrent stuffs and now i want be sure and clear about this question!

Regards,
Bathroth

---

### Post by schragge on 2013-03-18
Not sure if I correctly understand your question, but I successfully use [pGina]("http://pgina.org") to login on Windows with LDAP credentials (both Windows XP and Windows 7). It has an [LDAP authentication plugin](http://pgina.org/docs/v3.0/ldap.html).

---

### Post by Bathroth on 2013-03-18
> **schragge said:**
> Not sure if I correctly understand your question, but I successfully use [pGina]("http://pgina.org") to login on Windows with LDAP credentials (both Windows XP and Windows 7). It has an [LDAP authentication plugin]("http://pgina.org/docs/v3.0/ldap.html").

It seems yes, you understood my question. 

My question is if it is possible to login with a windows Client to LDAP without combining LDAP and Samba.

So Standalone LDAP, without samba (thats the important part)

Tomorrow ill watch ur links.

Regards,
Bathroth

---

### Post by schragge on 2013-03-18
There's nothing that prevents logging in without Samba, but obviously each user will get a local profile, as remote user profiles centrally stored on the Samba server woudn't be available.

---

