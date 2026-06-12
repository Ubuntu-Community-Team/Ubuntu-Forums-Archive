---
title: "ufw doesn't open ports"
date: 2010-07-06
forum: Security
---

### Post by judoka1113 on 2010-07-06
when i enable my ufw it completely shuts me out and closed my internet connection.  i installed firewall configuraiton interface and through it defined rules to accept incoming internet connections on port 80, i can see the rules are there but when i enable my firewall it just shuts me out completely again.
when i do(with my firewall enabled):
```
$ sudo ufw status
```
it gives me:
> Status: active

To                         Action      From
--                         ------      ----
80                         ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere

but shuts me out completely so i can't surf the net
in order to surf the net i have to disable my ufw
What is going on? Shouldn't i have internet access even
if my firewall is enabled? Isn't that what the rules are for.
P.S.
I also messed around with fwbuilder and iptables but since then deleted fwbuilder(besides i just compiled firewall policy and never actually installed it because of errors while trying to install it.  Iptables I cleared with:
```
$ sudo iptables -F
```
So can someone give me some advice on the firewall problem that i have? Thanks.

---

### Post by CharlesA on 2010-07-06
Check the configuration of ufw by using gufw.

It shouldn't block access when enabled, since it would allow established and related connections by default.

---

### Post by judoka1113 on 2010-07-06
How do i do that?

---

### Post by CharlesA on 2010-07-06
> **judoka1113 said:**
> How do i do that?
Install gufw from software center.

Then launch it by hitting Alt+F2 and typing gufw

---

### Post by judoka1113 on 2010-07-06
I have it installed, but i don't know how to check its configuration.

---

### Post by CharlesA on 2010-07-06
Incoming should be blocked, outgoing should be allowed.

---

### Post by bodhi.zazen on 2010-07-07
Please do not start multiple threads on the same topic. It causes duplication of effort.

I can not replicate the behavior you describe and you have installed at least two tools to configure your firewall, ufw and fwbuilder.

Both of these are tools to configure iptables and somewhere along the line you have broke something.

My general comments are :

No offence, but you do not seem to understand how a firewall works. Opening port 80 to incoming traffic does not allow you to surf the internet, it allows other to connect to your box (assuming you are running Apache or another web server, which you are not).

I suggest you stop and look at how a firewall works. 

Answer this question , when you "surf" the internet, what port on your computer is connection to what port on the server ?

The vast majority of Desktop users do not need a firewall as there are no listening servers (no open ports).

If you wish to enable your firewall, on a fresh install, open a terminal and run:

```
sudo ufw enable
```

Try it with any live CD.

I have no idea how to fix your system, you will need to remove everything you have installed to configure your firewall and probably remove and re-install ufw.

If you want to try to figure out why you can not surf the web you need to post

```
sudo ufw status verbose
sudo iptables -L -v -n
```

The problem is that the second command is likely to be quite verbose ...

And you need to enable logging and watch /var/log/messages to see what is blocked exactly.

---

### Post by judoka1113 on 2010-07-07
when i do $ sudo ufw status verbose 
i get:```
Chain INPUT (policy DROP 14 packets, 2219 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 14 packets, 934 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
    0     0 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
    0     0 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID limit: avg 3/min burst 10 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by judoka1113 on 2010-07-07
and for $ sudo ufw status verbose \i get:
> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
80                         ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere


but the question that bothers me the most now is this:
i made a firewall policy with fwbuilder but when i try to install this policy it asks me to enter the password
i put my sudo password and it doesn't work.  How and where do i set it up so i can install my policy?

---

### Post by judoka1113 on 2010-07-07
I finally figured it out.
Can you let me know if these rules that i set up with fw builder are good for just surfing the net while being protected?
I have them set up and have an internet connection, i just don't know how secure they are, and would appreciate your opinion.
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
In_RULE_0  all  --  192.168.0.194        anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-transit state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-reassembly state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 8 code 0 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW 
ACCEPT     all  --  192.168.0.194        anywhere            state NEW 
RULE_4     all  --  anywhere             anywhere            state NEW 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
In_RULE_0  all  --  192.168.0.194        anywhere            state NEW 
RULE_4     all  --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state NEW 
Cid2676X14506.0  all  --  anywhere             192.168.0.194       state NEW 
ACCEPT     all  --  anywhere             anywhere            state NEW 
RULE_4     all  --  anywhere             anywhere            state NEW 

Chain Cid2676X14506.0 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-transit 
ACCEPT     icmp --  anywhere             anywhere            icmp ttl-zero-during-reassembly 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp type 8 code 0 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain In_RULE_0 (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `RULE 0 -- DENY ' 
DROP       all  --  anywhere             anywhere            

Chain RULE_4 (3 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `RULE 4 -- DENY ' 
DROP       all  --  anywhere             anywhere       
```

---

### Post by spynappels on 2010-07-07
As far as I can see, those rules would be very relaxed, not actually blocking anything. You do not appear to have understood what Bodhi has said about firewalls on desktop machines, and the rules you have written almost amount to having no firewall at all. 

I suggest you read Bodhi's sticky on firewalls again.

---

### Post by CharlesA on 2010-07-07
Like bodhi.zazen has said, you don't really need a firewall on a desktop machine, as there are no listening services by default. The rules you have created would not block any connections at all.

Please remove fwbuilder and ufw/gfw from a terminal like so:

```
sudo apt-get purge fwbuilder ufw gufw
```

Then reboot and post what the output of this:

```
sudo iptables -L
```

It *should* say "Policy ACCEPT" for everything.

---

### Post by judoka1113 on 2010-07-07
here it is:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
and i have a question that really buggs me.  I wrote a policy form my firewall with fwbuilder
it compiles fine, but when i use the installer ti gives me this:
>   p, li { white-space: pre-wrap; }  scp: /etc/fw/tmp/: Is a directory
 SSH session terminated, exit status: 1

I set-up fwadmin to manage the account and set up the password, I just can't install it.
Do you know what the problem is?

---

### Post by CharlesA on 2010-07-07
Don't use fwbuilder or fwadmin for creating firewall rules. Just use guwf.

It looks like you got rid of the problem rules so install ufw and gufw like so:

```
sudo apt-get install ufw gufw
```

You can then run gufw from Alt+F2 and add rules as needed from there, but it blocks incoming connections and allows outgoing ones by default. It is easier to configure the rules using GUFW imo.

---

