---
title: "IP tables problem."
date: 2009-09-26
forum: Server Platforms
---

### Post by rnodal on 2009-09-26
Hello all,

I recently moved my vps from arch linux to ubuntu and my iptables rules do not work anymore. I was wondering if someone could maybe point me in the right direction.

Here is my rules files.
[PHP]*filter


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
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

#//////////////////////////////////////////////////////////////////////////////
# My Chains.
#//////////////////////////////////////////////////////////////////////////////

# MyWall
:MyWall - [0:0]

# SSHD
:SSHD - [0:0]

#MySQLD
:MySQLD - [0:0]

#//////////////////////////////////////////////////////////////////////////////
# Add Rule to INPUT chain that jumps to my chain (MyWall).
#//////////////////////////////////////////////////////////////////////////////
-A INPUT -j MyWall

#//////////////////////////////////////////////////////////////////////////////
# MyWall rules.
#//////////////////////////////////////////////////////////////////////////////

# Allow related, stablished.
-A MyWall -m state --state ESTABLISHED,RELATED -j ACCEPT

# Jump to SSHD chain if incoming connection is to SSHD.
-A MyWall -m state --state NEW -p tcp -m tcp --dport 22 -j SSHD

# Drop whatever did not match until now.
-A MyWall -j DROP

#//////////////////////////////////////////////////////////////////////////////
# SSHD rules.
#//////////////////////////////////////////////////////////////////////////////
-A SSHD -j ACCEPT

#//////////////////////////////////////////////////////////////////////////////
# Done!
#//////////////////////////////////////////////////////////////////////////////
COMMIT
[/PHP]

I soon as I do an iptables-restore I cannot log in via ssh any more. Any hint to what may be causing this would be welcome. Thank you,

-r

---

### Post by rnodal on 2009-09-26
I don't know what I did other than after flushing the rules, added a rule to log dropped packages and reloaded all the rules and everything worked.
Thanks.

-r

---

