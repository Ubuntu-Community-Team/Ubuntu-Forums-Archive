---
title: "php5-fpm processes receiving SIGKILL"
date: 2013-09-17
forum: Server Platforms
---

### Post by aschlosberg on 2013-09-17
Distribution: 12.0.4.3
PHP5-FPM: 5.5.3+dfsg-1+debphp.org~precise+2 (from debphp.org - [https://launchpad.net/~ondrej/+archive/php5](https://launchpad.net/~ondrej/+archive/php5))
nginx: 1.4.2 (compiled from source)

As of yesterday I started noticing that all of my PHP child processes were being killed and there were messages such as the following in the logs:
```
[17-Sep-2013 16:01:01] WARNING: [pool cp] child 9787 exited on signal 9 (SIGKILL) after 14.205774 seconds from start
```

All I could find on a Google search was someone experiencing something similar after moving to PHP 5.3, hence my upgrade to 5.5 but it is still occurring (although not being logged any more).

Watching processes with strace results in (I have no idea how to debug this!):

```
access("/var/www/path/to/file.php", F_OK) = 0stat("/var/www/path/to/file.php", {st_mode=S_IFREG|0744, st_size=1601, ...}) = 0
chdir("/")                              = 0
clock_gettime(CLOCK_MONOTONIC, {56519, 672954391}) = 0
times({tms_utime=6, tms_stime=5, tms_cutime=0, tms_cstime=0}) = 1723716611
fcntl(4, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
rt_sigaction(SIGPIPE, {SIG_IGN, [PIPE], SA_RESTORER|SA_RESTART, 0x7f27c41384a0}, {SIG_IGN, [PIPE], SA_RESTORER|SA_RESTART, 0x7f27c41384a0}, 8) = 0
write(6, "\1\0\0\0\1", 5)               = 5
shutdown(6, 2 /* send and receive */)   = 0
close(6)                                = 0
rt_sigaction(SIGPIPE, {SIG_IGN, [PIPE], SA_RESTORER|SA_RESTART, 0x7f27c41384a0}, {SIG_IGN, [PIPE], SA_RESTORER|SA_RESTART, 0x7f27c41384a0}, 8) = 0
setitimer(ITIMER_PROF, {it_interval={0, 0}, it_value={30, 0}}, NULL) = 0
write(5, "\1\7\0\1\0H\0\0Passing INI directive th"..., 368) = 368
shutdown(5, 1 /* send */)               = 0
recvfrom(5, "\1\5\0\1\0\0\0\0", 8, 0, NULL, NULL) = 8
recvfrom(5, "", 8, 0, NULL, NULL)       = 0
close(5)                                = 0
clock_gettime(CLOCK_MONOTONIC, {56519, 676442183}) = 0
setitimer(ITIMER_PROF, {it_interval={0, 0}, it_value={0, 0}}, NULL) = 0
clock_gettime(CLOCK_MONOTONIC, {56519, 676788798}) = 0
accept(0,  <unfinished ...>
+++ killed by SIGKILL +++

```

Occasionally it is only the following, after waiting to accept for a while.

```

accept(0,  <unfinished ...>
+++ killed by SIGKILL +++

```

PHP5-FPM pool configuration:

```

[cp]
listen = 127.0.0.1:41005
listen.backlog = -1
listen.allowed_clients = 127.0.0.1
user = cp
group = cp
catch_workers_output = yes
slowlog = /var/log/php5-fpm/slowlog-cp.log


pm = dynamic
pm.max_children = 8
pm.start_servers = 2
pm.min_spare_servers = 2
pm.max_spare_servers = 3
pm.max_requests = 50 #this should send a SIGCHLD not a SIGKILL and will give an error log of "exit with status 0"


php_admin_flag[display_errors] = off
php_admin_value[error_log] = /var/log/php5-fpm/cp.log
php_admin_flag[log_errors] = on
php_admin_flag[expose_php] = off
php_admin_value[disable_functions] = socket_create,socket_create_listen,socket_create_pair


php_admin_flag[apc.cache_by_default] = true;

```

Any advice as how to troubleshoot would be greatly appreciated!

---

### Post by user7460 on 2014-01-01
Did you find a solution to this problem?

---

