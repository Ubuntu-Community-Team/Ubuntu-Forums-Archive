---
title: "Improvements to my UFW list?"
date: 2017-01-25
forum: Security
---

### Post by thane1 on 2017-01-25
Trying to set up UFW rules to lock things down, as my system is about to become much more complicated with new equipment soon and there will be inter-device and internet access concerns.  Everything seems to work now as far as I can tell (a little knowledge being dangerous).  But I need some advice on the “in” vs “out” on a lot of these rules please, as I am afraid I may have opened too much. 

 For instance I am confused by such requirements as needed “passthrough” and what I am actually needing to stop/allow.  As background I now use a vpn service (NordVPN) , my isp blocks ```
25
``` inbound and Thunderbird with my isp’s email and also gmail uses ```
143, 110, 993
``` for “server” ports and ```
25, 465, 587
``` for the smtp side.  I have been thinking that the account server side ports should only be open for the “in” traffic and the smtp ports for the “out” traffic.  My vpn service requires me to allow ```
1723 tcp, 443 tcp, 1194 udp
``` to be open.  Does this mean they should be in, out or both?  ```
Port 53
``` I have set to both in and out for the dns.  Do I need both?  I have ```
80
``` open both in and out, although I have read that ```
80
```  inbound is the most common route for attacks and that incoming traffic will come in anyway on other ports.  Is this wrong?  Also blocked for future use is ```
1900
``` in and out to stop IoT access with the internet.  Apparently IoT was never originally meant to be used with net access and is a huge safety concern as I understand it. 

 At present I think these are the only ports I am concerned with --> no need for ftp, ssh, etc yet.  Included below is a copy of my ufw list.  Are there any weaknesses in the list, non-necessities or redundancies?  Pretty soon there will be two routers and some subnets in the system, so I’d like to get started off on the right track, as I do want to exercise control soon over what devices can access other devices, the internet, etc.  Thanks.

     To                         Action      From
     --                         ------      ----
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 1194/udp                   ALLOW IN    Anywhere                  
[ 2] 1723/tcp                   ALLOW IN    Anywhere                  
[ 3] 1900                       DENY OUT    Anywhere                   (out)
[ 4] 1900                       DENY IN     Anywhere                  
[ 5] 53/tcp                     ALLOW OUT   Anywhere                   (out)
[ 6] 53/tcp                     ALLOW IN    Anywhere                  
[ 7] 80/tcp                     ALLOW OUT   Anywhere                   (out)
[ 8] 80/tcp                     ALLOW IN    Anywhere                  
[ 9] 443                        ALLOW IN    Anywhere                  
[10] 25/tcp                     ALLOW OUT   Anywhere                   (out)
[11] 110                        ALLOW IN    Anywhere                  
[12] 143                        ALLOW IN    Anywhere                  
[13] 465                        ALLOW OUT   Anywhere                   (out)
[14] 587                        ALLOW OUT   Anywhere                   (out)
[15] 993                        ALLOW IN    Anywhere                  
[16] 1194/udp (v6)              ALLOW IN    Anywhere (v6)             
[17] 1723/tcp (v6)              ALLOW IN    Anywhere (v6)             
[18] 1900 (v6)                  DENY OUT    Anywhere (v6)              (out)
[19] 1900 (v6)                  DENY IN     Anywhere (v6)             
[20] 53/tcp (v6)                ALLOW OUT   Anywhere (v6)              (out)
[21] 53/tcp (v6)                ALLOW IN    Anywhere (v6)             
[22] 80/tcp (v6)                ALLOW OUT   Anywhere (v6)              (out)
[23] 80/tcp (v6)                ALLOW IN    Anywhere (v6)             
[24] 443 (v6)                   ALLOW IN    Anywhere (v6)             
[25] 25/tcp (v6)                ALLOW OUT   Anywhere (v6)              (out)
[26] 110 (v6)                   ALLOW IN    Anywhere (v6)             
[27] 143 (v6)                   ALLOW IN    Anywhere (v6)             
[28] 465 (v6)                   ALLOW OUT   Anywhere (v6)              (out)
[29] 587 (v6)                   ALLOW OUT   Anywhere (v6)              (out)
[30] 993 (v6)                   ALLOW IN    Anywhere (v6)             
[31] Anywhere (v6)              DENY OUT    Anywhere (v6)              (out)

