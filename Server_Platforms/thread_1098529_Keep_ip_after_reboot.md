---
title: "Keep ip after reboot"
date: 2009-03-17
forum: Server Platforms
---

### Post by kristensson.jonas on 2009-03-17
Hello everyone!
I have a ubuntu server here at home where i have set up a homepage. However I have it in a locker without a display and keyboard so everything I do, i do it over SSH. Sometimes i have to reboot my server and it is quite annoying when the computer then changes its ip adress. Is there any way i can make it static in the sense that I keep the same ip after a reboot?
Im running xubuntu at the moment (The computer is quite old).

---

### Post by yeats on 2009-03-17
You need to change the /etc/network/interfaces file to give it a static IP address.  Here's an example of the eth0 section of that file:

```
auto eth0
iface eth0 inet static
        address 10.0.1.15
        netmask 255.255.255.0
        network 10.0.1.0
        broadcast 10.0.1.255
        gateway 10.0.1.1

```

You would, of course substitute the correct addresses from your own IP range.  Then you'll need to restart networking by doing:

```
sudo /etc/init.d/networking restart

```

(This assumes you're using a terminal connected to the actual server, since after you restart, you will likely lose your SSH connection.)

---

### Post by sahabcse on 2009-03-17
Hi

Set auto eth0 in your /etc/network/interfaces

---

### Post by BkkBonanza on 2009-03-17
Keep in mind that if you are on your own network with a router gateway to the net then you may have other computers getting ips from the router via DHCP. If you need other addresses like that then you will need to make sure your router doesn't assign the static address you use for your server. Often you can still use dynamic addresses but set your router to assign a fixed address to your server machine (based on it's mac address). Check your router for how to config that or if it supports it.

---

### Post by MrWES on 2009-03-17
> **BkkBonaza said:**
> Keep in mind that if you are on your own network with a router gateway to the net then you may have other computers getting ips from the router via DHCP. If you need other addresses like that then you will need to make sure your router doesn't assign the static address you use for your server. Often you can still use dynamic addresses but set your router to assign a fixed address to your server machine (based on it's mac address). Check your router for how to config that or if it supports it.


Definitely the best way to go. Fire up your web browser and point it to [http://192.168.1.1](http://192.168.1.1) (usual address for your router gateway). Look for the 'device' listing and see if there is a 'static ip' option which is based on the MAC address of the card.

Bill

---

### Post by volkswagner on 2009-03-17
If you have a crappy router like mine (no static routes), then reduce the number of DHCP addresses, and use a higher or lower address for your static setting.

IE:  If your DHCP server on the router is set to dish out 25 DHCP addresses starting at 192.168.1.100, set it to 20.  This will leave 192.168.1.120-192.168.1.124 available for static addresses, not used by the DHCP server.

---

