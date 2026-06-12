---
title: "The responding of my ubuntu server 7.10 is contingently slow"
date: 2008-02-15
forum: Server Platforms
---

### Post by realker on 2008-02-15
I only installed apache on my ubuntu server 7.10 server, and it is turning quite lagging at the time when client visit it.

I run wget on the local server for testing result.

```

root@web04:/etc# wget http://127.0.0.1/g
--23:35:02--  http://127.0.0.1/g
           => `g'
Connecting to 127.0.0.1:80... ((((HERE,IT USUALLY NEEDS 3 OR 4 SECONDS TO PROCESS TO THE NEXT STEP, WHY?!))))
connected.
HTTP request sent, awaiting response... 404 Not Found
230215 ERROR 404 Not Found.

```

I have other 2 servers running ubuntu 7.04, which are running perfectly. These 2 servers has no problems like the one running 7.10.

When the lagging problem shows, the following is the status of the server which is running ubuntu 7.10:

CPU:  98% Idle

Load average:0.21,0.32,0.24

Memory: Working good


TCP connection status:

FIN_WAIT2 176
CLOSING 1
SYN_RECV 171
CLOSE_WAIT 11
TIME_WAIT 3271
ESTABLISHED 1020
LAST_ACK 29
FIN_WAIT1 19
 
But this problem is not showing every time when visit the apache server, but intermittently appears.

Please help me to find out what problem it is, and how can I solve it?

(of course, I’ve tried to use wget on other computers to test the server which has the problem I’ve told. The result is the same.)

I am a ubuntu fan from P.R.China, and I really apprieciate your work.

Looking forward your reply, and thank you very much for your help in advance.


PS: I didn’t change any unusual settings of the system on the server.

---

### Post by crouton on 2008-02-15
Can you check your logs to see if any other activity is going on when the 'slowdown' occurs?  'dmesg | less' will show the current system log and  'tail -f /var/log/messages' will give a running account of the latest entries.

---

### Post by realker on 2008-02-15
my  /var/log/messages  :


Feb 16 00:16:05 web03 kernel: [4327609.407404] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:17:17 web03 kernel: [4327681.075428] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:18:24 web03 kernel: [4327748.374758] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:19:26 web03 kernel: [4327810.121427] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:23:57 web03 kernel: [4328080.667134] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:25:08 web03 kernel: [4328151.198032] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:27:56 web03 kernel: [4328319.206734] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:28:56 web03 kernel: [4328379.099059] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:29:57 web03 kernel: [4328439.561867] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:34:36 web03 kernel: [4328718.189713] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:36:15 web03 kernel: [4328817.782086] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:39:11 web03 kernel: [4328992.500568] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:40:14 web03 kernel: [4329056.310801] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:41:22 web03 kernel: [4329123.855434] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:43:12 web03 kernel: [4329233.209451] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:49:29 web03 kernel: [4329609.733795] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:50:29 web03 kernel: [4329669.623516] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:51:56 web03 kernel: [4329756.861889] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:52:57 web03 kernel: [4329817.141223] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:54:19 web03 kernel: [4329899.102680] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:55:20 web03 kernel: [4329960.422618] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:57:41 web03 kernel: [4330101.200281] possible SYN flooding on port 80. Sending cookies.


what is this?

---

### Post by faulkes on 2008-02-15
> **realker said:**
> my  /var/log/messages  :


Feb 16 00:16:05 web03 kernel: [4327609.407404] possible SYN flooding on port 80. Sending cookies.
Feb 16 00:17:17 web03 kernel: [4327681.075428] possible SYN flooding on port 80. Sending cookies.

what is this?

A SynFlood is an old attack against services to deny access to them.  The kernel has built=in protections against it (and has for a long time).  However, given the contiunuos stream of those log messages, I would hazard a guess that someone or something is attacking your server.

Faulkes

---

### Post by crouton on 2008-02-15
You may want to consider changing the port and/or interface your HTTP server listens on.  If this is just for internal testing, you can tell Apache to only respond to requests from the LAN; if you still need it externally available, you can change the port to 8080 or some other number greater than 1024.

---

### Post by realker on 2008-02-16
I think i may be attacked by someone or somecomputer, because the other 2 servers which are running ubuntu 7.04 have the same log
"Feb 16 00:16:05 web03 kernel: [4327609.407404] possible SYN flooding on port 80. Sending cookies."

But I am not sure what kind of consequences maybe occur due to the log record, and how can i solve the problem?

About the lagging problem, i've tried to change the port to 8089 and so on to test, but the problem remain the same.
But if I retrict it as LAN access only, there will be no lagging anymore.

---

### Post by faulkes on 2008-02-16
The best option, is to find out which IP Address is sending the SynFlood and then either block it at your router (depending on what router you have and if it supports it) or to do so in iptables.

Faulkes

---

