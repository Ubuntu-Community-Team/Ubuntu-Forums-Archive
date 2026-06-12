---
title: "danted - iptables- imspector"
date: 2009-06-11
forum: Server Platforms
---

### Post by Kasian on 2009-06-11
I need to store icq history on web server, so i installed imspector (imspector.org)

My icq client is connecting to dante socks5 server, and its traffic is outputted by iptables to imspector.
ICQ works well via socks5, but imspector gets nothing.
When I connect to imspector directly via http all is ok. So I believe it's not imspector problem. 

imspector is listening on port 16667 for non http connections and on port 18080 for http connections.

danted.conf:
```

internal: eth0 port = 1080
internal: 127.0.0.1 port = 1080

external: eth0
external: XX.XX.XX.XX #my server ip

method: none
clientmethod: none
user.notprivileged: nobody

client pass {
        from: 0.0.0.0/0 to: 0.0.0.0/0 port = 1080
}

client block {
        from: 0.0.0.0/0 to: 0.0.0.0/0
        log: connect error
}

pass {
        from: 0.0.0.0/0 to: 205.188.0.0/16 port = 5190
        protocol: tcp udp
}

pass {
        from: 0.0.0.0/0 to: 64.12.0.0/16 port = 5190
        protocol: tcp udp
}

block {
        from: 0.0.0.0/0 to: 0.0.0.0/0
        log: connect error
}


```

iptables output rule:
```

iptables -t nat -A OUTPUT -p tcp --destination-port 5190 -m owner --uid-owner 0 -j REDIRECT --to-ports 16667

```

What's wrong here?

---

### Post by Kasian on 2009-06-26
Any ideas? =(

---

