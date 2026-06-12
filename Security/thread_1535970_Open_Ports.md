---
title: "Open Ports"
date: 2010-07-21
forum: Security
---

### Post by alan2796 on 2010-07-21
can someone help me, im trying to find any open ports on my machine and close them, so i run nmap on my external ip-address that a speed test website told me it was and the result i got was 

Not shown: 996 closed ports
PORT   STATE    SERVICE
21/tcp filtered ftp
22/tcp filtered ssh
23/tcp open     telnet
80/tcp open     http

does anyone know why these are open and how to close them ? or am i going about this the wrong way ?

---

### Post by The Cog on 2010-07-21
Either you have installed FTP, SSH, telnet and web services, or you scanned the wrong machine.

You can see what ports are open on your OS with the command
```
netstat -lntu
```

Is your PCs IP address (from the command **ifconfig**) different to the external IP address? If yes, then you would have been scanning your router, not your PC.

---

### Post by alan2796 on 2010-07-21
output of that is......

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:54916           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:* 

so what does what mean now ?

ifconfig does not give me a ip-address anywhere the same as, the one on the speedtest website so i must be scanning wrong machine.

---

### Post by Rubi1200 on 2010-07-21
The listening process with PID 631 is cups, used for printing; nothing to worry about there it is quite normal.
PID 5353 and PID 68 is _probably_ avahi.
You can also get more information by using:

```
sudo lsof -i -n -P
```You will find it is a handy command to run. Post the results here please

---

### Post by alan2796 on 2010-07-21
thanks guys, this is the ouput  is this normal and can i turn these things off and is there any benifit in doing so ?

```
alan@amg-laptop:/$ sudo lsof -i -n -P
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  513 avahi   13u  IPv4   3110      0t0  UDP *:5353 
avahi-dae  513 avahi   14u  IPv4   3111      0t0  UDP *:54916 
cupsd     1364  root    5u  IPv6  36863      0t0  TCP [::1]:631 (LISTEN)
cupsd     1364  root    6u  IPv4  36864      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  2383  root    5w  IPv4  15116      0t0  UDP *:68
```

---

### Post by anomie on 2010-07-21
[QUOTE=alan2796]... the result i got was 

Not shown: 996 closed ports
PORT   STATE    SERVICE
21/tcp filtered ftp
22/tcp filtered ssh
23/tcp open     telnet
80/tcp open     http[/QUOTE]

My WAG is you scanned the wrong host, *or* (perhaps more likely) your host is sitting behind a "home router" (NAT device), and that's what you actually scanned.

---

### Post by Rubi1200 on 2010-07-21
> **alan2796 said:**
> thanks guys, this is the ouput  is this normal and can i turn these things off and is there any benifit in doing so ?

alan@amg-laptop:/$ sudo lsof -i -n -P
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  513 avahi   13u  IPv4   3110      0t0  UDP *:5353 
avahi-dae  513 avahi   14u  IPv4   3111      0t0  UDP *:54916 
cupsd     1364  root    5u  IPv6  36863      0t0  TCP [::1]:631 (LISTEN)
cupsd     1364  root    6u  IPv4  36864      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  2383  root    5w  IPv4  15116      0t0  UDP *:68

Everything looks quite normal; nothing to be concerned about.

As anomie and The Cog already pointed out, you probably scanned your router.

---

### Post by alan2796 on 2010-07-21
yup i think so guys, so how would i find my actual ip address of this machine not the router ?

---

### Post by Telengard C64 on 2010-07-21
> **The Cog said:**
> Is your PCs IP address (from the command **ifconfig**) different to the external IP address?

You can use the command **ifconfig** to find the IP address of your computer.

---

### Post by cdenley on 2010-07-21
If you're behind a router, the actual IP of your computer is a LAN IP which cannot be accessed from the internet. Any traffic that reaches your computer from the internet must be routed through your router (hence the name). Unless you created "port forward" rules or a DMZ, only traffic from a connection you establish will be routed to your computer.

---

### Post by alan2796 on 2010-07-21
> **cdenley said:**
> If you're behind a router, the actual IP of your computer is a LAN IP which cannot be accessed from the internet. Any traffic that reaches your computer from the internet must be routed through your router (hence the name). Unless you created "port forward" rules or a DMZ, only traffic from a connection you establish will be routed to your computer.

so my router ip would be like xxx.xxx.xx.xx then 
192.168.1.3 is my LAN IP ? 

im still slightly confused, in that case a would be attacker couldn't port scan my laptop ?

---

### Post by Telengard C64 on 2010-07-21
Just think of your router as a device which connects two different IP networks, the LAN side and the WAN side. The router allows traffic to pass from the LAN to the WAN, but not the reverse.

