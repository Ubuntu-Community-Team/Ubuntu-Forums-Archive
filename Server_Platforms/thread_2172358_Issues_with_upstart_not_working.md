---
title: "Issues with upstart not working"
date: 2013-09-04
forum: Server Platforms
---

### Post by AnalBeard on 2013-09-04
I've been configuring my 13.04 server install to spawn a getty on my serial port, and whilst the config is correct, upstart will not start the service. 'sudo start ttyS0' just sits there not doing anything. A strace produces the following:

```

root@sepulveda:/etc/init# strace stop ttyS0
execve("/sbin/stop", ["stop", "ttyS0"], [/* 21 vars */]) = 0
brk(0)                                  = 0x7f6c36ef4000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6c3696f000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=28777, ...}) = 0
mmap(NULL, 28777, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6c36967000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnih.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0PH\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=96280, ...}) = 0
mmap(NULL, 2191776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6c36537000
mprotect(0x7f6c3654d000, 2097152, PROT_NONE) = 0
mmap(0x7f6c3674d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f6c3674d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnih-dbus.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340,\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=38920, ...}) = 0
mmap(NULL, 2134040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6c3632d000
mprotect(0x7f6c36335000, 2097152, PROT_NONE) = 0
mmap(0x7f6c36535000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0x7f6c36535000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdbus-1.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340j\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=277456, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6c36966000
mmap(NULL, 2373312, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6c360e9000
mprotect(0x7f6c3612c000, 2093056, PROT_NONE) = 0
mmap(0x7f6c3632b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x42000) = 0x7f6c3632b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\37\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1848024, ...}) = 0
mmap(NULL, 3961912, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6c35d21000
mprotect(0x7f6c35edf000, 2093056, PROT_NONE) = 0
mmap(0x7f6c360de000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1bd000) = 0x7f6c360de000
mmap(0x7f6c360e4000, 17464, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6c360e4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20#\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31760, ...}) = 0
mmap(NULL, 2128984, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6c35b19000
mprotect(0x7f6c35b20000, 2093056, PROT_NONE) = 0
mmap(0x7f6c35d1f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f6c35d1f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20m\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=135175, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6c36965000
mmap(NULL, 2212936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6c358fc000
mprotect(0x7f6c35914000, 2093056, PROT_NONE) = 0
mmap(0x7f6c35b13000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7f6c35b13000
mmap(0x7f6c35b15000, 13384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6c35b15000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6c36964000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6c36962000
arch_prctl(ARCH_SET_FS, 0x7f6c36962740) = 0
mprotect(0x7f6c360de000, 16384, PROT_READ) = 0
mprotect(0x7f6c35b13000, 4096, PROT_READ) = 0
mprotect(0x7f6c35d1f000, 4096, PROT_READ) = 0
mprotect(0x7f6c3632b000, 4096, PROT_READ) = 0
mprotect(0x7f6c3674d000, 4096, PROT_READ) = 0
mprotect(0x7f6c36535000, 4096, PROT_READ) = 0
mprotect(0x7f6c36b9f000, 8192, PROT_READ) = 0
mprotect(0x7f6c36971000, 4096, PROT_READ) = 0
munmap(0x7f6c36967000, 28777)           = 0
set_tid_address(0x7f6c36962a10)         = 20365
set_robust_list(0x7f6c36962a20, 0x18)   = 0
futex(0x7fff0c857e4c, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, 7f6c36962740) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0x7f6c35902800, [], SA_RESTORER|SA_SIGINFO, 0x7f6c3590bbd0}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7f6c35902880, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7f6c3590bbd0}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
brk(0)                                  = 0x7f6c36ef4000
brk(0x7f6c36f15000)                     = 0x7f6c36f15000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1613376, ...}) = 0
mmap(NULL, 1613376, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6c367d8000
close(3)                                = 0
open("/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6c3696e000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7f6c3696e000, 4096)            = 0
open("/usr/share/locale/en_GB/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_GB/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/upstart.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
getuid()                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 3
connect(3, {sa_family=AF_FILE, path=@"/com/ubuntu/upstart"}, 22) = 0
fcntl(3, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(3, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
geteuid()                               = 0
getsockname(3, {sa_family=AF_FILE, NULL}, [2]) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
sendto(3, "\0", 1, MSG_NOSIGNAL, NULL, 0) = 1
sendto(3, "AUTH EXTERNAL 30\r\n", 18, MSG_NOSIGNAL, NULL, 0) = 18
poll([{fd=3, events=POLLIN}], 1, 4294967295) = 1 ([{fd=3, revents=POLLIN}])
read(3, "OK 908b1234ec862832645889cc5224c"..., 2048) = 37
poll([{fd=3, events=POLLOUT}], 1, 4294967295) = 1 ([{fd=3, revents=POLLOUT}])
sendto(3, "NEGOTIATE_UNIX_FD\r\n", 19, MSG_NOSIGNAL, NULL, 0) = 19
poll([{fd=3, events=POLLIN}], 1, 4294967295) = 1 ([{fd=3, revents=POLLIN}])
read(3, "AGREE_UNIX_FD\r\n", 2048)      = 15
poll([{fd=3, events=POLLOUT}], 1, 4294967295) = 1 ([{fd=3, revents=POLLOUT}])
sendto(3, "BEGIN\r\n", 7, MSG_NOSIGNAL, NULL, 0) = 7
poll([{fd=3, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=3, revents=POLLOUT}])
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\2\1\n\0\0\0\1\0\0\0_\0\0\0\1\1o\0\23\0\0\0/com/ubu"..., 112}, {"\5\0\0\0ttyS0\0", 10}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 122
poll([{fd=3, events=POLLIN}], 1, 25000) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1#\0\0\0\1\0\0\0\17\0\0\0\5\1u\0\1\0\0\0\10\1g\0\1o\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 67
recvmsg(3, 0x7fff0c857a30, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\2\1\4\0\0\0\2\0\0\0p\0\0\0\1\1o\0\36\0\0\0/com/ubu"..., 128}, {"\0\0\0\0", 4}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 132
poll([{fd=3, events=POLLIN}], 1, 25000) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1%\0\0\0\2\0\0\0\17\0\0\0\5\1u\0\2\0\0\0\10\1g\0\1o\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 69
recvmsg(3, 0x7fff0c8579e0, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\2\1\10\0\0\0\3\0\0\0i\0\0\0\1\1o\0\36\0\0\0/com/ubu"..., 128}, {"\0\0\0\0\1\0\0\0", 8}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 136
poll([{fd=3, events=POLLIN}], 1, 4294967295) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\4\1\1\t\0\0\0\3\0\0\0w\0\0\0\1\1o\0 \0\0\0/com/ubu"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 145
recvmsg(3, 0x7fff0c857b20, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}], 1, 4294967295^C <unfinished ...>

```

The 'Resource temporarily unavailable' message is what confuses me - this is the only thing I've found which is of any relevance so far [http://ubuntuforums.org/showthread.php?t=1695016](http://ubuntuforums.org/showthread.php?t=1695016)

Can anyone shed any light on this?

---

### Post by SeijiSensei on 2013-09-07
The last time I needed to spawn a getty, it was back in the days when this was managed by /etc/inittab.  However I notice that there are conf's in /etc/init for the six tty's.  Perhaps you can write one for ttyS0 based on /etc/init/tty1.conf.

---

