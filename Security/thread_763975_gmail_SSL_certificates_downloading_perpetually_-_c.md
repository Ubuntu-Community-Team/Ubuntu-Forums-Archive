---
title: "gmail SSL certificates downloading perpetually - compromise?"
date: 2008-04-23
forum: Security
---

### Post by pytheas22 on 2008-04-23
My ISP gave me a report last week that one of my servers, running Ubuntu 6.06, suddenly had an exponential increase in Internet traffic (<300 bytes a day outbound to >10000 MB).  There's nothing to explain this sudden increase in traffic.

I used Wireshark to look at the traffic going beyond  the machine's subnet, and it turns out that all of it (at least during the hour or so that I observed) is going to a machine with hostname wx-in-f111.google.com, which as far as I can tell is a mail server for gmail.

My server occasionally receives mail from gmail, so it makes sense that it would be connecting to Google's server.  When I looked more closely at the traffic, however, it all appeared to be SSL certificates, as if my server and Google's server are exchanging handshakes constantly.  This doesn't make sense to me.

I want to know whether this represents a system compromise or something less serious.  I found no signs of a compromise--rkhunter and chkrootkit gave no indication of a rootkit present, and the machine is not sniffing or port scanning its neighbors--but I am still at a loss to explain the sudden traffic increase.  Is there anything else I should be checking for?  Or can anyone suggest a legitimate reason that these SSL handshakes would be going on continuously?

Thanks in advance for any help.

By the way, the server's function is to run a IT support-ticketing system.  It receives support requests via email (hence its connection to gmail).  Beyond that, it's not supposed to be doing anything else.

---

### Post by pytheas22 on 2008-04-23
Nevermind; after some more thinking, I tracked the problem down to issues with the local SSL certificate, which I've resolved.  Things appear to work alright now.  I don't know why these SSL problems came up all of a sudden; maybe something changed on Google's end that broke it.

---

### Post by hggdh on 2008-04-28
Just a comment: every new HTTPS session will cause *at* *least* the server to send out its certificate chain (i.e., the server certificate and all root certificates on the path to the top-most root). This is part of the protocol, SSL or TLS. If on client-server authentication, both sides will forward their certificate chain.

---

