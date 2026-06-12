---
title: "Debian server issue + questions."
date: 2009-06-11
forum: Server Platforms
---

### Post by uberlube on 2009-06-11
I have recently set up a Debian home server following the guidlines from the how-to forge and so far things are running excellent. At least up until ISPconfig told me that my clamAV updater hasn't been receiving database updates. I logged in and ran freshclam and freshclam -v recieving a reply on both that a connection to get the daily isn't being made. It also said that im using an outdated version. So I decided to run apt-get update/upgrade and it also told me that it could not make the connection. I am led to believe that somehow i've blacklisted something or ive blocked incoming connections somehow. If anyone could help me get this up and running again it'd be much appreciated. I have verified that I have a connection on this box as i've logged into it remotely via ssh.


Which leads me to my next question. I am only able to log into my server via ssh as my administrator atm. Can i set up users for this via ISPconfig or do i have to manually make them. If you could explain it or give me a link to a RELEVANT howto that would be great.


Also if I am not within my home network how can i log into my server? I have DYNdns set up and working properly (as i have used it before to log into my main cpu using ssh a while back) but will i encounter issues logging into my server seeing as how i have 3 cpu's in my internal network?

Thanks for taking the time to read this and hopefully answer it.

---

### Post by uberlube on 2009-06-11
Also if anyone has come across a good admin cheatsheet that is relevant to my setup id love a link. ;)

---

### Post by uberlube on 2009-06-12
bump

---

### Post by drave99 on 2009-06-12
if you cannot apt-get then you could have some fundamental problems to begin with so..

turn the firewall off
can you ping your gateway
is your dns resolution OK, can you ping [www.google.com](www.google.com)
if all that lot is OK you "should" be able to apt-get

ISPconfig ?? dont know that

for remote logins
create an account on the box you want to login to
put a NAT rule in your router and route port 22 from the internet to that box
disable root login and login prompts, use rsa keys for security

---

### Post by uberlube on 2009-06-12
Thanks for the response. 

Im currently doing a clean install on my workstation atm but once i get my system back up ill try to ping google and see if it works.

As for the NAT idea with the router that seems to be a viable solution.

If anyone else can give me help with the ISPconfig/SSH question id love to hear your ideas.

---

### Post by uberlube on 2009-06-12
ok ping to google gives

```
server1:/home/administrator# ping google
connect: Network is unreachable

```

---

### Post by cariboo on 2009-06-12
How does your server get it's ip address. through dhcp or did you set up a static ip address?

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> ok ping to google gives

```
server1:/home/administrator# ping google
connect: Network is unreachable

```

Please post the output of the following from your server :
```

ifconfig -a
route -n
cat /etc/resolv.conf
ping 194.109.21.51

```

(And I guess you meant to type : ping google.com)

---

### Post by uberlube on 2009-06-12
```
server1:/home/administrator# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:47:88:e5:a5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe88:e5a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33808228 (32.2 MiB)  TX bytes:1907409 (1.8 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1727203 (1.6 MiB)  TX bytes:1727203 (1.6 MiB)

```
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```
```
server1:/home/administrator# cat /etc/resolv.conf
nameserver 192.168.1.1

```
```
server1:/home/administrator# ping 194.109.21.51
connect: Network is unreachable

```

---

### Post by uberlube on 2009-06-12
i set my server as static

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> ```

[CODE]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

Looks good, except that you're missing a gateway in the routing table.

Try this to see whether that helps :
```

sudo route add default gw 192.168.1.1

```
If that works, edit your network settings to include that gateway.

---

### Post by uberlube on 2009-06-12
AH HA!! that did the trick. So is that pertinently added or do i have to manually add it to keep it after reboot?

---

### Post by uberlube on 2009-06-12
also any advice on how to add users for my ssh?

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> AH HA!! that did the trick. So is that pertinently added or do i have to manually add it to keep it after reboot?

That "route" command defines a gateway only once.

Configuring it permanent depends on your configuration, did you use /etc/network/interfaces, or Network Manager (or wicd) ?

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> also any advice on how to add users for my ssh?

Adding a new user (as you would normally do) will mean that you have a new user that can use ssh.

