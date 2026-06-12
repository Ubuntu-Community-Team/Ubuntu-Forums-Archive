---
title: "Google Chrome update: GPG error and missing public key"
date: 2017-08-05
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2017-08-05
In case people encounter```

W: GPG error: http://dl.google.com/linux/chrome/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6494C6D6997C215E
W: The repository 'http://dl.google.com/linux/chrome/deb stable Release' is not signed.
```
this can be fixed with
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6494C6D6997C215E
```Or```
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```

---

### Post by monkeybrain20122 on 2017-08-05
Thanks. Just saw this error when updating a few minutes ago, fixed.

---

### Post by MarlonNelson on 2017-08-06
Thanks.  Very helpful.

---

