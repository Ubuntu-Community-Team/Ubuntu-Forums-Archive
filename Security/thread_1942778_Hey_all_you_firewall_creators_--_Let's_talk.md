---
title: "Hey all you firewall creators -- Let's talk"
date: 2012-03-18
forum: Security
---

### Post by kevdog on 2012-03-18
On the subject of linux firewalls, there seems to be a lot of discussion about opening or allowing certain ports, however a lot of the other finer nuances seemed to be missed.   

I often see code floating around the internet such as the following, which are commonly added to ip start up scrips:

echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
echo "1" > /proc/sys/net/ipv4/conf/all/log_martians
echo "2" > /proc/sys/net/ipv4/conf/all/rp_filter
echo "30" > /proc/sys/net/ipv4/tcp_fin_timeout
echo "2400" > /proc/sys/net/ipv4/tcp_keepalive_time
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
echo "0" > /proc/sys/net/ipv4/tcp_sack
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
echo "0" > /proc/sys/net/ipv4/tcp_timestamps
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/all/send_redirects

Are these kernel modifications really effective, and are there others that should be added to any firewall startup script?

---

### Post by Dangertux on 2012-03-18
> **kevdog said:**
> On the subject of linux firewalls, there seems to be a lot of discussion about opening or allowing certain ports, however a lot of the other finer nuances seemed to be missed.   

I often see code floating around the internet such as the following, which are commonly added to ip start up scrips:

echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
echo "1" > /proc/sys/net/ipv4/conf/all/log_martians
echo "2" > /proc/sys/net/ipv4/conf/all/rp_filter
echo "30" > /proc/sys/net/ipv4/tcp_fin_timeout
echo "2400" > /proc/sys/net/ipv4/tcp_keepalive_time
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
echo "0" > /proc/sys/net/ipv4/tcp_sack
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
echo "0" > /proc/sys/net/ipv4/tcp_timestamps
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/all/send_redirects

Are these kernel modifications really effective, and are there others that should be added to any firewall startup script?

These are all kernel tuneables and they can be very effective depending on the desired result.  There are a few in there that are performance as opposed to security enhancements and I would think depend heavily on the type of traffic you're expecting to see. From a system security point of view the ones that I feel are important are the following

```

echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
echo "1" > /proc/sys/net/ipv4/conf/all/log_martians
echo "2" > /proc/sys/net/ipv4/conf/all/rp_filter
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/all/send_redirects

```

As these tuneables all focus on either logging or deterring traffic that could be used in a malicious nature.

Hope this helps

---

### Post by kevdog on 2012-03-18
Any more kernel tuneables of any value in terms of security? It seems these "details" are often a footnote.

---

### Post by bodhi.zazen on 2012-03-19
> **kevdog said:**
> Any more kernel tuneables of any value in terms of security? It seems these "details" are often a footnote.

Best links I know are

[http://www.puschitz.com/SecuringLinux.shtml#KernelTunableSecurityParameters](http://www.puschitz.com/SecuringLinux.shtml#KernelTunableSecurityParameters)

[http://www.cyberciti.biz/faq/linux-kernel-etcsysctl-conf-security-hardening/](http://www.cyberciti.biz/faq/linux-kernel-etcsysctl-conf-security-hardening/)

The second is mainly networking.

From there it "degenerates" to kernel documentation fairly rapidly

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

