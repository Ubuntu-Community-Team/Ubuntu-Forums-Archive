---
title: "Vino over SSH question"
date: 2010-10-20
forum: Security
---

### Post by obogobo on 2010-10-20
Anybody know why I can SSH into to my Ubuntu box on port XXXX, but can only access my desktop through tunneled VNC if port 5900 is also open on the router?

I would think that I only need to keep port XXXX for SSH open and VNC would get tunneled through that... but if 5900 is not open, "The connection closed unexpectedly".

Could I get a little insight? :confused: Thanks!

---

### Post by CharlesA on 2010-10-20
You have to create a tunnel in order to tunnel VNC over it.

Something like:

ssh -L 5900:host:5900 user@host

Then connect by typing in localhost into a vncviewer.

---

### Post by obogobo on 2010-10-20
Oh yes I forgot to mention, I use PuTTY to create a tunnel and forward local port 5900 to remote port 5900. It works great when port 5900 is open on my router, but fails when this port is closed.

I shouldn't have to keep this port open if the SSH Tunnel is encapsulating the VNC traffic right? I only want one port to be open, as having VNC open as well would create a security hazard I assume

---

### Post by CharlesA on 2010-10-21
> **obogobo said:**
> Oh yes I forgot to mention, I use PuTTY to create a tunnel and forward local port 5900 to remote port 5900. It works great when port 5900 is open on my router, but fails when this port is closed.

I shouldn't have to keep this port open if the SSH Tunnel is encapsulating the VNC traffic right? I only want one port to be open, as having VNC open as well would create a security hazard I assume

Correct.

It's not a good idea to expose VNC directly to the internet.

How are you creating the tunnel, and do you have a firewall in place?

---

### Post by obogobo on 2010-10-21
A few details about my setup might help

Ubuntu:  10.04.1
OpenSSH: Pub/Private Keyfiles, (Let's say port 1024)
Vino:    Just Vino, I don't know much about it

Windows: 7
I've tried the tunnel with both PuTTY and the OpenSSH Client

[LIST]
[*]PuTTY: me@host, Port 1024 SSH, Compression Enabled, Specify Keyfile
   <Tunnel> Local, Source Port:5900, Destination:me@host:5900

[*]OpenSSH Client: ssh me@host -p 1024 -L 5900:host:5900
[/LIST]

RealVNC Viewer: Connects to localhost:5900

Router: ports 1024 and 5900 are open and forwarded to the Ubuntu box

There are no firewalls that I'm aware of running on Ubuntu, I figured the router would suffice... and Comodo Firewall usually runs on my Windows 7 laptop, however I disable it for testing purposes.

Umm that's really all the information I can think to put

---

### Post by perspectoff on 2010-10-21
The router will block incoming traffic, but not outgoing traffic. 

For troubleshooting, it is easiest if firewall is turned off (i.e. all ports unblocked and allowed, or "permissive mode"), though, even if you have one.

PuTTY does not use the same key structure as the OpenSSH server, so if you are using key authentication make sure your keys are compatible.

If you are tunneling, you don't need port 5900 to be open to the Internet through the router (that's the whole point of tunneling). However, you do need it open locally (on both the server and the client), or there will be no access from the SSH tunnel to the VNC Server, which is a local loop on either end.

SSH / VNC / Remote Access info in detail is available at:

