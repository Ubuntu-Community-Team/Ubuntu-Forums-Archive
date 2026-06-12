---
title: "Do you use Linux firewall?"
date: 2011-06-07
forum: The Cafe
---

### Post by Nyromith on 2011-06-07
I am a very dangerous hacker and look for easy targets to break into. Are you one of them? :twisted:

---

### Post by 3Miro on 2011-06-07
> **Nyromith said:**
> I am a very dangerous hacker and look for easy targets to break into. Are you one of them? :twisted:

If you were, you would know that Ubuntu doesn't need a firewall.

In order for an attack to come from the outside, you need an open port and Ubuntu doesn't open any (by default).

Also, the firewall is technically always installed, just not enabled. Various tools only serve to setup rules and policies, they don't install a firewall the same way you would in Windows.

---

### Post by Nyromith on 2011-06-07
Of course I was kidding.

As for me, I used to be a paranoid and had a very limiting router configuration and an enabled Linux firewall that allowed only 80 and 443 outbound. Recently, I bought a modem without a router function and disabled the Linux firewall, and got a huge boost. It feels like opening a window to look outside rather than looking through the glass. Yes, there are dangers, but it feels wonderful when your computer is a direct member of a huge global network.

On Windows though, I wouldn't dare to disable the firewall.

---

### Post by sisco311 on 2011-06-07
Where is the *other* option?

The firewall is disabled on my desktop, but a *linux* firewall is enabled on my router. ;)

---

### Post by fuduntu on 2011-06-07
Yes, and anyone with a portable computer that leaves their internet router and connects to a public network now and then or forwards ports / uses upnp should have one enabled.

---

### Post by Gremlinzzz on 2011-06-07
sudo ufw enable
do it after a fresh install:)

---

### Post by Old_Grey_Wolf on 2011-06-07
I have a switch/router at home. When at home, I am behind the switch/router that only forward ports other than 80 and 443 to the WAN. On my LAN, I use ssh, rdp, and samba; therefore, I have ports open. When I take my laptop or netbook out of the house I enable ufw. ufw simplifies the process of manipulating setting up the rules and policies.

It is funny when I get home again, then try to use cssh to update all my servers and desktops all at once, and it takes me a few seconds to realize the reason cssh doesn't work is because ufw is enabled :).

---

### Post by Frogs Hair on 2011-06-07
Enabled with the most basic settings .

---

### Post by BigCityCat on 2011-06-07
Don't most routers use a linux firewall?

---

### Post by Nyromith on 2011-06-08
I don't think blocking outbound ports can enhance security very much, because most malicious software use port 80, the most popular. After all, ports are just numbers, no?

---

### Post by Random_Dude on 2011-06-08
> **Gremlinzzz said:**
> sudo ufw enable
do it after a fresh install:)
+1

It's been always the first command I run after a fresh install.

---

### Post by FunkyRes on 2011-06-08
I use Linux firewall on my servers (CentOS 5.x) but for my home network, I primarily rely upon my routers firewall and not running any services I don't need.

Firewall is just one line of defense on them, I also turn off services I don't need and run services for personal use (IE ssh) on non standard port.

I don't use linux firewall rules on home network because I don't want to mess with reconfiguring the firewall every time I want to play with some new service. I would prefer to just start the daemon, access it from various clients, and kill the daemon when I no longer need/want it.

---

### Post by jerenept on 2011-06-08
> **Nyromith said:**
> I don't think blocking outbound ports can enhance security very much, because most malicious software use port 80, the most popular. After all, ports are just numbers, no?

Any port between 1024 and 65536 can be opened by any process, with any permission, right? Just a number!

Most malicious software uses user trust and ignorance on IT security, as modern OS's are pretty much unbreakable now.

---

### Post by markp1989 on 2011-06-08
I got a dedicated firewall at home running Astaro Home edition. 

only opened a few ports needed for xbox live and basic web use, everything else is blocked.

although I do have ufw enabled on my laptop as it frequently gets used out side my house.

---

### Post by Glencore on 2011-06-08
I use Mobloquer if that counts.

---

### Post by uRock on 2011-06-08
> **Nyromith said:**
> Of course I was kidding.

As for me, I used to be a paranoid and had a very limiting router configuration and an enabled Linux firewall that allowed only 80 and 443 outbound. Recently, I bought a modem without a router function and disabled the Linux firewall, and got a huge boost. It feels like opening a window to look outside rather than looking through the glass. Yes, there are dangers, but it feels wonderful when your computer is a direct member of a huge global network.

On Windows though, I wouldn't dare to disable the firewall.

Did you have any issues with DNS?

---

### Post by lisati on 2011-06-08
Each to their own......

My setup only allows incoming connections to what I choose to let in, with a slightly tweaked fail2ban (which works with iptables) monitoring suspicious behaviour on my server machine.

---

### Post by handy on 2011-06-08
I use a standalone headless Dell Optiplex PIII 700Mhz 256MB RAM 20GB HDD (the original 2GB HDD eventually failed), running [IPCop]("http://www.ipcop.org/").

It is quick & simple to set up (once you know how), is quiet & uses $53-/year electricity (I tested it).

I have screenshots of all of the client side browser interface configuration screens, so that in the inevitable case that I have to reinstall due to hardware failure, the configuration will be quick & simple, saving me from having to reinvent the wheel.

I also have an Athlon 700 machine that is already setup & ready to swap in when the Dell inevitably fails.

The IPCop box is the firewall router for the household LAN, the ADSL modem/router runs in bridge mode, which basically turns that router off & just uses modem straight through.

I've been running this $5- Dell from the rubbish tip 24/7 for years now. No problems bar the drive failure, (I have a pile of both IDE & SATA drives laying around). :)

---

### Post by Nyromith on 2011-06-09
> **uRock said:**
> Did you have any issues with DNS?

Yes, how could I forget... Port 53/udp also must be opened.

---

### Post by kimda on 2011-06-09
I use Debian with iptables as a firewall/router. At home I have a Linksys wireless router which I flashed with dd-wrt firmware which uses also iptables as a firewall.

---

