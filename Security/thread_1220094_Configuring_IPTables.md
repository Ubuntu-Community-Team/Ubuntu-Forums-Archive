---
title: "Configuring IPTables"
date: 2009-07-22
forum: Security
---

### Post by Victor43 on 2009-07-22
Hello all.  I am trying to follow the following tutorial here [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) but need some help.  I would like to be able to configure outbound access based on application names ? Another words I would like to enable Firefox access to the internet and same goes for gFTP only. How do I go about allowing these two applications access to the internet ? What rule set do I configure ?  Also I don't wish to allow any inbound traffice and only the outbound traffic and the inbound traffic associated (reply traffic)  I am pretty sure that I don't need any forwarding rules either.  Thanks in advance  Victor

---

### Post by cdenley on 2009-07-22
This is not possible (anymore) with iptables. I just noticed that they removed this option from the iptables manpage, so I guess they're not planning on fixing it. Maybe apparmor can do something like this.

---

### Post by Victor43 on 2009-07-23
Thank you for the reply. I will look into AppArmor.

---

### Post by bodhi.zazen on 2009-07-23
aa profiles here : [http://bodhizazen.net/aa-profiles](http://bodhizazen.net/aa-profiles)

and see the apparmor sticky at the top of these forums for additional information.

---