---

### Post by TheFu on 2017-01-25
Please use "code tags" when posting things that should line up nicely. Harder to read otherwise.

The simple answers are these:
Block everything inbound by default, unless you intend to run a service/listener/daemon on the port. External VPN services generally don't need **any** inbound ports open.

For most people, it is smartest to allow only ssh in, so you can get back to your home network from anywhere. Then there is little need to allow any other ports open on the internet.

If you **are not** running an email server, then you don't need to open any of those ports inbound.  If you are running an email server, it would be smart to place an email gateway on a $5/month VPS and use ssh to pick up that email as needed to your main system in the house.

Learn to use ssh for most things.  It is an amazing tool.

VPNs have 2 purposes.
a) Hide your outbound traffic from your ISP or nearby network providers. No inbound firewall rule necessary.

b) Allow secured inbound connections to your network. ssh can do this too, but for non-technical users, openVPN can make it easier, assuming YOU setup their client access. 1 inbound firewall rule needed, only for the single port (should be UDP) and it is smart to make it non-standard, if that will work for the locations your client will connect from.

For example, I run a nextcloud server, but don't allow access over the internet.  To use it, either clients need to be on the LAN or they need to appear as if they are on the LAN using either openvpn or ssh tunnels.  For a few, small, subnets, for places I frequent, I do allow direct access over HTTPS without the VPN, but there is a yuuuuuge difference between allowing the entire world access to that service and allowing a single /24 subnet access.  Make sense?

Basically, if you aren't running any public services, it is best to have only ssh available to the world and run that on a non-standard port - something high, above 50K just to keep all the riff-raff away.  Also run something like fail2ban to block infinite brute-force attacks.

---

### Post by TheFu on 2017-01-25
It is very unlikely that allowing inbound 53/tcp/udp is a smart idea. I've been hacked 2 times in my career. Once was over port 53. I pay external DNS providers for this service now.  $20/yr goes a long way for my sanity.  I self-host pretty much everything else.

---

### Post by thane1 on 2017-01-25
Thanks TheFu.  I will use the code tags next time.  Will sift through my firewall settings using your ideas and see, what I can modify. 

 I don't run any servers, don't access my system from elsewhere and it's just a home system.  No services, listeners or daemons.  I haven't used ssh to this point in time, but am planning to use it in the near future to update/maintain/modify a few of the devices behind my first router from behind the most-trusted zone main computer behind the soon-to-be second router . I am somewhat uncertain about the meaning of your part b answer for vpn's.  I do use the opendns servers and use the openvpn option on my NordVPN service.  Your line > 1 inbound firewall rule needed, only for the single port (should be UDP)  has me a bit puzzled though.  Is this the port 1194 you're referring to, which my vpn service requires to be open?  I have no intention of allowing anyone (including myself) to ssh in from outside of my system in the near future.  Not sure if that would change.  Fail2ban is new to me.  I will look that up, when the hectic bit of getting the new system has subsided.  Your second post > It is very unlikely that allowing inbound 53/tcp/udp is a smart idea. has me wondering also.  I wasn't sure if I needed port 53 open on the inbound.  If I remove that "allow inbound" rule will the dns lookup come back by another route instead?  I'm not informed enough to know the path a dns lookup would normally return by.

---

### Post by TheFu on 2017-01-25
If you aren't running a DNS server for the entire world, then you don't need/want any inbound port 53 allowed.
The same for the VPN service on 1194.  If your system connects to them, you do not need inbound port open.

If you aren't running any services, then you do not need any inbound ports open. I'm 99.999999999999999% certain of that. 

It could help others if you edited the first post and added code tags too.

If you want to understand how the internet works, grc.com/sn has a few episodes about just that beginning at ep 25.

---

