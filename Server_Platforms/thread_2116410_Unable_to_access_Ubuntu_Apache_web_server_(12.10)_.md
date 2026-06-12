---
title: "Unable to access Ubuntu Apache web server (12.10) from internal (or external) LAN"
date: 2013-02-15
forum: Server Platforms
---

### Post by themykel on 2013-02-15
I am using Ubuntu 12.10 server x64 to run a SpotWeb for newsgroup access. However, I am unable to ping the IP of the ubuntu server within my network (although localhost is fine). I have searched the forums for a solution and have tried multiple but am unable to come up with something that works so hoping that someone can help!

Here is what I have done so far:

- I have done a fresh 12.10 install and setup Spotweb for my NZB needs (Sickbeard YAY!). 
-I have installed firestarter and allowed ports 80, 8080 and 8008 (all of which my apache server is listening for) for inbound traffic as I have seen recommended on this site. 
-My static IP is 192.168.2.121. 
--I am able to access the server using my IP and localhost on my ubuntu machine
-I have an untangled server up and running.
-I have a windows server running as well on port 192.168.2.190.
-I am UNABLE to access my ubuntu machine using mykel-ubuntu (name of the server) or 192.169.2.121 or 192.169.2.121:8080 or 192.169.2.121:8008 when used from another machine on my internal network (have tried from 3 different machines)
-I am able to access the internet on my ubuntu machine 
-I have used netstat -nlp and all ports listed above are listed as "Listening" as would be expected.

Not sure what else to do and have searched extensively to come up with a solution prior to posting - any help would be appreciated!

---

### Post by brent1975 on 2013-02-15
show us what your  /etc/network/interface looks like.

---

### Post by themykel on 2013-02-15
> **brent1975 said:**
> show us what your  /etc/network/interface looks like.

Thanks Brent!
```

#interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by lykwydchykyn on 2013-02-15
If the server isn't in any way available outside your network, what's the use of a firewall?  I would start by turning off your firewall and getting the services working first.

Also, how did you configure your static IP?  /etc/network/interfaces should have something about eth0 in it.  Did you install a GUI and configure it in network manager?

---

### Post by themykel on 2013-02-15
> **lykwydchykyn said:**
> If the server isn't in any way available outside your network, what's the use of a firewall?  I would start by turning off your firewall and getting the services working first.

Also, how did you configure your static IP?  /etc/network/interfaces should have something about eth0 in it.  Did you install a GUI and configure it in network manager?

I should have put that in - I have turned off the firewall with Firestarter and had no success. The static ip is done through my Untangled router recognizing the MAC of the server and assigning it 192.168.2.121 - I found that to be the most reliable way of making sure nothing else takes 121 :)

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> I am using Ubuntu 12.10 server x64 to run a SpotWeb for newsgroup access. However, I am unable to ping the IP of the ubuntu server within my network (although localhost is fine). I have searched the forums for a solution and have tried multiple but am unable to come up with something that works so hoping that someone can help!

Here is what I have done so far:

- I have done a fresh 12.10 install and setup Spotweb for my NZB needs (Sickbeard YAY!). 
-I have installed firestarter and allowed ports 80, 8080 and 8008 (all of which my apache server is listening for) for inbound traffic as I have seen recommended on this site. 
-My static IP is 192.168.2.121. 
--I am able to access the server using my IP and localhost on my ubuntu machine
-I have an untangled server up and running.
-I have a windows server running as well on port 192.168.2.190.
-I am UNABLE to access my ubuntu machine using mykel-ubuntu (name of the server) or 192.169.2.121 or 192.169.2.121:8080 or 192.169.2.121:8008 when used from another machine on my internal network (have tried from 3 different machines)
-I am able to access the internet on my ubuntu machine 
-I have used netstat -nlp and all ports listed above are listed as "Listening" as would be expected.

Not sure what else to do and have searched extensively to come up with a solution prior to posting - any help would be appreciated!


Your interface file should look like this
```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

		address 192.168.2.121
		netmask 255.255.255.0
		gateway 192.168.2.1
		network 192.168.2.0
		broadcast 192.168.2.255

		dns-nameservers 8.8.8.8 8.8.4.4
		dns-search google.com

