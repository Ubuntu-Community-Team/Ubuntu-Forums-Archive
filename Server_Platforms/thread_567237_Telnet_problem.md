---
title: "Telnet problem"
date: 2007-10-04
forum: Server Platforms
---

### Post by satimis on 2007-10-04
Hi folks,


Ubuntu 7.04 server amd64


I have problem running;

$ telnet vmware_machine_IP 8333```

Trying vmware_machine_IP...
telnet: Unable to connect to remote host: Connection refused
```

$ telnet vmware_machine_IP    ```
 
Trying vmware_machine_IP...
telnet: Unable to connect to remote host: Connection refused

```

Please advise which file shall I check and how to fix the problem?  TIA


B.R.
satimis

---

### Post by kast on 2007-10-04
Satimis sorry for answering a question with a question, but is there a reason why your choosing telnet over a more secure connection like SSH?

Also do you have Firestarter (or any firewall) installed? i know when i setup my SSH access i had to allow connection from the I.P i was connecting from.

---

### Post by satimis on 2007-10-05
> **kast said:**
> Satimis sorry for answering a question with a question, but is there a reason why your choosing telnet over a more secure connection like SSH?

I ran telnet testing the connection.  Because I was unable to connect vmware server on browser by typing "vmware_machine_IP 8333"

> 
Also do you have Firestarter (or any firewall) installed? i know when i setup my SSH access i had to allow connection from the I.P i was connecting from.
Yes, iptables.

Following is the complete script/rules
$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0
#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d MGMT_NIC_IP -m state --state
RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management
interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d MGMT_NIC_IP --reject-with
icmp-port-unreachable


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s MGMT_NIC_IP -m state --state
RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s MGMT_NIC_IP -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with
icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s MGMT_NIC_IP --reject-with
icmp-port-unreachable

```

MGMT_NIC-IP = fixed IP address assigned by ISP.


Ran "sudo iptables -F" to stop firewall.  Still can't telnet.


I forget there is a file governing telnet.  Any advice?


B.R.
satimis

---

