---
title: "xen domU produces error doing md5sum"
date: 2008-02-21
forum: Virtualisation
---

### Post by sudoyang on 2008-02-21
I'm noticing a strange problem when running certain commands in the Xen domU.  Example:

# rpm -qpi *.rpm >/dev/null
error: IBM_db2cbsr81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(748f248a348f8d230194feded0eb4f22) != (e4c5365a4a9cc0c97596449e2e4c2102)
error: IBM_db2detw81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(9bb5a77c1efa9bb1112ad1f2403aaeab) != (250bd72fe3228b75f9313a00c2b6be2b)
error: IBM_db2dwcm81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(325368ed3e1c0e551e6f746dd71020f9) != (35817714c023cf5f6a7662027a349abe)
error: IBM_db2hsys81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(1e6c3402d15d86fc6293f6b1d7f59681) != (f9ba5105b633787c44bc8e6e4b940e71)
error: IBM_db2msBG81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(c8b3fd2b849ca4119b23c03ad6437b82) != (d6a9ffe83999cccad45bd0af85096e6d)
error: IBM_db2msCN81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(54e035e416e9ddd3baff6af2d3102462) != (efdde2067fbd87c871359184f4253f64)
error: IBM_db2msES81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(a02c4d3405b407afcfc031384a4e39a4) != (b67885e6e677f20a45bad04af475ffce)
error: IBM_db2msHU81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(5c787c346c7bb7ebcc8946c5ddde6b46) != (8fe52a1f39f9db430f53fe973d616e52)
error: IBM_db2msru81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(a173e5e6dd6fe0d32cc205609b526bda) != (1f8208c7ff7b883db046f74c548c6f5e)
error: IBM_db2repl81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(b1d566c4106d8ac5c454780e360270c9) != (fe5c7f6cec2691f8d82f9e55e9db93f7)
error: IBM_db2rte81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(8d572acc837b71c74cbd8161c8916b17) != (0f0d8388f16a1f2a1bb5a6dff42f1685)
error: IBM_db2sesv81-8.1.2-144.i386.rpm: MD5 digest: BAD Expected(24fbcf556ffab931aa302a5313234884) != (0e26d7d4a34937c88388020954382613

The same command on the same set of files produces NO error when runnning on the dom0 (mgt host) or on a standalone server.  Is this a problem with Xen.

My dom0 is running Ubuntu 7.10 (Gutsy) 32-bit and the domUs are CentOS 4.6 32-bit.

This is strange.  Any idea what could be wrong?

---

