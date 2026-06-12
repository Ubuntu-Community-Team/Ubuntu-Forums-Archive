---
title: "qemu: no guest to host firewall, virtual router vulnerabilities"
date: 2009-04-10
forum: Security
---

### Post by egravet on 2009-04-10
I was wondering if someone has a solution or further information on the following issues, in order of importance. I realize that using a "qemu -net none" switch would provide an extreme workaround for all issues, but with but the guest needs to be on a network.

===system booted via:
$ qemu -boot d -cdrom <any livecd with nmap preinstalled>.iso
(this should provide implicitly -net nic -net user)

Issuing a command from within the guest to examine the default "virtual router", "virutal router" ip from $ netstat -nr:
$ nmap 10.0.2.2
Shows the following output (truncated):
Interesting ports on 10.0.2.2
Not shown: xxxx closed ports
PORT STATE SERVICE
80/tcp open http
513/tcp open login
514/tcp open shell

1) How would one create a guest-> host firewall? The qemu guest can see and modify content (via $ firefox 10.0.2.2) on an apache2 web server service on my host computer. Apache2 is behind the host iptables firewall, and is also configured to listen only to localhost (127.0.0.1:80) in /etc/apache2/ports.conf. I realize qemu is free, but this is a security issue for anyone expecting to have the guest operate in a sandbox, because action within the guest can affect the host web service (which accepts anonymous user input and uses php). I realize a solution would be to restrict the web service via passwords and performing security tasks on the host LAMP installation, but it would be useful and more convenient to have the extra layer of security of a guest -> host firewall preventing connection. Does anybody know of a command line switch or other solution to block connections to the host from the guest that still allows the guest to be contactable via network?

2) Are the 513 and 514 ports exploitable? How? And how to close them? There are two additional services provided by the "qemu virtual router" regardless of what services are running on the host computer. It is actually possible to successfully connect to the login port via:
$ telnet 10.0.2.2 513
Connected to 10.0.2.2.
Escape character is '^]"

I'm not sure if it is possible to execute something at this point, because I am unfamiliar with telnet. The security issue here is vague because the purpose of the services on 513 and 514 on the qemu virtual router at 10.0.2.2 is not documented, but it is not good security to let a sandboxed guest interact directly with the qemu process. Anyone know how to lockdown or further explore these virtual services?

3) Can qemu source be modified (for custom installations) to ignore all host listeners? The dhclient3 (UDP) listener on the host computer is not visible: is this hardcoded into qemu to ignore dhclient listeners, or is it a condition to ignore UDP listeners? 

Setup:==================
=== qemu (0.9.1) kqemu(1.3.0~pre11-8), this was originally performed on a Debian machine, but Debian and Ubuntu have nearly identical qemu packages, and Ubuntu is a Debian-based system:
[http://packages.ubuntu.com/search?keywords=qemu](http://packages.ubuntu.com/search?keywords=qemu)

===guest ip via # ifconfig -a
10.0.2.15

---

### Post by bodhi.zazen on 2009-04-10
You use NAT to firewall the guest.

---

### Post by egravet on 2009-04-11
I'm not sure how to set up NAT to prevent the guest from contacting the host's services.  I would like to make the "virtual router" perform NAT and firewalling, but there are no qemu switches to enable the features and the features may not even exist. (The features may not have been coded by the qemu developers.)

I already have an iptables firewall up on the host that should be stopping all incoming packets to the host, and the host services are configured to listen to the localhost or 127.0.0.1 address only. The issue is that the qemu binary is operating on the host machine, so for all networking purposes its packets appear to come from 127.0.0.1.

---

