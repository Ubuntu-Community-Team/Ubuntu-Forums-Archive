---
title: "(Newbie, warning)Connect via ODBC to Postgresql on port 5432"
date: 2018-02-19
forum: Security
---

### Post by akky_66 on 2018-02-19
Hi,

I'm trying to connect over ODBC to port 5432 on my Ubuntu 16.04 box.

I have fail2ban installed with some iptable settings.

I can see on a netstat -a that the port is open and  listening.
I can connect via phppgadmin.
My pg_hba.conf file has the account able to logon.
My postgresql.conf file is listening on all ports.

However, I think there must be something in my iptables config that is blocking it.

Here is the current output with an iptables-save -c performed.

```
root@localhost:/var/lib/postgresql# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
f2b-pam-generic  tcp  --  anywhere             anywhere
f2b-recidive  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-nsd    tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-named-refused  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-vsftpd  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-suhosin  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-php-url-fopen  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-shellshock  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-modsecurity  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-fakegooglebot  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-botsearch  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-nohome  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-overflows  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-noscript  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-badbots  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-auth  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-selinux-ssh  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-dropbear  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-sshd-ddos  tcp  --  anywhere             anywhere             multiport dports ssh
f2b-sshd   tcp  --  anywhere             anywhere             multiport dports ssh
DROP       all  --  anywhere             anywhere             -m geoip --destination-country CN
DROP       all  --  anywhere             anywhere             -m geoip --destination-country US
f2b-pam-generic  tcp  --  anywhere             anywhere
f2b-recidive  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-nsd    tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-named-refused  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-vsftpd  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-suhosin  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-php-url-fopen  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-shellshock  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-modsecurity  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-fakegooglebot  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-botsearch  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-nohome  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-overflows  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-noscript  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-badbots  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-apache-auth  tcp  --  anywhere             anywhere             multiport dports http,https
f2b-selinux-ssh  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-dropbear  tcp  --  anywhere             anywhere             multiport dports 0:65535
f2b-sshd-ddos  tcp  --  anywhere             anywhere             multiport dports ssh
f2b-sshd   tcp  --  anywhere             anywhere             multiport dports ssh
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere
ACCEPT     tcp  --  xxx.xxx.xxx.xxx       xxx.xxx.xxx.xxx       tcp spts:1024:65535 dpt:postgresql state NEW,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:postgresql


Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere
ufw-track-forward  all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere


Chain f2b-apache-auth (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-badbots (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-botsearch (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-fakegooglebot (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-modsecurity (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-nohome (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-noscript (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-overflows (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-apache-shellshock (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-dropbear (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-named-refused (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-nsd (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-pam-generic (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-php-url-fopen (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-recidive (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-selinux-ssh (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-sshd (2 references)
target     prot opt source               destination
REJECT     all  --  58.187.224.245       anywhere             reject-with icmp-port-unreachable
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-sshd-ddos (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-suhosin (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain f2b-vsftpd (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain ufw-after-forward (1 references)
target     prot opt source               destination


Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination


Chain ufw-after-output (1 references)
target     prot opt source               destination


Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere


Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             xxx.xxx.xxx.xxx          udp dpt:mdns
ACCEPT     udp  --  anywhere             xxx.xxx.xxx.xxx      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination


Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere


Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere


Chain ufw-reject-forward (1 references)
target     prot opt source               destination


Chain ufw-reject-input (1 references)
target     prot opt source               destination


Chain ufw-reject-output (1 references)
target     prot opt source               destination


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-track-forward (1 references)
target     prot opt source               destination


Chain ufw-track-input (1 references)
target     prot opt source               destination


Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     udp  --  anywhere             anywhere             udp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     udp  --  anywhere             anywhere             udp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8443
ACCEPT     udp  --  anywhere             anywhere             udp dpt:8443
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8447
ACCEPT     udp  --  anywhere             anywhere             udp dpt:8447
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:postgresql


Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination


Chain ufw-user-output (1 references)
target     prot opt source               destination
root@localhost:/var/lib/postgresql#
```


Any assistance greatly appreciated.

---

