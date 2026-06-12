---
title: "password characters and length"
date: 2010-03-24
forum: Security
---

### Post by e24ohm on 2010-03-24
Folks:
I need a little insight, and I’m not sure if the two can relate, but I am trying to find out the following.

When generating WEP Keys the available bits are: 64/128/152/256; however, you need 5/13/16/29 character respectfully for each key if you generate the key manually.

Can this formula be applied to passwords and the length of the password? For example: if my password had 29 characters, could I say that my password is 256-bits?

Thank you,
E

---

### Post by cdenley on 2010-03-24
Each character in a string is represented by a byte with a decimal value from 0-255. Each byte is comprised of 8 bits. A bit is a 0 or 1 (binary).
[http://www.asciitable.com/](http://www.asciitable.com/)

A = 65  = 01000001
l = 108 = 01101100
[NOPARSE]
So a string with 6 characters, like "Ubuntu", is 6 bytes long, or 48 bits long (6 x 8 = 48).
[/NOPARSE]
Ubuntu = 01010101 01100010 01110101 01101110 01110100 01110101

I'm not sure what the extra 3 bytes are used for with those WEP keys, though.

---

### Post by e24ohm on 2010-03-24
> **cdenley said:**
> Each character in a string is represented by a byte with a decimal value from 0-255. Each byte is comprised of 8 bits. A bit is a 0 or 1 (binary).
[http://www.asciitable.com/](http://www.asciitable.com/)

A = 65  = 01000001
l = 108 = 01101100
[NOPARSE]
So a string with 6 characters, like "Ubuntu", is 6 bytes long, or 48 bits long (6 x 8 = 48).
[/NOPARSE]
Ubuntu = 01010101 01100010 01110101 01101110 01110100 01110101

I'm not sure what the extra 3 bytes are used for with those WEP keys, though.

thanks so much...this really helped out...thanks..Cheers!!!

---

### Post by justanothergreysky on 2010-03-24
I think it would be incorrect to use the length of your password as a function of "bits".  Generally, the "bit strength" refers to the key of the cryptographic cypher and has nothing to do with the length of the password.

A simple and well known example might be the old LanManager hashes still sometimes used by Windows.  It doesn't matter at all how long the password is, cryptographically, since it splits the password into 6-character chunks and captalizes them before encoding.

Other systems (like WEP) will often have an algorithm to accept arbitrary passwords and convert them into usable hexidecimal values.  The password "AjR5##21" in most wireless systems is only 8 characters, but it is then hashed into the appropriate length hash.  It's equally valid as a 64-bit WEP key, or as a 256-bit AES key.  The former is exceedlingly weak and the latter is relatively strong.

In the case of the AES key in the WPA2 standard, the strength of the system is directly proportional to how difficult it is to utilize a dictionary attack against it.   They key "superluminal" is a very weak key, despite being 12 characters, where the shorter key I specified above is stronger.

But regardless of the length of the password, it's transformed into a 256-bit hash before it's actually used.

---

### Post by rookcifer on 2010-03-25
What you want to calculate is password *entropy*, which can be found with the following formula:

```
entropy per character = log2(n)

(where n = the pool of characters to choose from)
```

Now, to find the entropy of the password itself:

```
length of password * entropy per character
```

Basically a password using any possible character on a standard keyboard (94 possible characters) will have an entropy of 6.55 bits per character.  A password that does not use any special characters (but uses a-z, A-Z, 0-9) will have an entropy of 5.95 bits per character.  

So, to answer your question, if your 29 character password is using a-z, A-Z, 0-9, then it will have *173 bits* of entropy.  If using all possible characters, it will have *190 bits* of entropy.  Naturally, it is assumed that you are generating these passwords *randomly* and not merely using something like "abcdefg."

---

### Post by e24ohm on 2010-03-25
> **rookcifer said:**
> What you want to calculate is password *entropy*, which can be found with the following formula:

```
entropy per character = log2(n)

(where n = the pool of characters to choose from)
```

Now, to find the entropy of the password itself:

```
length of password * entropy per character
```

Basically a password using any possible character on a standard keyboard (94 possible characters) will have an entropy of 6.55 bits per character.  A password that does not use any special characters (but uses a-z, A-Z, 0-9) will have an entropy of 5.95 bits per character.  

So, to answer your question, if your 29 character password is using a-z, A-Z, 0-9, then it will have *173 bits* of entropy.  If using all possible characters, it will have *190 bits* of entropy.  Naturally, it is assumed that you are generating these passwords *randomly* and not merely using something like "abcdefg."

I understand thank you. Is it safe to say that a password, which is 30 characters long randomly using: a-z, A-z, 0-9 would build a strong password?

---

### Post by cdenley on 2010-03-25
With 591222134364399413463902591994678504204696392694759424 possibilities for what your password can be, I would say you are safe. I don't think anyone will be guessing that random password anytime in the next century. It doesn't help that you just revealed the character set of your password on a public forum, though.

---

### Post by e24ohm on 2010-03-25
> **cdenley said:**
> With 591222134364399413463902591994678504204696392694759424 possibilities for what your password can be, I would say you are safe. I don't think anyone will be guessing that random password anytime in the next century. It doesn't help that you just revealed the character set of your password on a public forum, though.

It was only a hypothetical question, because I do not understand why a site would not allow special characters.

---

### Post by cdenley on 2010-03-25
> **e24ohm said:**
> It was only a hypothetical question, because I do not understand why a site would not allow special characters.

My guess is because they store it in a database in plaintext, and are too lazy to sanitize user input properly to prevent SQL injection. Either that, or they store it in a plaintext file delimited by a special character such as a comma. Either way, password hashes should only be stored, not the passwords themselves, so the characters used should be irrelevant.

---

### Post by e24ohm on 2010-03-25
> **cdenley said:**
> My guess is because they store it in a database in plaintext, and are too lazy to sanitize user input properly to prevent SQL injection. Either that, or they store it in a plaintext file delimited by a special character such as a comma. Either way, password hashes should only be stored, not the passwords themselves, so the characters used should be irrelevant.
"Either way, password hashes should only be stored, not the passwords themselves, so the characters used should be irrelevant", is this becuase each character has 8 bits, which can represent any ASCII character?

---

### Post by cdenley on 2010-03-25
> **e24ohm said:**
> "Either way, password hashes should only be stored, not the passwords themselves, so the characters used should be irrelevant", is this becuase each character has 8 bits, which can represent any ASCII character?

Are you asking why password hashes only should be stored? If an attacker somehow retrieved a hash, they would still have to crack the hash before they can determine what the actual password is (no easy task). If it was stored in plaintext, then the attacker would already have the password, which gives them access to the site which uses that database, as well as any other account that user may have used that password with. A hash already has a limited character set irrelevant to that of the password. No user input would generate a hash which can be used to inject any kind of code.

---

