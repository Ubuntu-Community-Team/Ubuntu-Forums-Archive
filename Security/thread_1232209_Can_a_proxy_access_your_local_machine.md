---
title: "Can a proxy access your local machine"
date: 2009-08-05
forum: Security
---

### Post by Rytron on 2009-08-05
Hi.
If someone uses a proxy, can that proxy access your local machine?

---

### Post by Dr Small on 2009-08-05
Not if that local machine isn't connected to the network.

---

### Post by cdenley on 2009-08-05
If you configure firefox to use a proxy, then all your web requests will be sent to the proxy instead of the destination server, expecting the proxy to respond with the web server's response. The proxy can capture and read your traffic, or send fake responses which never actually came from the web server you asked for. This is the only type of "access" a proxy has when you connect to it. You're safe as long as the software communicating with the proxy (firefox) can't be exploited by a carefully crafted response, which is highly unlikely.

---

### Post by Rytron on 2009-08-05
> **cdenley said:**
> If you configure firefox to use a proxy, then all your web requests will be sent to the proxy instead of the destination server, expecting the proxy to respond with the web server's response. The proxy can capture and read your traffic, or send fake responses which never actually came from the web server you asked for. This is the only type of "access" a proxy has when you connect to it. You're safe as long as the software communicating with the proxy (firefox) can't be exploited by a carefully crafted response, which is highly unlikely.

Thank you cdenley for clarifying that.

---

