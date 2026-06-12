---
title: "PHP fsockopen slow in chroot environment"
date: 2011-07-28
forum: Server Platforms
---

### Post by ShishKabab on 2011-07-28
Hello everyone,

I'm having a very strange problem. I have a service running on local port 2025 on my server. I run PHP in a chroot. When I connect from PHP in the chroot to the service (or any other local port), it takes five seconds for fsockopen to return. When I do it from PHP outside the chroot, fsockopen returns quickly. But the stangest part is that when I attach with strace to the PHP process running in the chroot, the fsockopen call returns quickly again (the same applies to running strace /usr/sbin/chroot /usr/bin/php5 .. etc .. ). Does anyone know what causes this?

Here are my tests:

```
root@vps7553:~# time /usr/bin/php5 -r 'printf("\n%s\n", microtime()); $fp = fsockopen("localhost", 2025); printf("\n%s\n", microtime()); fclose($fp); printf("\n%s\n", microtime());'

0.22701300 1311843305

0.22801400 1311843305

0.22828500 1311843305

real    0m0.097s # Running PHP outside the chroot is fast
user    0m0.020s
sys     0m0.032s

root@vps7553:~# time chroot /webroot/ /usr/bin/php5 -r 'printf("\n%s\n", microtime()); $fp = fsockopen("localhost", 2025); printf("\n%s\n", microtime()); fclose($fp); printf("\n%s\n", microtime());'

0.08645200 1311843336

0.09519800 1311843341

0.09529200 1311843341

real    0m10.093s # Running PHP inside the chroot is slow
user    0m0.032s
sys     0m0.024s

root@vps7553:~# time strace /usr/sbin/chroot /webroot/ /usr/bin/php5 -r 'printf("\n%s\n", microtime()); $fp = fsockopen("localhost", 2025); printf("\n%s\n", microtime()); fclose($fp); printf("\n%s\n", microtime());' 2> /tmp/strace.txt

0.05391500 1311843370

0.05915000 1311843370

0.06011600 1311843370

real    0m0.183s # But running PHP the chroot with strace is fast?
user    0m0.064s
sys     0m0.120s

```

---

