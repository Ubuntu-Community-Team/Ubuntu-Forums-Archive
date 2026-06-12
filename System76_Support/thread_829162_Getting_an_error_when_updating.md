---
title: "Getting an error when updating"
date: 2008-06-14
forum: System76 Support
---

### Post by z01nx on 2008-06-14
I have been getting this error when using the update manager and since upgrading to hardy heron. Can someone help me out, I like to make sure I am up to date. Thanks. 

> W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2F355BA8FB4A41C3

---

### Post by freduardo on 2008-06-14
You probably just need to re-import the key.

Open up a terminal and issue:

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

That should fix it.

---

### Post by z01nx on 2008-06-14
That fixed it, thank you.

---