```

Take in mind I set the DNS to google.com's dns servers. you can use them or change them to your ISP dns.

Once you have that done run ```
sudo /etc/init.d/networking restart
```
verify that your static IP has taken place with this command
```

sudo ifconfig eth0
```

Now verify that DNS is corrent
Use the cat command. Basically just shows you the contents of the file without having to open it. :)
```

cat /etc/resolv.conf
```

now check that you have internet connection with a simple
```

sudo apt-get update
```

If you have that firewall installed disable it.
for UFW
run this command to disable
```

sudo ufw disable
```

to verify that your firewall has been stoped run this command
```

sudo ufw status
```

If you want a firewall I would recommend using UFW.Its very simple to use and will get you more involved at whats going on in the background vs a client like firestarter. Nothing wrong with firestarter just if you want to know how things work you got to dig into the terminal and before long you will start asking questions about IPTABLES.. :)

First and for most you want to enable SSH on your server before you enable UFW or do anything else. Assuming UFW has been disabled at this point. 

This first command will reset the firewall removing any entries you have made.
```

sudo ufw --force reset

```

This will open up ssh on your server assuming you are using the default port 22
```

sudo ufw allow 22

```

Now enable your firewall. Except for ssh, which you allowed with the above rule, this will deny all incoming (udp/tcp) traffic to your server.
```

sudo ufw enable
sudo default deny

```

Now for adding your public server to be seen out on the net
```

sudo ufw allow 80

```
Or if you wish, by protocol and port (most servers will be tcp).
```

sudo ufw allow 80/tcp

```

This will get you started and you should be able to ssh to your server and see your default website.

---

### Post by themykel on 2013-02-16
Tried all of the above with no luck. I am posting on the machine right now so I am getting internet connection however I can not see the pc via ping from within my LAN, I am getting the reply that the desination host is unreachable :S

only change I did from above is made the assumption that sudo default deny should be sudo ufw default deny....

I also uninstalled firestarter to start using ufw :D

edit:
I am using PuTTY for my telnet session from a windows machine and unable to connect - I have done all of the steps and verified the output should be as you state - even left the DNS servers to be google instead of using my own ISPs dns servers (although those seem to work fine). I also use no-ip for dynamic dns forwarding (not currently setup on this machine - although my windows newznab is running fine). Kind of stumped which is why I am turning to this. I haven't worked with ubuntu for a few years so very rusty but still do most things with CLI :) I really appreciate the input I am getting here and am also researching for a solution online while waiting for replies here...

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> Tried all of the above with no luck. I am posting on the machine right now so I am getting internet connection however I can not see the pc via ping from within my LAN, I am getting the reply that the desination host is unreachable :S

only change I did from above is made the assumption that sudo default deny should be sudo ufw default deny....

I also uninstalled firestarter to start using ufw :D

edit:
I am using PuTTY for my telnet session from a windows machine and unable to connect - I have done all of the steps and verified the output should be as you state - even left the DNS servers to be google instead of using my own ISPs dns servers (although those seem to work fine). I also use no-ip for dynamic dns forwarding (not currently setup on this machine - although my windows newznab is running fine). Kind of stumped which is why I am turning to this. I haven't worked with ubuntu for a few years so very rusty but still do most things with CLI :) I really appreciate the input I am getting here and am also researching for a solution online while waiting for replies here...

I would totally disable the firewall till things are working proper.
Then test the connection over SSH. Also are you using IP or host name to connect to the server? if you are trying via host name try and use the IP.

Next go back into /etc/network/interfaces and change to dhcp just for testing purposes. 
reload the network with
```
sudo /etc/init.d/networking restart
```
you will have to check and see what the new ip is with
```
sudo ifconfig eth0
```
use that IP to try and ssh into your server.
also can you ping your windows box from the server?
```
 ping 192.168.2.x -c 4
