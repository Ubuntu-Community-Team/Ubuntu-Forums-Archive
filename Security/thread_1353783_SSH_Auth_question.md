---
title: "SSH Auth question"
date: 2009-12-13
forum: Security
---

### Post by vexy on 2009-12-13
Before all, Hello everyone, I'm new in this forum.

I have a trouble as regarding SSH Auth. I detain the RemoteHost Private Key. Is there any solution to auth via ssh from LocalHost to RemoteUser@RemoteHost:port while I have only Remote's Private Key ?

I can't upload my public key to remote host because I don't know RemoteUser's password. As I know, detaining the Remote's private key, I could generate Remote's public key. Does this help any way ?

Thank you!

---

### Post by BkkBonanza on 2009-12-13
No. You need either a password or to put your public key in the remote host's authorized_users file. I'm assuming you don't have physcial access because if you did then you could get root and add your key.

---

### Post by Rob_H on 2009-12-13
> **vexy said:**
> As I know, detaining the Remote's private key, I could generate Remote's public key. Does this help any way ?

Knowing the private key does not allow you to "regenerate" the public key. They come as a pair. The only difference between them lies in how each one is used. Nothing technical.

---

### Post by BkkBonanza on 2009-12-13
I'm not sure if an ssh key is similar to a gpg key. With gpg the private key does contain a copy of the public key and it is possible to get it back. However, even if that were the case you don't need the public key of the server, it's the server that needs your (client) public key. After all, public keys are generally given out to whoever (they're public) but it is the server that needs to decide who can come in to play, and hence has to already have your key to confirm you are who you say.

---

### Post by falconindy on 2009-12-13
> **Rob_H said:**
> Knowing the private key does not allow you to "regenerate" the public key. They come as a pair. The only difference between them lies in how each one is used. Nothing technical.
If this were true, public key authentication would not work. Having a public key gives you nothing without the private key. Having the private key gives you everything.

From the man page for 'ssh-keygen':
```
       -y     This option will read a private OpenSSH format file and print an  OpenSSH  public  key  to
              stdout.
```

---

### Post by Rob_H on 2009-12-13
> **falconindy said:**
> If this were true, public key authentication would not work. Having a public key gives you nothing without the private key. Having the private key gives you everything.

From the man page for 'ssh-keygen':
```
       -y     This option will read a private OpenSSH format file and print an  OpenSSH  public  key  to
              stdout.
```

I was unaware that SSH stores a copy of the public key with the private key, but it's an implementation detail of that particular tool set. In general, public-key cryptography does not require a copy of the public key to be stored as part of the private key package.

---

### Post by falconindy on 2009-12-13
> **Rob_H said:**
> I was unaware that SSH stores a copy of the public key with the private key, but it's an implementation detail of that particular tool set. In general, public-key cryptography does not require a copy of the public key to be stored as part of the private key package.
You misunderstand. I can take my private key file (which contains **no** public key) and regenerate my public key based on the private key (provided of course that I have the correct password). It's a fact of public key cryptography and has little to do with the implementation.

---

### Post by BkkBonanza on 2009-12-13
I don't think you're right about that. You may be able to generate a new public key but I believe it would be close to impossible to generate the same public key again.

If you think you can then show me how. I'm interested to know. 

gpg or ssh can generate a key pair, but I have never seen an option to generate one half from the other. If you could then you could also likely generate a private key from it's public one.

---

### Post by falconindy on 2009-12-13
You're comparing GPG to SSH which is a completely invalid comparison. GPG uses symmetric cryptography whereas SSH uses asymmetric. I suggest you read up on the difference.

Just try it for yourself. Generate a new private and public key pair. Inspect the resulting private key half to reassure yourself that its only the private key and contains no public key. Now rename the public key. Feed the private half back to ssh-keygen. Provide the password for the private half and out pops the public half. Run a diff on the original and the new public key halves. They are identical.

PuTTY does this as well when converting OpenSSH keys to PuTTY's own format. Provide a private key to puttygen, and it will happily churn out a new private (and public) key which are **identical** in function to their OpenSSH counterparts.

If this process wasn't possible, public key cryptography **would not work**. If the private key doesn't know what its own public half looks like, how does the authentication happen? It doesn't.

Quote from Wikipedia's page regarding Public-key cryptography:
> The distinguishing technique used in public key cryptography is the use of asymmetric key algorithms, where the key used to encrypt a message is not the same as the key used to decrypt it. Each user has a pair of cryptographic keys &#8212; a public key and a private key. The private key is kept secret, whilst the public key may be widely distributed. Messages are encrypted with the recipient's public key and can only be decrypted with the corresponding private key. The keys are related mathematically, but the private key cannot be feasibly (ie, in actual or projected practice) derived from the public key. It was the discovery of such algorithms which revolutionized the practice of cryptography beginning in the middle 1970s.

---

### Post by BkkBonanza on 2009-12-13
Yes, actually after digging around to figure this out I found that the private key file format includes not just the private key but all the info. It has the modulus, public exponent, private exponent, prime1, prime2, exponent1, exponent2, and a coefficient. So given all those numbers it can of course re-calculate anything it needs. 

I was going by some info I saw that said the private key only contained the modulus and private exponent, which seems to be wrong. If it only had those then it could not regenerate it's public exponent.

The public key file format has only the modulus and public exponent.

I don't think authentication depends on the private key having those extra details as long as the public key is also present. I can see it's more convenient in one file though. But a client can verify a signature without the private key details since the message has been signed already with that key.

For any encrypt/decrypt the math needs the modulus and the appropriate exponent.

Also note I was comparing gpg only so far as using it's asymmetric functions as it does offer both.

The info I found about the private key including all the info is here:
[http://ospkibook.sourceforge.net/docs/OSPKI-2.4.7/OSPKI-html/sample-openssl-usage.htm](http://ospkibook.sourceforge.net/docs/OSPKI-2.4.7/OSPKI-html/sample-openssl-usage.htm)

In the PEM format you can't tell but the same info as TXT format shows internals. Actually I realize the formats are different. I looked around a lot for the ssh private format. Apparently the private formats are non-standardized, so this format here was the closest I could find.

Update: I just found a reference saying the ssh private key format is the one used by openssl for the dsa key. So I expect they contains the same info.

---

