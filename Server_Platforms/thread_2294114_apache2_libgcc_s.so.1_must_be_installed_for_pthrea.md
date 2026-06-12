---
title: "apache2 libgcc_s.so.1 must be installed for pthread_cancel to work on 12.04.5"
date: 2015-09-09
forum: Server Platforms
---

### Post by @hJ?oS6^ on 2015-09-09
I updated from 10.04 to 12.04.5 a few months back. Ever since I get this line in my Apache error log, over and over and over:

libgcc_s.so.1 must be installed for pthread_cancel to work

I've seen many people talking about this problem and in 99% of the cases they have vsftp installed which causes it, in my case I don't have that installed. So the fixes they've come up with won't work in my case.

The libgcc package is installed:
root@host:# dpkg -l | grep libgcc
ii  libgcc1                              1:4.6.3-1ubuntu5                    GCC support library
ii  libgcc1:i386                         1:4.6.3-1ubuntu5                    GCC support library



and ldconfig sees the libraries in what I think are the correct locations:
root@host:# ldconfig -p | grep libgcc
 libgcc_s.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libgcc_s.so.1
 libgcc_s.so.1 (libc6) => /lib/i386-linux-gnu/libgcc_s.so.1
 libgcc_s.so.1 (libc6) => /usr/lib32/libgcc_s.so.1

I'm not sure what's missing here. Can anybody help?

---

### Post by sandyd on 2015-09-09
Is this a self-compiled apache2 or from a package?
If it is self-compiled, you will have do a rebuild.

If you are running apache2 in a chroot, try adding
```

 LoadFile /lib/x86_64-linux-gnu/libgcc_s.so.1
``` to the Apache config

Please also list modules you are using.

---

### Post by @hJ?oS6^ on 2015-09-10
It's from a package and not in a chroot.

Server version: Apache/2.2.22 (Ubuntu)
Server built:   Jul 24 2015 17:25:42
Server's Module Magic Number: 20051115:30
Server loaded:  APR 1.4.6, APR-Util 1.3.12
Compiled using: APR 1.4.6, APR-Util 1.3.12
Architecture:   64-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT="/etc/apache2"
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="mime.types"
 -D SERVER_CONFIG_FILE="apache2.conf"

Here are the modules in use:
core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 actions_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 auth_digest_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 cloudflare_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 fcgid_module (shared)
 include_module (shared)
 jk_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 proxy_module (shared)
 reqtimeout_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 ssl_module (shared)
 status_module (shared)
 suexec_module (shared)
 unique_id_module (shared)

---

### Post by @hJ?oS6^ on 2015-10-21
I recently built a new server, this one is running Ubuntu 14.04.3 LTS. I configured it pretty much the same was as the old server that was reporting this error message and guess what? The new one is doing the same thing. Every few seconds I get "libgcc_s.so.1 must be installed for pthread_cancel to work" in the /var/log/apache2/error_log.

Server version: Apache/2.4.7 (Ubuntu)
Server built:   Sep 23 2015 15:34:04
Server's Module Magic Number: 
Server loaded:  APR 1.5.1-dev, APR-UTIL 1.5.3
Compiled using: APR 1.5.1-dev, APR-UTIL 1.5.3
Architecture:   64-bit
Server MPM:     prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=256
 -D HTTPD_ROOT="/etc/apache2"
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="mime.types"
 -D SERVER_CONFIG_FILE="apache2.conf"


Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)
 http_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 unixd_module (static)
 access_compat_module (shared)
 actions_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 auth_digest_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cloudflare_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 fcgid_module (shared)
 filter_module (shared)
 include_module (shared)
 mime_module (shared)
 mpm_prefork_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 slotmem_shm_module (shared)
 socache_shmcb_module (shared)
 ssl_module (shared)
 status_module (shared)
 suexec_module (shared)
 unique_id_module (shared)

Any help would be appreciated.

---

