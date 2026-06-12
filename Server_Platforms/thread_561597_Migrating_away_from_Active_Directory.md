---
title: "Migrating away from Active Directory"
date: 2007-09-27
forum: Server Platforms
---

### Post by schase02 on 2007-09-27
Howdy folks, 

I'm intending/desiring to move my servers away from Active Directory and onto a Linux platform.  I already have a Ubuntu Server running Bind as secondary. (actually I hope to move all 50 workstations to Ubuntu in the future also).

But what would be the counterpart?  I've got mostly XP pro clients, some OSX though.  What I've read is to use Bind & OpenLDAP & Samba.

I do need to do file and printer sharing and possibly roaming profiles - although being able to authenticate in a domain environment no matter the workstation is a must.

And any tutorials?  I spotted one but that was for the desktop version instead of the server one.

Also - what about if I ran two servers, one as PDC the other as BDC?

Thanks for the inputs.

---

### Post by HermanAB on 2007-09-27
I wish I could move away from Active Directory...

Anyhow, the solution is to use Samba for domain authentication.  You can move the settings over to Linux using the 'net rpc vampire' command, which sucks the brains out of the Windows server!

Cheers,

Herman

---

### Post by rennen01 on 2007-09-28
Here are some links to get you started:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)

I would do alot of reading on Samba.  If you have the budget, bring up a Samba Server in a test environment with an XP Client and see if that will work for you.

Good luck.

---

### Post by netlogic on 2007-09-28
It will be not exactly you are looking for...
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by schase02 on 2007-09-28
lol suck the brains out.

Thank you everybody, I shall get out my reading glasses.:popcorn:

---

