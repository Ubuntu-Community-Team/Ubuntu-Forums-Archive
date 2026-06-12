---
title: "OpenPGP acii version of pub or sub key?"
date: 2010-03-02
forum: Security
---

### Post by jase21 on 2010-03-02
I've made OpenPGP keys using gpg 1.4.9 
I have a public key and a sub key.
And a passphrase.
I can distribute the pub key. What is sub key? Can I distribute sub key?
I think the phasephrase is the private key. Right ? (in the RSA Algorithm)?

Where to use the Secure Shell Key? And why to distribute it?
Thank You.

---

### Post by noway2 on 2010-03-02
I will attempt to answer your questions, but here are a couple of excellent documents on the subject.
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)
[https://wiki.ubuntu.com/GPGKey](https://wiki.ubuntu.com/GPGKey)

As you surmised, you have a public and private key and you distribute the public key while keeping the private key secret.  The public key is used to encrypt data and this can then be decrypted with your private key.  Your private key is protected with a password that is to help keep unauthorized users from gaining access to it.  For this reason you should use a good, strong, password.

Using your primary key, you can generate a sub key.  There are limitations on the length, or strength, of your main key.  These limits used to mean that your primary key, which could be used for encryption and signing could only be a 768 bit DSA key.  You could then generate a sub key, say a 4096 bit RSA key that could be used to better encrypt data.

You can both self sign and get your key signed by others who can then publicly assert that you are who you say you are.  When your primary key is signed, the sub keys which are derived from it, are automatically signed along with it.

---

