---
title: "Where and when should we use OpenPGP and OpenSSH?"
date: 2010-06-10
forum: Security
---

### Post by opengl_cpp on 2010-06-10
hi, I wonder what is the real difference between these two tools or standards: OpenPGP and OpenSSH.
 
I use gnupg(OpenPGP implementation)  and ssh(OpenSSH implementation). both of theme produce public and private key pairs, what is the real difference between these two tools. Are these tool interchangeable, I mean can i use openpgp instead of openssh?

---

### Post by -grubby on 2010-06-10
They're completely different. OpenSSH is an implementation of a [Secure Shell](http://en.wikipedia.org/wiki/Secure_Shell), whereas OpenPGP is an implementation of [Pretty Good Privacy](http://en.wikipedia.org/wiki/Pretty_Good_Privacy). They are not interchangeable.

---

### Post by rookcifer on 2010-06-10
> **opengl_cpp said:**
> hi, I wonder what is the real difference between these two tools or standards: OpenPGP and OpenSSH.

The main difference is what they're used for.  Technically, the keys are very similar (they both can use RSA and/or DSA, for instance).  
 
> I use gnupg(OpenPGP implementation)  and ssh(OpenSSH implementation). both of theme produce public and private key pairs, what is the real difference between these two tools. Are these tool interchangeable, I mean can i use openpgp instead of openssh?

There is supposedly [a tool]("http://www.red-bean.com/~nemo/openssh-gpg/") that can convert between ssh/GPG keys, but I have ever attempted to use it.  Most people just generate two key pairs.

---

### Post by Agent ME on 2010-06-10
**OpenSSH** is a program that follows the SSH protocol. The SSH protocol is used to establish a secure connection to a server, and can have traffic forwarded over it and be used to control a remote terminal. This is the most common way to remotely administer a Unix-type server.

GPG is a program that follows the **OpenPGP** standards. OpenPGP defines ways to encrypt and digitally sign files. It's usually used to protect and authenticate emails (similar to S/MIME in this use). It's frequently also used to distribute files with an external sig file, which authenticates that the file was not changed since the author signed it.

Note that while gpg can encrypt files, it isn't suited for on-the-fly encryption; if you want to have your personal files on your hard drive be always protected from attackers who get physical access to your system, you will need to use an encryption file system or block device, such as LUKS for whole-disk encryption or EcryptFS for per-user home directory encryption (both of these are available from the Ubuntu installers).

---

