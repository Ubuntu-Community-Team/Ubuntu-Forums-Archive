---
title: "Port forwarding with KVM (NAT)"
date: 2010-07-12
forum: Virtualisation
---

### Post by rpw on 2010-07-12
Hello,

I've got a server with one public IP-address. Then I've installed 3 virtual machines, which I want to use for different services. My question is, is there a way to forward incoming traffic on a special port of the host to a virtual machine? Lets say I want to forward traffic on the host on port 2222 to a guest machine on port 22 (ssh), so that I can directly access the virtual machine via ssh with "ssh -p 2222 username@public-ip-of-the-host".

I know it would be more easy to buy some more IP-addresses and create a bridge on the host machine, or at least I've read that it is very easy ;-) The problem is just, the hoster does not offer more than one IP-address for this rootserver, so it's impossible.

Hope to get some good answers here.

Thanks and regards,

rpw

---

### Post by YorYor on 2010-07-12
```
sudo iptables -t nat -A PREROUTING -p tcp [optional: -i <CONNECT_INTERFACE>] [optional: -d <CONNECT_IP>] --dport <CONNECT_PORT> -j DNAT --to <TARGET_IP>
sudo iptables -A FORWARD -p tcp [optional: -i <CONNECT_INTERFACE>] -d <TARGET_IP> [optional: --dport <CONNECT_PORT>] -j ACCEPT
```

e.g.
```
sudo iptables -t nat -A PREROUTING -p tcp --dport 2222 -j DNAT --to <TARGET_IP>
sudo iptables -A FORWARD -p tcp -d <TARGET_IP> -j ACCEPT

```

Have fun.

---

### Post by rpw on 2010-07-13
@YorYor

Thank's for the response. I'm afraid it does not work... ;-(

First of all I enabled forwarding in /etc/sysctl.conf (net.ipv4.ip_forward=1) of the host-system and restarted the machine.

Next I made sure that ssh is runing in the virtual machine by login to the host via ssh, and then login from there to virtual machine, again via ssh. And it worked without problems.

Then I copied the 2 command you told me into the ssh-session of the host (and I made sure it was the host and not the virtual machine). Of cource I changed the ip-addresses as neccessary.

Last thing was to test login directly to the virtual machine via ssh, but I only got a timeout.

Both host and guest are default Ubuntu Server 10.04 installation with ssh installed during the installation. No more changes.

Any ideas what I'm doing wrong?

I've read somewhere about NAT-forwarding via Qemu, but did not really understand how it works ;-(

Best regards, rpw

---

### Post by YorYor on 2010-07-25
What happens when you telnet <host IP> 2222?

---

