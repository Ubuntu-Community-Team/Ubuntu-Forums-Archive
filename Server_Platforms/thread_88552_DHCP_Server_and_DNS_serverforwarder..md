---
title: "DHCP Server and DNS server/forwarder."
date: 2005-11-10
forum: Server Platforms
---

### Post by eldaria on 2005-11-10
I'm in the process of migrating my Windows server to Linux, and after finding Ubuntu I decided that this would be my platform, mostly becasue of the community, as I'm a newbie to linux, and will probably need a lot of support. :) 

Ok so to my situation.
I recently moved to another ISP, delivering me ADSL2+, but the router they gave me sucks big time, since it has a DHCP server that gives out new IP address everytime a client lease expires.

Also it does not support to assign Internal DNS entries.

Now that is not very handy when you have 6 computers, and 2 of them are servers.

For example currently my Windows server is running http and mail.
So if someone externaly types in [www.mydomain.net](www.mydomain.net) it will use external DNS servers and point it to my public IP address on port 80.
This also works with the new router, since at least I can do port forward, well it works until the router gives my server a new IP address.

But if I type [www.mydomain.net](www.mydomain.net) on one of the computers on the internal network, I get the router web config.

So I thought, that my linux box can take over the dhcp and dns.
Basically what I need is to set up a dhcp server where I can set that some computers always get the same IP address based on their MAC address.

But other computers that connect should just get assigned an IP.

Also for the DNS problem, I need that I can tell that local addresses for my domain, should be pointed to the internal ip addresses.

So I need that in the DHCP they get assigned the linux box as a DNS server, and also that the linux box then forwards DNS requests that are not from the internal network.'


Huff, ok hope I got that out somewhat clear. :-)

Best Regards.
Brian Levinsen

---

### Post by LordHunter317 on 2005-11-10
DHCP can do that , and it's explained in the documentation for dhcpd.conf.  Basically, you create a host entry with the mac address and a fixed-address directive.  

The only gotcha is that address should not be in the dynamic address range, if any exists.  So if you tell it to hand out dynamic addresses between 192.168.0.128 and 254, you should use 1-127 for static addresses.

---

### Post by eldaria on 2005-11-10
Ok, I think I got the dhcpd.conf file configured now.

But I just realized something, How do I configre my ubuntu server to use a static IP? And use the same address after reboot?

Also my second problem still needs solving, DNS?
How do I configure my Linux to serve DNS requests?

---

### Post by N8MAN1068 on 2005-11-11
For your DNS server, use Bind.
For static ip:
System-Administration-Networking-eth0(or whatever your interface is)-Properties, Change Configuration from DHCP to Static, then enter the correct info.

---

### Post by eldaria on 2005-11-11
Ok, thanks, worth noting that I'm rather new to Linux, and ok I will look up the man page for Bind.

The Server has no Gui, and my guess is the "System-Administration-Networking-eth0" is a reference to a gui somewhere.

Is there somewhere to do it from command line?

Thanks.
Brian.

---

### Post by N8MAN1068 on 2005-11-11
from a gui?
no clue.

---

### Post by LordHunter317 on 2005-11-11
Yes, read the interfaces(5) manpage and edit /etc/network/interfaces as apprporiate.

As for bind, don't even bother installing it until you've read and totally understand the DNS-HOWTO.

Please don't even bother asking questions about the HOWTO until you've read it at least twice.

---

### Post by Abhi Kalyan on 2007-03-15
There are two ways for remote operation on your ubuntu server, as you have said it does not have gui.
"sudo apt-get install Openssh "
Lets say your ubuntu server is "serv1"
Lets say your workstation is "wrkstn05"
so from a terminal in "wrkstn05" type
ssh root@serv1 -X
When asked for password, type in the root password of "serv1"
now you are logged into your server remotly.
Type in any command and VIOLA you have it as a GUI on your screen.

the next best thing is "webmin"
its great give it a try
Cheers
Please do post back on what happens.
Note: Am not very sure if ssh with "-X" will work if you dont have gui on your server so check it out
Thank you

---

### Post by eldaria on 2007-03-15
Hehe Old thread ressurected. :-)

Since last my new Ubuntu server has been running fine and is happily serving both Web and Mail.
I bought another router instead of the one they gave with me, and Are using the Router to server DHCP, and providing DNS.

I also learned a lot about linux since, and now the only Windows I'm running is in a Virtual Machine and with Crossover Office.
My Laptop and My Desktop is running Kubuntu Edgy, and the server is running Ubuntu Dapper.
I use ISPconfig for administrating the server, when I'm not using ssh.

oh and ssh -X will only work if you have a GUI installed on the server, wich I don't. :-)
thanks though.

Regards
Brian.

---

### Post by Abhi Kalyan on 2007-03-16
Dear Eldaria,
WOW, i just came along. All the above knowledge has helped me. Thank you for replying.
And thank you for :
"oh and ssh -X will only work if you have a GUI installed on the server, wich I don't.
thanks though."

I really did not know, but now thanks to you, i do.
All the Best, Thank you

---

### Post by eldaria on 2007-03-16
> All the above knowledge has helped me.
Great. :-D

Enjoy the experience, I know I did. :-)

---

