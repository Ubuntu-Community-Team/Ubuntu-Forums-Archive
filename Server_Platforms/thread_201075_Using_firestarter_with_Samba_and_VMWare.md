---
title: "Using firestarter with Samba and VMWare"
date: 2006-06-21
forum: Server Platforms
---

### Post by gwi on 2006-06-21
I have the following setup:
Ubuntu 6.06 host, with interface eth0 connected to LAN (and Internet via this LAN). Subnet is 192.168.11.0/24.

VMWare's host-only network (interface vmnet1) is on 192.168.25.0/24.

Samba is used to share a directory via vmnet1, so the virtual machines in VMWare can access it.

In firestarter I made a rule to allow incoming traffic on ports 137-139 445, coming from 192.168.25.0/24.

The virtual machines can't access the Samba share however (they can't even ping the host). If I turn off the firewall, the can access and browse the share.

In firestarter I see events like blocking UDP port 137, with source addresses in ranges other than 192.168.11.0/24, and that seems ok.

Why can't the machines on the 192.168.11.0/24 subnet access the Samba share, and at the same time firestarter is not showing blocking events on this subnet?

---

### Post by omargomez on 2006-08-02
Try this:

Edit > Preferences > Netwok settings

Local network connected device:
   > detected device vmnet8
   > Check 'Enable internet connection sharing' checkbox

Hope it helps

::omar

---

### Post by mannheim on 2006-08-02
Hi Gwi,

I had a similar problem. I did something like omargomez's suggestion, which solved it. (If it isn't clear, he is referring to the menu items in firestarter's gui, I think.) I am using VMWares' "nat" networking option, which may work differently.

But here are two [COLOR="Red"]warnings[/COLOR].

First, if you check the box for "shared in networking" in the firestarter gui, then the script that starts up firestarter on reboot will check whether the interface vmnet1 (or vmnet8 in my case) is up. If it is not up, the script just bails out -- and you will have no firewall (i.e. no rules in iptables, just accept all). This is a problem, because (on my machine) the vmware script that brings up the vmnet interface runs **after** the firestarter script! So I was getting [COLOR="Red"]no firewall[/COLOR] -- and I didn't realise. I consider this a bug in firestarter.

Second warning (not a security issue). I had a similar problem with samba, which was configured to lisen only on vmet8. When the samba startup script runs at boot time, the interface vmnet8 is not up; so samba doesn't start. I solved this job (and the one above) by creating a script called from /etc/rc.local which restarts firestarter and samba 4 minutes after boot time.

In the end, I was fed up with the firestarter script, and created my own iptables script by hand and removed firestarter entirely. Now at least I know what's going on. The relevant line in my iptables script are:

```

# Default policies: ACCEPT outbound traffic, DROP input

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Accept connections on the SMB_PORT (port 445), from VMWARE_GUESTS to VMWARE_HOST on interface VMNET_IFACE

iptables -A INPUT -d $VMWARE_HOST -i $VMNET_IFACE -s $VMWARE_GUESTS -p tcp --dport $SMB_PORT -j ACCEPT

```

where (in my case) VMWARE_HOST is something like 192.168.123.1 adn VMWARE_GUESTS is something like 192.168.123.0/255.255.255.0. The above lines seem sufficient to get my vmware configuration working. (In my case, because the guest is Windows XP, port 445 seems sufficient for sharing.) A disclaimer though: I know only enough about iptables to experiment, read examples, and get it working for me in a configuration I believe is ok.

---

### Post by gwi on 2006-08-07
Mannheim,

Thanks for your information, especially the samba restart tip!

---

