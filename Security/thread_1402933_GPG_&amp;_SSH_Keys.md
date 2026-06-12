---
title: "GPG &amp; SSH Keys"
date: 2010-02-09
forum: Security
---

### Post by sharpdust on 2010-02-09
Can anyone give me a short description of the difference between GPG and SSH keys?

Also, is it possible to combine the two keys? Meaning I can just use one key for both applications?

---

### Post by Agent ME on 2010-02-09
Client SSH keys are used to authenticate who you are to a server. (The SSH server also has its own pair of keys it uses to authenticate who it is to the clients.)

GPG keys are used to authenticate a message with a digital signature, or to act as a key for decrypting messages to you.

SSH and GPG are separate programs that do not depend on each other or interact in normal use. They both keep their own keyrings.

It *might* be possible to convert a GPG key to an equivalent SSH key or vice versa, but this conversion isn't in any way standard or particularly useful, and any mistakes in the conversion could possibly give away your private keys.

There's no real need to try to use the same key for both. If you want people who know your GPG (public) key to be absolutely sure of what you say your SSH (public) key is, then you can sign a public message (like on some webserver) stating your SSH key and name with your GPG key.

---

### Post by sharpdust on 2010-02-09
Thank you for your response Agent Me.
However, I have to think it's possible to use the same key for both since you can do

ssh-keygen -t rsa -b 2048

and

gpg --gen-key 
and then select rsa encryption, 2048 bits long.

---

### Post by Rubicon_82 on 2010-02-09
Although GPG and SSH can both be configured to use the same type of key encryption and key length (e.g. 2048 bit RSA), the format of the key files is quite different.  For example, GPG key files include meta data such as name and e-mail address, whereas SSH key files often include options which are passed on to the SSH server.  Additionally, both SSH and GPG can encrypt the private/secret half of the key, but they do so in different ways (SSH uses 3DES, GPG uses CAST5). As a result, SSH can't decrypt GPG secret keys, and vice versa.

Although it *may* be possible to manually convert a GPG key into something SSH could use, it would be quite difficult and could possibly lead to your private keys being exposed during the GPG to SSH conversion.

The question you're asking about using the same key for GPG and SSH, given that they both use 2048 bit RSA keys, would be analogous to the following:

The locks on both the door of my house and my car use 5-pin tumblers.  Do you think it would be possible for me to use the same key to unlock my house or start my car?

---

### Post by sharpdust on 2010-02-10
> **Rubicon_82 said:**
> Although GPG and SSH can both be configured to use the same type of key encryption and key length (e.g. 2048 bit RSA), the format of the key files is quite different.  For example, GPG key files include meta data such as name and e-mail address, whereas SSH key files often include options which are passed on to the SSH server.  Additionally, both SSH and GPG can encrypt the private/secret half of the key, but they do so in different ways (SSH uses 3DES, GPG uses CAST5). As a result, SSH can't decrypt GPG secret keys, and vice versa.

Although it *may* be possible to manually convert a GPG key into something SSH could use, it would be quite difficult and could possibly lead to your private keys being exposed during the GPG to SSH conversion.

The question you're asking about using the same key for GPG and SSH, given that they both use 2048 bit RSA keys, would be analogous to the following:

The locks on both the door of my house and my car use 5-pin tumblers.  Do you think it would be possible for me to use the same key to unlock my house or start my car?

Good analogy. It would be purely for proof of concept. I understand it would be nearly impossible to have people change. But I figure if you can write some middle-man application that takes the keys and converts your GPG key to SSH key syntax and vice versa, then you'd be set.

---

### Post by noway2 on 2010-02-10
I was discussing this very subject earlier today in a linux users group.  One of the participants pointed me towards the package signing-party, which contains several tools for working with PGP keys.  Apparently one of the tools in the package is for converting between an SSH and PGP key, on the basis that they both use the same type of encryption (RSA).

---

### Post by Geremia on 2012-03-04
> **Agent ME said:**
> It *might* be possible to convert a GPG key to an equivalent SSH key or vice versa, but this conversion isn't in any way standard or particularly useful, and any mistakes in the conversion could possibly give away your private keys.It is possible with gpgkey2ssh. I am not sure about [the opposite operation]("http://www.linuxquestions.org/questions/linux-security-4/opposite-of-gpgkey2ssh-932739/").

---

### Post by Damascushead on 2012-03-05
This helps me out as well thanks!

---

