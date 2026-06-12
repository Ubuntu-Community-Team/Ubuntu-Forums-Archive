---
title: "Need help connecting to Ubuntu SSH server"
date: 2006-04-19
forum: Server Platforms
---

### Post by Dertiger on 2006-04-19
I have the standard newbie problem - I can't establish an SSH connection from outside my home network - but I believe I have exhausted all the basic pitfalls.  Can someone offer any other suggestions?

-My router is set to DMZ to my Ubuntu server, which is running Firestarter.
-Firestarter has a policy to allow ALL to connect to port 2223
-I can confirm this setup is correct using Shield's Up to portscan my IP.  It reveals all ports are stealthed except 2223, which is open.

-sshd_config is listening on port 2223 - in fact, I can SSH just fine from inside the local network.
-netstat -plat shows this:
tcp6       0      0 *:2223                  *:*                     LISTEN     2240/sshd

-I have the same problems whether I use the IP or no-ip address name.

I can find no evidence of attempted connections in any logs...should there be?

Any suggestions are greatly appreciated, this has been driving my crazy for weeks.

Thanks!

---

### Post by Nequeo on 2006-04-19
Fascinating problem...

Have you checked your router logs, too?

---

### Post by Dertiger on 2006-04-20
Yeah, I've checked those logs too, for what they are worth.  I got the cheap router (DI-514) and think I am suffering the consequences of it.  When I turn on all logging capabilities, the router logs show nothing about any connections being made.  I did the Shields Up port scan with the router blocking all ports except 2223 and the router log did record all the dropped packets (it correctly dropped all except 2223).  I went back into DMZ mode and it correctly recorded no dropped packets.

I'm confident the router is working correctly, the problem seems to be on the server side.  Are there any logs that show attempted connections?  The Firestarter logs don't see anything on 2223.

Could something in the server setup or default Ubuntu setup that might disallow outside connections?

---

### Post by Nequeo on 2006-04-20
I've had a similar problem with a cheap router. At first it wouldn't correctly forward port 22 to my Ubuntu machine at all. After resetting to factory settings and reopening the port it now does - but still drops the connection every couple of minutes.

I've never had any trouble at all with SSH on any of the other five or so Ubuntu servers I've remotely administered. 

One other thing that might be worth trying is installing another server, like Apache, and open a port for it. Also, try changing the ssh port to the standard 22 and seeing if that works any better.

No real ideas at this point, just throwing a few ideas around in case I hit on something you haven't tried yet :)

[Edit] Another thought: Does the router have a built in firewall or packet filtering capabilities? One thing I found helpful for my cheapo router is add a rule to allow all incoming packets to my private IP address. Which is the default, anyway - but creating the rule for it forces successful connections to show up in the logs - whereas normally they don't. [/edit]

---

### Post by Iowan on 2006-04-20
Is the router forwarding the port - or just allowing connections on its port 2223?
I also noticed tcp6 - dunno if there may be an issue between v4 and v6.

---

### Post by Dertiger on 2006-04-20
Thanks Nequeo, I'll give those ideas a stab when I get home (can't do it from here...argh!)

I have the same problem whether I set the router to DMZ or just forward the single SSH port.

What does tcpv4 and v6 mean?  Is this something I can change within the sshd config?

---

### Post by Nequeo on 2006-04-20
[QUOTE=Iowan]Is the router forwarding the port - or just allowing connections on its port 2223?
I also noticed tcp6 - dunno if there may be an issue between v4 and v6.[/QUOTE]


Iowan - I also noticed the tcp6 thing, but didn't mention it. I assumed if he was able to SSH in from other machines internally, it was probably listening on tcp4 as well. But maybe I'm wrong about that. *shrug* Also, I didn't have access to my own machine to double-check whether that was the standard netstat output.

