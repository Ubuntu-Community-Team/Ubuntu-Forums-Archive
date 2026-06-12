---
title: "How can i decryp[t Linux source code?"
date: 2008-02-15
forum: Security Discussions
---

### Post by az on 2008-02-15
The source code isn't encrypted.

But, I gather your question has to do with security?  If the source code is available, how can it be secure?

Well, we know that "security by obscurity" doesn't work.  Keeping something binary-only doesn't prevent exploits.  On the other hand, publishing the source code allows many people to look at at and find vulnerabilities before they get exploited.

As well, just because you know how a lock works, doesn't mean it's possible to pick it.  Specific to encryption, knowing how something is encrypted is a lot different than actually knowing the encryption key.  Even by knowing the method by which something is encrypted, it can still take a staggering amount of time and computer power to break a key.

---

### Post by gaten on 2008-02-15
If you mean user passwords, you are partly correct. They are stored in the **/etc/shadow** file, and they are **hashed**, not encrypted. See [http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)
for an explanation of what a Hash is.

In short, your passwords are thrown into a one-way hashing algoriithm, so you cannot **decrypt** any of your user passwords; at this point and time no mathematical technique is know which is able to do this (it's theoretically impossble). 

However, there are programs out there that can **crack** your password by hashing possible passwords and comparing them to the origonal hash. John the Ripper ([http://en.wikipedia.org/wiki/John_the_Ripper](http://en.wikipedia.org/wiki/John_the_Ripper)) is one such program, check it out.

---

### Post by scorp123 on 2008-02-16
> **techbrain55 said:**
>  If Linux is open source  any one can know where the password are stored  **/etc/shadow** ... as is the case with most other UNIX-like OS'es. But knowing where the passwords are is one thing, being able to access them is another, and being able to crack the strongly encrypted hashes again another.

> **techbrain55 said:**
>   and if they are encrypted any one can decrypt it using source code.   You are confusing a lot of things here. The source code is written in the C programming language and it's not encrypted and it doesn't store the passwords in any way.

---

### Post by The Cog on 2008-02-16
What is stored in /etc/shadow, it's not directly decryptable. What is stored is a one-way hash. When the user gives a pssword, it is hashed and that hash is compared with the stored one. 

Although the stored hash is not directly unhashable, if you know the hash, you can try lots of words and try to find one (the same or not) that gives the same hash. For this reason, /etc/shadow is only readable by root.

---

### Post by bmora96 on 2008-02-17
Hello

Unix and other systems including Windows, web sites, content management systems, databases etc do not store the passwords themselves. Instead, they calculate digest out of password and store that digest (in /etc/passwd or /etc/shadow file in case of Unix).

Regards,
Bmora

---

### Post by bobpaul on 2008-03-13
How does one create their own hashes? I thought they were SHA1 hashes, but I just compared 'echo -n "password" | openssl sha1' and it was not the same as the hash field in /etc/shadow.

---

### Post by Dr Small on 2008-03-13
> **bobpaul said:**
> How does one create their own hashes? I thought they were SHA1 hashes, but I just compared 'echo -n "password" | openssl sha1' and it was not the same as the hash field in /etc/shadow.
Use:
```
grub-md5-crypt
```

The only problem with it, it doesn't support stdin.


Dr Small

---

### Post by The Tronyx on 2008-03-13
> **bobpaul said:**
> I just compared 'echo -n "password" | openssl sha1' and it was not the same as the hash field in /etc/shadow.

It could very well be MD5 hashes.  MD5 hashes are 32 character alpha-numeric strings.  If you supply the password 'password' and hash it in SHA1 you come up with 40 alpha-numeric characters, MD5 generates a 32 character string.

That's usually the first noticeable difference.

---

### Post by Dr Small on 2008-03-13
> **2point0 said:**
> It could very well be MD5 hashes.  MD5 hashes are 32 character alpha-numeric strings.  If you supply the password 'password' and hash it in SHA1 you come up with 40 alpha-numeric characters, MD5 generates a 32 character string.

That's usually the first noticeable difference.
Yes, passwords in /etc/shadow are MD5 hashed. I have checked before, and that is how John dictionary attacks them.

---

### Post by kevdog on 2008-03-14
No way to change the hash from md5 to something else is there without modification of the source code?

Just an FYI
Two passwords that hash to the same digest is known as a "collision".

---

### Post by bobpaul on 2008-03-19
> **2point0 said:**
> It could very well be MD5 hashes.  MD5 hashes are 32 character alpha-numeric strings. 

Hmm.. When I supply the passwd command and change the password, I consistently get 35 char hashes, but when I use the grub-md5-crypt command, I get 32 char hashes. Also interesting, every time I supply either command I get a different hash then previous times even though I'm supplying the same password (because it's salted?) and all hashes seem to work fine for authenticating.

---

### Post by 3rdalbum on 2008-03-20
The original poster posted exactly the same question to the Cnet forums a few days ago. I gave him exactly the same answer there as you guys have done here :-)

---

### Post by scorp123 on 2008-03-22
> **3rdalbum said:**
> The original poster posted exactly the same question to the Cnet forums a few days ago. Just enter his nickname into Google ... there are dozens of forums where he is posting the same question again and again and again. Here, another example: 
[http://www.daniweb.com/forums/thread111164.html](http://www.daniweb.com/forums/thread111164.html)

He ("techbrain55") will ask the same silly question about "decrypting Linux source code" and then start a discussion with what looks like a second nick "bmora96" (please note the same weird "accent", vocabulary and spelling errors!) and then always come to the same silly conclusion that "Linux is too closed, nobody can decrypt it -- use  <insert silly pointless product here>  instead!" ... And he repeats this on a dozen of forums.

Methinks this guy is just a spammer.

---

### Post by bhavi on 2008-03-24
I'm not understanding it..The source code is in plain, readable text. You compile the source code to create the executable programs.. The main question is IS IT POSSIBLE TO STOP REVERSE ENGINEERS?

Passwords, on the other hand, are stored, encrypted, in the /etc/passwd and /etc/shadow files. They can be decrypted using John the ripper..

More info:

[http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/open-source-security.html](http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/open-source-security.html)

---

### Post by scorp123 on 2008-03-24
> **bhavi said:**
> I'm not understanding it.. The threadstarter is a spammer and his original postings have already been removed. The current #1 posting was in fact #2 when this thread started. So just forget about this.

---

### Post by bhavi on 2008-03-24
> **scorp123 said:**
> The threadstarter is a spammer and his original postings have already been removed. The current #1 posting was in fact #2 when this thread started. So just forget about this.
OK.... :)

---

