---
title: "T/fer a Tiny CA cert to a Windows Server 2003?"
date: 2010-04-14
forum: Security
---

### Post by Dikko on 2010-04-14
At work we are trying to avoid paying for a cert for our outlook owa.  I thought of Tiny CA, but can't find a windows variant, it appears to depend on things that would not allow that.

Does anyone know if it is possible to create a Tiny CA Cert and install it on a Windows Server 2003?  If not does anyone know of a good free Cert creation utility for Winedoze.  

I have a feeling this is going to be another feather in the basket to convince my boss to go Ubunutu.

Cheers All,
Rick.

---

### Post by OpSecShellshock on 2010-04-14
Honestly I'd recommend not using OWA (when you allow an employee's home computer to connect to your enterprise mail server, there's a huge risk of exposing Active Directory credentials, among other things). You'd avoid the whole CA issue by using VPN.

---

