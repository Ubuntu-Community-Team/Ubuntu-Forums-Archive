---
title: "Port forwarding"
date: 2019-02-27
forum: Security
---

### Post by packetsmacker on 2019-02-27
I am trying to forward 514/tcp to 5515/tcp. I followed some guides but they didn't work. Can someone please provide the cmd? I am on the latest version of the server OS.

---

### Post by Tr1p on 2019-03-12
Do you mean by iptables?

In iptables:
*-A PREROUTING -i eno1 -p tcp -m tcp --dport 1337 -j DNAT --to-destination 10.10.10.10:8000*

1337 is outside port, 8000 inside port

---

### Post by SeijiSensei on 2019-03-12
If you're trying to redirect traffic arriving on the server to another port on the same server, use REDIRECT.  Try this:

```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 5515  --destination-port 514
```

The rule in the previous post is designed to send traffic arriving on one port to *another* machine and potentially a different port.

---

