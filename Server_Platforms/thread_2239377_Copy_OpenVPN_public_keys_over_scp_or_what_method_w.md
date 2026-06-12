---
title: "Copy OpenVPN public keys over scp or what method works from server to client"
date: 2014-08-13
forum: Server Platforms
---

### Post by excetara2 on 2014-08-13
I am trying to copy the keys I generated on my server via scp but could only copy the ca.crt. The two client certificates throw an error with scp saying

```
Permission denied (publickey,password).

```

or

```
scp: /etc/openvpn/easy-rsa/keys/clientUbu.crt: Permission denied

```

when using none root.

Any suggestions?

---

### Post by nerdtron on 2014-08-13
YUP! That is correct! And it is the standard security feature.

You see, certificate files has the permission of 600 which means only the owner will be able to read them, in your case, the root user only.

Well you can either login as root and copy the files, or login as root and copy the contents of the certificate and paste it on the client
Or you can change the permissions of the certificates to 644 so that other users can read them. Then change them back to 600.

Always make sure the certificate files are kept secret due to security reasons.

---

### Post by excetara2 on 2014-08-14
Thanks

---

