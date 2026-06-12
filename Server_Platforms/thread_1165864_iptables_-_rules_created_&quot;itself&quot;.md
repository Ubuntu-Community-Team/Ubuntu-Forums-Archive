---
title: "iptables - rules created &quot;itself&quot;"
date: 2009-05-21
forum: Server Platforms
---

### Post by kuda on 2009-05-21
Hi all,

I have a problem which is very frustrating :| , have server witch postfix, mailscanner, spamassassin+brothers, mailwatch,mailscanner-mrtg,vispan and ossec .. everything is working but there is something /apparmor??/ blocking incoming communication with machine I need to talk to ... problem is that "something" is creating rules on iptables and DROPs whole incoming traffic from that machine i am talking about .. even if I reset iptables to "full open" drop rule comes after 10-15 minutes itself back. Using ubuntu 8.04.2 distro.

Thanx in advance for any suggestions.

kuda

---

### Post by mechdave on 2009-05-21
First thing I would do is isolate the machine from your network and then investigate whether a root kit has been covertly installed on it. It seems a little sus that rules create themselves...

---

### Post by sickdude on 2009-05-21
Check out this thread about rootkit scanners and make your choice.

[http://ubuntuforums.org/showthread.php?t=578161](http://ubuntuforums.org/showthread.php?t=578161)

It might help if you paste a piece of the syslog in here. Do you have a firewall running on this machine? What rules are set in iptables?

---

### Post by kuda on 2009-05-21
Thanx a lot for tips!
I am working on it. That is actually some rootkit which have been installed together with osssec .... but I thought that this software is only non-invasive ...

***********************************************************************
here is my problematic iptables - "selfcreated", even if iptables is cleaned/flushed this comes after a while

root@gate:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       all  --  viruswall.hkommune.no  anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       all  --  viruswall.hkommune.no  anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@gate:~# 

***********************************************************************
here is my original iptables

root@gate:~# iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

  672 97465 ACCEPT     all  --  lo     any     anywhere             anywhere    

 2016  383K ACCEPT     all  --  any    any     anywhere             anywhere    
        state RELATED,ESTABLISHED
    3   252 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp echo-request
    1    60 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh
   29  1392 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:smtp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp spt:domain
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp spt:domain
  164 17465 DROP       all  --  any    any     anywhere             anywhere 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination  

Chain OUTPUT (policy ACCEPT 3495 packets, 532K bytes)
 pkts bytes target     prot opt in     out     source               destination  
root@gate:~#     

*************************************************************************
and netstat

root@gate:~# netstat -nlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:11553         0.0.0.0:*               LISTEN      1439/MailWatch SQL
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4476/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4852/apache2
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1856/smtpd
tcp6       0      0 :::22                   :::*                    LISTEN      4376/sshd
udp        0      0 127.0.0.1:161           0.0.0.0:*                           4768/snmpd
udp        0      0 172.32.1.12:123         0.0.0.0:*                           3548/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                           3548/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                           3548/ntpd
udp6       0      0 fe80::202:a5ff:fe75:123 :::*                                3548/ntpd
udp6       0      0 ::1:123                 :::*                                3548/ntpd
udp6       0      0 :::123                  :::*                                3548/ntpd
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     11868    4476/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12343    4755/master         public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     12350    4755/master         private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     12354    4755/master         private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     12358    4755/master         private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     12362    4755/master         private/defer
unix  2      [ ACC ]     STREAM     LISTENING     12366    4755/master         private/trace
unix  2      [ ACC ]     STREAM     LISTENING     12370    4755/master         private/verify
unix  2      [ ACC ]     STREAM     LISTENING     12374    4755/master         public/flush
unix  2      [ ACC ]     STREAM     LISTENING     12378    4755/master         private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     12382    4755/master         private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     12386    4755/master         private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     12390    4755/master         private/relay
unix  2      [ ACC ]     STREAM     LISTENING     12394    4755/master         public/showq
unix  2      [ ACC ]     STREAM     LISTENING     12398    4755/master         private/error
unix  2      [ ACC ]     STREAM     LISTENING     12402    4755/master         private/retry
unix  2      [ ACC ]     STREAM     LISTENING     12406    4755/master         private/discard
unix  2      [ ACC ]     STREAM     LISTENING     12410    4755/master         private/local
unix  2      [ ACC ]     STREAM     LISTENING     12414    4755/master         private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     12418    4755/master         private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     12422    4755/master         private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     12426    4755/master         private/scache
unix  2      [ ACC ]     STREAM     LISTENING     12430    4755/master         private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     12434    4755/master         private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     12438    4755/master         private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     12442    4755/master         private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     12446    4755/master         private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     12450    4755/master         private/mailman

---

### Post by kuda on 2009-05-21
seems that osssec is cause of the problem, so now i have to figure out how does it work and why it behaves so ....

---

### Post by kuda on 2009-05-21
solved ... in /var/ossec/etc/ossec.conf - whitelisting .. tnx to all, have a nice day!

---

