---
title: "Wake on LAN not working..."
date: 2013-01-08
forum: Server Platforms
---

### Post by Mycah on 2013-01-08
I have  spent a couple of hours (at least) tonight trying to get this to work with no avail.

My situation:
I have a Gigabyte board that supports WOL and it is turned ON in the bios. I am running Ubuntu Server 12.10 and have edited my eth0 with ethtools so that it reads "g" and not "d" on the read out when I do ethtools eth0. I have forwarded ports 7 and 9 to my server.

My problem:
Firstly, I have tried over and over again to get a port checking tool to tell me that port 7 and 9 are open, but cannot get them to. This could be part of the problem, or it might just be that it is not listening properly. I have been unable to verify this. Ports like 80, 22 and 21 are all listed as "open," so there shouldn't be any real issue with my port forwarding. 

Secondly, I am using a Windows machine to send a magic packet. I have tried 2-3 different programs that do this, and none of them work. I am using the correct Mac address, and subnet mask is 255.255.255.0, and am using the internet address as my ip. This does nothing. I have been unable to verify whether or not it is being sent by the colors on my router or my port because A) the port on my board is always flashing orange and B) I only have solid colors on my router for all of the my connected computers.



I am sorry if this has been asked before, but I have searched and asked in IRC, etc, and have not been able to find a solution.

Any ideas??

---

### Post by volkswagner on 2013-01-08
Can you try from inside your LAN to see if the board will wake, thus eliminating firewall/ports as the issue.

I imagine that canyouseeme.org will not show the port as open because there is no service listening on port 9.

---

### Post by Mycah on 2013-01-08
> **volkswagner said:**
> Can you try from inside your LAN to see if the board will wake, thus eliminating firewall/ports as the issue.

I imagine that canyouseeme.org will not show the port as open because there is no service listening on port 9.

I've tried from within my LAN with the following settings in WOL - Magic Packet Sender:

Host name: (Server's internal ip)
Subnet Mask: 0.0.0.0
MAC Address: (Server's MAC address from running ifconfig)
Protocol: UDP
Port: 9 and 7

Nothing.

---

### Post by tgalati4 on 2013-01-08
You obviously haven't spent enough time on this problem.  I found that you need to keep power on the bus turned on that the network card hangs off of.  So even though the BIOS has WoL turned on, during standby, the bus powers off and the card never gets the power it needs to wake up.

[http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool](http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool)

---

### Post by egpetrich on 2013-01-09
You may have seen these already, but here are some threads that I found useful when I was getting WoL working:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

If you want to verify that your system is seeing the WoL packets, I recommend installing the "wireshark" package. It's a command-line logging tool, and the more you know about TCP/IP, the more useful you'll find it. Nonetheless, if you minimize the number of active systems on your LAN, you can at least monitor the network traffic and verify that the WoL packets are visible to your system.

I agree with the earlier post about ensuring bus power. This was a sticking point when I was working on my system.

---

### Post by Mycah on 2013-01-10
> **tgalati4 said:**
> You obviously haven't spent enough time on this problem.  I found that you need to keep power on the bus turned on that the network card hangs off of.  So even though the BIOS has WoL turned on, during standby, the bus powers off and the card never gets the power it needs to wake up.

[http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool](http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool)

While I assure you that I have read at least 12 articles on all things WOL, asked around in both the #ubuntu and #networking rooms on Freenode, and read several things about my particular motherboard, I have not run into anything about keeping power to the bus.

I will try this and see if it works.

---

### Post by pqwoerituytrueiwoq on 2013-01-10
you can't port forward a wakeonlan as it is a broadcast (i have been there and tried that several ways), i can login to my router and have it send a wakeonlan request as a workaround, i am using tomato firmware on my router

how to setup wakeonlan (use the manual section)
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

---

### Post by tgalati4 on 2013-01-10
```
sudo apt-get install acpitool
man acpitool
acpitool -e
acpitool -w
acpitool -W 5

```

Post the output of -w and change the "5" to the number of the device that you want to keep powered--preferably the PCI slot that your ethernet card is connected to.

```
lspci -vv
```

This will show a list of devices connected to the pci bus.

---

