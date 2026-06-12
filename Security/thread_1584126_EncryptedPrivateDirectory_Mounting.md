---
title: "EncryptedPrivateDirectory Mounting"
date: 2010-09-28
forum: Security
---

### Post by Buzzbait on 2010-09-28
I'm on Ubuntu release 10.04, I've setup my EncryptedPrivateDirectory, and it is working very well. I like my private directory to be unmounted until I need to access the encrypted data, so I've turned off the auto-mount. I've also created a launcher to unmount the private directory when I'm finished with it.

But here's the question. When I mount the private directory, it prompts me to enter my login password. Is there a way to have it prompt me to enter my mount pass phrase instead of my login password?

---

### Post by bodhi.zazen on 2010-09-28
> **Buzzbait said:**
> I'm on Ubuntu release 10.04, I've setup my EncryptedPrivateDirectory, and it is working very well. I like my private directory to be unmounted until I need to access the encrypted data, so I've turned off the auto-mount. I've also created a launcher to unmount the private directory when I'm finished with it.

But here's the question. When I mount the private directory, it prompts me to enter my login password. Is there a way to have it prompt me to enter my mount pass phrase instead of my login password?

Easiest way to do that is to change your log in password from teh command line.

```
passwd
```

Doing that will update your log in password, but not the password to decrypt your home directory.

As long as you do not need X you would be fine.

IMO a better solution would be to make a new crypt , separate from your home directory. If you want a graphical tool to do this try cryptkeeper.

---

