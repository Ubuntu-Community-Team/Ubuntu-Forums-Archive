---
title: "LTSP! Alternative CD dhcpd.conf.. urgent!"
date: 2008-06-27
forum: Server Platforms
---

### Post by Lapp-Same on 2008-06-27
[HTML]"No interface for LTSP dhcpd configuration found!

There are no free interfaces for usage with LTSP Server. 
pleas configure the file /etc/ltsp/dhcpd.conf manually to point to 
a valid static interface after installation"[/HTML]

Do i need two network cards? because i just got one on this machine but i can fix that

I can find the file and edit it, but where do I put what in?

---

### Post by Lapp-Same on 2008-06-27
Any one?

---

### Post by cariboo on 2008-06-27
You shouldn't need another network card, how are you planning on connecting to the terminals.

Jim

---

### Post by Lapp-Same on 2008-06-28
> **cariboo907 said:**
> You shouldn't need another network card, how are you planning on connecting to the terminals.

Jim

Do i need one for the internet, and one for the LTSP-Enviroment?
What if i want to be "offline"

I want the Ltsp-server to take the dhcp and the thin clients, and the internet have to be on a own connection antoher place in the network... with or without dhcp enabled/static ip-adreess

---

### Post by Lapp-Same on 2008-06-30
> **Lapp-Same said:**
> Do i need one for the internet, and one for the LTSP-Enviroment?
What if i want to be "offline"

I want the Ltsp-server to take the dhcp and the thin clients, and the internet have to be on a own connection antoher place in the network... with or without dhcp enabled/static ip-adreess


??

---

### Post by koenn on 2008-06-30
> **Lapp-Same said:**
> [HTML]"No interface for LTSP dhcpd configuration found!..

a valid **static** interface after installation"[/HTML]


is your server getting its address by dhcp ? apparently, that won't work, you need a static address.

---

### Post by Lapp-Same on 2008-06-30
> **koenn said:**
> is your server getting its address by dhcp ? apparently, that won't work, you need a static address.

Static from the dhcp, or just set ha static one?

