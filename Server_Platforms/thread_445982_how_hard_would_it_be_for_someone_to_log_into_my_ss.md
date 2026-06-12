---
title: "how hard would it be for someone to log into my ssh connection?"
date: 2007-05-16
forum: Server Platforms
---

### Post by graigsmith on 2007-05-16
my ssh connection is using a non password login, with they key system.  not sure what you call this. public key authentication?  automated computer attackers have been trying to use passwords to log in.  it's using RSA keys.  I'd be pretty much impossible for them to log in, unless there was some sort of bug or something in the ssh server correct?

---

### Post by gaten on 2007-05-16
>      my ssh connection is using a non password login, with they key system. not sure what you call this. public key authentication?Yes, public key authentication. 

>  automated computer attackers have been trying to use passwords to log in. it's using RSA keys. I'd be pretty much impossible for them to log in, unless there was some sort of bug or something in the ssh server correct?Yes, it's almost impossible for them to break into your ssh system if you *only* allow public key access. That means that this line must be in your **/etc/ssh/sshd_config** somewhere:
```
PasswordAuthentication no
```In Ubuntu, you must change this as the default is set to **yes**.

Also, you may want to check out **Fail2Ban or Denyhosts** (they're both in the repositories), or try changing the default ssh port.

---

### Post by graigsmith on 2007-05-17
yeah, i had that no password set, thanks alot.

---

