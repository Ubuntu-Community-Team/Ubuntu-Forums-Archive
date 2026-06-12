---
title: "Ubuntu 16.04 LTS  Am I missing something?"
date: 2016-06-27
forum: Server Platforms
---

### Post by paul212 on 2016-06-27
I am bring a new Ubuntu 16.04 LTS SFTP server online.  I currently have it in a testing network. I can SSH into the new server in the test network.  Now I did the same thing when I went from 12.04 LTS to 14.04 LTS.  I edited my network interface and put in the production ip address.  Unplugged the old server's network cable and plugged it into the new server and it was up and running.  Now I am doing the same thing.  Editing the interface putting in the production ip address in the new 16.04 LTS server just as it is in the old 14.04 LTS and shutting down the new 16.04 LTS server.  Unplugging the network cable from the old 14.04 LTS server and plugging it into the new 16.04 LTS server.  Turning on the new 16.04 server and I cannot SSH into the new 16.04 LTS server. I cannot SFTP into the new 16.04 LTS server.  What the hell am I missing?   This process worked perfectly when I went from 12.04 LTS to 14.04 LTS.  
Any help with be much appreciated. 
Thank you

---

### Post by MAFoElffen on 2016-06-27
Can you ping to it from another net node?

Is the results of
```

ifconfig -a

```
Is the results of, what you expected? Starting with 15.10 through 16.04... some of the net device names did seem to have changed, so what was previously ethX, shows the same on mine as an upgrade, but when I do a clean install on the same server hardware, it showed up as being different.

So... with the above, if you temporarily set ports to dhcp, then do an ifconfig to see what it comes up with,m that will show you if there are diffrences.

If that was all-good, next to do is to ensure that openssh-server is installed and that it is listening on port 22:
```

sudo systemctl status sshd.service
sudo netstat -plnt | grep ':22'

```
If not running, then correct the service. If running but not showing through, then check why the installation of didn't open the port in UFW.

---

### Post by paul212 on 2016-06-27
MAFoElffen Thank for the reply 
     When the new 16.04 LTS is on my local network  192.168.150.7  I can ping, I can SSH into it no problems.  But I change the interface from:
```
#The primary network interfaces
auto eno1
iface eno1 inet static
address 192.168.150.7
netmask 255.255.255.0
network 192.168.150.0
broadcast 192.168,150.255
gateway 192.168.150.1
dns-nameserver 192.168.150.36

```
Change to Production server address that is currently working : 

```
#The primary network interfaces
auto eno1
iface eno1 inet static
address 192.168.155.10
netmask 255.255.255.0
network 192.168.155.10
broadcast 192.168,155.255
gateway 192.168.155.1
dns-nameserver  this is the ip address of my internet service provider

```
The only difference between current working production configuration and new server is the name of the Ethernet port.
Old server eth0    New server eno1  
I do not change that on the new server. It stays at the eno1.
Again unplug the network cable from old server and plug in the new server and nothing unable to ping, unable to SSH, unable SFTP. It is like it is not there. 
Why?

---

### Post by MAFoElffen on 2016-06-27
Please go back to your last post and put your output between code tags. (Advanced Edit > Hightlight the text > Select the "#" icon)

Here's your problem:
```

address [COLOR=#ff0000]192.168.155.10
[/COLOR]...
network [COLOR=#ff0000]192.168.155.10
[/COLOR]...

```
you put your network ID (NID) the same as your node IP address.

It should be more like: 
```

#The primary network interfaces
auto eno1
iface eno1 inet static
address 192.168.155.10
netmask 255.255.255.0
network [COLOR=#ff0000]192.168.155.0[/COLOR]
broadcast 192.168,155.255
gateway 192.168.155.1
dns-nameserver xxx.xxx.xxx.xxx

```

---

