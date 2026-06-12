---
title: "Telnet settings needed for VM UBUNTU Session"
date: 2013-01-13
forum: Virtualisation
---

### Post by bxdobs on 2013-01-13
XP-SP3 running VMPlayer 4.0.4 with a Ubuntu 10.04.4 LTS VM

Using TinyTerm residing on the "same" machine, I can telnet to this VM with no issues. What I can't seem to determine is how to telnet to this VM from another machine on the local network. 

UBUNTU has created a domain of 192.168.149.xxx ... this doesn't match my local network address of 214.197.79.xxx ... I am wondering if this may be the reason I cannot get to the UBUNTU VM from an external machine.

I need to replace some old hardware running UNIX based software so would like to use a VM but all of the peer machines need access to this VM via Telnet ... the only thing stopping me is being able to connect to the VM from another machine on the local network.

---

### Post by Ms. Daisy on 2013-01-15
Use [ssh]("https://help.ubuntu.com/community/SSH") instead of telnet.  Telnet sends all its packets unencrypted (including your password), so they're easily intercepted by anyone listening.  Ssh encrypts all traffic so it's far superior to telnet.  Is there even any documentation on using telnet from this century?  Home routers use telnet but I don't know many other uses of it today.

192.168.149.xxx ...  
214.197.79.xxx ...

214.197.79.xxx is probably your external IP address- that's the address that the world uses to find you.  192.168.149.xxx is the internal network and will not talk to the rest of the world.  I'm guessing that your Ubuntu computer is plugged into a modem and directly facing the internet, right?  (Please consider getting a router). VMPlayer creates a subnet for the virtual machines that it runs (so that's probably the 192.168 subnet).  Your XP host can talk to the virtual machine, but no other machines will be able to talk to it.  You need to create a bridged network connection for the Ubuntu guest to be routable to the internet.

---

### Post by CharlesA on 2013-01-15
[Tiny Term]("http://www.centurysoftware.com/products/tinyterm-terminal-emulator.php") looks like something you would use to access a mainframe.

/unhelpful

---

### Post by Ms. Daisy on 2013-01-15
Let me guess... the mainframes are on the 214.197.79 subnet...

Somebody shoot me please.

---

### Post by bxdobs on 2013-01-15
ssh ... not concerned with security for this app as this is for internal network use only.

Tiny term is an VT emulator from Century software ... I use this primarily on AIX systems.

192.168.149.xxx ... is the UBUNTU/VMPlayer Settings
  
214.197.79.xxx ... is my local network subnet managed by my router ... my external IP is provided by my ISP on the other side WAN side of the router.

XP box has VMPlayer running with Ubuntu installed as a VM ... no modems ... I have a P2P network on the LAN side of my Router and not using DHCP ... all devices have Static addresses in the 214.197.79 domain .

>  You need to create a bridged network connection for the Ubuntu guest to be routable to the internet.

I don't need or want UBUNTU to be accessed from the internet ... I just need the local P2P machines to be able to access it.
 
netstat shows the ubuntu connection but I can't seem to see or access the UBUNTU traffic on the LAN side of the router

My thoughts were that I must somehow configure the VMP and UBUNTU to use the Routers LAN domain ... but the discussion of bridging and or proxy appear to be the way everyone is pointing me ... I was hoping there would be a procedure I could follow to test this.

---

### Post by eenofonn on 2013-01-15
Sounds to me like you're vm is setup using NAT and you need to get it setup bridged.  Even if you don't want it to access the internet it's currently residing in a different network than your other machines and the vm kernel is routing the traffic to and from the vm.  You might be able to figure out how to write some sort of route to and from the machine but I've found in my dealings with NAT it's much easier to just change the connection to bridged and assign it an IP on the same network as your other machines.

I hope this makes sense

---

### Post by CharlesA on 2013-01-15
> **eenofonn said:**
> Sounds to me like you're vm is setup using NAT and you need to get it setup bridged.  Even if you don't want it to access the internet it's currently residing in a different network than your other machines and the vm kernel is routing the traffic to and from the vm.  You might be able to figure out how to write some sort of route to and from the machine but I've found in my dealings with NAT it's much easier to just change the connection to bridged and assign it an IP on the same network as your other machines.

I hope this makes sense

What they said ^.

---

