---
title: "Auto input the password for the encryption disk during boot up"
date: 2010-04-26
forum: Server Platforms
---

### Post by ivancheng on 2010-04-26
Hi,

I would like to known whether I can configure the server to input the password for the encryption disk automatically during boot up.  Is it possible?

Thanks in advance.

Rgds,
Ivan

---

### Post by iponeverything on 2010-04-26
humm.. doesn't that defeat the purpose of encryption?

---

### Post by ghost_ryder35 on 2010-04-26
> **iponeverything said:**
> humm.. doesn't that defeat the purpose of encryption?

+1

Just remove encryption

---

### Post by cdenley on 2010-04-26
I believe you can store the key on a USB drive, so it will boot up without a password if the USB drive is connected. If you keep the key and the encrypted filesystem at the same physical location, though, then anyone with physical access can easily decrypt your filesystem, which defeats the purpose of encryption.

---

