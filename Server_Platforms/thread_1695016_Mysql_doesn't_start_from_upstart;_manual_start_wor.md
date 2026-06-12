---
title: "Mysql doesn't start from upstart; manual start works fine?"
date: 2011-02-25
forum: Server Platforms
---

### Post by h.aling on 2011-02-25
I was tinkering with my mysql configuration to play nice with my 256MiB VPS I own since a few days now but somehow I managed to screw things up badly ;)

Turns out that starting mysqld directly from the CLI works fine, but the upstart/init scripts can't get mysqld running. :confused:

```
$ sudo mysqld --verbose --user=mysql
110225 12:52:33 [Note] Plugin 'FEDERATED' is disabled.
110225 12:52:33 [Note] Plugin 'InnoDB' is disabled.
110225 12:52:33 [Note] Event Scheduler: Loaded 0 events
110225 12:52:33 [Note] mysqld: ready for connections.
Version: '5.1.49-1ubuntu8.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
```

```
$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

That looks mighty fine to me! Starting mysql with the upstart scripts however does absolutely nothing... It just sits there and waits until I press ctrl-c...

```
$ sudo service mysql start
_ <- cursor
```

```
$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

```
$ ps axu|grep mysql
root     13986  0.0  0.3  16428   868 pts/1    S+   12:56   0:00 start mysql
harold   14187  0.0  0.3   7748   856 pts/0    S+   12:58   0:00 grep --color=auto mysql
```


Here's my mysql my.cnf: :cool:

```
$ cat my.cnf |grep -v ^#
[mysqld]
port            = 3306
socket		= /var/run/mysqld/mysqld.sock
skip-external-locking
key_buffer = 16K
max_allowed_packet = 1M
table_cache = 4
sort_buffer_size = 64K
read_buffer_size = 256K
read_rnd_buffer_size = 256K
net_buffer_length = 2K
thread_stack = 128K
skip-innodb

bind-address		= 127.0.0.1

[mysqldump]
quick
max_allowed_packet = 16M

[mysql]
no-auto-rehash

[isamchk]
key_buffer = 8M
sort_buffer_size = 8M

[myisamchk]
key_buffer = 8M
sort_buffer_size = 8M

[mysqlhotcopy]
interactive-timeout

!includedir /etc/mysql/conf.d/
```


**Almost forgot**: there's nothing interesting in the logs. In fact, the logs never get updated when using the upstart script...

---

### Post by elico on 2011-02-25
what about your /etc/init.d/mysqld (or mysql)
file content?

---

### Post by h.aling on 2011-02-25
> **elico said:**
> what about your /etc/init.d/mysqld (or mysql)
file content?

I didn't change anything in those scripts...

```
$ ls -la /etc/init.d/mysql* 
lrwxrwxrwx 1 root root 21 2011-02-25 12:16 /etc/init.d/mysql -> /lib/init/upstart-job
```

I guess this is the real startup script?

```
$ cat /etc/init/mysql.conf
# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up
          and local-filesystems
	  and runlevel [2345])
stop on runlevel [016]

respawn

env HOME=/etc/mysql
umask 007

# The default of 5 seconds is too low for mysql which needs to flush buffers
kill timeout 300

pre-start script
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    # Load AppArmor profile
    if aa-status --enabled 2>/dev/null; then
        apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld || true
    fi
    LC_ALL=C BLOCKSIZE= df --portability /var/lib/mysql/. | tail -n 1 | awk '{ exit ($4<4096) }'
end script

exec /usr/sbin/mysqld

post-start script
   for i in `seq 1 30` ; do
        /usr/bin/mysqladmin --defaults-file="${HOME}"/debian.cnf ping && {
            exec "${HOME}"/debian-start
            # should not reach this line
            exit 2
        }
        sleep 1
    done
    exit 1
end script
```

---

### Post by h.aling on 2011-02-25
Strace:

