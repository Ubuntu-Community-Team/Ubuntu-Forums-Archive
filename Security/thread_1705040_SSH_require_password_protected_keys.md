---
title: "SSH: require password protected keys"
date: 2011-03-11
forum: Security
---

### Post by fela on 2011-03-11
How can I configure my SSH server (OpenSSH on Debian 5) so that it requires public key authentication *and that the keys are password protected*?

cheers

---

### Post by cariboo on 2011-03-11
Enter a password when you are creating a key. Use:

```
ssh-keygen -t rsa
```

to generate the key, and the process will ask yo to enter a pass-phrase.

---

### Post by fela on 2011-03-11
> **cariboo907 said:**
> Enter a password when you are creating a key. Use:

```
ssh-keygen -t rsa
```

to generate the key, and the process will ask yo to enter a pass-phrase.

Yes but is there a way of requiring users' SSH keys to be password protected - and if not dropping their connection?

thanks

EDIT: never mind, I think I'm going to go with standard password authentication instead.

---

### Post by matt_symes on 2011-03-11
Hi

> Yes but is there a way of requiring users' SSH keys to be password protected - and if not dropping their connection?

What do you mean ? If they don't know the passphrase they will not be able to log on and create the connection.

Talk through what you mean.

Kind regards

---

### Post by fela on 2011-03-11
> **matt_symes said:**
> Hi



What do you mean ? If they don't know the passphrase they will not be able to log on and create the connection.

Talk through what you mean.

Kind regards

Well there's quite a few people requesting SSH access to my server. I'd like to use public keys cause I heard it was more secure, however it wouldn't be more secure if they used password-less keys. So my idea was to have everyone use public keys but force them to have passwords (and strong ones at that).

---

### Post by matt_symes on 2011-03-11
Hi

Have a read of this.

[http://www.puddingonline.com/~dave/publications/SSH-with-Keys-HOWTO/document/html/SSH-with-Keys-HOWTO-5.html](http://www.puddingonline.com/~dave/publications/SSH-with-Keys-HOWTO/document/html/SSH-with-Keys-HOWTO-5.html)

Is it what you mean ?

Kind regards

---

### Post by CharlesA on 2011-03-11
I don't think that's possible. Even if you set it up to use keys, someone could still use a key without a passphrase.

In any case, you could just tell them to punch in a strong passphrase when generating the keypair.

---

### Post by fela on 2011-03-12
Hmm, I'm going to go with a centralized password system now (no public keys). Well it supports public keys but if people want SSH access I'll give them the password for a low-privilege account.

Thanks guys :)

---

### Post by CharlesA on 2011-03-12
You could also just chroot them into their home directory and leave it at that.

---

