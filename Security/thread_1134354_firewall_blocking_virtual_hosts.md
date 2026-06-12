---
title: "firewall blocking virtual hosts"
date: 2009-04-23
forum: Security
---

### Post by equick on 2009-04-23
Hi,

I have a firewall issue :(

I have set up some KVM virtual hosts on my ubuntu 8.10 server using the documentation at [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) to configure a network bridge.

Unfortunately the firewall on my server blocks all outgoing traffic from the virtual hosts including DNS lookups. You can see I have a rule allowing all dns traffic below but traffic is still blocked.

root@ubuntu:/home/ed# ufw status
Status: loaded

To                         Action  From
--                         ------  ----
53/tcp                     ALLOW   Anywhere
53/udp                     ALLOW   Anywhere

In iptables I have :

Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53


And my network interface looks like this

cat /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.20
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


Apart from stopping my firewall, I'm not sure how to fix this. Can anyone help me please?

Thanks,

Ed.

---

### Post by equick on 2009-04-23
This command seems to fix it but not sure if this is secure enough???

iptables -A FORWARD -i br0 -o br0 -j ACCEPT

Also can this be done in ufw?

Thanks,

Ed.

---

### Post by bodhi.zazen on 2009-04-23
I think you are fine with that command.

You can not do it directly with ufw, edit the ufw config files and add in that line.

should be fairly ovbious ...

Otherwise, get your firewall running, add in that line ...

Then

sudo -c bash "iptables-save > /etc/iptables.rules"

then disable ufw

then 

sudo iptables-restore < /etc/iptables.rules

to make it active on boot, add

```
iptables-restore < /etc/iptables.rules
```to /etc/rc.local

You are now using iptables directly w/o ufw ;)

---

### Post by equick on 2009-04-23
Thanks for your reply. Actually I am really keen to get my head round iptables but when I ran iptables-save it seems to list out quite a few references to ufw (see extract below), so would that cause any issues if I disable ufw?


:ufw-user-output - [0:0]
-A INPUT -j ufw-before-input
-A INPUT -j ufw-after-input
-A FORWARD -j ufw-before-forward
-A FORWARD -j ufw-after-forward
-A FORWARD -i br0 -o br0 -j ACCEPT
-A OUTPUT -j ufw-before-output
-A OUTPUT -j ufw-after-output
-A ufw-after-forward -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK FORWARD]: "
-A ufw-after-forward -j RETURN
-A ufw-after-input -p udp -m udp --dport 137 -j RETURN
-A ufw-after-input -p udp -m udp --dport 138 -j RETURN
-A ufw-after-input -p tcp -m tcp --dport 139 -j RETURN
-A ufw-after-input -p tcp -m tcp --dport 445 -j RETURN

---

### Post by equick on 2009-04-23
Actually bad news. The command
iptables -A FORWARD -i br0 -o br0 -j ACCEPT 
seems to open up my firewall, at least on the internal network. :(

---

### Post by equick on 2009-04-24
I think the solution will be to use this rule after all

iptables -A FORWARD -i br0 -o br0 -j ACCEPT 

and install iptables on my virtual hosts. I'm using JeOS which by default, doesn't come with iptables.

---

### Post by bodhi.zazen on 2009-04-24
> **equick said:**
> I think the solution will be to use this rule after all

iptables -A FORWARD -i br0 -o br0 -j ACCEPT 

and install iptables on my virtual hosts. I'm using JeOS which by default, doesn't come with iptables.

If you have a set of rules you apply to every machine, put then in the forward chain of the host.

iptables -A FORWARD -i br0 -o br0 -p udp --sport 53 -j ACCEPT  #DNS
iptables -A FORWARD -i br0 -o br0 -p tcp --dport 53 -j ACCEPT  #SSH

# Multiple ports (ssh, http, https)
iptables -A FORWARD -i br0 -o br0 -p udp -m multiport --dports 22,80,443 -j ACCEPT

And on ...

If you want unique rules on the guests, user a per guest firewall.

---

