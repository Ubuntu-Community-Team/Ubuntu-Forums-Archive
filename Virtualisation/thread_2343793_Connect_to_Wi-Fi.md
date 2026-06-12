---
title: "Connect to Wi-Fi"
date: 2016-11-19
forum: Virtualisation
---

### Post by nati323 on 2016-11-19
Hey all, I installed Ubuntu on my machine with VirtualBox, for learning purpose.
& I try to connect to internet via WiFi.
So I googled it, and I found this site:
[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html)
But it not helped me, I'll explain what I did:
They wrote there to click on `network menu` on the `menu bar`
So I assumed that this is the arrows icon, I click on it, but I didn't saw my WiFi there like described in the site [COLOR=#3E3E3E][FONT=inherit]above-mentioned
[/FONT][/COLOR]& they said there that if the network not shown click on more network
But I dont have this menu either.
I attach a print screen:
[IMG]https://i.imgur.com/IfNhPF1.png[/IMG]

---

### Post by howefield on 2016-11-19
Moved to the "*Virtualisation*" forum for a better fit.

---

### Post by &amp;KyT$0P# on 2016-11-19
VirtualBox doesn't care what your physical Internet connection is.  VMs use their own virtual wired connection(s) to connect through NAT behind your host.

It is your host machine you need to connect to the Wi-Fi, not the guest.

---

### Post by nati323 on 2016-11-19
> **halogen2 said:**
> VirtualBox doesn't care what your physical Internet connection is.  VMs use their own virtual wired connection(s) to connect through NAT behind your host.

It is your host machine you need to connect to the Wi-Fi, not the guest.
But my host connected to wifi, what should I do next?

EDIT:
Its fix from itself, tnx anyway

---

### Post by daniel280187 on 2016-11-22
If not, you can always use some other Networking modes in Virtualbox

Bridge Adapter ->Will basically ask your DHCP to give you an IP within the same range of the Host.
NAT -> Will NAT the VM IP to the Host IP and viceversa. You can think of this as if you were using the same IP of the host to send and receive traffic (Just a way to think about it, is not what actually happens). 

You can modify this by selecting the VM on the menu and press ctrl+s (Settings) -> Network.

---

