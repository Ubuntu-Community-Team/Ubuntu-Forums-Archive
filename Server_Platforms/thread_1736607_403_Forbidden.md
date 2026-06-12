---
title: "403 Forbidden"
date: 2011-04-22
forum: Server Platforms
---

### Post by AngryGrapes on 2011-04-22
Hello, I am attempting to set up a server on ubuntu server (newest version) and I am running into some issues. When I try to access the site locally i get 403 Forbidden you do not have access to index.html. From browsing other threads around here it seems to be a permissions error i'm guessing that other users don't have permissions to execute the files. But the suggestions I found about similar things did not seem to fix my problem. Also when trying to access the site from outside the network im getting page doesn't exist both from my noip.com address and ip address. But that's a different problem altogether i'm guessing. Any help on this issue would be greatly appreciated.


update: it seems like if i do chmod 777 to each individual file within the directory it works. I tried doing it to the folder itself earlier but it seems it doesnt make the whole thing and i have to do it to each file. This will be tedious work if i have to go through this for each one. What is the command to set it for the entire thing and all its subfolders?

---

### Post by Joe of loath on 2011-04-22
You will want chmod -R 655 /path/to/directory

777 is a security risk, it means anyone can access it.

---

### Post by bmathis on 2011-04-22
If everything is in your web directory (default is /var/www) then you need to give apache2 (assuming) ownership of the files you just uploaded. 

> sudo chown -R www-data:www-data /var/www

chown changes the ownership, -R means recursive (will run the same command on all files and folders in the root of the folder you specify), www-data is the default user/group for apache2, and /var/www is the folder.

---

### Post by AngryGrapes on 2011-04-22
So i'm guessing i should undo the chmod 777 and do 

```
sudo chown -R www-data:www-data /var/www
```

How exactly would I undo the 777 so my files arent at risk? Does giving apache ownership of the files overwrite it?

---

### Post by Mosabama on 2011-04-22
> **AngryGrapes said:**
> So i'm guessing i should undo the chmod 777 and do 

```
sudo chown -R www-data:www-data /var/www
```

How exactly would I undo the 777 so my files arent at risk? Does giving apache ownership of the files overwrite it?

You cannot undo .. you can do this:

```

sudo chmod -R 644 /var/www/*

```

and add x to directories inside /var/www if there is any so you can navigate normally:

```
sudo chmod uo+x directoryname 
```

---

### Post by AngryGrapes on 2011-04-22
Thanks for all the advice everything seems to be working properly now. Im just till having the issue of only being able to access the site locally. Any attempts to access the page outside shows page not found. I set up a noip address (on a seperate comp with the same public ip) that i can works internally but not externally if that makes any kind of difference.
The only thing i really did on the server was setup my /etc/network/interfaces: to static based on what the ubuntu documentation website said.

---

### Post by Mosabama on 2011-04-22
> **AngryGrapes said:**
> Thanks for all the advice everything seems to be working properly now. Im just till having the issue of only being able to access the site locally. Any attempts to access the page outside shows page not found. I set up a noip address (on a seperate comp with the same public ip) that i can works internally but not externally if that makes any kind of difference.
The only thing i really did on the server was setup my /etc/network/interfaces: to static based on what the ubuntu documentation website said.

do you mean from outside the lan?
did you do port redirection in your router settings? you have to make it that if your router receives a port 80 request "which is http" to redirect the request to the server.

---

### Post by AngryGrapes on 2011-04-22
Yeah, nobody outside my network can access the site. I have port forwarding open for 80 to my servers ip. (port range forwarding from 80 to 80 protocol:both,  ip: servers ip). Could it be that because i have DMZ enabled and the dmz host ip address is different from my servers ip that it is overriding that?

---

### Post by Mosabama on 2011-04-22
I dont know much about that.
but, did you "yourself" tried to access you server from outside? 
what I want to say that if you try to do that by your host name taken from a dynamic IP service. and from inside your network you typed your address or hostname "the public one - like you.dyndns.org for example" it may not work because some routers will reject this loop .. just like my router. "I cried until I knew the problem"

