---
title: "Internet Connection Sharing Documentation"
date: 2007-07-17
forum: Unanswered Posts Team
---

### Post by spd106 on 2007-07-17
Hello all,

During my unanswered posts tracking I'm seeing rather a lot of threads posted to the wireless and networking forum about sharing an internet connection on a home network (ICS). I'm sure there are many reasons for the increase in these posts. Maybe it's because we are seeing a growth in users with multiple computers who can't afford or simply don't want to buy a switch/router, who knows? 

What it does indicate is that either the current method is too hard for new users, the documentation is not good enough or it's just too difficult to find.

The first of these can probably be dealt with by helping users through the process on an individual case by case basis, but this takes a lot of resources. So ideally I think it would be best to try and improve the documentation we already have and make it more accessible.

The best of the current documentation that I have found are as follows.

This wiki page contains a wealth of information, but it suffers from bad formatting and is in great need of a clean up. The difficulty is in clarifying the material without sacrificing depth. Initially I pointed most users to Firestarter, as that's what I first used. Unfortunately it doesn't work in all cases and can sometimes create even more problems due to the restrictive firewall rules. Though it's still the easiest solution to former windows users.
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

I found this wiki page only recently and found it is easy to follow but too specific in most places and lacking the formal tone of good, solid, easily translatable documentation. 
[https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing)

This wiki page is more generically focused on configuring a router and as such is a little beyond the scope of what a simply ICS guide should contain. Though it is well written and does provide some good background information and examples.
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

There is also this excellent forum thread that contains a great script for automating the configuration of NAT and port forwarding. It is however a little verbose for beginners.
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Of course this functionality should be built in to GNOME's network-admin capplet or Network Manager, indeed I believe it has been discussed on the mailing lists.  However, until a proper solution is found I think it would be a good idea to create a central resource from the above guides. Perhaps a clean up of the main ICS page in the wiki?

Anyone willing to help?

Thanks

---

### Post by babysteps on 2007-07-18
"..... Initially I pointed most users to Firestarter, as that's what I first used. Unfortunately it doesn't work in all cases and can sometimes create even more problems due to the restrictive firewall rules. Though it's still the easiest solution to former windows users.
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
.."

due to the difficulties with getting on line for some machines in the house, I've started to look for solutions. I tried to follow the Firestarter info, but found that for Ubuntu you can get it for 4.10 and 5.4, but nothing after that?  Is that correct? Or maybe I just haven't found them, yet?

And a very dumb question here but in this: 

Key Features

    *Suitable for use on desktops, servers and gateways
    *Enables Internet connection sharing
    * Allows you to define both inbound and outbound access policy
    *Wizard for easily configuring your firewall
    * Sets up DHCP for a local network
    *Real time firewall events view
    *View active network connections, including any traffic routed  through the firewall

The first line that says it's suitable for use on "desktops".....etc.
Is that literal as in you can't use it for a laptop?

Thanks for your answer, and thanks for starting this project!

babysteps

---

### Post by spd106 on 2007-07-18
Firestarter is available on all Ubuntu releases in the universe repository. Though it hasn't seen any significant updates for nearly two years (since Breezy).

There is no reason why it wouldn't work on a laptop, I believe the reason it wasn't specifically mentioned was that laptops aren't typically used as a router/server due to their mobility advantage.

I am hoping that this team can do more than just answer posts. It seems like a waste of time trying to fight a never ending battle. To me it makes more sense to attempt to reduce the number of easily solved problems and improving documentation is one way this can be achieved.

---

### Post by jpeddicord on 2007-07-18
> I am hoping that this team can do more than just answer posts. It seems like a waste of time trying to fight a never ending battle. To me it makes more sense to attempt to reduce the number of easily solved problems and improving documentation is one way this can be achieved.Agreed. :)

By the look of your first post, it seems that you are coming up across a bunch of threads like these. If you have found a common solution, whether it is a list of links from the wiki or instructions, feel free to check out the Canned Responses section:
[https://wiki.ubuntu.com/UnansweredPostsTeam/Canned/](https://wiki.ubuntu.com/UnansweredPostsTeam/Canned/)

Anything on the Responses subpage on that wiki is automatically pulled into the extension. I haven't really publicized it much yet since I am still tweaking with the script. I'll make an announcement on the forums whenever it is finished.

As for the wiki pages on ICS, again I couldn't agree more. Although, I am curious on what troubles you are having with Firestarter. I am on a laptop myself, and I can use ICS just by using the Firestarter GUI.

Jacob

---

### Post by mckryptyk on 2007-08-31
Hi I wrote something back in late 2005 that is along these lines.
It was written for beginners setting up ICS for the first time.

More specifically, I wrote it to connect an original xbox to a computer via ethernet,
and then connect the PC to the internet.

I used firestarter to do all the heavy lifting :)

[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)

I hope this will help some,

Cheers.

---

### Post by LexRoss on 2008-03-14
Since sharing Internet connection requires nothing more than NAT configuration with ipchains, the option to share internet connection should be included within Network Manager applet as simple checkbox.

That is what Vista users will expect and it is really convenient to have an ICS option there.

Firestarter is an overkill, and in my case, it screwed up my network connection completely (I have computer with one network card and VPN connection to my ISP). That gives us dynamically assigned IP on my eth0 interface and VPN PPTP connection on ppp0. Home LAN is supposed to be configured on eth0:1 logical interface.

Neither Network Manager or Firestarter could deal with logical interfaces but I will be happy for laptop users with wireless cards if they could easily share their ethernet based Internet connection over wireless home LAN. Any ideas on how it can be implemented with Network Manager applet? Maybe to have a top level menu item that says "Share network connection" and then present the user with the dialog to choose "From" and "To" interfaces, "From" being connected to the Internet. Then there should be an option to stop sharing, also activated on Internet disconnect (to handle cases when ppp0 interface cease to exist).

---

