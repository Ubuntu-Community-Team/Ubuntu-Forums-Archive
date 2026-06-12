---
title: "How to clear iptables ?"
date: 2011-04-21
forum: Security
---

### Post by oygle on 2011-04-21
Hi,

Installing a router, and I need to completely "wipe" iptables (flush I mean) on both computers, and I think I run ufw/gufw on both, so that would need to be uninstalled. The router is very secure, has NAT, etc, etc, and I'd rather setup all that side of things in one point, rather than on each computer.

Can someone please explain how to do this ?

Oygle

---

### Post by stealth. on 2011-04-21
> **oygle said:**
> Hi,

Installing a router, and I need to completely "wipe" iptables (flush I mean) on both computers, and I think I run ufw/gufw on both, so that would need to be uninstalled. The router is very secure, has NAT, etc, etc, and I'd rather setup all that side of things in one point, rather than on each computer.

Can someone please explain how to do this ?

Oygle

**EDIT: Why do you have to do this, because you installed a router... Please explain?**

"sudo iptables -F" <--that will flush iptables
"sudo iptables -Z" <--that will zero it (i think... you should check just in case)

No need to uninstall ufw, just give it a:
"sudo ufw disable" 
it should output "ufw: disabled on system startup"

You *might* need to uninstall GUFW, I'm not 100 percent sure, but I believe it might override ufw.

---

### Post by oygle on 2011-04-22
> **stealth. said:**
> **EDIT: Why do you have to do this, because you installed a router... Please explain?**

Because the internet connection is via a USB dongle directly attached to the computer, hence no 'security', and therefore the need for UFW/GUFW to establish iptables 'rules'.

Now, with the addition of a proper (NAT) router/firewall ( [Billion 7404VGPX](http://au.billion.com/product/voip/bipac7404vgpx.php) ), there is no need for iptables rules. All firewalling will be done at the router/modem, at one point.

> **stealth. said:**
> 
"sudo iptables -F" <--that will flush iptables
"sudo iptables -Z" <--that will zero it (i think... you should check just in case)

No need to uninstall ufw, just give it a:
"sudo ufw disable" 
it should output "ufw: disabled on system startup"

You *might* need to uninstall GUFW, I'm not 100 percent sure, but I believe it might override ufw.

Okay, thanks for those 2 iptables commands. Yes, it would be safest to uninstall GUFW, as it does alter ufw, which in turn alters iptables.

Thanks,

Oygle

---

