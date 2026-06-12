---
title: "iptables with sshd acting as proxy"
date: 2011-09-04
forum: Security
---

### Post by Frozen Forest on 2011-09-04
By using this trick was it possible to use my ssh server as a proxy, but how should iptables be configured for traffic that is tunneled through ssh and then uses port forwarding? Can even iptables distingush the traffic that is tunnled for portforwarding from traffic that originate from the server itself? I only want the server to connect to update.ubuntu.com while the traffic that being tunneled should be able to connect to any site.
[http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)
```
$ssh -D 9999 username@ip-address-of-ssh-server
```

---

### Post by CharlesA on 2011-09-04
You'd have to allow whatever port you are forwarding in iptables, even if it's not a service running on the host.

Not sure if you can filter traffic like that with iptables, maybe using squid or dansguardian or something like that.

---

### Post by The Cog on 2011-09-05
You might be able to use the iptables clause **--uid-owner username** if you run the ssh proxy under a special user account. I can't think of a way of doing it if the user uses the same user id when logging in locally.

---

### Post by Frozen Forest on 2011-09-05
Thanks for the answers --uid-owner might do the trick, if I create a separate account for proxy.

---

