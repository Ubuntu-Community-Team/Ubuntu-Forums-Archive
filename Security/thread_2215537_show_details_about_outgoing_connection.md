---
title: "show details about outgoing connection"
date: 2014-04-07
forum: Security
---

### Post by MikeCyber on 2014-04-07
Hi
a app connects to a remote server to get a file. Now how to see exactly which file it's accessing via http?
Many thanks

---

### Post by TheFu on 2014-04-07
There must be 100 different ways depending on where the app sits, who has control over the network, who has control over the server. Lacking any data on that - wireshark running on the same machine is one solution.

---

### Post by SeijiSensei on 2014-04-07
If you have access to the server, then just use the server's access log.

Otherwise you'd probably have to install something like Squid somewhere along the path to log all outbound HTTP requests.  Then you can see the URL requested.

---

### Post by MikeCyber on 2014-04-07
Thanks, wireshark found that remote file. Now another question: Would it be possible to fake that request? Get that file locally and tell the app to use that instead?

---

### Post by sandyd on 2014-04-07
Thread being reviewed.

---

