---
title: "Firewall FTP Problem"
date: 2018-06-27
forum: Server Platforms
---

### Post by secooonder on 2018-06-27
Hello
i am using iptables Firewall  + squid in Ubuntu 16.04.3 LTS .
i can not ftp a computer on the internal network from the external network.
i did not solve the 3 days.
192.168.50.101 is ftp Server.
my iptables conf is;
&#304;nput Chain
> -A INPUT -j ACCEPT ( Fully Open for ftp not working)
Forward Chain
-A FORWARD -j ACCEPT ( Fully Open for ftp not working)
Prerouting Chain
-A PREROUTING -p tcp -m tcp -m multiport  -i eth2 -j DNAT --to-destination 192.168.50.101 --dports 20,21

192.168.50.101 is fully open local firewall.But i cant ftp from outside network to this machine.
i setup ftp server another machine.i redirect ip and port in firewall,but i can not ftp this machine too.

i can ftp from local network.
So, i have read alot of articles.And then i insert the command my firewall.This commans are
```
[COLOR=#111111][FONT=Consolas]ip_conntrack_ftp,[/FONT][/COLOR]modprobe nf_conntrack_ftp,modprobe ip_nat_ftp


```

But ,i can not ftp from outside to inside .Active ,passive both of them is not running

My firewall log is 
> [COLOR=#242729][FONT=Consolas]425 Can't open data connection[/FONT][/COLOR]

What do i have to do on the iptables firewall ?

Can you help me ?

Thank you very much








[COLOR=#212121][FONT=arial]What do I have to do on the firewall[/FONT][/COLOR]

---

### Post by uRock on 2018-06-27
Do you have port forwarding enabled on the router?

---

### Post by 1clue on 2018-06-27
ftp protocol is not compatible with NAT. To fix it you need a firewall with ftp-specific hacks and an ftp server which is aware of NAT.

Considering that ftp is impossible to secure (it sends clear-text, unencrypted passwords) these problems don't matter much.

Instead, consider sftp which is built-in to openssh, is firewall friendly, encrypted and provides exactly the same functionality with none of the problems.

---

### Post by secooonder on 2018-06-28
uRock and 1clue

Thank you very much for your help
ip forwarding is enable.
> root@gateway:~# more /proc/sys/net/ipv4/ip_forward
1



and
> root@gateway:~# more /etc/sysctl.conf#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#


#kernel.domainname = example.com


# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3


##############################################################3
# Functions previously found in netbase
#


# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1


# Uncomment the next line to enable TCP/IP SYN cookies
# See [http://lwn.net/Articles/277146/](http://lwn.net/Articles/277146/)
# Note: This may impact IPv6 TCP sessions too
net.ipv4.tcp_syncookies=1


# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1




1clue.
 i managed ubuntu firewall 12.04 LTS at another location . i can make ftp from outside to inside.


Please help me

---

### Post by 1clue on 2018-06-28
I haven't used an ftp server for more than 10 years, so I don't remember much about it and it's likely not the same as it was. I had to find ftp server software which was aware of nat, that's all I remember.

Just FYI, if a company is trying to get any sort of network security certification, the mere presence of an FTP server is an automatic fail for the entire site. FTP is not secure, and cannot be made secure.

In my opinion, starting an FTP server with access to the outside world is a big welcome mat for people with malicious intent. Spend a few minutes with google and you'll see a whole lot of information supporting my position.

I'll gladly help you set up sftp though.

---

### Post by TheFu on 2018-06-30
> 
Just FYI, if a company is trying to get any sort of network security certification, the mere presence of an FTP server is an automatic fail for the entire site. FTP is not secure, and cannot be made secure.

+1.

Happy to help with sftp.  Haven't touched plain FTP since the 1990s other than for CTF competitions.

---

