---
title: "Ubuntu 12.04 resolv.conf issues?"
date: 2012-06-28
forum: Server Platforms
---

### Post by oliwei on 2012-06-28
Hi,

I have a very odd problem on my new installed Ubuntu 12.04 machines. We use puppet and for some reason puppet is running very very slow, but only on 12.04. On 10.04 puppet runs very fast. I checked a few things (tcpdump and logfiles) and noticed that for some reason the puppet agent on 12.04 tries to resolve host puppet instead of the fqdn puppet.mydomain.local. This is only the case on 12.04.

Most of the machines are configured via DHCP and the search domain is definitely set in /etc/resolv.conf. Running a ping on puppet appends the domain name just fine. It's just the puppet agent that doesn't seem to resolve correctly. I have a few Solaris 10 machines that are running the same version of puppet and they also use DHCP and here puppet behaves correctly. I even tried setting server = puppet.mydomain.local in /etc/puppet/puppet.conf but this doesn't solve the whole problem. As soon as a file gets pulled by a manifest the agent again tries to resolve puppet without the domain name.

I'm really stuck here. One strange thing I did notice is that it seems to be a combination of Ubuntu 12.04 and our 10.04 Bind DNS servers. They are just forwarding all the requests to our Windows Server and we never ever had a problem with this setup. If I use one of the Windows DNS Servers, resolving a host without a domain appended works fine.

I'm really lost.... please give me a hint.

---

### Post by oliwei on 2012-06-28
the problem seems to be not just with puppet. I ran tcpdump on the ubuntu 12.04 host and every time it tries to resolve ipv6 hostnames without a domain:

16:49:43.714130 IP ve6330.a.space.corp.40453 > gedaspw02.a.space.corp.domain: 62997+ AAAA? ds-san-02. (27)

the system hangs.... but only when querying the bind dns servers. When querying the Windows DNS servers there is no problem.

---

### Post by CharlesA on 2012-06-28
Is DNSMasq running on that box?

By default 12.04 desktop has it enabled.

See here on how to disable it:
[http://ubuntuforums.org/showpost.php?p=11923702&postcount=40](http://ubuntuforums.org/showpost.php?p=11923702&postcount=40)

---

### Post by oliwei on 2012-06-28
Hi,

no I'm running 12.04 Server.

Regards,
Oliver

---

### Post by CharlesA on 2012-06-28
Interesting, what does /etc/resolv.conf say now?

---

### Post by oliwei on 2012-06-28
it lists my dns server (both BIND Ubuntu 10.04)
and a search domain.

It's just so strange that it seems that my BIND DNS servers can't handle/forward this AAAA queries. And also why this AAAA queries are always missing the search domain?

nameserver 172.28.16.11
nameserver 172.28.16.13
search a.space.corp

---

### Post by CharlesA on 2012-06-28
I haven't deal with IPv6 much, but maybe this could help:
[http://docs.oracle.com/cd/E19683-01/817-4843/dnsintro-ex-32/index.html](http://docs.oracle.com/cd/E19683-01/817-4843/dnsintro-ex-32/index.html)

Not quite sure why BIND isn't handling AAAA records.

Ubuntu 12.04 should have bind9 installed:
[http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html](http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html)

---

### Post by oliwei on 2012-06-29
I think it is a bug. I have installed a 10.04 vm on the same network using the BIND DNS servers and tcpdump shows clearly that it's always using the fully qualified domain name.

---

### Post by CharlesA on 2012-06-29
File a bug report over on launchpad. :)

---

### Post by oliwei on 2012-07-02
I have first started a thread on launchpad answers. Maybe this is really just a configuration issue.

[https://answers.launchpad.net/ubuntu/+question/202011](https://answers.launchpad.net/ubuntu/+question/202011)

Thanks for all the help.

Best Regards,
Oliver

---

