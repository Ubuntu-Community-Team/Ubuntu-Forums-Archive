---
title: "[openVPN] Routing only port 25 through"
date: 2017-12-16
forum: Server Platforms
---

### Post by wgmvanhees on 2017-12-16
I have my own mail server, but was recently forced to switch ISPs and the new ISP blocks port 25 (outbound and inbound). Therefore I decided to get a VPS, install a openVPN server on it and route port 25 to the VPS. Since the VPS has a bandwidth cap, I want to route only port 25.

I set up an openvpn server on the VPS successfully and tested it by setting it to redirect all traffic (redirect gateway) and tested this using a laptop and verified that it was, indeed, redirecting the traffic (IP changed as should). Since I wanted to only forward port 25, I removed the 'redirect gateway' line, so it would stop redirecting all traffic.

I connected the mail server as a client, pinged the tun gateway IP (10.146.139.1) and verified it worked. Next, I decided to forward port 80 and 443 to see whether the ip would change:

```
echo '201 mail.out' | sudo tee /etc/iproute2/rt_tables
sudo ip rule add fwmark 1 table mail.out
sudo iptables -t mangle -A OUTPUT -p tcp --dport 80 -j MARK --set-mark 1
sudo iptables -t mangle -A OUTPUT -p tcp --dport 443 -j MARK --set-mark 1
sudo ip route add default via 10.146.139.5 dev tun1 table mail.out
```

However, if I run 'curl http://ipinfo.io/ip', it doesn't return anything, so it isn't working. What am I doing wrong?

---

### Post by SeijiSensei on 2017-12-16
I'd run an instance of your SMTP server of choice on the remote machine.  Configure it to relay all incoming messages to your local server via its VPN address, and likewise configure your local server to use the remote's VPN address as its relayhost.  Make sure the external machine is configured to receive mail from anywhere. Then point your MX at the external IP of the remote.

Finally use a simple firewall on the remote like
```

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

iptables -A INPUT  -i lo -j ACCEPT
iptables -A INPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT  -i eth0 -s ext.ip.of.local -d ext.ip.of.remote -j ACCEPT
iptables -A OUTPUT -o eth0 -s ext.ip.of.remote -d ext.ip.of.local -J ACCEPT
iptables -A INPUT  -i tun0 -j ACCEPT
iptables -A OUTPUT -o tun0 -j ACCEPT
iptables -A INPUT  -i eth0 -d ext.ip.of.remote -p tcp --dport 25 -j ACCEPT
iptables -A OUTPUT -o eth0 -s ext.ip.of.remote -p tcp --dport 25 -j ACCEPT
iptables -A INPUT  -j REJECT --reject-with icmp-port-unreachable

```

where "ext.ip.of.local" is the externally-facing address of your network, probably your router's address.  "ext.ip.of.remote" is the IP address assigned to your VPS.

That should block all traffic except the connection to create the tunnel, the traffic over the tunnel, and SMTP exchanges between the server and remote hosts.  You may have a different external interface identifier than "eth0".  If you need to manage the server using SSH via its external address you need to add
```
iptables -A INPUT -i eth0 -p tcp -d ext.ip.of.server --dport 22 -j ACCEPT
```
You can manage the remote from the local server both over the Internet and over the tunnel without this rule.

---

### Post by wgmvanhees on 2017-12-16
Thanks for the suggestion! I hadn't thought of that. I haven't done mail relay yet so I'll need to check whether it's a viable option, but seems like a good solution at first glance. Thanks for the firewall suggestion, but I already have a fair amount of experience with them. Not so much with ip route though.

---

