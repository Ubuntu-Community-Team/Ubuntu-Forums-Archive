---
title: "iptables-restore --noflush is not working"
date: 2012-04-23
forum: Server Platforms
---

### Post by dashang.trivedi on 2012-04-23
[b]iptables-restore default behavior is to flush all table and then apply all chain. but there is one option in iptables-restore is --noflush 
> 
iptables-restore --help
Usage: iptables-restore [-b] [-c] [-v] [-t] [-h]
           [ --binary ]
           [ --counters ]
           [ --verbose ]
           [ --test ]
           [ --help ]
           [ --noflush  ]
           [ --table=<TABLE> ]
           [ --modprobe=<command>]

means old rules is not deleted ..
so i have create two file a.txt and b.txt file 

** _ vi a.txt _ **

> 
*mangle
:acctup - [0:0]
:acctdn - [0:0]
-I acctup -s 10.104.1.122 -d 0/0   -j MARK --set-mark 1
-I acctdn -d 10.104.1.122 -s 0/0   -j MARK --set-mark 1
COMMIT
*nat
-A POSTROUTING -s 10.104.1.122 -d 0/0 -j MASQUERADE
COMMIT



** _ vi a.txt _ **

> 
*mangle
:acctup - [0:0]
:acctdn - [0:0]
-I acctup -s 10.104.1.121 -d 0/0   -j MARK --set-mark 1
-I acctdn -d 10.104.1.121 -s 0/0   -j MARK --set-mark 1
COMMIT
*nat
-A POSTROUTING -s 10.104.1.121 -d 0/0 -j MASQUERADE
COMMIT




now when i run  this file with --noflush option . but still its delete all the rules.....


> 

[b]iptables-restore --noflush < a.txt 
iptables -t mangle -L acctup -nvx [/b]
Chain acctup (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 MARK       all  --  *      *       10.104.1.122         0.0.0.0/0           MARK xset 0x1/0xffffffff 


[b]
iptables-restore --noflush < b.txt 
iptables -t mangle -L acctup -nvx [/b]
Chain acctup (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 MARK       all  --  *      *       10.104.1.121         0.0.0.0/0           MARK xset 0x1/0xffffffff 
root@bhushan:/home/bhushan# 



So after run b.txt  iptables-restore --noflush delete all chain ...my ip is change every time...so its dynamic ....

PLEASE TELL ME THE SOLUTION ......how to work in iptables-restore --noflush option.....[/b]

---

### Post by darkod on 2012-04-23
Is there a specific reason you want the --noflush? Usually it's best to flush the rules because that deletes all rules and it applies the rules you have in your file.

In the file you enter all the rules you want to exist, and that's it.

In lots of cases, a left over rule can create big problems for you, so the flush helps a lot.

If you have a problem setting up a specific rule, you can ask for advice about that, not using the --noflush option.

---

