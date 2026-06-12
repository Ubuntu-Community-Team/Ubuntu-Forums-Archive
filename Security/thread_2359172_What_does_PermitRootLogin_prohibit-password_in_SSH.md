---
title: "What does PermitRootLogin prohibit-password in SSH server mean?"
date: 2017-04-21
forum: Security
---

### Post by Bobby_James on 2017-04-21
I am quite confused about this entry in sshd_config.

```
# Authentication:
LoginGraceTime 120
PermitRootLogin prohibit-password
StrictModes yes
```

I have searched around but find the explanations confusing. What is "prohibit-password" for a root login in plain English? 

What does one need to provide to access root@192.168.x.x?

Thanks!

---

### Post by SeijiSensei on 2017-04-21
A quick Google search brings up [this](https://www.openssh.com/txt/release-7.0):

```

 * The default for the sshd_config(5) PermitRootLogin option has
   changed from "yes" to "prohibit-password".

 * PermitRootLogin=without-password/prohibit-password now bans all
   interactive authentication methods, allowing only public-key,
   hostbased and GSSAPI authentication (previously it permitted
   keyboard-interactive and password-less authentication if those
   were enabled).

```

With that configuration you cannot login in as root with a password.  Use [keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") instead.

---

