---
title: "Basic IPtables rules for Ubuntu Desktop"
date: 2009-09-14
forum: Security
---

### Post by nick1 on 2009-09-14
Hi,

I have Ubuntu 8.x Desktop installed on a laptop and want to use IPtables to setup a basic firewall.
The firewall should be designed to handle the following:

- laptop will be used on either a private LAN or public network
- laptop will switch between wired and wireless network
- no server services will be running (HTTPD, FTP, etc.)

I think I've got my IPtables rules ready but I'd like to get some opinions on them first.
Feel free to constructively critique them. Thanks!


IPtables Rules
--------------

```
# Establish some variables:

# Location of IPTABLES on your system
IPTABLES="/sbin/iptables"


# SETUP:

# Flush active rules and custom tables
$IPTABLES --flush
$IPTABLES -t nat --flush
$IPTABLES -t mangle --flush

$IPTABLES --delete-chain
$IPTABLES -t nat --delete-chain
$IPTABLES -t mangle --delete-chain

# Give free reign to the loopback interfaces, i.e. local processes may connect
# to other processes' listening-ports.
$IPTABLES -A INPUT  -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT

# Set default policies for all chains.
# User-defined chains cannot be assigned default policies.
# NAT and mangle tables use default ACCEPT policies.
# DROP in nat table is prohibited in newer iptables.
# DROP in mangle table creates hassle.
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -P OUTPUT ACCEPT


# INBOUND POLICY:

# Accept inbound packets that are part of previously-OK'ed sessions
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Log and drop anything not accepted above
$IPTABLES -A INPUT -j LOG --log-prefix "Dropped by default (INPUT):"


# OUTBOUND POLICY:
# Allow all outbound traffic.


# Log & drop ALL incoming packets destined anywhere but here.
$IPTABLES -A FORWARD -j LOG --log-prefix "Attempted FORWARD? Dropped by default:"
```


--- end ----

---

### Post by ajgreeny on 2009-09-14
I think for the uses you are putting the machine to, you really could have left the system as it was at install.  Any programs you open that need network/internet access would get it by default, but nothing would be open except for those, and no server or other utilities would be listening, nor open, to allow incoming access to your machine.  Only if you are running a server of some kind, which by default must let incoming traffic be acted upon, would you need to make any changes to the default setup.

---

### Post by The Cog on 2009-09-15
> **nick1 said:**
> - no server services will be running (HTTPD, FTP, etc.)


Then you don't need a firewall. Any incoming connections don't have anything to connect to so there's nothing to protect from the Bad Guys.

Actually, even if you were to install (frinstance) an HTTP server, you still don't have any use for a firewall. It would block incoming HTTP requests, so you would have to configure it to let them through again. 

A firewall would only be useful if you had a clear idea that you want to block some IP addresses from you server and permit others. Now in that case, you can configure a firewall and tell it to allow **these** calling addresses through and no others.

The reason you need a firewall on windows is that it's so damn hard to stop it from running lots of services that listen for incoming connections, and of course each of those services is a potential hack point.

---

