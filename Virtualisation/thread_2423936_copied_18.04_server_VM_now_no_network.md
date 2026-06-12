---
title: "copied 18.04 server VM now no network"
date: 2019-07-31
forum: Virtualisation
---

### Post by tony68 on 2019-07-31
[FONT=arial][SIZE=2]
[/SIZE][/FONT][SIZE=2][SIZE=3][/SIZE][/SIZE]Hi All

Hopefully someone can help me here... I am running a number of VMs on an UnRAID host. However I had a failure and have had to copy the VMs onto a new host. While the 14.04 VMs have all worked fine... the 18.04 machines run but have no network connectivity.

I have been told this is because the MAC address may have changed - but while there is a lot of information on here I cant find anything which had helped yet.

When I try "ifconfig -a', I get an adapter called ens3 and lo... I was expecting to see something like eth0 / eth1 etc.

Anyway some posts suggested changing /etc/network/interfaces - which tells me that netplan(5) is now used - anyway, I seem to be going round and round in circles.

I am close to having to reinstall and reconfiguring five 18.04 multi-site webhosts which will take forever... is there a way to reset the default netwok settings so these hosts will get a DHCP address from the router as they used to do on my last host?

I am no expert but could do with a pointer if possible.

Can anyone offer some pointers?

Thanks in advance.

---

### Post by TheFu on 2019-07-31
Netplan is used in 18.04.
Device names change based on the device driver used.
The hypervisor used controls which network adapter/device is presented to each guest.

Which hypervisor are you using?  This is definitely a virtualization question, BTW.
 
Some hypervisors make moving between different VM hosts really easy.

---

### Post by wildmanne39 on 2019-07-31
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by tony68 on 2019-08-01
> **TheFu said:**
> Netplan is used in 18.04.
Which hypervisor are you using?  This is definitely a virtualization question, BTW.

Thanks TheFu... as far as I know UnRAID uses KVM as its hypervisor. On my Windows VMs (which are all working) it has the option "Hyper-V" yes or no? These are all set to yes... but this option isnt present in the VM Manager for the Ubuntu images.

---

### Post by tony68 on 2019-08-01
Thanks @wildmanne39 for moving ;-)

---

### Post by tony68 on 2019-08-01
Hi All

After speaking with a friend who is Ubuntu conversant I have managed to sort this out...

I logged in to the server locally and searched in the /etc/netplan directory... on my machine there was a file called 50-cloud-init.yaml which contained the following code;

```
network:
      ethertnets:
             enp1s0:
                   addresses: []
                   dhcp4: true
      version: 2
```

So, he told me to change the name of the adapter (enp1s0) to match the adapter name from: ```
ifconfig -a
``` (ens3)... I did this and saved the file and then ran: ```
netplan apply
```

After doing this it was all OK again and after a reboot it was still all OK... so fingers crossed its good from here on.

I thought I'd share this in case anyone else has the same issue.

Thanks

---

