---
title: "Problems connecting to UnrealIRCd"
date: 2012-07-16
forum: Server Platforms
---

### Post by starriol on 2012-07-16
Hi guys I'm having the following issue using Unreal 3.2.8.1 when trying to connect from the server itself:


13:34 -!- Irssi: Looking up 127.0.0.1
13:34 -!- Irssi: Connecting to 127.0.0.1 [127.0.0.1] port 6668
13:34 -!- Irssi: Connection to 127.0.0.1 established
13:34 -!- Irssi: Connection lost to 127.0.0.1

IRCD seems to be running:

:~# lsof -i
COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME
ircd 11831 root 1u IPv4 1256154 0t0 TCP *:6668 (LISTEN)

See the output for ps x:
11831 ? S 0:15 /home/ircd/Unreal3.2/src/ircd

BTW, I don't see anything written at the ircd.log nor service.log

This is the listen line at the .cfg file:
listen *:6668; // IRC Port; choose desired port (1 - 65000)

When trying to login using telnet, I see the following:

root@suprapowaz:/home/ircd/Unreal3.2# telnet localhost 6668
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
NICK Paul
USER ircd 8 * : Paul Mutton
Connection closed by foreign host.
root@suprapowaz:/home/ircd/Unreal3.2# telnet localhost 6668
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
sdfwe45645th
:Server.name 451 sdfwe45645th :You have not registered

Is that last error important?

Any help would be appreciated, first time setting up an IRC server.

---

