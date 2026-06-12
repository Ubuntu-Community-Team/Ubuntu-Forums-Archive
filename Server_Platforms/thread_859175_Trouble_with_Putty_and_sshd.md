---
title: "Trouble with Putty and sshd"
date: 2008-07-14
forum: Server Platforms
---

### Post by jbsimon000 on 2008-07-14
Hi,
I am having trouble accessing my server from outside my local LAN using ssh.

SSH is on port 23. I am doing this because at the location I am at, outgoing telnet port is open but not ssh port. I was reading a thread where one of the posters was getting telnet running (for the same reason, outgoing ssh port not open) and someone suggested using ssh on the telnet port instead. I used to use telnet, but wanted something more secure so I am trying to get ssh working.

From within my LAN if I use putty, I can connect to [www.myserver.com](www.myserver.com) on port 23, no problem.

From outside my lan, when I try to get to [www.myserver.com](www.myserver.com) a message box pops up after a little while "Network error: Software caused connection abort". 

If I try to telnet into the port, I get "SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2", so it appears that I have connectivity to the server. Any insight into the problem is appreciated ?

Thanks !
Joe

---

### Post by cdenley on 2008-07-14
Can you ping the server? For some reason, some windows clients require you to be able to ping the server, but some routers won't respond to pings. Can you connect from an ubuntu livecd?

---

### Post by windependence on 2008-07-14
Do you have port 23 forwarded back to your server from your router?

Did you start the ssh daemon on port 23?

```
sudo /usr/sbin/sshd -p 23
```

-Tim

---

### Post by jbsimon000 on 2008-07-14
I cannot ping the server from where I am.

H:\>ping [www.jbsimon000.com](www.jbsimon000.com)

Pinging jbsimon000.com [69.205.183.211] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 69.205.183.211:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

H:\>

I need to be able to ping it before I can use SSH ? It appears that I can't ping any external entities from here, does that rule out SSH ?

I sued the ssh configuration script to set the port. It appears to be working since if i telnet to the port I get 
"SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2"\

Thanks !
Joe

---

### Post by jbsimon000 on 2008-07-14
Oops, finish my reply to cdenley

I have not tried a live CD. I attempted from a solaris box but I got a message "PRNG is not seeded" which indicates that ssh is not set up correctly on the box. I will try a live CD when I get the chance.

Thanks !
Joe

---

### Post by windependence on 2008-07-14
Sorry but being able to ping the server does not necessarily have anything to do with ssh. If the router is set to quench pings you won't be able to ping it anyway. Your router port is most likely not forwarded back to the server. 

I don't know what a live CD is going to prove.

-Tim

---

### Post by cdenley on 2008-07-14
> **windependence said:**
> Sorry but being able to ping the server does not necessarily have anything to do with ssh. If the router is set to quench pings you won't be able to ping it anyway. Your router port is most likely not forwarded back to the server. 

I don't know what a live CD is going to prove.

-Tim

Based on my experience, some clients require you to be able to ping. Ubuntu's does not. Using an ubuntu livecd would verify that this is the problem. Since the OP connected on port 23 over the internet, and got a response from SSH (SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2), the router must be forwarding the port.

---

### Post by jbsimon000 on 2008-07-14
Yes, based on the response when I attempt to telnet in, "SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2" I am assuming that the request is making it through my router correctly, and that SSH is configured for the correct port (in this case 23).

The question is, why cant I connect properly with ssh.

if someone wants to try connecting ssh to [www.jbisimon.com](www.jbisimon.com) on port 23, see if you can connect. I cannot (it might be a problem on the client end, I do not know, this is the only place I can go at this time to try and get in).

Thanks !
Joe

---

### Post by cdenley on 2008-07-14
> **jbsimon000 said:**
> 
if someone wants to try connecting ssh to [www.jbisimon.com](www.jbisimon.com) on port 23, see if you can connect. I cannot (it might be a problem on the client end, I do not know, this is the only place I can go at this time to try and get in).

Your domain name doesn't seem to resolve to an IP address. Are you sure you typed it correctly? Did you use that domain for your ssh client and telnet?

---

### Post by jbsimon000 on 2008-07-14
Dang !

[www.jbsimon000.com](www.jbsimon000.com)


Sorry !

Joe

---

### Post by cdenley on 2008-07-14
I can connect fine. I can't login, of course.

---

### Post by jbsimon000 on 2008-07-14
OK Great. That means the server is OK but that this client is giving me trouble.

DRAT.

Thanks !
Joe

---

