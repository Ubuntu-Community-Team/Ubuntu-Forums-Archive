---
title: "DHCP not found"
date: 2009-12-17
forum: Server Platforms
---

### Post by Robert98374 on 2009-12-17
Ahlo!

For some reason my newly installed Ubuntu server has issues with connecting/finding the DHCP. I the computer was able to setup the DHCP at my house and when i brought over the computer back to work for my boss it worked fine. Once we established that it was working i left for the night, when i came back this morning it would not recognize DHCP. Tried a fresh install and its having the same issue, with automatically configure. When i manually enter in the information it still doesn't agree with settings. 

Its Ubuntu 9.10 server edition 86x if that would make a difference...

---

### Post by oneloveamaru on 2009-12-17
I don't really understand the problem. The Ubuntu Server is looking for DHCP to obtain it's IP address, or the Ubuntu Server IS the DHCP server?

---

### Post by Robert98374 on 2009-12-18
The ubuntu server is looking for the DHCP to obtain it's IP address. I am getting ready to hook up the server at my house to see if theres something that went wrong with the network cable at my work during the night.

---

### Post by Robert98374 on 2009-12-19
OK, so i reinstalled Ubuntu server at my house. It automaticly picked up the internet at my house and i am in fact writing this from the server. The second part of the issue now is that this server is supposed to have a static IP and i went through and configured that through the Network manager, enabled it to be the default connection. I dont see the option to switch to that connection instead of the DHCP connection that was automaticly setup.

---

### Post by Iowan on 2009-12-20
I still have a hard time connecting Network Manager with a server - just seems wrong. ;)
Not sure about Karmic, but Jaunty had an option to Connect automatically on network connections. You should be able to disable that function on Auto eth0 and enable it on the static configuration. 
(Forgive/ignore me if Karmic configuration is completely different.)

---

### Post by Skidbladniir on 2009-12-21
Static ip:

(Substitute VI if you have another editor)

sudo vi /etc/network/interfaces

auto eth0
another line ... dhcp <- Change to 'static'
address 192.168.1.X
gateway 192.168.1.1
network 192.168.1.0 <- Don't take my word for that - I seem to have a lot of IP trouble.  x|
netmask Obtain from network admin (you can usually get it from your router login, or contact your ISP)

---

### Post by Robert98374 on 2009-12-21
The weird thing is that it shows that the eth0 has never been used, tho i am on the internet....i read a post that another person was having a similar issue where they were connected to the internet but network manager doesnt show they are. It seems like this is right along those lines because there doesnt seem to be an active internet....even tho there is....Im not to worried about setting the Static IP, i am assuming that if i/we can figure out why its not showing an active internet connection i will be easier to go from there.

---

### Post by Iowan on 2009-12-21
What is in */etc/network/interfaces*? If eth0 is defined there, NM won't touch it - or isn't supposed to touch it...
Comment out the definition if you want NM to manage it.

---

### Post by Robert98374 on 2009-12-21
Iface eth0 Inet dhcp

How would i comment it out?

---

### Post by Robert98374 on 2009-12-21
Alright so with that commented out, it now allows me to connect to the static IP, and then to the router at work. Past the router is a different issue tho, it shows it connected but not able to access the internet. Any suggestions?

---

### Post by Robert98374 on 2009-12-22
So what does Ubuntu use to connect to the Internet when it doesn't have gnome installed? And how can i check those settings?

---

### Post by Robert98374 on 2009-12-22
So instead of setting up the Static IP i removed Network Connection Manager and just manually edited the /etc/network/interfaces. its now running like a champ.

---

### Post by Iowan on 2009-12-23
Glad you got it... sometimes the old ways are still the best.
Give it a couple of days to insure the problem is fixed, then use Thread Tools to mark thread [SOLVED].

---

