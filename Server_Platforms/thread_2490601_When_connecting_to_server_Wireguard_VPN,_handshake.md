---
title: "When connecting to server Wireguard VPN, handshake detected, but no internet"
date: 2023-09-08
forum: Server Platforms
---

### Post by japtar on 2023-09-08
I've been trying to setup Wireguard for my Ubuntu 22.04.3 LTS server that, along with Pi-hole, is hosting a couple of my own self-hosted websites.  Ideally, I'd like it so that by connecting via VPN, I'd get access to both the internet and my self-hosted website, filtered through Pi-hole's ad-blocking.  I've been following Pi-hole's [instructions here]("https://docs.pi-hole.net/guides/vpn/wireguard/server/"), and got up to what seems to be my laptop and Android Phone doing a proper handshake with the server.
```

$ sudo wg
interface: wg0
  public key: (redacted)=
  private key: (hidden)
  listening port: 47111

peer: (redacted, Android)=
  preshared key: (hidden)
  endpoint: 172.59.185.188:31743
  allowed ips: 10.100.0.2/32, fd08:4711::2/128
  latest handshake: 34 seconds ago
  transfer: 30.54 KiB received, 22.71 KiB sent

peer: (redacted, laptop-win)=
  preshared key: (hidden)
  endpoint: 73.9.84.143:52098
  allowed ips: 10.100.0.4/32, fd08:4711::4/128
  latest handshake: 1 minute, 26 seconds ago
  transfer: 302.57 KiB received, 2.41 KiB sent

peer: (redacted)=
  preshared key: (hidden)
  allowed ips: 10.100.0.3/32, fd08:4711::3/128

```
Boot up Firefox, though, and on Android, neither Google nor my own self-hosted website shows up.  I've turned off the wifi on the device, thus using the 5G network to see if the problem is related to the router or not, but to no avail.  For laptop, Google barely shows up (presumably from the browser's cache,) LinkedIn doesn't; my self-hosted sites doesn't show up, either.  The Wifi notification on the laptop starts telling me there's no internet as soon as I turn Wireguard client on, so that's also concerning.

What are some ways to troubleshoot what's going on with this?

Anyway, my [FONT=lucida console]/etc/wireguard/wg0.conf[/FONT] is currently configured like so:
```

[Interface]
Address = 10.100.0.1/24, fd08:4711::1/64
ListenPort = 47111
PrivateKey = (redacted)=

PostUp = nft add table ip wireguard; nft add chain ip wireguard wireguard_chain {type nat hook postrouting priority srcnat\; policy accept\;}; nft add rule ip wireguard wireguard_chain counter packets 0 bytes 0 masquerade; nft add table ip6 wireguard; nft add chain ip6 wireguard wireguard_chain {type nat hook postrouting priority srcnat\; policy accept\;}; nft add rule ip6 wireguard wireguard_chain counter packets 0 bytes 0 masquerade
PostDown = nft delete table ip wireguard; nft delete table ip6 wireguard

# Android
[Peer]
PublicKey = (redacted)=
PresharedKey = (redacted)=
AllowedIPs = 10.100.0.2/32, fd08:4711::2/128

# laptop-mac
[Peer]
PublicKey = (redacted)=
PresharedKey = (redacted)=
AllowedIPs = 10.100.0.3/32, fd08:4711::3/128

# laptop-win
[Peer]
PublicKey = (redacted)=
PresharedKey = (redacted)=
AllowedIPs = 10.100.0.4/32, fd08:4711::4/128

```
My laptop client config looks like this:
```

[Interface]
[Interface]
PrivateKey = (redacted)=
Address = 10.100.0.4/32, fd08:4711::4/128
DNS = 10.100.0.1, fd08:4711::1

[Peer]
PublicKey = (redacted)=
PresharedKey = (redacted)=
AllowedIPs = 0.0.0.0/0, ::/0
Endpoint = (redacted).duckdns.org:47111
PersistentKeepalive = 25

```
If there's anything else I should look over, that'd help.  It might be worth noting that I am on XFinity network with a modem provided by them, but using my own Wifi router to designate the Ubuntu server as the DNS server. I've checked what ports Comcast blocks, but 47111 didn't appear on that list.  Maybe they're lying?