I just wanted to make sure that you physically went out side of your network and tried accessing it. or at least ask some one to do that and tell you the result.

---

### Post by AngryGrapes on 2011-04-22
Every time it was tested, I asked a friend who is outside the network to do it. Page not found was the result every time.

---

### Post by bmathis on 2011-04-22
Who is your ISP? 

If you opened port 80 on your router and pointed it to your web server which also has the port open (assuming a firewall is active on the server), then its possible that your ISP is one of the many that block port 80.

---

### Post by usatonycuba on 2011-04-23
Dump to my next post.. ;)

---

### Post by AngryGrapes on 2011-04-23
Im using Optimum online. I'm thinking it isn't that tho. None of the ports I try to forward are working. I mean I know i'm doing it correctly, it's not rocket science. Canyouseeme just always says connection refused. Theres exceptions on the firewall of the machine im on at the moment that im checking the status from. I've even tried shutting the firewall completely off but to no avail, no ports that I have forwarded are said to be open. I do have DMZ on which im not quite clear on what it is but it seems to be that it opens all ports so they should even all be open forwarded or not.

---

### Post by usatonycuba on 2011-04-23
> **AngryGrapes said:**
> internally but not externally if that makes any kind of difference.
The only thing i really did on the server was setup my /etc/network/interfaces: to static based on what the ubuntu documentation website said.
Note: always, before making changes to some file, you must first create a backup..!! .... 

Try:

 ```
nano /etc/network/interfaces
```

make sure that:
```
# The loopback network interface
auto lo
iface lo inet loopback
```
and :

```
[COLOR="DarkRed"]# The primary network interface[/COLOR]
auto eth0
iface eth0 inet [COLOR="DarkRed"]static[/COLOR]
```

also in the [COLOR="DarkRed"]# The primary network interface[/COLOR].. your router values are set correctly... ie
```
# The primary network interface
auto eth0
iface eth0 inet static
        [COLOR="DarkRed"]address[/COLOR] 192.168.0.100
        [COLOR="DarkRed"]netmask[/COLOR] 255.255.255.0
        [COLOR="DarkRed"]network[/COLOR] 192.168.0.0
        [COLOR="DarkRed"]broadcast [/COLOR]192.168.0.255
        [COLOR="DarkRed"]gateway[/COLOR] 192.168.0.1
```

always after any change on your networking conf files, do..
```
/etc/init.d/networking restart 
```

can you .. please c/p your /etc/hosts here..?

---

### Post by AngryGrapes on 2011-04-23
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#The loopback network interface
auto lo 
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
       address 192.168.1.100
       netmask 255.255.255.0
       gateway 192.168.1.1
       broadcast 192.168.1.255
       network 192.168.1.0

```

things seem to be changing a lot here, i guess you wanted hosts.

```

127.0.0.1       localhost
127.0.1.1       ubuntuserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by usatonycuba on 2011-04-23
Note: always, before making changes to some file, you must first create a backup..!! .... 

at your /etc/hosts  try this:

```

127.0.0.1       localhost.localdomain   localhost
192.168.0.100       ubuntuserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


restart host services

One of my  FQDN looks like this:
```

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   virtualmachine_example.com     virtualmachine_example

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

	   
```

---

### Post by AngryGrapes on 2011-04-23
I made all the suggested changes. Still no access from outside the network (Page not found). Also I think from one of the earlier permission changes now when i try to access the site internally from my noip address or external ip, it says my router wants me to sign in. Also my ports are still not forwarding despite my efforts.

---

### Post by usatonycuba on 2011-04-23
@AngryGrapes ... there is just a conf problem.. Do not despair ;)
Note: that I use as an example a FQDN  (virtualmachine_example.com)...This is the sequence I follow to a case like this:
```

 nano /etc/network/interfaces

``````


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```
Where the above values, mach exactly the router configuration... then
```

 /etc/init.d/networking restart 

