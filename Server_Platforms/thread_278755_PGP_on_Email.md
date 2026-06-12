---
title: "PGP on Email"
date: 2006-10-16
forum: Server Platforms
---

### Post by wizzkid on 2006-10-16
Hi!

I want my email to have PGP signed, however i am new to this stuff and i need your help. 

What I did was, type gpg --gen-key then i choose DSA and Elgamal, then I just follow instruction, after the process, it gives me some sort of configuration summary 

Here it is ( i scrambled it)
gpg: key E1B98766 marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
pub   1024D/E5A67678 2006-10-16
      Key fingerprint = 0DE1 F4BF D421 4322 1212  D117 4AFA 32E9 E6A1 2332
uid                  myname (comments) <email@domain.com>
sub   1024g/6DE4BF83 2006-10-16  

Then I went to my email client evolution, then Accounts > Security and I put the GPG Key E1B98766. 

thats all what I did. Is this correct? or I did something wrong? :)

Is it safe to give out or let other people know my PGP key? 

Also, what's the use of keyserver?

Hope to receive input.. Thanks.

---

### Post by tomBorgia on 2006-10-17
You need to give people your public key (or upload it to a keyserver) - keep your private key, well, private! 
If your just looking to sign the email then people who have your public key will be able to verify that you sent it as only your private key can be used to generate a signature that corresponds to your public key. If you wish to encrypt the entire email then you will need the recipients public key - this will be used to encrypt the mail and then they can use thier private key to decrypt it. Basically the public key for a signature is required to decrpt the signature but only the private key can generate it. 
Did that make sense? Hope so!:D

---

