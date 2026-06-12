---
title: "Cryptsetup: Command Failed"
date: 2007-07-08
forum: Server Platforms
---

### Post by dbee on 2007-07-08
So I've installed the cryptsetup package from the universe repo. I've created a partition and I've checked it for badblocks and added noise.

When I try to do a 
> 
root@mysystem: cryptsetup --verbose --verify-passphrase luksFormat /dev/sda3


It gives me the warning to tell me that all my data on that partition will be erased. I continue and then it just tells me 'Command Failed'.

I've tried encrypting a local file instead, but I get the same result. I also tried to encrypt the partition from a live cd. Same issue.

Can anyone help ?

Thanks

---

### Post by dbee on 2007-07-10
Is it just me, or is the standard of support on these forums gone way down ?

---