```
```

 nano /etc/hosts
 
```

```

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   virtualmachine_example.com     virtualmachine_example

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
```

 echo virtualmachine_example.com > /etc/hostname 

```
```

 /etc/init.d/hostname restart 

```
```

 hostname 

```
```

 hostname -f 
 
```

> **AngryGrapes said:**
>  Also I think from one of the earlier permission changes now when i try to access the site internally from my noip address or external ip, it says my router wants me to sign in. Also my ports are still not forwarding despite my efforts.
You can try to reset your router to original settings/values, and configure your server to listen to  those values..?

---

### Post by AngryGrapes on 2011-04-23
IP Address: 	 192.168.1.1	 	 
Subnet Mask: 	 255.255.255.0	 	 
DHCP Server: 	 Enabled	 	 
Start IP Address: 	 192.168.1.100 	 	 
End IP Address: 	 192.168.1.149

These are the settings I see in my router. Some of the other values that aren't there iv'e just been following what others have put. Thats probably a problem there but I don't know where to find the other values.

---

### Post by usatonycuba on 2011-04-23
> **AngryGrapes said:**
> IP Address: 	 192.168.1.1	 	 
Subnet Mask: 	 255.255.255.0	 	 
DHCP Server: 	 Enabled	 	 
Start IP Address: 	 192.168.1.100 	 	 
End IP Address: 	 192.168.1.149

These are the settings I see in my router. Some of the other values that aren't there iv'e just been following what others have put. Thats probably a problem there but I don't know where to find the other values.
what is your router name and version

---

### Post by AngryGrapes on 2011-04-23
Linksys wrt54g v4

---

### Post by usatonycuba on 2011-04-23
> **AngryGrapes said:**
> IP Address: 	 192.168.1.1	 	 
Subnet Mask: 	 255.255.255.0	 	 
DHCP Server: 	 Enabled	 	 
Start IP Address: 	 192.168.1.100 	 	 
End IP Address: 	 192.168.1.149

These are the settings I see in my router. Some of the other values that aren't there iv'e just been following what others have put. Thats probably a problem there but I don't know where to find the other values.
> **AngryGrapes said:**
> Linksys wrt54g v4
Type [http://192.168.1.1](http://192.168.1.1) , In the Control Panel, go to VLANs and take a look of the values there

---

### Post by AngryGrapes on 2011-04-23
There is no VLANs section or things that looked similar.

---

### Post by Mosabama on 2011-04-23
> **AngryGrapes said:**
> There is no VLANs section or things that looked similar.

I am kinda sure that there is something wrong with you router configurations. cause as I can see you computer configurations are fine.

if there is no Vlan section whats the name of the section that you configured the router to redirect port 80 requests to your server?

and can you mention the router configurations?

anyway if all of this fail, can you try to make the the router DHCP to assign the ip address to your computer? "by using MAC address". I know this doesnt have anything to do but MAYBE it would solve the problem.

---

### Post by AngryGrapes on 2011-04-23
If i'm understanding correctly the section I used to redirect port 80 requests to my server was just called port range forwarding. I forwarded port 80 to my servers ip address for both tcp and udp.

Which configurations would you like me to post?

I'm beginning to think the issue is my modem (motorola surfboard). According to some sites it has a similar page to my router and I will prob have to forward the ports on that thing too. The thing is I don't know how to access it behind my router because 192.168.1.1 brings me to my router page and it seems people are using that for the modem too. Is there a seperate IP I can look for to connect to my modem?

---

### Post by mn_bat on 2011-05-01
hi, how to solve ERROR 403: Forbidden. when i download something, i got that error in ubuntu11.04. pls help me :cry:

---

### Post by lisati on 2011-05-01
192.168.1.1 is a network address local to your own network.

[LIST=1]
[*]Is anyone on your local (home) network able to access your web site and get *anything* (even a 403) from your website?
[*]Do you have a dynamic IP address which could have changed and thus confounding efforts to access your website from outside?
[/LIST]

---

