---
title: "Configuring iptables"
date: 2009-08-06
forum: Security
---

### Post by terminator14 on 2009-08-06
I just setup an Ubuntu Server on one of my old machines and got a second ip address from my ISP so my home LAN and the server are on separate networks. I plugged in the modem into a 10/100 dlink switch along with the router I had before for my home network, and the server (I think this setup is right and it seems to work but if it isn't please correct me).

Anyway, since my server is connected directly to the internet with no router running a firewall to protect it, I need to configure the iptables firewall on the server to block everything except the ports I need to keep my server secure. This is what I ran, which I gathered from a few online resources:

```
sudo iptables -F
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 2/s -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 22 -s 0/0 -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -j LOG --log-level warning --log-prefix "Unauthorized Network Access"
```

I also tried running the above commands with -i eth0 where it seemed necessary but I guess that's not required since eth0 is my only real interface.

Most of this seems to work, as the pinging works to the server unless I increase it to 5 times per second where the limit rules on ICMP kicks in and starts dropping packets. The SSH port is also open just like the rules above state, which is what I wanted. I can access the internet with the server (ping google) so the ESTABLISHED,RELATED rules seem to be working as well.

The problem I'm having is that when I do a portscan with any kind of utility (zenmap or ubuntu's network tools app) on the server, I always see a bunch of ports open that are not in the rules above anywhere. These ports include ftp (21), ssh (22) - this one is supposed to be open so that's good, rtsp (554) - no idea what that is, and realserver (7070) - also no idea about this one. These are all tcp. Why is the firewall not blocking these ports? Or is this expected?

---

### Post by gombadi on 2009-08-06
> 
The problem I'm having is that when I do a portscan with any kind of utility (zenmap or ubuntu's network tools app) on the server

and

sudo iptables -A INPUT -i lo -j ACCEPT


If you do the portscan on the server, and to the server, you will probably be using the loopback interface. You have a firewall rule to allow all traffic arriving on the loopback interface.

If you want to see what processes and ports the server is listening on then run this command -
```

netstat -plntu

```

If you still see strange ports open but your server does not show them open then I would guess you are not actually scanning the server but some other device.

---

### Post by terminator14 on 2009-08-07
Sorry for the crappy looking drawing but I still can't find an easy to use drawing tool for linux. Anyway, the attached image has the basic idea of my network. Both the router, and the ubuntu server have different external ip addresses (as opposed to the PCs which all share the router's external ip address). When I did a port scan, I ran it from PC1 on the diagram, using the external ip of the ubuntu server. The results I see, as far as I can tell is what everyone else on the internet sees when they portscan my server. Just to be sure, I also asked a friend to port scan my server and he got the same results - random ports being open on my server. As for the netstat command, it shows that a bunch of services on the server are "listening", but I don't know if that means they are listening through the firewall, or they don't know that nothing can contact them because of the firewall.

---

