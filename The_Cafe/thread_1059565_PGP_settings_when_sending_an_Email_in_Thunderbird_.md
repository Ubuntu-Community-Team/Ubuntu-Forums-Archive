---
title: "PGP settings when sending an Email in Thunderbird question."
date: 2009-02-03
forum: The Cafe
---

### Post by Swerve1000 on 2009-02-03
Hi,

I have setup PGP in Thunderbird and now am trying to send my first encrypted message with a new email account.

Thunderbird asks :

Sign Message
Encrypt message

Use PGP/MIME

Should I tick both the top two? Just one, or all three?

And I will have to send my friend my public key in a separate unencrypted message, yes?

When I send a message with just encryption enabled, the encrypted message is very long (I used a 4096 bit key).

When I chose encrypt and sign, the email received is much shorter.

I do not want to compromise the key.

Many thanks.

---

### Post by icheyne on 2009-02-04
I haven't used Thunderbird with PGP, but:

> **Swerve1000 said:**
> 
Sign Message
Encrypt message

Use PGP/MIME

Should I tick both the top two? Just one, or all three?

I expect just Encrypt and Use PGP/Mime

> 
And I will have to send my friend my public key in a separate unencrypted message, yes?
 Best to exchange it manually. Theoretically, it might be possible for someone to intercept the public key and substitute their own.

---

### Post by Nepherte on 2009-02-04
You might as well check the sign email as well. There's also an option (in enigmail) to include your public key. You do realize that you have to use the public key of the recipient to encrypt the message right? The purpose of sending your own public key to the recipient is that he can also send you an encrypted message with your public key and to verify that the mail is coming from you an is unaltered in case you have signed the mail.

---