[http://ubuntuguide.org/wiki/Ubuntu:All#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:All#Remote_Access)

or

[http://kubuntuguide.org/All#Remote_Access](http://kubuntuguide.org/All#Remote_Access)

Further, you must have not only an OpenSSH Server running on the host, but also a VNC Server.

Some of the VNC servers are a bit flaky, IMO. I like X11VNC Server the best.

TightVNC Server on Linux has been erratic for me. Krfb in Kubuntu has also been erratic.

---

### Post by CharlesA on 2010-10-21
You don't need to have port 5900 open the in order to connect to VNC.

Is anything listed for port 5900 when you run this:
```
netstat -ln
```

vino doesn't start until you physically login to the GUI as far as I know.

---

### Post by endotherm on 2010-10-21
one thing to consider is that the firewall on your vnc server must be configured to allow 5900 connections from localhost. you can block everyone else, but your ssh process needs to be able to connect to the vnc service. or you can just open it up to all network hosts in iptables, as long as you turn off the port forwarding to  5900 on your router. and Charles is right, vino is only available after desktop login, and is per user, so the logged in user must have themselves configured "remote desktop". if you want to be able to login after connecting to vnc, then you need to set up a full vnc server. check here for some details: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by obogobo on 2010-10-21
Right I have keys that work with ssh and PuTTY

When I analyze the packets with wirehark, VNC **is** being tunneled correctly. And when my desktop appears, a notifiaction pops up and says, "Your desktop is being controled by a user" and then gives the Ubuntu box's EXTERNAL IP.

Shouldn't this say localhost instead of my external IP?

Also, even though I know the VNC traffic is encrypted and tunneled, if I close port 5900... VNC tells me the connection.has closed unexpectedly!!! it makes no sense.

---

### Post by CharlesA on 2010-10-21
Are you closing port 5900 on the router, or on the box you are connecting to?

You need that port open on the box you are connecting to, else you'll lose the connection.

Basically that's happening when you do ssh tunnels is this:

You connect to SSH via port 22 (or whatever port you designate) and then tell it to connect to port 5900 on that machine, which it can't do if you close that port.

```
Host1 ====== Host2 ===== Host3
```

Example: If you are Host1 and are trying to connect to Host3 using VNC that is being tunneled over SSH, you would have to connect to Host2 first, and then it would create a tunnel to Host3.

You are still connecting from yer external IP, but VNC is being "tunneled" thru SSH over the internet, not on port 5900.

---

### Post by obogobo on 2010-10-21
Hmm okay so iptables? Never played with those before. If you're saying I need to allow connections from localhost, how would I go about this? Thanks a lot for the insight by the way :)

---

### Post by CharlesA on 2010-10-21
```
sudo iptables -A INPUT -i lo -j ACCEPT
```

That should set it to access anything on the loopback address.

You can also use ufw or gufw to set it up.

---

### Post by obogobo on 2010-10-21
I'm only dealing with ports on the router, the box's ports I am not messing with. And I'll try the netstat and iptables suggestions as soon as I get home!

 Also, I have a gnome session set to start on auto login every boot so Vino is always running.

---

### Post by CharlesA on 2010-10-21
There shouldn't be anything that needs to be configured on the router except to forward the port SSH is using.

I've tunneled VNC over SSH with just that port open without problems.

---

### Post by perspectoff on 2010-10-21
> **obogobo said:**
> Right I have keys that work with ssh and PuTTY

When I analyze the packets with wirehark, VNC **is** being tunneled correctly. And when my desktop appears, a notifiaction pops up and says, "Your desktop is being controled by a user" and then gives the Ubuntu box's EXTERNAL IP.

Shouldn't this say localhost instead of my external IP?

Also, even though I know the VNC traffic is encrypted and tunneled, if I close port 5900... VNC tells me the connection.has closed unexpectedly!!! it makes no sense.

Well, port 5900 is used on your localhost computer for VNC. A tunnel is actually a local loop, after all. If you forbid port 5900 locally, the tunnel will be closed.

That's quite a different thing then allowing port 5900 to pass through your router to the Internet (which is generally set at the router level).

---

### Post by obogobo on 2010-10-21
Well netstat -ln shows the system is listening for SSH and on 5900...

At least we know the services are running! Hah well I tried the IPTables too...  no luck.

---

### Post by CharlesA on 2010-10-21
Not sure what else you can do tbh.

It *should* be working.

---

### Post by perspectoff on 2010-10-21
Ok, I re-read what you are saying. Yes, you are doing VNC directly, and the connections are not going through the tunnel. 

There is probably some syntax error in your tunneling command from your client.

From my (SSH) client, I use this:

ssh -C 244.205.123.123 -p 22 -L 5900:192.168.1.155:5900 -l joe.friday
krdc vnc://localhost:5900

where port 5900 is used for VNC on both client and host, the SSH port is the standard 22, the router WAN IP address is 244.205.123.123 (can also be a URL), and the VNC host on the LAN is at 192.168.1.155.

(I use Krdc instead of Vino as my VNC client, but it shouldn't matter much).

You know, SSH is included by default in Ubuntu -- is there a reason you're using PuTTY?

Anyway, if connecting using PuTTY, the commands are rather similar.

putty -ssh -i ~/.ssh/id_rsa -l joe.friday -L 5900:127.0.0.1:5900 remoteserver.computer.xyz -P 22
krdc vnc://127.0.0.1:5900

(I use OpenSSH keys with PuTTY, as designated by the -i ~/.ssh/id_rsa option).

Oh yes, last thought. Many VNC servers provide only a single session instance. If you log out you can't log back in without restarting the server again. In X11VNC, for example, you have to start with the --forever option if you want to be able to log out and log back in repeatedly. 

I'm not sure if you have to do something similar with other VNC servers.

---

### Post by obogobo on 2010-10-21
Keyword: *should* be working hah but okay i'll definitely try the different snytax commands right after class. 

Just fyi, I'm at college using my Windows 7 laptop to remote into my Ubuntu server at home... which happens to be ln the other side of the country haha sometimes its a little tricky making changes, thanks for bearing with me

---

### Post by obogobo on 2010-10-21
[SIZE="3"]**Ah sweet success!**[/SIZE] perspectoff, you were correct I had a syntax error in creating the tunnel...

I was using:
```
ssh me@EXTERNALhostIP -p 1024 -L 5900:EXTERNALhostIP:5900 
```

When I should have been using:
```
ssh me@EXTERNALhostIP -p 1024 -L 5900:**INTERNALhostIP**:5900 
```

The connection would fail when port 5900 was closed on the router because I was creating the tunnel using the server's External IP address instead of it's Internal. That's NAT for ya haha

Anyways thanks so much to everyone who helped, this issue is now solved :D

---

### Post by mrhhug on 2011-03-07
i know im posting in a year old 'solved' thread but i stumbled across it so others probably will too

X = the ip your want to view

vinarge will do all the ssh tunneling and dirty work for you (at least as of maverick) make sure protocol is VNC, the host is X and the bottom line "use host X as ssh tunnel" is checked 

you'll be controlling your server in 2 pastes flat

---

