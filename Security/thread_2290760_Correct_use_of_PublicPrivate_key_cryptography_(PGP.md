---
title: "Correct use of Public/Private key cryptography (PGP, GPG, GnuPG, OpenPGP)"
date: 2015-08-15
forum: Security
---

### Post by enricobe on 2015-08-15
Hello,
I need some help with Public/Private key cryptography and how to use it correctly.

I have created a OpenPGP key and now I have:
1) Public Key
2) Private Key
3) Passphrase

I know that the Public Key is the one that I need to share with others and the Passphrase is only in my mind. I can't fully understand how to use the Private Key.

-Public Key: used to encrypt files/messages that only I can read.
-The Passphrase is requested to decrypt the encrypted file

-where The Private Key should be stored? It must be kept secret like the passphrase? If it must be kept secret, why it's stored in the key-manager like Gnome's seahorse?

---

### Post by Dennis N on 2015-08-15
> **enricobe said:**
> ...-where The Private Key should be stored? It must be kept secret like the passphrase? If it must be kept secret, why it's stored in the key-manager like Gnome's seahorse?

gnupg stores public keys in its public keyring file. The name and location of this file is actually displayed when you list the keys:
```
dmn@Daphne:~$ gpg --list-keys
/home/dmn/.gnupg/pubring.gpg
--snip---

```
gnupg stores secret keys in its secret keyring file:
```
dmn@Daphne:~$ gpg --list-secret-keys
/home/dmn/.gnupg/secring.gpg
--snip--
```

Keys are stored in these files by gnugpg when generated, or when imported. The passphrase will be needed to access the secret key of a key pair when decoding.

---

### Post by enricobe on 2015-08-15
> **Dennis N said:**
> gnupg stores public keys in its public keyring file. The name and location of this file is actually displayed when you list the keys:
```
dmn@Daphne:~$ gpg --list-keys
/home/dmn/.gnupg/pubring.gpg
--snip---

```
gnupg stores secret keys in its secret keyring file:
```
dmn@Daphne:~$ gpg --list-secret-keys
/home/dmn/.gnupg/secring.gpg
--snip--
```

Keys are stored in these files by gnugpg when generated, or when imported. The passphrase will be needed to access the secret key of a key pair when decoding.

Thank you very much. 
One more question. If the Passphrase is used to access the private key, i can suppose that it is like a normal password. If this is true, there are all the security risks related to a normal password. Am i right?

---

### Post by untrustytahr on 2015-08-15
> **enricobe said:**
> Thank you very much. 
  ...If this is true, there are all the security risks related to a normal password. Am i right?

Correct.  The password is the weakest link in the overall design.  Some people will export it to a different device such as a usb stick if there is sufficient reason to separate it from a machine and plug it in when needed to decrypt something, but that is probably a little bit of overkill if you are beginning to learn how to use gpg.

From the gpg man page:


> WARNINGS
       Use a *good* password for your user account and a *good* passphrase to protect your secret key. This passphrase is the weakest part  of  the  whole  system.
       Programs to do dictionary attacks on your secret keyring are very easy to write and so you should protect your "~/.gnupg/" directory very well.

---

### Post by enricobe on 2015-08-15
> **untrustytahr said:**
> Correct.  The password is the weakest link in the overall design.  Some people will export it to a different device such as a usb stick if there is sufficient reason to separate it from a machine and plug it in when needed to decrypt something, but that is probably a little bit of overkill if you are beginning to learn how to use gpg.

From the gpg man page:

I'm not an FBI's Most Wanted person :) I just want to better understand how the Public/Private key cryptography works. I'm using it primarily to encrypt my cloud-stored personal files and I have not saved the passphrase anywhere, it is just in my mind. If I don't save the passphrase on the PC can I feel secure?

You say that "Some people will export it to a different device such as a usb stick", but how long should the passphrase be? Mine is composed by 14 letters + 1 special character + 2 numbers... Is it too short?
For my needs it is ok, but I just want to understand what is the best phassphrase. Thank you! :)

---

### Post by untrustytahr on 2015-08-15
> **enricobe said:**
> ... I just want to better understand how the Public/Private key cryptography works. I'm using it primarily to encrypt my cloud-stored personal files...
Public/Private key encryption is a type of encryption known as asymmetric (two different keys) encryption.  It generally is used for encryption where two or more entities are exchanging information and ensures that only the intended recipient can decrypt it.  Protecting files for cloud storage doesn't really need asymmetric keys- you can safely encrypt them symmetrically and spare yourself the need to maintain two different keys. 

 > **enricobe said:**
> and I have not saved the passphrase anywhere, it is just in my mind. If I don't save the passphrase on the PC can I feel secure?
I should clarify what i meant by storing on a usb stick.  I meant people will export the private key on a usb stick, not the passphrase.

> **enricobe said:**
>  but how long should the passphrase be? Mine is composed by 14 letters + 1 special character + 2 numbers... Is it too short?
There is no easy straight forward answer to this.  There are many factors that determine if a password is "good".  This explanation gives a decent overview:[https://en.wikipedia.org/wiki/Password_strength](https://en.wikipedia.org/wiki/Password_strength)
[I][U][B]
Generally speaking[/B][/U][/I] 17 characters with alpha-numeric & special characters would be considered secure today.

---

### Post by enricobe on 2015-08-16
> **untrustytahr said:**
> Public/Private key encryption is a type of encryption known as asymmetric (two different keys) encryption.  It generally is used for encryption where two or more entities are exchanging information and ensures that only the intended recipient can decrypt it.  Protecting files for cloud storage doesn't really need asymmetric keys- you can safely encrypt them symmetrically and spare yourself the need to maintain two different keys. 

 
I should clarify what i meant by storing on a usb stick.  I meant people will export the private key on a usb stick, not the passphrase.


There is no easy straight forward answer to this.  There are many factors that determine if a password is "good".  This explanation gives a decent overview:[https://en.wikipedia.org/wiki/Password_strength](https://en.wikipedia.org/wiki/Password_strength)
[I][U][B]
Generally speaking[/B][/U][/I] 17 characters with alpha-numeric & special characters would be considered secure today.

Ok! Thank you for your help :)

---

### Post by obake2 on 2015-08-18
Further resources for you:

1) Video: [Public Key Cryptography]("https://www.youtube.com/watch?v=GSIDS_lvRv4") (beginner friendly)

2) Encryption, and other self defense method guides:

[https://ssd.eff.org/en/index](https://ssd.eff.org/en/index)


3)[ Privacy and Security Howto]("https://trisquel.info/en/wiki/security")

---

### Post by enricobe on 2015-08-24
> **obake2 said:**
> Further resources for you:

1) Video: [Public Key Cryptography]("https://www.youtube.com/watch?v=GSIDS_lvRv4") (beginner friendly)

2) Encryption, and other self defense method guides:

[https://ssd.eff.org/en/index](https://ssd.eff.org/en/index)


3)[ Privacy and Security Howto]("https://trisquel.info/en/wiki/security")thank you, too! :)

---

