---
title: "Apache authentication of Samba Domain users with PAM"
date: 2007-07-07
forum: Server Platforms
---

### Post by kineosven on 2007-07-07
Hello,

I would like to get Apache2 to authenticate certain web directories against the Samba domain users on the same machine (Feisty server).

I am running Samba (as domain controller) and Apache2 as general web server on the same server (not ideal but I only have the one server). I have installed libapache2_mod_auth_pam and so far, I can authenticate any users that have a password for the actual server. If I try to log on as a domain user and supply my Samba domain password, the login is refused.

Is there any way of getting Apache to use the samba users and passwords?

---

### Post by jamessnell on 2008-07-15
I'd also like to see notes on this. I have a fairly similar setup. My SMB server however authenticates with a Win2K3 Active Directory server using WinBind/Kerberos. I'd like apache to authenticate in the same way. I suppose at this point I just need to find a means of Authenticating Apache using "system users".

---

