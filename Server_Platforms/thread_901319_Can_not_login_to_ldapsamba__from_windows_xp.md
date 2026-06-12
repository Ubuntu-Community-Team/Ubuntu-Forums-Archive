---
title: "Can not login to ldap/samba  from windows xp"
date: 2008-08-26
forum: Server Platforms
---

### Post by cmare on 2008-08-26
I did the tutorial from: [link to tutorial]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10") to setup the ldap/samba domain controller.

Now I can join the domain in the win XP, but when I want to login I get the message: "Windows can not connect to the domain, either because the domain controller is down or otherwise unavailable, or  because your computer account was not found. ...."

In the /var/log/samba/log.versor-laptop I get:

[2008/08/26 15:54:49, 0] rpc_server/srv_netlog_nt.c:get_md4pw(258)
  get_md4pw: Workstation LAPTOP-VERSOR$: account is not a trust account
[2008/08/26 15:54:49, 0] rpc_server/srv_netlog_nt.c:_net_auth_2(461)
  _net_auth2: failed to get machine password for account LAPTOP-VERSOR$: NT_STA$

Does any one has a clue?

---

### Post by CraigInParadise on 2008-08-27
Um, did you do step 13?  
 >  Step 13: Add a workstation account to LDAP

This tutorial is meant to create an opensource domain for Windows XP Professional client (and Linux clients) to authenticate against. Therefore we will add a workstation account for the Windows XP Professional workstation that we will be joining to the domain.

# Execute the command:

smbldap-useradd -w client-winxp

* "client-winxp" is the hostname of the computer that you will be adding to the domain. This must be very specific!

In your case, you should use [COLOR="Red"]LAPTOP-VERSOR[/COLOR] instead of [COLOR="Red"]client-winxp[/COLOR].

The error message indicates no workstation account for the computer you are trying to add to the domain.

---

### Post by cmare on 2008-08-27
> **CraigInParadise said:**
> Um, did you do step 13?  
 

In your case, you should use [COLOR="Red"]LAPTOP-VERSOR[/COLOR] instead of [COLOR="Red"]client-winxp[/COLOR].

The error message indicates no workstation account for the computer you are trying to add to the domain.


But it is! I did created. When I look at the LDAP Users-Groups in the webmin I see: laptop-versor$. And I did created it with writte (-w).

---

### Post by cmare on 2008-08-28
I did remove the laptop-versor host and again added with: smbldap-useradd -w laptop-versor. But no changes. I can not log in.
I did try to add some another hosts and login to the domain over them but it is all the same.

I really don't know what to do. Pleas help me.:-?

---

