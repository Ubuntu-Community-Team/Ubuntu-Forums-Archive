---
title: "Changing IP causes SSH not to authenticate anymore"
date: 2018-09-15
forum: Server Platforms
---

### Post by salnet on 2018-09-15
Hello Folks,

I'm just setting up a new virtual mchine (vSphere) with 18.04.1.
For convenience I got an DHCP during installation.
After installation finished I was able to ssh into that new machine with that dynamic IP.

After I changed that dynamic IP to a manual one I was able to connect to ssh on that machine using the new IP address but the system refused to accept my credentials (Access denied).

For changing IP-address I did this:
```
sudo mv /etc/netplan/50-cloud-init.yaml /etc/netplan/50-cloud-init.yaml.bak

sudo nano 01-netcfg.yaml
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
 version: 2
 renderer: networkd
 ethernets:
   ens160:
     dhcp4: no
     dhcp6: yes
     addresses: [10.254.0.22/24]
     gateway4: 10.254.0.1
     nameservers:
       addresses: [10.254.0.21,10.254.0.1]

sudo netplan apply

sudo /etc/init.d/ssh restart
```

SSH is configured with default settings, it should listen to all configured IP addresses (0.0.0.0).

After a fine reboot problem is still there :-(

Is there someone who could help me?

Kind regards
Tim

---

### Post by darkod on 2018-09-15
What is actually the message when trying to connect from the client?

You can get more info if you try something like ssh -vv user@IP (if using linux client).

---

### Post by salnet on 2018-09-15
Just getting Access denied for my user. If connecting local (ssh tim@localhost) everything works fine.
I think the problem is my DNS. After manually updating the entry for that server to the new IP everything works well.
Adding "UseDNS no" to /etc/ssh/sshd_config will work as well if you are only connecting via IP address instead of hostname.

---

### Post by darkod on 2018-09-15
You left out that you use DNS. After changing the IP to static and if it doesn't registrate it is normal that the old DNS entry will try reaching the wrong old IP.

Please mark the thread as Solved if you don't have the problem any more. Cheers.

---

