---
title: "Server issue. Fixed IP"
date: 2011-06-04
forum: Server Platforms
---

### Post by keith_irl on 2011-06-04
Hello everyone.

I am a newbie to linux and running ubuntu server 10.10 (no gui)
I had it configured with a fixed ip address and all was fine till I changed internet poroviders and got issued with a new router.

I am trying to configure the server to reflect the new settings of the new service provider.

here are the contents of /etc/network/interfaces

```
auto eth0
iface eth0 inet static
address 192.168.15.52
netmask 255.255.255.128
gateway 192.168.15.1
```

Just so I got this right can someone tell me if I am right here.
address is the IP I wish to give to my server statically.
and gateway is the ip of the router.

When I try to ping the router I get ```
Ping 192.168.15.1 (192.168.15.1) 56(84) bytes of data.
From 192.168.15.1 icmp_seq=1 Destrination Host unreachable
```

When I try to ping the internet i get : ```
ping: unknown host google.com
```

Here are the results of netstat -r 
```
Destination   Gateway   Genmask   Flags   MSS Window irtt Iface
192.168.15.0    *   255.255.255.128   U   0 0   0  eth0
192.168.122.0   *   255.255.255.0     U   0 0   0  vibr0
default         *   0.0.0.0           UG  0 0   0  eth0
```

In /etc/resolf.conf my file looks like this. 
```
nameserver 89.16.72.129
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Is there anyone that can shed some light on where my problem may be.
As i said before I got the new router I had been working with the server no problem.

Thanks guys in advance.

---

### Post by amauk on 2011-06-04
Try changing your netmask so it looks like this
> **keith_irl said:**
> ```
auto eth0
iface eth0 inet static
address 192.168.15.52
netmask 255.255.255.[COLOR="Red"]0[/COLOR]
gateway 192.168.15.1
```

I'm not 100% sure, but I believe that a netmask of
255.255.255.128
will only allow the machine to see IP addresses
192.168.15.129 - 192.168.15.254
Which means it cannot see the router (at 192.168.15.1), so no external connectivity

Change netmask to 255.255.255.0, and the machine can see all IPs in 192.168.15.*

---

### Post by alazou on 2011-06-04
I would guess there is a conflict of configuration between your ubuntu box and the router. but I can't be sure because I can't see the router configuration. Have you checked for exemple if the netmask match between router and interface file ?

-- edit
@arnauk : ho didn't see your reply. The way I understand it having the 128 split the network into 2 subnets so he should be able to see the gateway if he is in either one (I think), but wouldn't be able to see devices on the other subnet. But either way, he is in the first subnet because he has 52 as his last digit : from 2 to 127, but can't see the gateway...

---

### Post by keith_irl on 2011-06-04
> **amauk said:**
> Try changing your netmask so it looks like this


I'm not 100% sure, but I believe that a netmask of
255.255.255.128
will only allow the machine to see IP addresses
192.168.15.129 - 192.168.15.254
Which means it cannot see the router (at 192.168.15.1), so no external connectivity

Change netmask to 255.255.255.0, and the machine can see all IPs in 192.168.15.*

Thanks for your reply,

IO have just tried this but I am still having trouble pinging the router or internet. 

Thanks for your help.

---

### Post by keith_irl on 2011-06-04
> **alazou said:**
> I would guess there is a conflict of configuration between your ubuntu box and the router. but I can't be sure because I can't see the router configuration. Have you checked for exemple if the netmask match between router and interface file ?

Hi alazou, yes the netmask matches the one on the router. Attached here is a screen grab of my router settings.
Thanks again

---

### Post by alazou on 2011-06-04
But It doesn't match the local network subnet. So like amauk suggested you should change it to 255.255.255.0 in the interface file, unless you really need to split your network in 2, then you need to change the router configuration to 255.255.255.128.

Also on the router you have set a limit to the maximum number of device to 50. That means that your IP address you want for your box may not be valid. Try setting the limit to 254 if you want the 255.255.255.0 subnet mask, or 252 if you want the 255.255.255.128 subnet mask

---

### Post by capscrew on 2011-06-04
> **alazou said:**
> But It doesn't match the local network subnet. So like amauk suggested you should change it to 255.255.255.0 in the interface file, unless you really need to split your network in 2, then you need to change the router configuration to 255.255.255.128.

I would not suggest that.  The subnet mask sets the boundaries of the network.  All the hosts would need to be inside those boundaries. If you set it to 255.255.255.128 (/25) then all of the hosts need to be within the range of 129 to 254.> 

Also on the router you have set a limit to the maximum number of device to 50. That means that your IP address you want for your box may not be valid. Try setting the limit to 254 if you want the 255.255.255.0 subnet mask, or 252 if you want the 255.255.255.128 subnet mask

The 50 host limit is for DHCP assigned IP addresses.  The OP can still assign addresses statically as they have done.

---

### Post by alazou on 2011-06-04
> **capscrew said:**
> I would not suggest that.  The subnet mask sets the boundaries of the network.  All the hosts would need to be inside those boundaries. If you set it too .128 then all of the hosts need to be within the range of 129 to 254.
I wouldn't recommend it either, but I think it is still possible to be in the 2 to 127 address range too. I had this kind of configuration for a while. there is 7 bits available with a .128 subnet, so there is 2^7-2=126 combination possible per subnet for a total of 252. But I may be mistaken, that was so long ago :/

> 
The 50 host limit is for DHCP assigned IP addresses.  The OP can still assign addresses statically as they have done.
Yes you are right about that... wasn't thinking :P

---

### Post by capscrew on 2011-06-04
> **alazou said:**
> I wouldn't recommend it either, but I think it is still possible to be in the 2 to 127 address range too. I had this kind of configuration for a while.

Yes it is possible. The question is: why do it?.  All that is needed is that all subnet masks match in the local network.

---

### Post by alazou on 2011-06-04
> **capscrew said:**
> Yes it is possible. The question is: why do it?.  All that is needed is that all subnet masks match in the local network.

Right. But it is strange the OP can't ping his router even when the subnet matches if the IP adress is valid. keith_irl, have you tried to restarting the network interfaces first ?

---

### Post by keith_irl on 2011-06-04
Just so I'm clear - change the subnet on the interfaces file to 255.255.255.0

On the router leave it at 255.255.255.128

and change the local subnet to 255.255.255.0 ?

I dont really understand all this but I can do it.

Is thsi all I need to do? Thanks all.

---

### Post by alazou on 2011-06-04
It should be enough I think

---

### Post by keith_irl on 2011-06-04
Ill try again. BRB

---

### Post by keith_irl on 2011-06-04
Sorry guys have tried all the suggestions. Still not working.
Pinging the router responds . destination unreachable.

In netstat -r there is a * under gateway. Could this be something to do with it?

---

### Post by capscrew on 2011-06-04
> **alazou said:**
> Right. But it is strange the OP can't ping his router even when the subnet matches if the IP adress is valid. keith_irl, have you tried to restarting the network interfaces first ?

There are plenty of reasons that the router doesn't respond.  I would reboot the router as well as as recycling the hosts networking.  I guess I would check to make sure the cable is attached too.  ;-)

---

### Post by keith_irl on 2011-06-04
Thanks capscrew. Tried all that. I even tested the network cable with my tester. All is good. Everything else connected to the router is working fine dhcp. Tried changing the interfaces file on server to dhcp but still would not work. I then swapped out the network card and substituted it for another one. Still nothing! Thanks for your reply.

---

### Post by capscrew on 2011-06-04
> **keith_irl said:**
> Thanks capscrew. Tried all that. I even tested the network cable with my tester. All is good. Everything else connected to the router is working fine dhcp. Tried changing the interfaces file on server to dhcp but still would not work. I then swapped out the network card and substituted it for another one. Still nothing! Thanks for your reply.

Keith,

Can you ping the loopback address```
ping localhost
ping 127.0.0.1
```

Can you ping the hosts IP address```
ping 192.168.15.52

