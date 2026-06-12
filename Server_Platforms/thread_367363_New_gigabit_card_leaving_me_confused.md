---
title: "New gigabit card leaving me confused"
date: 2007-02-22
forum: Server Platforms
---

### Post by creigscofield on 2007-02-22
Hello, I'm feeling like a n00b right now.  I recently put a new ethernet card in my server box (because the old one was a 10baseT/10base2 combo :lolflag: ) But now the system doesn't connect to the network.  I checked if it was the card with a couple of live cds (dsl, gentoo minimal) and they recognized the card right away.  So obviously the card needs to be setup, and therein lies my n00bitude, as I don't know the commands to do this.  Please help.

---

### Post by Strider on 2007-02-22
If you run "ifconfig -a" does it show the new card?

Use "dmesg" to verify the card was picked up during boot-up.  It should list it.

run "lspci -v" which will verify if the card is being detected by the OS.  Most likely it is but it's being listed as a different ethernet name, which can be verified using ifconfig.

If the new card is detected and is being shown as "eth1" or something else, instead of "eth0" (assuming eth0 was your old card), you need to add configuration for this.

edit /etc/network/interfaces:

add the following if your new card shows up as "eth1":

```

auto eth1
iface eth1 inet static
  address <ip_address>
  netmask 255.255.255.0 (assuming you're using that as your netmask)
  gateway <gateway/router ip>
  broadcast <broadcast address> (if using 192.168.1.0/24, then it's 192.168.1.255)

```

Save the file and run "/etc/init.d/networking restart".  After that you should be able to access your network on the new card.

-Mike

---

### Post by MJN on 2007-02-22
This is quite a common occurance when swapping network cards, or indeed restoring images onto new machines (hence different network card than the original machine) due to the mappings in **/etc/iftab**.

Run **ifconfig** and confirm your card is present/detected and make a note of its MAC address. Now edit **/etc/iftab** so that the name eth0 is assigned to your new card (identified by its MAC address).

Strider's solution is just as valid, however if you're a stickler for 'neatness' and don't want legacy settings hanging around (and indeed want your first/only network card to be eth0 as per convention) then iftab may be worth checking. Furthermore, fixing iftab is fixing the true source of the problem as opposed to managing the symptom.

Mathew

---

### Post by creigscofield on 2007-02-22
thanx, that fixed it.:p

---

