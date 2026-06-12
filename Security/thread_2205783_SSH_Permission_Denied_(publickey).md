---
title: "SSH Permission Denied (publickey)"
date: 2014-02-15
forum: Security
---

### Post by Elastic_Potential on 2014-02-15
I've had the idea to set-up a personal server to easily manage my documents and other minor projects.  As I'm fairly new to SSH, I was wondering how to manage keys with multiple devices.  Disabling password authentication in favor of public key (RSA) makes it seemingly impossible to add new keys to my server.  Currently, my sshd_config file has these functions set:

```

RSAAuthentication yes
PubkeyAuthentication yes

PasswordAuthentication no

```

On one device, I set PasswordAuthentication to "yes," added its public key, and I can connect fine.  On another, I cannot send my public key at all: "Permission Denied (publickey)".  I realize that the simplest solution, mentioned in a couple forum posts, would be enabling password authentication; but, I am under the impression that RSA is more secure, so I'd prefer using it.

So, I guess my question is twofold:
a) how can I easily use keys between multiple devices without turning PasswordAuthentication on, or
b) would using my Linux user password over SSH be less-secure than using RSA?

---

### Post by cariboo on 2014-02-16
This may be a better place to get an answer to your question.

---

### Post by CharlesA on 2014-02-16
> **Elastic_Potential said:**
> I've had the idea to set-up a personal server to easily manage my documents and other minor projects.  As I'm fairly new to SSH, I was wondering how to manage keys with multiple devices.  Disabling password authentication in favor of public key (RSA) makes it seemingly impossible to add new keys to my server.  

Carry your public and private keys with you and use:

```
ssh-copy-id
```

Before disabling password auth.

> 
So, I guess my question is twofold:
a) how can I easily use keys between multiple devices without turning PasswordAuthentication on, or
b) would using my Linux user password over SSH be less-secure than using RSA?

a) See above. ssh-copy-id works wonders. :)
b) The password is still encrypted before it is sent, so that's fine. As long as you have a strong password you should be fine. However, passwords can be bruteforced, keys cannot.

---

### Post by Elastic_Potential on 2014-02-16
I'll definitely give ssh-copy-id a run with pass.auth enabled (disabled, it produced the "permission denied" error).  From what I've gathered, there really won't be an "ideal" way to manage keys with password auth. off.  But, I'm willing to overlook convenience for security :)

---

### Post by jdeca57 on 2014-02-16
> **Elastic_Potential said:**
> I'll definitely give ssh-copy-id a run with pass.auth enabled (disabled, it produced the "permission denied" error).  From what I've gathered, there really won't be an "ideal" way to manage keys with password auth. off.  But, I'm willing to overlook convenience for security :)
But that's only one-time (unless you frequently add new machines). 
ssh-copy-id does nothing more than adding your public key to ~/.ssh/authorized_keys so in fact you could copy your public key to a usb stick and transport it manually to another computer and add it with >> but it's reasonable that untill the key is added access is denied. After all, you denied it yourself... ;-)

---

### Post by fugu2 on 2014-02-18
Just to reiterate what has been said before, but from what you'll see when you do it:
From a fresh ssh-server config, it starts with password auth enabled.
if you ssh-copy-id to the ssh-server, it will ask for your password, and then it
 moves your keys onto the server (BTW, it helps to have your server running on 
port 22 just for the ssh-copy-id)if you test your `ssh [email]username@ip.addr.com[/email]` and 
everything went correctly, you should get a command prompt without having to 
enter a password. At that point you shouldbe able to disable password auth in 
the ssh-server and be setup correctly.

---

