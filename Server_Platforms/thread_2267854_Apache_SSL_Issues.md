---
title: "Apache SSL Issues"
date: 2015-03-04
forum: Server Platforms
---

### Post by ocpistol on 2015-03-04
When My Server was loading SSL is extremely slow, so I checked error logs.

```
[SIZE=2][Wed Mar 04 09:33:50.549285 2015] [mpm_prefork:notice] [pid 1265] AH00169: caught SIGTERM, shutting down
[Wed Mar 04 09:34:15.061576 2015] [ssl:warn] [pid 6871] AH01909: RSA certificate configured for 127.0.1.1:443 does NOT include an ID which matches the server name
[Wed Mar 04 09:34:15.062832 2015] [ssl:warn] [pid 6871] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Wed Mar 04 09:34:15.157129 2015] [ssl:warn] [pid 6872] AH01909: RSA certificate configured for 127.0.1.1:443 does NOT include an ID which matches the server name
[Wed Mar 04 09:34:15.158381 2015] [ssl:warn] [pid 6872] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Wed Mar 04 09:34:15.163722 2015] [mpm_prefork:notice] [pid 6872] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.6 OpenSSL/1.0.1f configured -- resuming normal operations
[Wed Mar 04 09:34:15.163766 2015] [core:notice] [pid 6872] AH00094: Command line: '/usr/sbin/apache2'[/SIZE]
```

I guess I am not familiar with the SSL stuff were should I begin?

---

### Post by nerdtron on 2015-03-04
Posting you apache config or vhost config will be helpful too.

---

