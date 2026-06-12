---
title: "Bypass VPN for some URLs"
date: 2017-10-04
forum: Server Platforms
---

### Post by mc-rpg on 2017-10-04
I want to know if there is a way to bypass the VPN for traffic directed to certain urls. I'm using openvpn with network manager. Ubuntu 16.04.

---

### Post by SeijiSensei on 2017-10-04
By URL? No. But you can write routing rules for specific destination IP addresses. Suppose you wanted to connect directly to 10.10.10.10, and your router has address 192.168.1.1. Then you could add this route 

```
sudo ip route add 10.10.10.10 via 192.168.1.1
```

Now traffic for 10.10.10.10 will go out over the Internet rather than through the VPN.

---

### Post by mc-rpg on 2017-10-04
IPs yes, ultimately that's what I meant. If an url example.com resolves to 10.10.10.10 then, after adding this rule, browsing that url will bypass the VPN? Also, will this route persist after a restart? Thanks.

---

### Post by SeijiSensei on 2017-10-04
Yes, that rule tells the machine to send packets for 10.10.10.10 to the router (in this case, 192.168.1.1) rather than sending them upstream over the VPN tunnel.

To make the ruleset persistent, put the rules into /etc/rc.local, which is the last script run at boot.  Remove the "sudo" from any such rules as /etc/rc.local is run with root privileges automatically.  If you have a lot of rules, you might want to put them in a script (say, /usr/local/sbin/routing_rules) and invoke that script in /etc/rc.local.

---

### Post by mc-rpg on 2017-10-04
> **SeijiSensei said:**
> To make the ruleset persistent, put the rules into /etc/rc.local, which is the last script run at boot.  Remove the "sudo" from any such rules as /etc/rc.local is run with root privileges automatically.  If you have a lot of rules, you might want to put them in a script (say, /usr/local/sbin/routing_rules) and invoke that script in /etc/rc.local.

That didn't work. Doing the commands by themselves work but once I modified rc.local to include them and restarted, a traceroute reveals that the routes aren't in effect. I'm on ubuntu 16.04 btw.

---

### Post by wildmanne39 on 2017-10-04
*Thread moved to **Server Platforms for a better fit.**.*

---

### Post by SeijiSensei on 2017-10-05
Let's see the contents of /etc/rc.local.  You did omit the "sudo" from each rule, right?  Also try using the full path to ip, /sbin/ip, if you have not done so.

---

### Post by mc-rpg on 2017-10-21
> **SeijiSensei said:**
> Let's see the contents of /etc/rc.local.  You did omit the "sudo" from each rule, right?  Also try using the full path to ip, /sbin/ip, if you have not done so.

Here it is, I modified it after your comment but I still haven't been able to persist the routes.

```
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

#/usr/local/sbin/vpn_bypassing_rules.sh
/sbin/ip route add XXX.XX.0.0/16 via XXX.XX.75.254	
/sbin/ip route add XX.XX.134.178 via XXX.XX.75.254	
/sbin/ip route add XXX.XX.21.43 via XXX.XX.75.254 	

exit 0
```

---

### Post by SeijiSensei on 2017-10-22
See any errors reported in /var/log/syslog when these commands are run?

Can the system see XXX.XX.75.254 at the end of the boot sequence?  If you're relying on NetworkManager, the network may not be up at the end of boot but only start after you log in.  In any complicated network arrangement, I prefer to run everything manually with entries in /etc/network/interfaces.  Then the network will be started early in the boot sequence.  See the sections on DHCP and static assigments here: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/lts/serverguide/network-configuration.html#ip-addressing)

---

### Post by mc-rpg on 2017-10-30
> **SeijiSensei said:**
> See any errors reported in /var/log/syslog when these commands are run?

Can the system see XXX.XX.75.254 at the end of the boot sequence?  If you're relying on NetworkManager, the network may not be up at the end of boot but only start after you log in.  In any complicated network arrangement, I prefer to run everything manually with entries in /etc/network/interfaces.  Then the network will be started early in the boot sequence.  See the sections on DHCP and static assigments here: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/lts/serverguide/network-configuration.html#ip-addressing)