Computers on the Internet (the WAN) can only see your router; nothing on your LAN is visible to the Internet. The only exception is when you configure your router to allow traffic to enter the LAN through a specific port.

HTH

---

### Post by cdenley on 2010-07-21
> **alan2796 said:**
> so my router ip would be like xxx.xxx.xx.xx then 
192.168.1.3 is my LAN IP ? 

im still slightly confused, in that case a would be attacker couldn't port scan my laptop ?

No. Not unless they had access to your LAN. One of the benefits of using a router. They could only port scan the device with a WAN IP (your router).

---

### Post by alan2796 on 2010-07-21
does that mean unless i run some server like program or something else my machine is pretty secure ?

---

### Post by endotherm on 2010-07-21
> **alan2796 said:**
> so my router ip would be like xxx.xxx.xx.xx then 
192.168.1.3 is my LAN IP ? 

im still slightly confused, in that case a would be attacker couldn't port scan my laptop ?
not easily, but you still want to close or limit internal ports, just in case. there are ways to trick state-full firewalls, and malicious code running inside your network might end up with carte blanche to control your network services. not essential, but a good depth of defense strategy can not only make sure that villians can't get in, but also that if they do get in, their ability to hurt you is as minimal as you can make it.

---

### Post by cdenley on 2010-07-21
> **alan2796 said:**
> does that mean unless i run some server like program or something else my machine is pretty secure ?

Router or no router, unless you run some server software, your machine is pretty secure. The router adds yet another layer of protection, though. Even if you ran server software for some reason, unless your router is configured to forward traffic to it or an attacker manages to bypass it somehow, you are still safe from external threats.

---

### Post by Telengard C64 on 2010-07-21
I have created a diagram which I hope will clear things up a bit. Comments and constructive criticism welcome.