```
$ sudo strace service mysql start > ~/mysql_start_strace
execve("/usr/sbin/service", ["service", "mysql", "start"], [/* 14 vars */]) = 0
brk(0)                                  = 0x2399000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fbc63ae8000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=14594, ...}) = 0
mmap(NULL, 14594, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fbc63ae4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\356\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fbc63547000
mprotect(0x7fbc636c1000, 2093056, PROT_NONE) = 0
mmap(0x7fbc638c0000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7fbc638c0000
mmap(0x7fbc638c5000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fbc638c5000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fbc63ae3000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fbc63ae2000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fbc63ae1000
arch_prctl(ARCH_SET_FS, 0x7fbc63ae2700) = 0
mprotect(0x7fbc638c0000, 16384, PROT_READ) = 0
mprotect(0x618000, 4096, PROT_READ)     = 0
mprotect(0x7fbc63aea000, 4096, PROT_READ) = 0
munmap(0x7fbc63ae4000, 14594)           = 0
getpid()                                = 24259
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTORER|SA_RESTART, 0x7fbc6357ac20}, {SIG_DFL, [], 0}, 8) = 0
geteuid()                               = 0
brk(0)                                  = 0x2399000
brk(0x23ba000)                          = 0x23ba000
getppid()                               = 24258
getcwd("/var/www/sait.nl", 4096)        = 17
open("/usr/sbin/service", O_RDONLY)     = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x40f790, ~[RTMIN RT_1], SA_RESTORER, 0x7fbc6357ac20}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7fbc6357ac20}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7fbc6357ac20}, NULL, 8) = 0
read(10, "#!/bin/sh\n\n#####################"..., 8192) = 4614
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fbc63ae29d0) = 24260
close(4)                                = 0
read(3, "service\n", 128)               = 8
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 24260
--- SIGCHLD (Child exited) @ 0 (0) ---
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fbc63ae29d0) = 24261
close(4)                                = 0
read(3, "service\n", 128)               = 8
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 24261
--- SIGCHLD (Child exited) @ 0 (0) ---
chdir("/")                              = 0
stat("/etc/init/mysql.conf", {st_mode=S_IFREG|0644, st_size=1043, ...}) = 0
geteuid()                               = 0
execve("/usr/local/sbin/start", ["start", "mysql"], [/* 16 vars */]) = -1 ENOENT (No such file or directory)
execve("/usr/local/bin/start", ["start", "mysql"], [/* 16 vars */]) = -1 ENOENT (No such file or directory)
execve("/usr/sbin/start", ["start", "mysql"], [/* 16 vars */]) = -1 ENOENT (No such file or directory)
execve("/usr/bin/start", ["start", "mysql"], [/* 16 vars */]) = -1 ENOENT (No such file or directory)
execve("/sbin/start", ["start", "mysql"], [/* 16 vars */]) = 0
brk(0)                                  = 0x7f696f61a000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6ca000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=14594, ...}) = 0
mmap(NULL, 14594, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f696e6c6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnih.so.1", O_RDONLY)      = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0PZ\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=92144, ...}) = 0
mmap(NULL, 2187640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f696e295000
mprotect(0x7f696e2aa000, 2097152, PROT_NONE) = 0
mmap(0x7f696e4aa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15000) = 0x7f696e4aa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnih-dbus.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200,\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=34792, ...}) = 0
mmap(NULL, 2129960, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f696e08c000
mprotect(0x7f696e094000, 2093056, PROT_NONE) = 0
mmap(0x7f696e293000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7f696e293000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libdbus-1.so.3", O_RDONLY)   = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20g\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=269104, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6c5000
mmap(NULL, 2365056, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f696de4a000
mprotect(0x7f696de8a000, 2097152, PROT_NONE) = 0
mmap(0x7f696e08a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x40000) = 0x7f696e08a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\356\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f696dac7000
mprotect(0x7f696dc41000, 2093056, PROT_NONE) = 0
mmap(0x7f696de40000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7f696de40000
mmap(0x7f696de45000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f696de45000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/librt.so.1", O_RDONLY)       = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31744, ...}) = 0
mmap(NULL, 2128848, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f696d8bf000
mprotect(0x7f696d8c6000, 2093056, PROT_NONE) = 0
mmap(0x7f696dac5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f696dac5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libpthread.so.0", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\\\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=136067, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6c4000
mmap(NULL, 2212768, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f696d6a2000
mprotect(0x7f696d6ba000, 2093056, PROT_NONE) = 0
mmap(0x7f696d8b9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7f696d8b9000
mmap(0x7f696d8bb000, 13216, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f696d8bb000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6c3000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6c2000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6c1000
arch_prctl(ARCH_SET_FS, 0x7f696e6c2700) = 0
mprotect(0x7f696d8b9000, 4096, PROT_READ) = 0
mprotect(0x7f696dac5000, 4096, PROT_READ) = 0
mprotect(0x7f696de40000, 16384, PROT_READ) = 0
mprotect(0x7f696e08a000, 4096, PROT_READ) = 0
mprotect(0x7f696e293000, 4096, PROT_READ) = 0
mprotect(0x7f696e4aa000, 4096, PROT_READ) = 0
mprotect(0x7f696e8e9000, 4096, PROT_READ) = 0
mprotect(0x7f696e6cc000, 4096, PROT_READ) = 0
munmap(0x7f696e6c6000, 14594)           = 0
set_tid_address(0x7f696e6c29d0)         = 24259
set_robust_list(0x7f696e6c29e0, 0x18)   = 0
futex(0x7fff2342b6bc, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x7fff2342b6bc, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, 7f696e6c2700) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0x7f696d6a7b20, [], SA_RESTORER|SA_SIGINFO, 0x7f696d6b1b40}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7f696d6a7bb0, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7f696d6b1b40}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
brk(0)                                  = 0x7f696f61a000
brk(0x7f696f63b000)                     = 0x7f696f63b000
open("/usr/lib/locale/locale-archive", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1534640, ...}) = 0
mmap(NULL, 1534640, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f696e54a000
close(3)                                = 0
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f696e6c9000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7f696e6c9000, 4096)            = 0
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
getuid()                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 3
connect(3, {sa_family=AF_FILE, path=@"/com/ubuntu/upstart"}, 22) = 0
fcntl(3, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(3, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
geteuid()                               = 0
getsockname(3, {sa_family=AF_FILE, NULL}, [2]) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
write(3, "\0", 1)                       = 1
sendto(3, "AUTH EXTERNAL 30\r\n", 18, MSG_NOSIGNAL, NULL, 0) = 18
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "OK 148cceca3d0f76456899b26800000"..., 2048) = 37
poll([{fd=3, events=POLLOUT}], 1, -1)   = 1 ([{fd=3, revents=POLLOUT}])
sendto(3, "NEGOTIATE_UNIX_FD\r\n", 19, MSG_NOSIGNAL, NULL, 0) = 19
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "AGREE_UNIX_FD\r\n", 2048)      = 15
poll([{fd=3, events=POLLOUT}], 1, -1)   = 1 ([{fd=3, revents=POLLOUT}])
sendto(3, "BEGIN\r\n", 7, MSG_NOSIGNAL, NULL, 0) = 7
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\2\1\n\0\0\0\1\0\0\0_\0\0\0\1\1o\0\23\0\0\0/com/ubu"..., 112}, {"\5\0\0\0mysql\0", 10}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 122
clock_gettime(CLOCK_MONOTONIC, {18935, 899195721}) = 0
poll([{fd=3, events=POLLIN}], 1, 25000) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1#\0\0\0\1\0\0\0\17\0\0\0\5\1u\0\1\0\0\0\10\1g\0\1o\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 67
recvmsg(3, 0x7fff2342b150, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\2\1\10\0\0\0\2\0\0\0i\0\0\0\1\1o\0\36\0\0\0/com/ubu"..., 128}, {"\0\0\0\0\1\0\0\0", 8}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 136
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\4\1\1%\0\0\0\2\0\0\0o\0\0\0\1\1o\0\36\0\0\0/com/ubu"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 165
recvmsg(3, 0x7fff2342b260, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {18935, 901256205}) = 0
poll([{fd=3, events=POLLIN}], 1, -1287389453
```

And then it just stops...

---

### Post by dreamjockey on 2011-06-02
Was converting db from latin1 to support utf8 and hence was playing with /etc/mysql/my.cnf when I got stuck.
I am using instructions from the following link to do the same:
[http://aptoma.com/select.star/2008/12/19/mother-of-all-utf-8-checklists/](http://aptoma.com/select.star/2008/12/19/mother-of-all-utf-8-checklists/)

From the stack trace -
> open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)

Lines after these just keep reappearing.
My inference - It looks like upstart wants a utf8 translation to start a service which has been configured to use utf8 charset, and hence it looks like an upstart issue.
Your observation of starting it via mysqld instead of scripts helped me progress... so Thanks! :)

---

