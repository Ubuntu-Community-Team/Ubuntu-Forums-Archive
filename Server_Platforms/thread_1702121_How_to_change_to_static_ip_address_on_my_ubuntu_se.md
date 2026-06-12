---
title: "How to change to static ip address on my ubuntu server"
date: 2011-03-07
forum: Server Platforms
---

### Post by alfamuzjak on 2011-03-07
Hi,
Im running ubuntu server 10.10 on my wirtual mashine at home.
For now i have few service installed and configured:apache with phpand mysql support,ftp,phpmyadmin..
My ip address is not static, i tryed to configure by following some guide but without success.

First i edit this in /etc/network/interfaces (changing dhcp to static
```
# The primary network interface
auto eth0
iface eth0 inet static
address (adding some random ip address - lets say the address which is granted from previous dhcp configuration)
netmask 255.255.255.0
broadcast -.-.-.255
network -.-.-.0
gateway my.gateway.address.
```

Then i edit /etc/resolv.conf
```
nameserver (changing to my.gateway.address.10)
domain localdomain #
search localdomain # those 2 not changing

```
then in some guide it says to remove dhcpclient if it's installed.. so i enter this:
```
sudo apt-get remove dhcp-client
```

then reboot network adapter with ( ~networking restart) or just reboot server.
So the address and configuration is stored, but i cant for example ping [www.google.com](www.google.com)
...dont have internet conection and i cant connect with browser to test my ftp or apache(...dont recognize address)

I think im something doing wrong with nameserver,domain and search (/etc/resolv.conf - in global)
This all is a bit confusing for me... 

Can someone explain me where is my mistake and help me configure static ip for my server

---

### Post by bsntech on 2011-03-07
This is the configuration I have in my /etc/network/interfaces file on one of my desktop PCs:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.254.1
        netmask 255.255.255.0
        network 192.168.254.0
        broadcast 192.168.254.255
        gateway 192.168.254.254

The /etc/resolv.conf file should be something like this:

nameserver 192.168.254.254

Ensure you use an IP address.  If you don't know of any  name servers to use, use the Google name server of 8.8.8.8 - but it will only work if your ISP allows you to connect out on port 53 UDP.

After updating that, go ahead and just do a full reboot and see if it makes a difference.  When you do an:

ifconfig

The information for eth0 should show up with the info you provided in the /etc/network/interfaces file.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/about-bsntech.html")

---

### Post by alfamuzjak on 2011-03-07
My interfaces configuration:
```
auto eth0
iface eth0 inet static
address 192.168.23.130
netmask 255.255.255.0
network 192.168.23.0
broadcsst 192.168.23.255
gateway 192.168.0.1  # i use gateway which was standing at   **lo paragraf of ifconfig command...that is address of my router...**
```

/etc/resolve.conf contain only:
nameserver 8.8.8.8 (i delete lines with 'domain' and 'search')

after pinging google i got:
```
ping: unknown host www.google.com
```

---

### Post by sergio-bobillier on 2011-03-07
```
ping: unknown host www.google.com
```

This means that the DNS server couldn't be reached. If you have a Router most likely it will have an embeded DNS server try changing your resolv.conf and set your router's IP as DNS Server like so:

```
nameserver 192.168.0.1
```

---

### Post by bsntech on 2011-03-07
In addition - to be sure that you actually do have Internet connectivity, see if you can ping an IP address.  This way it isn't using DNS to do a lookup - but it is fully skipping this step.

So see if you get replies if you do a "ping 8.8.8.8".  This will ensure that your /etc/network/interfaces file is setup properly and that you have Internet access.

If you can do a ping to 8.8.8.8, then your ISP may be blocking outgoing port 53 UDP.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321.html")

---

### Post by alfamuzjak on 2011-03-07
Nothing!
I dont know what to do, its insane, i cant have static server.
any advice?!

P.S.Thank you for trying to help me

---

### Post by alfamuzjak on 2011-03-07
ping 8.8.8.8
```
connect: network is unreachable
```

---

### Post by wormyblackburny on 2011-03-07
Ummm, if your computer is on the 192.168.23.0 network, how can your gateway be the 192.168.0.1 network? Your gateway is incorrect, point it to 192.168.23.0 or 192.168.23.254 (depending on your routers configuration). The router will handle the forwarding to the .192.168.0.0 network if it is indeed connected to that network....

---

### Post by alfamuzjak on 2011-03-07
Didn't quitely understand, you are saying what...to change:
network to 192.168.0.0, or to change gateway to 192.168.23.1/0/254 in /etc/network/intefaces?

Sorry but i tryed so many combination and have dizzyness from numbers:/

P.S. how then virtual mashine and my comp can ping each other - if they arent on same network.. - try to ignore this if u think it is stupid

---

### Post by wormyblackburny on 2011-03-07
Actually, I take that back. Sounds like you have just a single router so your static ip needs to be in the 192.168.0. (1-254) range and gateway needs to be 192.168.0.0 as well as nameserver needs to be 192.168.0.0 (unless you are running a dns server)

---

### Post by alfamuzjak on 2011-03-07
Then, u think i must try to set up my static ip in that range (192.168.0.1-254)?
And other to leave same

Second thing is then contradictory - when ip address was dinamic(by dhcp), why then my address was 192.168.23.130

---

### Post by wormyblackburny on 2011-03-07
> **alfamuzjak said:**
> Then, u think i must try to set up my static ip in that range (192.168.0.1-254)?
And other to leave same

Easiest wat to tell would be to get off the virtual machine and do an ifconfig (windows) or an iwconfig and see what the address is of the physical machine is, that is the network you need to be on..

---

### Post by bsntech on 2011-03-07
Let us know what your IP address is that you are attempting to set on your server.  Based on this information, we can probably tell you what your network line should be.

Do you have any other computers in that network?  If so, best bet is to ensure you set your gateway to the same gateway that the other PC has.

So,if your default gateway is 192.168.0.1, then you could set your server config like:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
    address 192.168.0.2
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

Now, if your router's IP address is actually 192.168.0.254, then the "gateway" line should have 192.168.0.254 in it, not 192.168.0.1.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/terms-of-service.html")

---

### Post by YesWeCan on 2011-03-07
> **alfamuzjak said:**
> Nothing!
I dont know what to do, its insane, i cant have static server.
any advice?!

P.S.Thank you for trying to help me
Have you considered using your router to give your server a static address? This is usually easily configured in the router and you don't need to change your server at all.

---

### Post by alfamuzjak on 2011-03-07
I get this from windows:

Ethernet adapter Local Area connect.
connection-specific DNS Suffix . :
Link- local Ipv6 ...........with hexadecimal numbers
ipv4.......................192.168.1.2
mask......................./23
def.gateway................192.168.1.1


Ethernet adapter Local Area connect.2
connection-specific DNS Suffix . :
Link- local Ipv6 ...........with hexadecimal numbers
ipv4.......................192.168.88.1
mask......................./23
def.gateway................(blanc)


Ethernet adapter Local Area connect.3
connection-specific DNS Suffix . :
Link- local Ipv6 ...........with hexadecimal numbers
ipv4.......................192.168.23.1
mask......................./23
def.gateway................

---

### Post by bsntech on 2011-03-07
Perfect.

Based on that information, you need this on your server.  Note that you CAN change the IP address below to something else if you'd like:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Now - here is my next question - you have two other Ethernet adapters listed under that - 2 & 3 - are those hooked up to anything?  And if they are - did you assign those statically?

---

### Post by alfamuzjak on 2011-03-07
I will try with that.

Those two ethernet adapters are probably from virtual mashines...number 3 is for this ubuntu server (i copied previous state of virtual mashine so i can do this and other experimentation without affecting original:)

---

### Post by alfamuzjak on 2011-03-07
> **bsntech said:**
> Perfect.

Based on that information, you need this on your server.  Note that you CAN change the IP address below to something else if you'd like:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Now - here is my next question - you have two other Ethernet adapters listed under that - 2 & 3 - are those hooked up to anything?  And if they are - did you assign those statically?
I used exactly those numbers,and in resolv.conf i tryed everything...including 192.168.1.1,8.8.8.8 but nothing happened.(every time i restart networking) - host still unreachable

---

### Post by alfamuzjak on 2011-03-07
I can say one more thing in virtual mashine i have few options for net adapter :
bridged:connected directly to the physical network + option with -replicate physical net con state
and NAT: used to share the host's IP address

I always use NAT, it only worked for me.
While trying every configurations u all suggest, in meanwhile i select and try also those options(nat,bridged..)

Im have adsl, i can tell you also my home address,telephone etc if u want, just help me fix this:)))))
Kidding, u r all great guys