```

Try using your router as the dns
change your dns settings to reflect your router

```
dns-nameservers 192.168.2.1
``` I am assuming your router IP is 2.1 from your IP scheme. 

Report back. :)

---

### Post by themykel on 2013-02-16
Using UFW is it UFW disable (as you had me do in the previous step)?

It is completely disabled:

> mykel@mykel-ubuntu:~$ sudo ufw status verbose
Status: inactive

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> Using UFW is it UFW disable (as you had me do in the previous step)?

It is completely disabled:

```
sudo ufw disable
```

Please verify if you are able to ping from the server to Desktop, Laptop, router.

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> ```
sudo ufw disable
```

disabled and not working - it worked for a second then went to re-enable ufw and it stopped working - disabled it again and cnat ping it 

> eth0      Link encap:Ethernet  HWaddr 00:0c:f1:ff:83:1e  
          inet addr:192.168.2.121  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:feff:831e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2373988 (2.3 MB)  TX bytes:540434 (540.4 KB)
          Interrupt:17 Memory:90100000-90120000 

mykel@mykel-ubuntu:~$ sudo ufw status
Status: inactive
mykel@mykel-ubuntu:~$ 


---

### Post by themykel on 2013-02-16
This bothers me and I wonder if it has something to do with it?

```
mykel@mykel-ubuntu:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.2.1
nameserver 127.0.1.1
search google.com example.com
mykel@mykel-ubuntu:~$ 


```

---

### Post by themykel on 2013-02-16
Completely at a loss - NO firewall is enabled. As I stated before this is a fresh install off of a formatted hard drive. Yes, I am pinging both the hostname and the ip address. I can ping out OK - just cant ping in. I have tried a cross over cable and still unable to see the pc. I can not PuTTY into it. UFW is disabled at startup.....no clue why this is going on!

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> disabled and not working - it worked for a second then went to re-enable ufw and it stopped working - disabled it again and cnat ping it

So you were able to ping the server for a second then enabled, then disabled and it stopped working? Sorry just making sure I am playing it correct in my head. If the ufw is disabled reboot the server  sudo reboot  or sudo reboot -n

Once back up check the ufw status

---

### Post by themykel on 2013-02-16
That is correct - it worked for just a second (was able to pull up the spotweb at 192.168.2.121/spotweb) and then re-enabled UFW and now I can't get it to work...

Currently rebooting server

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> This bothers me and I wonder if it has something to do with it?

```
mykel@mykel-ubuntu:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.2.1
nameserver 127.0.1.1
search google.com example.com
mykel@mykel-ubuntu:~$ 


```

actually the localhost should be 127.0.0.1 change it under /etc/hosts

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> No this is fine from a cat report The only thing I would get rid of is "example.com"  /etc/network/interfaces

example.com is not listed in my /etc/network/itnerfaces....or the 127.0.0.1.....

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> example.com is not listed in my /etc/network/itnerfaces....or the 127.0.0.1.....

actually the localhost should be 127.0.0.1 change it under ```
sudo nano /etc/hosts
```

should look like 
```

127.0.0.1       localhost
192.168.2.106   ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
These are my values of course.

---

### Post by themykel on 2013-02-16
this is my /etc/hosts

```
127.0.0.1       localhost
127.0.1.1       mykel-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
127.0.0.1       localhost.localdomain localhost ubuntu

```

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> this is my /etc/hosts

```
127.0.0.1       localhost
127.0.1.1       mykel-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
127.0.0.1       localhost.localdomain localhost ubuntu

```

```
127.0.1.1       mykel-ubuntu
```

needs to look like
```
192.168.2.121       mykel-ubuntu
```

also remove the very last line
```
127.0.0.1       localhost.localdomain localhost ubuntu
```

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> ```
127.0.1.1       mykel-ubuntu
```

needs to look like
```
192.168.2.121       mykel-ubuntu
```

also remove the very last line
```
127.0.0.1       localhost.localdomain localhost ubuntu
```

done - no change!GARRRR :)

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> done - no change!GARRRR :)

after you have made those changes you need to restart the networking.

```
sudo /etc/init.d/network restart
```

also check the UFW status again. verify that it is off.

```
sudo ufw status
```

---

### Post by themykel on 2013-02-16
yes, I did restart the network and UFW is disabled still

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> yes, I did restart the network and UFW is disabled still

Okay from the server use the browser and go to your site. error?

from another computer try it also..

you may also want to check your router and make sure that the IP is not in use still. reboot the router, reboot the server

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> Okay from the server use the browser and go to your site. error?

from another computer try it also..