```
Or whatever IP address you are now using?

---

### Post by keith_irl on 2011-06-04
> **capscrew said:**
> Keith,

Can you ping the loopback address```
ping localhost
ping 127.0.0.1
```

Can you ping the hosts IP address```
ping 192.168.15.52

```
Or whatever IP address you are now using?

Yes could ping all three.

---

### Post by capscrew on 2011-06-04
> **keith_irl said:**
> Yes could ping all three.

This means your host is working.  The entire TCP/IP stack can ping all of your interfaces (lo and eth0).

Do you have a second host on the network you can ping?

Edit: Is the netmask is now 255.255.255.0?

---

### Post by keith_irl on 2011-06-04
> **capscrew said:**
> This means your host is working.  The entire TCP/IP stack can ping all of your interfaces (lo and eth0).

Do you have a second host on the network you can ping?

Edit: Is the netmask is now 255.255.255.0?

Yes netmask is 255.255.255.0
Have a windows 7 system on the network and can ping the router.
However cannot ping the server @ 192.168.15.50
When I try ping the server I get ```
Reply from 192.168.15.100 : Destination host unreachable
``` I also get the same response when I try ping the windows 7 box from the server by pinging 192.168.15.100

---

### Post by capscrew on 2011-06-04
> **keith_irl said:**
> Yes netmask is 255.255.255.0
Have a windows 7 system on the network and can ping the router.
However cannot ping the server @ 192.168.15.50
When I try ping the server I get ```
Reply from 192.168.15.100 : Destination host unreachable
``` I also get the same response when I try ping the windows 7 box from the server by pinging 192.168.15.100

Interesting...

So pinging 192.168.[COLOR="Blue"]15.50[/COLOR] returns "Reply from 192.168.[COLOR="Red"]15.100[/COLOR]...".

Not good, but not a problem with the host [COLOR="Green"]**.15.52**[/COLOR].

Does "the server" have multiple NIC's.  At this point I'm just fishing for answers that would account for the misconfiguration.  Can you provide me with the output from 15.52 of this```
arp -a
```

---

### Post by keith_irl on 2011-06-04
Solved...

remembered I had an old router in the attic. Linksys wrt54gs.
Swapped it over and plumbed in the settings. Powered on server. ping 192.168.1.1 (new ip of this router) bingo.

Bytes recieved.

Dont know what was up with the other one given its only brand new.

Anyway I would like to thank everyone who contributed to this post.
I cant believe it turned out to be a hardware problem! 

Thank you guys very much. :D

---

### Post by capscrew on 2011-06-04
> **keith_irl said:**
> ...
I cant believe it turned out to be a hardware problem! 


Maybe....

You can plug the new router into the old router (LAN side) and give in an IP address and subnet mask that matches the new network addressing scheme.  Then you can see if you can ping it.  If it still fails it is definitely a bad piece of hardware.  Or you can just return it... :D

Nice to see you worked your way through the problem.

-Cappy

---

### Post by alazou on 2011-06-04
In my line of work I always had trouble with the router provided by ISPs. I remember I spent 2 weeks trying to connect a printer to a network with hours spent at the phone with consumer (no) support who only advise seem to be to review our configuration or restart the printer/router... sic. Anyways glad you could find a solution to your problem.

---

