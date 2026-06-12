---
title: "Random Network Disconnects"
date: 2011-09-12
forum: Server Platforms
---

### Post by bsntech on 2011-09-12
Hello all,

I've got an issue that doesn't seem to be going away.  Started last Friday out of the blue.

I have ping systems setup to monitor my servers and I have two servers that have begun to stop responding on the network for periods of five or more minutes - then come back online without any troubles.

Both servers are Compaq ProLiant servers with dual NICs on the board.

```
eth0      Link encap:Ethernet  HWaddr 00:13:21:0b:45:c9  
          inet addr:x.x.x.x  Bcast:x.x.x.127  Mask:255.255.255.128
          inet6 addr: <removed> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1472  Metric:1
          RX packets:594618 errors:190 dropped:0 overruns:0 frame:190
          TX packets:530666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197575194 (197.5 MB)  TX bytes:327792148 (327.7 MB)
          Interrupt:25 

eth1      Link encap:Ethernet  HWaddr 00:13:21:0b:45:c8  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:21ff:fe0b:45c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1472  Metric:1
          RX packets:779338 errors:6 dropped:0 overruns:0 frame:6
          TX packets:411034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204578954 (204.5 MB)  TX bytes:108012376 (108.0 MB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:217005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:217005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76103906 (76.1 MB)  TX bytes:76103906 (76.1 MB)

```

As you can see, I've even went as far as changing the MTU down to 1472 per another post I found that appeared to have the same problem.  Note that the errors shown above only began incrementing once I changed the MTU; when the MTU was set at 1500, there were not any errors.

Servers are connected to a switch and then there is a Cisco router that feeds to them to the Internet.  I've also hard-coded the MAC addresses of the server in the ARP table on the Cisco router thinking another computer may be infected and trying to steal the IP.

One NIC on each has a public IP and one NIC on each has a 10.0.0.x address - so that allows me to connect into one server and open a secure shell connection to the other.

When the public IP NIC goes down, so does the private IP NIC.  I can still connect to the other server during this time and try that - so it isn't affecting both servers at the same time - although it is affecting both.  Therefore that rules out anything with the Cisco router or the network in my opinion.

If it makes any difference, NIC 2 (eth1) is used as a bridge NIC for a virtual server run on the machine using VirtualBox.  What IS interesting is that I am able to ping and gain access to the VirtualBox server if I try to connect to that public IP address - even though I'm not able to ping the 10.0.0.x private IP assigned to that NIC from the other server.

Does anyone have any ideas what would cause this - and what kind of logs may show me what is going on?  I've looked at the /var/log/syslog but it doesn't tell me anything.

Thank you all!

---

### Post by Entilza on 2011-09-12
I don't think you are going to find anything in any logs with this type of problem you are going to have to do some old fashion manual debugging as this could be hardware related.

You are able to access the Virtual machine on server-A during this downtime?

- Try pinging the main computer from the router.
- Switch going bad since it affects other computer too?

Sounds like something with the routing paths.  Are you able to access the console on the machine during this time?

I would check the route and as much as possible during this time.  What about pinging from Server-A outbound during this time.

Sounds like you don't have much time to debug this when it happends as well, how often is it happening?  You might want to do some tracerouting as well during this time to see where it's trying to go.

Check any "dmesg" logs as well for hardware related errors but I doubt you'll find anything there.  Maybe check your router logs as well?  Goodluck this sounds like a hard one but if it happens often you should be able to debug this.  Sorry I don't have any definite answers.

---

### Post by bsntech on 2011-09-12
Appreciate the response.  I also believe it is hardware-related as it uses the tg3 driver.  I found online that others had the same problem.

On Friday, I set my replication to update between servers every 1 minute instead of every two minutes - thereby increasing the load on the card.

Others have mentioned that they encountered problems with the BCM5704 NIC as well with the same kind of issue - network randomly stopping when receiving data.

As for pinging the server from the router - did that - dead as a doornail.

I've thought about the switch going bad - but it only seems to affect my two servers.  There are other servers on the same switch that are unaffected.

Cannot access the console when the server is unavailable as I'm remote.  The routing is very simple with only localhost and default gateway routes.

---

### Post by Entilza on 2011-09-13
How often does it happen, you can set a script to test the pings running on the server so you can see the results from the server's point of view but if you can't ping it from the router that's not a good sign.

Maybe install one new e1000e card on one of the computers and see if that resolves it?

I'd set the replication back to 2 minutes in the meantime?

---

### Post by bsntech on 2011-09-13
Most likely is the next step is to put another NIC in the servers.

I ran all of the updates that were available last night on both servers.  Thus far, only one of the servers went 'down' overnight for a total of around 20 minutes (five minutes at four different times).  This is the server that has heavier replication than the other server.

---

### Post by bsntech on 2011-09-13
Speak of the devil - just changed replication and now it just went down again.. it absolutely must be something with the darn NIC and the tg3 driver.

