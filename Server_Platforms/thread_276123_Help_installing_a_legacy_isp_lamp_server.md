---
title: "Help installing a legacy isp lamp server"
date: 2006-10-12
forum: Server Platforms
---

### Post by Vashu on 2006-10-12
Ok, for educational porpouses I revived and old PII computer with 128mb ram I used to own. Slapped and 10gb HDD and 2 network Cards.

My intention is to use it as a middle man between my internet and local lan to serve as a firewall/internet for the lan/dhcp server/ lamp development area.

I'm rather new to linux, but i've been using ubuntu desktop for 2 months windowless, and have picked up a few things or two.

Any tips on how to set up the server?

I was thinking about installing ubuntu server with the LAMP option. then xubuntu-desktop for easy management even thou i want to learn how to manage it  by CLI. 

Also how do i set up the network cards for the porpouses of having eth0 act as firewall, internet access and eth1 as dhcp server,isp server? 

Thanks in advanced.

---

### Post by Endwin on 2006-10-12
Ah the fun of the home router. Yes installing the ubuntu server CD with LAMP will get Apache, PHP, and MySQL on and ready to go for a server. If you really want to learn the command line, I would advise against it and just try to follow the guides on-line and here. (If you have the graphical UI you are more inclined to use it.

That said, if you want to install the xubuntu desktop...

```
sudo aptitude -R install xubuntu-desktop
```

Now as for DHCP and the router. Do you plan to also run a DNS server for the local LAN? Or do you just plan to pass through the DNS information from your ISP? 

For the firewall/NAT (Read shareing the net connection) IPTABLES handles this fine, however configuring is a nightmare by hand. I used shorewall and had mine up in under an hour.

```
sudo aptitude -R install shorewall
```

[http://www.shorewall.net/two-interface.htm]("http://www.shorewall.net/two-interface.htm") 

That site gives a great guide to setup Shorewall to handle the firewall and do NAT.

Once I know how you want to do the DHCP/DNS I can point to some guides on that as well.

---

### Post by Iowan on 2006-10-12
[http://howtoforge.com/perfect_setup_ubuntu_6.06]("http://howtoforge.com/perfect_setup_ubuntu_6.06")
[http://www.howtoforge.com/lamp_installation_ubuntu6.06]("http://www.howtoforge.com/lamp_installation_ubuntu6.06")
Here are some ideas - they seem to cover *most* of your questions.

---

### Post by Vashu on 2006-10-12
> **Endwin said:**
> Now as for DHCP and the router. Do you plan to also run a DNS server for the local LAN? Or do you just plan to pass through the DNS information from your ISP? 

Well i would like to able to surf the web and use p2p applications inside the local LAN, i was thinking about something like masking or fowarding, but i think thats what the dns server would do. My networking 101 is a little rusty.

---

### Post by Endwin on 2006-10-12
Endy's Networking 101
=====================
[B]
DNS = Domain Name Service[/B]

DNS is used to associate a name say [www.google.com](www.google.com) to an IP like 72.14.203.99. Since computers only understand IP numbers for networking and humans remeber names better then 12 numbers the DNS system was invented. When you get on-line your ISP provides you with some of it's DNS Server numbers to use. This lets your machine lookup names of websites. If the ISP's DNS server does not know it goes to a master DNS server and asks it. This can continue all the way up to the root domain servers for the entire net. 

How this can help you... 

You could set up a DNS server locally for your lan (like a mini ISP) that does the DNS for your lan when it dosn't know it asks the ISP's DNS server and so on. This can be helpful for naming your machines on the LAN or providing a temp backup when the ISP's DNS servers go down.


[B]DHCP = Dynamic Host Configuration Protocol 
[/B]
DHCP is a cool little service that gives an IP, gateway (Read: computer to get to the net on) and DNS servers to machines that join a network. Many ISPs run DHCP servers since they are easier then asigning and configuring a customer with a static IP, an IP that does not change.

Many people at home buy little routers that do this for them and it is one of the easiest way to manage IPs for a LAN. Additionally if you run your own you can set it up so that it will update the DNS server you own with the IP of the client that just joined so that you can always refrence it by name even when the IP changes.  For example say you computer's nam is CookieMonster whose IP is 192.168.0.10 The DHCP server will update the DNS so that other machines on the network can just type in CookieMonster and get that machine. If the IP changes to say 192.168.0.14 it is updated and you don't need to keep track of it.

[B]
NAT = Network Address Translation[/B]

NAT, also called IP Masquerading, is done by firewall software to modify packets (bits of information on the net) so that multiple computers can share the same internet connection. It tracks connections and makes sure that if a computer on the inside asks for website A and another one for website B they both get the correct site. In Ubuntu NAT, and firewalling are both done by IPTABLES, a program, however it is hard to write all the rules for it and many people have written front ends to handle it for you. I suggested shorewall as one of those frontends because I found it stright forward, easy to understand and very powerful at the same time.

If this or any other terms need further clerification please ask :D

---

### Post by Vashu on 2006-10-12
Ok. I dont really have any interest in running a DNS server for the lan, NAT and DCHP would  be more than enough. It's a shame I have to wait until later tonight to get working. Since I have no access to the server from work. Meanwhile i'll start making my check list.

[X] Ubuntu server - Lamp Install
[ ] xubuntu-desktop with a gui i have access to more software than just cli. And monitoring gets easier too.
[ ] firewall and fowarding via iptables/shorewall 
[ ] DHCP maybe following ubuntuguide.org

---

### Post by Endwin on 2006-10-12
Well once this is done you can. In that case you will just want to install shorewall and dhcp3-server when you get home. The guide above should help for shorewall. Copy down your ISP's DNS servers for when you configure the DHCP server. The server config is located in /etc/dhcp3/dhcpd.conf

[This site]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html") gives a good basic example of setting up a DHCP server locally. Feel free to ask questions if you get stuck.

---

### Post by Vashu on 2006-10-13
OK. here's my progress report:
[X] Ubuntu server - Lamp Install
[X] xubuntu-desktop with a gui i have access to more software than just cli. And monitoring gets easier too.
[ ] firewall and fowarding via iptables/shorewall
[X] DHCP maybe following ubuntuguide.org

The computers on my lan are now getting their network setup from the server :D. And they can also see the default apache webpage if directed to the server's ip on a browser (duh). I'm running xubuntu desktop but im thinking of making it not boot by default. and only startx when i really need it. Also i can access by ssh from inside pc's.

shorewall is kind of giving me troubles thou. not even with sudo i can access the directory where the configuration files are at (dunno why) so i cant see if they are there or edit them. Also its a little confusing as some files it says will you have to edit are nowhere to be found.

Since its a little late (xubuntu took a long time to install) i'll continue on tomorrow night.

Edit: Managed to share internet connection, but I still have a lot of reading left to do in order to set it up to my liking. (Ie. Bittorrent isnt working very well.)

---

### Post by pppetter on 2006-10-13
Vashu, bittorrent will work when you have configured shorewall to forward a specific port of your choice to the IP of your choice and set bittorrent to use the same port, remember that the your computer need a static IP.

However I'm not familiar with using shorewall so I can't tell you how to use configure it :/

---

### Post by Endwin on 2006-10-13
In order to edit the files and get to the directories with the shorewall data you need to be in a root shell.

```
sudo su - 
```

That command will give you a root shell. By default there are not may config files in **/etc/shorewall** There are only three. You need to copy the modules file over to this directory.

```
cp /usr/share/doc/shorewall/default-config/modules /etc/shorewall/.
```

Once done since I presume you want to do a two interface setup (One connection to the outside and another to the inside) copy over the files for that.

```
cp /usr/share/doc/shorewall/examples/two-interfaces/* /etc/shorewall/.
```

There you have all the files you need to edit.

There rest of the guide at 
[http://www.shorewall.net/two-interface.htm]("http://www.shorewall.net/two-interface.htm")
should be fairly streight forward from there. make sure to do gzip -d on the files with a .gz extension.

To forward bittorent know the IP of the local machine and edit /etc/shorewall/rules

---

