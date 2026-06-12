---
title: "cant connect to vnc"
date: 2009-08-04
forum: Security
---

### Post by parrimin on 2009-08-04
Hi,

I have installed xvnc4viewer in a xubuntu installation, and have some problem. The server (xubuntu) is a server from the job, and it was running before ive been born XD, so i cant reinstall.
Ok, just i said before xvnc4viewer is installed properly. If i try from a Windows XP (with VNC Viewer) to connect to the server it says "unable to connect to host: Connection timed out (10060)".
To fix this i have to do the next steps:
- Go to the server and make a ping to Windows host.
- Go to Windows host and try to connect via VNC.
and... walla! All running ok as expected. I spent some days to find this solution.

So, whats the problem? I would like to not to have to go to the server to ping my machine every time i wanna connect. I cant understand this behaviour. 
- I tried to reset iptables in the server and nothing changes.
- From Windows machine, i can ping the server.
- There is a firewall in the company, but it only blocks connections between lan - wan.
- Ah, and there is another server in the company that we can connect with no problem.

Any suggestions? I have no idea how to continue trying

---

### Post by parrimin on 2009-08-24
uppppp. Hey, no ideas? If you consider i must ask this in another thread, tell me please. I was wonderin if i would ask in network, or general...

---

### Post by HermanAB on 2009-08-24
It is your ethernet switch that is screwing with your head.  It may have a badly implemented port-to-port security enabled, but more likely it just forgets who is who and then needs a fresh set of ARPs to figure it out again and make the connection.  Swap the switch with another and see if the problem goes away.

---

### Post by parrimin on 2009-08-25
Hey, thanks for your reply. Do you think is the switch, but in server side, or the client? If client, doesnt make sense, because i can connect to another server. And if server, no sense either. There are several VMWares on that server, and all of them running different types of servers ok. Only VNC cant connect.

---

### Post by HermanAB on 2009-08-25
In that case, it sounds more like a server firewall issue with the VNC port.

---

