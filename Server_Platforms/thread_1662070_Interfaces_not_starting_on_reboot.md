---
title: "Interfaces not starting on reboot"
date: 2011-01-07
forum: Server Platforms
---

### Post by markmid on 2011-01-07
I have been running Ubuntu 8.10 server.  I had not been restarted for several months.  On reboot, the interfaces (lo and eth0) did not restart.  I can start lo with command :

ifconfig lo up

and then restart /etc/init.d/networking

Apache and most services are running OK.  However, I have a perl script that is giving the error:
"connection to localhost failed connection refused"
ping localhost works.

Any ideas why the interfaces are not starting on reboot and why the failed connection to localhost?

---

### Post by NIT006.5 on 2011-01-07
Did eth0 come up when you restarted networking services? Can you post the contents of /etc/network/interfaces, /etc/hosts and the output from 

```

ifconfig -a

```

The connection refused issue seems to imply that a necessary service is not listening on localhost (it doesn't look like its failing to resolve localhost). What port is that script trying to connect to? You could also make sure no strange firewall rules are blocking loopback traffic, but then it would normally time out instead of refusing the connection.

---

### Post by markmid on 2011-01-07
> **NIT006.5 said:**
> Did eth0 come up when you restarted networking services? Can you post the contents of /etc/network/interfaces, /etc/hosts and the output from 

```

ifconfig -a

```

The connection refused issue seems to imply that a necessary service is not listening on localhost (it doesn't look like its failing to resolve localhost). What port is that script trying to connect to? You could also make sure no strange firewall rules are blocking loopback traffic, but then it would normally time out instead of refusing the connection.

eth0 did come up when I restarted networking.  I am not sure what port the script is trying to connect to.  It is using the following perl modules:
use DBI;
use CGI qw(:standard *table :html3);

use Mail::POP3Client;
use MIME::Parser;
use Mail::Sendmail;

I think it is in the POP3Client that it is failing.  Below are the contents of my files:

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.254

cat /etc/hosts
127.0.0.1	localhost
192.168.2.2	prod.forl.com 	prod

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a0:3d:53  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fea0:3d53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1665073 (1.6 MB)  TX bytes:5623647 (5.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8120 (8.1 KB)  TX bytes:8120 (8.1 KB)

---

### Post by NIT006.5 on 2011-01-07
Can't see anything major wrong there, other than there should be a 127.0.1.1 entry in your hosts file for the fqdn of the machine, which to the best of my knowledge can be important for some services. But I doubt that would be causing your issues. You'd have to dig into log files to see what went wrong during boot.

I'm no perl expert, so I'm not familiar with all the modules... but you should probably confirm that all the necessary services are running, that the script might be trying to connect to. Also make sure that any such services are not bound to the LAN address and will in fact accept connections on the loopback interface. You can do quick checks with:

```

nc -zv localhost 25
nc -zv localhost 110

```

for smtp/pop ports, but obviously you need to check the port numbers for any services that the script might be using.

---

### Post by markmid on 2011-01-07
Checking port 25 revealed postfix was not running.  This has corrected my perl script.  Thanks for the input.  

I still do not understand why these services are not starting on reboot.  I have reviewed syslog and messages and it is not apparent to me where the problem is.  Any suggestions?

---

### Post by NIT006.5 on 2011-01-10
Sorry for the delay.

Depending on your version, you may or may not have a /var/log/boot.log file. If you do, this might be a good starting point as you will be able to see if any errors were shown on boot. i.e. if postfix is trying to start and failing. Otherwise, if postfix isn't even trying to start, then you might need to check in the /etc/rcX.d/ directories to see if postfix is listed there. e.g. /etc/rc2.d/S20postfix, /etc/rc3.d/S20postfix, etc. If nothing is listed for postfix, you can have these added by using the update-rc.d command (see 'man update-rc.d' for more info). This obviously also applies to any other services that aren't starting.

Other than that, I don't have any other clever ideas at this point. Absolutely no idea why the interface isn't coming up at boot.

---

