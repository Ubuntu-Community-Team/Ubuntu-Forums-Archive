---
title: "FTP Server Issues with Router"
date: 2011-01-29
forum: Server Platforms
---

### Post by Skrypt on 2011-01-29
Hi all,

I've got a router running tomato 1.28. FTP tests from ftptest.net only connect if I enable and point the DMZ to the computer running the server (192.168.1.102). No other settings need to be changed for the FTP work, but obviously I don't want the server running on a DMZ. I can't figure out what the problem is.

I have the server set to listen on port 5025 and 5000 to 5050 (UDP and TCP) are forwarded to 192.168.1.102. An exception added to the firewall. 

The FTP's passive mode settings are are set to not use the external IP for local connections and to use the custom port range 6000-7000 (and those ports are forwarded in the router).

Ultimately, I'd like to use FTPS so I've forwarded ports 990-992, but I won't bother with that until I can get the basic stuff working.

I guess this is the wrong forum since it's a router/tomato issue, but there's not really a helpful community behind either.

Any idea where I'm going wrong?

---

### Post by HermanAB on 2011-01-30
Howdy,

FTP uses random ports.  The initial connection is on the 'FTP' port, the data is then transferred on a high port.  To make it work through a router, you need to use a 'FTP Tracker', or put it in a DMZ.  

However, the best solution is not using FTP at all.  Rather use SSH, scp and SFTP over port 22.

---

