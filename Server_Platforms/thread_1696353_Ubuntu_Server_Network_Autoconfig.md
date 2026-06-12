---
title: "Ubuntu Server Network Autoconfig"
date: 2011-02-27
forum: Server Platforms
---

### Post by Captain Potter Fujichan on 2011-02-27
Hey guys, I recently set up an Ubuntu server on an old machine intended for the popular game, Minecraft. I'm not sure what was on the machine, it appeared to be a very old version of the Linux disto IPCOP, a kind of turn-your-pc-into-a-firewall kind of thing. Command line, and I hadn't the slightest as to what the login password was. I F-disked it and installed Ubuntu server, but since the pc was used as a firewall, it had three network cards on it, and I doubt they all work. I pulled two of them. I manually configured the network, and something came out wrong. Now, I have the command-line Ubuntu server on the machine, and I haven't the slightest as to how to reconfigure the network. I would like for it just to be autoconfiguration. I have a KVM switch and dual input monitor to copy/paste code into the command line from my other pc. If anyone has experience with installing such things as games via command line, that would help alot too.

Help greatly appreciated, thanks.

---

### Post by volkswagner on 2011-02-27
Can you identify your network card by running the following?
```
lspci
```

What does your interfaces file look like?
```
cat /etc/network/interfaces
```

---

### Post by Captain Potter Fujichan on 2011-02-27
The network card is a Macronix,Inc. Ethernet controller. [MXIC] MX987x5 {rev 20). The network interfaces file looks like the following;

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static


address 192.198.1.111
netmask 255.255.255.0
network 192.198.1.255
gateway 192.198.1.1
dns-nameservers 192.198.1.1

I think the address' were set up incorrectly. How can I fix them? 

Alternatively, can I put the LXDE package on a zip drive on my XP and install it onto the server machine?

---

### Post by CharlesA on 2011-02-27
It should read:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.111
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
```

The IP addresses were wrong for a class C private network.

---

### Post by volkswagner on 2011-02-27
> **Captain Potter Fujichan said:**
> The network card is a Macronix,Inc. Ethernet controller. [MXIC] MX987x5 {rev 20). The network interfaces file looks like the following;

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static


address 192.198.1.111
netmask 255.255.255.0
network 192.198.1.255
gateway 192.198.1.1
dns-nameservers 192.198.1.1

I think the address' were set up incorrectly. How can I fix them? 

Alternatively, can I put the LXDE package on a zip drive on my XP and install it onto the server machine?

As CharlesA pointed out you do need to change the addressing.

To do so:
```
sudo nano /etc/network/interfaces
```

Change the addresses, save and restart networking.

```
sudo /etc/init.d/networking restart
```

---

### Post by Captain Potter Fujichan on 2011-02-27
New error:
```

sudo /etc/init.d/networking restart
*reconfiguring network interfaces...
SIOCSIFADDER: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
[OK]

```Is my card not reading? I have another two i can put in. Would have multiple cards in at once create issues?

---

### Post by CharlesA on 2011-02-27
Post the output of this please:

```
sudo ifconfig -a
```

---

### Post by Captain Potter Fujichan on 2011-02-28
Thanks for the help, i managed to resolve everything.

---

