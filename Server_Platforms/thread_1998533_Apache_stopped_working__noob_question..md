---
title: "Apache stopped working / noob question."
date: 2012-06-06
forum: Server Platforms
---

### Post by sona1111 on 2012-06-06
Hello, I just got myself completely worked up after i took a few hours trying to fix this and failed, now i have calmed down and come to you guys for help. :p While i am not an all out complete noob at ubuntu / linux, i am not that great either. 

Hardware is a IBM xseries 366 server, the only notable thing is that their are 8 gigabit ports installed. Software is ubuntu server version 11.10 

About a week ago i had a crappy ISP called earthlink that gave horrible speeds. With this setup i had the modem/router combo connected directly to the server by a LAN cable. It has a default ip of 192.168.3.1 and the server has a port configured with a static of 192.168.3.5 i told the modem/router to forward port 80 to 192.168.3.5 and all is well, the website on the server worked (slowly)

Then the isp got changed to comcast. They provide a device which is only a modem, no router. So i connected a router (grandstream HT-502 V1.1C, used on our network for Voip) in between the new modem and the server. I should mention at this point that the server was also being used as a traffic control/ftp server for all of the devices on the network. The other devices were connected to other ethernet ports on the server, which were bridged (using bridge-tools) to each other and another modem. This second modem was ditched when we upgraded to comcast, so now the website hosting is not separate from the bridge / all the ports but one are bridged (back to that "one" later), anyway the port that the cable going from the grandstream to the server used was 192.168.3.5 as well but i have tried troubleshooting this to dhcp and manual settings. The bridge port, br0, is set to a static of 192.168.3.82. I forwarded port 80 to this address in the grandstream and, when trying from outside of the network, the hosted websites worked fine. 

recently i got a comment that someone could not access them anymore. and sure enough, they were not working. The only thing that i have done in the last few days was to install transmission-daemon on the server, but it is bound to the other network port (the "one" port mentioned earlier, which is outside of the network bridge) I have removed it from startup just to be sure. I have been trying all sorts of ips and settings in the /etc/networking/interfaces file but with no luck so far. From outside the network i can ping the website (the comcast modem) fine. The problem is some setting either between the modem and router (unlikely) or between the server and router. (i also know apache is working correctly because from the other bridge devices i can type 192.168.3.82 and the website pops up)

I have had a few problem with this in the past, but usually i can just change the network connection to dhcp, reset network, and change it back to static and it will work. I think somehow adding the network bridge into the mix has caused a problem, but i am a newb at this, so maybe i am completely wrong. 

anyway tell me if you want me to post the interfaces file or another file. 

thanks...

---

### Post by CharlesA on 2012-06-07
Comcast blocks port 80 IIRC. Try switching the port forwarding from port 80 to port 8080 on the WAN side and see if you can access the site from outside your network.

---

### Post by sona1111 on 2012-06-07
Hello, thank you for the reply.

I tried switching the wan side to 8080, and this makes it so that i get the router configuration page from outside of the network. O_o

i then tried switching the routers web port to 81 instead of 80, but this just made it so i can not connect again. 

thanks again for the help.

---

### Post by CharlesA on 2012-06-07
> **sona1111 said:**
> Hello, thank you for the reply.

I tried switching the wan side to 8080, and this makes it so that i get the router configuration page from outside of the network. O_o

i then tried switching the routers web port to 81 instead of 80, but this just made it so i can not connect again. 

thanks again for the help.
What brand of router?

---

### Post by sona1111 on 2012-06-07
as stated in op, it is a grandstream HT-502 V1.1C. This has just one WAN and LAN port, and two phone ports. It was provided by our phonepower voip service, but it has all the necessary settings to be a router.  If you think it is the problem i can try a regular linksys wired router instead.

---

### Post by CharlesA on 2012-06-07
> **sona1111 said:**
> as stated in op, it is a grandstream HT-502 V1.1C. This has just one WAN and LAN port, and two phone ports. It was provided by our phonepower voip service, but it has all the necessary settings to be a router.  If you think it is the problem i can try a regular linksys wired router instead.
It would be a good idea to put a regular router in between the internet and the VOIP box.

