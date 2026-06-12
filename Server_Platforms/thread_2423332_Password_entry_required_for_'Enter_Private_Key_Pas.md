---
title: "Password entry required for 'Enter Private Key Password:'"
date: 2019-07-21
forum: Server Platforms
---

### Post by fredy50 on 2019-07-21
Hello People

I trying to create a openVPN Server but then i try to start the service i got this error here

[HTML]Password entry required for 'Enter Private Key Password:' (PID 4849).
Please enter password with the systemd-tty-ask-password-agent tool![/HTML]

and this?

[HTML]Sun Jul 21 11:45:28 2019 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jun 22 2017
Sun Jul 21 11:45:28 2019 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Sun Jul 21 11:45:28 2019 Diffie-Hellman initialized with 2048 bit key
Failed to query password: Timer expired
Sun Jul 21 11:46:58 2019 ERROR: could not not read Private Key password from stdin
Sun Jul 21 11:46:58 2019 Exiting due to fatal error[/HTML]

Can someone help me with this?

---

### Post by TheFu on 2019-07-21
Did you enter the password?

---

### Post by fredy50 on 2019-07-21
Yes

---

### Post by TheFu on 2019-07-21
> **fredy50 said:**
> Yes

```
Sun Jul 21 11:46:58 2019 ERROR: could not not read Private Key password from stdin
```
says differently.  I use a credentials file, so I'm not bothered with a password to authenticate with the different servers. There is a setting in the client config ovpn file to point to a credentials file.

---

### Post by fredy50 on 2019-07-21
what does this mean?

i follow the guide here: [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)

---