### Post by dmizer on 2008-07-17
I just went through the server configuration of the [ICS wiki](https://help.ubuntu.com/community/Internet/ConnectionSharing) with an eye toward organizational changes and parallel structure.  I broke things down a bit by adding a few helpful headings.  I also corrected the confusing iptables commands.

In the very near future, I also intend to spend some time on the client side as well as clean up the "other approaches" sub section as I get time.

This is my first major wiki edit, so I'm glad to have input.  It's not perfect, but it's a start.

---

### Post by lincoln32 on 2008-07-18
I need to connect a xbox to a ubuntu machine in rear of house wireless to ubuntu machine and lan to xbox 360 but found fire starter unable to make connection and made wireless to ubuntu extra slow less than 900bytes transfer at best any ideas or how to make work in simple wording would help

---

### Post by dmizer on 2008-07-18
> **lincoln32 said:**
> I need to connect a xbox to a ubuntu machine in rear of house wireless to ubuntu machine and lan to xbox 360 but found fire starter unable to make connection and made wireless to ubuntu extra slow less than 900bytes transfer at best any ideas or how to make work in simple wording would help

okay, have you looked at the wiki article?

if so, what points do you think need clarity?

---

### Post by dmizer on 2008-07-21
Cleaned up the client configuration section, and rewrote the introduction.  I felt as though the original introduction was cryptic and far from helpful.

Client section now includes concrete configuration examples which match the server configuration section.

I also included some external links to aid in understanding terminology.

My next step will be to provide good documentation for alternative configurations, as well as to give a few advanced configuration examples.

Looking for testers to provide feedback on the documentation.  Thank you.

---

### Post by lincoln32 on 2008-07-26
I keep trying to find what I need but but get confused by lack of details or my lack of hard networking background.
I need to connect wireless ubuntu 8.04 to x box 360 so i have installed fire starter and setup but It will not connect to 360 and some places it says firestarter has the dchp that i need and what is the need for the master? other places it says to set dchp range. is that the input to firestarter or output? this the only area I have found windows to be easier
to bridge or ics otherwise Ubuntu seems as good or better than windows

---

### Post by dmizer on 2008-07-26
> **lincoln32 said:**
> I keep trying to find what I need but but get confused by lack of details or my lack of hard networking background.
I need to connect wireless ubuntu 8.04 to x box 360 so i have installed fire starter and setup but It will not connect to 360 and some places it says firestarter has the dchp that i need and what is the need for the master? other places it says to set dchp range. is that the input to firestarter or output? this the only area I have found windows to be easier
to bridge or ics otherwise Ubuntu seems as good or better than windows

i have not yet gotten around to working on the firestarter documentation.  the existing CLI/iptables documentation was erroneous and misleading, so that's where i started.

my next step will be to work on a few advanced CLI techniques, then i will focus on firestarter. i know that firestarter howtos exist, so if you need a gui interface, i suggest you look for them.  if you need ICS now, you can try the CLI/iptables section.

---

### Post by dmizer on 2008-07-27
Just updated the wiki with directons for including a DHCP server in ICS configuration.

As ever, testing and feedback is appreciated.

---

### Post by dmizer on 2008-07-28
Wiki article is just about complete.  Could use some formatting cleanup and improvments in wording in some places.

The section on using firestarter is incomplete and written badly, but I think it's easy enough to do ICS without firestarter that elaboration isn't necessary.

---

### Post by majornoob on 2008-09-05
Hello all!

Just read through all the documentation on the wiki and am still a bit confused - my ICS situation is a little weird.  I hope I am posting in the right place.

I have a Hardy based laptop connected to my building's internet with wifi (wlan0, no ethernet available).  I want to share the connection via the laptop's ethernet port (eth0) to a wired-only router which, unfortunately, is hard-coded to use 192.168.15.x subnet.  This router, in turn, will supply an internet connection to the wired-only desktop and an old wired-only notebook.

If possible, I would still like to use Network Manager for wlan0 on the Hardy laptop.  Any ideas?

Thanks!

---

### Post by dmizer on 2008-09-06
> **majornoob said:**
> Hello all!

Just read through all the documentation on the wiki and am still a bit confused - my ICS situation is a little weird.  I hope I am posting in the right place.

I have a Hardy based laptop connected to my building's internet with wifi (wlan0, no ethernet available).  I want to share the connection via the laptop's ethernet port (eth0) to a wired-only router which, unfortunately, is hard-coded to use 192.168.15.x subnet.  This router, in turn, will supply an internet connection to the wired-only desktop and an old wired-only notebook.
The router will be a problem. Enabling ICS will turn your laptop into a router. Two routers on the same network can be done, but you should really try to see if there is a way to disable DHCP on the router before resorting to configuring two subnets.

What make and model of router do you have?

> **majornoob said:**
> If possible, I would still like to use Network Manager for wlan0 on the Hardy laptop.  Any ideas?
This should not be a problem with the wireless side, but it could interfere with the wired (eth0) side.

---

### Post by majornoob on 2008-09-10
Sorry for the late reply, was out of town for a few days.

The router is a Vonage-supplied Linksys (similar to a WRT54G) with a phone port.  Unfortunately, Vonage locks down their hardware pretty tight, so it is more or less impossible to change settings AFAIK.  Thus, the router is basically permanently set as 192.168.15.1 and assigns IP addresses in the 192.168.15.x subnet.

Any ideas that I can try are much appreciated.

---

### Post by dmizer on 2008-09-11
In that case, this will likely not be possible:
internet <-> ubuntu <-> vonage router <-> other computers

This is possible:
internet <-> vonage router <-> ubuntu <-crossover-cable-> other comptuers
-or-
internet <-> ubuntu <-> hub (remove router) <-> other computers

Your may also call and talk to vonage about your situation (that you connect to the internet wirelessly), and ask them what they suggest you do to get around this problem.

Before calling Vonage, you would need to configure ICS and test it with the router removed. Then you could call them and tell them you have ICS configured and working on your wirelessly connected computer, and that you are unable to connect with your router in place.

---

### Post by wdypdx1 on 2008-09-25
I've been working through the ICS documentation and ran into this issue concerning the **[COLOR="DarkOrange"]"state"[/COLOR]** argument in iptables.


-----------------------------------
$sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
$sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$sudo iptables -A POSTROUTING -t nat -j MASQUERADE
-----------------------------------

My code for the first line is actually this:
---------------------------------------
$sudo iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.1.0/24 -m state --state NEW -j ACCEPT
---------------------------------------

When running the command I get this error message:

-----------------------------------
[B][I]iptables v1.3.8: Unknown arg `--state'
Try `iptables -h' or 'iptables --help' for more information.[/I][/B]
-----------------------------------

I tried iptables -h and did some searching but haven't come up with an answer. 

Hardy 8.04 LTS updated yesterday. I'm also very rusty when it comes to command line and pretty much re-learning at this point.

Thanks.

Now solved--------I found a typing error on my part----

---

### Post by kazbear on 2008-10-01
I have followed the wiki, but I am not having any luck.  I am not getting any errors, and things appear to be setup properly, but I am still unable to get Internet access with my Xbox (1).

I can access shared files on the Linux box through the XBox, but cant get beyond that.

can anyone help me figure this out?

Thanks

**Never mind, Figured it out...**

---

### Post by tCarls on 2008-10-23
I seem to be having a similar problem to kazbear. I followed the wiki and can ssh between the two computers but can't connect to the internet from the second one. kazbear, can you post what you did to fix it?

My laptop is connected to a wireless network. I'm trying to share the connection with my desktop through ethernet. I've tried using both static IPs and dhcp, with similar results. ssh works but the internet doesn't. The only difference is that with static IPs, when I ping google from the desktop it says it couldn't resolve the name and when I ping google's IP it says it's unreachable. However, with dhcp the pings don't print errors, they just timeout. Any ideas?

thanks

---

### Post by dmizer on 2008-10-23
Are you sure you configured the dns servers on the desktop, as described under "[Client set up](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#Client%20set%20up)"?

---

### Post by tCarls on 2008-10-23
> Are you sure you configured the dns servers on the desktop, as described under "Client set up"?

Fairly sure, unless I missed something. See below.

Actually, one thing important that I just now noticed: the ping on the desktop is actually able to resolve google's IP, it just can't transfer any data.

```

tcarls@desktop$ grep prepend /etc/dhcp3/dhclient.conf
#prepend domain-name-servers 127.0.0.1;
prepend domain-name-servers 208.67.222.222,208.67.220.200;

tcarls@desktop$ cat /etc/resolv.conf
search example.org
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 208.67.216.132
nameserver 208.67.216.132

```

Below is the output of a few more commands that may be useful. Note: I changed the subnet from 192.168.0 to 192.168.2 so it wouldn't conflict with the wireless subnet.

```

tcarls@desktop$ route
Kernel IP routing table
Destination    Gateway    Genmask          Flags Metric Ref    Use Iface
192.168.2.0    *          255.255.255.0    U     0      0        0 eth0
default        laptop     0.0.0.0          UG    0      0        0 eth0


tcarls@desktop$ ifconfig eth0 | grep 'inet addr'
    inet addr:192.168.2.20 Bcast:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0

tcarls@desktop$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.000 ms
^C

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.000/0.000/0.000/0.000 ms

tcarls@desktop$ ping www.google.com
PING www.l.google.com (209.85.173.147) 56(84) bytes of data.
^C

--- www.l.google.com ping statistics ---
60 packets transmitted, 0 received, 100% packet loss, time 59007ms

```

```

tcarls@laptop$ ifconfig eth0 | grep 'inet addr'
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0

tcarls@laptop$ ifconfig wlan0 | grep 'inet addr'
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0

tcarls@laptop$ cat /proc/sys/net/ipv4/ip_forward
1

# I'm using Hardy. The wiki said there's a bug in Gutsy and
# a couple lines need to be added. I wasn't sure if it still
# applied to Hardy to I tried with and without them.
tcarls@laptop$ grep forward /etc/sysctl.conf
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
# Uncomment the next line to enable packet forwarding for IPv6
net.ipv6.ip_forward=1
#net.ipv4.conf.default.forwarding=1
#net.ipv4.conf.all.forwarding=1

```

---

### Post by dmizer on 2008-10-23
Okay, I've tested this on a few systems so it may also work for you.

Let's try dumping your current firewall configuration with the following command:
```
sudo iptables -F
```
Make sure there are no remaining iptables rules in place:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Then try this firewall argument:
```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

---

### Post by Dmole on 2009-01-08
>Open /etc/resolve.conf with your favorite text editor: 
>sudo nano /etc/dhcp3/dhclient.conf

seems to me there is an error here because /etc/dhcp3/dhclient.conf != /etc/resolve.conf


also it did not work for me :(

---

### Post by dmizer on 2009-01-08
> **Dmole said:**
> >Open /etc/resolve.conf with your favorite text editor: 
>sudo nano /etc/dhcp3/dhclient.conf

seems to me there is an error here because /etc/dhcp3/dhclient.conf != /etc/resolve.conf


also it did not work for me :(

Thank you for pointing this out. I've updated the wiki.

You may have to restart your networking (or reboot) before these settings will take effect.

---

### Post by brnetonboy on 2009-03-03
The wiki says 

> Unless your ICS gateway can also **perform DNS**, you must manually configure the client with your **ISP DNS servers**. If you do not know your ISP's DNS servers, you can **use OpenDNS** servers instead. 

all three of these options fail.
[LIST]
[*]Option 1: "Perform DNS." The link is to the Wikipedia entry on DNS. Not very helpful, I still have no idea whether or not my computer can do this or how to set it up. So I give up and move on.

[*]Option 2: "ISP DNS servers." What are those??!! How do I find out what my ISP DNS servers are? I searched the internet to no avail.

[*]Option 3: "use OpenDNS." The link to a very helpful step-by-step is great, however, I get stuck on step 3, as no connection shows up. In fact, Network Manager has a little X by it like I have no connection (though I do now have a connection, having gone through the ICS steps). Actually, the client computer is Ubuntu Studio, and it didn't even have Network Manager installed by default, so I had to install it and reboot (which deleted my connection and I had to do it all over again.)
[/LIST]
So I definitely think the Wiki should be updated in this part, with more info on how people can pursue these different options.

----
PS: Please help me if you know the answers to these questions! I just want to have internet on my second computer! Thanks.

---

### Post by brnetonboy on 2009-03-03
> **brnetonboy said:**
> 
Option 3: "use OpenDNS." The link to a very helpful step-by-step is great, however, I get stuck on step 3, as no connection shows up. In fact, Network Manager has a little X by it like I have no connection (though I do now have a connection, having gone through the ICS steps). Actually, the client computer is Ubuntu Studio, and it didn't even have Network Manager installed by default, so I had to install it and reboot (which deleted my connection and I had to do it all over again.)

I just had a thought... is it possible that the wiki wants me to configure OpenDNS on the Gateway, as opposed to the Client? The wiki does not specify. Which is it? I can easily follow the directions to install it on the Gateway computer. Please help! Then update the wiki to be more clear on this point.

---

### Post by dmizer on 2009-03-03
> **brnetonboy said:**
> I just had a thought... is it possible that the wiki wants me to configure OpenDNS on the Gateway, as opposed to the Client? The wiki does not specify. Which is it? I can easily follow the directions to install it on the Gateway computer. Please help! Then update the wiki to be more clear on this point.

Nope, you'll have to configure OpenDNS on the client. It's under the client configuration settings so I thought it was clear enough. I'll take another look in a bit.

Your gateway AND client are both Ubuntu?

Edit: took another look at the wiki. This is what's currently written, and what you quoted earlier ->

> Unless your ICS gateway can also perform DNS, you must manually [COLOR="Red"]configure the client[/COLOR] with your ISP DNS servers. If you do not know your ISP's DNS servers, you can use OpenDNS servers instead. 

Is there something about the wording that made you confused?

---

### Post by brnetonboy on 2009-03-03
> **dmizer said:**
> Nope, you'll have to configure OpenDNS on the client. It's under the client configuration settings so I thought it was clear enough. I'll take another look in a bit.

Your gateway AND client are both Ubuntu?

You are probably right that it is clear enough but since I'm running into hurdles I started second guessing everything and thinking I must be doing something wrong. 

Yes, both are Ubuntu. Gateway is Ibex 8.10, Client is Ubuntu Studio (8.10 as well).

---

### Post by brnetonboy on 2009-03-03
> **brnetonboy said:**
> You are probably right that it is clear enough but since I'm running into hurdles I started second guessing everything and thinking I must be doing something wrong. 

Yes, both are Ubuntu. Gateway is Ibex 8.10, Client is Ubuntu Studio (8.10 as well).

Caveat: I'm triple booting the client, so I'll eventually want to get this working with XP and Windows 7, but that's a lower priority at the moment.

---

### Post by dmizer on 2009-03-03
Okay, please post the output of the following command from both the client and the gateway:
```
sudo ifconfig
```

---

### Post by brnetonboy on 2009-03-03
> **dmizer said:**
> 
Edit: took another look at the wiki. This is what's currently written, and what you quoted earlier ->

Is there something about the wording that made you confused?

I think that my confusion is mostly my fault, not the wikis. The wiki article is extremely well written and I was able to follow it better than most other stuff on the internet. 

I was confused mostly because I don't know what I'm doing. :) In my head, I was thinking "ISP's DNS servers vs OpenDNS servers"... ISP DNS sounds like what a computer connects to in order to get to the outside internet... so maybe for OpenDNS the client needs to connect to the Gateway the way that it'd normally connect to the ISP."

Honestly, I would not have been confused if it had worked, but then I started over-thinking everything. So I guess the wiki is clear on that point as it is.

---

### Post by brnetonboy on 2009-03-03
> **dmizer said:**
> Okay, please post the output of the following command from both the client and the gateway:
```
sudo ifconfig
```
GATEWAY:
```
brenton@Sceadufax:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:fe:37:a9:1c  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe37:a91c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24218314 (24.2 MB)  TX bytes:3594910 (3.5 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:10:4b:9b:3b:42  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:4bff:fe9b:3b42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1500644 (1.5 MB)  TX bytes:10427574 (10.4 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1948 (1.9 KB)  TX bytes:1948 (1.9 KB)

```

CLIENT:
```

brenton@UbuntuStudio:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:93:d6:bf  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe93:d6bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6406905 (6.4 MB)  TX bytes:1241399 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```
The client doesn't have a IP address unless I follow the steps in the wiki, so this is it after I've gone through the steps.

---

### Post by dmizer on 2009-03-03
I realize that sometimes I can be overly verbose and muddy, so I just wanted to make sure.

Your network setup looks good.

Can you ping something? Try pinging google for example:
```
ping www.google.com
```
and try pining by IP address as well:
```
66.249.89.104
```

---

### Post by brnetonboy on 2009-03-03
> **dmizer said:**
> I realize that sometimes I can be overly verbose and muddy, so I just wanted to make sure.

Your network setup looks good.

Can you ping something? Try pinging google for example:
```
ping www.google.com
```
and try pining by IP address as well:
```
66.249.89.104
```

I should have mentioned this before: the client has internet just fine right now. I am just trying to get to the next part of the Wiki which seems to offer a more permanent solution. When I restarted UbuntuStudio, everything went away and I had to go through the whole process again, but I thought that the point of setting up OpenDNS or using a ISP DNS was to make it more permanent, but I wasn't able to do either of those.

--edit--
I just rebooted the Client and did ifconfig to show what happens:
```

eth0      Link encap:Ethernet  HWaddr 00:16:76:93:d6:bf  
          inet6 addr: fe80::216:76ff:fe93:d6bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2862 (2.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```

---

### Post by dmizer on 2009-03-03
> **brnetonboy said:**
> I should have mentioned this before: the client has internet just fine right now. I am just trying to get to the next part of the Wiki which seems to offer a more permanent solution. When I restarted UbuntuStudio, everything went away and I had to go through the whole process again, but I thought that the point of setting up OpenDNS or using a ISP DNS was to make it more permanent, but I wasn't able to do either of those.

No, DNS servers simply resolve IP addresses into URLs. It really doesn't matter if you use your ISP DNS servers or OpenDNS. I use OpenDNS on all of my machines because it tends to resolve URLs much more quickly than my ISP.

If you're having problems with the client settings sticking, you have two choices. Either are perfectly acceptable and will depend on what you intend to do with your client.

[s]1) NetworkManager doesn't handle static IP well, and interferes with the settings in /etc/network/interfaces. You could simply uninstall NetworkManager in Synaptic and you probably won't have any more problems.[/s]

2) You could follow the directions under "Advanced Gatway Configuration" to configure your gateway to resolve DNS and provide a DHCP IP address to your client. It's not too difficult to perform, and the commands given in the examples will fit your network. [s]Then, you'll need to remove the static settings in /etc/network/interfaces.[/s]

Edit: sorry, I had forgotten that the wiki article doesn't discuss editing /etc/network/interfaces. Give the "DHCP/DNS server" a whirrl. That should get you going.

---

### Post by brnetonboy on 2009-03-03
> **dmizer said:**
> No, DNS servers simply resolve IP addresses into URLs. It really doesn't matter if you use your ISP DNS servers or OpenDNS. I use OpenDNS on all of my machines because it tends to resolve URLs much more quickly than my ISP.

If you're having problems with the client settings sticking, you have two choices. Either are perfectly acceptable and will depend on what you intend to do with your client.

[s]1) NetworkManager doesn't handle static IP well, and interferes with the settings in /etc/network/interfaces. You could simply uninstall NetworkManager in Synaptic and you probably won't have any more problems.[/s]

2) You could follow the directions under "Advanced Gatway Configuration" to configure your gateway to resolve DNS and provide a DHCP IP address to your client. It's not too difficult to perform, and the commands given in the examples will fit your network. [s]Then, you'll need to remove the static settings in /etc/network/interfaces.[/s]

Edit: sorry, I had forgotten that the wiki article doesn't discuss editing /etc/network/interfaces. Give the "DHCP/DNS server" a whirrl. That should get you going.

Ah, ok: I had thought I would need either ISP DNS servers or OpenDNS. I'll follow the advanced instructions and see if that will keep my client connected through a bounce. Thanks!

--edit--
Final question: I should be installing the DHCP/DNS stuff on the gateway, right?

---

### Post by dmizer on 2009-03-03
> **brnetonboy said:**
> Final question: I should be installing the DHCP/DNS stuff on the gateway, right?

Indeed. :) Let me know how it turns out!

---

### Post by brnetonboy on 2009-03-03
> **dmizer said:**
> Indeed. :) Let me know how it turns out!
Success! Mostly. I bounced the client and it worked great! However, when I bounced the gateway, the client no longer got internet until I did this:

```
brenton@Sceadufax:~$ sudo ifconfig eth1 192.168.0.1
brenton@Sceadufax:~$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

I guess I will do something to make these two lines run on startup.

Thanks so much, dmizer, I'm really impressed with getting personal, instant help! One of the best experiences in any forum or any tech support service I've experienced anywhere!

---

### Post by dmizer on 2009-03-03
> **brnetonboy said:**
> Success! Mostly. I bounced the client and it worked great! However, when I bounced the gateway, the client no longer got internet until I did this:

```
brenton@Sceadufax:~$ sudo ifconfig eth1 192.168.0.1
brenton@Sceadufax:~$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

I guess I will do something to make these two lines run on startup.

Thanks so much, dmizer, I'm really impressed with getting personal, instant help! One of the best experiences in any forum or any tech support service I've experienced anywhere!

No problem!

Edit /etc/rc.local like so:
```
gksudo gedit /etc/rc.local
```

And make the file look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth1 192.168.0.1
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
exit 0

```

Save the file, reboot your gateway and see if that makes things persistent.

---

### Post by brnetonboy on 2009-03-04
So I thought everything was working before, but somehow it all stopped working. 

The network is unreachable on the client when I boot it up. It has no IP (like the example I pasted in earlier). I have to run these three commands from the wiki:

```
sudo /etc/init.d/networking stop
sudo ifconfig eth0 192.168.0.100
sudo route add default gw 192.168.0.1
```

and then it gets an IP (192.168.0.100) but no internet until I do these two commands on the gateway:
```
sudo ifconfig eth1 192.168.0.1
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

Even though I did what you said to get those two lines to run automatically.

I am wondering about the "Configure DNS Servers" section of the wiki which I completely skipped. What does that do? It seems like it's there for a reason and doing it would help. Is it worth my time to pursue that route? If this isn't the appropriate place, I can start a new thread asking what an ISP DNS is and how I can find out what mine are. It seems like that will be easier to figure out than to figure out how to get past step 3 of the OpenDns instructions.

--edit--
the internet on the client is snail-on-a-sloth slow. I can ping google, but in Firefox it takes forever to connect. Actually, it still hasn't connected, and I typed it in well before I even started editing this post.

---

### Post by dmizer on 2009-03-04
DNS is not your problem, your problem is getting IP addresses to automatically assign themselves.

I'm a bit tied up for the afternoon, and I need to do some direct testing as it's been some time since I've used that wiki to do ICS (I don't have the need). Once I get some more information, I'll post back with a solution. I'll try to get that done tonight.

---

### Post by brnetonboy on 2009-03-04
> **dmizer said:**
> DNS is not your problem, your problem is getting IP addresses to automatically assign themselves.

I'm a bit tied up for the afternoon, and I need to do some direct testing as it's been some time since I've used that wiki to do ICS (I don't have the need). Once I get some more information, I'll post back with a solution. I'll try to get that done tonight.

No hurry, I've got it manually configured for now. It's near midnight here, so I probably won't be working on this again for 11 hours. :)

---

### Post by sansa dude on 2009-03-22
ok im having problems with this. i have my desktop computer which has 2 ethernet ports in it, i want to give access to my laptop through a wired connection using the 2nd port. 

i went through the instructions [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") and have had no luck the internet does not show up on my laptop and it didnt work on my desktop then i switched the connections on my computer so auto eth1 was on my home network. 

i have no clue really on what some of the instructions mean on that page. on my other card i can not get on to any websites but it says im connected and the network is fine. any halp is greatly appreciated!

---

### Post by brnetonboy on 2009-03-22
> **sansa dude said:**
> ok im having problems with this. i have my desktop computer which has 2 ethernet ports in it, i want to give access to my laptop through a wired connection using the 2nd port. 

i went through the instructions [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") and have had no luck the internet does not show up on my laptop and it didnt work on my desktop then i switched the connections on my computer so auto eth1 was on my home network. 

i have no clue really on what some of the instructions mean on that page. on my other card i can not get on to any websites but it says im connected and the network is fine. any halp is greatly appreciated!
Can you go through the instructions and quote exactly the first part you don't understand? I have had trouble getting this set up too, but I think I understood most of it, so if you tell me particularly which parts you can't figure out, maybe I can help. Just quote the part and explain what you don't get and what you think it means or something.

---

### Post by sansa dude on 2009-03-23
ok, i imputed the terminal codes fromthese points > Configure internal network card

Configure your internal network card (eth1) for static IP like so:

sudo ifconfig eth1 192.168.0.1

(The external and internal network cards cannot be on the same subnet)
Configure NAT

Configure iptables for NAT translation so packets can be correctly routed through the Ubuntu gateway.

sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

(rule1 allows forwarded packets (initial ones), rule2 allows forwarding of established connection packets (and those related to ones that started), rule3 does the NAT.)


i get an output that looks like this from terminal.

```
steve@steve-desktop:~$ sudo ifconfig eth1 192.168.0.1
[sudo] password for steve: 
steve@steve-desktop:~$ sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
steve@steve-desktop:~$ sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
steve@steve-desktop:~$ sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
steve@steve-desktop:~$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
steve@steve-desktop:~$ 

```

so is this what i am supposed to be getting when i eneter these in the terminal? and once i get to the next step 

> Enable routing

    * Configure the gateway for routing between two interfaces by enabling IP forwarding: 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

    * Edit /etc/sysctl.conf and add these lines: 

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
i went into the file system, found the file i am supposed to edit but im not too sure where in the file i am supposed to add the lines.

thats a start, thanks for the help!

---

### Post by brnetonboy on 2009-03-26
> **sansa dude said:**
> ok, i imputed the terminal codes fromthese points 

i get an output that looks like this from terminal.

```
steve@steve-desktop:~$ sudo ifconfig eth1 192.168.0.1
[sudo] password for steve: 
steve@steve-desktop:~$ sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
steve@steve-desktop:~$ sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
steve@steve-desktop:~$ sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
steve@steve-desktop:~$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
steve@steve-desktop:~$ 

```

so is this what i am supposed to be getting when i eneter these in the terminal? and once i get to the next step 


i went into the file system, found the file i am supposed to edit but im not too sure where in the file i am supposed to add the lines.

thats a start, thanks for the help!

Sorry for the delay in answering. Looking at this, I can't tell what you're doing wrong... I am not an expert by any means, in fact I'm rather new to Linux, so hopefully somebody more knowledgeable than I will post here too. As far as I can figure you're doing everything right.

--edit--
just a thought--are you perhaps using the wrong IP addresses? the ones there are just examples, you need to find out what the real IP address of the computers is.

---

### Post by sansa dude on 2009-03-28
ok, that makes sence so i will have to replace the examples with my real one. ok that seems simple enough. it just looks weird because usually when you enter a line in terminal there is  more to it than just going to the next line.

---

### Post by Selmi on 2009-06-26
did something change in 9.04 which could influence this?
i had working connection sharing in 8.04, as soon as system started and 
login screen appeared other pcs from local network could connect to internet without any problem. to set it up i made all these steps mentioned in first part of help (ifconfig, iptables magic, echo to start ip forward, edit of sysctl.conf). then i installed dnsmasq and changed it configuration file. since then all worked. to make changes permanent i added all ifconfig and iptables things to /etc/init.d/selminet and make them launch with sudo update-rc.d selminet defaults 80 and since then it was working after reboot too

now with 9.04 it doesn't. exactly same step but it works only if i always do changes locally from terminal, when its in rc.local or such init.d file it doesn't. any idea why? it seems content of rc.local was not launched at all becaue when i do ifconfig then it says only:
```
eth0      Link encap:Ethernet  HWaddr 00:06:4f:57:14:7d  
          inet6 addr: fe80::206:4fff:fe57:147d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6921 (6.9 KB)  TX bytes:4724 (4.7 KB)
          Interrupt:19 Base address:0x8c00 

```
and only when i do ifconfig manually it adds
```
inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
```
to what i wrote in previous and also only after this clients are able to connect

commands which i placed to rc.local and to this selminet script now look like this:
```

ifconfig eth0 192.168.0.1
sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward

```

any idea what i am doing wrong? btw file is executable for sure..

i found bug about rc.local not being launched on boot, this is what i experienced on 8.04 too and i have same problem now. but why this other approach with having all things in /etc/init.d fails in 9.04 is mystery to me

---
this message was corrected because i had few mistakes there about things i didn't remembered well and i forgot to mention that rc.local didn't worked well already in 8.04

---

### Post by dmizer on 2009-06-28
You'll have to install gnome-network-admin and uninstall network-manager in order for this to happen automatically.

---

### Post by Selmi on 2009-06-28
> **dmizer said:**
> You'll have to install gnome-network-admin and uninstall network-manager in order for this to happen automatically.

this did the trick! thanks. i think it should go also to documentation.

only thing i had to do after what you recommended was to set network from start - enable eth1 and eth0, set eth1 to use dhcp and set dsn manually otherwise it remained on 127.0.0.1. since then everything works well. thanks

---

### Post by mckennov3 on 2009-08-01
need help:confused:
Im newbe from linux Im using ubuntu server 9.04 eth0 & eth1 Im make it for gateway / proxy
eth0 static
address x.x.x.x
netmask x.x.x.x
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x

eth1
address 192.168.0.2
netmask 255.255.255.0

and so my server can't be internet sharing for client
# sudo /etc/init.d/networking restart
   * Reconfiguring network interfaces...
   * If-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts

please step by step to explain me for it work...[-o<
thanks alots before......

YM : [email]adhes_008@yahoo.com[/email]

---

### Post by dmizer on 2009-08-01
Please post the output of:
```
lshw -C network
```

Also, if you're using 9.04, you'll need to ditch network-manager in order to make this work. Instead, you can use gnome-network-admin.

---

### Post by deepakdeshp on 2009-09-02
I am trying to set up Internet sharing form a Ubuntu gateway connected to the internet . WIndows XP is a client connected to eth1.
The set up is simple as follows:-
Internet <<==>> eth0 <> Ubuntu gateway <> eth1 <<==>> Client PC Windows machine
 
**[SIZE=4]On The Ubuntu gateway:-[/SIZE]**
eth0 address 61.17.76.37
eth1 address 192.168.0.1
/etc/network/interfaces file is:-
# The primary network interface
auto eth0
iface eth0 inet static
 address 61.17.76.37
 netmask 255.255.255.0
 network 61.17.76.0
 broadcast 61.17.76.255
 gateway 61.17.76.1
 # dns-* options are implemented by the resolvconf package, if installed
 dns-nameservers 85.255.112.191
 dns-search domain
##############Addes following by deepak
auto eth1
iface eth1 inet static
 address 192.168.0.1
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 61.17.76.1

Addedd the following lines to /etc/sysctl.conf
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwaarding=1

[SIZE=4]On the Windows client:-
[/SIZE]Address 192.168.0.100
Mask 255.255.255.0
Gateway 192.168.0.1
DNS 85.255.112.191 (DNS address of the ISP)

The problem is that I can not ping the Windows machine from Ubuntu gateway.
I can ping both eth0 and eth1 from the Windows machine.
Internet isnt available from the Windows machine.

What should be the browser proxy setting on the Windows machine?

---

### Post by sloggerkhan on 2009-09-02
[http://firehol.sourceforge.net/tutorial.html?](http://firehol.sourceforge.net/tutorial.html?)
Shows some info on how to do a simple setup with a relatively intuitive firewall builder to create lan/internet bridinging/routing with a good basic firewall setup.

---

### Post by mellowtothemax on 2009-09-05
This is what worked for me in Ubuntu Jaunty.  

You need at least 2 different network interfaces, they can be either wireless or wired.

My setup is as follows

Internet >> Ubuntu wireless share to wired >> Windows XP or whatever OS

Assuming you have an active Internet Connection on either wireless or wired already setup.

1.  Install dnsmasq-base (most likely it is preinstalled)

2.  Right-click Network Manager in system tray and edit connections.

3.  Choose the network interface you want to share internet to and click edit.

4.  Click on the ipv4 settings tab and change Method option to shared to other computers.

5. Click Apply

6. Disable and re enable Networking by right clicking again on Network Manager.

---

### Post by oygle on 2009-09-16
I have not been able to share the internet with another Ubuntu computer. I have followed the [Help on ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") , but still no ICS available to the client computer.

One problem I found with that guide, is that it does not distinguish, in a number of areas, whether the command/s to be done are for the 'gateway' or the 'client' PC.

The guide could be improved if that was made clear.  :)

Oygle

---

### Post by tevang on 2010-01-26
I have 2 laptops and 1 socket which accepts only 1 MAC address. So I would like to connect one laptop to the socket and share connection from that to my other laptop. In the respective tutorial :

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

there's a "Ubuntu 9.10 Method". Apparently it applies to Gnome environment. I was wondering what are the equivalent steps in Kubuntu 9.10. Can anyone help me please?

---

### Post by deeflex on 2010-02-15
Hey

This guide does not seem to work in 9.10 :(

Any suggestions if I want to do it with iptables and not some gui app?

---

### Post by deeflex on 2010-03-01
This guide DO work in 9.10 as well now. 

I had to confirm that the setup was correct, so I tried to share in Windows, which worked. Then I switched back to Ubuntu and also eth0/eth1, not sure if it had anything to do with it, but that's what I tried in Windows.

Now it works!!!

In the guide it says
"For this example, eth0 is the network card on the client which is connected (by crossover cable) to eth1"

a crossover cable is NOT needed here.

---

### Post by alexisespinosa on 2010-03-29
I am having problems to share my internet connection to windows vista using the network manager.
I have Ubuntu 9.10 installed and a computer with two network cards. I'm trying to share internet from this computer to a laptop with windows vista.

I tried using the Network Manager wtih the option "shared to other computers" for eth1, but windows vista is not optaining a IP automatically, so the internet is not shared. The only thing I get in windows vista, after typing ipconfig is: ip 169.254.157.158 and subnet mask 255.255.0.0, gateway and DNS fields appear empty.

Is this a problem of the Network Manager? Should I uninstall it and install the gnome version? How can I do that?

Is this a problem of windows vista? How can I fix it?

I know that there is an option of configuring a fixed ip by editing the interfaces, sysctl.conf and the rc.local, but I want to try the "shared to other computers" option in the network manager first.

Thanks a lot,
Alexis

---

### Post by Selmi on 2010-03-29
> **alexisespinosa said:**
> ...
I tried using the Network Manager wtih the option "shared to other computers" for eth1, but windows vista is not optaining a IP automatically, so the internet is not shared. The only thing I get in windows vista, after typing ipconfig is: ip 169.254.157.158 and subnet mask 255.255.0.0, gateway and DNS fields appear empty.

Is this a problem of the Network Manager? Should I uninstall it and install the gnome version? How can I do that?
...


you have to update network manager with version taken from here: [https://launchpad.net/~network-manager](https://launchpad.net/~network-manager). version in official repository behaves exactly as you wrote. temprary workaround is that you can disable and enable connection in network manager and refresh network settings on windows side, but you have to do this after every restart....

---

### Post by dmizer on 2010-03-29
> **alexisespinosa said:**
> I am having problems to share my internet connection to windows vista using the network manager.
I have Ubuntu 9.10 installed and a computer with two network cards. I'm trying to share internet from this computer to a laptop with windows vista.

I tried using the Network Manager wtih the option "shared to other computers" for eth1, but windows vista is not optaining a IP automatically, so the internet is not shared. The only thing I get in windows vista, after typing ipconfig is: ip 169.254.157.158 and subnet mask 255.255.0.0, gateway and DNS fields appear empty.

Is this a problem of the Network Manager? Should I uninstall it and install the gnome version? How can I do that?

Is this a problem of windows vista? How can I fix it?

I know that there is an option of configuring a fixed ip by editing the interfaces, sysctl.conf and the rc.local, but I want to try the "shared to other computers" option in the network manager first.

Thanks a lot,
Alexis

No, this is not a problem at all. You will need to manually enter the DNS servers (this is typical of ICS connections). If you don't know any DNS servers to use, you can use opendns servers: [http://www.opendns.com/](http://www.opendns.com/)

If you still can't connect, then add the gateway. The gateway will be your Ubuntu PCs IP. It's probably 192.168.157.1, but check ifconfig in Ubuntu to make sure.

---

### Post by dbclinton on 2010-05-25
Hi,
I'm trying to share an Internet connection between Lucid computers and I'm having no luck so far. I'm using the "Ubuntu Internet Gateway Method (iptables)" ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)) although I configured the clients through NetworkManager rather than Terminal. Here are my settings (ifconfig on the clients confirms them):

address 192.168.0.100 (or .101)
broadcast 255.255.255.0
gateway 192.168.0.254 (which is my server's internal NIC address). 

My server accesses the internet via a proxy and I've configured the clients to use that proxy.
I know my server is configured properly because, for one session, I actually got access from one client - but I lost it when I rebooted because some other DHCP server (probably my own server which is also a thin client server) took control of it and assigned it different IPs. By the time I had figured out how to force control away from the DHCP server and keep the client's fixed address, I had somehow lost Internet. 
I will add that I definitely have network connectivity - I can use VNC from my server to view and use the clients' desktops. 
Any ideas about what I'm doing wrong?
Thanks.

UPDATE:
I'm not quite sure how, but the network is now up and running - perhaps it had something to do with the fact that I redid the configuration on my server just to make sure.

FURTHER UPDATE:
The problem was that the iptables rules I set on the server (see [https://help.ubuntu.com/community/In...nectionSharing](https://help.ubuntu.com/community/In...nectionSharing)) weren't surviving reboots and had to be saved. For information on how to do that, see the "Saving iptables" section from [https://help.ubuntu.com/community/In...nectionSharing](https://help.ubuntu.com/community/In...nectionSharing)

---

### Post by crazycaveman on 2010-05-26
I had noticed that the iptables needed to be saved as well and just added them. Hopefully it will help people in the future.  Other than that, the guide seems really good.

---

### Post by drofmij on 2010-10-13
for gui method at: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

does this work in 10.04? or 10.10?

I am trying to find a simple way to share my wired internet connection to wireless devices (ie creating a software wap with my wifi card) but haven't found an easy guide for this. Firestarter appears to be able to configure it, but it does not work just following the wizard.

any suggestions?

Thanks,
Jim

---

### Post by dmizer on 2010-10-13
> **drofmij said:**
> for gui method at: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

does this work in 10.04? or 10.10?

I am trying to find a simple way to share my wired internet connection to wireless devices (ie creating a software wap with my wifi card) but haven't found an easy guide for this. Firestarter appears to be able to configure it, but it does not work just following the wizard.

any suggestions?

Thanks,
Jim

Yes, the simple click GUI method works perfectly in all versions beyond 9.10. However, you need to be aware that your wireless card may or may not support ad-hoc networking. If you are having problems, it could simply mean that your wireless card is not capable of this.

If you need further help, you'll be better off creating a thread in the [Networking and Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section of the forums.

---

### Post by ganyx on 2010-10-17
I am building a local network with 4 nodes behind a switch and 1 node connect with two network interfaces.

Following this instruction, I still can not ping the ip outside from the nodes behind the switch.

My local network is 192.168.1.x, the server has two network interfaces, 
eth0 pointed to switch to other nodes
eth1 pointed to the internet

From the frond node connect to internet directly
```

:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  192.168.1.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

And
```

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         129.78.142.254  0.0.0.0         UG    100    0        0 eth1

```

Any one can help me on solving this problem? Thanks!


Added 18.10:

This is solved. 
At Front Node, edit file /etc/rc.local by adding one line
```

/sbin/iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth1 -j MASQUERADE

```

---

### Post by -genin- on 2010-12-22
hi...

I read [help.ubuntu.com/community/Internet/ConnectionSharing]("help.ubuntu.com/community/Internet/ConnectionSharing")

then I do all steps but the iptables...
this is my iptables...

> sudo iptables -A FORWARD -o eth0 -i eth0 -m mac --mac-source 00:23:a4:5a:ee:67 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

I just want that mac address only can use my ICS... but, everyone can use my ICS...

any idea??

*I use 1 nic...

---

### Post by jhahoneyk on 2011-01-31
Hi, I've been using the steps on [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) since a couple of years now, and its been AWESOME. THANKS to all who wrote it.

However, it doesn't work[1] with my new computer's WLAN card. My laptop accesses Internet through ppp0 and I want to share it using wlan0. However using the steps, I can't do it (I could do using my old laptop). However sharing using ethernet (eth0) works perfectly.

So, any idea why it doesn't work[1] for wlan0 but works for all other interfaces?

```
shaan@shaan-laptop:~$ lspci | grep -i wireless
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

```

[1] doesn't work == I can ping my laptop through the other machine, but not anything on the Internet.

---

### Post by larryd85 on 2011-02-03
hey, i decided to set up a ubuntu server at the house.

but i am putting it in the place of one of my ethernet couplers..... its not practical to have the server anywhere else. and a seperate cable cant be fished. 

anyway, i followed EVERYTHING to the T on the KB article [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") and even a couple things on this forum to get a connection shared.

i am running ubuntu 10.10 server edition, with an internet connection.

i am trying to connect my Windows 7 to the linux box to get an internet connection.

if anyone out there can help me out that would be greatly appreciated. 
let me know what kind of info you need me to give you.

---

### Post by jhahoneyk on 2011-02-03
> **larryd85 said:**
> hey, i decided to set up a ubuntu server at the house.

but i am putting it in the place of one of my ethernet couplers..... its not practical to have the server anywhere else. and a seperate cable cant be fished. 

anyway, i followed EVERYTHING to the T on the KB article [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") and even a couple things on this forum to get a connection shared.

i am running ubuntu 10.10 server edition, with an internet connection.

i am trying to connect my Windows 7 to the linux box to get an internet connection.

if anyone out there can help me out that would be greatly appreciated. 
let me know what kind of info you need me to give you.
Hi, first of all you should tell what the problem you faced, you didn't mention at all :P

Anyway, it will be helpful if you mention the following-

1. output of "lspci | grep -i wireless"
2. IP addresses you are using (ifconfig output can help for this)

---

### Post by larryd85 on 2011-02-03
ok well, i was having trouble getting my other pc connecting.

i was able to find an old wired Linksys router, i just used it as a switch (instead of a router)....... 

works fine now, thanks for offering support, feel free to tell me to delete my post sorry about that.

---

### Post by MisterFink on 2011-02-07
Hi there.

I am running an Asus eeepc 1005HA with Ubuntu 9.10.

Scenario: I am going to be in a hotel for two weeks that provides wired internet. There are a number of smart phones etc. that will need to access the internet via my eeepc's wireless device. I set-up ICS in Windows with no problem, but there is an issue if the internet gateway (hotel router) is going to be 192.168.0.1 as Windows ICS also used this as a gateway address. I already dual-boot Windows and Ubuntu on my eeepc, so I wanted to try ICS on Ubuntu after seeing this tutorial [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) which seems to suggest that I can share the internet through an IP range of my choosing. I chose 192.168.1.x. 

I followed the tutorial from the Ubuntu "Internet Gateway Method (iptables)" heading and as far as "Other approaches". My understanding is that this would help me share the (wired) internet through the wireless device, and that the clients would only need to connect to the wireless network and would be served an IP etc. I replaced instances of 'eth1' with 'wlan0' and where it mentioned 192.168.0... I did 192.168.1...

The tutorial doesnt talk about setting up with wireless network, but I saw from other tutorials that for ICS you usually just 'Create new wireless network', choose a Network Name/Wireless Security/Key and then connect to the network. 

This all seemed to be OK, and indeed after doing everything and rebooting, the wireless device connects to my 'test' network, but then keeps disconnecting/reconnecting. After a while, my network applet disappears from my panel so Ive no idea of the status. None of the smart phones list the 'test' wireless network.

I'm not sure where to go from here. My first question is, after I rebooted, is there anything I would have to do to start ICS again? 

I also noted this line during set-up (Configure internal network card): "sudo ifconfig eth1 192.168.0.1" I changed eth1 for wlan0, and set 192.168.1.1. But when I go into Network Setting and check the wlan0 properties, is has 'enable roamin mode' ticked with no static IP showing. Is this normal?

Sorry for sounding a bit of a dumbass. This is the most adventurous thing I've done with Ubuntu, and only just about understood what was happening with each step of the tutorial, so trouble-shooting without help is beyond me.

Thanks :)

---

### Post by Cerox Rex on 2011-03-10
Hello 

I am trying to set my buntu server box to act as a ruter/gateway. 
I have internett conectivity tru ppp0 interface wich runs from an usb modem.
And the server is "online"

Also my local computers are talking over the network as i am able to remotly administer the server via webmin and also write this post from my server box thanks to VNC from my laptop :)

Now it seems to me the problem has to do with my box not forwarding packets from eth0 to ppp0 and vica versa! I'v followed the several ics guides and am still very confused.

Atm i have no fw running.

---

### Post by dmizer on 2011-03-10
> **Cerox Rex said:**
> Hello 

I am trying to set my buntu server box to act as a ruter/gateway. 
I have internett conectivity tru ppp0 interface wich runs from an usb modem.
And the server is "online"

Also my local computers are talking over the network as i am able to remotly administer the server via webmin and also write this post from my server box thanks to VNC from my laptop :)

Now it seems to me the problem has to do with my box not forwarding packets from eth0 to ppp0 and vica versa! I'v followed the several ics guides and am still very confused.

Atm i have no fw running.

If you're having trouble configuring this and your box is acting as a gateway, I strongly suggest (for the security of your network) that you enable a firewall ASAP and worry about the finer details of your internet browsing later.

Security first, convenience second.

Also, if you're having trouble configuring this, I highly suggest that you go with a dedicated router distribution like [ClearOS]("http://www.clearfoundation.com/") (Based on CentOS) or [Zentyal]("http://www.zentyal.org/") (Based on Ubuntu). There's lots more here: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions) just take your pick.

I have used both Zentyal and ClearOS to great effect and have no complaints about either. They are extremely easy to install and you can configure them via an easy to use and understand web interface. There's lots of help and howtos, and they offer a lot more features and tools (including things like VPN, email, voip, etc) than you would have if you try to configure things yourself.

Think about your security first. If you mis-configure your firewall, you are likely opening your server to the great and unfiltered internet throngs. This is not something to take lightly. Don't make the mistake of learning how to properly configure an internet gateway firewall on a live gateway, as that's just asking for trouble.

---

### Post by Cerox Rex on 2011-03-10
> **dmizer said:**
> If you're having trouble configuring this and your box is acting as a gateway, I strongly suggest (for the security of your network) that you enable a firewall ASAP and worry about the finer details of your internet browsing later.

Security first, convenience second.

Also, if you're having trouble configuring this, I highly suggest that you go with a dedicated router distribution like [ClearOS]("http://www.clearfoundation.com/") (Based on CentOS) or [Zentyal]("http://www.zentyal.org/") (Based on Ubuntu). There's lots more here: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions) just take your pick.

I have used both Zentyal and ClearOS to great effect and have no complaints about either. They are extremely easy to install and you can configure them via an easy to use and understand web interface. There's lots of help and howtos, and they offer a lot more features and tools (including things like VPN, email, voip, etc) than you would have if you try to configure things yourself.

Think about your security first. If you mis-configure your firewall, you are likely opening your server to the great and unfiltered internet throngs. This is not something to take lightly. Don't make the mistake of learning how to properly configure an internet gateway firewall on a live gateway, as that's just asking for trouble.

I'v managed to get the fw up and running now andportscanned it from the web and i'm now secure. Also while fw was down i unplugged the cable to the wan so only lan was available.

I'll read up on thos and migth find som tips there. also i'f i wanted an easy soulution i would just use my providers box and standard fw setup. 
However i'm doing this so i can learn mor on how to setup and run a router, and administrate fw, NAT and later on apache and webservers.

---

### Post by dmizer on 2011-03-11
> **Cerox Rex said:**
> However i'm doing this so i can learn mor on how to setup and run a router, and administrate fw, NAT and later on apache and webservers.

It's fine for you to want to learn how to do this, but as I said before, it's a bad idea to learn how to do this on a live server where your entire network (as well as others if you have a live website) is potentially at risk if you make a mistake. I'm all for learning, but please do so safely. :)

---

### Post by Dr.Helperstein on 2011-03-30
Has anyone tried to share a laptop's connection that it gets from tethering with an Android (or any other) phone?

I'd like to be able to share the connection with another laptop through Ethernet. I'm having an extremely rough time trying to pull this off. I know some people have had success using EasyTether and Windows ICS to share their phones internet connection with a Xbox 360, so I may just have to try that. 

I just want to do this through Linux!

I see in the documentation that it could be a 3g or mobile bb connection but I can't get it to work for the life of me.

If anyone has any ideas, information, or link. Please let me know.

Thanks,

T

---

### Post by lukanova on 2011-06-04
hi,

on the wiki seems like a mistake. is it?

instead of:

[INDENT]Configure your internal network card (eth1) for static IP like so:
sudo ip addr add 192.168.0.1/24 dev eth0
[/INDENT]

shouldn't it be
[INDENT]
Configure your internal network card (eth1) for static IP like so:
sudo ip addr add 192.168.0.1/24 dev eth1
[/INDENT]

?

---

### Post by szal on 2011-06-09
> **lukanova said:**
> on the wiki seems like a mistake. is it?

instead of:[INDENT]Configure your internal network card (eth1) for static IP like so:
sudo ip addr add 192.168.0.1/24 dev eth0
[/INDENT]shouldn't it be[INDENT]
Configure your internal network card (eth1) for static IP like so:
sudo ip addr add 192.168.0.1/24 dev eth1
[/INDENT]?
Either that, or the example should name a different subnet, as the article states that the two network interfaces cannot be on the same subnet, and the example only covers configuring one interface.

***[Edit]*** Yes, the example should definitely read &#8216;eth1&#8217; instead of &#8216;eth0&#8217;.

---

### Post by Horibal on 2011-06-14
Currently deployed, my ISP filters MACs.  I'm hoping to connect my PSP through my laptop using 2 wireless cards.  I'd appreciate any tips specific for the PSP.  Thanks,

---

### Post by dmizer on 2011-06-14
> **szal said:**
> Either that, or the example should name a different subnet, as the article states that the two network interfaces cannot be on the same subnet, and the example only covers configuring one interface.

***[Edit]*** Yes, the example should definitely read ‘eth1’ instead of ‘eth0’.
Feel free to edit the page if you feel that there is a mistake.

> **Horibal said:**
> Currently deployed, my ISP filters MACs.  I'm hoping to connect my PSP through my laptop using 2 wireless cards.  I'd appreciate any tips specific for the PSP.  Thanks,

You should post a separate thread for this in the networking section here: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by brianmck on 2011-06-25
This documentation seems to be way out of date! In my experience ICS can be achieved in all later ubuntu versions by setting up your internet connection normally and simply going to Network Manager GUI and under IPv4 options on the port you want to share select "shared to other computers". That's it, nothing more to do - NM does it all for you

---

### Post by szal on 2011-07-20
brianmck: That would then be an additional (and nowadays probably the preferred) way of achieving the goal. I, for one, had the ifup method set up automatically on installing Kubuntu and don’t use NetworkManager—neither is there a need for it on a desktop machine without WiFi.

---

### Post by grizdog on 2011-09-11
Hi,

I've looked at the wiki and read the thread, but it didn't seem to help - I think I am almost there, but not quite.

I have my Ubuntu (lynx) connected to the internet through eth1.  I have eth0 connected to a Linksys WAP53G.  This is nothing more than a wireless access point - it is not a router at all.  The idea is to have a wireless network in my house that makes use of the firewall and other security features of my desktop computer.

I followed the dirctions in the wiki, and most things seems to work.  The default address of the WAP is 192.168.1.245, so I let it stay at that, and the default gateway that the WAP uses is 192.168.1.1, so I used that as the address of eth0 (ifconfig eth0 192.168.1.1).  I can ping those two addresses from my desktop machine, and a ping for any other address in 192.168.1 gets lost, so that appears to be working.  I have dhcp3 set up and running on my computer, is the config file:

```

INTERFACES = "eth0";
# option definitions common to all supported networks...

default-lease-time 6000;
max-lease-time 72000;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "alexfeldman.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.1 192.168.1.250;
}


```Should I have not left my domain in there?  Oh well.

No errors, or at least obvious errors, appear in the logfiles.  It just seems like the dhcp signal isn't getting out there, and that's why my laptop isn't finding a signal.

Any ideas?

Thanks.

---

### Post by SlickClick on 2012-05-12
So I have installed ver 12.x on my machine I actually like the interface except for the complicated command line gibberish found in this "guide": [https://help.ubuntu.com/community/In...nectionSharing](https://help.ubuntu.com/community/In...nectionSharing)

For the most part I figured out how to edit files using the terminal, which for a newbie it would have been nice if in the "guide" it mentioned editing files this way...

So I get to the point of "ubuntu Internet Gateway Method (iptables)" gateway setup & well basically the example code makes no sense and doesnt work at all & now im getting crash reports that I dont know what have to do with what anymore now....

Here is my setup & im sure for many others its a common setup that seems to be complicated by a simple "disabled" settings area in the GUI portion of "network settings" panel...

After trying to follow the above links "guide" it seems to me that IF when the "share connection" is selected in the ipv4 tab of the network card to bey shared that IF there in the GUI I could simply input my IP, sub-net, & gateway info there none of this other confusing command line giberish would be needed... But its all shaded out & not accessible...

I have 2 NICs one wifi which works fine & is my internet connection to my ISP router the other is the onboard wired NIC to feed a second router...

All I need for is the wired/onboard nic (eth0) to be "shared" & to have the following settings: IP 192.168.0.1 Subnet 255.255.255.0 Gateway 92.168.10.x

Its my understanding from the "guide" this has to be set/done from a terminal command line, but the guides references dont work or set the "eth0" to anything; i

---

### Post by overdrank on 2012-05-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

