---
title: "cloud file server newb"
date: 2011-09-10
forum: Server Platforms
---

### Post by colm1749 on 2011-09-10
im trying to use ubuntu server to create a file server accessible over the internet. i installed ubuntu server onto an old computer and plugged in an external hard drive via usb. i have it setup as an ftp server but i can only access it over my home network. i found a gude to set a static ip address ([http://www.ghacks.net/2009/03/30/configure-static-ip-address-in-ubuntu-server-810/)]("http://www.ghacks.net/2009/03/30/configure-static-ip-address-in-ubuntu-server-810/") but i don't know what to put in as the ip address. can i just make up a number? also how can i set it up to store stuff on the external hard drive? 
sorry if its a dumb question im new to Ubuntu in general.

---

### Post by Wayne_V on 2011-09-10
no, you can't just make up a public IP.   your ISP should assign you one, whether static or dynamic.   if it is a dynamic IP you can use a DDNS service to map that to a static name.

once you know the public IP you must open the ports on your router/firewall you need and forward them to the internal server running the services.

---

### Post by zackwasa on 2011-09-10
to make the files available over the internet you can do so either using a FTP server, web server or using samba shares

try googling for all these for more info

---

### Post by colm1749 on 2011-09-10
> **Wayne_V said:**
> no, you can't just make up a public IP.   your ISP should assign you one, whether static or dynamic.   if it is a dynamic IP you can use a DDNS service to map that to a static name.

once you know the public IP you must open the ports on your router/firewall you need and forward them to the internal server running the services.

thanks so much for the help, i forwarded the port i needed and got a domain name set up thru dyndns.com. all went well connecting to it over my home network but i tried to connect over a different network and it said "connection denied" any ideas as to what i did wrong?

---

### Post by egpetrich on 2011-09-11
It's not clear to me from your post whether your server computer has a static IP address on your local (i.e. home) network. If you don't have a static local address, then you should configure one as described in the document you reference.

When you say that all went well connecting over your home network, did you mean that you tried connecting to "yourdomain.dyndns.com" and it worked?

---

### Post by colm1749 on 2011-09-12
yes, i connected to my dyndns domain from my home network and it worked, i was able to run commands on the server. when i tried from a different network if told me connection denied. and yes i have set it up to have a static ip address of 192.168.1.105 if that's what your asking.

---

### Post by dudumomo on 2011-09-12
Check your firewall if the required ports are open and redirected to the correct IP (92.168.1.105)

And by the way, to get something nicer than just FTP or Samba shares, I strongly recommend you AjaXplorer. It's a great project.

---

### Post by egpetrich on 2011-09-13
> **colm1749 said:**
> yes, i connected to my dyndns domain from my home network and it worked, i was able to run commands on the server. when i tried from a different network if told me connection denied. and yes i have set it up to have a static ip address of 192.168.1.105 if that's what your asking.
When you say that you were able to run commands on the server, does this mean that you were logged in via SSH? If not, what program were you running?

I do find myself wondering if your ISP is limiting the ports that you are allowed to connect to. When you try to connect to your dyndns domain from your home network, dyndns will give you the IP address that your network router has been assigned. From there, your connection attempt would go out through your router and turn around immediately to go back through your router to your server.

Your ISP may enforce some port restrictions upstream from your router. If so, you'd only see them when trying to connect from outside your immediate subnet. If you know of a neighbor who uses the same ISP, you could ask him/her to try connecting to your dyndns domain. If that connection succeeds, then I'd say you have some upstream filtering going on.

---

### Post by colm1749 on 2011-09-14
i think ive found my real problem. i thought i had configured my server to have a static ip but i ran a network sniffer on another computer and found that it didnt keep the same ip. my [I]/etc/network/interfaces file looks like this...

______________________________________________________________________________________
[/I]# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5).  

# The loopback network interface 
auto lo 
iface lo inet loopback  

# The primary network interface 
 auto eth0 
  iface eth0 
  inet static  
   address 192.168.0.103 
   netmask 255.255.255.0  
  network 192.168.0.0  
  broadcast 192.168.0.255 
   gateway 192.168.0.1
______________________________________________________________________________________

and i found when i run a network restart i get an error now "SIOCDELRT: No such process" could i have the wrong netmask or broadcast? (i copied the interfaces config file from a guide site and changed the address to what i wanted so i might have done it drastically wrong. 

also thanks for the other recommendations especially "AjaXplorer" looks like just what i need once i get this up and running

---

### Post by egpetrich on 2011-09-17
I get a static IP address with this:
```
auto eth0
iface eth0 inet static
  address 192.168.0.7
  netmask 255.255.255.0
  gateway 192.168.0.6
```
I'm not sure if "inet static" has to appear on the same line as "iface eth0"; the man page talks about "stanzas", implying that you can split across multiple lines, but all examples that I have seen use a single line "iface eth0 inet static".

I'd avoid using the "network" and "broadcast" commands, since they can be inferred from the address and netmask.

Also, you can see what address you've been assigned by entering the command "ifconfig eth0". Then you won't need another computer. (Oh, yes. Make sure that the address you're using isn't being used by another computer. If you have a DHCP server running on your home router, which is likely the source of your dynamic addresses, you'll need to adjust its settings to provide yourself a range for static IP addresses.)

---

### Post by colm1749 on 2011-11-15
the server is now set up with a proper static local ip address and i have my router set up to forward port 22 to 192.168.1.105 and set to update to dyndns.com but when i try to connect to the server via dyndns.com or just my networks ip address it says connection denied. i can ssh to it and log in just fine from my home network at 192.168.1.106 but the server blocks connections from any other network. i looked arround and found that usually this problem was due to open ssh not being installed but i checked the installations and they were good. any ideas what might be causing this? it bugs the hell out of me because i have everything else set up if i could just connect to it =/

---

### Post by Wayne_V on 2011-11-15
what happens if you run a port scan (common ports only):

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by colm1749 on 2011-11-16
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000060][**22**]("https://www.grc.com/port_22.htm")[/COLOR][/SIZE][/FONT] [IMG]https://www.grc.com/image/transpixel.gif[/IMG]
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000060]SSH[/COLOR][/SIZE][/FONT] [IMG]https://www.grc.com/image/transpixel.gif[/IMG]
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#003300]Stealth[/COLOR][/SIZE][/FONT] [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=1][COLOR=#000060]There is NO EVIDENCE WHATSOEVER that a port (or even any computer) exists at this IP address!

hmmm that the problem... but how would i fix it? could it be firewall settings? or is it something on the server itself?
[/COLOR][/SIZE][/FONT]

---

### Post by darkod on 2011-11-16
I don't know too much about servers but I noticed something in your post #9. You had dhcp address in the 192.160.0.x range with netmask 255.255.255.0.
Then you say you configured your server with 192.168.1.105.

You are aware that the mask on your router 255.255.255.0 doesn't cover 192.168.1.x but only 192.168.0.x?

You would need to use a mask of 255.255.254.0 to cover the range 192.168.0.1-192.168.1.254 if I am not mistaken. You will need to make this change in your router dhcp, and of course to set the address range smaller so that it doesn't cover all addresses from 192.168.0.1 to 192.168.1.254 otherwise it may allocate 192.168.1.105 to another machine.

Hope this makes sense.

---

### Post by Wayne_V on 2011-11-17
There does seem to be some confusion between 192.168.1 and 192.168.0 ... I would make sure that if you are setting a static 192.168.x.x IP on your server you make sure it is in the same domain as the router (better yet, just set it for dhcp and then tell your router to always give that IP to your servers MAC address).  Then make sure in your port forwarding you have external 22 routed to the correct internal IP.

---

