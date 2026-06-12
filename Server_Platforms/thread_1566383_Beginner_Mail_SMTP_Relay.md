---
title: "Beginner: Mail SMTP Relay"
date: 2010-09-02
forum: Server Platforms
---

### Post by pazza98 on 2010-09-02
I'm running ASSP on Ubuntu 10.04.1 it's mostly working fine. I have one problem which has been bugging me for some time. I don't want to filter outbound mail, but if I can relay (proxy) my outbound mail through ASSP, then it can automatically add to the whitelist.

As ASSP is a proxy, I need a server to send it to once ASSP receives it. I've tried my ISP, but this failed and they weren't willing to confirm if a connection attempt was received at their end, which gives me trouble locating the problem.

Current setup

Inbound

mx -> router -> ASSP -> Exchange 2003

Outbound

Exchange 2003 -> mx

I'd like to setup outbound as either

Exchange 2003 -> ASSP -> <ISP> SMTP relay
Exchange 2003 -> ASSP -> <relay running on Ubuntu eg postfix>

Can anyone help me with troubleshooting steps or a better suggestion for how I can set this up. I'd love to know why my ISP setup didn't work, but I don't know a tool for monitoring IP traffic in Ubuntu SE, in windows I use Wireshark is there any equivalent I can setup for Ubuntu or a tool I can use in windows which will show all traffic, Ubuntu and windows server are on the same netgear switch, not sure it's smart enough to copy all traffic to another port for monitoring.

---

### Post by pazza98 on 2010-09-02
I've tried some more testing. Telnet from the same computer comes back with

451 4.7.1 Local configuration error, please try again later

There is a delay / grey listing setting in ASSP, so I tried putting my own IP, localhost, 127. etc in the exceptions and restarted ASSP, then restarted ASSP, still the same message.

Tried disabling the delay feature and restarted, still getting the same error, not sure if the error is local eg. from ASSP or if it's from my ISP. Can anyone guide me in the right direction?

---

### Post by pazza98 on 2010-09-02
OK. I realise I missed this out earlier, but seems to rule out one option. I've just telnet to port 25 on the ISP relay without any problem, so this seems to make it a problem with ASSP.

---

### Post by pazza98 on 2010-09-02
Tried to connect to ASSP machine from my laptop running Ubuntu

```
will@ubuntu:~$ telnet 192.168.1.20 25
Trying 192.168.1.20...
Connected to 192.168.1.20.
Escape character is '^]'.
554 <webmail.parry-net.co.uk> Relay Service denied for IP 192.168.1.10, closing transmission channel
Connection closed by foreign host.

```

I realised that I haven't allowed relaying for this, so added exception and tried again.

```
will@ubuntu:~$ telnet 192.168.1.20 25
Trying 192.168.1.20...
Connected to 192.168.1.20.
Escape character is '^]'.
451 4.7.1 Local configuration error, please try again later
Connection closed by foreign host.

```

As I said before I think I've disabled the delay, and then restarted, I don't know why I'm still getting delayed with 451 error.

---

### Post by pazza98 on 2010-09-02
```
02-Sep-10 17:14:20 *** post.demon.co.uk didn't work, trying others...;
02-Sep-10 17:14:20 Couldn't create server socket to post.demon.co.uk -- aborting connection;
```

This was from the ASSP logs. I'm not sure what bit of code might produce this error, before it was presumably reproduced by the ASSP perl script.

---

