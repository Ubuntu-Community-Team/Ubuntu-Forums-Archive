---
title: "Ubuntu 14.04.2 Cannot access server from external network."
date: 2015-06-02
forum: Server Platforms
---

### Post by Toomas_Hide on 2015-06-02
Hello everyone. I have decided to learn how to set up and configure an ubuntu server, so that means I am a complete novice, so please bear with me.
I have installed the server on my spare laptop. I thought it would be a neat idea to create a portable development server I could take to programming events because the internet access there is usually of questionable quality. Is that even a good Idea? I seriously don't know :).

Anyhow, I cannot seem to access my server from an external network. Only locally. I have installed openssh and nginx on it and I have assured they are up and running..
```
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2664 (2.6 KB)  TX bytes:2664 (2.6 KB)


p2p1      Link encap:Ethernet  HWaddr d4:be:d9:48:c9:3a  
          inet addr:192.168.7.167  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::d6be:d9ff:fe48:c93a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1219183 (1.2 MB)  TX bytes:24966 (24.9 KB)
```


```
sudo ufw status
Status: inactive
```


```
sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.7.1     0.0.0.0         UG    0      0        0 p2p1
192.168.7.0     *               255.255.255.0   U     0      0        0 p2p1
```


```
sudo netstat -taupen
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      0          13270       707/vsftpd      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          10014       998/sshd        
tcp        0      0 0.0.0.0:8002            0.0.0.0:*               LISTEN      0          14241       1526/nginx      
tcp        0      0 192.168.7.167:22        192.168.7.114:54020     ESTABLISHED 0          14654       1793/sshd: toomas [
tcp6       0      0 :::22                   :::*                    LISTEN      0          10016       998/sshd        
tcp6       0      0 :::8002                 :::*                    LISTEN      0          14242       1526/nginx
```   

I have configured nginx to use port 8002 because port 80 was already in use on my local network.

I hope that the information I provided is sufficient to get started :)
Thank you in advance,
Toomas

---

### Post by darkod on 2015-06-02
To be able to reach services on your server from the outside, you need to configure port forwarding on the router which is between your outside and local network. Forward the wanted ports (and only those), and then you can reach the services using the public (outside) IP of the router and the port number.

---

### Post by TheFu on 2015-06-02
Is it a good idea?  Depends on the event. If you are at Linux or Defcon events, no, it is NOT a good idea. Not having any firewall rules is a poor idea too.

To get more detailed help, please help us help you by using "code tags" so things line up. You can edit the 1st post in this thread.

And darkod is correct.  If your internet connection is behind a router (very common in homes and I've never seen a business that wasn't), then any ports/services you want available from the internet will need to be forwarded to the server on the LAN.  There's a website that is full of how-to forward ports for hundreds of different routers.  Your "server" must have a static IP on the private LAN, so the forwarded port can go to the same place all the time.

---

### Post by Toomas_Hide on 2015-06-03
Thank you for the quick and informative reply. I will see what I can do with the routers port forwarding settings.

---

### Post by rhandy2 on 2015-06-04
If you want remote access to your machine you should forward ports to him. but be careful, you should enable ufw firewall and configure open ports you want. read here [https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html).

Change the default pot of ssh server, default is 22. harden your ssh server, read here [http://askubuntu.com/questions/2271/how-to-harden-an-ssh-server](http://askubuntu.com/questions/2271/how-to-harden-an-ssh-server).

Install fail2ban. [https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)


i´m a begginer like you, but is a long way to the top if you want some secure.

---

