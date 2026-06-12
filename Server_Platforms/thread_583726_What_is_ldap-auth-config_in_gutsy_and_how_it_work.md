---
title: "What is ldap-auth-config in gutsy and how it work?"
date: 2007-10-20
forum: Server Platforms
---

### Post by Ilya Skorik on 2007-10-20
I answer on all questions in ldap-auth-config debconf, but ldap login don't work!

---

### Post by Ilya Skorik on 2007-10-21
[https://wiki.ubuntu.com/AuthClientConfig](https://wiki.ubuntu.com/AuthClientConfig)


It a great thing!!!

---

### Post by garba on 2007-10-21
indeed, had the same problem here, it looks like the default confguration file for libnss-ldap (for example) is no longer the old /etc/libnss-ldap.conf we were used to, the lib now seems to point to /etc/ldap.conf, and chances are this is is the file libpam-ldap points to as well (dunno for sure cause im using kerb auth)... problem is, /etc/ldap.conf isn't properly populated with the values you provided when cfg'ing the pkg through debconf... to sum it up, this release is giving me a lot of headaches and it's breaking backward compatibility big time (see my other post regarding nfs4)

---

### Post by garba on 2007-10-21
> **Ilya Skorik said:**
> [https://wiki.ubuntu.com/AuthClientConfig](https://wiki.ubuntu.com/AuthClientConfig)


It a great thing!!!

no it isn't, sorry

---

### Post by Ubuntu Warrior on 2007-10-22
We are having the same problems with LDAP auth. Our install procedure for Feisty worked well and Linux workstations were able to logon to the Samba domain without any problems. With Gutsy the system just hangs at booting and breaks the whole login process (can't even access the machine with root???).

Anyway rebooting into recovery mode and taking out the LDAP stuff (nsswitch.conf, etc.) allows the workstation to function as normal.

We will try the ldap-auth-config script to see if this helps.

I agree that the old way of having to set up pam and nss config files was a bit laborious but at least it worked.

We have about 20 Feisty workstation installs in our business and were trying to move these onto Gutsy and roll out a further 30 or so. Until we resolve this we are having to roll out the new workstations on Feisty.

---

### Post by joker-eph on 2007-10-23
I had the same problem, I have just resolved it few hours ago by changing bind_policy from hard to soft.

---

### Post by Ubuntu Warrior on 2007-10-23
Right, we have tried to use the auth-client-config script but this does not work either. The system simply refuses to auth against our OpenLDAP server. When removing and reinstalling the libnss-ldap package and selecting NOT to use deb conf we could use the old libnss-ldap.conf and pam_ldap.conf files to successfully id an LDAP user from the client. However, after booting the system freezes again in the boot process complaining about:

klogd

Any resolution or work-around?

---

### Post by Ubuntu Warrior on 2007-10-23
> **joker-eph said:**
> I had the same problem, I have just resolved it few hours ago by changing bind_policy from hard to soft.

Yep, tried this and it seems to have solved the problem. Can now boot into Gutsy and auth from our OpenLDAP server.

Thanks :)

---

### Post by garba on 2007-10-23
> **Ubuntu Warrior said:**
> Right, we have tried to use the auth-client-config script but this does not work either. The system simply refuses to auth against our OpenLDAP server. When removing and reinstalling the libnss-ldap package and selecting NOT to use deb conf we could use the old libnss-ldap.conf and pam_ldap.conf files to successfully id an LDAP user from the client. However, after booting the system freezes again in the boot process complaining about:

klogd

Any resolution or work-around?

you'd better rely on linss-db, i no longer have nsswithc.conf point directly to ldap but use something like "files db" instead, much better

---

### Post by joker-eph on 2007-10-24
> **Ubuntu Warrior said:**
> 
Any resolution or work-around?


Did you try to 'bind_policy soft' ?

---

### Post by chimney on 2007-10-29
Currently I've used Debian conf to configure for LDAP authentication, and have set the bind policy to soft, and right away I was pulling from my openLDAP server, however when I reboot, it hangs hard.  Is there some subtle detail that I'm missing?   FYI I've gotten Dapper to authenticate with zero problems, using the same settings.

Chimney

---

### Post by garba on 2007-10-29
> **chimney said:**
> Currently I've used Debian conf to configure for LDAP authentication, and have set the bind policy to soft, and right away I was pulling from my openLDAP server, however when I reboot, it hangs hard.  Is there some subtle detail that I'm missing?   FYI I've gotten Dapper to authenticate with zero problems, using the same settings.

Chimney

the reason is simple: your box can't query the ldap server since the network interfaces are brought up later in the boot process, hence the locking... the ldap query takes a lot of time before timing out, at least that's the behaviour I experienced... do yourself a favor and rely on libnss-db and nss-updatedb, it should be fine in a small to mid-sized environment

---

### Post by chimney on 2007-10-30
Thanks for the advice man, I just still can't wrap my brain around why with the Bind_policy set at soft, it still hangs.  Crazy.  But again thanks for the advice.  

Chimney

---

