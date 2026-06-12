---
title: "Public/private keys on multiple servers"
date: 2010-03-26
forum: Security
---

### Post by Zendal on 2010-03-26
At the moment we have one SSH server with the private key being on a usb flash drive, and the public key being on the server in *authorized_keys2*.
 
Now that three more servers are coming online, should we generate new keys, so we have muliple private and public keys (one pair for each server), or use the same two keys to access all the servers 
 
thanks

---

### Post by CharlesA on 2010-03-26
I suppose it would be a security vs convience issue. If you lost the private key, you would be SoL.

That being said, I would just use the same key unless it was a highly mission critical server. If that was the case, a new key with a different passphrase would be used.

---

### Post by OpSecShellshock on 2010-03-26
There are both security and business continuity considerations. One tiny USB drive is easy to lose or damage, and is also easy to copy. In one case, you're locked out of four servers, and in the other someone else potentially gets into four servers for the price of one. It really depends on the specifics of the operation and how access to the USB drive is tracked. It might be a good idea to have more than one (but not necessarily four) so that you can still run at partial capacity in the event of unforeseen loss/damage. Much as I hate to say it, it's kind of a management decision.

---

### Post by stlsaint on 2010-03-26
+1 for above poster. I say make one more key pair "just in case" you so happen to lose track of your main one you can still have access to your servers. And with this backup key pair keep them somewhere locked up and or safe. IE: Not used on daily basis.

---

### Post by CharlesA on 2010-03-26
> **stlsaint said:**
> +1 for above poster. I say make one more key pair "just in case" you so happen to lose track of your main one you can still have access to your servers. And with this backup key pair keep them somewhere locked up and or safe. IE: Not used on daily basis.
+1 to the backup pair.

---

### Post by Zendal on 2010-03-27
Thanks to all.
 
I will follow the advice of the single key with a "backup pair"

---

