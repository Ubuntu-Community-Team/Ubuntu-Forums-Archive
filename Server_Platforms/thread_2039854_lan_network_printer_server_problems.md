---
title: "lan network printer server problems"
date: 2012-08-09
forum: Server Platforms
---

### Post by jocatoth on 2012-08-09
i am running ubuntu 8.04.03 server as a print server and as a file server. i experienced a power outage at my home which lasted several hours. when the power came back on i could no longer reach my server (via ssh).

my router works
my switch shows no activity lights and the switch appears dead 
i replaced the switch 
the ethernet cabling tests okay
several other computers in the house could not reach the internet through the cat 5 cable and new switch and router until i replaced their NICs.
so i replaced the NIC on the 8.04 server
instead of being identified as eth0 it shows up as eth1
i changed the /etc/network/interfaces file to
auto eth1
iface eth1 inet static
gave it the same ip address assigned to it by the router.
i have restarted both the router and server several times and still can not get to the server. it does not show up in the attached devices on my router. i am about to conclude that the mobo is somehow damaged. before i go to the trouble of replacing it is there anything else i should check?

thanks for you help. i hope i am overlooking something simple but for the life of me i can not think of what it is.

jocatoth

---

### Post by volkswagner on 2012-08-09
I would change the interface to dhcp.

Change:
```
iface eth1 inet static
```

To:

```
iface eth1 inet static
```

and comment out all other static info lines.

Your router may have corrupt lease table, or the /etc/rules.d file related to persistent-net rule may have old data from your  card's mac address, causing an issue.

Can you ping any thing from the server?

---

### Post by jocatoth on 2012-08-10
> **volkswagner said:**
> I would change the interface to dhcp.

Change:
```
iface eth1 inet static
```

To:

```
iface eth1 inet static
```

and comment out all other static info lines.

Your router may have corrupt lease table, or the /etc/rules.d file related to persistent-net rule may have old data from your  card's mac address, causing an issue.

Can you ping any thing from the server?

i assume in the second```
 To:

iface eth1 inet static
```

you mean iface eth1 inet dhcp

and comment out the rest?
any tips on getting rid of a corrupt lease table on a consumer netgear router?

i think what i am going to try is to use a different (than prior to the power outage) fixed ip address for the server. if that does not work i will temporarily switch the server to dhcp finding out if there is an address the router and server can agree on then making that static.

i can ping 127.0.0.1 but nothing else.

either the router is not letting the server in to the lan or the server (mobo?) can not make it out.

thanks

please keep the suggestions coming

---

### Post by kennethconn on 2012-08-10
Take as much out of the equation and build it back up.
 
Have you tested a direct connection between your computer and server with a crossover cable using static IPs? You could also use the new switch if you are sure it is working.
 
You don't need the router at this stage as everything is on your LAN right?

---

### Post by jocatoth on 2012-08-11
thanks for you comments

i did replace the switch. i took advantage of the opportunity to go from 10/100 equipment to 10/100/1000 equipment.

so i put in a new 16 port gigabit switch

and i could not get computers or server (ubuntu and a freenas) to reach the lan let alone the internet.

i did test the router with a laptop and could get to the internet.

then i added the switch and with the laptop i could get through the switch through the router to the internet

then i tested the cat 5 cables. they all tested fine

then i added 3 new 10/100/1000 NICs when i put those in the complaining computers they could see each other on the lan and get to the internet.

then i put the same model 10/100/1000 NIC in the ubuntu 8.04.3 server 
so far no lan connection.

the router does not show the ubuntu server as an attached device under an assigned static address or a dhcp chosen address.

when i changed the /etc/network/interface file from a static assigned address to dhcp and rebooted, i did see an error message going by about a sshd configuration issue.

either the router will not let the server into the lan or some configuration setting on the server will not let the server out.

i had used mac filtering on the router to assign the server the static address.

since the server was set up with the onboard built into the mobo nic mac to get an assigned ip address i thought at first just change the mac address and change from eth0 to eth1 it should work. so far it has not.
i have tried a number of other things (everything i can think of)

what i think i will do next is install a cd drive and run a live cd on the server box and poke around. i can also get all the drive settings from the 6 or 7 hard drives should i need to re install the os. i still have the feeling that i am missing something (often called obvious but not obvious to me). 

keep those ideas coming in. i think there is only a finite (and not all that large) number of possibilities of why this equipment is behaving this way.

i hate to "give in" and just reinstall. i am trying to learn.

thanks again

---

### Post by kennethconn on 2012-08-11
Well you've certainly tried quite a bit, and you are right not to give up on it. You will learn more from this and it will really help going forward.
 
I would say you still have too much in the mix. Don't worry about the internet or the router (or DHCP) yet. See if you can get a laptop to communicate with the server when both have static IPs (using the switch or crossover cable would be even better, as sometimes switches can have uplink/special ports).
 
A few other things I would check (perhaps you have already done so):
Did you do anything with the firewall on the server some time ago?
Have you tried the onboard NIC again?
Are you using hostnames or IP addresses when you ping etc?

---

### Post by jocatoth on 2012-08-14
thanks for you suggestions.

i hooked up a cd rom and booted the equipment into a live linux cd. when i did this i did not get a network connection. 

i tried a different network card and still got no network connection

i tried both nics in a different pci slot and still got no network connection

today i purchased a crossover cable.

i do have several questions about this avenue. how should i try to connect? from the laptop to the server?

do i use a browser or do i use a terminal program like putty?

thanks

jocatoth

---

### Post by kennethconn on 2012-08-14
The crossover cable allows for a network connection between two PCs without the need for a switch or hub.
 
Plug directly into each PCs network card and you should be able to ping the other machine (by IP address) from command line. So it is a direct connection via network cards.
 
The fact that your liveCD is having issues with the server and networking, I would try the crossover cable between two PCs that you know are working fine (not the server).
 
From what you've indicated, it is looking more like a configuration issue as opposed to a hardware one.

---

### Post by jocatoth on 2012-08-14
just to be clear i ran a desk top live cd on the server's hardware and could not get any type of network connection.

this suggests to me that it is a hardware problem.

i will try the crossover cable

thanks for you help suggestions and encouragement
j

---

### Post by jocatoth on 2012-08-15
after the last round of using a desktop live disk testing of my server hardware i had a growing suspicion that my hardware was not right. i talked this over with my son who is getting to be tech savy. we repeated testing cables with a inexpensive cat 5 testing device. the in wall cable as well as patch cables passed the testing. however a laptop would not connect with the in wall cable + the patch cable. long story short i had an open short on a home-made cat 5 patch cable.

i am not sure i can explain how a patch cable can carry voltage or a little bit of current for the cable tester but not carry a signal that supports computer communication. i will leave that to the engineering typs to explain.

hopefully this may save someone else 15 hours of fooling around and two weeks of down time.

thanks again to all who gave suggestions and advice

jocatoth

---

### Post by kennethconn on 2012-08-15
I didn't think it was a hardware issue (as in server hardware). It can be very tough to troubleshoot when one of the things you have tested and ruled out later turns out to be the culprit. May be due to the fact that it was an inexpensive device. I don't use home-made cables anymore as they are so inexpensive now.
 
Glad it got sorted.

---