Dertiger - You're posting in the server forum about SSH over a non-standard port, so I'm going to assume you know more than the standard newbie and just post a link to the Wikipedia site: [http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6) 
It explains it much better than I ever could :) I don't think you can change it from sshd_conf. That just lets you set the port you listen on - or the addresses you're listening from.

Actually, there's a thought. If I recall correctly, doesn't the config let you specify which IP addresses you will accept connections from? Have you checked to make sure that it will allow connections from any IP? Pretty sure that's the default, but you may have changed it.

---

### Post by nagilum on 2006-04-21
Have you tried running the daemon in debug mode? It should then print if it actually received any SSH packets from your remote machine.

Another thing, some time ago I had also problems with SSH not accepting connections. It turned out that the hosts access control caused this. After I entered a line with "sshd: ALL" in my /etc/hosts.allow I could connect. Just an idea...

---

### Post by Dertiger on 2006-04-25
I have an update (with no success).  I installed and played with Ethereal to see if packets were actually making it down the pipe - they aren't when I try to access it remotely.  I've checked and re-checked my Firestarter and router policies and they seem fine - DMZ is enabled to my server, but it never sees the packets.  Neither Firestarter nor the router make any mention of dropped packets (I think it is a logging limitation).

I also installed an FTP server with exactly the same problem.  It works from within the local network, but not outside the router.

No luck adding the lines to hosts.allow.  I did learn something interesting though - Ubuntu doesn't come with inet.d by default.  Oops, learned that one trying to figure out why proftpd wouldn't work when set to inetd mode :)

Well, I'm stumped and I'm ready to give up.  Maybe I'll try another router in it's place someday, but I don't have one handy.  Thanks for all the suggestions!

---

### Post by alamba on 2006-04-25
I had a similar problem till I nmapped my system from an external network and realized my ISP was blocking all ports.

A

---

### Post by imagine on 2006-04-25
[QUOTE=Dertiger]I also installed an FTP server with exactly the same problem.  It works from within the local network, but not outside the router.[/QUOTE]How are you testing the connection from outside? At work?

---

### Post by LuisC-SM on 2006-04-25
I had a similar problem with SSH but I could fix it in some way.
Firstoff what I cannot understand is how you configured your server to DMZ as far as a server has a static IP and therefore cannot be turned to DMZ (maybe your r using DHCP I believe). 
If your server has a dinamic IP you will have to deal with such problems.  I strongly suggest u to change to "static" IP first. If u have a static IP then you must ask your routers manufacturer why it is letting u have a static IP under DMZ..
If you were just tricky (like me one time) and change your server's IP to to DMZ as soon as the router recognized it, then go back and leave it in "normal mode" (protected) and configure it to static. Then u must manually open all ports.
SSH uses port 22 by default and is not a big deal to open it.
Kind Regards

Luis C. Suárez

---

### Post by Dertiger on 2006-04-25
I scanned my system from the outside using the Shields Up website: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Would this be equivalent to "nmap"?  This website reports my ports as "open", so I assumed that meant the packets are getting through.

To connect from the "outside" I am just ftp'ing or ssh'ing from my local network, but I use the cable modem's IP address (or name - it is translated to the correct IP).  This is what I am doing when I run Ethereal and learn that these packets don't hit the server.  Will this accomplish what I need it to?

---

### Post by imagine on 2006-04-25
[QUOTE=Dertiger]To connect from the "outside" I am just ftp'ing or ssh'ing from my local network, but I use the cable modem's IP address (or name - it is translated to the correct IP).[/QUOTE]
That doesn't work (with your router). Use a computer which is located outside of your LAN.

---

### Post by Dertiger on 2006-04-26
Final update - I asked a friend to attempt to ssh into my machine and he said he got a connection!  I've only been able to try from work, and apparently they (a large corporation) are blocking these types of connections because I sure can't ssh, ftp, ping, or even resolve the domain name from my work computer.  Wow, I was impressed with what I've learned so far, now I'm blown away by the complexity of the networking equipment big companies have to manage!

Thanks for all your help, this has been very educational!

---