### Post by thane1 on 2017-01-25
Thank you so much TheFu!!  Trying to find specifics like this by doing online searches is almost futile I've found.  I will edit my first post in short order with the code tags.  Also I have only just recently found and have been watching the Security Now podcasts.  That is where I found out about the potential problems of leaving IoT 1900 UPnP port open among other things.  Haven't gotten that far back to see episodes starting at number 25.  I will definitely do that shortly.  Many thanks.

---

### Post by TheFu on 2017-01-25
UPnP should be disabled if you care about security at all. Allowing devices to control the ports on a router is asking for problems.  Any javascript running can determine the router IP and send UPnP commands effectively opening the entire subnet to any attack. It isn't wide spread yet, but you can bet someone is using this as an attack vector.  

BTW, every security expert I know has little respect for SG, mainly because he has made big deals about nothing for decades. 

Ufw is not a firewall, it is an interface into the Linux kernel firewall - [netfilter]("https://www.netfilter.org/documentation/HOWTO/netfilter-hacking-HOWTO-3.html").  Same for iptables or ipset or gufw or any other firewall program on a Linux system since the 2.6.x line. Not that it matters much, just for technical accuracy.

Your ufw so default to **blocking all inbound ports** except those you want to work on your subnet. Everything on the internet should be blocked, unless you specifically, know it must be opened.  Basically, try it close and if it doesn't work, then open 1 port at a time and watch the firewall logs.

---

### Post by thane1 on 2017-01-25
Learning all kinds of new things today.  Will start in again in earnest tomorrow and make good progress.  It's been rather daunting at my age (a senior) trying to learn ip addressing, netmasking, firewalls, vpns, etc all at the same time.  I may have another question or two in the next couple of days related to this thread.  Thanks again TheFu.

---

### Post by kevdog on 2017-01-25
My only advice,  run iptables directly setting it up through a script file.  Much more versatile solution if you ever possibly want to move to a different linux platform.  You can also pass kernel tunning parameters.   I'm glad you're getting started with running a firewall -- and only if I could take my iptables command and translate them into a freebsd firewall....

---

### Post by thane1 on 2017-01-25
Thanks Kevdog for your reply.  I have played with iptables a little bit.  But due to time constraints and the amount of other learning I'm having to do on the other skills right now, getting to grips with ufw is just more practical at present for me.  Iptables is in my future though.  cheers

---

### Post by thane1 on 2017-01-27
This is better.  Did a lot of edits and got locked out of both email and web access at one point.  Couldn't get it back with ufw but eventually got back to square one with the iptables -F -Z and -X method.  Did I somehow develop a deny line before the start of my own rules list that didn't show up with a ufw status command?  Thanks for steering me in the right path.  One last question if I could please.  I understand it is more efficient to order rules in a way that the system doesn't need to process lesser used rules unnecessarily.  Is there a general rule of thumb for a list like mine below, for grouping rules in a certain order?  This list will get more complicated in the near future as I assemble the new system.  Many thanks.


```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 110                        ALLOW OUT   Anywhere                   (out)
[ 2] 25                         ALLOW OUT   Anywhere                   (out)
[ 3] 53/tcp                     ALLOW OUT   Anywhere                   (out)
[ 4] 80/tcp                     ALLOW OUT   Anywhere                   (out)
[ 5] 443                        ALLOW OUT   Anywhere                   (out)
[ 6] 1194/udp                   ALLOW OUT   Anywhere                   (out)
[ 7] 1723/tcp                   ALLOW OUT   Anywhere                   (out)
[ 8] 110 (v6)                   ALLOW OUT   Anywhere (v6)              (out)
[ 9] 25 (v6)                    ALLOW OUT   Anywhere (v6)              (out)
[10] 53/tcp (v6)                ALLOW OUT   Anywhere (v6)              (out)
[11] 80/tcp (v6)                ALLOW OUT   Anywhere (v6)              (out)
[12] 443 (v6)                   ALLOW OUT   Anywhere (v6)              (out)
[13] 1194/udp (v6)              ALLOW OUT   Anywhere (v6)              (out)
[14] 1723/tcp (v6)              ALLOW OUT   Anywhere (v6)              (out)


```

---

