---
title: "VLAN packets not reaching NUC"
date: 2024-07-23
forum: Server Platforms
---

### Post by shifty-189 on 2024-07-23
Hello everyone,
 
I&#8217;m facing an issue with my VLAN setup on an Ubuntu Server (NUC). I&#8217;ve installed VLAN and configured Netplan, 
but I cannot ping the NUC from a different subnet. 
Here are the details:
 
Setup:
MikroTik RouterOS 6.49.10
VLAN 2 on interface ether5
NUC with Ubuntu Server (24.04) connected to ether5
 
Netplan Configuration yaml:
 
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: no
  vlans:
    enp2s0.2:
      id: 2
      link: enp2s0
      addresses:
        - 192.168.2.10/24
      routes:
        - to: default
          via: 192.168.2.1
      nameservers:
        addresses: [195.186.4.162, 195.186.1.162]
 
Observations:
The NUC can ping the gateway (192.168.2.1), the subnet laptop (192.168.0.103) and access the internet.
The laptop in the 192.168.0.x subnet can ping the VLAN gateway (192.168.2.1) but not the NUC (192.168.2.10).
 
Actions Taken:
Installed the vlan package and loaded the 8021q module.
Rebooted the NUC.
Checked the firewall on the NUC and allowed ICMP packets.
 
Any advice would be greatly appreciated!

---

### Post by currentshaft on 2024-07-23
Take a packet capture on both ends with "tcpdump" and see where the packets are being dropped.

You also haven't said why you're trying to "ping" the other host. What does this solve?

---

### Post by shifty-189 on 2024-07-24
[FONT=arial]Thank you for the suggestion to use tcpdump. I have conducted packet captures on both ends.[/FONT]
[FONT=arial]My laptop runs Windows, so I used WinDump -i 2 icmp:[/FONT]

[LIST]
[*][FONT=arial]Sent ICMP echo requests to 192.168.2.10.[/FONT]
[*][FONT=arial]Received strange ICMP replies from host.docker.internal and "ICMP net 192.168.1.109 unreachable."[/FONT]
[*][FONT=arial]The address 192.168.1.109 doesn't actually exist in my LAN (I don't have a 192.168.1.x subnet), and Docker has nothing to do with this... I'm puzzled why requests are being sent to this address.[/FONT]
[/LIST]
[FONT=arial]NUC (tcpdump -i enp2s0.2 icmp):[/FONT]

[LIST]
[*][FONT=arial]No incoming ICMP packets.

[/FONT]
[/LIST]
[FONT=arial]It seems the packets are being lost somewhere between the laptop and the NUC.[/FONT]
[FONT=arial]I'm trying these pings because I want to reach the NUC via SSH from the laptop, which also doesn't work.[/FONT]

---

### Post by The Cog on 2024-07-24
I'm not sure that tcpdump can capture on vlan interfaces. Try "tcpdump -i enp2s0 -e icmp or arp" to print the ethernet header, and maybe the vlan header if present.

---

### Post by currentshaft on 2024-07-24
Can you confirm the firewall is off on the NUC?

"sudo dmesg" and "sudo less /var/log/ufw.log" (if you installed ufw) should show you any packets being blocked.

Can you also just try SSH instead of ping; tcp should provide more troubleshooting information.

---

### Post by shifty-189 on 2024-07-24
[FONT=arial]I used sudo tcpdump -i enp2s0 -e icmp or arp and observed that ARP packets are correctly arriving from the gateway to the NUC. 
However, no ICMP packets are coming through.

[/FONT][FONT=arial]Example of the tcpdump output:
14:28:16.927456 XX:XX:XX:XX:XX:XX > XX:XX:XX:XX:XX:XX, ethertype 802.1Q (0x8100), vlan 2, p 0, ethertype ARP (0x0806), Reply 192.168.2.1 is-at YY:YY:YY:YY:YY:YY (oui Unknown), length 42[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]It appears that the ARP packets are properly tagged with VLAN 2 and are being received by the NUC, but ICMP packets are not arriving.[/FONT]

---

### Post by shifty-189 on 2024-07-25
Yes, I've had the firewall (UFW) turned off since the beginning of the setup. Therefore, I also don't have any logs for it.

---

### Post by currentshaft on 2024-07-25
Can you try a TCP traceroute?

---

### Post by shifty-189 on 2024-07-30
Setting up a static route from the laptop to the NUC resolved the issue, and now it works perfectly.

---

### Post by currentshaft on 2024-07-30
Nice. Mind marking this thread as solved?

---

