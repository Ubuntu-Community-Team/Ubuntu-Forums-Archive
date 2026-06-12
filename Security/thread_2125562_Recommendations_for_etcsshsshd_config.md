---
title: "Recommendations for /etc/ssh/sshd_config ?"
date: 2013-03-14
forum: Security
---

### Post by nadamsieee on 2013-03-14
I have a server that I wish to log into without being prompted for a password.

So I've set this up using [ssh keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

On the server I made the following changes to /etc/ssh/sshd_config (from the stock file that ships with 12.04):

```
$ diff /etc/ssh/sshd_config /etc/ssh/sshd_config.original
27c27
< PermitRootLogin no
---
> PermitRootLogin yes
51c51
< PasswordAuthentication no
---
> #PasswordAuthentication yes
```

My goal is, of course, to minimize any security risks under this scheme.

Any other recommendations?

---

### Post by prodigy_ on 2013-03-14
PermitRootLogin yes is always risky. Particularly with unprotected keys. Leaked key = someone can get full control. Passwords are OK but if your server is open to the Internet you want strong passwords.

---

### Post by nadamsieee on 2013-03-14
> **prodigy_ said:**
> PermitRootLogin yes is always risky. Particularly with unprotected keys. Leaked key = someone can get full control. Passwords are OK but if your server is open to the Internet you want strong passwords.

Both are disabled, per above (current config shown first, followed by stock config for 12.04). :)

---

### Post by prodigy_ on 2013-03-14
:) That's why I hate diff.

---

### Post by unspawn on 2013-03-16
> **nadamsieee said:**
> I have a server that I wish to log into without being prompted for a password.
Then combine an un unprivileged account with using ssh-agent.


> **nadamsieee said:**
> Any other recommendations?
Other than that adding fail2ban (which IMHO is always good) it kind of depends what the purpose is. In ~/.ssh/authorized_keys you can limit key access by subnet range ("from=") and allow it to only perform a specific command ("command=").

---

### Post by ptn107 on 2013-03-16
Allow only specified users to connect:

```
AllowUsers username
```

Users listed are separated by a space.  You can specify as *user* or *user@host* or mix and match.

ex.

```
AllowUsers phil root@192.168.1.1 greg@192.168.1.1 craig
```

---

