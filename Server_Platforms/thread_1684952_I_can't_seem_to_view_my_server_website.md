---
title: "I can't seem to view my server website"
date: 2011-02-09
forum: Server Platforms
---

### Post by Fertech on 2011-02-09
when i type localhost i can see the page, when i type 127.0.0.1 i can see the page, when i type 192.168.0.30 i can view the page when i type the websitename.dyndns.info i can't seem to view the page or when i type 96.24.144.216 can't see the page. 

```
fertech@ubuntu:~$ sudo /etc/init.d/apache2 restart
[sudo] password for fertech: 
 * Restarting web server apache2                                                [Wed Feb 09 21:12:05 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting .[Wed Feb 09 21:12:07 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ]
fertech@ubuntu:~$ 
```

---

### Post by lisati on 2011-02-09
Is that the correct public IP address? You might want to check somewhere like [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

---

### Post by volkswagner on 2011-02-09
Possibly a NAT issue with the router.  Can folks outside your LAN access using your external ip address?  Possibly try from a cellular device?

The error is a conflict with /etc/apache2/ports and your virtual host config listen expression.  Either both need the port expression or neither.

---

### Post by Fertech on 2011-02-09
no people can't access the page from an external computer, it can only be view local, im using a clear hot spot not a router.

---

### Post by Fertech on 2011-02-09
yes i went to [http://www.whatismyip.com/]("http://www.whatismyip.com/") it's the correct public ip address.

---

### Post by volkswagner on 2011-02-09
Navigate to canyouseeme.org and verify port 80 is open.

If more than one device can connect to your hot spot device, it must have a router built in.

---

### Post by lisati on 2011-02-09
> **Fertech said:**
> yes i went to [http://www.whatismyip.com/]("http://www.whatismyip.com/") it's the correct public ip address.

My browser timed out with 96.24.144.216, but I managed to get a page with FERTECH on it when visiting 96.24.144.215

---

### Post by Fertech on 2011-02-09
Your ISP is not blocking port 80

port 80 is open

---

### Post by Fertech on 2011-02-09
yes it's 96.24.144.215 not 96.24.144.216

---

### Post by volkswagner on 2011-02-09
> **Fertech said:**
> yes it's 96.24.144.215 not 96.24.144.216

Problem solved?

Now it just seems to you need to get dyndns up and working correctly.  Are you using Ubuntu to do the updating?

---

### Post by Fertech on 2011-02-09
I type 96.24.144.215 or [http://fertech.dyndns.info/](http://fertech.dyndns.info/) and the page just keeps on loading... and it stay like that.

---

### Post by lisati on 2011-02-09
> **Fertech said:**
> Your ISP is not blocking port 80

port 80 is open

Relevance? 

Using the tools available to the forum staff, I found out that the IP address you gave in your first post (96.24.144.216) isn't the one that you used to post the first message in this thread. Is the server you're testing on the same network as the computer you're using to post in this thread?

---

### Post by volkswagner on 2011-02-09
Seems to load correctly here.

Page source seems simple.

```
<html><body><h1><CENTER>FERTECH</CENTER></h1></body></html>

```

Is this the whole page?

Perhaps you need to refresh or clear cache?

---

### Post by lisati on 2011-02-09
> **Fertech said:**
> I type 96.24.144.215 or [http://fertech.dyndns.info/](http://fertech.dyndns.info/) and the page just keeps on loading... and it stay like that.

Works for me here. The fact that I'm seeing something tells me that port forwarding on your router is probably OK, and there's possibly a configuration problem elsewhere.

---

### Post by Fertech on 2011-02-09
here is a pic of the dyndns ip address

---

### Post by volkswagner on 2011-02-09
This seems to be an issue with DynDns or your actual ip is VERY dynamic.  Try opening both your Dyndns page and canyouseeme.org and refresh the pages and see if the agree.

Also try clicking on the "your current ip address is ..." link at dyndns and see if it updates.

---

### Post by Fertech on 2011-02-09
I reset the clear hot spot, and the problem is still there. I'm posting the thread with the ubuntu server.

---

### Post by Fertech on 2011-02-09
clear port fordward

---

### Post by volkswagner on 2011-02-10
Fertech.  The issue is not with your Clear device nor with port forwarding, nor with Ubuntu Server.  This is proved by myself and lisati were able to navigate to your site.  In fact I was able to navigate to your site via your domain.

So what is your current problem?

[IMG]http://volkswagner.com/gate/fertech.png[/IMG]

---

### Post by Fertech on 2011-02-10
my problem is that i cant view it from my ip, i try it from my laptop and same problem can't view the page.

---

### Post by elico on 2011-02-10
if we can see it and you dont that means... it's something on your machine.
try to run the next commands on the terminal\shell
ping 96.24.144.215
ping [Fertech]("http://ubuntuforums.org/member.php?u=606533").dyndns.info
you should get the reply from them and also in the dyndns it should show like this:
ping fertech.dyndns.info
PING fertech.dyndns.info (96.24.144.215) 56(84) bytes of data.
64 bytes from 96-24-144-215.chi.clearwire-wmx.net (96.24.144.215): icmp_seq=1 ttl=46 time=294 ms

and also traceroute should give you a list of hosts on the way to yours.
from my server it wont get the route but from my windowfertech.dyndns.infos client i can get the full path by 18 hosts.

also try
telnet fertech.dyndns.info 80
and in the line enter GET (big letters)
and see what you got.

---

### Post by Fertech on 2011-02-10
fertech@ubuntu:~$ ping 96.24.144.215
PING 96.24.144.215 (96.24.144.215) 56(84) bytes of data.
64 bytes from 96.24.144.215: icmp_seq=1 ttl=64 time=5.64 ms
64 bytes from 96.24.144.215: icmp_seq=2 ttl=64 time=1.83 ms
64 bytes from 96.24.144.215: icmp_seq=3 ttl=64 time=1.99 ms
64 bytes from 96.24.144.215: icmp_seq=4 ttl=64 time=1.73 ms
64 bytes from 96.24.144.215: icmp_seq=5 ttl=64 time=7.35 ms
64 bytes from 96.24.144.215: icmp_seq=7 ttl=64 time=6.15 ms
64 bytes from 96.24.144.215: icmp_seq=8 ttl=64 time=1.79 ms
64 bytes from 96.24.144.215: icmp_seq=9 ttl=64 time=2.37 ms
64 bytes from 96.24.144.215: icmp_seq=10 ttl=64 time=2.22 ms
64 bytes from 96.24.144.215: icmp_seq=11 ttl=64 time=1.76 ms
64 bytes from 96.24.144.215: icmp_seq=12 ttl=64 time=1.76 ms
64 bytes from 96.24.144.215: icmp_seq=13 ttl=64 time=2.08 ms
64 bytes from 96.24.144.215: icmp_seq=14 ttl=64 time=2.99 ms
64 bytes from 96.24.144.215: icmp_seq=15 ttl=64 time=1.72 ms
64 bytes from 96.24.144.215: icmp_seq=16 ttl=64 time=1.77 ms
^C
--- 96.24.144.215 ping statistics ---
17 packets transmitted, 15 received, 11% packet loss, time 16023ms
rtt min/avg/max/mdev = 1.720/2.879/7.350/1.811 ms
fertech@ubuntu:~$ ping Fertech.dyndns.info
PING Fertech.dyndns.info (96.24.144.215) 56(84) bytes of data.
64 bytes from 96-24-144-215.chi.clearwire-wmx.net (96.24.144.215): icmp_seq=1 ttl=64 time=1.55 ms
64 bytes from 96-24-144-215.chi.clearwire-wmx.net (96.24.144.215): icmp_seq=2 ttl=64 time=1.81 ms
64 bytes from 96-24-144-215.chi.clearwire-wmx.net (96.24.144.215): icmp_seq=3 ttl=64 time=4.64 ms
64 bytes from 96-24-144-215.chi.clearwire-wmx.net (96.24.144.215): icmp_seq=4 ttl=64 time=1.73 ms
64 bytes from 96-24-144-215.chi.clearwire-wmx.net (96.24.144.215): icmp_seq=5 ttl=64 time=1.95 ms
^C
--- Fertech.dyndns.info ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 1.553/2.340/4.649/1.162 ms
fertech@ubuntu:~$

---

### Post by Fertech on 2011-02-10
fertech@ubuntu:~$ telnet fertech.dyndns.info 80
Trying 96.24.144.215...
telnet: Unable to connect to remote host: No route to host
fertech@ubuntu:~$ FERTECH.DYNDNS.INFO 80
bash: FERTECH.DYNDNS.INFO: command not found
fertech@ubuntu:~$

---

### Post by volkswagner on 2011-02-10
> **Fertech said:**
> my problem is that i cant view it from my ip, i try it from my laptop and same problem can't view the page.

If your only issue is from inside your LAN, then it is most likely a NAT issue.

If there are no settings for NAT on your Clear device, I'm not sure what you can do.

Perhaps you can edit /etc/hosts file on the server and add your dyndns domain to the static ip or loopback.  You can also edit your /etc/hosts on your laptop to point directly to the server.

---

### Post by elico on 2011-02-11
clearly some network settings.
if you can ping but cannot access the port 80 
try
traceroute  fertech.dyndns.info

just to understand how your computer is trying to get to your server IP.

i think it's one of three:
1. firewall settings
2. nat\dnat settings.
3. dont remember what i was thinking about =\

---

### Post by Fertech on 2011-02-17
what static ip do i use the router ip or the isp ip

---

### Post by volkswagner on 2011-02-17
> **Fertech said:**
> what static ip do i use the router ip or the isp ip

If you are asking me, you can use both actually.

run
```
hostname
```

and 
```
hostname -f
```
You can add each of the host names output from above, hopefully they are both the same.

/etc/hosts
```
127.0.0.1 localhost.localdomain localhost

192.168.0.30 fertech.dyndns.info fertech
96.24.144.215 fertech.dyndns.info fertech

```

You may need to enter the above info to all hosts files for machines inside your LAN.  I really think the issue has to do with NAT.  I searched NAT and Clear hotspot and found on [their forums]("http://forums.clear.com/clearcom/topics/how_can_i_make_my_on_the_go_hot_spot_open_nat?from_gsfn=true") a recommendation to call support.

---

### Post by Fertech on 2011-12-03
I had a clear hotspot, I cancel it and got comcast that solved the problem.

---

