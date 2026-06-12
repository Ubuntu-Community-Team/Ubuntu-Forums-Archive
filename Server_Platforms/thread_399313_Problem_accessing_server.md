---
title: "Problem accessing server"
date: 2007-04-02
forum: Server Platforms
---

### Post by chr0nik on 2007-04-02
Hello,

I've been reading the forums for a long time but this is my first time posting here and I hope this is not the last time :-). My problem is that I have a ftp server and a ssh server and those are both visible and accesible within the network but whenever I try to connect from the internet, it's not possible.

My server's IP is 192.168.0.86 and I have a Dynamic DNS from DysDNS and whenever I tried to connect through the DNS name, it would connect me to the router.

Can anyone please tell me how can I "link" the server IP (192.168.0.86) to the DNS name so I can access it from the internet.

Thanks everybody!!!!

Chr0nik

---

### Post by huygens on 2007-04-02
From what I understood from you, you have a router connecting you to the internet. This router simply does not allow traffic coming from the internet to reach your box, unless your box asked for it (for example, when you browse the internet).


So you need to tell your router to do port forwarding. Basically, you tell your router to forward any incoming request from the internet on the FTP, SSH, etc. port to your box address (the one which you give the IP address in your original post).
FTP uses mainly port 21 and 20 in passive mode, it will be more complicated in non-passive mode, SSH uses port 22.
So for SSH, you should ask your router to forward incoming connection on port 22 to the IP 192.168.0.86 to port 22.

N.B.: if you use DHCP (dynamic IP address) for your computer, you might want to use its hostname for the port forwarding rather than its IP which could be subject to changes.

I cannot help you further now, because I would need confirmation from you that you really have a router. And furthermore, the port forwarding configuration is in word similar from one router to the other, but in exact actions might slightly differ. So if you do not find out, we will have to know what type of router you are using.

---

### Post by chr0nik on 2007-04-02
Thanks for the reply, I have fowarded the SSH port on the router that I'm using (Netgear Super Wireless ADSL Router DG834GT). What I would like to know is how can I "link" the Dynamic DNS name to 192.168.0.86 so that I could access the SSH or any other services from the internet.

Thanks!

---

### Post by huygens on 2007-04-02
You will not be able to link the DynDNS to your local address (a.k.a. 192.168.0.86). Because this address is "local", meaning it exist only at your place.
You should link the DynDNS name to the IP address of your router. Your router might provide this facility automatically (yep! just find out...)
If you have the documentation of your router, check page 7-7 the chapter about Dynamic DNS and follow its instructions.
If you do not have it, you cal download it (in English) here: [http://kbserver.netgear.com/products/DG834GT.asp](http://kbserver.netgear.com/products/DG834GT.asp)

Basically, in the Dynamic DNS configuration area of your router, you select DynDNS (if it is your dynamic DNS provider), for the host, you type the hostname you have chosen (e.g. mybox.dyndns.org) and finally your username and password.
After enabling this, each time you start your router (or it is renewing its internet address), your router will connect to dynDNS (or another equivalent) to update the IP of your router, so that you can reach your home computer from internet.

:-)

---