The way I have mine set up - is to connect to VOIP box to the router via LAN port and leave the regular router to do all the traffic management.

---

### Post by sona1111 on 2012-06-08
sorry for the long reply, and thanks for sticking with me. (i have to wait for others to be offline before i can switch around anything.) I installed a "regular" router in between the modem and server. Its a linksys BEFSR41, not that new but should still be useful. Anyway comcast gave me a new IP so i was sure to stick it on "static ip" mode now. (if it would help with diag i can give the internet address info.) I set first a regular port 80 forward and then a port 8080. Neither did anything (timeout) I might also add that comcast's website states they do not block port 80. 

any more ideas?

---

### Post by CharlesA on 2012-06-08
Try double checking your port forwarding to make sure it is set correctly and then going to [http://canyouseeme.org/](http://canyouseeme.org/) and check to see if the port is open.

---

### Post by sona1111 on 2012-06-08
i believe the settings are correct , but i can send a few pictures if needed to verify. I have also disabled that "block anonymous internet requests" thingy. 

clearly something weird is going on. 

canyouseeme can not see both port 80 and 8080 when running from lynx on the server itself - even after i gave the server a DMZ (just for diag purposes)

---

### Post by CharlesA on 2012-06-08
Pictures would probably help.

You could always try a random high number port like 9900 and see what happens.

---

### Post by kennethconn on 2012-06-08
I read your first post and got totally lost - I think you need to re-evaluate (read simplify) your network config.

---

### Post by sona1111 on 2012-06-08
upon further research, i have found that the server linux will not actually connect to the internet at all through the network bridge. all the devices on the bridge can use the internet , but the server itself can not. This was masked before by that "one" connection (torrent connection) which is separate from the bridge. but after unplugging that and restarting, i can not get lynx or a simple apt-get to work. How can i get the bridge to correctly bridge the server into the..bridge. (lol) 

network config:

[http://pastebin.com/dkMdQGwc](http://pastebin.com/dkMdQGwc)

maybe this was the problem all along.

---

### Post by sona1111 on 2012-06-08
also i thought i should mention that in the first entry, (#Comcast Internet / Voip) I have tried that with other values but nothing changes even after a reboot of the server. I have tried static with ip 192.168.3.5 as well as the "manual" setting the other bridged connections have. 

Something is very strange about this situation because remember that other computers can connect to the website by direct ip from inside the network, and also ftp and other services work, so the server must be able to connect through the bridge. maybe the server requires nameservers somethere? what connection should i place them on?

---

### Post by sona1111 on 2012-06-08
yes, that confirms it. 

I just took all the other devices offline to check, this network config instead of the stuff in the other post, the website can connect fine. (on port 80) Any idea how i could get the bridge working correctly?


[LIST=1]
[*]# This file describes the network interfaces available on your system
[*]# and how to activate them. For more information, see interfaces(5).
[*] 
[*]# The loopback network interface
[*]auto lo
[*]iface lo inet loopback
[*] 
[*]# List of Network interfaces (hot plug)
[*] 
[*]#Comcast Internet / Voip
[*]auto eth9
[*]iface eth9 inet static

[*]address 192.168.3.82
[*]gateway 192.168.3.1
[*]netmask 255.255.255.0
[*]#network 192.168.2.0
[*]#nameserver 192.168.2.1
[/LIST]

---

### Post by kennethconn on 2012-06-08
I think CharlesA and myself meant a network diagram as in physical layout, cables connecting where etc (LAN/ WAN port of device). You are on the right path narrowing it down in this way taking unneccessary devices out of the picture, are you restricted to using a bridging set-up?
 
I'll be honest, I've never really needed to use a bridging set-up, but that was what I was getting at when I said to simplify things (standard LAN setup with a switch), and as I said in last post I got totally lost reading through your initial set-up.
 
Stick with it.

---

### Post by CharlesA on 2012-06-08
> **kennethconn said:**
> I think CharlesA and myself meant a network diagram as in physical layout, cables connecting where etc (LAN/ WAN port of device). You are on the right path narrowing it down in this way taking unneccessary devices out of the picture, are you restricted to using a bridging set-up?

Yep. I don't think I have ever needed to set up a bridged network, but that ifconfig output doesn't look right for bridged networking.

---

