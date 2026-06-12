---
title: "iptables help (where can I find IP's that's stored with RECENT)?"
date: 2010-04-18
forum: Security
---

### Post by wconstantine on 2010-04-18
I'm playing around with iptables on Ubuntu 10.04 Beta2.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       tcp  --  anywhere             anywhere            state NEW recent: UPDATE seconds: 30 hit_count: 4 TTL-Match name: SSH side: source tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
```

That's what I got so far. Accoring to iptables man pages: "/proc/net/ipt_recent/* are the current lists of addresses and information about each entry of each list." There's nothing like that there on my Ubuntu installation. There's a file that's called /proc/net/ip_tables_matches. However, it doesn't contain the information I'm looking for. It contains: 
```
udplite
udp
tcp
recent
state
icmp

```

Anyone know where I can find the file where iptables stores the matching IPs? Also, can anyone verify that I have put the rules in the right order for them to work? :)

---

### Post by cdenley on 2010-04-19
I still have 9.10, but my man page gives the correct directory.
> 
/proc/net/xt_recent/*  are  the current lists of addresses and informa&#8208;
       tion about each entry of each list.

       Each file in **/proc/net/xt_recent/** can be read from to see  the  current
       list or written two using the following commands to modify the list:

       echo +addr >**/proc/net/xt_recent/DEFAULT**
              to add addr to the DEFAULT list

       echo -addr >**/proc/net/xt_recent/DEFAULT**
              to remove addr from the DEFAULT list

       echo / >**/proc/net/xt_recent/DEFAULT**
              to flush the DEFAULT list (remove all entries).

The first rule in your INPUT chain accepts everything, so no other rules will ever be processed. Your iptables configuration will do nothing, and all traffic will be accepted.

---

### Post by wconstantine on 2010-04-19
No, that's the rule for the loopback interface only. Should have posted the verbose output, sorry.

> Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  596 66344 ACCEPT     all  --  lo     any     anywhere             anywhere            
29772   36M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            state NEW recent: UPDATE seconds: 30 hit_count: 4 TTL-Match name: SSH side: source tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
 1141  143K DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 6504 packets, 387K bytes)
 pkts bytes target     prot opt in     out     source               destination         
16365 1773K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 


I found the files I was looking for. Right where it was specified. Don't know where I was looking before... Must have been tired or something.

---

### Post by tumandro on 2010-04-21
> **wconstantine said:**
> No, that's the rule for the loopback interface only. Should have posted the verbose output, sorry.



I found the files I was looking for. Right where it was specified. Don't know where I was looking before... Must have been tired or something.

What he was saying is that the default policy for your chains is set to ACCEPT. IE:

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)

This basically makes all the rules you have in there pointless.

---

### Post by jetole on 2011-09-21
I know this is an old thread but if I found it (while looking for something else) then someone else will too so I think this is worth mentioning...

> **tumandro said:**
> What he was saying is that the default policy for your chains is set to ACCEPT. IE:

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)

This basically makes all the rules you have in there pointless.

tumandro, actually that's not what cdenley said at all. He said:
> **cdenley said:**
> The first rule in your INPUT chain accepts everything, so no other rules will ever be processed. Your iptables configuration will do nothing, and all traffic will be accepted.

The policy of a built in chain is not a rule; first, last or in between. cdenley was actually referring to the first rule of his chain and not the policy. He was right because wconstantine didn't post the verbose output, so how it appeared before wconstantine corrected his layout did appear to allow everything in the first rule, policy aside.

Also, and this is only semantics over grammar but the default policy for all built-in chains in all tables is ACCEPT. You can change policy for any built-in chain to one of several different targets but then it would not be the default policy.

tumandro, you're also mistaken about all of his rules being pointless, especially in the INPUT chain which you are referring to. While I would agree that the rules he has in the FORWARD and OUTPUT chain may be pointless, the last rule he has in the INPUT chain matches everything and jumps to the DROP target which is essentially the same thing as changing the policy on the INPUT chain to DROP. Anything which isn't matched to his prior rules input will hit his last rule of DROP and therefor his previous ACCEPT rules do serve a purpose.

wconstantine, while it looks like you are getting the hang of iptables, I think you should look into policies, what they are and how they work. If you change the default policy of the INPUT chain then all packets which do not match a rule in the built-in chains will be sent to the target specified in the policy. So, for example, if you change the policy of INPUT to DROP and then remove the last rule which drops all then, if a packet traverses each rule in the INPUT chain and doesn't match any of the rules, then when it gets to the bottom and has finished the chain, it will be dropped because that will be the policy for the chain.

Also, you have a rule in the FORWARD chain and a rule in the OUTPUT chain which will ACCEPT a packet based on it's previous state but these are the only rules in both of those chains and the policy for both of these chains are ACCEPT so this means that if your packet matches the rule in these chains then it will be sent to ACCEPT but if it doesn't match a rule in these chains then it will still be sent to ACCEPT so either way, the packet is still treated the same.

---

### Post by bodhi.zazen on 2011-09-21
> **jetole said:**
> I know this is an old thread but if I found it (while looking for something else) then someone else will too so I think this is worth mentioning...

Thank you for your post. I was going to say the same thing, then I saw your post.

---

### Post by jetole on 2011-09-22
Guess it's a current thread again :-)

---

### Post by spynappels on 2011-09-22
Just to add that it is often good practice on a remote server to leave the default for the INPUT chain to ACCEPT and make the last rule in the chain "drop everything".

This avoids you being unable to access SSH on a remote host if the IPTables are flushed. It means that if the rules are flushed, the box will accept on all ports and you can access and recreate the required rules. With the default set to DROP, a flush will only allow console access, not remote SSH access, which may become a problem....

This IS from personal experience:redface:

---

