---
title: "Restricting ssh access to a smaller domain"
date: 2010-08-19
forum: Security
---

### Post by nipun2512 on 2010-08-19
Hi,

I am trying to block all ssh access from anyone outside a given domain say "abc.com"?

Can anyone suggest how I can go about doing this..? I've had a look at iptables and .ssh configurations but haven't exactly been able to resolve this...

Thanks
Nipun

---

### Post by Bachstelze on 2010-08-19
Blocking connexions with iptables based on a name (as opposed to an IP address) in iptables might be cumbersome (if at all possible).  You'd probably be better off doing it in sshd_config:

```
AllowUsers *@*.abc.com
```

Be careful, though, sshd is very strict about addresses: the forward and reverse DNS records must match, otherwise login will be denied.

---

### Post by bodhi.zazen on 2010-08-20
You can also use tcpwrapper (ie /etc/hosts.allow and /etc/hosts.deny).

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-tcpwrappers-access.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-tcpwrappers-access.html)

---

### Post by bilkay on 2010-08-23
I'm just guessing here, but I think you can do this in the /etc/hosts.allow and /etc/hosts.deny files.

In hosts.allow: ssh: {allowed domains}
In hosts.deny: ssh: ALL

Of course, if there's another entry in hosts.allow like ALL: ALL, this won't work.

---

### Post by Lars Noodén on 2010-08-24
To refine what @Bachstelze wrote, it is easier to work with Groups than Users.  The [sshd_config](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html) configuration syntax is the same.  

The **Match** directive gives a wider range of choices and allows specific hosts and networks to be matched.  **Match Address**  allows you to use CIDR addressing.

So deny everyone and then add a **Match Host** option after that to allow in just that one that subnet.

---

