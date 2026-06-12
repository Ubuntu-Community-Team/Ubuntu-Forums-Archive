---
title: "Problem connecting to web from XP guest"
date: 2010-01-19
forum: Virtualisation
---

### Post by tla123 on 2010-01-19
I am running a XP pro 32-bit guest on an Ubuntu Karmic 64-bit host.
The problem I am having is that the guest cannot connect to the web.

I am completely new to using virtualbox or any type of virtualization,
so I am probably doing something wrong.  The web connection should 
"work out of the box" according to most experiences posted on the web.

I connect to the internet through DSL, and on the ubuntu host I use the
following command: sudo pon dsl-provider.  Normally, I am not connected.
I connect only when I need to access the web.

How should I connect to the web on the XP guest?  Do I setup a PPPOE 
connection as if it were a real XP PC? Or connect (sudo pon dsl-provider) 
first on the host, and then on the guest configure it as if it is 
connected directly to the web?   Note that I tried both, and neither worked.

My host's /etc/network/interfaces is listed below, if that provides a clue.
Additionally, running ipconfig /all on the guest shows the "AMD PCNET
PCI Ethernet Adapter" is found.  The card is setup as NAT.

Any help or pointers in debugging this would be greatly appreciated.

Mike

--------------------------------------------------
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet dhcp
--------------------------------------------------

---

### Post by tla123 on 2010-01-19
As is often the case, soon after posting my question an idea popped in my head which got the web connection to work.

What I found was that I needed to login to my DSL provider on the
host *before* booting the guest.  There is no need to change the guest's LAN connection from the default settings.  It will automatically establish a web connection.

The guest's web connection will not work if I log into the DSL provider on the host *after* the guest has booted up.  This is even the case if I disable then re-enable the LAN connection.

Does anybody know why this is the case, and if there is a way around it?

---

