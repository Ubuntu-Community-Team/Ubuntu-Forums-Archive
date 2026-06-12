---
title: "Route host port 2223 to guest port 22"
date: 2012-09-05
forum: Virtualisation
---

### Post by kiiiir on 2012-09-05
Hi,

I have a LXC container with IP 10.0.3.2 and a host system with public IP.
How to route public_ip:2223 of host to the 10.0.3.2:22 to login via ssh to the container?

---

### Post by mfontani on 2012-09-10
> **kiiiir said:**
> have a LXC container with IP 10.0.3.2 and a host system with public IP.
How to route public_ip:2223 of host to the 10.0.3.2:22 to login via ssh to the container?

I use the following to let me ssh from the outside to the LXC container, assuming the interface your public IP is listening on is "eth0":

  sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 2223 -j DNAT --to-destination 10.0.3.2:22

---

### Post by kiiiir on 2012-09-11
Thank you!

---

### Post by HermanAB on 2012-09-13
Another nice tool for redirecting traffic is socat.

---

### Post by kiiiir on 2012-09-13
> **HermanAB said:**
> Another nice tool for redirecting traffic is socat.

Could you describe how to use it in my case?

---

### Post by markbl on 2012-09-13
> **kiiiir said:**
> Could you describe how to use it in my case?

Socat is just a general purpose byte stream forwarder. It is the modern day replacement for netcat but much more flexible and powerful. Unfortunately it is a little more complex to use. You want something like:

```

socat TCP-LISTEN:2223,fork,reuseaddr TCP:10.0.3.2:22

```

That command will accept connections on host port 2223 and then fork off a new instance to forward the received bytes to port 22 on 10.0.3.2. Will keep doing this until you ctrl+c it.

See the copious examples in the man page for socat.

---

