---
title: "ufw logfile inside lxc container and unbound"
date: 2020-01-13
forum: Security
---

### Post by pimandos on 2020-01-13
Hi,

ufw, running inside an unprivileged container, block all kinds of traffic on my 18.0.4 Server.

Host and container have each a public IP address, Macvlan is used for the container.
[I]
ufw reset[/I] does leave things behind that are seen in iptables -L
Created a file reset-iptables.asc
```
# Empty the entire filter table
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
COMMIT
```
which i use, 
*iptables-restore < reset-iptables.asc *
to reset iptables.

Every time i do, *ufw enable*, all outgoing traffic is blocked even though 
*ufw status verbose*
writes that Outgoing is allowed and no rules are listed.
*apt update* does not work.

The fact that i can ping IPs and get a reply hints that it should be DNS related.
Outgoing was allowed so DNS should work?
I am running unbound 1.6.7 and it is listening on port 0.0.0.0:53
The unbound log file i created shows activity when i disable the Firewall.

I tried,
[I]ufw allow in from 127.0.0.1 to any port 53
ufw allow out from 127.0.0.1 to any port 53[/I]
without luck.

relevant config files:

*cat /etc/ufw/ufw.conf*
```
# /etc/ufw/ufw.conf
#

# Set to yes to start on boot. If setting this remotely, be sure to add a rule
# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
ENABLED=no

# Please use the 'ufw' command to set the loglevel. Eg: 'ufw logging medium'.
# See 'man ufw' for details.
LOGLEVEL=low

```
(ufw is disabled atm therefore ENABLED=no)

*cat /etc/ufw/sysctl.conf*
```
# Uncomment this to allow this host to route packets between interfaces
#net/ipv4/ip_forward=1
#net/ipv6/conf/default/forwarding=1
#net/ipv6/conf/all/forwarding=1

# Disable ICMP redirects. ICMP redirects are rarely used but can be used in
# MITM (man-in-the-middle) attacks. Disabling ICMP may disrupt legitimate
# traffic to those sites.
net/ipv4/conf/all/accept_redirects=0
net/ipv4/conf/default/accept_redirects=0
#net/ipv6/conf/all/accept_redirects=0
#net/ipv6/conf/default/accept_redirects=0

# Ignore bogus ICMP errors
net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/icmp_echo_ignore_all=0

# Don't log Martian Packets (impossible addresses)
# packets
net/ipv4/conf/all/log_martians=0
net/ipv4/conf/default/log_martians=0

#net/ipv4/tcp_fin_timeout=30
#net/ipv4/tcp_keepalive_intvl=1800

# Uncomment this to turn off ipv6 autoconfiguration
net/ipv6/conf/default/autoconf=1
net/ipv6/conf/all/autoconf=1

# Uncomment this to enable ipv6 privacy addressing
#net/ipv6/conf/default/use_tempaddr=2
#net/ipv6/conf/all/use_tempaddr=2

```
(ipv6 is disabled)

*cat /etc/ufw/ufw.conf*
```
# /etc/default/ufw
#

# Set to yes to apply rules to support IPv6 (no means only IPv6 on loopback
# accepted). You will need to 'disable' and then 'enable' the firewall for
# the changes to take affect.
IPV6=no

# Set the default input policy to ACCEPT, DROP, or REJECT. Please note that if
# you change this you will most likely want to adjust your rules.
DEFAULT_INPUT_POLICY="DROP"

# Set the default output policy to ACCEPT, DROP, or REJECT. Please note that if
# you change this you will most likely want to adjust your rules.
DEFAULT_OUTPUT_POLICY="DROP"

# Set the default forward policy to ACCEPT, DROP or REJECT.  Please note that
# if you change this you will most likely want to adjust your rules
DEFAULT_FORWARD_POLICY="DROP"

# Set the default application policy to ACCEPT, DROP, REJECT or SKIP. Please
# note that setting this to ACCEPT may be a security risk. See 'man ufw' for
# details
DEFAULT_APPLICATION_POLICY="SKIP"

# By default, ufw only touches its own chains. Set this to 'yes' to have ufw
# manage the built-in chains too. Warning: setting this to 'yes' will break
# non-ufw managed firewall rules
MANAGE_BUILTINS=no

#
# IPT backend
#
# only enable if using iptables backend
IPT_SYSCTL=/etc/ufw/sysctl.conf

# Extra connection tracking modules to load. Complete list can be found in
# net/netfilter/Kconfig of your kernel source. Some common modules:
# nf_conntrack_irc, nf_nat_irc: DCC (Direct Client to Client) support
# nf_conntrack_netbios_ns: NetBIOS (samba) client support
# nf_conntrack_pptp, nf_nat_pptp: PPTP over stateful firewall/NAT
# nf_conntrack_ftp, nf_nat_ftp: active FTP support
# nf_conntrack_tftp, nf_nat_tftp: TFTP support (server side)
# nf_conntrack_sane: sane support
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_netbios_ns"

```

*cat /etc/unbound/unbound.conf*
```
server:
prefetch: yes
qname-minimisation: yes
# Rewrite URLs written in CAPS
use-caps-for-id: yes
statistics-interval: 600
statistics-cumulative: yes
root-hints: "/etc/unbound/root.hints"
# Hide DNS Server info
hide-identity: yes
hide-version: yes
# Add an unwanted reply threshold to clean the cache and avoid when possible a DNS Poisoning
unwanted-reply-threshold: 10000
# Enable logs
chroot: ""
#verbosity (log level from 0 to 4, 4 is debug)
verbosity: 0
logfile: /var/log/unbound.log
log-queries: yes
#use-syslog: (do not write logs in syslog file in ubuntu /var/log/syslog -zaib)
use-syslog: no
#interface (interfaces on which Unbound will be launched and requests will be listened to)
# Respond to DNS requests on all interfaces
interface: 0.0.0.0
# DNS request port, IP and protocol
port: 53
do-ip4: yes
do-ip6: no
do-udp: yes
do-tcp: yes
# Authorized IPs to access the DNS Server / access-control (determines whose requests are allowed to be processed)
access-control: 127.0.0.0/8 allow
# Improve the security of your DNS Server (Limit DNS Fraud and use DNSSEC)
harden-glue: yes
harden-dnssec-stripped: yes
# TTL Min (Seconds, I set it to 7 days)
cache-min-ttl: 604800
# TTL Max (Seconds, I set it to 14 days)
cache-max-ttl: 1209600

```

How do i enable rsyslog to log ufw?
The command, ufw logging medium, does nothing.

---

### Post by pimandos on 2020-01-15
if i cannot run ufw / iptables in a lxc container due to no access to kernel what other fw options do i have?

---

