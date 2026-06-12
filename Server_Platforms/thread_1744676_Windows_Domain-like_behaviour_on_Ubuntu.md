---
title: "Windows Domain-like behaviour on Ubuntu"
date: 2011-04-30
forum: Server Platforms
---

### Post by listerthrawn on 2011-04-30
Hi,

I'm looking at creating a Windows style domain but with Ubuntu.  I'm pretty sure I can get most of the functionality I require with LDAP and Kerberos but I have some laptop users and I was interested to see if it can function like Windows does with 'Cached Credentials'.  

Basically, Can I get an ubuntu laptop to authenticate with LDAP while it is on the network, but when it is away and has no connectivity, can the user still log on with the same password?  

Just to clarify, this is a solely Linux exercise.  I'm not looking for an AD replacement that Windows can connect to, I would just like Windows style behaviour with authentication.

Thanks

---

### Post by headvampyre@hotmail.co.uk on 2011-05-02
Hi, SSO(Single Sign On) is possible with ubuntu, but for pushing user policies, user/machine scripts etc, its gonna be a LOT different and probably a fair amount harder than with AD. You could achieve a setup with NIS(google it), which can make use of an LDAP server and im sure it can work with kerberos.

---

### Post by DavePlummer on 2011-05-02
This may help: [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto).

---

### Post by listerthrawn on 2011-05-02
I'm quite happy about the pushing of policy etc.  It's solely for authentication that I want this behaviour.  Basically I want it to be nice and easy for the user so that if they change their password on the network they can still log in when away from the network.  If this is possible to configure, do you have any advice on how to achieve it?

Thanks for your reply.

Chris

---

### Post by listerthrawn on 2011-05-02
> **DavePlummer said:**
> This may help: [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto).
Thanks for the link.  It looks like just what I'm trying to achieve.

---

### Post by bobmct on 2011-05-02
Trying to accomplish the same this I found Resara Server, an open source active-directory like facility that runs on Ubuntu.  Works quite well.  And if support is absolutely required they offer a commercial version.

---

### Post by collisionystm on 2011-05-02
> **listerthrawn said:**
> Hi,

I'm looking at creating a Windows style domain but with Ubuntu.  I'm pretty sure I can get most of the functionality I require with LDAP and Kerberos but I have some laptop users and I was interested to see if it can function like Windows does with 'Cached Credentials'.  

Basically, Can I get an ubuntu laptop to authenticate with LDAP while it is on the network, but when it is away and has no connectivity, can the user still log on with the same password?  

Just to clarify, this is a solely Linux exercise.  I'm not looking for an AD replacement that Windows can connect to, I would just like Windows style behaviour with authentication.

Thanks


The answer to your problems.

[http://www.zentyal.com/](http://www.zentyal.com/)

---

### Post by elwarreno on 2012-01-17
i would also consider looking at Resara Server, which has just released its 1.1 version with multi-server replication and load balancing.  the open source version can be found at [http://www.resara.org]("http://www.resara.org")

---

