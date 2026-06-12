---
title: "Need help with counter-strike dedicated server (HLDS)"
date: 2010-05-22
forum: Server Platforms
---

### Post by TheShader on 2010-05-22
Hello, I'm a newbie and have a little knowledge about networking and servers. And I'm trying to learn. I've installed Ubuntu server 10.04 to an old pc in my house. I have a static IP and I could configure LAMP, openssh and deluge command line torrent daemon without any problems. Now I'm trying to install Half Life dedicated server to run a Counter-Strike server.

I could get the HLDS to run on the local network. I can connect to the server from a client on the network. However I couldn't get the server to the outside internet. I've forwarded the ports on the router(DRG A226G) as follows(There was a preset in the router cfg for HLDS):
TCP Any -> 27020-27039
UDP Any -> 1200
UDP Any -> 27000-27015

I guess I have to open the ports on the server too, right? The only info I could get about it is [here]("http://server.counter-strike.net/server.php?cmd=howto&show=linux#router"). But that has some kind of old school ip configuration, ipmasqadm as far as I can understand.

So what should I do, please enlighten me :)

---

### Post by jerome1232 on 2010-05-22
Unless you explicitly set up Ubuntu's firewall to drop or reject connections, then when the server is running those ports should be open. Also if your able to reach the server from within your lan than the ports are open.

Are you trying to connect to the server via the public address from within your lan? I ask because some routers are unable to do that, I know mine isn't. It's also possible that your isp filters ports, if this is the case you'd have to call them and try to get them unfiltered.

I like to use a website to scan ports and let me know if they are open to the outside world. This is the one I use, you may want to find one that will scan udp ports though.

