---
title: "Stunnel4 exits itself aprox. 1 time a day"
date: 2008-09-15
forum: Server Platforms
---

### Post by greenyblue on 2008-09-15
Hi guys.

I'm new here and I have been running a server for the last two months which has been a great way of learning linux; without instant gratification, that's for sure hehe.

Well, my problem is that stunnel4 recieves the term signal 15 about one time per day, often at night when there are very little activity through stunnel.

I use stunnel like this:  user-irc-client > stunnel > stunnel connects to local ircd-server.

Here is the last lines in the log just after the incident:

```

2008.08.31 03:21:27 LOG7[30744:3082279824]: irc finished (3 left)
2008.08.31 03:21:42 LOG7[30744:3082627984]: SSL alert (read): warning: close notify
2008.08.31 03:21:42 LOG7[30744:3082627984]: SSL closed on SSL_read
2008.08.31 03:21:42 LOG7[30744:3082627984]: Socket write shutdown
2008.08.31 03:21:42 LOG7[30744:3082627984]: Socket closed on read
2008.08.31 03:21:42 LOG7[30744:3082627984]: SSL write shutdown
2008.08.31 03:21:42 LOG7[30744:3082627984]: SSL alert (write): warning: close notify
2008.08.31 03:21:42 LOG6[30744:3082627984]: SSL_shutdown successfully sent close_notify
2008.08.31 03:21:42 LOG5[30744:3082627984]: Connection closed: 77756 bytes sent to SSL, 14057 bytes sent to socket
2008.08.31 03:21:42 LOG7[30744:3082627984]: irc finished (2 left)
2008.08.31 03:24:30 LOG7[30744:3082558352]: SSL alert (read): warning: close notify
2008.08.31 03:24:30 LOG7[30744:3082558352]: SSL closed on SSL_read
2008.08.31 03:24:30 LOG7[30744:3082558352]: Socket write shutdown
2008.08.31 03:24:30 LOG7[30744:3082558352]: SSL write shutdown
2008.08.31 03:24:30 LOG7[30744:3082558352]: SSL alert (write): warning: close notify
2008.08.31 03:24:30 LOG6[30744:3082558352]: SSL_shutdown successfully sent close_notify
2008.08.31 03:24:30 LOG5[30744:3082558352]: Connection closed: 29434 bytes sent to SSL, 1747 bytes sent to socket
2008.08.31 03:24:30 LOG7[30744:3082558352]: irc finished (1 left)
2008.08.31 06:36:56 LOG5[30744:3082754816]: Received signal 15; terminating
2008.08.31 06:36:56 LOG7[30744:3082754816]: removing pid file /stunnel4.pid

```

As you see it recieves signal 15 which terminates the process.

My config is practically the standard config except for adding:
[irc]
accept = 6667
connect = 6697

Also, I created my own certificate which has been proving to work just fine.


I would greatly appreciate if anyone could help me with this problem.

Thanks in advance

---

