---
title: "importing pgp keys"
date: 2010-07-21
forum: Security
---

### Post by tsucol11 on 2010-07-21
I am moving over from windows XP to Ubuntu 10.04 (at home). I need to import both my pubring.pkr & secring.skr from the windows version of PGP into Ubuntu.

It doesn't matter whether I have to use seahorse or GPG as long as the program permits me to encrypt both emails & files. I need to be able to decrypt these emails & files in a windows environment (at work) using PGP.

Windows PGP version currently used is 8.0.

Any suggestions? 

If someone could point me to a link describing the above I would be grateful.

Brian

---

### Post by mikewhatever on 2010-07-21
Does the program you use in Windows allow exporting? If so, do it, then open Seahorse, File->Import...

---

### Post by tsucol11 on 2010-07-21
> **mikewhatever said:**
> Does the program you use in Windows allow exporting? If so, do it, then open Seahorse, File->Import...

After some experimenting it appears that seahorse can import both windows generated pgp keys as well as the PGP program export (.asc).

Now I need to learn how to use seahorse to encrypt files & emails. I am using evolution any special pugins required?

Thanks for the prompt reply.

Brian

---

### Post by tsucol11 on 2010-07-22
I have now imported my PGP keys & downloaded the seahorse plugins.

I can now encrypt & decrypt files while in Nautilus.

2 questions:

1- I want seahorse to stop storing the passphrase in memory. Where do I go to change the setting?

2- what plugins do I need to encrypt email in evolution?

thanks again

Brian

---

### Post by noway2 on 2010-07-22
I am not sure how to tell it to not temporarily store your password in memory, but configuring evolution is easy.

Go to edit -> preferences, select your mail account and click edit in the pop up window.  On the far right of the options tabs will be one for security.  Enter your key there, which will allow you to decrypt messages.  Personally, I check the always sign messages and always trust keys in my key ring.  The latter one will allow you to send mail to someone using their public key without designating their key as being trusted.

The always encrypt to myself can be useful if you want to be able to read what you sent.  I have seen this cause problems on the recipient end and I have been leaving this off.

One other tip is that if you want to reply to an encrypted message and include the decrypted text, select the text of interest and highlight it (mouse drag) and THEN hit reply.  The text will be transferred to your reply message.

---

### Post by tsucol11 on 2010-07-22
> **noway2 said:**
> I am not sure how to tell it to not temporarily store your password in memory, but configuring evolution is easy.

Go to edit -> preferences, select your mail account and click edit in the pop up window.  On the far right of the options tabs will be one for security.  Enter your key there, which will allow you to decrypt messages.  Personally, I check the always sign messages and always trust keys in my key ring.  The latter one will allow you to send mail to someone using their public key without designating their key as being trusted.

The always encrypt to myself can be useful if you want to be able to read what you sent.  I have seen this cause problems on the recipient end and I have been leaving this off.

One other tip is that if you want to reply to an encrypted message and include the decrypted text, select the text of interest and highlight it (mouse drag) and THEN hit reply.  The text will be transferred to your reply message.

Thanks Noway2. I will try that as soon as I get home.

Brian

---