---

### Post by alfamuzjak on 2011-03-07
i got brain damage from this

---

### Post by bsntech on 2011-03-07
OK - because you are using this on a virtual machine - this may be the cause of the problem.

You said you had this virtual machine setup in DHCP - and it was working for you, correct?

Maybe it is time to revert back to DHCP - then reboot - and then write down everything you get when doing an "ifconfig".  Get the IP address, broadcast, subnet mask.  Then do a "route" command and look for the default gateway IP address (will be under the "Gateway" heading) - the line that says "default" under "Destination".  Then you'll need to re-create your /etc/network/interfaces file with those settings.

Brian S.

---

### Post by alfamuzjak on 2011-03-07
Screenshots...



AND, like i said (/etc/resolv.conf):
nameserver 192.168.23.2
domain localdomain
search localdomain

---

### Post by oldfred on 2011-03-07
Your static address cannot overlap the dynamic range. In effect all the dynamic addresses are used. 

> Second thing is then contradictory - when ip address was dinamic(by dhcp), why then my address was 192.168.23.130

Most routers reserve 50 or 100 numbers starting at 100. Just use .3 as suggested above, not .130.

---

### Post by bsntech on 2011-03-07
Good.  Now you have some information to work with.

On your host that hosts the virtual machine - how do you have the network setup?  Do you have it as bridged or do you have it as NAT?  Hopefully bridged - which means it just bridges right out to the network.