---

### Post by TheFu on 2023-09-09
What about the iptables/nftables forwarding rules?

And I wouldn't assume that it is ok to have duplicate stanza headers.

I keep the VPN server configured to use a different subnet than where all other systems are located.  That different subnet is how the VPN clients and server communicate.  Also, all other LAN and WAN servers are located on different IPs/subnets.  So my piholes aren't on the VPN at all.  Keeping the VPN completely separate makes things easier, I've found.

---

### Post by japtar on 2023-09-11
Thanks for the reply.  I haven't considered separating wireguard into a  different computer, I'd probably need to grab a few more  hardware-related materials (mostly a switch and ethernet cord) to pull  that off.  Would perhaps using a pre-made docker container like Firezone  work as an option, with access to both internet and self-hosted docker  container websites?

ETA: oh, right, the IP Tables.  I've mostly been using UFW for configuring the firewall, haven't explored IP Tables too much:
```

&#10140;   sudo iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DOCKER-USER  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-1  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere
ufw-track-forward  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere

Chain DOCKER (6 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             172.19.0.2           tcp dpt:http
ACCEPT     tcp  --  anywhere             172.19.0.2           tcp dpt:3012
ACCEPT     tcp  --  anywhere             172.28.0.2           tcp dpt:5005
ACCEPT     tcp  --  anywhere             172.30.0.2           tcp dpt:4567
ACCEPT     tcp  --  anywhere             172.30.0.3           tcp dpt:3000
ACCEPT     tcp  --  anywhere             172.30.0.3           tcp dpt:ssh
ACCEPT     tcp  --  anywhere             172.17.0.3           tcp dpt:9443
ACCEPT     tcp  --  anywhere             172.17.0.3           tcp dpt:9000
ACCEPT     tcp  --  anywhere             172.17.0.3           tcp dpt:8000
ACCEPT     tcp  --  anywhere             172.22.0.3           tcp dpt:http
ACCEPT     tcp  --  anywhere             172.18.0.2           tcp dpt:mysql
ACCEPT     tcp  --  anywhere             172.18.0.4           tcp dpt:http

Chain DOCKER-ISOLATION-STAGE-1 (1 references)
target     prot opt source               destination
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain DOCKER-ISOLATION-STAGE-2 (6 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain DOCKER-USER (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

Chain ufw-after-forward (1 references)
target     prot opt source               destination

Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination

Chain ufw-after-output (1 references)
target     prot opt source               destination

Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere

Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination

Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere

Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere

Chain ufw-reject-forward (1 references)
target     prot opt source               destination

Chain ufw-reject-input (1 references)
target     prot opt source               destination

Chain ufw-reject-output (1 references)
target     prot opt source               destination

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain ufw-track-forward (1 references)
target     prot opt source               destination

Chain ufw-track-input (1 references)
target     prot opt source               destination

Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh /* 'dapp_OpenSSH' */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             multiport dports 4443,http-alt
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:3306
ACCEPT     tcp  --  anywhere             anywhere             multiport dports http,https
ACCEPT     tcp  --  192.168.0.0/24       anywhere             tcp dpt:domain
ACCEPT     udp  --  192.168.0.0/24       anywhere             udp dpt:domain
ACCEPT     tcp  --  10.10.10.0/24        anywhere             tcp dpt:domain
ACCEPT     udp  --  10.10.10.0/24        anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:2375
ACCEPT     tcp  --  172.17.0.0/16        10.0.0.171           tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:9091
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8929
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8930
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8099
ACCEPT     udp  --  anywhere             anywhere             multiport dports 1900,7359
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8096
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:222
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8383
ACCEPT     udp  --  anywhere             anywhere             udp dpt:47111

Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination

Chain ufw-user-output (1 references)
target     prot opt source               destination

```

