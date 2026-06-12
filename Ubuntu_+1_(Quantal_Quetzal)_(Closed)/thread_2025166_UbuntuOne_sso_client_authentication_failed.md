---
title: "UbuntuOne sso client authentication failed"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ti_tux on 2012-07-14
Hi everybody,

I'm having trouble with ubuntuone sso client in 12.10 : I cannot log in my account... There is a problem with python library I think... I attached the sso client log file. 

Thanks for any help.

---

### Post by mc4man on 2012-07-14
May not be a 12.10 issue, no doubt that ubuntuone/sso break down on occasion

For starters I'd take a read here, [https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/](https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/)

if going the delete token route then I don't think Passwords and keys is in system settings. Just search pass in the Dash or run - 

seahorse

Ubuntuone installed & set up here fine (using prior SSO account

---

### Post by ti_tux on 2012-07-14
Maybe it is not a 12.10 issue but I test Kubuntu 12.10 so.. And on 12.04 it works correctly. On kubuntu it is KWallet for password, etc not seahorse. Ubuntuone does not need it but need gnome-keyring. Moreover, gnome-keyring does not launch any pop up for asking my password whereas on 12.04 it did. So there is a problem on 12.10 (in addition of the lack of integration in Kubuntu) that I do not understand.

The ubuntuone faq does not help me. I uninstall then reinstall and it's the same way...

For the sso log, it seems that there is a problem with python 2.7 but I am not an expert in python nor in U1.

Thanks for your reply.

---

### Post by ti_tux on 2012-07-14
I uninstall all python libraries,  gnome-keyring and other gnome libs with --purge and some rm -rf out of X session... I've reinstalled ubuntuone and so python libs and it solves my problem. I do not understand why this problem happened with python libs. But it re-works so sorry for  the noise !

---

