---
title: "Howto change password from cgi script?"
date: 2009-02-12
forum: Server Platforms
---

### Post by mysteron on 2009-02-12
Hi.

I've recently installed a Ubuntu 8.10 server, but now I'm trying to figure out how to change the password for a local user account from a suidperl CGI script. I've used before the passwd --stdin function in CentOS, but it seems that this does not work in Ubuntu.

I've also tried the 'echo "password:name" | chpasswd' but that does not either work properly. A new password is set, but it is not encoded the same way as a password is done with the passwd command.

I'd really appreciate help for solving this issue :)


Thx,
/mysteron

---

### Post by cdenley on 2009-02-12
how about...
```

usermod -p `mkpasswd -m SHA-512 newpass` username

```

---

### Post by mysteron on 2009-02-13
> **cdenley said:**
> how about...
```

usermod -p `mkpasswd -m SHA-512 newpass` username

```

Thank you, works like a charm :)


/mysteron

---

