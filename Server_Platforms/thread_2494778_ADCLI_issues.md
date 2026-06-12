---
title: "ADCLI issues"
date: 2024-01-26
forum: Server Platforms
---

### Post by user-abcd on 2024-01-26
Hello,

I have an Ubuntu Server 22.04 running in a VM on ESXi.

It is connected to a local Windows domain via realm. I have set up a HTTP SPN in the domain for kerberos support of the Gitlab application.

After the 30-day renewal, kerberos stops working. As I run adcli update manually, it finds the HTTP SPN and claims to write it to the keytab, but the keytab is never updated.

---

### Post by MAFoElffen on 2024-01-27
Connected through "realm"... Did you happen to mean using 'realmd' through sssd?

---

### Post by user-abcd on 2024-01-29
Possibly...can't claim to be an expert in understanding how all the tools work together.

I use the realm utility/commands to do everything I need and just started digging in trying to determine why the keytab won't update. The exact same setup appears to work fine in Ubuntu 20.

---

### Post by MAFoElffen on 2024-01-30
realmd uses sssd. 

Thinking about Windows AD Polcies that might timeout over a 30 day period... 

Look at your Windows AD policies, and see if there is anything there about password life for any accounts associated with that server... If so, set those account not to expire those passwords.

That would be my first guess on that. Usually the default on passwords in AD is to change them at a month. This works for Workstations, that have interactive users, not so much for Servers.

AD_SSD ad_maximum_machine_account_password_age is set default at 30 days...

RE:
[https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/domain-member-maximum-machine-account-password-age](https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/domain-member-maximum-machine-account-password-age)
[https://funinit.wordpress.com/2017/11/29/how-sssd-updates-machine-account-password/](https://funinit.wordpress.com/2017/11/29/how-sssd-updates-machine-account-password/)
[http://manpages.ubuntu.com/manpages/xenial/man5/sssd-ad.5.html](http://manpages.ubuntu.com/manpages/xenial/man5/sssd-ad.5.html)

---