### Post by sasho_zl on 2009-08-07
You can install shorewall - it is very easy and powerful tool for configuring your firewall. 
I have wrote how to set it up here - [http://ubuntuforums.org/showthread.php?p=7736369#post7736369](http://ubuntuforums.org/showthread.php?p=7736369#post7736369)
That way you will have a file /etc/shorewall/rules which is very easy to manage.
And also I recommend that you change your ssh from port 22 to something else.

---

### Post by terminator14 on 2009-08-07
> **sasho_zl said:**
> You can install shorewall - it is very easy and powerful tool for configuring your firewall. 
I have wrote how to set it up here - [http://ubuntuforums.org/showthread.php?p=7736369#post7736369](http://ubuntuforums.org/showthread.php?p=7736369#post7736369)
That way you will have a file /etc/shorewall/rules which is very easy to manage.

Thanks, I'll have a look at that.

> **sasho_zl said:**
> 
And also I recommend that you change your ssh from port 22 to something else.
Ya, I usually do, just wanted to get the basic firewall up before messing with anything else.

---

### Post by cariboo on 2009-08-07
> The problem I'm having is that when I do a portscan with any kind of utility (zenmap or ubuntu's network tools app) on the server, I always see a bunch of ports open that are not in the rules above anywhere. These ports include ftp (21), ssh (22) - this one is supposed to be open so that's good, rtsp (554) - no idea what that is, and realserver (7070) - also no idea about this one. These are all tcp. Why is the firewall not blocking these ports? Or is this expected?

If you use the builtin port scan utility you will get false readings, See this bug [lpbug]257042[/lpbug]. I haven't used zenwalk (I prefer the console for server administration), so I can't say how it works. I would check to see what servers you are running and shut down everything you don't need. I would also get rid of ftp, and use sftp which is a part of the openssh-server package, that way you can close one more port. Most ftp client (filezilla and gftp) also do sftp.

---

### Post by terminator14 on 2009-08-09
> **cariboo907 said:**
> 
I haven't used zenwalk (I prefer the console for server administration), so I can't say how it works. 

I have never used zenwalk either and am administering my server through CLI as well. Zenmap, is a GUI interface for nmap, a very common network scanning tool which I use. I have never heard of zenwalk.

> **cariboo907 said:**
> If you use the builtin port scan utility you will get false readings, See this bug [lpbug]257042[/lpbug]. 

Thanks for the info about the bug, I never knew that. I'll be sure to double check any results I get from it now, or possibly avoid it altogether. 

> **cariboo907 said:**
>  I would check to see what servers you are running and shut down everything you don't need. I would also get rid of ftp, and use sftp which is a part of the openssh-server package, that way you can close one more port. Most ftp client (filezilla and gftp) also do sftp.

Shutting down unneeded services sounds like a good idea to free up resources and make the server more secure. Switching to sftp is also a good idea. I will definitely do that at some point. Figuring out how sftp works and which services I'm running that I won't need may take me some time though, however short or long. I was hoping to bring the server permanently online soon though and I can't do that without being 100% satisfied that the firewall is configured to my liking and only letting services that I want be reachable from the internet. Right now though, this is not the case as I am still having trouble with iptables. 

As soon as I have some free time, I will look into the shorewall firewall recommended above which sounds promising, but meanwhile, if anyone knows of any reason my iptables configuration might not be blocking everything I need it to, please let me know.

---

### Post by cariboo on 2009-08-09
That was a typo on my part, it should be zenmap, not zenwalk, sorry.

---

### Post by The Cog on 2009-08-09
> **terminator14 said:**
> As soon as I have some free time, I will look into the shorewall firewall recommended above which sounds promising, but meanwhile, if anyone knows of any reason my iptables configuration might not be blocking everything I need it to, please let me know.

Use the command sudo **iptables -nvL** to see what the actual rules (and packet counts) are. It might reveal something.

---

### Post by terminator14 on 2009-08-09
> **The Cog said:**
> Use the command sudo **iptables -nvL** to see what the actual rules (and packet counts) are. It might reveal something.

I've been checking the rules with **iptables -L** the whole time to make sure the rules are correct, and they seem to reflect what I wrote above. I will try the extra nv parameters and see if I get any more useful info.

It seems that after trying everything rational I could think of to discover/solve the problem, trying something irrational showed some interesting results. I just tried to port scan the server after shutting it down. The extra ports I kept seeing are still found to be open by nmap! I am not scanning the wrong IP since I have double checked it many times, and when I add ssh in the rules above, the port scan reveals an open ssh port, and when I remove ssh from the rules, the port scan shows it disappear as well. Is there any reason a shut down system would have ports open?

---

### Post by koenn on 2009-08-09
shutdown systems can't respond to any connection attempt, so if nmap shows an open port, your scanning something else than what you think you're scanning

could it be you're actually scanning that router you have there ? maybe by mistake (it probably has an IP adress very similar to the address of the server) ? Or there is some peculiar NAT / MASQ / REDIRECT thing going on ?

---

### Post by terminator14 on 2009-08-09
> **koenn said:**
> shutdown systems can't respond to any connection attempt, so if nmap shows an open port, your scanning something else than what you think you're scanning

could it be you're actually scanning that router you have there ? maybe by mistake (it probably has an IP adress very similar to the address of the server) ?

I wish that were the case since that would be an easy fix, but unfortunately, like I said, I can effect the outcome of the port scan by changing firewall rules on the server (either add or remove port 22 as being open). The only thing that doesn't change are the 3 ports that are always open:

```
$ nmap [server ip] -PN

Starting Nmap 4.76 ( http://nmap.org ) at 2009-08-09 10:58 MDT
Interesting ports on [server ip]:
Not shown: 997 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
554/tcp  open  rtsp
7070/tcp open  realserver

```

This scan was done when the server was shut down. I used the -PN arguments for nmap because when I don't (when I run **$ nmap [server ip]**), I get:

```
Starting Nmap 4.76 ( http://nmap.org ) at 2009-08-09 11:00 MDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.06 seconds
```

Performing the same scan while the server is up and the iptables rules I posted above are applied I get:

```
$ nmap [server ip] -PN

Starting Nmap 4.76 ( http://nmap.org ) at 2009-08-09 11:12 MDT
Interesting ports on [server ip]:
Not shown: 996 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
554/tcp  open  rtsp
7070/tcp open  realserver

Nmap done: 1 IP address (1 host up) scanned in 16.87 seconds

```

If the server is up and I scan without the -PN argument, I get:

```
Starting Nmap 4.76 ( http://nmap.org ) at 2009-08-09 11:12 MDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.06 seconds
```

If however I flush the iptables rules with **iptables -F** and run the nmap again without the -PN tag, it easily discovers the server along with about 10 open ports.

Another thing that might be worth noting is that my server gets its external ip address through DHCP (for now) so every time it gets restarted, it seems to change its IP (I think it juggles about 3 ip addressees it could be) so I guess there's no way for me to tell while the server is down which ip belongs to it since none are assigned while it is down. The results above of port scans while the server is down are basically aimed at the last ip the server used before it was shut down but I still can't be sure what I'm scanning. It is a pretty big coincidence however that while the server is down the same ports are open as when the server is up (with the exception of ssh which depends on the firewall rules I set). At least the ssh port stops being open when the server is shut down.

> **koenn said:**
> Or there is some peculiar NAT / MASQ / REDIRECT thing going on ?

This is what I think might be happening since I'm not entirely sure how to setup 2 external ip addresses physically. I drew that diagram above of what my setup looks like, but this might not be the ideal way to configure a 2 ip address setup, and the 2 networks (server and home LAN) might be interfering with each other somehow.

---

### Post by koenn on 2009-08-09
Here's a theory. It's probably wrong, but it's a start :

Let's say that you think you're scanning the server, but in fact your scanning the router, which happens to have ports 21, 554 and 7070 open, and has port 22/tcp forwarded to the server. In that case, you would get the results you describe : the router answers for ports 21, 554 and 7070, the server answers for 22 when it's up and it's firewall doesn't block that port. 

Another theory, even more far-fetched:
Both the router and the server respond to the address you scan, and each respond to probes on *some* ports - like in the first theory


I know just how unlikely that sounds, but
a/ it explains what I meant with "you're not scanning what you think you're scanning" - it also explains why I suspect there might be some sort of Address Translation/port forwarding going on *somewhere*

b/ it raises some questions that might help diagnose this : in what sort of circumstances could things as in those 2 theories, actually happen ?

I think you should check your router (is it an appliance or a linux box with routing / iptables ?) and its configuration.

The modem and how you connect to the internet may play a role - is it a pppoe conf ?  Does your ISP provide info on how it serves multiple addresses over the same modem ? Are you quite sure it does DHCP ? Are you quite sure you actually *get* 2 addresses ?

It might be helpfull if you could pin some IP addresses on your diagram. Now you only show 'this cable goes from here to there' - that does not explain how the network is (logically, at IP-level) is layed out.

You might want to give a static address to the server and see if you can reproduce your problem. 

554/tcp  and 7070/tcp are typical for a Real Media / Real Networks RealServer - a audio / video streaming server for RealPlayer clients. That may give you a clue. 

You could also repeat you nmap with '-O' to do OS detection, and maybe 'sO' for service probing, it might give details about what machine you're looking for.

---

### Post by terminator14 on 2009-08-18
After some more tests, it seems that any IP I scan with nmap shows those 3 ports open. Is this a known nmap bug or something? I tried to use several online port scanners with the original iptables rules I posted, and only port 22 is shown as open. Weird...

---

### Post by koenn on 2009-08-18
there's a bug in the gnome nettool portscanner (the  GUI portscanner in network tools), it shows random high ports as  open. I'm not aware of a similar bug in nmap but you could google for it (eg with the version number of your nmap)

---

### Post by mmhohman on 2009-11-26
> **terminator14 said:**
> After some more tests, it seems that any IP I scan with nmap shows those 3 ports open. Is this a known nmap bug or something? I tried to use several online port scanners with the original iptables rules I posted, and only port 22 is shown as open. Weird...

Hi terminator14,

I'm guessing that the reason you're (we're) having this problem is that you're using an AirPort Extreme Base Station, see [http://discussions.apple.com/thread.jspa?threadID=1531675&tstart=77](http://discussions.apple.com/thread.jspa?threadID=1531675&tstart=77)

I haven't been able to figure out how to make it stop, though.

---

### Post by bodhi.zazen on 2009-11-26
See:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/fir...untu-desktops/]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/")

[http://blog.bodhizazen.net/linux/fir...buntu-servers/]("http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/")

---

