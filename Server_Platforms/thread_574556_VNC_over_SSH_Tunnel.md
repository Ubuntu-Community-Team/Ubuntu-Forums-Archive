---
title: "VNC over SSH Tunnel"
date: 2007-10-12
forum: Server Platforms
---

### Post by ddcc on 2007-10-12
I've set up the openssh-server, x11vnc, and vnc-common on a remote computer that I want to vnc into through ssh, however, every time I try vncviewer -via 192.168.1.110 192.168.1.110:0, after logging in to the remote ssh server I get 
"channel 3: open failed: connect failed: Connection refused" and ReadFromRFBServer: rdr::EndOfStream, which closes vncviewer. I've got firestarter on both remote and local machines, however, I've permitted connections the other host on each machine yet it still doesn't work. What's odd, is if I setup the tunnel manually (ssh -L 5900:127.0.0.1:5900 192.168.1.110 and then vncviewer 127.0.0.1:0) the connection works, as well as if I use putty and vncviewer in Windows. Any ideas why vncviewer just fails?

---

### Post by HermanAB on 2007-10-13
Try "vncviewer localhost" after logging in with SSH.

---

### Post by ddcc on 2007-10-13
I'm not sure if you've misunderstood my issue, but it's that vncviewer -via 192.168.1.110 192.168.1.110:0 doesn't work right but establishing the ssh tunnel and manually vncviewer 127.0.0.1:0 works.

---

### Post by HermanAB on 2007-10-14
Yes, once the tunnel is up, you can connect to the local machine localhost address and the requests will be tunneled to the remote machine, as if you are logged into the remote machine.

If you first do SSH, then you are connected to the remote machine and then you can vnc to the localhost of the remote machine (since you are already there).

Anyway, to debug these connection issues and see where the VNC server is listening, run a nmap scan, then use telnet to look for the server banner:
telnet ipaddress port
telnet 127.0.0.1 5900
telnet 192.168.1.110 5900
and the server should respond.  

If it doesn't, then it is either not listening on that address and port, or you have a firewall problem with iptables or tcpwrappers hosts.allow.

---

