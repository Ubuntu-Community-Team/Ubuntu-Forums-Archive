---
title: "Ping via direct ethernet connection to macOS fails"
date: 2024-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by erick00 on 2024-04-13
[FONT=&quot]I have a PC running Ubuntu connected to my Mac mini running Sonoma via an ethernet cable. I can log onto the Ubuntu system over the ethernet cable using Microsoft Remote Desktop on the macOS.  Therefore I do have connectivity.[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]However, while I can ping the Ubuntu system from the macOS using ‘ping 192.168.1.2’ successfully when I try to ping the macOS from Ubuntu using ‘ping 192.168.1.3’ it fails with:[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.[/FONT]
[FONT=&quot]From 192.168.1.242 icmp_seq=1 Destination Host Unreachable[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]I searched the internet and tried to fix it by adding two lines to the ufw configuration file /etc/ufw/before.rules. They are shown below but commented out:[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]# ok icmp codes for INPUT[/FONT]
[FONT=&quot]-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT[/FONT]
[FONT=&quot]-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT[/FONT]
[FONT=&quot]-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT[/FONT]
[FONT=&quot]-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]# Allow outbound ICMP Added by My-Name-Redacted[/FONT]
[FONT=&quot]# -A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT[/FONT]
[FONT=&quot]# -A ufw-before-outut -p icmp --icmp-type echo-request -j ACCEPT[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]# ok icmp code for FORWARD[/FONT]
[FONT=&quot]-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT[/FONT]
[FONT=&quot]-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT[/FONT]
[FONT=&quot]-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT[/FONT]
[FONT=&quot]-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]When I uncomment the two rules "ufw-before-output' rules I added to the file and run the command ‘sudo ufw reload’ I get the following:[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]ERROR: problem running ufw-init[/FONT]
[FONT=&quot]iptables-restore: line 79 failed[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]Problem running '/etc/ufw/before.rules'[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]Line 79 is the last line in the file which just says 'COMMIT'[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]Do you have a suggestion why I still cannot ping my macmini from Ubuntu?[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]Also note that I can ping the macOS system from Ubuntu if I ping to the wifi address of the mac as in ‘ping 192.168.1.176’.[/FONT]
[FONT=&quot]
[/FONT]

---

### Post by hyperlinxe on 2024-04-13
Is your mac mini configured to deny/drop icmp 

that is a basic security precaution, in linux we have to manually enable that as an option.

If your computers aren't given Ip addresses by dhcp, via for example a typical router on the lan, than how are they being linked together initially?

> [FONT=&amp]Also note that I can ping the macOS system from Ubuntu if I ping to the wifi address of the mac as in &#8216;ping 192.168.1.176&#8217;.[/FONT]

I think you answered your own question...

You're on the local network using IP addresses' typically assigned by dhcp by the router
and then attempting to connect outside of that network, defined by the router, and wondering why it doesn't work.

---

