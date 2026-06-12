---
title: "tftp transfer timed out in 10.10"
date: 2010-11-07
forum: Server Platforms
---

### Post by jeter on 2010-11-07
Hi,

I'm trying to test transfering tftp files on my localhost using tftpd/xinetd but it keeps timing out/transfer failed. I setup xinetd and tftpd on my laptop (ubuntu desktop 10.10 32bit)

/etc/xinetd.conf
```

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
 log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d

```

/etc/xinetd.d/tftp
```

service tftp
{
        protocol        = udp
        port            = 69
        socket_type     = dgram
        wait            = yes
        user            = nobody
        server          = /usr/sbin/in.tftpd
        server_args     = -c -s /tftpboot
        disable         = no
}

```

root@laptop:/etc# nmap -sU localhost

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-11-07 00:23 CDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000015s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 997 closed ports
PORT     STATE         SERVICE
68/udp   open|filtered dhcpc
69/udp   open|filtered tftp
5353/udp open|filtered zeroconf


root@laptop:/etc/xinetd.d# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


root@laptop:/home/jete# tftp localhost
tftp> verbose
Verbose mode on.
tftp> trace
Packet tracing on.
tftp> status
Connected to localhost.localdomain.
Mode: netascii Verbose: on Tracing: on
Rexmt-interval: 5 seconds, Max-timeout: 25 seconds
tftp> put test
putting test to localhost.localdomain:test [netascii]
sent WRQ <file=test, mode=netascii>
sent WRQ <file=test, mode=netascii>
sent WRQ <file=test, mode=netascii>
sent WRQ <file=test, mode=netascii>
sent WRQ <file=test, mode=netascii>
Transfer timed out.


So, I'm lost and need help

---

### Post by jeter on 2010-11-09
I disabled both apparmor and ufw. I tried transferring another file and saw this in /var/log/messages


Nov  8 22:49:07 H#016Ð¶-laptop#000#025#000#000#000127.0.0.1#000#000#000<81>#000#000#000¸#000Ð¶¸#000Ð¶#020#000#000#0004#000#000#000#000#000#000#000rted working: 1 available service#000 t@#000#000#000D#000#000#000#000#000#000#000 8 22:48:53 jete-laptop xinetd[4174]: removing time#012<80>#000#000#000,#000#000#000xinetdessage repeated 4 times#000#000#000#000#000#000#000#031#000#000#000#000#006Ð¶P#000Ð¶<80>#000#000#000H#000#000#000#030#000#000#000#024#000#000#000imudp#000aptop#0001#000#000#000h#000Ð¶h#000Ð¶174]:#000#000#000!#000#000#000#031#000#000#000#000#006Ð¶@#000Ð¶<80>#000#000#000H#000#000#0000#000#000#000$#000#000#000localhost.localdomain#000+#0000#00#025#000#000#000imudp#0000.1#000#000#000M#001#000#000H&*#010#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#001#000#001#000ÿÿ#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000ÿÿ#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000p#015Ð¶#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000<90>#016Ð¶#025#000#000#000<80>#015Ð¶#011#000#000#000P#016Ð¶#005#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000ÃÒØL#000#000#000#000Ú#007#000#000#013#000#000#000#010#000#000#000#026#000#000#0001#000#000#000#007#000#000#000<9f>.#005#000#006#000#000#000-#006#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000Ú#007#000#000#013#000#000#000#010#000#000#000#026#000#000#0001#000#000#000#007#000#000#000<9f>.#005#000#006#000#000#000-#006#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#0000#000#000#000#000#000#000#000q#000#000#000¨#000Ð¶¨#000Ð¶ 8 22:48:53 xinetd[4174]: removing discard#00009#000#000#000<88>#015Ð¶@#000Ð¶ 8 22:48:53 xinetd[4174]: removing time#000p#000#000#000#034#000#000N
Nov  8 22:49:08 ¨#016Ð¶-laptop#000#035#000#000#0004174<80>#015Ð¶!#000#000#000#006#000#000#000!#000#000#000#015#010#000#000H#016Ð¶-laptop#000#025#000#000#000127.0.0.1#000#000#000<81>#000#000#000¸#000Ð¶¸#000Ð¶#020#000#000#0004#000#000#000#000#000#000#000rted working: 1 available service#000 t@#000#000#000D#000#000#000#000#000#000#000 8 22:48:53 jete-laptop xinetd[4174]: removing time#012<80>#000#000#000,#000#000#000xinetdessage repeated 4 times#000#000#000#000#000#000#000#031#000#000#000#000#006Ð¶P#000Ð¶<80>#000#000#000H#000#000#000#030#000#000#000#024#000#000#000imudp#000aptop#0001#000#000#000h#000Ð¶h#000Ð¶174]:#000#000#000!#000#000#000#031#000#000#000#000#006Ð¶@#000Ð¶<80>#000#000#000H#000#000#0000#000#000#000$#000#000#000localhost.localdomain#000+#0000#00#025#000#000#000imudp#0000.1#000#000#000M#001#000#000H&*#010#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#001#000#001#000ÿÿ#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000ÿÿ#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000p#015Ð¶#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000<90>#016Ð¶#025#000#000#000<80>#015Ð¶#011#000#000#000P#016Ð¶#005#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000ÃÒØL#000#000#000#000Ú#007#000#000#013#000#000#000#010#000#000#000#026#000#000#0001#000#000#000#007#000#000#000<9f>.#005#000#006#000#000#000-#006#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000Ú#007#000#000#013#000#000#000#010#000#000#000#026#000#000#0001#000#000#000#007#000#000#000<9f>.#005#000#006#000#000#000-#006#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#000#0000#000#000#000#000#000#000#000q#000#000#000¨#000Ð¶¨#000Ð¶ 8 22:48:53 xinetd[4174]: removing disca

i think i need to file a bug report

---

### Post by HermanAB on 2010-11-09
Note that tftp has NO built-in authentication.  Therefore, in order to avoid a huge security hole, they made the hole a bit smaller by refusing to work if the data directory is writeable.

Here is a guide that some info on using tftp in there somewhere:
[http://www.aeronetworks.ca/howtos/ris-howto.html](http://www.aeronetworks.ca/howtos/ris-howto.html)

---

