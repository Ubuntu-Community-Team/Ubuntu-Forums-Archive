---
title: "Having Trouble Forwarding Traffic With Iptables"
date: 2011-07-02
forum: Server Platforms
---

### Post by mjhasbach on 2011-07-02
Hey all, I have a VPS running Ubuntu 11.04, and I'm trying to forward incoming traffic on port 7777 from that VPS to a different IP address.

I originally asked this question at HowToForge and the person who was helping me recommended that I post here. [Here's the link]("http://www.howtoforge.com/forums/showthread.php?t=53228").

Here's what I've tried and the error that I received:

#1
```
root@xx:~# iptables --list -n -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  0.0.0.0/0            x.x.x.x     tcp dpt:7777 to:x.x.x.x:7777
DNAT       tcp  --  0.0.0.0/0            x.x.x.x     tcp dpt:7777 to:x.x.x.x:7777

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
*Accidentally had the rule in there twice from earlier testing


#2
```
root@xx:~# iptables -t nat -F PREROUTING
root@xx:~# iptables -t nat -F POSTROUTING
```

#3
```
root@xx:~# iptables -t nat -A PREROUTING -p tcp -d x.x.x.x --dport 7777 -j DNAT --to x.x.x.x:7777
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -j MASQUERADE
**iptables: No chain/target/match by that name.**
```

#4
```
root@xx:~# iptables --list -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             x.x.x.x     tcp dpt:7777 to:x.x.x.x:7777

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


x.x.x.x represents the correct IP addresses in the preceding quotes. It's also worth mentioning that in the game client, when I type the domain and port to connect to, it resolves the IP address of my Ubuntu box and not the IP that I want to forward the traffic to.


Thanks in advance.

---

### Post by Dangertux on 2011-07-02
K edited since I boffed it the first time. 

Try adding a
 -o interface

On the masquerade postrouting line

---

### Post by mjhasbach on 2011-07-02
Thanks for the quick reply.

```
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -j MASQUERADE -o interface
iptables: No chain/target/match by that name.
```

---

### Post by Dangertux on 2011-07-02
> **mjhasbach said:**
> Thanks for the quick reply.

```
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -j MASQUERADE -o interface
iptables: No chain/target/match by that name.
```

The interface is meant to be a variable for the interface the traffic is being nat'ed through like eth0 or ppp0


Check this out it explains it better then I can on my phone. 
[http://www.ibiblio.org/pub/linux/docs/HOWTO/other-formats/html_single/Masquerading-Simple-HOWTO.html](http://www.ibiblio.org/pub/linux/docs/HOWTO/other-formats/html_single/Masquerading-Simple-HOWTO.html)

---

### Post by mjhasbach on 2011-07-02
I have four interfaces:

```
root@xx:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7771826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7771826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1454127178 (1.4 GB)  TX bytes:1454127178 (1.4 GB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:3750559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4244972 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:577253895 (577.2 MB)  TX bytes:958687132 (958.6 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:x.x.x.x  P-t-P:x.x.x.x  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:1  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:x.x.x.x  P-t-P:x.x.x.x  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
```


Not sure which one is the proper one to use when adding the iptable rule. I'm guessing venet0:0, because its "inet addr" is the IP address that needs the traffic forwarded.

Regardless, that doesn't matter too much at this point, because adding the iptable rule fails regardless of which interface I choose:


```
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -o lo -j MASQUERADE
iptables: No chain/target/match by that name.
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -o venet0 -j MASQUERADE 
iptables: No chain/target/match by that name.
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -o venet0:0 -j MASQUERADE 
iptables: No chain/target/match by that name.
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -o venet0:1 -j MASQUERADE 
iptables: No chain/target/match by that name.
```


I'll read that article though and see if it will point to a solution.

---

### Post by HermanAB on 2011-07-04
Howdy,

Read the iptables man page about five times - it will eventually make some sense - really.  It has a redirect command.

Otherwise, use socat.

---

### Post by mjhasbach on 2011-07-04
I ended up simply using socat, because I couldn't get iptables working as intended. Thanks a lot for the recommendation HermanAB, I was not aware of the existence of socat until you mentioned it.

For anyone who's interested in my solution:

```
apt-get install socat
socat TCP-LISTEN:7777,fork TCP:x.x.x.x:7777
```
It really was _that easy_, however, it acts as a foreground process (terminates when exiting SSH).

For whatever reason, running it as a background process using the following two methods _did not work_ after exiting SSH:

```
socat TCP-LISTEN:7777,fork TCP:x.x.x.x:7777 &
```
```
socat TCP-LISTEN:7777,fork TCP:x.x.x.x:7777
(Ctrl-Z)
bg
(Enter)
```

So, I ended up running it in a screen session, which worked:

```
screen -S SOCAT1 socat TCP-LISTEN:7777,fork TCP:x.x.x.x:7777
```

Obviously the disadvantage here is, if the server reboots or if the process is otherwise terminated, it will be gone until it is brought back manually.

It would be nice if there was a way to have socat running as a service with "rules" like iptables that are always applied. What I'll probably end up doing is writing an init.d script that launches the above socat command at boot.

I'm hesitant to mark this thread as solved, as the iptables problem hasn't really been fixed. I read the man pages for iptables, and a solution didn't really jump out at me. I did some net research, and it seems my iptables problem *may* be caused by missing modules.

Here's the output of lsmod:

```
root@xx:~# lsmod
Module                  Size  Used by
```

This seems to indicate that I don't have any modules installed? I don't know how to add modules for iptables, but will do some more research. It apparently may involve compiling a new Linux kernel, which is something that I have no experience with and may cause issues in my case because I'm operating in an OpenVZ environment.

Further suggestions are welcome.

---

### Post by mjhasbach on 2011-07-07
For those of you that are interested, I managed to solve this myself.

Apparently, "ipt_MASQUERADE," the module that makes masquerading possible, is not (yet?) available in OpenVZ. The absence of this module is what causes the following command to fail:

```
root@xx:~# iptables -t nat -A POSTROUTING -d x.x.x.x -j MASQUERADE
**iptables: No chain/target/match by that name.**
```

I discovered that it was still possible to accomplish my goal, only that an alternate second command was required. So here's what I did.

1. Cleared out existing nat PREROUTING and POSTROUTING rules from earlier testing.
```
root@xx:~# iptables -t nat -F PREROUTING
root@xx:~# iptables -t nat -F POSTROUTING
```

2. Added the following two rules:
```
root@xx:~# iptables -t nat -A PREROUTING -p tcp -d x.x.x.x --dport 7777 -j DNAT --to y.y.y.y:7777
root@xx:~# iptables -t nat -A POSTROUTING -j SNAT --to-source x.x.x.x
```
*Where x.x.x.x represents the source IP and y.y.y.y represents the destination IP.

3. Saved iptables (necessary for changes to persist after reboot)
```
root@xx:~# iptables-save
```


Hope this helps someone...I know it would have helped me.

---

### Post by Rakeshvijayan on 2011-07-17
[http://ilconnettivo.wordpress.com/2011/02/20/virtualbox-4-nat-bridged-networking/](http://ilconnettivo.wordpress.com/2011/02/20/virtualbox-4-nat-bridged-networking/)

---

### Post by HermanAB on 2011-07-18
Yeah, I've used socat in the past when faced with the problem of replacing an old server with a new one and the DNS still points to the old one for a few days, so then I left the old server up just running socat and redirecting to the new one.  

The iptables redirect rule should do it, but it is also dependent on actually having the right module available and on my old servers, that was not the case - same kind of problem the OP ran into with masquerade.

---

