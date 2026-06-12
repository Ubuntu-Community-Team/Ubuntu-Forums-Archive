---
title: "Hash question"
date: 2010-03-25
forum: Security
---

### Post by hakermania on 2010-03-25
Hi all! I have 3 questions
1) What kind of hash is this: **783a39d5092053e6 **(md5, sha1 or what???)
2) How can I understand the kind of any hash?
3) Which is the most appropriate tool to decrypt a hash? (I use john the ripper or something like that)
Thx in advance!:popcorn:

---

### Post by new_tolinux on 2010-03-25
At least it's not MD5, because it's to short for MD5

Most likely you will never "understand" any hash, or be able to "convert" it to something you can read. Hashes are most of times "one way". Not a bad thing when you know most passwords are stored as hashes and the password you type in is then hashed and that hash is compared to the existing hash in the password list.

---

### Post by hakermania on 2010-03-25
Hmmm interesting. After a search I did it resulted to be an sql hash...Thank you

---

### Post by hakermania on 2010-03-25
Can anyone find what is the pass of 0f0dd38b61d3a824 ????
If yes, then I suppose that I am insecure!!!
hint:It not md5

---

### Post by aysiu on 2010-03-25
Is that what shows up in your /etc/shadow file?

---

### Post by hakermania on 2010-03-25
Can anyone find what is the pass of 0f0dd38b61d3a824 ????
If yes, then I suppose that I am insecure!!!
hint:It not md5

---

### Post by hakermania on 2010-03-25
oups, double post. By mistake! Any mod here?

---

### Post by hakermania on 2010-03-25
N00000000 but it could be an sql hash....(who knows????) ;)

---

### Post by wojox on 2010-03-25
Lan Manager?

---

### Post by gnupipe on 2010-03-25
You can use John the Ripper to crack mysql hashes. You need to download
john's source code and apply diff patch (adds mysql hash support) and then compile john.

[http://openwall.com/john/g/john-1.7.3.4.tar.gz](http://openwall.com/john/g/john-1.7.3.4.tar.gz)
[http://openwall.com/john/contrib/john-1.7.3.4-jumbo-3.diff.gz](http://openwall.com/john/contrib/john-1.7.3.4-jumbo-3.diff.gz)

---

### Post by cdenley on 2010-03-25
That is a pre-4.1 mysql password hash. Hashes can't be decrypted, but they can be cracked. A simple google search reveals the password to be "bM4FJcMT", which I confirmed with mysql.
```

mysql> SELECT old_password('bM4FJcMT');
+--------------------------+
| old_password('bM4FJcMT') |
+--------------------------+
| 783a39d5092053e6         | 
+--------------------------+
1 row in set (0.00 sec)

```
[http://dev.mysql.com/doc/refman/5.1/en/encryption-functions.html#function_old-password](http://dev.mysql.com/doc/refman/5.1/en/encryption-functions.html#function_old-password)

Must be a commonly used default or something.

---

### Post by falconindy on 2010-03-25
0f0dd38b61d3a824 is an old LanMan hash.

---

### Post by hakermania on 2010-03-26
> **falconindy said:**
> 0f0dd38b61d3a824 is an old LanMan hash.
Nice, can you crack it?

---

### Post by hakermania on 2010-03-26
To help you it is actually an sql323 hash!

---

