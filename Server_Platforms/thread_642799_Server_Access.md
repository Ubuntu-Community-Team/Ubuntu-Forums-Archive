---
title: "Server Access"
date: 2007-12-17
forum: Server Platforms
---

### Post by expatCM on 2007-12-17
I rebooted my server yesterday.  Today three of four clients still function as normal. The client I use cannot access the server.  The services used are SSH (PuTTY), Squid, Cups and Webmin.  All nothing doing and generally it appears that everything times out.

If I ping the server IP this does not seem to do anything ....  I have not waited for more than a few minutes to see if it eventually times out but immediately it just hangs...

I do not understand what is wrong since the other clients are working normally.  No changes have been made.

How do I fix this or at least work out what is the problem?

---

### Post by HermanAB on 2007-12-17
Check your network settings.  Ensure that you are in the same subnet as the server.

---

### Post by expatCM on 2007-12-17
subnet on both client and server is 255.255.255.0

I added another Ethernet card to the server a day ago.  I am certain that the services were all working after this but is it possible there could be any related effect?  Does not seem like it since the other client machines work but I mention it just in case.

---

### Post by expatCM on 2007-12-17
I have just removed the newly installed network card and all is back to normal operation.  

With the card in place it appears to be correct if I look with ifconfig but obviously is not.

What is the correct way to install a new NIC on a server please?

---

### Post by crouton on 2007-12-17
1) Install NIC and remember what it is (D-Link, 3com, etc) so you can tell that it is detected correctly.
2) Check dmesg (dmesg | grep eth) to see which interface the new card is assigned.  For this example I used eth1.
2) sudo edit /etc/network/interfaces (use whatever program you like):
  you want to add 'auto eth1' and 'iface eth1 auto dhcp' if you are using DHCP, or 'auto eth1' and 'iface eth1 auto static' for static IP.
3) for static you will need 3 further lines:
  address aaa.bbb.ccc.ddd
  netmask eee.fff.ggg.hhh
  gateway iii.jjj.kkk.lll

4) 'sudo /etc/init.d/networking restart' to restart networking.

---

### Post by expatCM on 2007-12-17
well that is sad then ....  exactly what I did and ifconfig shows the NIC correctly. So at this point I can rule out any hardware error (such as defective motherboard or NIC).

But ...  ssh / squid / cups ...  cannot then be accessed.  The server runs but the services cannot be accessed.

So there has to be some other reason. 

I can recall the first time that I used PuTTY that I needed to accept some form of certificate in order to access the service.  Is there any possibility that this is certificates related?  Would adding a NIC change the nature of the certificates?

---

### Post by now-new on 2007-12-18
check your Ips  is it dynamic? what if it changed already and/or your httpd.conf  maybe something it misspelled

---

### Post by expatCM on 2007-12-18
static IP - nic 1 192.168.1.98, nic 2 192.168.1.99.  Same subnet.

Please tell me about httpd.conf since I did not make any edits to this file.  Should I have?

---

