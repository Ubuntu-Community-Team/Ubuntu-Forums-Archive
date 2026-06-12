---
title: "TFTPD problems. - Connection timed out."
date: 2008-01-28
forum: Server Platforms
---

### Post by syncro11 on 2008-01-28
Hi, I have deployed ubuntu server 7.04
the configuration is simple, just want to serve config files for various cisco devices.
the server is sitting on the edge network with static ip, not behind any firewalls or NAT's.

I followed the instructions for tftpd deployment from the site 
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/) 
with no success...

The TFTPD is setup and working internally however i cannot access the service from outside the network or across the internet.

I know i can access the SSH from the internet, but I cannot successfuly transfer TFTP over internet.

it will work on local host and on itself, but not across internet. When I open the daemon logs, I see the TFTP actvity as it should, however it is not serving any files, the clients report as connection timed out.

can anyone help me on this?

thanks so much,

-j

---

### Post by freebeer on 2008-01-28
Sound like something along the way is blocking your FTP port(s).
ISP, maybe?

---

### Post by syncro11 on 2008-01-29
There is no blockage. When I run solarwinds tftp server on windows server, it works perfect.

keep in mind this is a e1 static IP.

thanks,

---

### Post by amo-ej1 on 2008-01-29
try sniffing port 69 ( sudo tcpdump -ni any port 69 ) to see if the tftp requests for files are entering.

(or try to use netstat (sudo netstat -anp | grep 69 ) to see of port 69 is open and accepting tftp connections).

On my system tftpt is handled through xinetd.
```

root@lape:/home/edb# netstat -anp | grep xinetd
udp        0      0 0.0.0.0:69              0.0.0.0:*                          4984/xinetd         
udp        0      0 0.0.0.0:69              0.0.0.0:*                          4984/xinetd   

```

---

### Post by syncro11 on 2008-01-29
hi amo-

this is the result of my netstat

$ sudo netstat -anp | grep 69
Password:
udp        0      0 0.0.0.0:69              0.0.0.0:*                          6387/xinetd       

and here is the result of the tcpdump: (keep in mind i #'d out the IP's)

$ sudo tcpdump -ni any port 69
Password:
tcpdump: WARNING: Promiscuous mode not supported on the "any" device
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
10:34:04.720232 IP 99.###.###.###.7410 > 208.###.###.###.69:  55 RRQ "/sub/sub.cfg" octet timeout 5 tsize 
10:34:07.214026 IP 99.###.###.###.7410 > 208.###.###.###.69:  55 RRQ "/sub/sub.cfg" octet timeout 5 tsize 
10:34:09.712824 IP 99.###.###.###.7410 > 208.###.###.###.69:  55 RRQ "/sub/sub.cfg" octet timeout 5 tsize 
10:34:12.211872 IP 99.###.###.###.7410 > 208.###.###.###.69:  55 RRQ "/sub/sub.cfg" octet timeout 5 tsize

---

### Post by syncro11 on 2008-01-30
So the requests are hitting the tftp box? any reason why it wont serve?

Thanks,

---

