---
title: "is it safe to copy files over scp"
date: 2016-10-13
forum: Security
---

### Post by ltoso on 2016-10-13
I am looking for some way to access my home desktop files over the 
Internet and I think scp is a great option to do that, where I will use 
Ssh login ids. What I want to know is when we use scp, is it the credentials
That are sent encrypted or all the files are sent as encrypted.
Please recommend

---

### Post by sudodus on 2016-10-13
If the ssh server is using SSH keys instead of passwords, you need not send anything unencrypted. See this link

[OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by SeijiSensei on 2016-10-13
Everything sent over SSH is encrypted, though using shared keys is still a good idea.

---

### Post by ltoso on 2016-10-14
Hi, thanx for the replies, can you please explain why is it better to use shared keys instead of using passwords

---

### Post by kevdog on 2016-10-14
Shared keys would nearly be impossible to guess as compared to passwords.  Also shared keys follow under the topic of asymmetric encryption with a public and private key.  The private key can additionally be secured with a password if need be.

---

