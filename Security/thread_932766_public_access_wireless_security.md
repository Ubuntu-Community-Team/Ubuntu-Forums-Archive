---
title: "public access wireless security"
date: 2008-09-28
forum: Security
---

### Post by azebuski on 2008-09-28
I live in an apartment complex that has free 802.11b wireless internet access and I am wondering how secure I am running Hardy Heron.  There is no WEP or any other type of security enabled, but all residents must register their wireless card MAC address before being able to access the network.
I have run the Shield's Up test at grc.com and port 22, SSH remote login is completely open and port 80 HTTP World Wide Web is also completely open. All other ports are closed and not one single port is stelathed.
The GRC site says that most apartments and residential wireless access points are behind a NAT hardware firewall and the port scan is probing this NAT firewall and not my actual PC.  Is this correct?  Am I safe?

---

### Post by cariboo on 2008-09-28
If you don't need a web server, shutdown Apache2. Use Hostsdeny or Fail2ban to deny access to ssh. Use a strong password, I had a 6 character password it to john (the butcher) 1:35 minutes to crack my password, I added 1 letter and changed the case on 2 letters and I finally shut john down after 7 hours it still hadn't cracked my password.

Jim

---

### Post by Dr Small on 2008-09-28
> **cariboo907 said:**
> If you don't need a web server, shutdown Apache2. Use Hostsdeny or Fail2ban to deny access to ssh. Use a strong password, I had a 6 character password it to john (the butcher) 1:35 minutes to crack my password, I added 1 letter and changed the case on 2 letters and I finally shut john down after 7 hours it still hadn't cracked my password.

Jim
Only seven hours? The minimum I run my is 2 weeks!

---

### Post by kevdog on 2008-09-28
> **Dr Small said:**
> Only seven hours? The minimum I run my is 2 weeks!

Paranoid Freak!

---

### Post by Dr Small on 2008-09-28
> **kevdog said:**
> Paranoid Freak!
Well, I figured if anyone ever got ahold of my password hash, they probably wouldn't try over 2 weeks, so I said, what the heck with this. I just wanted to make sure my password is secure ;)

---

### Post by kevdog on 2008-09-28
What hash are you using for your password?  I have no knowledge of the default hash used by ubuntu to store hashes.  Can I change it to whirlpool or something else?

---

### Post by Dr Small on 2008-09-28
> **kevdog said:**
> What hash are you using for your password?  I have no knowledge of the default hash used by ubuntu to store hashes.  Can I change it to whirlpool or something else?
Ubuntu uses MD5 + Salts, I presume, so that's what I am using. I generate my passwords and test them first with grub-md5-crypt. You can probably change the default hash with PAM, though.

---

### Post by kevdog on 2008-09-28
With md5 its an eight character salt.  Where is the salt stored?

---

### Post by cdenley on 2008-09-29
> **kevdog said:**
> What hash are you using for your password?  I have no knowledge of the default hash used by ubuntu to store hashes.  Can I change it to whirlpool or something else?

[http://ubuntuforums.org/showpost.php?p=5873671&postcount=13](http://ubuntuforums.org/showpost.php?p=5873671&postcount=13)
I don't think whirlpool is supported.

---

### Post by cdenley on 2008-09-29
> **kevdog said:**
> With md5 its an eight character salt.  Where is the salt stored?

$<ID>$<SALT>$<PWD>
test:$1$xaGhRo58$P3rOk3B4fZYNfZwATmM7t1:14151:0:99999:7:::
ID=1 (MD5)
SALT=xaGhRo58
HASH=P3rOk3B4fZYNfZwATmM7t1

---

### Post by kevdog on 2008-09-29
I thought the hash was the result of the salt+password --> Hash product.  Is this not the case?  If you have to store the hash prepended to the password somewhere, what security does this gain you rather than just simply hashing the password?

---

### Post by cdenley on 2008-09-29
> **kevdog said:**
> I thought the hash was the result of the salt+password --> Hash product.  Is this not the case?  If you have to store the hash prepended to the password somewhere, what security does this gain you rather than just simply hashing the password?

The hash is generated after adding the salt to the plaintext password. This improves security because attackers cannot use precomputed hashes for commonly used passwords (rainbow tables). An attacker would have to either compute hashes for all possible passwords and hashes together, or compute the hashes once they obtain your salt. The salt needs to be stored because the computer needs it to obtain the correct hash if the user inputs the correct password.

---

### Post by kevdog on 2008-09-29
Yes, just like I thought.  Do they run the md5 hash through a series of iterations -- like 5 times, or is it simply salt+password=hash, and hash is stored?  What generates the salt?  I assume its some random number gen, however given the openssh exploit, is it much the same process?

---

### Post by cdenley on 2008-09-29
> **kevdog said:**
> Yes, just like I thought.  Do they run the md5 hash through a series of iterations -- like 5 times, or is it simply salt+password=hash, and hash is stored?  What generates the salt?  I assume its some random number gen, however given the openssh exploit, is it much the same process?

[http://en.wikipedia.org/wiki/Crypt_(Unix)#MD5-based_scheme](http://en.wikipedia.org/wiki/Crypt_(Unix)#MD5-based_scheme)

Maybe with the debian random number generator vulnerbility, salts would've been more predictable, possibly making rainbow tables more practical. I'm not entirely sure.

If in doubt, you can always reset your password.

---

### Post by kevdog on 2008-09-29
Thanks for that link -- looks like the password hash salt numbers are hashed multiple times.  That link suggested 100x --  I guess it still comes down to the strength of the initial password however.

---