I want the server to take over the DHCP, but the internet would come in another place in the building to the main switch (because i dont have a 10 gigabit fiber card to the server to connect it to the internet!.

---

### Post by koenn on 2008-06-30
> **Lapp-Same said:**
> Static from the dhcp, or just set ha static one?

Don't know, I just read the error msg you posted  :)
I'd say just set a static Ip address + the rest of the nic config manually (mask, gateway, ...). Servers should have a static address, anyway. 
You might want to use a dhcp reservation, but in this case, I don't see how ltspd would see the difference between a dhcp reservation and a normal dhcp lease, so it would probably still complain.

> **Lapp-Same said:**
> 
I want the server to take over the DHCP, but the internet would come in another place in the building to the main switch (because i dont have a 10 gigabit fiber card to the server to connect it to the internet!.
I don't see how this has anything to do with it, so I ignored it.

---

### Post by Lapp-Same on 2008-06-30
> **koenn said:**
> Don't know, I just read the error msg you posted  :)
I'd say just set a static Ip address + the rest of the nic config manually (mask, gateway, ...). Servers should have a static address, anyway. 
You might want to use a dhcp reservation, but in this case, I don't see how ltspd would see the difference between a dhcp reservation and a normal dhcp lease, so it would probably still complain.


I don't see how this has anything to do with it, so I ignored it.

I'll try, thanks

---

### Post by koenn on 2008-06-30
> **Lapp-Same said:**
> I'll try, thanks

don't forget to add the addres to /etc/ltsp/dhcpd.conf as well. 

'night.

---

### Post by Lapp-Same on 2008-06-30
> **koenn said:**
> don't forget to add the addres to /etc/ltsp/dhcpd.conf as well. 

'night.

Everything is running now
i can load the Thin Client but when i try to login I'll just get "Workstation isn't authorized to connect to the server" HELP! :P

---

### Post by koenn on 2008-07-01
I've never used or even set up LTSP or edubuntu, so I have no idea where to go from here. 

I suppose you need to create user accounts on the server, and guessing from the error msg, you also need to inform the server from which workstations users will log in. Maybe this is the time you start looking for the documentation. 

Half-educated guess: if ltsp uses tcpwrapper to control which workstations can connect, adding an address range in /etc/hosts.allow might help.

---

### Post by Lapp-Same on 2008-07-01
> **koenn said:**
> don't forget to add the addres to /etc/ltsp/dhcpd.conf as well. 

'night.

That's where I added the sttings the server are running, but when i try to login on a thin-client i just get "Machine is not authenticated" !!??

---

### Post by Lapp-Same on 2008-07-01
> **koenn said:**
> I've never used or even set up LTSP or edubuntu, so I have no idea where to go from here. 

I suppose you need to create user accounts on the server, and guessing from the error msg, you also need to inform the server from which workstations users will log in. Maybe this is the time you start looking for the documentation. 

Half-educated guess: if ltsp uses tcpwrapper to control which workstations can connect, adding an address range in /etc/hosts.allow might help.

Well is that's how i have to do it i would never be done, i got 900 thin-clients to add then...

---

### Post by koenn on 2008-07-01
> **Lapp-Same said:**
> Well is that's how i have to do it i would never be done, i got 900 thin-clients to add then...

As if you'd be the first one who needs to manage access for a medium-sized network ... 

if it's hosts.allow we're dealing with, you don't have to list every individual hostname or ipadress. you can use wildcards, regular expressions, network/mask notation, .... to cover multiple hosts in one statement. 

try:
man hosts_access

also : the absense of /etc/hosts.allow and /etc/hosts.deny will result in unlimited access. (this could actually be an easy way to test if this is the cause of your problem : just rename those two files ...)

and even if you'd have to list every single host ip address, it would be trivial to create a script that generates ip addresses or read them from your dhcp lease files, and writes them to the allow list in the required format. 

It's Unix, it's been dealing with this sort of things for 30 years already :)

---

### Post by Lapp-Same on 2008-07-01
> **koenn said:**
> As if you'd be the first one who needs to manage access for a medium-sized network ... 

if it's hosts.allow we're dealing with, you don't have to list every individual hostname or ipadress. you can use wildcards, regular expressions, network/mask notation, .... to cover multiple hosts in one statement. 

try:
man hosts_access

also : the absense of /etc/hosts.allow and /etc/hosts.deny will result in unlimited access. (this could actually be an easy way to test if this is the cause of your problem : just rename those two files ...) 

and even if you'd have to list every single host ip address, it would be trivial to create a script that generates ip addresses or read them from your dhcp lease files, and writes them to the allow list in the required format. 

It's Unix, it's been dealing with this sort of things for 30 years already :)

I added things to the Hosts.allow, now isn't the ******* ltsp-server working anymore....

---

### Post by koenn on 2008-07-01
> **Lapp-Same said:**
> I added things to the Hosts.allow, now isn't the ******* ltsp-server working anymore....

d*mn.
so i suppose hosts.allow wasn't the answer. (or you made a syntax error in the file). Can you roll it back ?

---

### Post by Lapp-Same on 2008-07-01
> **koenn said:**
> d*mn.
so i suppose hosts.allow wasn't the answer. (or you made a syntax error in the file). Can you roll it back ?

I'am trying *** hell, up here

---

### Post by Lapp-Same on 2008-07-01
> **koenn said:**
> d*mn.
so i suppose hosts.allow wasn't the answer. (or you made a syntax error in the file). Can you roll it back ?

Well now i shall try to install the ltsp-server to the real server så the we can see how that would go....

---

### Post by koenn on 2008-07-01
wait 1 sec. 

