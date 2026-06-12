---
title: "Howto create a Ubuntu PC network with central logon"
date: 2011-11-24
forum: Server Platforms
---

### Post by ruffieux on 2011-11-24
Hello,

I am deploying 3 Ubuntu PC's in a network of which one is a server providing file and print services.

Now I would like to get a configuration where everybody can login at every PC by having always the same username and password and the same user settings.

In a nutshell I would like to get the same configuration you have today in a professional Windows Network where the userprofile follows the user.

Is this feasible with Ubuntu? I only found articles talking about Samba with Windows clients.

Any ideas would be appreciated.

Thanks

Heinz

---

### Post by darkod on 2011-11-24
Does this help starting you off?
[https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html)

Just google for something like "roaming profiles in ubuntu network"...

---

### Post by ruffieux on 2011-11-24
> **darkod said:**
> Does this help starting you off?
[https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html)

Just google for something like "roaming profiles in ubuntu network"...

Thanks Darko

Yes, I am aware of the Samba server but Samba is to be used - at least to my best knowledge - with Windows clients. I want to do the same but with pure Ubuntu client PC's

Any other ideas?

Heinz

---

### Post by darkod on 2011-11-24
The beginning of that link says:
Although it cannot act as an Active Directory Primary Domain Controller (PDC), a Samba server can be configured to     appear as a Windows NT4-style domain controller.

My understanding is that it will not be the same as AD, but it can serve as PDC equivalent to the older NT4.0 style. It never says you need to have Windows Server running the show.

The way I understand it is that you can run this as ubuntu-only network.

PS. Don't view samba only as sharing point for windows/ubuntu mixed network. I haven't used it much, but I guess it has many features and this seems to be one of them.
As a separate step you will probably need to investigate how to add ubuntu client to the samba PDC server/domain. But google helps with this too.

---

