---
title: "Back up or transfer key pairs"
date: 2009-02-14
forum: Security
---

### Post by Vincoor on 2009-02-14
How do you back up a private key, or transfer the key pair to another computer? Of course, the public key is easy to back up.

Also, if you want to use a live CD how can you use your private key (during separate logins) if it's not saved on some removable media? I imagine that you'd want to save the whole key pair so you wouldn't lose their relationship.

---

### Post by dfreer on 2009-02-15
Private key is located in the clients ~/.ssh/id_rsa, simply save it to your USB drive/CD/whatever (make sure no one else gets a hold of whatever you save it to!). The only issue to backing it up is having the permission to do so (should be readable/writable only by your user).

To transfer the key pair (like if you reinstall the SSH server and want to use the same key pair), you need to edit the server's ~/.ssh/authorized_keys file to include your Public key (id_rsa.pub). There should be an automated method (probably better) to import your key, but according to my setup: 
authorized_keys == id_rsa.pub
Off the top of my head, the server uses the public key to validate the private key, and never keeps a copy of the private key on the server-side drive.

As for your last question, not sure I understand fully, but the only thing I can think of is you would need to create a custom live CD that contains a fully installed SSH server and your public key already, you wouldn't be able to use the standard live CD unless you (a) install SSH server (b) import your public key each and every time.

---

### Post by Vincoor on 2009-02-15
> **dfreer said:**
> Private key is located in the clients ~/.ssh/id_rsa, simply save it to your USB drive/CD/whatever (make sure no one else gets a hold of whatever you save it to!). The only issue to backing it up is having the permission to do so (should be readable/writable only by your user).

To transfer the key pair (like if you reinstall the SSH server and want to use the same key pair), you need to edit the server's ~/.ssh/authorized_keys file to include your Public key (id_rsa.pub). There should be an automated method (probably better) to import your key, but according to my setup: 
authorized_keys == id_rsa.pub
Off the top of my head, the server uses the public key to validate the private key, and never keeps a copy of the private key on the server-side drive.

As for your last question, not sure I understand fully, but the only thing I can think of is you would need to create a custom live CD that contains a fully installed SSH server and your public key already, you wouldn't be able to use the standard live CD unless you (a) install SSH server (b) import your public key each and every time.

Thanks for your reply, however, I'm not involved in any server administration, I'm only referring to key pairs for use with email. Just your basic Ubuntu/seahorse/evolution setup.

I'd like to be able to save a copy of a key pair generated on one computer onto another. Then, if someone sends me an encrypted email I'd be able to decrypt it whether I'm using 1) my desktop, 2) my laptop, or 3) running a live CD on whatever.

I'm not a very advanced user. It's possible that this question is so basic (dumb?) that it tends to be interpreted as something more sophisticated.

---

### Post by kevdog on 2009-02-15
What kind of keys are we talking about here?  SSH keys or GPG keys?

---

### Post by dfreer on 2009-02-15
> **Vincoor said:**
> I'm not a very advanced user. It's possible that this question is so basic (dumb?) that it tends to be interpreted as something more sophisticated.

No, it was just me assuming you were referring to using SSH. Not sure I can help you with email keys (gpg or whatever).

---

### Post by Vincoor on 2009-02-17
> **kevdog said:**
> What kind of keys are we talking about here?  SSH keys or GPG keys?

GPG keys

---

### Post by kevdog on 2009-02-17
gpg --list-secret-keys

This will list keys on your secret keyring

gpg --output <outfile> --armor --export-secret-key <key_identifier as gleaned from above>

key_identifier usually in the form of something like: ABCDFE01  

Depending on your host, you could also just copy the entire .gpg directory if you wanted to do it that way also.

Of course there is the paperkey utility if you need to make a paperkey backup of your secret key: [http://www.jabberwocky.com/software/paperkey/](http://www.jabberwocky.com/software/paperkey/)

---

### Post by Vincoor on 2009-02-17
> **kevdog said:**
> gpg --list-secret-keys

This will list keys on your secret keyring

gpg --output <outfile> --armor --export-secret-key <key_identifier as gleaned from above>

key_identifier usually in the form of something like: ABCDFE01  

Depending on your host, you could also just copy the entire .gpg directory if you wanted to do it that way also.

Of course there is the paperkey utility if you need to make a paperkey backup of your secret key: [http://www.jabberwocky.com/software/paperkey/](http://www.jabberwocky.com/software/paperkey/)
Thank you! Works great.

---

### Post by CHaoSlayeR on 2009-11-06
Just for the record (and for myself)...

I recently installed Karmic on a new partition and of course I wanted to have all the keys from my Jaunty installation. So what I did was mounting the Jaunty partition and then did this (assuming the user IDs are the same on both installations):

```
gpg --homedir /media/jaunty/home/chaoslayer/.gnupg/ --export | gpg --import
```

This way you don't have to deal with temporary files. Just nice.

C]-[aoZ

---

