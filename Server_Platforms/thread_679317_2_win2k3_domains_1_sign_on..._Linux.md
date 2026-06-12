---
title: "2 win2k3 domains 1 sign on... Linux???"
date: 2008-01-26
forum: Server Platforms
---

### Post by joescpusupport on 2008-01-26
Hello everyone... I have a wierd situation... I have two windows 2k3 server machines... one is SBS, one is STD. R2... I can't configure a trust due to SBS EULA and default config... my issue is with a HP MFP device which uses digital sending software to auth. with the DC's OR a LDAP Gateway... (software can only retain 1 set of credentials) so since the DC's won't talk to eachother through trusts... HP says use a LDAP gateway for a single set of credentials for both domains... does anyone have an idea as to how to accomplish this goal with Ubuntu or any other linux setup???

Thanks,
                 Joe

---

### Post by HermanAB on 2008-01-26
Uhhh... uhmmm... I suggest that you go to the Samba web site and study The Official Howto.  The answer is in there Sculley...

CHeers,

Herman

---

### Post by Maxtorm on 2008-01-27
> **joescpusupport said:**
> HP says use a LDAP gateway for a single set of credentials for both domains... does anyone have an idea as to how to accomplish this goal with Ubuntu or any other linux setup???
There is a very good step-by-step tutorial for setting up LDAP, Samba etc. here [http://www.linewbie.com/2008/01/configure-openldap-samba-domain-controller-on-ubuntu-710.html](http://www.linewbie.com/2008/01/configure-openldap-samba-domain-controller-on-ubuntu-710.html)

However, as I'm sure you realize, you're then going to have to configure the servers to use the LDAP server for authentication. Things could get messy in a hurry. Are we talking an HP4345? If so, and depending on how many users we're talking about, have you considered using PIN-based authentication?

---

### Post by joescpusupport on 2008-01-27
> **Maxtorm said:**
> There is a very good step-by-step tutorial for setting up LDAP, Samba etc. here [http://www.linewbie.com/2008/01/configure-openldap-samba-domain-controller-on-ubuntu-710.html](http://www.linewbie.com/2008/01/configure-openldap-samba-domain-controller-on-ubuntu-710.html)

However, as I'm sure you realize, you're then going to have to configure the servers to use the LDAP server for authentication. Things could get messy in a hurry. Are we talking an HP4345? If so, and depending on how many users we're talking about, have you considered using PIN-based authentication?



Actually Maxtorm, I have an HP 9500 MFP, and the DSS 4.0 for the send to folder option... The HP DSS support division is who told me to use a LDAP gateway of some sort...

---