Was down for about two minutes and it is now active again.

---

### Post by bsntech on 2011-09-13
Found another person that has the same problem indicate that the following command worked for them:

> ethtool -K eth[x] gso off

Going to try that on the server that has the most problems and see if this takes care of it.

---

### Post by rubylaser on 2011-09-13
If it's a production server, I'd just put a few [Intel PCI-e CT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106036") gigabit NICs in and be done with it.  I only run Intel nics in my machines, and they work fantastically.

---

### Post by bsntech on 2011-09-13
Looks like the ethtool command didn't work - just had a brief 5 minute outage again.

As rubylaser said, it is time to get new NICs.

---

### Post by bsntech on 2011-09-13
So I must use a PCI-X card - the one above that rubylaser provided won't work in the ProLiant DL380 G4 servers.

What about this cheaper one?  Someone says it works - wondered if anyone else had feedback.  The Intel PCI-X card is $130!

[StarTech PCI-X NIC]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833114006")

---

### Post by bsntech on 2011-09-13
A bit more digging and I uncovered this auction:

[HP/Compaq Intel 2-Port Gigabit NIC]("http://www.ebay.com/itm/HP-Compaq-Intel-2-Port-Gigabit-NIC-PCI-X-Network-NC7170-/120767416433?pt=LH_DefaultDomain_0&hash=item1c1e4c8871")

Now that I am thinking of it - the server had an extra PCI-X dual-NIC card in them.. will have to see if I still have them and if it is this model.  I took them out since I figured it was pointless having it in the server.

---

### Post by Entilza on 2011-09-13
Have you tried compiling the latest tg3 linux drivers from the website?  It's going to be tricky to install if you don't have console access.

---

### Post by bsntech on 2011-09-14
Alright - so I'm completely lost now.

Went to the location and put in some Intel cards that originally were installed in the servers - but I took them out since I didn't need four network connections.

The Intel cards are using the e1000 driver - as someone mentioned here was bulletproof.

Everything has been setup and is using the new cards - but there is still downtime for a couple of minutes several times a day.

So, I think I can rule out both a hardware and a driver issue since this has been changed.

The servers are running web services.  Anyone have any insight as to how I can continue to troubleshoot this?  I've looked at the logs and there is nothing in there about any kind of network disconnects.

---

### Post by Entilza on 2011-09-14
Early on you mentioned that you had 2 servers having this problem.  This could have ruled out the need to replace the NIC's but perhaps a switch problem?  At least you took one piece of the puzzle out, by swapping nic cards.

Later you mentioned on the friday you increased replication, was that to both servers or just one?

While you were on site did you have any freezes and were you able to access the console during the downtime?  Did you make a script to ping from the server point of view out and log it?  I would also log route and ifconfig from the server point of view every minute in order to make your own logs since you cant be there when it happens.

Keep it up you are getting closer to finding the problem :)

---

### Post by bsntech on 2011-09-14
Appreciate the responses.

Yes, so the NICs have been changed out.  I've set replication back to the normal time frames - but the problem continues.

One of the servers is three times as busy as the other one.  The most busy server is having the problem 12+ times a day.  The other server - so far - has not had the problem today.

I wasn't at the facility for very long when changing the NICs out; I just got the NICs changed, updated the IP information, and left - but there wasn't any issues while I was there for the 30 minutes.

Next step will be to make a script as you said.  I've even blacklisted the tg3 drivers and did a 'modprobe -r tg3' to disable it and the issue is still occurring.

---

### Post by bsntech on 2011-09-15
Problem appears to be solved.  Not the cause of the network card or anything OS-related.

The servers are sitting at a wireless ISP.  The servers are connected to a switch - which is then connected to a MikroTik router that is set in bridging mode and is simply acting as a bandwidth control unit (BCU) for the owner to limit download speeds for customers.

The MikroTik device is then connected to a Cisco router.

In the Cisco router, I did a static ARP mapping of the MAC addresses of the servers to the two servers - thinking something on the network was 'stealing' the IP address.

Both servers are connected to the same switch - and they are on the same network/subnet.

The ISP owner upgraded the firmware in the MikroTik device and consequently did a reboot.  After this was done, issue was solved.  He also had to reboot the device a few weeks ago when some of his customers were having difficulties - and the same troubles I am seeing now also occurred back then.

But - what I do not understand is WHY would rebooting that device fix the problem?  If both servers are connected to the same network switch on the same subnet, I should be able to ping the servers from each other.

The only thing I can think of is the MikroTik device was the culprit - and was broadcasting that it was the owner of the two server IPs and therefore was sending out it's MAC address when a arp request packet was sent across the network.  This is the only logical conclusion I can come up with because any computer that is on the same switch and the same subnet should be able to talk to one another - since the switch stores the MAC address(es) for each connected device - for each port on the device.

---