### Post by LuisC-SM on 2006-04-27
[QUOTE=Dertiger]Final update - I asked a friend to attempt to ssh into my machine and he said he got a connection!  I've only been able to try from work, and apparently they (a large corporation) are blocking these types of connections because I sure can't ssh, ftp, ping, or even resolve the domain name from my work computer.  Wow, I was impressed with what I've learned so far, now I'm blown away by the complexity of the networking equipment big companies have to manage!

Thanks for all your help, this has been very educational![/QUOTE]

One thing I forgot to tell u, for sure u cannot go with SSH 'cause there is a file you must delete or at least edit and delete all inside.

This file is in your $HOME/.ssh directory (follow this path):> ~/.ssh/known_hosts
Edit it and erase everything inside (or you can also save it before by):> cp -/.shh/known_hosts ~/.ssh/known_hosts.originalor even better:> mv ~/.ssh/known_hosts ~/.ssh/known_hosts.oldit doesnt matter if the file does not exists as far as it will be created with the next CA as soon as you run > ssh 192.168.#.###  (whatever your IP is

Note that ~/.ssh = /root/.ssh for this matter as far as only can use SSH with root.

Kind Regards

Luis C. Suárez

PS. Anyhow also check your home directory $HOME just in case

---

### Post by Jose Catre-Vandis on 2006-05-11
Unless you have already done so the best thing to do is to try to isolate the problem. This will mean having to drop ALL you guards, NAT/Firewall/Whatever, then try to connect from outside your LAN. If this works then add each element until you get blocked. Then get to work on that part. If you still have connection problems with everything down, then it must be either with your ISP or your "work"/other connection you are trying from.

IME its the software firewall, then the hardware firewall (NAT) that causes the probs

---

### Post by und3rtug4 on 2006-05-12
[QUOTE=Iowan]Is the router forwarding the port - or just allowing connections on its port 2223?
I also noticed tcp6 - dunno if there may be an issue between v4 and v6.[/QUOTE]

Yep... is it :-k ??

Just portforward or enable virtualservers on the router, so that all inbound traffic  on 2223 goes to the lan ip of your ssh server!

---

### Post by vivekR on 2006-05-22
[QUOTE=Dertiger]Final update - I asked a friend to attempt to ssh into my machine and he said he got a connection!  I've only been able to try from work, and apparently they (a large corporation) are blocking these types of connections because I sure can't ssh, ftp, ping, or even resolve the domain name from my work computer.  Wow, I was impressed with what I've learned so far, now I'm blown away by the complexity of the networking equipment big companies have to manage!

Thanks for all your help, this has been very educational![/QUOTE]

err.. as you say, this would mean outgoing ssh is being blocked from your office firewall. Most bigger companies always do that. 

So, you would have to tunnel ssh requests inside http requests, by using a special connect program. 

try this out, [http://zippo.taiyo.co.jp/~gotoh/ssh/connect.html](http://zippo.taiyo.co.jp/~gotoh/ssh/connect.html)

---

### Post by geezerone on 2006-05-22
[QUOTE=Dertiger] Wow, I was impressed with what I've learned so far, now I'm blown away by the complexity of the networking equipment big companies have to manage![/QUOTE]

This could be a traffic shaping firewall such as Packeteer which, when 'rules' are configured, would just be a matter of letting it do the hard work. You can block or limit bandwidth for well known apps or by port number(s) such as Quake, Torrents etc.

---

### Post by osinghrathore on 2006-05-27
Sorry if I m hijacking this thread :p
I've got similar problem with SSH 

Here's the description of the problem I m having:
> My Home PC is running SSHD (no firewall is there) and I am not able to connect to it from any outside system except from my live server, I've checked  hosts.allow to find any denying entries, when I try to SSH to it I get "connection timed out error", but when I SSH to it thru the live server I own, it works. Though I haven't made any specific settings for my live server.
 
 I m really clueless on this
 can somebody pls help.

---

