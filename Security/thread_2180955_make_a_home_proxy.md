---
title: "make a home proxy"
date: 2013-10-15
forum: Security
---

### Post by darklandspider on 2013-10-15
hey all,

i'm running ubuntu on a vm and have a working ssh tunnel to it from wan already.
i've installed squid3 and i would like to setup a personal proxy server that i can use
on my work conputer's web browser to tunnel the traffic securely throw.

how do i do that, and what will i later config into the browser to tunnel the traffic to my proxy?
thank in advanced :)

---

### Post by Lars Noodén on 2013-10-15
If you use the home machine as a SOCKS proxy, you don't need Squid. Make the proxy connection and then configure your browser to use the SOCKS proxy at the localhost.

```

ssh -D 12345 home.example.org

```

Then as long as that connection is open, you can use the SOCKS proxy via that port on the localhost.  Be sure that DNS queries are also going via the proxy.  Go to the URL *about:config* and set *network.proxy.socks_remote_dns* to true.

If you want to use Squid, don't use the SOCKS proxy.  Instead, make a tunnel to Squid and configure your browser to use the regular proxy at the designated port on the localhost.

```

ssh -L 3128:localhost:3128 home.example.org

```

You're using Firefox, right?

---

### Post by darklandspider on 2013-10-16
> **Lars Noodén said:**
> If you use the home machine as a SOCKS proxy, you don't need Squid. Make the proxy connection and then configure your browser to use the SOCKS proxy at the localhost.

```

ssh -D 12345 home.example.org

```

Then as long as that connection is open, you can use the SOCKS proxy via that port on the localhost.  Be sure that DNS queries are also going via the proxy.  Go to the URL *about:config* and set *network.proxy.socks_remote_dns* to true.

If you want to use Squid, don't use the SOCKS proxy.  Instead, make a tunnel to Squid and configure your browser to use the regular proxy at the designated port on the localhost.

```

ssh -L 3128:localhost:3128 home.example.org

```

You're using Firefox, right?

No, that's not what i meant.
i use firefox on all my machines but the fox is not with me at work.
i have a computer at work that's block from some sites by my work's network.
i want to tunnel my traffic from that work computer, via WAN , to my home computer that will be used as a proxy.
at work i can use only chrome or (god help me) IE.

and also, the work machine's running windows7, and putty is blocked there.
on the ubuntu machine - ssh server is active and i can access it via my phone (connectbot)
but i cant ssh from my work computer home.

the tunnel i want to build will look somewhat like that:

[IMG]http://imageshack.us/a/img689/6649/t8lk.jpg[/IMG]

also, i have an Apache server witch is running on the same vm , and all ports on the home router
is forwarding to that vm. from my work browser i can browse to my IP and go to the html files on my
Apache server.

---

### Post by cariboo on 2013-10-16
We don't support this type of activity here, if you want access to blocked web sites, you have to ask your IT department. Thread closed.

---

