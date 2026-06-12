---
title: "atftpd server file path"
date: 2011-11-09
forum: Server Platforms
---

### Post by spezticle on 2011-11-09
atftp server works fine. i'm trying to modify the default path.
no matter what i change in /etc/default/atftpd it still saves to /srv/tftp

I've tried in the /etc/default/atftpd file:

```

USE_INETD=false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5"

ATFTPD_DIRECTORY="/home/benjamin/tftp"

```

and


```

USE_INETD=false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /home/benjamin/tftp"

```

still saves to /srv/tftp

any insight?
thanks

---

