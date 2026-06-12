---
title: "server security"
date: 2015-03-11
forum: Server Platforms
---

### Post by atux on 2015-03-11
hello everyone.
i do have server 12.04 with public IP (vps) and it has freepbx 2.11, asterisk 11.
i have changed the default ports of apache to 88, ssh to 82, bindport to 5090.
i do need to stop all other kinds of attacks, but i am stuck.
eg ssh brute force. stop all countries IPs except Belgium, Greece, UK, Russia
ban all faulty attempts for 30 minutes.

---

### Post by Lars Noodén on 2015-03-11
You could look at rate limiting in iptables / UFW.  Then on top of that you could look at something like ssh-guard or one of the other log monitors. 

Have you already disabled remote root login and turned off passwords for SSH, using keys only?

---

### Post by SeijiSensei on 2015-03-11
The simplest way to avoid brute-force attacks is to use iptables to permit access to ports like 22 only from IP addresses you trust.  
```
/sbin/iptables -A INPUT -s a.good.ip.address -p tcp --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -s another.good.ip.address -p tcp --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 22 -j REJECT

```

Another good solution is to use OpenVPN to [set up an encrypted tunnel]("http://openvpn.net/static.html") between your server and the machines that need to reach it.  That's how I manage connections with my servers at Linode.

---