[http://www.t1shopper.com/tools/port-scan/](http://www.t1shopper.com/tools/port-scan/)

---

### Post by TheShader on 2010-05-22
thanks for your reply, I checked from the site you posted. It responds to the port 80 when the server is turned on. But it doesn't respond to the 27015 port which CS uses when I run the server.

So what should I do now? This means the problem is not because of the router preventing a local client connecting via a public IP? Should I try different ports?

---

### Post by jerome1232 on 2010-05-22
There are a couple things that could be happening.


I would try puting the computer in dmz+ mode, basically if you go into your router and do that it forwards all traffic it gets to the server. This will rule out any port forwarding issues.

If it doesn't work in dmz+ mode than your isp is filtering ports or the server isn't configured to listen to requests from the internet. I can't really help with either you'd have to take the first one up with your isp and the second one you can probably figure out by looking at the documentation that should come with the hlds.

If it works in dmz+ mode than there is an issue with the port forwarding, maybe you could post the output of the following command, it ought to tell us what ports that server is listening on for sure.

```
sudo netstat -tlnup
```

---

### Post by TheShader on 2010-05-22
DMZ mode didn't help... The output of the command is below:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      636/mysqld      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      843/sshd        
tcp6       0      0 :::80                   :::*                    LISTEN      714/apache2     
tcp6       0      0 :::22                   :::*                    LISTEN      843/sshd        
udp        0      0 192.168.1.112:27015     0.0.0.0:*                           953/hlds_amd    
udp        0      0 192.168.1.112:26900     0.0.0.0:*                           953/hlds_amd    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           826/dhclient3   

```

btw I changed the hlds IP to 127.0.0.1 just like the http but it didn't help neither.

---

### Post by jerome1232 on 2010-05-22
Yeah it wouldn't 127.0.0.1 is a loop back interface, it means it won't accept connections from anything but itself. (You mean mysqld, that the only service you have listening on 127.0.0.1?)

That looks fine to me, Unless there is something we are missing I think your isp just filters that port, will hlds allow you to set it to listen on other ports?

---

### Post by jerome1232 on 2010-05-22
As a second thought, I find it very odd that your isp wouldn't filter port 80, but would filter 27015.

You didn't mess with iptables or ufw did you? Iptables is the default "firewall" (it actually does much more than just block traffic) and ufw is the default front-end to make configuring it easy.

---

### Post by TheShader on 2010-05-22
Well actually I did. But I tried everything before playing with the iptables and it didn't work at that time also... You see, there are some ip forwarding commands on [this page]("http://server.counter-strike.net/server.php?cmd=howto&show=linux#router"). I entered corresponding commands with iptables.

Before editing the iptables when I started hlds it gave error "could not connect to steam servers", then "reconnected to steam servers" but after I changed iptables, it said "connected to steam servers". I don't know how to configure iptables correctly :/

Oh and for your first post, I tried port 27014 on hlds and had no difference from 27015.

---

### Post by jerome1232 on 2010-05-22
Well lets see what rules you have setup.

```
sudo iptables -L
```

I'm actually going to sleep (gotta love graveyard shifts) but hopefully someone else can chip in. If not I'll be back tomorrow.

---

### Post by TheShader on 2010-05-22
Hehe same here mate, and my grandma is sleeping in the room which the server is in :D I'll show you tomorrow. Good night, and thank you very much for your help! :popcorn:

---

### Post by XzZ-GaminG on 2010-05-22
Add **-Port 27015** to your launch ****" ./hlds_run -console -game cstrike -maxplayers 12 -ip 00.000.000.000** -port 27015 **

ps Open **4880 Both** "Dont know why but it seems to make the server "Call" the master more often" and **26900-26950 Both** allows you to have 50 server's registrated on the **VAC** "Main server" So if some one get's banned the info will be sent to **valve** and after Been Banned From many server's they Will Get **VAC** Banned

---

### Post by TheShader on 2010-05-23
Well it seems that the IPtables is the default... Don't know why.
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


```

@XzZ-GaminG It's already 27015 by default, but I added the port parameter just in case. Still the same. And what do you mean by opening 4880 both? I'm a newbie, can you explain further? Thanks.

---

### Post by TheShader on 2010-05-24
bumpn:confused:

---

### Post by jerome1232 on 2010-05-24
Well your iptables is at default settings, it's not blocking anything. Based on netstat output your server is listening, we put your server in dmz+ mode which means all ports get forwarded to it.

One thing I just realized, that port scanner I linked, scans tcp ports only.

Your game server is listening on 27015 UDP. UDP is connectionless unlike TCP which can make it difficult for port scanners to see if it's open or not.

I'm pretty much out of idea's, have you had a friend try connecting to see if they can connect?

---

### Post by TheShader on 2010-05-24
Hmm no, I tryed myself with the public IP and it always timed out. This is really strange... The bad thing about this is that the support for this dedicated server is "kind of" discontinued... I'll send a mail to valve about this later and see if it helps.

---

### Post by TheShader on 2010-05-24
Sorry for double posting, but can it be because of the router? Maybe I should port something else to 27015... For example Deluge web UI worked on 8112, if I set it to 27015 maybe it won't work? I'm a bit busy atm I'll try that 2-3 hours later and update this post.

---

### Post by jerome1232 on 2010-05-24
Doing some searching I found this site

[http://planethalflife.gamespy.com/View.php?view=HL2Guides.Detail&id=4&game=3](http://planethalflife.gamespy.com/View.php?view=HL2Guides.Detail&id=4&game=3)

The important part is this [http://www.gametiger.net](http://www.gametiger.net) can check to see if your server is online.

It also has this list of ports

```
UDP 1200 (Friends Network)
UDP 27000 to 27015 (Gameport)
UDP 27020
TCP 27030 to 27039
TCP 27015 (SRCDS Rcon port)
```

It for a windows hlds server but I imagine it's all the same (don't think you need rcon open)

I personally like to slap my server into dmz+ mode and configure it's firewall, I just think ufw is easier than configing a router. For now I wouldn't even put a firewall up at all until you get it working. I hope this helps some.

---

