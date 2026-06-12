---
title: "Can password transferred encrypted"
date: 2009-03-19
forum: Security
---

### Post by carlosrowlett on 2009-03-19
Hi

I setup an iSCSI target for storage RAID and hope to access my data on storage RAID anywhere through internet by using initiators. For security concerns, I use dmsetup/luks encrypting all data storage on RAID from initiators side, then all data can be thought safe in both transmission though internet and on RAID if no other interface to access these data.

I want to ask ?

if or not the first password using to open looks volume will expose to internet unencrypted? I have read some about protocol used by iSCSI but I am still not clear about how the password be transferred encrypted or not. 

Any help will be appreciated.

---

### Post by HermanAB on 2009-03-19
If you use SSH to log in and mount volumes then the password is protected.  

Once LUKS mounted a volume, the password is not used again.  The LUKS password is used to decrypt the key and the key is used to decode the the encrypted data.

So, if you use loooooooooooooong passwords for everything and always use SSH to connect to a server then you are OK.

Cheers,

Herman

---