you may also want to check your router and make sure that the IP is not in use still. reboot the router, reboot the server

IP is in use only by my ubuntu server - ip is still 192.168.2.121. on my server I am able to load up localhost/spotweb and 192.168.2.121/spotweb, unable to do so from any pc in the network other than the server

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> IP is in use only by my ubuntu server - ip is still 192.168.2.121. on my server I am able to load up localhost/spotweb and 192.168.2.121/spotweb, unable to do so from any pc in the network other than the server

Show your /etc/network/interfaces file sense you made changes.

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> Show your /etc/network/interfaces file sense you made changes.

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

                address 192.168.2.121
                netmask 255.255.255.0
                gateway 192.168.2.1
                network 192.168.2.0
                broadcast 192.168.2.255

                dns-nameservers 192.168.2.1
                dns-search google.com
```

---

### Post by brent1975 on 2013-02-16
run ```
sudo iptables -L
```

and show the results.

---

### Post by themykel on 2013-02-16
```
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination 
```

---

### Post by brent1975 on 2013-02-16
wow - run this ```
sudo ufw --force reset
```

and then show what the output of ```
sudo iptables -L
``` is

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> wow - run this ```
sudo ufw --force reset
```

and then show what the output of ```
sudo iptables -L
``` is

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination 
```

---

### Post by brent1975 on 2013-02-16
try ```
 sudo iptables -F
```

basically we are trying to remove all those entry's.

should look like
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by themykel on 2013-02-16
Did the following:

```
#!/bin/sh
sleep 10
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

then ran it and now get 

```
mykel@mykel-ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by brent1975 on 2013-02-16
Okay restart networking and try and ping the server from a different computer.

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> Okay restart networking and try and ping the server from a different computer.

negative ghost rider :S

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> negative ghost rider :S

reboot your server then test ping and websites. 
put your server on a DMZ on your router or better yet direct connect to the modem to eliminate the router as a cooperate. If you direct connect make sure you get the wan IP and you will want to go back into /etc/network/interfaces and change the nameservers to

```
dns-nameserver 8.8.8.8 8.8.4.4
```

---

### Post by themykel on 2013-02-16
ive somehow lost all connection (DHCP or Static) to the server now - it can't connect to the internet at all!!!! Frustrating...

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> ive somehow lost all connection (DHCP or Static) to the server now - it can't connect to the internet at all!!!! Frustrating...


reboot the server....

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> reboot the server....

thats when I lost it - did a full reboot

---

### Post by brent1975 on 2013-02-16
output of ```
 /etc/network/interfaces
```

UFW still disabled?  
```
sudo UFW status
```

check the tables

```
sudo iptables -L
```

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> output of ```
 /etc/network/interfaces
```

UFW still disabled?  
```
sudo UFW status
```

check the tables

```
sudo iptables -L
```
typing it manually since its no longer networked....

/etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 eth0 inet dynamic
``` (I just changed this from saying static while typing - didnt change anything about to change it to loopback like it was in my original configuration)

UFW status is inactive

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> typing it manually since its no longer networked....

/etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 eth0 inet dynamic
``` (I just changed this from saying static while typing - didnt change anything)

UFW status is inactive

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

change dynamic to dhcp
iface eth0 inet dhcp
and you had eth0 in there twice
then restart the networking /etc/init.d/network restart

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> typing it manually since its no longer networked....

/etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 eth0 inet dynamic
``` (I just changed this from saying static while typing - didnt change anything about to change it to loopback like it was in my original configuration)

UFW status is inactive

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

should look like this if you want to get dhcp back

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 eth0 inet dhcp

```

---

### Post by themykel on 2013-02-16
> **brent1975 said:**
> should look like this if you want to get dhcp back

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 eth0 inet dhcp

```

sigh - for some reason its not coming up anymore - screen just remains black - may have to start from scratch on this whole thing again! /facepalmx2

---

### Post by brent1975 on 2013-02-16
> **themykel said:**
> sigh - for some reason its not coming up anymore - screen just remains black - may have to start from scratch on this whole thing again! /facepalmx2

You still have eth0 in there twice remove one of them

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface [COLOR="Red"]eth0 eth0[/COLOR] inet dhcp

```

---

