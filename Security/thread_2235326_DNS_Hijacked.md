---
title: "DNS Hijacked?"
date: 2014-07-20
forum: Security
---

### Post by jason115 on 2014-07-20
Ubuntu 11.04


If I try to resolve a host name to IP of domains that don't exist, my box always resolves to 54.183.116.245.


Example:
root@system:~# ping fifcnrizzzzzzzzzzzzzz.com
PING fifcnrizzzzzzzzzzzzzz.com.com (54.183.116.245) 56(84) bytes of data.
^C


root@system:~# cat /etc/resolv.conf 
nameserver 8.8.8.8
nameserver 8.8.4.4


root@system:~# cat /etc/hosts
127.0.0.1	localhost


# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


Seems like a hijack of my DNS resolution. Not sure what to check for this. Any suggestions? Thank you.

---

### Post by coffeecat on 2014-07-20
You are running an unsupported version of Ubuntu. 11.04 went end-of-life in October 2012. As such we cannot support troubleshooting such an obsolete version of Ubuntu. You need to re-install with a currently supported version of Ubuntu, either the 12.04 LTS (long-term support) or the more recent 14.04 LTS.

What I would suggest is to boot up with a 14.04 live DVD or USB, set google nameservers as you have done with 11.04 if you wish, connect to the internet, and try your ping in the live session. If you get an "unknown host" error from the ping, then you know the problem is with your 11.04 installation, which is another reason to replace it with a supported version.

Please see:

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

