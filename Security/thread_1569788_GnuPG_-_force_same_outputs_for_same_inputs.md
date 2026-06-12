---
title: "GnuPG - force same outputs for same inputs"
date: 2010-09-07
forum: Security
---

### Post by saverio.miroddi on 2010-09-07
I observed that GnuPG encrypted output is different each time I encrypt some input, even if the input is the same.  Is there any way to make two outputs be the same if two input data sets are the same?  Thanks! Saverio

---

### Post by rookcifer on 2010-09-07
It's because the session key is generated at random each time you encrypt something.  Since the session key will never be the same, this results in different output.

---

### Post by saverio.miroddi on 2010-09-07
> **rookcifer said:**
> It's because the session key is generated at random each time you encrypt something.  Since the session key will never be the same, this results in different output.

 Is there a simple way to make the output the same using the same infrastructure (GnuPG and asymmetric encryption, possibly with an existing public key)? It's not a requirement to have different session keys for all the encryption sessions - in the specific case, it's counterproductive.  Thanks!

---

### Post by Bachstelze on 2010-09-07
> **saverio.miroddi said:**
> Is there a simple way to make the output the same using the same infrastructure (GnuPG and asymmetric encryption, possibly with an existing public key)? It's not a requirement to have different session keys for all the encryption sessions - in the specific case, it's counterproductive.  Thanks!

No. Not having session keys severely degrades security, to the point that you might as well not bother encrypting at all.

---

### Post by movieman on 2010-09-07
I believe there's also a random IV prepended to the data that's encrypted so even if the key is the same the output won't be.

If you reuse the same key and IV then, yeah, you open up a whole host of attacks on your messages.

---

