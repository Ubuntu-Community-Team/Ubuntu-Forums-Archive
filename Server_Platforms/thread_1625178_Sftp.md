---
title: "Sftp"
date: 2010-11-18
forum: Server Platforms
---

### Post by trentscott on 2010-11-18
I want to connect to the same machine that that I have OpenSSH server on which uses keys and I have disabled password-based logins (for ssh). Apparently, this also affects SFTP which makes sense. How do I setup SFTP to use key-based authentication?

---

### Post by CharlesA on 2010-11-18
As long as the key is in ~/.ssh/ you can connect without adding any other switches.

I think it gets tricky when you don't have the key in the default location.

```
charles@thor:~$ sftp charles@luna
Connecting to luna...
Enter passphrase for key '/home/charles/.ssh/id_rsa':
sftp>

```

---

### Post by amauk on 2010-11-18
> **CharlesA said:**
> I think it gets tricky when you don't have the key in the default location.Not really tricky, you just need to specify the location of the private key with -i

```
sftp -i /path/to/private.key user@machine
``````
scp -i /path/to/private.key local.file user@machine:/remote/dir/
```
etc.

---

### Post by CharlesA on 2010-11-18
Ah. I had problems getting sftp to connect to a different port and ended up using something like -o -P 2222 or somethign like that.

Thanks for the info. :)

---

### Post by amauk on 2010-11-18
ah, ok
never bothered changing default ports, etc.
(I'd only forget them ;))

---

### Post by CharlesA on 2010-11-18
Heh. I ended up changing the ports back to the default, since I was getting annoyed with adding extra switches. ;)

Thanks again for the info. Learn something new everyday. :)

---

