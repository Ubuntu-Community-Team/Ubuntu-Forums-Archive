---
title: "VMware Player (Ubuntu 12.04 Host + Windows 7 Guest) How to Port Forward to Guest"
date: 2012-08-10
forum: Virtualisation
---

### Post by johnathanamber on 2012-08-10
Hey everyone,

I seem to be having some issues in find out how to do this. I've searched for port forwarding on here and on Google, but most seem to be using VMware Workstation.

I am using Vmware Player.
Host is Ubuntu 12.04 w/ xubuntu-desktop.
Guest is Windows 7 Professional.
I have ufw/gufw installed.

I want to forward ports from IP 192.168.49.0/24 3389 + 5404 to 192.168.108.0/24 3389. This is to make it to where when I RDP to my IP 192.168.49.x:3389 on my Ubuntu host, that ufw actually redirects this to 192.168.108.x:3389 which is my virtual machine. Both are DHCP, so that is why I am wanting the ranges instead of the individual addresses.

How can I accomplish this?

When I loaded gufw, unlock, Edit > Add Rule > Advanced, enter:
0 Allow In Log All TCP
from: 192.168.49.0/24:3389
to: 192.168.108.0/24:3389

The Add button is still grayed out and I am not able to add this in.

So I am sure I am not using this correctly, or in the right format.

I am also working on figuring out how to do this via ufw instead of gufw, but not much luck.

Any help would be appreciated.

Thank you,
Johnathan

---

### Post by johnathanamber on 2012-08-10
Will this do the same thing as actually forwarding or will thus just allow it:
```
sudo ufw allow proto tcp from 192.168.49.0/24 port 3389 to 192.168.108.0/24 port 3389
```

---

### Post by dcstar on 2012-08-10
> **johnathanamber said:**
> Hey everyone,

I seem to be having some issues in find out how to do this. I've searched for port forwarding on here and on Google, but most seem to be using VMware Workstation.

I am using Vmware Player.
Host is Ubuntu 12.04 w/ xubuntu-desktop.
Guest is Windows 7 Professional.
I have ufw/gufw installed.

I want to forward ports from IP 192.168.49.0/24 3389 + 5404 to 192.168.108.0/24 3389. This is to make it to where when I RDP to my IP 192.168.49.x:3389 on my Ubuntu host, that ufw actually redirects this to 192.168.108.x:3389 which is my virtual machine.
.........

You can simply change the VM to use Bridge networking instead of NAT and there won't be any issues like this.

---

### Post by johnathanamber on 2012-08-11
@dcstar,

I would agree however, for some reason, I have issues with some of our company websites when using Bridge. So I need to see how I cam forward IP and Port requests from the host to the VM.

Thank you,
Johnathan

---

