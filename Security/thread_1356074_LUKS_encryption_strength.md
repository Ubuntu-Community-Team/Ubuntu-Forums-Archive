---
title: "LUKS encryption strength"
date: 2009-12-15
forum: Security
---

### Post by DouglasAWh on 2009-12-15
I've asked in IRC and done some searching, but no answers yet.  

It's a pretty simple question.

What's the default encryption strength when you use the alternate CD encryption method?

Thanks!

---

### Post by rookcifer on 2009-12-15
Aes-256 but you can change it to 128 or 192.  You can also change it to another cipher completely.

---

### Post by DouglasAWh on 2009-12-15
> **rookcifer said:**
> Aes-256 but you can change it to 128 or 192.  You can also change it to another cipher completely.

Fantastic!  This is a legal question actually.  Where is this documented or how can I check the current encryption?

---

### Post by FuturePilot on 2009-12-15
> **DouglasAWh said:**
> Fantastic!  This is a legal question actually.  Where is this documented or how can I check the current encryption?

```
sudo cryptsetup luksDump /dev/sdaX
```

Replace X with the partition number

You'll get something like this 

```
Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
```

---

### Post by DouglasAWh on 2009-12-15
> **FuturePilot said:**
> ```
sudo cryptsetup luksDump /dev/sdaX
```

Replace X with the partition number

You'll get something like this 

```
Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
```

merci beaucoup!

---

### Post by panneers740 on 2009-12-17
Both approaches have their right to existence although they usually will be found in different scenarios. 
A cryptographic file system with its per-user keying and lower administrative burden is suited when data confidentiality has to be provided on multi-user machines in an Intranet. Security drawbacks like leaking metadata information are either acceptable within corresponding threat models or are the price in a risk-benefit trade-off. 
Sector-level encryption offers a higher degree of security and is primarily indicated in situations with single-user standalone boxes.
More administrative work is acceptable because the work is usually limited to one standalone computer whereas in a company-based network with hundreds of clients workload may be prohibitive.

Because this site is mainly about protecting the "cold" disks of a laptop or single PC, a detailed comparison will be carried out only for the sector level encryption systems.
==================
[automotive air conditioning compressor](http://www.1airconditioning.com/)
[chicago wedding limo](http://www.chicagolimousine1.com)

---

