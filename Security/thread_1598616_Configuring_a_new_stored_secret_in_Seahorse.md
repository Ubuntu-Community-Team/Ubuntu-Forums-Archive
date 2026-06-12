---
title: "Configuring a new stored secret in Seahorse"
date: 2010-10-16
forum: Security
---

### Post by XVoX on 2010-10-16
Hi everyone!
I've checked pretty much everywhere but couldn't find an answer, so I'm sorry if this is a silly question, but how can I configure a new "stored secret" in Seahorse? Or System > Preferences > Passwords and encryption keys, in a free translation from Brazilian Portuguese "Senhas e chaves de criptografia"? For instance, let's say I want to add a stored secret to be used with Skype: in Seahorse (Ubuntu 10.10), I clicked on Files > New > Stored secret, select the "login" keyring, type "Skype" in the description field and my skype password in the "Password" field and finally click "Add". But when I right-click the new secret > Properties, I can't change or type anything in the "Details" or "Applications" tabs, So, how can I inform Seahorse how, when or with what should it use my secret?

Thank you very much in advance,
XVoX.

---

### Post by FuturePilot on 2010-10-16
I don't think gnome-keyring works this way. The application has to have support for gnome-keyring. If it doesn't then it won't be able to store or retrieve passwords from the keyring even if you manually add them. AFAIK Skype does not have any support for gnome-keyring.

---

### Post by XVoX on 2010-10-17
Thank you very much, FuturePilot!
One thing still bugs me, though: what's the purpose of having a manual "add" then, since we cannot do it ourselves? :confused:

Once again, thanks in advance,
XVoX.

---

