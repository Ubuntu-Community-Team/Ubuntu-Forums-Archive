---
title: "How to encrypt chat log in Pidgin?"
date: 2010-10-30
forum: Security
---

### Post by fjkum on 2010-10-30
I know Pidgin store chat log in plain text or HTML format.
Is there any plugin for pidgin to encrypt the chat log while logging it?

Similar to Windows version of MSN Messenger free application called MSNPlus! that contains this feature to encrypt chat log.

---

### Post by OpSecShellshock on 2010-10-30
If the chat log is stored under your home directory and your home directory is encrypted, then you should be in good shape already (it won't be encrypted when you're logged on with a desktop session, but it will be when it's turned off).

---

### Post by peculiar penguin on 2010-10-30
I would (and do) simply encrypt everything so I don't have to think about this for every single application.
If you really want a partial solution, set up LUKS/TrueCrypt/EncFS/... and tell Pidgin to store its profile directory on that file system (pidgin --config=/path/to/profile/directory). If you have an existing profile, copy it there first, obviously.

---

