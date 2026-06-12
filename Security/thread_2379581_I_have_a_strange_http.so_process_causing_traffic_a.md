---
title: "I have a strange http.so process causing traffic and I don't know what it is"
date: 2017-12-07
forum: Security
---

### Post by inte2 on 2017-12-07
With no browser, email- or im client running I noticed I still had some low traffic on my network interface.
Iftop revealed that this traffic is originating to a telekom dialin address which is not mine.
lsof grep shows a http.so process which is causing this traffic.
pstree returns nothing conclusive:
```

stree 24743
http.so&#9472;&#9516;&#9472;{QDBusConnection}
        &#9492;&#9472;{Thread (pooled)}

```

nor does ps
```

ps 24743
  PID TTY      STAT   TIME COMMAND
24743 ?        Sl     1:23 http.so [kdeinit5] https local:/run/user/1000/klauncherTJ2050.1.slave-socket local:/run/user/1000/plasmashellbj2111.1474.slave-socket

```
This process appears to be somehow related to KDE and started by user, but what does it do?

Thank you.

---

### Post by vasa1 on 2017-12-07
I don't know if this helps but:
[https://askubuntu.com/questions/964590/what-is-the-process-http-so](https://askubuntu.com/questions/964590/what-is-the-process-http-so)
[https://bugs.kde.org/show_bug.cgi?id=355669](https://bugs.kde.org/show_bug.cgi?id=355669)

---

### Post by inte2 on 2017-12-12
Mh, thank you for the replies. This process doesnt appear to be releated to akonadi, since it is still there when akonadi was stopped (akonadictl stop). What is it?

---

### Post by inte2 on 2017-12-18
Here is some further analysis:
```
[I]poll([{fd=7, events=POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = 0
getsockname(7, {sa_family=AF_INET, sin_port=htons(34962), sin_addr=inet_addr("192.168.2.106")}, [16]) = 0
getpeername(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, [16]) = 0
getsockopt(7, SOL_SOCKET, SO_TYPE, [1], [4]) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
gettimeofday({1513594012, 631245}, NULL) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 12977278}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 13029102}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 13059204}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 13086233}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 13114100}) = 0
poll([{fd=7, events=POLLIN|POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
write(7, "\26\3\1\0\305\1\0\0\301\3\1\312\214k\370\0244k\377\352\206\324]\351\200I8\f\345\335\366\266"..., 202) = 202
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 13311616}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 13338715}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 13366233}) = 0
poll([{fd=7, events=POLLIN}], 1, 20000) = 1 ([{fd=7, revents=POLLIN}])
ioctl(7, FIONREAD, [7])                 = 0
read(7, "\25\3\1\0\2\2F", 7)            = 7
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
close(7)                                = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 41153459}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 41234197}) = 0
socket(PF_INET, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 7
setsockopt(7, SOL_SOCKET, SO_OOBINLINE, [1], 4) = 0
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = -1 EINPROGRESS (Operation now in progress)
clock_gettime(CLOCK_MONOTONIC, {68990, 41458044}) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 41524464}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 41552122}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 41579081}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 41606739}) = 0
poll([{fd=7, events=POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = 0
getsockname(7, {sa_family=AF_INET, sin_port=htons(34964), sin_addr=inet_addr("192.168.2.106")}, [16]) = 0
getpeername(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, [16]) = 0
getsockopt(7, SOL_SOCKET, SO_TYPE, [1], [4]) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
gettimeofday({1513594012, 689989}, NULL) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 70996092}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 71034156}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 71065725}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 71096875}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 71128025}) = 0
poll([{fd=7, events=POLLIN|POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
write(7, "\26\3\1\0\305\1\0\0\301\3\1\352\370\226\177\34\10'\\H\265\336\255\370\260\242*G\10c\237\251"..., 202) = 202
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 71369681}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 71405930}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 71436172}) = 0
poll([{fd=7, events=POLLIN}], 1, 20000) = 1 ([{fd=7, revents=POLLIN}])
ioctl(7, FIONREAD, [7])                 = 0
read(7, "\25\3\1\0\2\2F", 7)            = 7
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
close(7)                                = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 98776472}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 98846874}) = 0
socket(PF_INET, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 7
setsockopt(7, SOL_SOCKET, SO_OOBINLINE, [1], 4) = 0
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = -1 EINPROGRESS (Operation now in progress)
clock_gettime(CLOCK_MONOTONIC, {68990, 99050326}) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 99111020}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 99135954}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 99161027}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 99186241}) = 0
poll([{fd=7, events=POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = 0
getsockname(7, {sa_family=AF_INET, sin_port=htons(34966), sin_addr=inet_addr("192.168.2.106")}, [16]) = 0
getpeername(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, [16]) = 0
getsockopt(7, SOL_SOCKET, SO_TYPE, [1], [4]) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
gettimeofday({1513594012, 746689}, NULL) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 128339524}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 128369696}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 128395119}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 128419703}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 128444917}) = 0
poll([{fd=7, events=POLLIN|POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
write(7, "\26\3\1\0\305\1\0\0\301\3\1$\t\356Hc\266\341\216\366P.\205\347\320\244\322\356//\313\353"..., 202) = 202
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 128611911}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 128637334}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 129155988}) = 0
poll([{fd=7, events=POLLIN}], 1, 20000) = 1 ([{fd=7, revents=POLLIN}])
ioctl(7, FIONREAD, [7])                 = 0
read(7, "\25\3\1\0\2\2F", 7)            = 7
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
close(7)                                = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 155798138}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 155878876}) = 0
socket(PF_INET, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 7
setsockopt(7, SOL_SOCKET, SO_OOBINLINE, [1], 4) = 0
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = -1 EINPROGRESS (Operation now in progress)
clock_gettime(CLOCK_MONOTONIC, {68990, 156164464}) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 156235494}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 156265387}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 156294442}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 156323706}) = 0
poll([{fd=7, events=POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
connect(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, 16) = 0
getsockname(7, {sa_family=AF_INET, sin_port=htons(34968), sin_addr=inet_addr("192.168.2.106")}, [16]) = 0
getpeername(7, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("151.101.64.67")}, [16]) = 0
getsockopt(7, SOL_SOCKET, SO_TYPE, [1], [4]) = 0
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
gettimeofday({1513594012, 803581}, NULL) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 184694818}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 184971536}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 185002267}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 185031251}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 185058839}) = 0
poll([{fd=7, events=POLLIN|POLLOUT}], 1, 20000) = 1 ([{fd=7, revents=POLLOUT}])
write(7, "\26\3\1\0\305\1\0\0\301\3\1\311!\3601\307\206\3\201\251\24`\234\345\276\354I\372\35\203\252u"..., 202) = 202
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
clock_gettime(CLOCK_MONOTONIC, {68990, 185241688}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 185267740}) = 0
clock_gettime(CLOCK_MONOTONIC, {68990, 185297144}) = 0[/I]
```

---

### Post by Habitual on 2017-12-18
```
lsof -i :<pid_of_interrest>
```I think it is.
User started or created a KDE plasmoid, it look like from here.

There is a Desktop, yes?

---

