---
title: "Is .zip safe from John the Ripper or am I messing up?"
date: 2008-01-22
forum: The Cafe
---

### Post by Arenlor on 2008-01-22
I created an empty .zip with a password, to see how secure it was. I then went to use john the ripper on it 'john -incremental:all test.zip' and it pulled a 'Loaded 0 passwords, exiting...' am I doing something wrong or are .zip safe from John the Ripper, and in either case can someone suggest any other crackers that could work on it? Yes I do actually have information to protect that I would need to test how long it takes to crack it.

---

### Post by p_quarles on 2008-01-22
John may not know how to look for a .zip password, but it's not designed to do so. .zip password protection is, all the same, the equivalent of no protection at all, since no encryption is used. 

If you have something important to keep secret, use encryption. A password protected .zip archive can be cracked by anyone who cares to.

---

### Post by Arenlor on 2008-01-23
What type of encryption would you suggest?

---

### Post by PartisanEntity on 2008-01-23
pgp

---

### Post by Namtabmai on 2008-01-23
rot13, so simple no one would suspect you'd use it.

---

### Post by Lostincyberspace on 2008-01-23
you could install easy crypt and true crypt and make a virtual encoded drive. you can even make one the size of a cd so If you need to you can burn it to cd to keep a record encrypted.

---

### Post by Lostincyberspace on 2008-01-23
> **Namtabmai said:**
> rot13, so simple no one would suspect you'd use it.
THat is one of the smatetest things I have ever herard.

---

### Post by p_quarles on 2008-01-23
> **Lostincyberspace said:**
> THat is one of the smatetest things I have ever herard.
Have to disagree with that. A simple substitution cypher is very easy to break, and no one has to "expect" you to be using it to break it.

---

### Post by Acglaphotis on 2008-01-23
First locally encrypted with 256-bit AES, using randomly generated keys encrypted with a SHA-256 hash of your password. All of this data must  then  be doubly encrypted with 128-bit AES encryption.** Hack that.**

In all seriousness, use AES or PGP.

---

### Post by Namtabmai on 2008-01-23
Just in case there was any wonder, I was only joking about rot13. Security through obscuring is not a smart way to go.
But then again it depends on who your trying to hide from. If you're trying to hide against the script kiddies who just run various cracker applications against a file, then it might actually work. They'll see a zip file and try a zip password breaker and it will fail, they probably won't even bother actually looking any further. But if you want to really hide your files against ALL forms of decyphering then PGP would be the best bet at the moment.

---

### Post by sargek on 2008-02-01
> **p_quarles said:**
> John may not know how to look for a .zip password, but it's not designed to do so. .zip password protection is, all the same, the equivalent of no protection at all, since no encryption is used. 

If you have something important to keep secret, use encryption. A password protected .zip archive can be cracked by anyone who cares to.

That depends on the zip product - Winzip does 256 AES encryption of archives. It is crackable with brute force methodologies though because the product does not stop repeated attempts when an incorrect password is entered. Most people will probably not want to spend weeks waiting for a strong password to be cracked to get an archive though, unless the data is worth it.

I realize this has nothing to do with Linux, but .zip archives - howevver those are normally associated with Windows anyway...

---

### Post by DenKain on 2008-04-22
Print the file.

Then shred the file on the pc with a shredding program 10,000 times.

Lock file in a safety deposit box inside of a LARGE bank.

Beat that for security.

:-p

Its unrealistic but the most secure thing you can do.

---