Google found me this ltsp setup quickstart : [http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html#AEN411](http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html#AEN411)

it clearly states you need tcpwrappers (hosts.allow) for ltsp to work. 

it also speaks of a tool that should help you set it all up : ltspadmin and/or ltspcfg.

its a 2004 paper so ltsp may have evolved since then, (or is it edubuntu you're using ?) but it might be an interesting read anyway. Shows you what to be looking for, if nothing else. 
Like I said, reading the documentation sometimes helps. 

Also, do "man hosts_access" to see what syntax hosts.allow uses.

---

### Post by koenn on 2008-07-01
> **Lapp-Same said:**
>  ... så the we can see how that would go....
love the way you write "so".

---

### Post by Lapp-Same on 2008-07-01
> **koenn said:**
> love the way you write "so".

Sorry about that!

But cross you're fingers that this would work!

---

### Post by Lapp-Same on 2008-07-02
> **koenn said:**
> wait 1 sec. 

Google found me this ltsp setup quickstart : [http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html#AEN411](http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html#AEN411)

it clearly states you need tcpwrappers (hosts.allow) for ltsp to work. 

it also speaks of a tool that should help you set it all up : ltspadmin and/or ltspcfg.

its a 2004 paper so ltsp may have evolved since then, (or is it edubuntu you're using ?) but it might be an interesting read anyway. Shows you what to be looking for, if nothing else. 
Like I said, reading the documentation sometimes helps. 

Also, do "man hosts_access" to see what syntax hosts.allow uses.

I shall try, and replay the results...

---

### Post by Lapp-Same on 2008-07-02
> **koenn said:**
> wait 1 sec. 

Google found me this ltsp setup quickstart : [http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html#AEN411](http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html#AEN411)

it clearly states you need tcpwrappers (hosts.allow) for ltsp to work. 

it also speaks of a tool that should help you set it all up : ltspadmin and/or ltspcfg.

its a 2004 paper so ltsp may have evolved since then, (or is it edubuntu you're using ?) but it might be an interesting read anyway. Shows you what to be looking for, if nothing else. 
Like I said, reading the documentation sometimes helps. 

Also, do "man hosts_access" to see what syntax hosts.allow uses.


Sorry but this is for the ltsp-versjon 4.0 and dosent work/in the 5.0 =/

---

### Post by Lapp-Same on 2008-07-04
> **koenn said:**
> love the way you write "so".

Hello Koenn, i got a trouble with the optins in the dhcp file and you where the first one to ask!

I dont get internet on a Windows Machine when connecting the network!
but it get the adress from the dhcp3-server, with everything but i can't get on the internet

network setup:

eth0----->(www) "connected with a static-ip to" 
eth1-----> running the dhcp/ltsp/ftp server to the network (Everything works) 

The thin-client works and getting adress, the windows machine also do, they can play on my dedicated server here but can't connect the internet!

---

### Post by koenn on 2008-07-05
When you're running sessions on a terminal server; it's actually the server who  needs internet access.
Check it's network settings on the eth0 interface. You will need a gateway address (i.e. your router) in /etc/network/interfaces. You also need a DNS server (in /etc/resolv.conf)

If it's not terminal clients you're talking about, then your dhcp server needs to provide these settings to its clients.


To pin-point the problem, start by pinging hosts along your route to the internet (ie. your router LAN address and WAN address, an ip address on the internet, ...).
Also, ping an internet host by name, to see if DNS works. 

```
ping -c2 66.249.91.104
ping -c2 www.google.com
```

---

### Post by Lapp-Same on 2008-07-05
> **koenn said:**
> When you're running sessions on a terminal server; it's actually the server who  needs internet access.
Check it's network settings on the eth0 interface. You will need a gateway address (i.e. your router) in /etc/network/interfaces. You also need a DNS server (in /etc/resolv.conf)

If it's not terminal clients you're talking about, then your dhcp server needs to provide these settings to its clients.


To pin-point the problem, start by pinging hosts along your route to the internet (ie. your router LAN address and WAN address, an ip address on the internet, ...).
Also, ping an internet host by name, to see if DNS works. 

```
ping -c2 66.249.91.104
ping -c2 www.google.com
```


The server got's internet and it works, soo do it on the thin-clients, it works perfectly, but when a xp machine connects to the network it gets the adress and everything, but the internet doesn't works.....

---

