---
title: "ufw absolute wierdness HELP!  (long)"
date: 2021-11-23
forum: Security
---

### Post by emiked on 2021-11-23
I couple of months ago I set up MASQUERADE between two interfaces, and set up 2 port forwards.

Everything was wonderful.

For the last week I've been trying to set up additional port forwards without ANY success.

1) None of the new port forwards work.
2) I even did a 'ufw reset', and added it all back in (/etc/ufw/before.rules)
3) EVEN AFTER THE 'ufw reset' THE OLD PORT FORWARDS STILL WORK!!!
4) EVEN WITH 'ufw disable' (ufw status: Status: inactive) THE OLD PORT FORWARDS STILL WORK!!!
5) With ufw disabled, MASQUERADE stops working (whew) but the original port forwards still work.
6) This continues, even after several reboots.

WTF!!!  How is this even possible??

before.rules:

```
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#
*nat

:PREROUTING ACCEPT [0:0]

-F

-A PREROUTING -i eno1 -p tcp --dport 28936 -j DNAT --to 192.168.2.36:3389
-A PREROUTING -i eno1 -p tcp --dport 28836 -j DNAT --to 192.168.2.36:1433
-A PREROUTING -i eno1 -p tcp --dport 80 -j DNAT --to 192.168.2.31:80
-A PREROUTING -i eno1 -p tcp --dport 443 -j DNAT --to 192.168.2.31:443
-A PREROUTING -i eno1 -p tcp --dport 28931 -j DNAT --to 192.168.2.31:3389
-A PREROUTING -i eno1 -p tcp --dport 28937 -j DNAT --to 192.168.2.37:3389
-A PREROUTING -i eno1 -p tcp --dport 28837 -j DNAT --to 192.168.2.37:1433
-A PREROUTING -i eno1 -p tcp --dport 28938 -j DNAT --to 192.168.2.38:3389
-A PREROUTING -i eno1 -p tcp --dport 28838 -j DNAT --to 192.168.2.38:1433
-A PREROUTING -i eno1 -p tcp --dport 818 -j DNAT --to 192.168.2.32:818
-A PREROUTING -i eno1 -p tcp --dport 29032 -j DNAT --to 192.168.2.32:29032
-A PREROUTING -i eno1 -p tcp --dport 8088 -j DNAT --to 192.168.2.32:8088
-A PREROUTING -i eno1 -p tcp --dport 28932 -j DNAT --to 192.168.2.32:3389
-A PREROUTING -i eno1 -p tcp --dport 28832 -j DNAT --to 192.168.2.32:1433
-A PREROUTING -i eno1 -p tcp --dport 28933 -j DNAT --to 192.168.2.33:3389
-A PREROUTING -i eno1 -p tcp --dport 28833 -j DNAT --to 192.168.2.33:1433
-A PREROUTING -i eno1 -p tcp --dport 4848 -j DNAT --to 192.168.2.34:4848
-A PREROUTING -i eno1 -p tcp --dport 81 -j DNAT --to 192.168.2.34:81

:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -s 192.168.0.0/16 -o eno1 -j MASQUERADE

COMMIT

*filter
```
....

```
# ufw status
Status: inactive
```

```
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
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

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-forward (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination
```

---

### Post by Doug S on 2021-11-23
UFW generated iptables rules can be difficult to follow.

We need to see your iptables nat table rules. Please do "sudo iptables -xvnL" and sudo "iptables -t nat -xvnL" and post the outputs within "CODE" tags (the "#" sign on the tool bar).
Is forwarding enabled? (I assume it is.)

```
doug@s15:~$ [COLOR="#FF0000"]cat /proc/sys/net/ipv4/ip_forward[/COLOR]
1
```

---

### Post by emiked on 2021-11-23
#  iptables -xvnL
```

Chain INPUT (policy ACCEPT 13477 packets, 30237796 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
  390682 194839737 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  390682 194839737 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  360214 171892758 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  359321 171746197 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  359321 171746197 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  359321 171746197 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 240 packets, 15432 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
  921841 428191312 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  921841 428191312 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  862549 343443931 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  862549 343443931 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  862549 343443931 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  862549 343443931 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 10986 packets, 59241446 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
  365377 239428735 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  365377 239428735 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  337769 200495441 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  337769 200495441 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  337769 200495441 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  337769 200495441 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination   

```

iptables -t nat -xvnL
```

Chain PREROUTING (policy ACCEPT 223 packets, 24100 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28936 to:192.168.2.36:3389
       2      120 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28836 to:192.168.2.36:1433
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 to:192.168.2.31:80
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443 to:192.168.2.31:443
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28931 to:192.168.2.31:3389
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28937 to:192.168.2.37:3389
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28837 to:192.168.2.37:1433
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28938 to:192.168.2.38:3389
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28838 to:192.168.2.38:1433
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:818 to:192.168.2.32:818
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:29032 to:192.168.2.32:29032
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8088 to:192.168.2.32:8088
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28932 to:192.168.2.32:3389
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28832 to:192.168.2.32:1433
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28933 to:192.168.2.33:3389
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28833 to:192.168.2.33:1433
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:4848 to:192.168.2.34:4848
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:81 to:192.168.2.34:81
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28934 to:192.168.2.34:22
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28935 to:192.168.2.35:3389
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28835 to:192.168.2.35:1433
       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28922 to:192.168.2.2:22


Chain INPUT (policy ACCEPT 122 packets, 9379 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 28 packets, 3269 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 263 packets, 15197 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      11      698 MASQUERADE  all  --  *      eno1    192.168.0.0/16       0.0.0.0/0           


```

Ok.  I see it. e.g.
```

       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28936 to:192.168.2.36:3389

```

The old port forwarding is the 1st two.  They work.  Even with 'ufw disable'

All the vollowing ones e.g.
```

       0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:28835 to:192.168.2.35:1433

```

Does NOT work (even though direct access to 192.168.2.35:1433 does work).

---

### Post by Doug S on 2021-11-23
It is not obvious what is wrong, at least not to me.

If it were me, what I would do next is run two instances of tcpdump (or wireshark, if you prefer) and watch the packets arrive and depart. On eno1, and for your not working specific example above I would filter by port 28835:

```
sudo tcpdump -tttt -n -i eno1 port 28835
```For other session (interface name unknown, use ???) filter by port 1433:
```
sudo tcpdump -tttt -n -i ??? port 1433
```Do you see the packets arriving and then leaving forwarded? Do you see any reply coming back from 192.168.2.35:1433 and being forwarded back to the original source IP and port? Also watch the packet counters in the "sudo iptables -xvnL" and sudo iptables -t nat -xvnL" commands attempting to trace the route through the tables, if possible (it might not be possible, depending on other traffic loads). This will assist to narrow down the issue.

---

### Post by emiked on 2021-11-24
Thanks. 

Yes yes, ****.  I'm getting senile.  I can watch both interfaces, both on the working port forward (28836 -> 1433) and the non-working port (28836 -> 1433).  I'll try that.

---

### Post by Doug S on 2021-11-24
> **emiked said:**
> I can watch both interfaces, both on the working port forward (28836 -> 1433) and the non-working port (2883[COLOR="#FF0000"]5[/COLOR] -> 1433).

Which you can without even changing tcpdump commands. The port 1433 one stays the same and the other one becomes:

```
sudo tcpdump -tttt -n -i eno1 port 28835 and port 28836
```

---

