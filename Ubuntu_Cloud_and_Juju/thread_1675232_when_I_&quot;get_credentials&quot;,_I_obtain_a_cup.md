---
title: "when I &quot;get credentials&quot;, I obtain a cuple of warnings"
date: 2011-01-25
forum: Ubuntu Cloud and Juju
---

### Post by mcanonic on 2011-01-25
Hi,
following the UEC/CDInstallation documentation, when I try to obtain the certificate file, I get two warnings:
```

mcanonic@minicloud02:~/.euca$ sudo euca_conf --get-credentials mycreds.zip
[sudo] password for mcanonic: 
--2011-01-25 13:12:18--  https://localhost:8443/getX509?user=admin&code=nFWLCnpe25ORB85lQ523kTwvOeWEWNcJqMgVXilkUyefngYw6uoPWuiv4dSy6e0ukJBxoATsMmdNt01dttxA
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:8443... failed: Connection refused.
Connecting to localhost|127.0.0.1|:8443... connected.
WARNING: cannot verify localhost's certificate, issued by `/C=US/O=Cloud/OU=Eucalyptus/CN=db':
  Self-signed certificate encountered.
WARNING: certificate common name `db' doesn't match requested host name `localhost'.
HTTP request sent, awaiting response... 200 OK
Length: 4893 (4.8K) [application/zip]
Saving to: `mycreds.zip'

100%[======================================>] 4,893       --.-K/s   in 0s      

2011-01-25 13:12:20 (510 MB/s) - `mycreds.zip' saved [4893/4893]

```

Is it ok?
M

---

### Post by kim0 on 2011-01-25
Yes, it should be ok :)
Those couple of warnings are just wget being unable to verify a secure chain (https) certificate hierarchy. Really nothing to worry about

---

