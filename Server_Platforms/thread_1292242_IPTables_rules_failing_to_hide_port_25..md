---
title: "IPTables rules failing to hide port 25."
date: 2009-10-15
forum: Server Platforms
---

### Post by rnodal on 2009-10-15
Hello all,

I'm trying to filter all the ports that I don't user but somehow my iptables rules fail to do so.

Here is my rules file:
```

#//////////////////////////////////////////////////////////////////////////////
#
#  Filter table.
#   
#  This is where we do filtering for all incoming traffic destined 
#  for our local host. Note that all incoming packets destined for this
#  host pass through this chain, no matter what interface or in 
#  which direction they came from.
# 
#//////////////////////////////////////////////////////////////////////////////
*filter

#//////////////////////////////////////////////////////////////////////////////
#
# Chains.
#
# A chain specification looks like: 
# :<chain-name> <chain-policy> [<packet-counter>:<byte-counter>] 
# The chain-name may be for example PREROUTING, the policy is described 
# previously and can, for example, be ACCEPT. 
# Finally the packet-counter and byte-counters are the same counters 
# as in the output from iptables -L -v. 
# Finally, each table declaration ends in a COMMIT keyword. 
# The COMMIT keyword tells us that at this point we should commit all 
# rules currently in the pipeline to kernel.
# 
#//////////////////////////////////////////////////////////////////////////////
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

#//////////////////////////////////////////////////////////////////////////////
# My Chains.
#//////////////////////////////////////////////////////////////////////////////

# MyWall
:MyWall - [0:0]

# DROPLOG
:DROPLOG - [0:0]

# SSHD
:SSHD - [0:0]

# HTTP
:HTTP - [0:0]

# HTTPS
:HTTPS - [0:0]

#//////////////////////////////////////////////////////////////////////////////
# Add Rule to INPUT chain that jumps to my chain (MyWall).
#//////////////////////////////////////////////////////////////////////////////
-A INPUT -j MyWall

#//////////////////////////////////////////////////////////////////////////////
# MyWall rules.
#//////////////////////////////////////////////////////////////////////////////

# Allow related, stablished.
#-A MyWall -m state --state RELATED,ESTABLISHED -j ACCEPT
-A MyWall -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT


# Jump to SSHD chain if incoming connection is to SSHD.
-A MyWall -p tcp -m state --state NEW -m tcp --dport 22 -j SSHD

# Anything that does not match gets send to DROPLOG chain.
-A MyWall -j DROPLOG

#//////////////////////////////////////////////////////////////////////////////
# DROPLOG rules.
#//////////////////////////////////////////////////////////////////////////////
-A DROPLOG -m limit --limit 5/min -j LOG --log-prefix "IPTABLES DROP: " --log-level 7
-A DROPLOG -j DROP

#//////////////////////////////////////////////////////////////////////////////
# SSHD rules.
#//////////////////////////////////////////////////////////////////////////////
-A SSHD -j ACCEPT

#//////////////////////////////////////////////////////////////////////////////
# Done!
#//////////////////////////////////////////////////////////////////////////////
COMMIT


```


Here is the output of nmap (nmap -P0 host):

```

Not shown: 998 filtered ports
PORT   STATE  SERVICE
22/tcp open   ssh
25/tcp closed smtp

```

I have read the rules from top to bottom and from bottom to top and I don't see what could be causing this. Maybe I'm missing something
due to my lack of experience with IPTABLES.

Any information, suggestions would be appreciated.

-r

---

