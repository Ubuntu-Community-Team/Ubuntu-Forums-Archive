---
title: "Kerberos testing"
date: 2010-11-03
forum: Server Platforms
---

### Post by Hate on 2010-11-03
Hi all,
I hope this is the correct section.
I'm working on a project about kerberos and I have to make some test with wireshark to compare different implementations of the protocol.
I'm total new to kerberos and even if I've read some papers about it I'm not very confident about what I've to do practically.
I've managed easily to install MIT client and server implementation on my machine (I'm using the same physical machine and capturing packets from loopback interface with wireshark ) and I've done a initial capture about the request of a ticket-granting ticket using the command

```
kinit <principalname>
```

Now I would have to capture packets going to ticket granting server (the ticket to get access to the service) and finally the exchange with the application server.
I've seen that in the packets I've installed there are some available commands about ftp, rlogin and rsh with kerberos but I'm a bit confused about what I would have to do now.
Anybody with some kerberos experience could give me some suggestion about how to proceed ?
Thanks in advance

---