I didn't see the route commands themselves being executed but I got this from the rc.local service:
```
Oct 30 09:54:03 laptop systemd[1]: Starting /etc/rc.local Compatibility...
Oct 30 09:54:03 laptop systemd[1]: Started Daily apt download activities.
Oct 30 09:54:03 laptop systemd[1]: Started Daily apt upgrade and clean activities.
Oct 30 09:54:03 laptop systemd[1]: Reached target Timers.
Oct 30 09:54:03 laptop rc.local[1384]: RTNETLINK answers: Network is unreachable
Oct 30 09:54:03 laptop systemd[1]: rc-local.service: Control process exited, code=exited status=2
Oct 30 09:54:03 laptop systemd[1]: Failed to start /etc/rc.local Compatibility.
Oct 30 09:54:03 laptop systemd[1]: rc-local.service: Unit entered failed state.
Oct 30 09:54:03 laptop systemd[1]: rc-local.service: Failed with result 'exit-code'.
```

Do I need to scape any command in the rc.local file? I am relying on network manager, which I think it's the default behavior in ubuntu. 

Kind of offtopic: Is there be a way to execute the route commands right after I connect to my vpn by any chance?

---

### Post by LHammonds on 2017-10-30
I rely heavily on root's crontab (which may not be the best thing to do but it is great visibility).

You could create a bash script to execute those commands and add an entry into root's crontab schedule to execute them whenever the system boots up.   If you need an artificial delay, you could just add a sleep command just before it.

Example: route-rules.sh
```

#!/bin/bash
## Pause script for 60 seconds. ##
/bin/sleep 60
## Add routing rules ##
/sbin/ip route add XXX.XX.0.0/16 via XXX.XX.75.254
/sbin/ip route add XX.XX.134.178 via XXX.XX.75.254
/sbin/ip route add XXX.XX.21.43 via XXX.XX.75.254

```

Switch into the root crontab:
```
sudo su
crontab -e
```

Add an entry that will execute the script after each reboot:
```
@reboot  /path/to/route-rules.sh
```

LHammonds

---

### Post by SeijiSensei on 2017-10-30
> **mc-rpg said:**
> Oct 30 09:54:03 laptop rc.local[1384]: RTNETLINK answers: Network is unreachable

Yes, that was the problem I guessed, that the network was not up when rc.local ran those commands.

> Kind of offtopic: Is there be a way to execute the route commands right after I connect to my vpn by any chance?
That's not off-topic and might be the best solution.  Put the commands in a script and add the directive

```
up /path/to/your/script
```

to the relevant openvpn.conf or similar .conf file.  They'll be run as soon as the VPN is active.

---

### Post by mc-rpg on 2017-10-30
> **SeijiSensei said:**
> Put the commands in a script and add the directive

```
up /path/to/your/script
```

to the relevant openvpn.conf or similar .conf file.  They'll be run as soon as the VPN is active.
It's not clear to me where this .conf file is but I added it to the VPN configuration file (not ending in .conf) under /etc/NetworkManager/system-connections with no luck. I found some openvpn related .conf files but they didn't have any info about the vpn connection in question. Seemed more like general openvpn conf files.

---

### Post by SeijiSensei on 2017-10-31
> **mc-rpg said:**
> It's not clear to me where this .conf file is but I added it to the VPN configuration file (not ending in .conf) under /etc/NetworkManager/system-connections with no luck. I found some openvpn related .conf files but they didn't have any info about the vpn connection in question. Seemed more like general openvpn conf files.

I've never run OpenVPN via NetworkManager so I don't know where the correct files are kept.  I run point-to-point tunnels between CentOS machines and configure them via files in /etc/openvpn.  I installed the OpenVPN package on this Ubuntu machine and see that it creates /etc/openvpn, but the only file there is a script to update resolv.conf.  I don't know where Ubuntu puts the default configuration.

---