---

### Post by TheFu on 2023-09-11
To my knowledge, UFW doesn't have the ability needed to control port forwards. I could be wrong.

Linux containers and running a VPN server are a terrible idea, even if it works. Don't do it.

---

### Post by japtar on 2023-09-22
OK, I'm back with this.  So since I had another computer lying around, just installed Ubuntu server and ran through [pi-hole's instructions]("https://docs.pi-hole.net/guides/vpn/wireguard/server/") again.  The concluding wg0.conf file is:
```

[Interface]
Address = 10.100.0.1/24, fd08:4711::1/64
ListenPort = 55123
PrivateKey = <redacted>
# android
[Peer]
PublicKey = <redacted>
PresharedKey = <redacted>
AllowedIPs = 10.100.0.2/32, fd08:4711::2/128

```

Testing it on Android with this configuration file:
```

[Interface]
Address = 10.100.0.2/32, fd08:4711::2/128
DNS = 10.100.0.1, fd08:4711::1
PrivateKey = <redacted>

[Peer]
PublicKey = <redacted>
PresharedKey = <redacted>
Endpoint = <redacted>.duckdns.org:55123
AllowedIPs = 10.100.0.1/32, fd08:4711::1/128
PersistentKeepalive = 25

```

And yet...still not able to connect.  There's definitely a handshake:
```

# sudo wg
interface: wg0
  public key: <redacted>
  private key: (hidden)
  listening port: 55123

peer: <redacted>
  preshared key: (hidden)
  endpoint: 73.9.84.143:49866
  allowed ips: 10.100.0.2/32, fd08:4711::2/128
  latest handshake: 35 seconds ago
  transfer: 15.58 KiB received, 13.45 KiB sent

```
But typing google.com in Firefox on Android gives me a page-not-found.  This is also a fresh new install, so ip tables is...uh, bare at the moment:
```

$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
My router IP address is not  10.0.0.1 as the instructions seems to assume, but rather, 192.168.0.1.   I've also disabled IP6 at the current moment as well (I forget why,  maybe a conflict with some web service?)  So perhaps instead of using  10.100.0.1 or similar allows IP address, I should use 192.168.100.1,  instead?  Not exactly sure about this.

---

### Post by TheFu on 2023-09-22
> **TheFu said:**
> What about the iptables/nftables forwarding rules?

You need to solve this part or it will never work.

---

### Post by japtar on 2023-09-24
So I completely forgot that the pi-hole documentation makes some assumptions that you've followed some steps installing pi-hole before attempting to install Wireguard.  So should have probably followed through some of those steps.  First off, the [FONT=courier new]wg0.conf[/FONT] were missing a few lines, specifically [FONT=courier new]PostUp[/FONT] and [FONT=courier new]PostDown[/FONT].  While scouring some Youtube vids, there was one that also mentions setting the [FONT=courier new]SaveConfig[/FONT] flag, so I just kind of went ahead and added that in.  The full [FONT=courier new]wg0.conf[/FONT] now reads:
```

[Interface]
PrivateKey = <redacted>
Address = 10.100.0.1/24, fd08:4711::1/64
ListenPort = 55123

# IMPORTANT: replace "enp3s0" in the PostUp/PostDown lines with your actual network interface,
# which you can find by installing net-tools (sudo apt install net-tools) then running the "sudo ifconfig"
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o enp3s0 -j MASQUERADE;
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o enp3s0 -j MASQUERADE;
SaveConfig = true

# taro-android
[Peer]
PublicKey = <redacted>
PresharedKey = <redacted>
AllowedIPs = 10.100.0.2/32, fd08:4711::2/128

```

ETA: Oh, snap, I forgot to mention that I enabled IP forwarding:
```

sudo nano /etc/sysctl.d/99-sysctl.conf

