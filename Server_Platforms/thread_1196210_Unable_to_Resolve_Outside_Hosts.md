---
title: "Unable to Resolve Outside Hosts"
date: 2009-06-24
forum: Server Platforms
---

### Post by SoulMazer on 2009-06-24
Sorry, I didn't know how to word the title. But in my 9.04 Server, if I tried say "wget www.google.com", I would get the following error:

> Resolving [www.google.com](www.google.com)... failed: Name or service not known.
wget: unable to resolve host address 'www.google.com'


What can I do to fix this?

Thanks in advance for any help.

---

### Post by ZeldeR on 2009-06-24
I think it's DNS problem, have you any DNS Server in your LAN?

---

### Post by R.Bucky on 2009-06-24
Ok, going for the captain obvious here... Is your internet connection in the back of your computer? Can you use your browser to view pages? Sorry, had to check.

---

### Post by SoulMazer on 2009-06-24
@ZeldeR - I do not believe so...I at least did not setup a DNS server by myself. So I would guess not.

@R Bucky - I can confirm that my computer is connected to the internet...I use it as a LAMP server for my website and I am able to access my website via a browser from another computer.

---

### Post by jimv on 2009-06-24
How do you have the internet connection setup?  DHCP?  Static IP?  If it's static, what's in /etc/network/interfaces?

---

### Post by SoulMazer on 2009-06-24
@jimv - static, and here is my /etc/network/interfaces file:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


---

### Post by Bachstelze on 2009-06-24
We also need the contents of [font="monospace"]/etc/resolv.conf[/font].

---

### Post by SoulMazer on 2009-06-24
@Hymn - Well I guess that was my problem. I guess when I was configuring my server I was going to change my nameservers, but I never did. I changed those and got everything working.

Sorry for the inconvenience everybody.

Thank you though!

---

