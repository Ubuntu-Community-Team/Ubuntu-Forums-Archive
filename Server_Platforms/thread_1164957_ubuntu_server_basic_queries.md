---
title: "ubuntu server basic queries"
date: 2009-05-20
forum: Server Platforms
---

### Post by salim.madni on 2009-05-20
dear gurus 

can some one let me know

1) if we use 64bits, does it work faster than 32 bits? is os very fast, is application also effect or it does not matter all are same

2) while installing server i want to select samba to installed how can i select it?

3)static ip lan setup,can some one guide me where to enter dns entries during installation time. i want to defined full qualified domain name. say
test.ubuntuserver.com

4) during installation, it ask for update option, like autoupdate, manual update or no update. advise each one how it work where to get help assistance support.

kind regards
salim

---

### Post by Cheesemill on 2009-05-20
> **salim.madni said:**
> 3)static ip lan setup,can some one guide me where to enter dns entries during installation time. i want to defined full qualified domain name. say
test.ubuntuserver.com

When the installation prompts you for the hostname, just hit ESC then select 'Manual network configuration'.

Cheesemill

---

### Post by langsweirdt on 2009-05-20
1) 64-bit is a lot faster for applications that are data-intensive. Both the application and the OS need to be 64 bit in order to work. For applications written in a non-interpreted language like C this means at least a recompilation. Java should handle 64 bit completely transparent.

2) During the installation you are asked to select the packages you want to install, samba should be there. If it's not or if you cant find it, you can still do it afterwards:  $sudo aptitude install samba

3) IP configuration is done in: /etc/networking/interfaces
If you want a static IP-address you need an entry like:
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
The fully qualified name of your machine is in /etc/hostname

---

