---
title: "OpenVPN broken after patch"
date: 2008-05-14
forum: Security
---

### Post by tx413 on 2008-05-14
Okay, so after today's OpenSSL / OpenVPN vulnerability patch craziness, OpenVPN no longer works (on the client side -- haven't tested server side yet).  It asks for the client.key password twice then fails:

```
~$ sudo /etc/init.d/openvpn restart
 * Stopping virtual private network daemon.                                  [ OK ]
 * Starting virtual private network daemon.
Enter pass phrase for /etc/openvpn/client.key:
Enter pass phrase for /etc/openvpn/client.key:
ERROR: 1:
unable to load Private Key
7445:error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:evp_enc.c:461:
7445:error:0906A065:PEM routines:PEM_do_header:bad decrypt:pem_lib.c:425:

 * client (FAILED)
                                                                             [ OK ]
```

The above results are after entering the password correct for the first time and incorrectly for the second time.  If I enter it correctly both times, I don't get the "unable to load client key", but I still get "client (FAILED)".

Also, if I enter the WRONG password the first time it will fail immediately and will not ask again.  My client key is now blacklisted, but I don't think that should affect operations.

I'm running 8.04 on VMWare with two procs specified with an i386 kernel.  Any ideas anyone?

Thanks

---

### Post by tx413 on 2008-05-14
I've reverted to openVPN v2.0.9 -- rebuilt from sources using the latest (rc7) openSSL libraries.  It works and allows me to get back onto the VPN.

And I've checked that both the CA and server / client keys are NOT blacklisted.  So that's nice, but I still can't run on the latest OpenVPN.

---

### Post by tx413 on 2008-05-15
Another update released today - openvpn2.1-rc7-1ubuntu3.2.  Still asks for the password twice and then fails to start just like above.

v2.0.9 still working.

---

### Post by Lazy123 on 2008-05-15
Yep, openvpn is broken here also.

---

### Post by lolobu on 2008-05-15
Yep ... same issue for me. I've removed the pass phrase from my key for the time being.

openssl (rsa|dsa) -in private.key -out privatekey-without-passphrase.key

After that, openvpn works with the new key.

---

### Post by lolobu on 2008-05-26
Nothing new on that one ?

---

### Post by lolobu on 2008-06-14
Today's openvpn update fixed the problem.

---

