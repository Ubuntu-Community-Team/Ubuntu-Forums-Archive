---
title: "ssh can't connect /firewall"
date: 2008-08-25
forum: Server Platforms
---

### Post by [pl]ice on 2008-08-25
hi guys,
 got myself VPS ubuntu, but at my work they're blocking my ssh outputs, i'm not sure if its on port or the protocol, whats the deal with that? the VPS company got online java script to open console or ssh. None of it works :/
checked the server, its up and running.
  How do i bypass this? I'm running windows at work :/

pls let me know :) or point in right direction, so i can setup the server heheh
thanks!!!

---

### Post by Stemp on 2008-08-25
SSH use port 22: Just change it.
In your server modify /etc/ssh/sshd_config :

```
# What ports, IPs and protocols we listen for
Port 22
```

And change 22 to the new port number.

On the client, you'll have to acces this port :

```
ssh <username>@<ipaddress> -p <num_port>
```

---

### Post by [pl]ice on 2008-08-25
Hi,
 i have changed the port, and then tested it. Now sitting back at work, and i still get connection timed out through putty.
telnet fails on that port as well, but ftp to the server works :/
other ideas? :)
thanks!!



> **Stemp said:**
> SSH use port 22: Just change it.
In your server modify /etc/ssh/sshd_config :

```
# What ports, IPs and protocols we listen for
Port 22
```

And change 22 to the new port number.

On the client, you'll have to acces this port :

```
ssh <username>@<ipaddress> -p <num_port>
```

---

### Post by Stemp on 2008-08-25
If ftp is working you may use this port to connect to ssh.
It's Port 21.

---

### Post by [pl]ice on 2008-08-25
> **Stemp said:**
> If ftp is working you may use this port to connect to ssh.
It's Port 21.

i don't get it fully, is the firewall blocking only few output ports, or the whole ssh protocol? if the ports then i'll play around with them, but i'm running the ftp as well hehehe
thanks!
EDIT:
  it is blocking the telnet to my IP on all ports eg 21,22,35(my new ssh) 80,8080 . Got apache on it, works through web, but not telnet. Also putty through RAW/Telnet will not work on any of those ports... 
wrrrrr

---

### Post by Stemp on 2008-08-25
The Firewall is blocking ports. 
So you'll have to try a non blocked port you don't use ;)

---

### Post by [pl]ice on 2008-08-25
> **stemp said:**
> the firewall is blocking ports. 
So you'll have to try a non blocked port you don't use ;)
67? Dns? :d

---

### Post by Stemp on 2008-08-25
If it's a big company they probably have their own dns servers, so they could also block this port.

---

### Post by [pl]ice on 2008-08-25
> **Stemp said:**
> If it's a big company they probably have their own dns servers, so they could also block this port.

its blocked as well :/
 The things open are VPN and VNC, so i have to lookup how to setup VPN on the server, and how to connect to it :/
  I could try to user proxies on port 80 etc ...? could I

---

### Post by doas777 on 2008-08-25
> **'[pl]ice said:**
> its blocked as well :/
 The things open are VPN and VNC, so i have to lookup how to setup VPN on the server, and how to connect to it :/
  I could try to user proxies on port 80 etc ...? could I

I'm guessing (and its just a guess, mind you) that they are blocking all packets with encrypted payloads (or just detecting tunneling protocols). 
Most corporate firewalls are far more than old-school packet filters, and check the content of the connection, rather than just the L4 and lower headers. this will likely extend to vpn tunnels as well, but probably not for SSL. 

I'm not sure how you would go about it, but I'd look for a host-admin tool that supports https\ssl. they kinda have to let that through, and it would be hard to tell whats inside.

do you have any accessible control interface for the server?

good luck,
franklin

---

### Post by doas777 on 2008-08-25
this looks a bit involved (but doable).if your up to it, it does explain how to tunnel ssh through a local apache server over https. it has the putty config you would need as well. it should work if you can hit https sites (ie: your bank, webmail) from inside the firewalled network.

