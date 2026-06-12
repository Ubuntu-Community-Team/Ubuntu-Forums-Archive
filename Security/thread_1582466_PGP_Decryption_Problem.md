---
title: "PGP Decryption Problem"
date: 2010-09-26
forum: Security
---

### Post by Geffers on 2010-09-26
I created a PGP key on a Windows computer some years back.

Using the same key in Ubuntu via Gnu Privacy Assistant I can encrypt and decrypt successfully but if I attach a signature and then decrypt I get the message /name-of-file contained no OpenPGPdata

Seems to be fine provided I don't sign.

Anyone else had this problem.

Geffers

---

### Post by Bachstelze on 2010-09-26
What are you doing exactly? How do you "attach a signature"?

---

### Post by Geffers on 2010-09-27
> **Bachstelze said:**
> What are you doing exactly? How do you "attach a signature"?

Using Gnu Privacy Assistant the gui has a file browser option, when the required file is highlighted there are a number of icon options including 'sign the selected file', 'check signature of selected file', as well as 'encrypt and decrypt selected file.

When I 'sign' a selected file after encrypting it any attempt to decrypt it gives the message /name-of-file contained no OpenPGPdata

Geffers

---

### Post by Bachstelze on 2010-09-27
If the signature data is added to the file, it's normal that you can't decrypt it since the file has been modified after it was encrypted.  As far as decryption is concerned, the signature is just garbage data.

Which "GUI" are you talking about?

---

### Post by Geffers on 2010-09-27
> **Bachstelze said:**
> If the signature data is added to the file, it's normal that you can't decrypt it since the file has been modified after it was encrypted.  As far as decryption is concerned, the signature is just garbage data.

Which "GUI" are you talking about?

Gnu Privacy Assistant

Geffers

---

### Post by Bachstelze on 2010-09-27
Then you can either make a detached signature or sign and encrypt in the same step (check the "sign" box on the encryption dialog).

---

### Post by noway2 on 2010-09-28
I have been running into the same problem.  I recently encrypted some files for archival purposes and I did encrypt and sign in the same operation using Gnu Privacy Assistant.  The file wasn't modified after the operation.  I suspect that there may be a bug in that tool; I was using the Windows version at the time to save some personal files at work.

---

### Post by Geffers on 2010-09-28
> **Bachstelze said:**
> Then you can either make a detached signature or sign and encrypt in the same step (check the "sign" box on the encryption dialog).

That seems to work OK, thanks for suggestion.

Geffers

---

