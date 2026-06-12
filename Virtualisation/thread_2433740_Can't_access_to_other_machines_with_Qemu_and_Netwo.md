---
title: "Can't access to other machines with Qemu and NetworkManager"
date: 2019-12-24
forum: Virtualisation
---

### Post by rudelune on 2019-12-24
Hello everybody,
I'm currently trying to use some virtual machines that I run with the command ```
sudo qemu-system-x86_64 -machine accel=kvm:tcg -cpu host -m 2048 -drive file=main.qcow2,format=qcow2,if=virtio -daemonize
```.
For this purpose, I have created a bridge br0 with NetworkManager. Here are the active connections of nmcli :
```
nmcli c show "bridge-br0"
```
```
connection.id:                          bridge-br0connection.uuid:                        da5be449-65d1-4904-b695-b424dc297628
connection.stable-id:                   --
connection.type:                        bridge
connection.interface-name:              br0
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.autoconnect-retries:         -1 (default)
connection.auth-retries:                -1
connection.timestamp:                   1577231558
connection.read-only:                   no
connection.permissions:                 --
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 --
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        default
connection.mdns:                        -1 (default)
ipv4.method:                            auto
ipv4.dns:                               --
ipv4.dns-search:                        --
ipv4.dns-options:                       ""
ipv4.dns-priority:                      0
ipv4.addresses:                         --
ipv4.gateway:                           --
ipv4.routes:                            --
ipv4.route-metric:                      -1
ipv4.route-table:                       0 (unspec)
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   no
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0 (default)
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
ipv6.method:                            auto
ipv6.dns:                               --
ipv6.dns-search:                        --
ipv6.dns-options:                       ""
ipv6.dns-priority:                      0
ipv6.addresses:                         --
ipv6.gateway:                           --
ipv6.routes:                            --
ipv6.route-metric:                      -1
ipv6.route-table:                       0 (unspec)
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
```

and ```
nmcli c show "bridge-slave-eno2
```
```
connection.id:                          bridge-slave-eno2connection.uuid:                        fb047c16-15ba-4339-aa25-e36fdf2c39f6
connection.stable-id:                   --
connection.type:                        802-3-ethernet
connection.interface-name:              eno2
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.autoconnect-retries:         -1 (default)
connection.auth-retries:                -1
connection.timestamp:                   1577231558
connection.read-only:                   no
connection.permissions:                 --
connection.zone:                        --
connection.master:                      br0
connection.slave-type:                  bridge
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 --
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        default
connection.mdns:                        -1 (default)
802-3-ethernet.port:                    --
802-3-ethernet.speed:                   0
802-3-ethernet.duplex:                  --
802-3-ethernet.auto-negotiate:          no
802-3-ethernet.mac-address:             --
802-3-ethernet.cloned-mac-address:      --
802-3-ethernet.generate-mac-address-mask:--
802-3-ethernet.mac-address-blacklist:   --
802-3-ethernet.mtu:                     auto
802-3-ethernet.s390-subchannels:        --
802-3-ethernet.s390-nettype:            --
802-3-ethernet.s390-options:            --
802-3-ethernet.wake-on-lan:             default
802-3-ethernet.wake-on-lan-password:    --
bridge-port.priority:                   32
bridge-port.path-cost:                  100
bridge-port.hairpin-mode:               no
GENERAL.NAME:                           bridge-slave-eno2
GENERAL.UUID:                           fb047c16-15ba-4339-aa25-e36fdf2c39f6
GENERAL.DEVICES:                        eno2
GENERAL.STATE:                          activated
GENERAL.DEFAULT:                        no
GENERAL.DEFAULT6:                       no
GENERAL.SPEC-OBJECT:                    --
GENERAL.VPN:                            no
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/Settings/4
GENERAL.ZONE:                           --
GENERAL.MASTER-PATH:                    /org/freedesktop/NetworkManager/Devices/3
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
```

Also, Iptables is empty and the configuration of netplan on the virtual machine is :
```
network:
   ethernets:
       addresses: [192.168.122.42/24]
       gateway4: 192.168.1.1
       nameservers:
           addresses: [8.8.8.8,8.8.4.4]
       dhcp4: yes
    version: 2
```

In fact, on this virtual machine I can access Internet and I can open a SSH connection to the host machine but the opposite is impossible (No route to host) and I can't open a connection between two virtual machines. Do you have any idea why the machines can't communicate?

Thank you very much in advance and if you need any other information I would be glad to give it to you.
I wish you a very happy festive season!
Jérôme

---

### Post by TheFu on 2019-12-26
```
addresses: [192.168.122.42/24]

```
looks wrong to me.
Don't you want a 192.168.1.x/24 network?

I don't use network-manager for anything. Wouldn't use it to manage static IPs or a bridge for a few reasons. OTOH, if this work for you, great!

---

### Post by rudelune on 2019-12-27
Thank you for your answer!
However, I still can't connect my host to my guests :x
I don't know if using network-manager is a bag thing in this context :/

---

### Post by rudelune on 2019-12-27
Okay...
I let the DHCP choosing the ip address and it chose 192.168.0.43. In this case, I was able to connect by SSH.
After setting the static ip to this one, everything was working :'(
I think that Qemu opens only these IP:/
Thank you so much for your help!
Jérôme

---

### Post by TheFu on 2019-12-27
Hate to say this, but setting a static IP to a value provided by the DHCP server is a poor choice.  Static IPs need to be picked from outside the DHCP range or bad things can happen.  May not today, but next week or next month or 5 months.  Best to just fix it today by picking a static IP outside the DHCP range.  The router will have that list, but you can just make an educated guess. I'd guess 192.168.0.222 for a static IP that was outside the range.

But you can check the router, if you want to be certain.

---

### Post by slickymaster on 2019-12-27
Thread moved to **Virtualisation** for a better fit

---

