---
title: "How do I login using Kerberos?"
date: 2009-05-21
forum: Server Platforms
---

### Post by lightnb on 2009-05-21
I've followed this guide:

[https://help.ubuntu.com/8.10/serverguide/C/kerberos.html#kerberos-linux-client](https://help.ubuntu.com/8.10/serverguide/C/kerberos.html#kerberos-linux-client)

I can get a ticket (on the client machine) using kinit username.

But it wont accept my Kerberos username to logon to the machine?

What am I missing?

---

### Post by HermanAB on 2009-05-21
Maybe you messed up the configuration of PAM?

---

### Post by lightnb on 2009-05-21
The tutorial didn't mention configuring PAM at all- So I assumed that part of installing the Kerberos PAM module would include configuring it to work...

I don't entirely understand the syntax of the PAM files yet, but here's what the client machine's say:


common-session:
```

session required    pam_unix.so
session optional    pam_krb5.so
session optional    pam_foreground.so

```

common-auth:
```

auth    sufficient  pam_unix.so nullok_secure
auth    sufficient  pam_krb5.so ignore_root use_first_pass
auth    required   pam_deny.so

```

common-account:
```
account required    pam_unix.so broken_shadow
```

common-password:
```

password   required   pam_unix.so nullok obscure min=4 max=8 md5
password        optional        pam_krb5.so ignore_root

```

Maybe someone could tell what's wrong?

---

### Post by gpredrag on 2009-05-22
Without knowing your exact setup...
This configuration assumes that user in question exist on local machine. It's just that password is checked against kerberos instead of local shadow file. But he/she still has to be valid user on the machine, that is
```
id that_user
```
should return his uid number.
What are the errors in /var/log/auth.log?

---

