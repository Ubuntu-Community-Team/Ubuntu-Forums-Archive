---
title: "How to enter passphrase from bash script?"
date: 2010-02-09
forum: Security
---

### Post by abcuser on 2010-02-09
Hi,
using Ubuntu 9.10 I would like to encrypt file using bash script.

I have written:
```
openssl aes-256-cbc -a -salt -in input_file.txt -out encrypted_ouput_file.txt.enc
```
I get question: "enter aes-256-cbc encryption password:" and then I manually enter password. After this another question is asked: "Verifying - enter aes-256-cbc encryption password:" and I need to enter password again.

How to enter password from file or command line using bash script?
Regards

---

### Post by cdenley on 2010-02-09
```

echo mypass|openssl aes-256-cbc -a -salt -in input_file.txt -out encrypted_ouput_file.txt.enc -pass stdin
openssl aes-256-cbc -a -salt -in input_file.txt -out encrypted_ouput_file.txt.enc -pass file:/path/to/mypass.txt
openssl aes-256-cbc -a -salt -in input_file.txt -out encrypted_ouput_file.txt.enc -pass pass:mypass

```
```

man openssl

```

---