[http://yfrog.com/0urouterv2p](http://yfrog.com/0urouterv2p)

[source code (Gimp)](http://sharebee.com/60410b28)


**_Edit_**

Version 2: remove "class C" text and point out address translation

See [_this article on GRC_](http://www.grc.com/nat/nat.htm) for a detailed discussion of NAT on home routers.

---

### Post by endotherm on 2010-07-21
not a bad diagram. if you ever find the time and the space, add a solicited nat connection as well.

---

### Post by Telengard C64 on 2010-07-21
> **endotherm said:**
> not a bad diagram. if you ever find the time and the space, add a solicited nat connection as well.

I thought about that, but considering the target audience it seemed a bit too much. All of these topics are explained in great detail in the college classes I took, but there's no way I could reproduce all that in a simple diagram or forum post.

BTW, the image is intended to be Free and Open Source even though I didn't attach any particular license to it. Please feel free to add anything you feel would make it better.

**_Edit_**

Here is a link to the source XCF I made in Gimp. Use it if you like to make a better diagram.

[http://sharebee.com/545e56dd](http://sharebee.com/545e56dd)

Not sure that one took, so here are some more just in case.

[http://sharebee.com/717b05bf](http://sharebee.com/717b05bf)
[http://www.megaupload.com/?d=HCMZ3PXM](http://www.megaupload.com/?d=HCMZ3PXM)

---

### Post by alan2796 on 2010-07-22
thanks all, for taking time to explain,the diagram is helpful !

---

### Post by The Cog on 2010-07-22
Just expanding a couple of points:

If you don't install server programs on your PC then nothing can connect to it. Any attempt to connect would get a "Connection refused" response. If (for example) you installed a web server that listens on port 80, then the OS will begin accepting calls to port 80 and passing them on to the web server. Stop the web service and port 80 refuses incoming calls again.

192.168.x.x is a private address space. You can use it on your own network but these addresses cannot be reached over the internet. You probably have several 192.168 addresses in your house, your PC and your router for instance. Your ISP will allocate just one IP address for you to use when talking over the internet and it will NOT be in that 192.168.x.x address range. Your router performs address translation for all outgoing connections so that from the internet's point of view, the connections all come from that router's public address. And of course, the router passes all the responses back to the right address internally. 

That's OK for outgoing connections - the router knows which internal PC started the connection. But what about incoming connection requests? Which of the hundreds of possible 192.168 addresses should the connection be passed through to? That's where you have to configure the router explicitly, saying that if you get an incoming call for (say) port 80 from the internet, it should be passed through to (say) PC 192.168.1.5. And you can choose to forward calls to different port numbers to different internal machines, so you can run different services, such as Web (80) and mail (25) on different machines. Without this explicit "port forwarding" configuration, the router doesn't know whereto connect incoming calls to, and therefore simply refuses all incoming connections from the internet. So an address translating router acts rather like a firewall, allowing outgoing connections but refusing all incoming connections.

---

### Post by Telengard C64 on 2010-07-22
It looks like I made an error in [_the diagram_](http://yfrog.com/hqrouterzp). I described the WAN side address as "class C", but that can't be correct. (Dunno what I was thinking.)

I'm thinking I should make it say "class A address" but is that actually the most common case for home routers/gateways? FWIW my own external address appears to be class A.

---

### Post by endotherm on 2010-07-22
> **Telengard C64 said:**
> It looks like I made an error in [_the diagram_]("http://yfrog.com/hqrouterzp"). I described the WAN side address as "class C", but that can't be correct. (Dunno what I was thinking.)

I'm thinking I should make it say "class A address" but is that actually the most common case for home routers/gateways? FWIW my own external address appears to be class A.
isp addresses run the full gamut thanks to route aggregation techniques like supernetting. my ISP usually uses ClassA addresses for subscribers, but many of their internal systems are class B. heck, thanks to nat, many smaller ISPs can run large numbers of clients on a single classC.

probably best to just refer to it as the ISP network, or the public network.

---

### Post by Telengard C64 on 2010-07-22
Just shows how I've allowed my knowledge to go stale. Use it or lose it, bros.  ;)

> **endotherm said:**
> probably best to just refer to it as the ISP network, or the public network.

Done. Also pointed out where address translation takes place.

---

### Post by yurfader on 2010-07-23
I ran netstat -lntu and i got 
> 
Conexiones activas de Internet (solo servidores)
Protocolo Recv-Q Send-Q Dirección Local Dirección Externa Estado      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN   
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN   
tcp        0      0 127.0.0.1:2628          0.0.0.0:*               LISTEN   
tcp6       0      0 ::1:631                 :::*                    LISTEN   
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:45822           0.0.0.0:*                          


I do not have any server only the DSL conexion, should I worry about the 2628 conexion?

---

### Post by cdenley on 2010-07-23
> **yurfader said:**
> I ran netstat -lntu and i got 


I do not have any server only the DSL conexion, should I worry about the 2628 conexion?

If you don't even know what it is, then you should worry. Either something is there listening for connections that shouldn't be, or you installed software without knowing what it does. That appears to be listening on 127.0.0.1, though, so no remote connections.
```

sudo netstat -tulnp

```

---

### Post by endotherm on 2010-07-23
> **yurfader said:**
> I ran netstat -lntu and i got 


I do not have any server only the DSL conexion, should I worry about the 2628 conexion?
no, that port is only listening for connections from the localhost (127.0.0.1) so people on other users can't access it. 
your other ports look mostly fine. are you really running a mailserver though? 

631 is cups. you should block it if it comes from any network other than yourown
same with 68 and 5353. not sure what the others are, but you may be able to find out with
```
**sudo netstat -plantu**
```

---

### Post by yurfader on 2010-07-23
I am only running my regular desktop with the DSL connected to the internet and this is the result of sudo netstat -plant

> 
Conexiones activas de Internet (servidores y establecidos)
Protocolo Recv-Q Send-Q Dirección Local Dirección Externa Estado       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               ESCUCHAR    1390/cupsd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               ESCUCHAR    1286/master     
tcp        0      0 127.0.0.1:2628          0.0.0.0:*               ESCUCHAR    1149/0          
tcp        0      0 10.0.0.2:42132          74.125.47.102:80        ESTABLECIDO 1771/firefox-bin
tcp        0      0 10.0.0.2:46062          74.125.166.153:80       ESTABLECIDO 1771/firefox-bin
tcp        0      0 10.0.0.2:39067          74.125.67.139:80        ESTABLECIDO 1771/firefox-bin
tcp6       0      0 ::1:631                 :::*                    ESCUCHAR    1390/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1251/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           787/avahi-daemon: r
udp        0      0 0.0.0.0:45822           0.0.0.0:*                           787/avahi-daemon: r
I do not know much about networking and I think that I have some a maliscious software installed on my PC when it starts it gives a warnig that skips the apprmor configuration for firefox.

I apppreciate your help

---

### Post by Rubi1200 on 2010-07-23
> **yurfader said:**
> I do not know much about networking and I think that I have some a maliscious software installed on my PC when it starts it gives a warnig that skips the apprmor configuration for firefox.

The AppArmor profile for Firefox is disabled by default. The message you see is quite normal.

See here for more information:

[https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?](https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?)

Unless you know what you are doing it might be best to leave the settings at their default level. Ubuntu is quite secure "out of the box."

---

### Post by cdenley on 2010-07-23
```

sudo ps -f -p 1149
sudo lsof -n -p 1149

```

---

### Post by yurfader on 2010-07-23
Here is the result of sudo ps -f -p 1149

> 
UID        PID  PPID  C STIME TTY          TIME CMD
dictd     1149     1  0 11:26 ?        00:00:00 dictd 1.11.2: 0/0
and of sudo lsof -n -p 1149

> 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dictd   1149 dictd  cwd    DIR    8,5     4096       2 /
dictd   1149 dictd  rtd    DIR    8,5     4096       2 /
dictd   1149 dictd  txt    REG    8,5   154988 3681307 /usr/sbin/dictd
dictd   1149 dictd  mem    REG    8,5    34408 3539073 /lib/tls/i686/cmov/libnss_nis-2.11.1.so
dictd   1149 dictd  mem    REG    8,5   113964 3539137 /lib/ld-2.11.1.so
dictd   1149 dictd  mem    REG    8,5    79676 3539057 /lib/tls/i686/cmov/libnsl-2.11.1.so
dictd   1149 dictd  mem    REG    8,5    30496 3539059 /lib/tls/i686/cmov/libnss_compat-2.11.1.so
dictd   1149 dictd  mem    REG    8,5    42572 3539063 /lib/tls/i686/cmov/libnss_files-2.11.1.so
dictd   1149 dictd  mem    REG    8,5   149392 3539046 /lib/tls/i686/cmov/libm-2.11.1.so
dictd   1149 dictd  mem    REG    8,5     9736 3539009 /lib/tls/i686/cmov/libdl-2.11.1.so
dictd   1149 dictd  mem    REG    8,5  1405508 3538995 /lib/tls/i686/cmov/libc-2.11.1.so
dictd   1149 dictd  mem    REG    8,5    79512 3539150 /lib/libz.so.1.2.3.3
dictd   1149 dictd  mem    REG    8,5    80460 3676145 /usr/lib/libmaa.so.2.0.0
dictd   1149 dictd  mem    REG    8,5    85678 3962610 /usr/share/dictd/freedict-eng-spa.dict.dz
dictd   1149 dictd  mem    REG    8,5    86023 3962611 /usr/share/dictd/freedict-eng-spa.index
dictd   1149 dictd  mem    REG    8,5 10757105 3962616 /usr/share/dictd/moby-thesaurus.dict.dz
dictd   1149 dictd  mem    REG    8,5   540892 3962617 /usr/share/dictd/moby-thesaurus.index
dictd   1149 dictd  mem    REG    8,5    53923 3962612 /usr/share/dictd/freedict-spa-eng.dict.dz
dictd   1149 dictd  mem    REG    8,5 13527748 3962614 /usr/share/dictd/gcide.dict.dz
dictd   1149 dictd  mem    REG    8,5  3952339 3962615 /usr/share/dictd/gcide.index
dictd   1149 dictd  mem    REG    8,5    68254 3962613 /usr/share/dictd/freedict-spa-eng.index
dictd   1149 dictd    0u   CHR    1,3      0t0    1262 /dev/null
dictd   1149 dictd    1u   CHR    1,3      0t0    1262 /dev/null
dictd   1149 dictd    2u   CHR    1,3      0t0    1262 /dev/null
dictd   1149 dictd    3r   REG    8,5  3952339 3962615 /usr/share/dictd/gcide.index
dictd   1149 dictd    4r   REG    8,5     1386  524978 /var/lib/dictd/db.list
dictd   1149 dictd    5u   CHR    1,3      0t0    1262 /dev/null
dictd   1149 dictd    6r   REG    8,5 13527748 3962614 /usr/share/dictd/gcide.dict.dz
dictd   1149 dictd    7r   REG    8,5    68254 3962613 /usr/share/dictd/freedict-spa-eng.index
dictd   1149 dictd    8r   REG    8,5    53923 3962612 /usr/share/dictd/freedict-spa-eng.dict.dz
dictd   1149 dictd    9r   REG    8,5   540892 3962617 /usr/share/dictd/moby-thesaurus.index
dictd   1149 dictd   10r   REG    8,5 10757105 3962616 /usr/share/dictd/moby-thesaurus.dict.dz
dictd   1149 dictd   11r   REG    8,5    86023 3962611 /usr/share/dictd/freedict-eng-spa.index
dictd   1149 dictd   12r   REG    8,5    85678 3962610 /usr/share/dictd/freedict-eng-spa.dict.dz
dictd   1149 dictd   13u  IPv4   5111      0t0     TCP 127.0.0.1:dict (LISTEN)

I am worried because before the lucid version, when I tried to turn off the PC it appeared a message asking me if I wanted to disconnect a user and it requested the password in order to turn off the PC. It didn't happened all the time but maybe 2 or 3 times, and I did not change any out of the box configuration. The only thing that i did was to activate the firewall.

---

### Post by cdenley on 2010-07-23
That listening process was dictd.
```

sudo dpkg -l dictd

```

As far as that message when shutting down, there must have been another user session running.
```

w

```

---

### Post by yurfader on 2010-07-23
Thanks, just in case i installed IPBlock, and I am going to continue reading about this topics.

---

