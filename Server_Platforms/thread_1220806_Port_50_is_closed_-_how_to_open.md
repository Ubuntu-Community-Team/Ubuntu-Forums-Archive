---
title: "Port 50 is closed - how to open?"
date: 2009-07-23
forum: Server Platforms
---

### Post by tom66 on 2009-07-23
As can be seen in the screenshot port 50 is blocked.

I want to unblock this for purposes as a SSH port, how could this be done? I've tried firestarter but I can only get it to act as stealth or as closed. 

Any help appreciated.

---

### Post by Cheesemill on 2009-07-23
Have you forwarded port 50 on your router?

---

### Post by wojox on 2009-07-23
Stop using firestarter and try ufw and gufw

---

### Post by tom66 on 2009-07-23
Good question...

Port 50 seems to be OK with the router because I can change it from closed to stealth using FireStarter. I just can't get it open. Also I checked the firewall rules on the router: local LAN allow all ports.

---

### Post by Cheesemill on 2009-07-23
Do you have anything listening on port 50?

---

### Post by tom66 on 2009-07-23
I don't know, how could I find out?

(I'm new to setting up a server, trying to make a http server with Ubuntu.)

---

### Post by dragos2 on 2009-07-23
> **tom66 said:**
> I don't know, how could I find out?

(I'm new to setting up a server, trying to make a http server with Ubuntu.)

nmap ip -p50 -P0

---

### Post by tom66 on 2009-07-23
Thanks, got result:

```

ross@jupiter:~$ nmap [IP REMOVED BY ME] -p50 -P0

Starting Nmap 4.62 ( http://nmap.org ) at 2009-07-23 12:35 BST
Interesting ports on BeBox.config ([IP REMOVED BY ME]):
PORT   STATE    SERVICE
50/tcp filtered re-mail-ck

Nmap done: 1 IP address (1 host up) scanned in 2.041 seconds

```

Seems port 50 is filtered. I noted this, so I removed all firewall rules on the port. Now port 50 is in stealth, as shown by a port test. But nmap still sees the port as filtered:

```

ross@jupiter:~$ nmap [IP REMOVED BY ME] -p50 -P0

Starting Nmap 4.62 ( http://nmap.org ) at 2009-07-23 12:38 BST
Interesting ports on BeBox.config ([IP REMOVED BY ME]):
PORT   STATE    SERVICE
50/tcp filtered re-mail-ck

Nmap done: 1 IP address (1 host up) scanned in 2.042 seconds

```

---

### Post by dragos2 on 2009-07-23
> **tom66 said:**
> Thanks, got result:

```

ross@jupiter:~$ nmap [IP REMOVED BY ME] -p50 -P0

Starting Nmap 4.62 ( http://nmap.org ) at 2009-07-23 12:35 BST
Interesting ports on BeBox.config ([IP REMOVED BY ME]):
PORT   STATE    SERVICE
50/tcp filtered re-mail-ck

Nmap done: 1 IP address (1 host up) scanned in 2.041 seconds

```Seems port 50 is filtered. I noted this, so I removed all firewall rules on the port. Now port 50 is in stealth, as shown by a port test. But nmap still sees the port as filtered:

```

ross@jupiter:~$ nmap [IP REMOVED BY ME] -p50 -P0

Starting Nmap 4.62 ( http://nmap.org ) at 2009-07-23 12:38 BST
Interesting ports on BeBox.config ([IP REMOVED BY ME]):
PORT   STATE    SERVICE
50/tcp filtered re-mail-ck

Nmap done: 1 IP address (1 host up) scanned in 2.042 seconds

```

Try this

nmap -sT ip -P0 -v -p50

It should say open if ok.

---

### Post by tom66 on 2009-07-23
No luck:

```

Starting Nmap 4.62 ( http://nmap.org ) at 2009-07-23 13:38 BST
Initiating Parallel DNS resolution of 1 host. at 13:38
Completed Parallel DNS resolution of 1 host. at 13:38, 0.00s elapsed
Initiating Connect Scan at 13:38
Scanning BeBox.config ([ip removed]) [1 port]
Completed Connect Scan at 13:38, 2.00s elapsed (1 total ports)
Host BeBox.config ([ip removed]) appears to be up ... good.
Interesting ports on BeBox.config ([ip removed]):
PORT   STATE    SERVICE
50/tcp filtered re-mail-ck

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 2.048 seconds

```

Thanks for your help.

---

### Post by wojox on 2009-07-23
UFW is currently the recommended firewall manager. You can install the GUFW (gui) from the Add/Remove menu.

---

### Post by tom66 on 2009-07-23
With (G)UFW I am able to 'Stealth' or 'Close' the port. I want to 'Open' it. Any tips?

---

### Post by wojox on 2009-07-23
```
sudo ufw allow 50
```

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by tom66 on 2009-07-23
Unfortunately it didn't work, still showing as Stealth. Do I have to update/save the ufw rules or reboot?

---

### Post by wojox on 2009-07-23
Show me 

```
sudo ufw status
```

---

### Post by tom66 on 2009-07-23
```

ross@jupiter:~$ sudo ufw status
[sudo] password for ross: 
Sorry, try again.
[sudo] password for ross: 
Status: loaded

To                         Action  From
--                         ------  ----
50/tcp                     ALLOW   Anywhere
50/udp                     ALLOW   Anywhere

```

---

### Post by cdenley on 2009-07-23
Nothing will say the port is open unless there is a server which accepts the connection. If you want to see if there is a server listening on port 50:
```

sudo lsof -i :50

```
If you want to start a listening process that accepts a single connection on port 50, then prints any sent data to the terminal:
```

sudo nc -l -p 50

```

The data is reaching your computer. There is no process listening for that data. There is no reason for your computer to accept the connection, so it is rejected. The port is available for a listening process to use, but it will not be "open" until a listening process uses it. What are you expecting your computer to do with incoming connections on port 50?

---

### Post by cariboo on 2009-07-23
Quit using GRC's Shields Up. All it does is check your router. You have a service listening  on port 50 called re-mail-ck - Remote Mail Checking Protocol.

To set what port ssh is listening on you need to change /etc/ssh/sshd_config, then port forward that port to your router. Then go to [canyouseeme]("http://canyouseeme.org") to make sure the port is open on the router.

---

### Post by cdenley on 2009-07-23
> **cariboo907 said:**
> Quit using GRC's Shields Up. All it does is check your router. You have a service listening  on port 50 called re-mail-ck - Remote Mail Checking Protocol.

Nmap did not indicate he had a service listening on port 50. It indicated the port was closed (filtered). The re-mail-ck service it listed was simply the service commonly associated with that port.

As he said, if you want SSH to listen on port 50, you have to configure that in /etc/ssh/sshd_config.

---