Oldfred makes a good point.  Basically if you are going to set the static IP address on this virtual machine, you'll need to ensure that your DHCP server (or router) does not give out that IP address to any other client.  Otherwise, you'll have an IP address conflict.

So, based on the screenshots above, this is how your /etc/network/interfaces file should look:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.23.130
        netmask 255.255.255.0
        network 192.168.23.0
        broadcast 192.168.23.255
        gateway 192.168.23.2
        # dns-* options are implemented by the resolvconf package, if installed
        # dns-nameservers 192.168.254.1

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281")

---

### Post by alfamuzjak on 2011-03-07
> **oldfred said:**
> Your static address cannot overlap the dynamic range. In effect all the dynamic addresses are used. 



Most routers reserve 50 or 100 numbers starting at 100. Just use .3 as suggested above, not .130.

Ok(i think i undestand -although my english isn't so good)...but what about resolv...what will be my nameserver?should i let it as default(dhcp default - screenshot from my previous post)?

---

### Post by bsntech on 2011-03-07
Your post actually didn't provide a nameserver.  The first picture just showed the IP addressing information for your NIC.  The second screen showed the router's IP address of 192.168.23.2.  If you have DNS running on the router, then you can set your name server to 192.168.23.2 if you desire.

Otherwise, go to a known-working system and look up what DNS servers you are using there.  On the Windows machine, do an "ipconfig /all" and it should show the DNS servers.

Brian S.

---

### Post by alfamuzjak on 2011-03-07
IT WORKS!!!
Finnaly..i do it like u said Brian, except i change .130 with .3. 
I edit only ```
/etc/network/intefaces
```
resolvconf didnt touch.

THANK YOU for your time and patience.
bye

---

### Post by alfamuzjak on 2011-03-08
The Real problem with all this was actually (in my case):

After adding information in /etc/network/intefaces
address,netmask,gatewat...

I type:
```
$ sudo route - n
```     and get:
only routing table from my ip address to 0.0.0.0 gateway

So, i add default gateway:
```
$ sudo route add default gw 192.168.1.1
``` (for example)
And everythng worked perfectly fine...Can't belive i didnt check that at first time.

Thank you all again!

---