[http://dag.wieers.com/howto/ssh-http-tunneling/](http://dag.wieers.com/howto/ssh-http-tunneling/)

---

### Post by [pl]ice on 2008-08-25
i have access through java script to console/ssh but that doesn't work as well. No other means of access ...
  if it was checking for encryption on packet level, then why i can't connect with telnet on port 80, timeouts using telnet on any ports, yet my Apache works...
 by host admin tool U mean like cPanel etc yeh?
how bout a tunnel through ssl to get the console ...?
and will a proxy work if i try to redirect ssh connection through 80 port?
thanks :)


> **doas777 said:**
> I'm guessing (and its just a guess, mind you) that they are blocking all packets with encrypted payloads (or just detecting tunneling protocols). 
Most corporate firewalls are far more than old-school packet filters, and check the content of the connection, rather than just the L4 and lower headers. this will likely extend to vpn tunnels as well, but probably not for SSL. 

I'm not sure how you would go about it, but I'd look for a host-admin tool that supports https\ssl. they kinda have to let that through, and it would be hard to tell whats inside.

do you have any accessible control interface for the server?

good luck,
franklin

---

### Post by windependence on 2008-08-25
The only way you are going to get around this is to use port 443. Don't forget if you use a proxy to get to the internet you will have to put that into putty as well. There is a place for your user name and password under the proxy tab.

-Tim

---

### Post by doas777 on 2008-08-26
> **'[pl]ice said:**
> i have access through java script to console/ssh but that doesn't work as well. No other means of access ...
  if it was checking for encryption on packet level, then why i can't connect with telnet on port 80, timeouts using telnet on any ports, yet my Apache works...
 by host admin tool U mean like cPanel etc yeh?
how bout a tunnel through ssl to get the console ...?
and will a proxy work if i try to redirect ssh connection through 80 port?
thanks :)
if your Apache is responding on port 80, you would not be able to connect to telnet via port 80, because telnet cannot listen on that port. Apache is already using it.

in terms of control, heres why I ask: you are trying to switch SSH listening ports on the server so you can connect via non-standard ports. you can only do that if you have access to the host via a CLI (ssh/telnet/etc) or desktop server (vnc/rdp/webmin/...) of some type. 

perhaps I'm confused by your description, but remember, what ever port you try to connect to needs to be running the server that your client expects. you can't just change putty to use destination port 4444 without changing the SSH server to listen on port 4444. otherwise you will just get endless timeouts, like you said you did running telnet over port 80. did you change your telnet server to listen on port 80?

---

### Post by doas777 on 2008-08-26
> **'[pl]ice said:**
> <snip>
how bout a tunnel through ssl to get the console ...?
and will a proxy work if i try to redirect ssh connection through 80 port? </snip>


yes using SSL for a tunnel is exactly what I;m suggesting. remember, ssl uses port 443 by default, not port 80. a remote proxy probably won't help unless your traffic can get out of the building. a local proxy may be needed to access the tunnel once you create it, but putty should be able to handle all of that.

---

### Post by windependence on 2008-08-26
If they're running ISA server, which is what they were using where I once worked, the only way out is through 443, because they filter traffic based on traffic type, so that if they block ssh, the only way you can run it is through SSL, because the filter cannot read that. Where I was also happened to run a proxy to get to the outside so I had to put my proxy settings in PuTTY as well, and then it worked fine. Just start an ssh daemon on your host at home by doing:

```
sudo /usr/sbin/sshd -p 443
```

This will not survive a reboot unless you set it up in the ssh config file. BTW, you can have one daemon listen on 22 and another on 443.

-Tim

---

### Post by doas777 on 2008-08-26
tim- you're quite right, if the org uses a proxy for internet connection, you would have to set putty to use it. I missed that. 

I do have a question though. does ISA not perform content checking on 443 traffic (thus missing that it was an SSH packet addressed to prt 443), or would you have to actually wrap the ssh packets in ssl ones?


thanks,
frank

---

### Post by windependence on 2008-08-26
Hehe, is doesn't detect them. It's the only pport I could use. ;)

-Tim

---

### Post by [pl]ice on 2008-08-27
443 blocked, proxy is checking packet headers.
  Hm, i haven't tried setting putty to local proxy hehe, will try that now. 
  I installed http-tunnel.com (after long trouble of forbidden notices...) and got the setup script from XP to find proxy IP. So yeh, it works heheh
putting my proxy into putty didn't work...

thanks guys :)

---

