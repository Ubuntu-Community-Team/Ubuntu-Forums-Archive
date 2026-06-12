---
title: "Generating hash password"
date: 2010-03-12
forum: Security
---

### Post by Devang on 2010-03-12
Hi everyone,

I am generating  script to add user in ubuntu 9.04.

I  am able to add user but i want to assign password to that user from script .

But it's not able to assign password . In other words not able to create hash for that text.

So is there any ways or script or command to generate hash from given phrase.

Thanks in advance....

---

### Post by cdenley on 2010-03-12
For an md5 hash:
```

sudo usermod -p `mkpasswd -m md5 newpassword` username

```

I think 9.04 supports SHA-512 hashes, though:
```

sudo usermod -p `mkpasswd -m SHA-512 newpassword` username

```

This isn't the most secure method of setting passwords, though, as the password can be captured by a user with local access when passed as a command argument.

---

