---
title: "Freeradius problem, EAP-TTLS works fine, EAP-PEAP does not"
date: 2010-06-04
forum: Server Platforms
---

### Post by dtech on 2010-06-04
Hello all,

my fraternity has been using freeradius for quite some time. However,
there were two problems: the default certificate was used and EAP-PEAP
MSCHAPv2 doesn't work, only EAP-TTLS PAP. This requires users to
install a supplicant (we recommend SecureW2). We would also enable
users to use EAP-PEAP MSCHAPv2 since that is supported by Windows XP
and up by default.

I've cleared the first problem, and I can now connect while validating
the certificate using EAP-TTLS PAP. EAP-PEAP still doesn't work
however. Windows asks for username + password, then again, then fails.

I've configured the module to the best of my knowlegde. When
connecting with Window 7 the following gets written to radius.log:

Sat Jun  5 00:00:59 2010 : Info: rlm_eap_md5: Issuing Challenge
Sat Jun  5 00:00:59 2010 : Info: rlm_eap_mschapv2: Issuing Challenge

As opposed to EAP-TTLS, then the following gets written:

Sat Jun  5 00:03:23 2010 : Info: rlm_eap_md5: Issuing Challenge

Here are the relevant config sections for eap.conf:
```

peap {
   default_eap_type = mschapv2

   copy_request_to_tunnel = yes
   use_tunneled_reply = yes

   proxy_tunneled_request_as_eap = yes
 }
mschapv2 {
}

```

and from radiusd.conf:
```

mschap {
   # I saw this in the default configuration on a site, but in the
documentation it was listed that the server can figure this out for
itself. Is it needed?
   #authtype = MS-CHAP
   use_mppe = yes
   require_encryption = yes
   require_strong = yes
   with_ntdomain_hack = yes
   ntlm_auth = "/usr/bin/ntlm_auth --request-nt-key
--username=%{Stripped-User-Nam$
}

```

As far as I know authentication is performed against local users.
(every user can login through SSH if he wanted). Samba is also
installed (and heavily used) but I could not find a /etc/smbpasswd so
I guess it also authenticates against local users.

Does anyone know where the problem may be? I cannot think of anything
to try anymore.

Thanks in advance,
David

---

