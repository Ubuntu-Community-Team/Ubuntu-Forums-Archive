---
title: "Multiple IPs one Nic Ubuntu server 16.04"
date: 2017-08-16
forum: Server Platforms
---

### Post by patdundee on 2017-08-16
Hi Guys
Hope i am in th eright place. Not so easy with the latest ubuntu xenial to set multiple ips

Every time i set more than one IP the system cannot ping outbound (loses dns even though dns is set). On the previous versions you could set up as

auto lo eth0 eth0:1
iface lo inet loopback

# The primary network interface
iface eth0 inet static

        address 109.xxx.xxx.xxx
        netmask 255.255.255.224
        broadcast 109.xxx.xxx.xxx
        network 109.xxx.xxx.xxx
        gateway 109.xxx.xxx.xxx
        dns-nameservers 8.8.8.8
        # dns-* options are implemented by the resolvconf package, if installed




iface eth0:1 inet static
        address 109.xxx.xxx.xxx
        netmask 255.255.255.255
        broadcast 109.xxx.xxx.xxx
        network 109.xxx.xxx.xxx

Both IPs work fine and respond and the server could ping out to anywhere

In xenial you cannot do this as it does not accept it

I have read some articles (very few around) and they all say to do this where they are all assigned to the same network interface and no virtual ones

auto lo enp17s0
iface lo inet loopback

# The primary network interface
iface enp17s0 inet static
        address 109.xxx.xxx.xxx
        netmask 255.255.255.224
        broadcast 109.xxx.xxx.xxx
        network 109.xxx.xxx.xxx
        gateway 109.xxx.xxx.xxx
        dns-nameservers 8.8.8.8
        # dns-* options are implemented by the resolvconf package, if installed

iface enp17s0 inet static
        address 109.xxx.xxx.xxx

iface enp17s0 inet static
        address 109.xxx.xxx.xxx

So as soon as you set a second IP you lose internet connectivity outbound but can still work on network

Any ideas would be greatly apprecoated

Many thanks

---

### Post by darkod on 2017-08-17
According to this it is correct that you do not use the eth0:0 format any more.
[https://askubuntu.com/questions/547289/how-can-i-from-cli-assign-multiple-ip-addresses-to-one-interface](https://askubuntu.com/questions/547289/how-can-i-from-cli-assign-multiple-ip-addresses-to-one-interface)

 But note that he puts the address and netmask in one command, like:
```
address 172.16.100.17/24
```

In your post you use only address with no netmask. In such case it will not know to communicate correctly. Try either using the address and netmask parameters, or the format x.x.x.x/y.

PS. I suggest you delete the broadcast and network parameters. They are not needed, they are calculated from the address and netmask. And if you make an error in them it can mess things up. I have seen people putting wrong values for broadcast and network not understanding what they are. And less lines make the interfaces file cleaner. :)

---

### Post by patdundee on 2017-08-17
Hi Darkod many thanks With that info I have now got it working. 

I am running on public IP's hence why they are hidden

One thing i had noticed is when you issue the cmd ifdown -a it says cannot assign requested addres, when in fact it actually does. when you then use ifup -a it starts fine

> auto lo enp17s0
iface lo inet loopback

# The primary network interface
iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27
        gateway 109.xxx.xxx.xxx
        dns-nameservers 109.xxx.xxx.xxx 109.xxx.xxx.xxx
        # dns-* options are implemented by the resolvconf package, if installed

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

---

### Post by patdundee on 2017-08-17
Hi Guys
I have the following set up in my interfaces With this i can resolve and ping internal and external ip addresses and all ips on the iface respond to a ping. The problem i have is it will not resolve any web addresses. For example it will not install anything through apt and says unable to resolve any of the apt stores in the list. Cannot ping / resolve ip address for a www address

However if i remove the extra ip addresses and have just a single ip it will responds to every type of ping and also updates from apt

```
auto lo enp17s0
iface lo inet loopback

# The primary network interface
iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27
        gateway 109.xxx.xxx.xxx
        dns-nameservers 109.xxx.xxx.xxx 109.xxx.xxx.xxx
        # dns-* options are implemented by the resolvconf package, if installed

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27
```

---

### Post by cariboo on 2017-08-17
Merge two similar threads

---

### Post by Hugo_Serrano on 2017-08-18
Hello,

have you tried to add the dns servers on /etc/resolv.conf ?


```
nameserver <ipaddress_dns1>
nameserver <ipaddress_dns2>
```

BR,
Hugo.

---