# Then in the config file, look for and uncomment the following lines:
net.ipv4.ip_forward = 1
net.ipv6.conf.all.forwarding = 1

# Save file, then run sysctl to apply new configuration
sudo sysctl -p

```

I also forgot to enable the firewall, so went ahead with that, too:
```

sudo ufw enable

# I configured port 55123 as my VPN port (see wg0.conf above,)
# so make sure that UDP port is open in the firewall.
sudo ufw allow 55123/udp comment 'Wireguard VPN port'

# Also make sure I can still SSH to this server
sudo ufw allow OpenSSH

```

While I could have reloaded the new Wireguard configuration with [FONT=courier new]sudo systemctl reload wg-quick@wg0[/FONT], since I am also enabling the firewall for the first time, I chose to reboot with [FONT=courier new]sudo reboot[/FONT], instead.

One last change to fix the problem: on the Android phone, I had to go edit the Wireguard configuration the following fields:

```

# Make sure the DNS IP address points to the pi-hole server's local IP address
DNS = 192.168.<redacted>

# To be able to connect the internet, allow connection to any IP address
AllowedIPs = 0.0.0.0/0, ::/0

```

This seemed to have solved my problem.  I can access Google, LinkedIn, and my own self-hosted websites without a problem.  Nice!

---

### Post by japtar on 2023-09-24
Also, the Pi-hole documentation has a really useful bash script to add a new peer, but taking above information into account, I've updated the script like so (don't forget to edit the line after [FONT=courier new]# IMPORTANT[/FONT]):
```

#! /usr/bin/env bash
cd /etc/wireguard
umask 077

# IMPORTANT: this line needs to change to IP address of Pi-hole server!!!
dnsServ="192.168.<redacted>"
ipv4="$1$4"
ipv6="$2$4"
serv4="${1}1"
serv6="${2}1"
target="$3"
name="$5"

wg genkey | tee "${name}.key" | wg pubkey > "${name}.pub"
wg genpsk > "${name}.psk"

echo "# $name" >> /etc/wireguard/wg0.conf
echo "[Peer]" >> /etc/wireguard/wg0.conf
echo "PublicKey = $(cat "${name}.pub")" >> /etc/wireguard/wg0.conf
echo "PresharedKey = $(cat "${name}.psk")" >> /etc/wireguard/wg0.conf
echo "AllowedIPs = $ipv4/32, $ipv6/128" >> /etc/wireguard/wg0.conf
echo "" >> /etc/wireguard/wg0.conf

echo "[Interface]" > "${name}.conf"
echo "Address = $ipv4/32, $ipv6/128" >> "${name}.conf"
echo "DNS = ${dnsServ}" >> "${name}.conf" #Specifying DNS Server
echo "PrivateKey = $(cat "${name}.key")" >> "${name}.conf"
echo "" >> "${name}.conf"
echo "[Peer]" >> "${name}.conf"
echo "PublicKey = $(cat server.pub)" >> "${name}.conf"
echo "PresharedKey = $(cat "${name}.psk")" >> "${name}.conf"
echo "Endpoint = $target" >> "${name}.conf"
echo "AllowedIPs = 0.0.0.0/0, ::/0" >> "${name}.conf" # clients isolated from one another
echo "PersistentKeepalive = 25" >> "${name}.conf"

# Print QR code scanable by the Wireguard mobile app on screen
qrencode -t ansiutf8 < "${name}.conf"

wg syncconf wg0 <(wg-quick strip wg0)

```

After adjusting the permissions of the script (e.g. [FONT=courier new]chmod +x script.sh[/FONT]), run it with:

```

sudo ./script.sh "10.100.0." "fd08:4711::" "my_server_domain:55123" 2 "1st-device"
sudo ./script.sh "10.100.0." "fd08:4711::" "my_server_domain:55123" 3 "2nd-device"

```

---

### Post by TheFu on 2023-09-25
There is absolutely ZERO need to redact private IPs or private DNS IPs.
Glad my hint about port forwarding was helpful.

---

