---
title: "A question of encrypted /home security?"
date: 2012-07-17
forum: Security
---

### Post by 0011235813 on 2012-07-17
Hi,
When I installed Ubuntu on one of my computers a couple of months ago, I had selected the encrypt /home option. That's caused me a fair amount of grief with the computer refusing to resume from suspend, and I was a bit annoyed that it didn't mention in the installer it would also encrypt the swap and the associated problems with hibernate& suspend.  Nor did it ask me whether I wanted the swap to be encrypted.
But the real question I'm wondering, is actually how secure is this method? My concern isn't with the encryption itself, it's the problem that the mount passphrase is decrypted using the users system password (one of the reasons for this is to prevent the home directory becoming unusable if the user changes the password, from what I understand). But the issue comes from the fact that the system files in / are left unencrypted. This has the obvious advantage of speed, but if the authentication passwords are stored in plain text on the unencrypted system folders, (especially the root password since the user is a sudoer) than the password used to decrypt the mount passphrase of the directory would be stored unencrypted. Is this correct? Am I missing something here?!

---

### Post by Cheesemill on 2012-07-17
> This has the obvious advantage of speed, but if the authentication  passwords are stored in plain text on the unencrypted system folders,  (especially the root password since the user is a sudoer) than the  password used to decrypt the mount passphrase of the directory would be  stored unencrypted. Is this correct? Am I missing something here?!
The authentication passwords aren't stored in plain text anywhere.

---

### Post by 0011235813 on 2012-07-17
> **Cheesemill said:**
> The authentication passwords aren't stored in plain text anywhere.

So how does the system know the sudo password is correct if the passwords aren't stored somewhere? Aren't any passwords kept in /etc/passwd?

---

### Post by Cheesemill on 2012-07-17
Password **hashes** are stored in /etc/shadow:
```
rob@precise:~$ sudo cat /etc/shadow | grep rob
[sudo] password for rob: 
rob:$6$D2TbFGvD$5RcAk6tVEB/kBtNyiBH7s1d0TYTfjfLp78eFHIlYXT1eI7y83bo8/oWMubuF.eUJDAqBYpcef5e571tPMfAt30:15526:0:99999:7:::

```The relevant information is the field between the first and second colons.
The $6$ means that the password hash is calculated using SHA512 hashing, the rest of the field is the hashed password, in this case:
```
D2TbFGvD$5RcAk6tVEB/kBtNyiBH7s1d0TYTfjfLp78eFHIlYXT1eI7y83bo8/oWMubuF.eUJDAqBYpcef5e571tPMfAt30
```Hashing is a mathematical function that is easy to do in one direction but impossible to do in the other direction. When you are prompted for your password the computer runs it through the hashing algorithm and compares the result with the value stored in /etc/shadow. If they match then the password is correct. It is, however, impossible to take the result of the hashing function and run it backwards to discover the actual password.

[http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)
[http://en.wikipedia.org/wiki/SHA-2](http://en.wikipedia.org/wiki/SHA-2)

---

### Post by 0011235813 on 2012-07-17
> **Cheesemill said:**
> Password **hashes** are stored in /etc/shadow:
```
rob@precise:~$ sudo cat /etc/shadow | grep rob
[sudo] password for rob: 
rob:$6$D2TbFGvD$5RcAk6tVEB/kBtNyiBH7s1d0TYTfjfLp78eFHIlYXT1eI7y83bo8/oWMubuF.eUJDAqBYpcef5e571tPMfAt30:15526:0:99999:7:::

```The relevant information is the field between the first and second colons.
The $6$ means that the password hash is calculated using SHA512 hashing, the rest of the field is the hashed password, in this case:
```
D2TbFGvD$5RcAk6tVEB/kBtNyiBH7s1d0TYTfjfLp78eFHIlYXT1eI7y83bo8/oWMubuF.eUJDAqBYpcef5e571tPMfAt30
```Hashing is a mathematical function that is easy to do in one direction but impossible to do in the other direction. When you are prompted for your password the computer runs it through the hashing algorithm and compares the result with the value stored in /etc/shadow. If they match then the password is correct. It is, however, impossible to take the result of the hashing function and run it backwards to discover the actual password.

[http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)
[http://en.wikipedia.org/wiki/SHA-2](http://en.wikipedia.org/wiki/SHA-2)

Ah right, that explains it. It's weird because I searched through a lot of articles and none of them were very clear on this point.

---

### Post by 0011235813 on 2012-07-18
One more question: If another use becomes root (or the attacker becomes root at login) can they change the users password? And if so, how does this affect the encryption?

---

### Post by cool110 on 2012-07-18
> **0011235813 said:**
> One more question: If another use becomes root (or the attacker becomes root at login) can they change the users password? And if so, how does this affect the encryption?
The encrypted directory will not be mounted automatically which will prevent the user logging on graphically. If the user is logged in on a tty they can access their home by using ecryptfs-mount-private with the old password. Graphical login can be restored by changing the password back to the old one.

---

