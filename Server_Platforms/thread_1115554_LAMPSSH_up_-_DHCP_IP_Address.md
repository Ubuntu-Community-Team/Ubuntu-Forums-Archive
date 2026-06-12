---
title: "LAMP/SSH up - DHCP IP Address"
date: 2009-04-03
forum: Server Platforms
---

### Post by redonwhite on 2009-04-03
Hello all,

I recently reinstalled ubuntu 8.10 server edition with no GUI this time.  I followed the directions from this site [http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)  . Although the installing is pretty self explanatory.  I have two questions. 

1.  Toward the bottom of the Link's Guide he tells you to change your IP address to a Static IP address.  Why is that?  Is a static IP address more secure?

2.  Also around that same step the person says how neat it is that it shows his CPU,Memory,Disk,Swap,No.of processes,No.of users logged .  When i boot up i don't see this on the screen.  Is there a certain command i need to run to see this informations.

Thank you for your time.

---

### Post by BkkBonanza on 2009-04-03
Static because that means the ip stays the same - doesn't get changed by your isp. That's pretty important for any server as otherwise you can't contact it - unless you also configure dynamic dns.

I don't know about that stats info - mine never did it. It could be done by putting some commands in the /etc/motd.tail file. But it's easy just to ask at any time and knowing it at boot is kinda useless anyway. To get a decent view of the system try using,

top

I'm sure there's others too. I actually use htop but it has to be installed first.

---

### Post by redonwhite on 2009-04-04
> **BkkBonaza said:**
> Static because that means the ip stays the same - doesn't get changed by your isp. That's pretty important for any server as otherwise you can't contact it - unless you also configure dynamic dns.

I don't know about that stats info - mine never did it. It could be done by putting some commands in the /etc/motd.tail file. But it's easy just to ask at any time and knowing it at boot is kinda useless anyway. To get a decent view of the system try using,

top

I'm sure there's others too. I actually use htop but it has to be installed first.

Thanks for the info.  I thought i had DHCP enabled but every time i check my IP on my Server box its always the same.  So i guess its already set to static?  Thanks again.

---

### Post by BkkBonanza on 2009-04-04
DHCP will assign the same address usually even when it's not static if the network isn't changed. That's simply due to using the same algorithm to assign the addresses. You can tell your DHCP server to make a given machine (by MAC) static. In which case it will assign dynamic addresses to everyone but always make sure it assigns the same one to that machine. This is called a static lease in the DHCP config.

Keep in mind that this address is only for use locally on your LAN. Any public ip that would be used by someone on the internet is a different thing. That one is assigned by your ISP (not your own DHCP) and typically (unless you pay extra) is dynamic and because they have many clients almost always changes.

---

### Post by cariboo on 2009-04-04
See the screenshot for what I see when I login remotely to my server. the stats are not all that accurate, my system temp is actually 24°C but the hard  drive space seems to pretty close for /home, but is off by about 10% for /home/storage.

Jim

---

### Post by redonwhite on 2009-04-04
> **BkkBonaza said:**
> DHCP will assign the same address usually even when it's not static if the network isn't changed. That's simply due to using the same algorithm to assign the addresses. You can tell your DHCP server to make a given machine (by MAC) static. In which case it will assign dynamic addresses to everyone but always make sure it assigns the same one to that machine. This is called a static lease in the DHCP config.

Keep in mind that this address is only for use locally on your LAN. Any public ip that would be used by someone on the internet is a different thing. That one is assigned by your ISP (not your own DHCP) and typically (unless you pay extra) is dynamic and because they have many clients almost always changes.

Thank you for the information.  So if I wanted to remotely access my server from out side of my own home network I would have to set up or pay my ISP for a static IP to access the server?

---

### Post by BkkBonanza on 2009-04-05
You have a couple choices. According to your isp rules the correct way is likely to pay more for a static address. But it's common for people to workaround this by using dynamic dns update services. You run a program (daemon) like ddclient and it checks your ip periodically to see if it's changed and if so then it sends an update to your dns service. There's an abundance of threads on here about that subject so if you want to go that way just do a search, "how-to ddclient". 

This isn't really suitable for 24/7 commercial sites since you can have brief outages, but it works for personal non-critical and test sites. If you are running a commercial site the best option is likely a small vps account in a good data center. Cheap, easy, as flexible as a dedicated server and usually reliable. But learning on a home server is fine.

---

### Post by redonwhite on 2009-04-05
> **BkkBonaza said:**
> You have a couple choices. According to your isp rules the correct way is likely to pay more for a static address. But it's common for people to workaround this by using dynamic dns update services. You run a program (daemon) like ddclient and it checks your ip periodically to see if it's changed and if so then it sends an update to your dns service. There's an abundance of threads on here about that subject so if you want to go that way just do a search, "how-to ddclient". 

This isn't really suitable for 24/7 commercial sites since you can have brief outages, but it works for personal non-critical and test sites. If you are running a commercial site the best option is likely a small vps account in a good data center. Cheap, easy, as flexible as a dedicated server and usually reliable. But learning on a home server is fine.

I will look into this ddclient.  Thanks for the knowledge and your time.

---

