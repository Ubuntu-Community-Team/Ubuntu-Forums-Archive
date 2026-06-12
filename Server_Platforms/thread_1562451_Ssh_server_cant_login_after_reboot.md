---
title: "Ssh server cant login after reboot"
date: 2010-08-27
forum: Server Platforms
---

### Post by X1R1 on 2010-08-27
Hi, I have a Samba file server setup at work, everything works great except for one thing. I usually do some remote maintenance and update installation for the server, sometimes its needs to be rebooted. The thing is everytime I reboot, I cant login back to the ssh server (of course I wait a bit, ping the machine and after succesfull response, try to ssh to it). For the ssh to work I will have to go ahead and login locally on the server (go to the office, plugin in keyboard, type in username and password) and then ssh works again.

This isnt practical because If I have to get to the office everytime I reboot then there is no point in having ssh installed.

hope you can help

regards

---

### Post by FuturePilot on 2010-08-27
Did you enable encryption of your /home when you installed it?

---

### Post by X1R1 on 2010-08-27
> **FuturePilot said:**
> Did you enable encryption of your /home when you installed it?

if I remember right, NO, how can I check?

---

### Post by FuturePilot on 2010-08-27
> **X1R1 said:**
> if I remember right, NO, how can I check?

Run

```
mount | grep ecryptfs
ls -la /home | grep ecryptfs
```

If both of those return nothing then you didn't.

---

### Post by X1R1 on 2010-08-27
> **FuturePilot said:**
> 
If both of those return nothing then you didn't.

I didnt, no return from the commands

---

### Post by cdenley on 2010-08-30
Is this a desktop installation? How is networking configured?
```

cat /etc/network/interfaces

```

---

### Post by X1R1 on 2010-08-30
> **cdenley said:**
> Is this a desktop installation? How is networking configured?
```

cat /etc/network/interfaces

```

No, ubuntu server 10.04 64bit setup, network is configured as follows:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


---

### Post by spiky001 on 2010-08-30
Hi Dont know if this helps ( i,m not a server user) when you reboot is auto login enabled just a thought

---

### Post by X1R1 on 2010-08-30
> **spiky001 said:**
> Hi Dont know if this helps ( i,m not a server user) when you reboot is auto login enabled just a thought

It isnt, but enabling it would pose a great security risk, imagine I have to restart the server remotely, someone could just sit in front of the machine and do whatever they want.

One thing that comes to my mind now you say that, would be to have the machine auto-login and then go in locked state, but I think that to lock a machine you need a graphical manager dont you (like gnome gdm or slim)?

That way the service would go up and then to unlock the machine you will need to input the password.

---

### Post by spiky001 on 2010-08-30
That is how mine works I use normal distro so screen saver locks on, maybe load a desktop just for that, at least your on your way now with solving

---

### Post by X1R1 on 2010-08-30
> **spiky001 said:**
> That is how mine works I use normal distro so screen saver locks on, maybe load a desktop just for that, at least your on your way now with solving

thing is, I dont have any graphical tools is just command line, I dont need a graphical environment, so I would need a command line locking tool.

---

### Post by akira7799 on 2010-08-30
I ran into this problem.  
 
> # The primary network interface
auto eth0
iface eth0 inet dhcp 
 
This might be causing it.  Are you trying to log-in via server name or IP?  If IP, it might change since it's auto.  You might want to try listing a static IP.
 
Just a thought, 
Dave

---

### Post by spiky001 on 2010-08-30
so you need network to start on boot

---

### Post by X1R1 on 2010-08-30
> **akira7799 said:**
> I ran into this problem.  
 

 
This might be causing it.  Are you trying to log-in via server name or IP?  If IP, it might change since it's auto.  You might want to try listing a static IP.
 
Just a thought, 
Dave

Ip is auto because the dhcp server has a reservation for my Ubuntu Server so even if its automatic, the ubuntu server machine always get the same IP address.

To clarify a little more, ssh wont work if I am not locally logged in into the Ubuntu Server first.

One thing that just crossed my mind is that maybe the ssh services is somewhere specified that it should load after login, so maybe I can change that behaviour by putting it to load at system boot before login, can it be done?

cheers

---

### Post by BkkBonanza on 2010-08-30
For a server install none of this makes sense.

Assuming sshd is correctly installed, it should be enabled to start listening on boot. You can check the init scripts to ensure it comes up, and use **sudo netstat -lntp** to make sure it is there after boot.

There is no way that you should need to login locally or enable auto-login or mess with dhcp  to solve this.

If you can ping the machine then obviously your IP is ok. If you can use nmap to check port 22 then do that, from another mahcine, **sudo nmap -sT -p 22 *IP***. If it is open then you have a sshd config problem of some sort. If it is closed/filtered then you have an issue with a firewall or iptables script that is blocking access. Or sshd is configured to listen on another address. How or why that is I couldn't say as there are many variants.

However, I've run servers across the net in data centers for years and never had to login at the tty console to get ssh enabled, so some other factor is at work here. Some firewall sounds most likely to me. Some firewalls include a default debug mode that have a few minutes delay before they disable themselves to prevent mistakes from full lockout.

---

### Post by X1R1 on 2010-08-30
> **BkkBonaza said:**
> For a server install none of this makes sense.

Assuming sshd is correctly installed, it should be enabled to start listening on boot. You can check the init scripts to ensure it comes up, and use **sudo netstat -lntp** to make sure it is there after boot.

There is no way that you should need to login locally or enable auto-login or mess with dhcp  to solve this.

If you can ping the machine then obviously your IP is ok. If you can use nmap to check port 22 then do that, from another mahcine, **sudo nmap -sT -p 22 *IP***. If it is open then you have a sshd config problem of some sort. If it is closed/filtered then you have an issue with a firewall or iptables script that is blocking access. Or sshd is configured to listen on another address. How or why that is I couldn't say as there are many variants.

However, I've run servers across the net in data centers for years and never had to login at the tty console to get ssh enabled, so some other factor is at work here. Some firewall sounds most likely to me. Some firewalls include a default debug mode that have a few minutes delay before they disable themselves to prevent mistakes from full lockout.

I will try your suggestions right now, everyone just left so server is not un use, be back in a couple of minutes with the results, stay tuned :D

---

### Post by X1R1 on 2010-08-30
Just rebooted the server, this is the output of the nmap command:


Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-08-30 19:05 CST
Nmap scan report for 172.24.3.57
Host is up (0.00017s latency).
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: D8:D3:85:AE:08:44 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds

And WOW, now I was able to log in without problems lol

I sent a reboot form an ssh session and when the server came back online all worked great again. Very weird, I have been having this problem for more than a month and just got fixed by itself wtf?? maybe and update or something like that solved it?

cheers

---

### Post by BkkBonanza on 2010-08-30
Hmmm. I'm guessing the problem will come back unless it has really been fixed somehow. 
nmap wouldn't have changed anything... 

There is a thing called "port knocking", where you have to "knock" on a port before it will allow access. But that has to be explicity added and configured, so unless someone did that it wouldn't be in effect.

---

### Post by X1R1 on 2010-08-30
> **BkkBonaza said:**
> Hmmm. I'm guessing the problem will come back unless it has really been fixed somehow. 
nmap wouldn't have changed anything... 

There is a thing called "port knocking", where you have to "knock" on a port before it will allow access. But that has to be explicity added and configured, so unless someone did that it wouldn't be in effect.

Well I didn't and I am the only one that configures this server lol.

Nevertheless, I did learn a lot from your input, now at least I would know where to look in case something goes wrong again.

Hope the problem doesn't come back but I am really intrigued at  how it got fixed :confused:

---

