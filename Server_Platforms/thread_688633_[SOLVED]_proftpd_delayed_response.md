---
title: "[SOLVED] proftpd delayed response"
date: 2008-02-05
forum: Server Platforms
---

### Post by cdenley on 2008-02-05
I'm replacing an old vsftpd server with an ubuntu proftpd server. I have it set up perfectly, except when I connect from outside our network, there is a 10 second delay before the new server gives a response. My initial thought was that this was a routing issue, but I copied the same rules the old server uses.

I checked the traffic on the client and server. The client sends a TCP packet. The server responds with a TCP packet. The client sends another TCP packet. The server receives that packet. The server waits exactly ten seconds, then sends an FTP 220 response. All packets seem to get through without delay, the server is just delayed in sending the response.

I have set the MasqueradeAddress and PassivePorts options in proftpd.conf. What can be causing this problem?

---

### Post by usererror on 2008-02-05
I have the exact same problem, would love to know if anyone else has found a solution or explanation.  I have had it for years, and just 'deal with it'.

---

### Post by cdenley on 2008-02-06
I fixed it. Just add this line to /etc/proftpd/proftpd.conf:
```

IdentLookups off

```

---

