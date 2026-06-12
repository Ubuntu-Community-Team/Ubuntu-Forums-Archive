---
title: "How are Ubuntu mirrors verified?"
date: 2016-05-07
forum: Security
---

### Post by pants2 on 2016-05-07
If I use a mirror, how do I know that an update file or package hasnt been replaced with something else (either by an outside attacker or by someone who works on the mirror)? I see that archive mirrors update once every six hours,  do these updates ensure that the mirror is 100% the same as the original (like a hash check)?* Could someone change the files in between these updates? When I download something on my end is there a hash check?Has there ever been a case where a mirror was used to spread viruses on Linux?

---

### Post by khelben1979 on 2016-05-07
I've been using Linux since 1999. I've never received any viruses or trojans on my system on this period which caused any type of harm. However, you're right to be cautious. Avoid being logged in as root is a good idea and will get sufficient protection, i.m.o. 

As long as you use verified mirrors by your distribution, you've chosen to trust your distribution, and unlike MS Windows which can cause harm to your system in all possible ways, you don't have those issues with Linux. The root user of the system is most likely to cause the maximum possible harm to the system (if not being careful) i.m.o, so you can definitely relax over there! Don't use mirrors for software packages not approved by your distro, unless you know what you're doing. Hope this helps!

---

### Post by DuckHook on 2016-05-07
*Thread moved to **Security** as the more appropriate forum.*

Approved mirror sites do undertake to hash check all files that they mirror, but in the end, all you've got is their word on this. Your upgrade downloads are also hash checked as part of the upgrade process itself, but only with the mirror file. If a bad guy changes a file in the mirror, there is no way for the average bear to know. You are right to note this as a security risk. Gurus could hash check against the original files in the master repository I suppose, but I don't know how to do this and have never felt the need.

As with all distributed models of software provisioning, it's based on a chain of trust. And as with all chains, this one is only as strong as its weakest link. In order to qualify as an official mirror site, mirrors have to meet some Ubuntu standards. I don't know the process by which Canonical oversees or enforces those standards.

It is theoretically possible for a rogue insider to change a mirror file. Many papers have been written about this vulnerability. I don't know of any real world occurrence in Ubuntu of such an exploit.

Unfortunately, security is not amenable to binary solutions. It is invariably comprised of shades of grey. At some point, we are forced to trust somebody, else we won't be able to get anything done. However, your instincts are good to question these matters.

---

### Post by grahammechanical on 2016-05-07
Packages are encrypted by the maintainer using public-key cryptography. The Ubuntu developers have recently deprecated use of the SHA-1 standard in favour of the SHA-2 standard. 

> Message authentication involves [hashing]("https://en.wikipedia.org/wiki/Cryptographic_hash_function") the message to produce a "digest," and encrypting the digest with the private key to produce a [digital signature]("https://en.wikipedia.org/wiki/Digital_signature").  Thereafter anyone can verify this signature by (1) computing the hash  of the message, (2) decrypting the signature with the signer's public  key, and (3) comparing the computed digest with the decrypted digest.  Equality between the digests confirms the message is unmodified since it  was signed, and that the signer, and no one else, intentionally  performed the signature operation &#8212; presuming the signer's private key  has remained secret.

The security of such procedure depends on a hash  algorithm of such quality that it is computationally impossible to alter  or find a substitute message that produces the same digest

[https://en.wikipedia.org/wiki/Public-key_cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)

[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

[https://wiki.ubuntu.com/Mirrors#Country_mirror_requirements](https://wiki.ubuntu.com/Mirrors#Country_mirror_requirements)

If you go to System Settings>Software & Updates>Authentication you will find a list of public keys that are used by the system to verify that the packages downloaded by Apt have not been tampered with.

Regards

---

### Post by pants2 on 2016-05-08
Thank you for your answers! Forgive me if I am mistaken but do the answers of Duckhook and grahammechanical conflict? If an update file on a mirror is replaced with a virus, am I right to believe that Ubuntu will not update with that virus as long as the private key is not compromised?

---

### Post by DuckHook on 2016-05-08
> **pants2 said:**
> Thank you for your answers! Forgive me if I am mistaken but do the answers of Duckhook and grahammechanical conflict? If an update file on a mirror is replaced with a virus, am I right to believe that Ubuntu will not update with that virus as long as the private key is not compromised?grahammechanical's answer is the correct one. The binary is signed at the point it is approved by Canonical and any variance should be evident to apt, which will refuse to install a questionable download.

---

### Post by pants2 on 2016-05-10
Understood. Thanks again for the answers!

---

