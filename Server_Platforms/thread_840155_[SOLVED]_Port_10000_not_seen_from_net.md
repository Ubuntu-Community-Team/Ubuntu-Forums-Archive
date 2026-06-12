---
title: "[SOLVED] Port 10000 not seen from net"
date: 2008-06-25
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-06-25
I have forwarded tcp port 10000 on my router to the ip of my ubuntu server however [http://www.canyouseeme.org](http://www.canyouseeme.org) says that it cannot see any service on that port. (nor could I connect remotely obviously)

How do I check that port 10000 is available for webmin across the net? It does work locally on the LAN.

Thanks,

---

### Post by windependence on 2008-06-25
Don't forget, if you are accessing Webmin from the outside, use [https://your_IP:10000](https://your_IP:10000)  

Note the 's'.

-Tim

FYI, you probably should have kept this all in one thread.

---

### Post by G1ZmO65 on 2008-06-25
Thanks Tim,

Yes, I did use the https and the work IP when I tried to access the server from home last night but it just timed out.

> **windependence said:**
> FYI, you probably should have kept this all in one thread. - Sorry, started a new thread because it was a different subject - Is that wrong?

---

### Post by windependence on 2008-06-25
Hmmm....gotta think about this. 

You should be fine with the new thread, just thinking some details from the original thread might be useful to folks who don't know what you have done so far. :)

-Tim

---

### Post by G1ZmO65 on 2008-06-25
Basically its a fresh install of ubuntu server 8.04 with webmin installed.

Now, to add to the issue. I just shutdown the server (from Webmin) to move it and when I put it back on I can log in from the CLI but not via webmin using the correct username/password and now its locked my ip.
Error - Access denied for IPADDRESS. The host has been blocked because of too many authentication failures.

Another small issue with my ubuntu-desktop pc is that it cant see [https://ubuntuserver:10000](https://ubuntuserver:10000) but can see [https://SERVER_IP:10000](https://SERVER_IP:10000)

First: How do I get round the lockout? [SOLVED]
Second: How to restore my webmin access? [SOLVED]
Third: The remote port 10000 problem

Lockout: The blocking of my ip address was obviously temporary but I still cant get into webmin. Just keeps saying **Login failed. Please try again.**

Ok, Got into Webmin by logging in as root but my original login isnt a webmin login anymore!
Recreated the login and logged out and back in successfully. OK, but why did that happen?

---

### Post by windependence on 2008-06-25
You may want to disable apparmor

```
sudo /etc/init.d/apparmor kill
sudo update-rc.d -f apparmor remove
```

-Tim

---

### Post by G1ZmO65 on 2008-06-25
Doesnt seem to let me do that. Do I need to be logged in as root? (nah doesnt work either)

[I]> sudo /etc/init.d/apparmor kill
Killing AppArmor module - failed, AppArmor is builtin: Failed.[/I]

---

### Post by G1ZmO65 on 2008-06-26
I forwarded port 10000 at home for my home server ip and can connect to it from work however I still cant connect to the work one from home.
As far as I can see its an identical install (same OS cd too)

Any other suggestions folks?:confused:

---

### Post by G1ZmO65 on 2008-06-30
Still stuck here I'm afraid.

I connected the server directly to the router port instead of through various switches but still am unable to connect from home.

Port 10000 is forwarded correctly to the LAN IP of the server.
My other port forwards for other machines (Win32) do work so I don't think the problem is with the router end. Got to be something on the Ubuntu server.

Can anyone suggest some diagnostic steps I can take (bearing in mind my total Linux newb status lol)

Thanks

Paul

---

### Post by G1ZmO65 on 2008-07-01
I have also checked with our ISP (Lumison) who say that they dont block ports for any broadband connection unless asked to do so.

I've to try to connect from home tonight again and do a tracert and they will check their firewall logs to see if theres anything relavent.

Failing that he suggested he suggested using a different port for Webmin. I'll try that the next night if I have no joy tonight.

Anyone else have this kind of problem?

(Think I'm talking to myself now)

---

### Post by windependence on 2008-07-01
Are you running a firewall on the Ubuntu box at work? You shouldn't need one if you are behind the router. I would suggest turning off the software firewall in Ubuntu.

-Tim

---

### Post by G1ZmO65 on 2008-07-01
Glad someone is reading this Tim :)

No firewall is running on the Ubuntu server

[I]"No IPtables firewall has been setup yet on your system. Webmin can set one up for you, to be stored in the save file /etc/iptables.up.rules, with the initial settings based your selection of firewall type below..
Allow all traffic"[/I]

---

### Post by windependence on 2008-07-01
:) Well I work nights and that is when I get to answer posts so most times during the day in the US you won't see me here. 

We're not giving up on this. YOU can fix it. I can help. Let me think about this some more. 

In the mean time, from the machine at work, go to canyouseeme.org and check port 10000 just for grins and giggles.

-Tim

---

### Post by G1ZmO65 on 2008-07-01
From [http://www.canyouseeme.org](http://www.canyouseeme.org) I get the following:

[I]Error: I could not see your service on OURIPADDRESS on port (10000)
Reason: Connection timed out[/I]

ALMOST posted our IP there too lol

I'm not in the US btw (Scotland)

---

### Post by windependence on 2008-07-01
OK either your port is not open, or the service is not listening on the port. I would bet the port is not open.

-Tim

---

### Post by G1ZmO65 on 2008-07-02
This is kind of an assumption I have made too but I have disabled and re-enabled it and still no joy

I have now got a VNC'd PC at home which I can connect to so that I can test the remote webmin from that IP while at work. 

Will report back in a wee while with any more findings.

Cheers

Paul

---

### Post by windependence on 2008-07-02
Just to confirm, you CAN get to webmin from inside the network at work. If so, that eliminates any problems on the Ubuntu box itself.

-Tim

---

### Post by G1ZmO65 on 2008-07-02
Yes, I can get into webmin from the LAN on port 10000

I spoke to our ISP tech folk and they checked the firewall logs and said that there were no reports of any blocking activity from my home IP to our work IP.

Next plan is to change my FTP server onto port 10000 and connect to it remotely. That'll eliminate the router being the issue.

btw the isp tech guy said that he thought "Ubuntu server does something funny with the IP tables as dafault and may only be allowing LAN access to port 10000"

Could this be the case?

---

### Post by G1ZmO65 on 2008-07-02
Right. I moved my (windows box) FTP server onto port 10000 and connected to it remotely with no problem so that says to me that:
1 - Neither the router or the ISP are blocking port 10000
2 - My port forwarding is working 
3 - The issue HAS to be on the Ubuntu box

btw he also suggested using "NoMachine" Server and Client to do a SSH VNC connection to the work server. Any opinions on that option?

I'd prefer to use Webmin if I can get it working tbh

---

### Post by windependence on 2008-07-02
Well we could zero out all the IPtables rules and see. You don't need a firewall in the corporate network anyway. Let me look up the commands. In Ubuntu, it's a real pain in the rear to disable the firewall.

-Tim

---

### Post by G1ZmO65 on 2008-07-02
FYI here's the Firewall page from Webmin

I have set the "Activate at boot" to NO and also did a RESET on the rules. Rebooted the server but still can't connect from the remote pc.

---

### Post by G1ZmO65 on 2008-07-02
I went to [http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html](http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html) and the very first test shows a problem.
----------------------------------
> ping 216.239.59.99
connect: Network is unreachable
> ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
----------------------------------
> less /etc/resolv.conf
Shows that the nameservers are correct
----------------------------------
> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
> route add default gw 192.168.0.250 eth0
> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.250   0.0.0.0         UG    0      0        0 eth0
----------------------------------
AND VOILA!! I can now get onto Webmin from the remote pc!

Yay! So it just needed a default gateway added.

Bet this is not the end of my questions though (not by a long way)

Thanks for your help Tim
So I start a new thread if I want to ask a question on a different topic?

Cheers

Paul

---

### Post by windependence on 2008-07-02
Good deal Paul and the best part is you figured it out YOURSELF!

Yes, if you have other questions by all means start another thread and we will do our best to help you.

-Tim

---

### Post by G1ZmO65 on 2008-07-02
I dont think "figured it out" is really what I did. More like "played about in the vain hope that something would work" lol

What do you think about?
 "NoMachine" Server and Client to do a SSH VNC connection to the work server. 
Any opinions on that option?

I've had a look at the installation pdf for it but it doesnt seem by any means easy.

---

### Post by windependence on 2008-07-02
You mean tunneling a VNC session? Sure, I do it all the time but mostly from a Windoze box. It's easy from puTTY. You can do it from a terminal also but I have to look up the command.

-Tim

---

### Post by G1ZmO65 on 2008-07-02
I take it I'd need to configure some SSH telnet service on the Ubuntu server for puTTY?

---

### Post by windependence on 2008-07-02
No, ssh should be already installed. You can try it by doing:


ssh user@server_name_or_ip

in a terminal on another machine or by using PuTTY in Windoze. If you can connect, you are ready to go. If not, let me know.

-Tim

---

### Post by G1ZmO65 on 2008-07-02
It says on Webmin:

SSH/Telnet Login 	
There is no SSH server running on ubuntuserver port 22.

and I get connection refused in puTTY

btw Just finishing work for the night so probably no more daft questions from me till the morning lol (unless I continue this at home)

---

### Post by windependence on 2008-07-02
You are trying o putty in from a different box right?

OK, get out of webmin, open a terminal and let's do some REAL admin stuff.

Try doing:

```
sudo /usr/sbin/sshd
```

at the command prompt and tell me what happens.

-Tim

PS, this should probably be a new thread. MODS, if you see this, can you split the ssh/VNC discussion? THX.

---

### Post by G1ZmO65 on 2008-07-02
Had to do it from the command shell in webmin cos I'm at home now :)

> sudo /usr/sbin/sshd
sudo: /usr/sbin/sshd: command not found

---

### Post by windependence on 2008-07-02
OK then we need to install it.

Try 

```
sudo apt-get install ssh

```


-Tim

---

### Post by G1ZmO65 on 2008-07-03
Had to do "sudo apt-get -f install" first but it couldnt resolve the address. Found that the default gateway had vanished again.
Fixed this.

Then did "sudo apt-get install ssh" but it failed saying that it couldnt find some files

[I]Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main libss10.9.8 0.9.8g-4ubuntu3.1 
404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libss10.9.8 0.9.8g-4ubuntu3.1 
404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libss10.9.8_0.9.8g-4ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libss10.9.8_0.9.8g-4ubuntu3.1_i386.deb) 404 Not Found
Unable to fetch some archives....[/I]

Tried "sudo tasksel" to install the openssh server but got "aptitude failed (100)"

---

### Post by G1ZmO65 on 2008-07-03
I've now got that installed I think

Yup, Installed and I can get into server via puTTY from work and from the remote pc (port 22 forwarded)

:)

---

### Post by G1ZmO65 on 2008-07-03
Any idea why the server loses the gateway setting every time it's shut down?

---

