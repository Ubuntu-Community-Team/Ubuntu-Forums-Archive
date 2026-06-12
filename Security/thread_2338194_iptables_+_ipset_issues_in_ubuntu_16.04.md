---
title: "iptables + ipset issues in ubuntu 16.04"
date: 2016-09-25
forum: Security
---

### Post by andrew725 on 2016-09-25
hi all,

I was successfully using iptables and ipset on my old ubuntu 14.04 server to block entire countries from accessing my site.  it seems to work fine on my new ubuntu 16.04 server until I reboot it, then it starts to fail and stops the server from grabbing an IP.  if anyone could lend a hand, that'd be greatly appreciated!

here's my iptable rules that I load (some stuff is obfuscated and the country blocking is commented out so it's not an issue if I need to reboot for now):

```

*filter
  
 #  Allow all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
 -A INPUT -i lo -j ACCEPT
 -A INPUT -d 127.0.0.0/8 -j REJECT
  
 #  Accept all established inbound connections
 -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
  
 # Block China
 #-A INPUT -p tcp -m set --match-set china src -j DROP
  
 # Block Ukraine
 #-A INPUT -p tcp -m set --match-set ukraine src -j DROP
  
 #  Allow all outbound traffic - you can modify this to only allow certain traffic
 -A OUTPUT -j ACCEPT
  
 #  Allow HTTP and HTTPS connections from anywhere (the normal ports for websites and SSL).
 -A INPUT -p tcp --dport 80 -j ACCEPT
 -A INPUT -p tcp --dport 443 -j ACCEPT
  
 # Allow SMTP
 -A INPUT -p tcp --dport 25 -j ACCEPT
  
 #  Allow SSH connections
 #
 #  The -dport number should be the same port number you set in sshd_config
 #
 -A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT
  
 #  Allow ping
 -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
  
 #  Log iptables denied calls
 -A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
  
 #  Drop all other inbound - default deny unless explicitly allowed policy
 -A INPUT -j DROP
 -A FORWARD -j DROP
  
 COMMIT

```

here's my ipset code that downloads the country IPs from ipdeny, removes the rule from iptables and then reloads it:

```

# remove the rule so we can delete the set before importing the new list
 /sbin/iptables -D INPUT -p tcp -m set --match-set china src -j DROP
  
 # remove any existing set
 /sbin/ipset destroy china
  
 # Create the ipset list
 /sbin/ipset -N china hash:net
  
 # remove any old list that might exist from previous runs of this script
 rm /etc/cn.zone
  
 # Pull the latest IP set for China
 wget -P /etc/ http://www.ipdeny.com/ipblocks/data/countries/cn.zone
  
 # Add each IP address from the downloaded list into the ipset 'china'
 for i in $(cat /etc/cn.zone ); do /sbin/ipset -A china $i; done
  
 # Restore iptables
 /sbin/iptables-restore < /etc/iptables.firewall.rules

```

my code that runs during boot up in /etc/network/if-pre-up.d:

```

#!/bin/sh
/sbin/iptables-restore < /etc/iptables.firewall.rules

```

syslog showing the error when booting up:

```

Sep 20 19:07:18 sys sh[768]: iptables-restore v1.6.0: Set china doesn't exist.
 Sep 20 19:07:18 sys sh[768]: Error occurred at line: 11
 Sep 20 19:07:18 sys sh[768]: Try `iptables-restore -h' or 'iptables-restore --help' for more information.
 Sep 20 19:07:18 sys sh[768]: run-parts: /etc/network/if-pre-up.d/firewall exited with return code 2
 Sep 20 19:07:18 sys sh[768]: Failed to bring up enp0s3.
 Sep 20 19:07:18 sys systemd[1]: ifup@enp0s3.service: Main process exited, code=exited, status=1/FAILURE
 Sep 20 19:07:18 sys ifup[844]: iptables-restore v1.6.0: Set china doesn't exist.
 Sep 20 19:07:18 sys ifup[844]: Error occurred at line: 11
 Sep 20 19:07:18 sys ifup[844]: Try `iptables-restore -h' or 'iptables-restore --help' for more information.
 Sep 20 19:07:18 sys ifup[844]: run-parts: /etc/network/if-pre-up.d/firewall exited with return code 2
 Sep 20 19:07:18 sys ifup[844]: /sbin/ifup: pre-up script failed.
 Sep 20 19:07:18 sys systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
 Sep 20 19:07:18 sys systemd[1]: Failed to start Raise network interfaces.
 Sep 20 19:07:18 sys systemd[1]: networking.service: Unit entered failed state.
 Sep 20 19:07:18 sys systemd[1]: networking.service: Failed with result 'exit-code'.
 Sep 20 19:07:18 sys systemd[1]: Reached target Network.

```

---

### Post by bluecafe on 2016-11-02
Hi, did you solve your issue? I have the same problem after restarting my server.

---

