---
title: "Error when starting DHCP server"
date: 2016-02-02
forum: Server Platforms
---

### Post by cody30 on 2016-02-02
I'm getting a semicolon error when I start isc-dhcp-server

My dchpd.conf file
```
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;


# option definitions common to all supported networks...
option domain-name "mydebian";
option domain-name-servers 192.168.1.100, 8.8.4.4;


default-lease-time 600;
max-lease-time 7200;


INTERFACES="eth1"

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.101 192.168.1.254;
   option subnet-mask 255.255.255.0;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
   option routers 192.168.1.100;
   option broadcast-address 192.168.1.255;
#  default-lease-time 600;
#  max-lease-time 7200;
}




```

As is, I get the error below.  It says line 30, but I've cut out a lot of comments for this post.  It's the line that has "log-facility local7;".  For fun, I tried commenting it out since the default comment just above the line says the syslog.conf needs to be hacked to complete the redirection.  Because I didn't do that, I thought I could comment this line out.  
```
Feb  2 06:34:49 ubuntu dhcpd: /etc/dhcp/dhcpd.conf line 30: semicolon expected.
Feb  2 06:34:49 ubuntu dhcpd: log-facility
Feb  2 06:34:49 ubuntu dhcpd: ^
Feb  2 06:34:49 ubuntu dhcpd: Configuration file errors encountered -- exiting

```

After commenting out with #log-facility local7; I get the following error
```
Feb  2 06:51:14 ubuntu dhcpd: /etc/dhcp/dhcpd.conf line 55: semicolon expected.
Feb  2 06:51:14 ubuntu dhcpd: subnet
Feb  2 06:51:14 ubuntu dhcpd: ^
Feb  2 06:51:14 ubuntu dhcpd: Configuration file errors encountered -- exiting

```

I've checked several example dhcpd.conf files and none of them have a semicolon on the first line of the subnet deceleration.  Not even the example inside the dhcpd.conf file had a semicolon on that line!  Anybody know what's going on?

I'm running 14.04 Desktop inside VMware player.  I have two NICs attached.  One is bridged to the hosts ethernet adapter (eth0) the other is lan segment (eth1).  Eth1 is what I want the DHCP server to run on.

---

### Post by darkod on 2016-02-02
Actually the line number might mean the next statement (line) after the mistake (missing semicolon). So you might need to look above. For example, shouldn't the line:
INTERFACES="eth1"

end with a semicolon? I don't see it in your posted code.

---

### Post by cody30 on 2016-02-02
I knew it was going to be something dumb.  It's working now!  Thanks. Just for future reference, is the reason for 'log facility' showing up below the error message because it's the next line following the INTERFACES="eth1" in the dhcpd.conf?

---

### Post by darkod on 2016-02-02
I can't claim for sure, but I believe the missing semicolon makes the program to continue reading the lines, and the 'log facility' is the next uncommented line. Once it read it, it knows it doesn't belong with the 'interface' command and reports an error.

Don't forget, in linux config files new lines and Enter mean nothing. Options can span over multiple lines. That's why some programs need a symbol like a semicolon to know where a command ends. A missing semicolon makes the program think the next line is also part of the previous.

In this situations, the error report is little misleading because it mentioned the next line, not where the error is. But that is not always the rule, many error messages actually point you to the line where the error is. So you have to do both when troubleshooting. Look at the line it reports, and little above it.

---

