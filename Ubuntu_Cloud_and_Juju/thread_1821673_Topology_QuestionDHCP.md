---
title: "Topology Question/DHCP"
date: 2011-08-09
forum: Ubuntu Cloud and Juju
---

### Post by Dori922 on 2011-08-09
Hey dudes,

Im running this topology for my first UEC cloud and just want to double check that its sound.

I have 1 front end with 1 Ethernet port and 1 Node with 1 Ethernet port.

Both machines are connected to a home router along with some other non-cloud, PC's, Laptops and other devices.

The home router is connected to an ISP's DHCP server which gives our machines their IP info.

Do i need to do something special to make this topology work, will it just work, or do i need to buy, for example another NIC card to make it work?

Your's,

Adam Miller

---

### Post by Rusty au Lait on 2011-08-14
Need more information.
You want to have each instance be assigned an IP from your ISP upon startup?

Do you have exclusive use of the IP's that are assigned to you?

Can you switch your router to perform NAT?

Worst case.
one more nic for the CLC and a router.

---

### Post by Dori922 on 2011-08-15
I have 1 public ip that my ISP gives me. Im using my home network with a Netopia router.

The way this network is working right now i access the instances via:

ssh -i ~/.euca/mykey.priv ubuntu@172.19.1.x

this works fine for the LAN, but eventually i want clients to be able to SSH into instances through the internet but because i only have private IP's assigned to the instances i dont know how to access them from outside the LAN :(

My router shows these NAT options: 
[SIZE=2][COLOR=white]**NAT**[/COLOR][/SIZE]   [[SIZE=2]Pinholes[/SIZE]]("http://192.168.1.254/Pinhole"),    [[SIZE=2]IPMaps[/SIZE]]("http://192.168.1.254/IPMap"),   [[SIZE=2]Default Server[/SIZE]]("http://192.168.1.254/NATDefault")

---

### Post by Rusty au Lait on 2011-08-18
If you want more that one web server on your single IP address you must use different port numbers to access them. From the internet your clients must enter something like this:
[http://nnn.nnn.nnn.nnn:81](http://nnn.nnn.nnn.nnn:81)
for your second web server and
[http://nnn.nnn.nnn.nnn:82](http://nnn.nnn.nnn.nnn:82) for your third; etc.
Set your router up to direct port 81 to the second instance and port 82 to your third; etc. nnn.nnn.nnn.nnn is the IP your ISP gave you.
Your next problem is how do you keep the public IP for each instance the same every time you launch that instance. In the default mode UEC will supply the starting instance with a new public IP address that may not be the same every time you launch the instance. You may be able to do that but it is not a trivial matter.
Sorry

---

### Post by Dori922 on 2011-08-22
thanks bro :D guess ill use ports :P cover them with a domain name to make em look nice :)

---

