---
title: "random encryption question"
date: 2009-10-24
forum: The Cafe
---

### Post by danastasio on 2009-10-24
Hi yall!
I got around to encrypting some sensitive information the other day and i got to wondering. What would happen if you encrypted a file within an encrypted folder? for example, you move file_a into folder_b, and folder_b has already been encrypted (by truecrypt in this example). Now that file_a is in folder_b, you go in with truecrypt and encrypt the file. now you need a password to open folder_b and another one to open folder_a.

does this make any significant difference from a security standpoint? having not done any real research on the subject of encryption (i was never one for math...) to me, it seems logical that even if you broke the encryption, you would still have an encrypted file within folder_b that would remain encrypted, because the encryption on the file is seperate from the foler, and thus, access is denied.

Am i just crazy or am i on to something?

Many thanks!!

---

### Post by Bachstelze on 2009-10-24
Well, it would depend *how* the encryption was cracked. If someone breaks into your folder by exploiting a vulnerability in your encryption method (here, TrueCrypt), the individual file will be easy to crack as well, since it was encrypted using the same method, which has the same flaw. However, if it was cracked by stealing your passphrase and if the individual file has a *totally* different one, then yes, the attacker will have to steal the passphrase for it as well. This is not a guarantee of additional security, however: if the attacker was able to steal the first passphrase, the odds are high that the same method would work for stealing the second one.

Long story short: there is no definite answer to your question. It depends on a large number of factors.

---

