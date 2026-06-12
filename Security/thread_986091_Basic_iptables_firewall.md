---
title: "Basic iptables firewall"
date: 2008-11-18
forum: Security
---

### Post by jerremy-tamlin on 2008-11-18
Hi all,

I ran into a wall (or a dark forest rather, there are no walls in linux) trying to open the right ports to connect to my uni's vpn and network.

I tried using firestarter and guarddog but had no joy, the ports the uni told me I needed to open weren't the only ones that I needed. I thought I'd have a go at going down to a more core level and try manipulating the iptables directly. So I hit the tutorials and docs and learnt enough about iptables to setup a basic firewall. In the process I had to uninstall firestarter because it kept fighting with me and changing the iptables it's self, even when I wasn't starting it.

Anyway I managed to setup the following basic iptables firewall, and it WORKS GREAT! I'm just a little concerned that perhaps it's not very secure.

Can anyone tell me if there are huge holes in it?
```

Laptop:~$ sudo iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2411 80062 ACCEPT     all  --  lo     any     anywhere             anywhere            
 3664 2980K LOG        all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED LOG level debug tcp-sequence tcp-options ip-options uid prefix `iptables-JW ESTABLISHED ' 
 3664 2980K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
  135 17483 LOG        all  --  any    any     anywhere             anywhere            LOG level debug tcp-sequence tcp-options ip-options uid prefix `iptables-JW DROPPED ' 
  135 17483 DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 6110 packets, 696K bytes)
 pkts bytes target     prot opt in     out     source               destination

```
Is there a danger in accepting all outbound traffic or all established/related connections?
This is on a personal laptop that only I use.

Cheers

---

### Post by The Cog on 2008-11-18
Personally, I wouldn't bother with a firewall unless I installed a server fo some kind and knew which IP address ranges I wanted to be able to access it. 

But anyway, that's a good basic config that blocks all incoming connections. I don't think you should be logging every packet that you accept - it'll hurt performance and disk space. Logging rejected pakets shouldn't hurt, but it's a waste unless you plan to look at the logs.

You don't need the final DROP jump - the policy will drop if there isn't another jump for those packets.

---

### Post by Sarmacid on 2008-11-18
> **The Cog said:**
> Personally, I wouldn't bother with a firewall unless I installed a server fo some kind and knew which IP address ranges I wanted to be able to access it. 

But anyway, that's a good basic config that blocks all incoming connections. I don't think you should be logging every packet that you accept - it'll hurt performance and disk space. Logging rejected pakets shouldn't hurt, but it's a waste unless you plan to look at the logs.

You don't need the final DROP jump - the policy will drop if there isn't another jump for those packets.

+1, I wouldn't worry with firewall unless I had some services running.

---

### Post by jerremy-tamlin on 2009-01-07
Thanks for that, the reason I wanted to log accepted packets was because that's what I care about, what get's in, not what gets rejected. I was running Apacke before and didn't have it secured. I think at some point I was connected to my uni's network without a firewall up and I got hacked. Something was using up my internet quota and then when I was investigating it an audio file suddenly played "Oh No! Go Awaaaaaaaaay"

So after a reinstall of everything I'm now back to making sure I'm behind a firewall BEFORE I install apache and also that I have figured out how to prevent it from answering connections from anything besides lo

Cheers

P.S.
Both Firestarter and UFW configure iptables with an
ACCEPT     all  --  anywhere             anywhere
close to the top of the input table/chain.
Can anyone tell me why this doesn't accept anything from anywhere?

---

