---
title: "[SOLVED] Need help configuring VPN server on Ubuntu 8.10"
date: 2008-12-03
forum: Server Platforms
---

### Post by bmwman on 2008-12-03
I'm trying to access my home PC from the internet or while I'm at work. I did a little research and there're many different ways to do it. I picked OpenVPN. I followed multiple guides here:

[http://ubuntuforums.org/showthread.php?t=239219&highlight=openvpn]("http://ubuntuforums.org/showthread.php?t=239219&highlight=openvpn")
[http://www.thebakershome.net/openvpn_tutorial]("http://www.thebakershome.net/openvpn_tutorial")
[http://openvpn.net/index.php/documentation/howto.html#install]("http://openvpn.net/index.php/documentation/howto.html#install")

In all of them i get stuck at the same place: I edit the Vars with my info, then do ```
. ./vars 
``` and this is what i get on the next step :```
 netvista@netvista-desktop:/etc/openvpn/examples/easy-rsa/2.0$ sudo ./clean-all 
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.

```

Of coarse I tried running "source ./vars" first but that's not changing anything.

What do I need to do, I'm totally lost??

Also if there are any better/simpler solutions than OpenVPN I am open for suggestions.

Thanks

---

### Post by cdenley on 2008-12-03
ssh is very simple.
```

sudo apt-get install openssh-server

```
You're done! Now, if you want file access from windows, you can use WinSCP or FileZilla. From Ubuntu, you can use nautilus (Places>Connect to Server) or FileZilla. If you want shell access, you can use putty from windows, or the ssh command in Ubuntu. If you want to access a server on your LAN, use port forwarding. If you want to use your home computer as a socks proxy, use tunneling. What kind of access did you need?

---

### Post by bmwman on 2008-12-03
I use VNC or Remote Desktop. I know how to set up my port forwarding on my router. My concern is securing the connection, especially if my home network could be exposed.

Is SSH going to work?

---

### Post by cdenley on 2008-12-03
> **bmwman said:**
> I use VNC or Remote Desktop. I know how to set up my port forwarding on my router. My concern is securing the connection, especially if my home network could be exposed.

Is SSH going to work?

SSH will work perfectly. It is very secure. If you want to connect to port 5900 on your server:
```

ssh -L 5900:127.0.0.1:5900 xxx.xxx.xxx.xxx

```
or from windows, use putty and configure Connection>SSH>Tunnels with
source port:5900
destination:127.0.0.1:5900

Then, simply connect to port 5900 on your local computer
```

vncviewer 127.0.0.1

```

The only port you need to forward through your router is port 22. Everything will be tunneled through your encrypted ssh session.

---

### Post by bmwman on 2008-12-03
Can I use local LAN IP or the router external IP address? Why is the localhost for??

---

### Post by cdenley on 2008-12-03
> **bmwman said:**
> Can I use local LAN IP or the router external IP address? Why is the localhost for??

The ssh server you connect to will obviously be your WAN IP for your home computer's router. The port forward will be "5900:127.0.0.1:5900", which means it will bind locally 5900 to the address 127.0.0.1:5900 from your home computer. If you wanted to connect to another computer on the same LAN as your home computer, you can use that LAN address instead (5900:192.168.1.102:5900). The host address you port forward to needs to be visible to your ssh server.

```
ssh -L [local port]:[host relative to server]:[host port] [user]@[home ip]
```

---

### Post by bmwman on 2008-12-03
I have a spare machine here at work and i was able to SSH into it. So when i get home, I login to my router and forward port 22 to my server 192.168.1.102. Lets say my WAN IP is 5.5.5.5. Then from work I do ssh -L 5900:5.5.5.5:5900 user@192.168.1.102 ???

Thanks for your help by the way, I feel like getting close :)

---

### Post by cdenley on 2008-12-03
> **bmwman said:**
> I have a spare machine here at work and i was able to SSH into it. So when i get home, I login to my router and forward port 22 to my server 192.168.1.102. Lets say my WAN IP is 5.5.5.5. Then from work I do ssh -L 5900:5.5.5.5:5900 user@192.168.1.102 ???

Thanks for your help by the way, I feel like getting close :)

almost
```

ssh -L 5900:192.168.1.102:5900 user@5.5.5.5

```

---

### Post by HermanAB on 2008-12-03
Note that Windows Remote Desktop *is* secure.  You don't need to wrap it in another layer of encryption.  VNC is best avoided since it is both slow and insecure - rather use SSH, since it can do everything VNC does and more.

Cheers,

Herman

---

### Post by bmwman on 2008-12-03
Awesome, thank you so much :)

So once I'm in, i start > vncviewer 192.168.1.102, correct?

---

### Post by cdenley on 2008-12-03
> **bmwman said:**
> Awesome, thank you so much :)

So once I'm in, i start  correct?

No. Once you're in:
```

vncviewer 127.0.0.1

```

Your ssh client binds to the local port you specified, and connections to it get forwarded through your ssh tunnel to the ssh server, then routed to the host address you specified.

---

### Post by bmwman on 2008-12-03
> **HermanAB said:**
> Note that Windows Remote Desktop *is* secure.  You don't need to wrap it in another layer of encryption.  VNC is best avoided since it is both slow and insecure - rather use SSH, since it can do everything VNC does and more.

Cheers,

Herman

I don't really care for VNC either, but i like to use GUI and not just the SSH command line. So you're saying Remote Desktop by itself is safe? No need of SSH?

BTW I just tried the WinSCP and love the file transfer feature. Is there a way to view the screen on my home PC via SSH or that's what Remote Desktop does?

---

### Post by bmwman on 2008-12-03
Got it all working. I was trying to launch VNC on the server and not on my laptop. :)

Thanks for all your help.

---

