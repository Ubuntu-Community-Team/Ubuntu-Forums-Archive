---
title: "Help me lock down my computer"
date: 2010-01-17
forum: Security
---

### Post by Revolutionary101 on 2010-01-17
I am currently trying to make my computer as secure as it can possibly be. I am configuring the firewall to be restrictive by default, but I have some programs that are still unable to connect to the internet.

1. Pidgin Internet Messenger (I use AIM and MSN)
2. Skype

Could anyone help me make my system as secure as possible?

---

### Post by rookcifer on 2010-01-17
> **Revolutionary101 said:**
> I am currently trying to make my computer as secure as it can possibly be. I am configuring the firewall to be restrictive by default, but I have some programs that are still unable to connect to the internet.

1. Pidgin Internet Messenger (I use AIM and MSN)
2. Skype

Could anyone help me make my system as secure as possible?

If you're trying to restrict outbound connections, then you will obviously have to know which ports skype and Pidgin use to connect.  You could allow them to connect by turning the firewall off, then run netstat to see which ports are being used, and finally, enter those ports as exceptions to your firewall ruleset.

Then I suggest you ready the security sticky, if you haven't already.  Lots of good advice there.

Then study up on AppArmor if you are really paranoid.  There is also a sticky on it.

---

### Post by garryknight on 2010-01-17
I don't use Pidgin so I can't help you there. I do use Skype and I notice that on the Advanced tab of the Options dialog, it has an option where you select which port Skype uses for incoming connections. Mine is still set to the default 23399. You could open that port in your firewall, or if you want paranoia-level security, open another port and tell Skype to use that instead.

---

### Post by Revolutionary101 on 2010-01-17
Thanks for the help. I will be sure to check the sticky threads on security.

---

