---
title: "firewall rules aren't preventing traffic"
date: 2015-03-27
forum: Security
---

### Post by brent21 on 2015-03-27
Hello,
  I have a linux computer that is connected to the cloud through a cellular connection, so bandwidth usage is important to me, because I pay for each megabyte.  I appear to be getting a number of port scans hitting my computer and I am unable to block them out through my firewall rules.  I new to working with firewall rules, so I apologize if my terminology is not always correct.  Below is the results of my iptables and a snippet from my syslog.  As you can see the default rule is to drop input traffic, but yet a significant amount is still coming in through the "established" rule.  This is through ports I never want to allow such as 5551 and 60963 and yet somehow traffic is occurring.   I need to have that rule enabled to allow communication to my web site, but yet somehow, somebody is able to create an "established" connection with my computer.  Can you help identify how I can prevent this from happening?  Any help is greatly appreciated.

Brent

```
root@twisthdm:~# iptables -L -v
Chain INPUT (policy DROP 19 packets, 1116 bytes)
 pkts bytes target     prot opt in     out     source               destination
66795   45M LOG        all  --  ppp0   any     anywhere             anywhere             LOG level debug prefix "BANDWIDTH_IN:"
66746   45M ACCEPT     all  --  any    any     anywhere             anywhere             state ESTABLISHED
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere             state RELATED
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:domain dpts:1024:65535
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp echo-reply
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp destination-unreachable
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp source-quench
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp time-exceeded
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp parameter-problem
    6   288 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh
   33  1584 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:9750
    1    48 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:9751
    2    96 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:9752
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:9753
```


```
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  any    ppp0    anywhere             anywhere             LOG level debug prefix "BANDWIDTH_OUT:"
    0     0 LOG        all  --  ppp0   any     anywhere             anywhere             LOG level debug prefix "BANDWIDTH_IN:"
```


```
Chain OUTPUT (policy ACCEPT 74839 packets, 7546K bytes)
 pkts bytes target     prot opt in     out     source               destination
74827 7545K LOG        all  --  any    ppp0    anywhere             anywhere             LOG level debug prefix "BANDWIDTH_OUT:"
```


Syslog
```
Mar 27 02:19:32 twisthdm kernel: [578917.511257] BANDWIDTH_IN:IN=ppp0 OUT= MAC= SRC=67.153.15.5 DST=10.5.153.118 LEN=98 TOS=0x00 PREC=0x00 TTL=120 ID=19808 DF PROTO=TCP SPT=5551 DPT=60963 WINDOW=65489 RES=0x00 ACK PSH URGP=0 
Mar 27 02:19:32 twisthdm kernel: [578917.511365] BANDWIDTH_OUT:IN= OUT=ppp0 SRC=10.5.153.118 DST=67.153.15.5 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=35646 DF PROTO=TCP SPT=60963 DPT=5551 WINDOW=229 RES=0x00 ACK URGP=0 
Mar 27 02:19:32 twisthdm kernel: [578917.511546] BANDWIDTH_OUT:IN= OUT=ppp0 SRC=10.5.153.118 DST=67.153.15.5 LEN=98 TOS=0x00 PREC=0x00 TTL=64 ID=35647 DF PROTO=TCP SPT=60963 DPT=5551 WINDOW=229 RES=0x00 ACK PSH URGP=0 
Mar 27 02:19:32 twisthdm kernel: [578917.681261] BANDWIDTH_IN:IN=ppp0 OUT= MAC= SRC=67.153.15.5 DST=10.5.153.118 LEN=98 TOS=0x00 PREC=0x00 TTL=120 ID=19817 DF PROTO=TCP SPT=5551 DPT=60963 WINDOW=65443 RES=0x00 ACK PSH URGP=0
```

---

### Post by ian-weisser on 2015-03-27
> **brent21 said:**
> 66746   45M ACCEPT     all  --  any    any     anywhere             anywhere             state ESTABLISHED

Yes, you are allowing replies to your outgoing packets. And those look like replies to me.

Use the command 'sudo netstat -tulpn' (among several possible commands) to determine which applications are sending and receiving on those ports.
If you really don't want your applications communicating, then stop them or uninstall them.
If you need more help, just let us know.

---

### Post by brent21 on 2015-04-01
Thank you.  That helped point me in the right direction.

---

### Post by brent21 on 2015-04-24
I eventually discovered that significant amounts of data was transferred on port 80 at random times during the day.  Running netstat -tulpn did not reveal any programs that were using port 80.  I suspect whatever uses the port, does not listen on port 80, but uses port 80 to contact a website periodically to download something.  I modified my firewall settings to reject anything on port 80 before allowing established connections.  This significantly reduced my bandwidth usage, but I still want to discover what was using port 80.  For all I know, there is an important daemon running in the background that needs access to port 80 and I am now blocking it.
  I have used netstat -tulpn and also fuser 80/tcp, but neither of these indicate any activity on port 80.  
  I am looking for a suggestion to try to find out what program is using port 80, so I can either remove it or possible adjust some of its configuration parameters so that it does not access the internet so often.

thanks in advance for any help,
Brent

---

### Post by ian-weisser on 2015-04-24
You're right. 'Port 80' refers to the port on the distant server, not on your machine. Only a webserver should be listening on port 80, and most people don;t run those on their desktop/laptop. Anything using http: , including apt (package) updates, web browsers, geolocation, and other services, communicate on server port 80.

To try and figure out the local applications that is sending data someplace else, see [http://askubuntu.com/questions/252179/how-to-inspect-outgoing-http-requests-of-a-single-application](http://askubuntu.com/questions/252179/how-to-inspect-outgoing-http-requests-of-a-single-application)
Both wireshark and tcpdump are in the Software Center.

---

