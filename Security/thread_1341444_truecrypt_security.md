---
title: "truecrypt security"
date: 2009-11-29
forum: Security
---

### Post by ffixcollector on 2009-11-29
I was wondering, would you data be more secure inside a hidden volume, or inside a trycrypt container, inside another truecrypt container?

I am not worried about someone forcing me to give up my password, just the security of my files.

---

### Post by rookcifer on 2009-11-29
> **ffixcollector said:**
> I was wondering, would you data be more secure inside a hidden volume, or inside a trycrypt container, inside another truecrypt container?

I am not worried about someone forcing me to give up my password, just the security of my files.

If you don't need hidden volumes, just use the Ubuntu alternate CD and setup whole disk encryption using LUKS.

---

### Post by ffixcollector on 2009-11-29
These volumes are on an external hot-swap HDD.

---

### Post by BkkBonanza on 2009-11-30
There's no point in double encrypting with truecrypt. The encryption is strong anyway and any compromise of the data will not be from crypto breaking but social engineering or brutal force (baseball bat method). If you don't require a hidden volume then just use a regular one. Most important though is to choose a good password, either long and random or use a key file and keep it safe. Someone is far more likely to brute force the password than break the encryption.

I don't see any point in whole disk encryption unless you really have a disk full of sensitive info. But I guess that would also owrk fine if it's not a big hassle to do. I've used Truecrypt for years and found it more than adequate. A lot depends on your circumstances - none of this will keep the mafia from getting your data because they aren't going to play by the rules.

The hidden volume doesn't give you any better security - it just gives you some deniability that the data is even there.

---

### Post by EJeanmaire on 2009-11-30
> **BkkBonaza said:**
> 
I don't see any point in whole disk encryption unless you really have a disk full of sensitive info. But I guess that would also owrk fine if it's not a big hassle to do. I've used Truecrypt for years and found it more than adequate. A lot depends on your circumstances - none of this will keep the mafia from getting your data because they aren't going to play by the rules.

The hidden volume doesn't give you any better security - it just gives you some deniability that the data is even there.

Encrypting a full system hdd is important because opening a file (say an office document for example) may duplicate the document in other areas of the harddrive.  If you only have a container, it does nothing to prevent your sensitive files from being read from temporary storage locations which are outside the container.

---

