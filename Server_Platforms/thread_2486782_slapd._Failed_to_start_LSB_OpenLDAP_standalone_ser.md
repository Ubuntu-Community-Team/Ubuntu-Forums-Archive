---
title: "slapd. Failed to start LSB: OpenLDAP standalone server (Lightweight Directory Acc"
date: 2023-05-10
forum: Server Platforms
---

### Post by civilpolisen on 2023-05-10
```
jakob@sssd:~$ sudo service slapd status 
[sudo] password for jakob: 
× slapd.service - LSB: OpenLDAP standalone server (Lightweight Directory Access Protocol)
     Loaded: loaded (/etc/init.d/slapd; generated)
    Drop-In: /usr/lib/systemd/system/slapd.service.d
             &#9492;&#9472;slapd-remain-after-exit.conf
     Active: failed (Result: exit-code) since Wed 2023-05-10 14:39:41 CEST; 1h 5min ago
       Docs: man:systemd-sysv-generator(8)
    Process: 1485 ExecStart=/etc/init.d/slapd start (code=exited, status=1/FAILURE)
        CPU: 43ms

maj 10 14:39:41 sssd slapd[1491]: index memberUid 0x0004
maj 10 14:39:41 sssd slapd[1491]: main: TLS init def ctx failed: -1
maj 10 14:39:41 sssd slapd[1491]: DIGEST-MD5 common mech free
maj 10 14:39:41 sssd slapd[1491]: DIGEST-MD5 common mech free
maj 10 14:39:41 sssd slapd[1491]: slapd stopped.
maj 10 14:39:41 sssd slapd[1491]: connections_destroy: nothing to destroy.
maj 10 14:39:41 sssd slapd[1485]:    ...fail!
maj 10 14:39:41 sssd systemd[1]: slapd.service: Control process exited, code=exited, status=1/FAILURE
maj 10 14:39:41 sssd systemd[1]: slapd.service: Failed with result 'exit-code'.
maj 10 14:39:41 sssd systemd[1]: Failed to start LSB: OpenLDAP standalone server (Lightweight Directory Access Protocol).

```

I've been fighting the Battle of Hope and Fame for quite some time by now!
My research so far is that if you start slapd as root, the priviledges gets wrong.

My setup is Ubuntu Server 22.04 on a static IP on the local network. Nothing fancy. What am I missing!?

---

### Post by MAFoElffen on 2023-05-11
> **civilpolisen said:**
> ```

maj 10 14:39:41 sssd slapd[1491]: main: TLS init def ctx failed: -1

```

That error is sometimes associated with a configuration error, but most times is an expired certificate, or a cert with the wrong permissions.

This may shed some light:
```

slapcat -n 0 | grep '^olcTLS'

```

---