You can use "AllowUsers" to restrict access, see here :
[http://www.faqs.org/docs/securing/chap15sec122.html](http://www.faqs.org/docs/securing/chap15sec122.html)

---

### Post by uberlube on 2009-06-12
ill have to add it via /etc/network/interfaces as i have no DE installed on the server. Should i do a reboot after i do this?

---

### Post by uberlube on 2009-06-12
> **albinootje said:**
> Adding a new user (as you would normally do) will mean that you have a new user that can use ssh.

You can use "AllowUsers" to restrict access, see here :
[http://www.faqs.org/docs/securing/chap15sec122.html](http://www.faqs.org/docs/securing/chap15sec122.html)

If i understand you correctly you mean add a new user account to the server box? What im trying to accomplish is to give someone an account that is not within my internal network so he can gain access from his house.

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> ill have to add it via /etc/network/interfaces as i have no DE installed on the server. Should i do a reboot after i do this?

Yes. Here's an example : [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
So in your case it would be like this, assuming that you have eth0 as network interface in use :
```

iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1

```

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> If i understand you correctly you mean add a new user account to the server box? 

Yes.
> 
What im trying to accomplish is to give someone an account that is not within my internal network so he can gain access from his house.
Just for accessing files ? If so, then you might want to consider giving that person a scponly account instead of a ssh account.

And do you have it working already for another ssh user ?
If not, then you probably need to configure port forwarding for ssh (port 22) in your router.

---

### Post by uberlube on 2009-06-12
> **albinootje said:**
> 

Just for accessing files ? If so, then you might want to consider giving that person a scponly account instead of a ssh account.

And do you have it working already for another ssh user ?
If not, then you probably need to configure port forwarding for ssh (port 22) in your router.

The only account i can log into with ssh so far is the administrator account and through that i can root for maintinence.

So scponly is that way to go for that? ill look into it now.

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> The only account i can log into with ssh so far is the administrator account and through that i can root for maintinence.

So scponly is that way to go for that? ill look into it now.

Scponly is a way to give users only access to files via ssh.

Here's a short howto :
[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

Read the "Normal SFTP" section, and ignore the "Chroot/Jail SFTP" section.

---

### Post by uberlube on 2009-06-12
Also i hit a snag, i rebooted and the new DG didnt take for some reason. Here is what my interfaces looks like now after i added in that command u told me about, see anything wrong?

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.102
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.0.1


```

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> Here is what my interfaces looks like now after i added in that command u told me about, see anything wrong?

```

        gateway 192.168.0.1

```

You made a typo it looks like, make that 1.1 instead of 0.1 in the end, and try again ;-)

---

### Post by uberlube on 2009-06-12
lol k 1 sec

---

### Post by uberlube on 2009-06-12
While im rebooting, i installed scponly and it looks pretty straightforward. So again, if im understanding correctly, iif i want anyone to be able to access my server they must have a physical user profile made on that box? and then i just use scponly on their username? Also is ISP config able to do any of this kind of management for me?


EDIT: yup i can ping google.com after reboot

---

### Post by albinootje on 2009-06-12
> **uberlube said:**
> While im rebooting, i installed scponly and it looks pretty straightforward. So again, if im understanding correctly, iif i want anyone to be able to access my server they must have a physical user profile made on that box? and then i just use scponly on their username? 

Please read the article about scponly that I mentioned in one of the previous comments. That article has instructions for that.
> 
Also is ISP config able to do any of this kind of management for me?

According to the ISPconfig website frontpage.. no.
Maybe you'd like to try webmin instead of ISPconfig : [http://www.webmin.com](http://www.webmin.com)
> 
EDIT: yup i can ping google.com after reboot
Good :-)

---

### Post by cariboo on 2009-06-12
@uberlube

You don't have to reboot after making changes. Depending on the service you are configuring, just restart the service for example you are working on networking right now, so to restart networking at the prompt type:

```
sudo /etc/init.d/networking restart
```

If you were editing apache config files:

```
sudo /etc/init.d/apache2 restart
```

you can also just stop or start a service

---

### Post by uberlube on 2009-06-12
K ive got users made and working now, thnx alot! One more question though, can i run ISPconfig and webmin together or will they interfere with one another?

---

### Post by uberlube on 2009-06-12
> **cariboo907 said:**
> @uberlube

You don't have to reboot after making changes. Depending on the service you are configuring, just restart the service for example you are working on networking right now, so to restart networking at the prompt type:

```
sudo /etc/init.d/networking restart
```

If you were editing apache config files:

```
sudo /etc/init.d/apache2 restart
```

you can also just stop or start a service

thnx for the tip :p

---

### Post by uberlube on 2009-06-12
great now mydns is down...

```
server1:/etc/init.d# mydns restart
mydns: Extraneous command-line arguments ignored
mydns[19933]: mydns 1.2.8.25 started Fri Jun 12 18:16:25 2009 (listening on 3 addresses)
^Cmydns[19933]: interrupted
mydns[19933]: server1.home.net up 2m9s (129s) 3 questions (0/s) NOERROR=2 SERVFAIL=0 NXDOMAIN=0 NOTIMP=0 REFUSED=0 
mydns[19934]: interrupted
mydns[19934]: server1.home.net up 2m9s (129s) 9 questions (0/s) NOERROR=2 SERVFAIL=0 NXDOMAIN=0 NOTIMP=0 REFUSED=0 (33% TCP, 3 queries
```

---

