---
title: "problem connecting to server over lan"
date: 2010-10-03
forum: Server Platforms
---

### Post by shanep-server on 2010-10-03
I installed a fresh copy of Ubuntu server 10.04 and installed vsftpd and openssh server. However I can't connect to either of these services. vsftpd can't connect... it doesn't recognise my host name or ip address. when I try to putty into openssh It just hangs and never gives me an option to login. I don't have firewall going... that i'm aware of... haven't enabled ufw. So unless there is something i'm missing from a fresh install i'm mind boggled as to why it won't allow me to connect to anything.

---

### Post by sanderj on 2010-10-03
On the Ubuntu server 10.04, can you successfully "ssh localhost"?

If so, on the same machine, can you successfully ssh to it's LAN IP address?

---

### Post by shanep-server on 2010-10-03
Ok i can connect too ssh from server... ssh localhost... I was able to connect via laptop ssh "ipaddress" without specifying port number... but when i try to connect via win7 + putty... still no go. I'm going to try to connect via Vista partition + putty on my laptop

---

### Post by sanderj on 2010-10-03
Maybe a Windows (firewall) problem?

---

### Post by shanep-server on 2010-10-03
I tried to connect via absolutetelnet on my vista laptop and keep getting 

connecting to 192.168.2.2:22
  attempting 192.168.2.2:22...   Failed: Timed Out 
Connect to 192.168.2.2 failed. Winsock Error: Timed Out

Putty times out on both win7 and vista... but I connected with xubuntu terminal by : ssh 192.168.2.2 

I logged in... I have disabled all firewalls on both win7 and vista with the same results... and Nothing can connect to FTP

---

### Post by sanderj on 2010-10-03
From the Windows machine, can you succesfully *ping* the Ubuntu machine?

If not, it's a network problem, not a SSH problem. Start by checking the IP address on the Windows machine, for example by typing "ipconfig"

---

### Post by kulshoks2121 on 2010-10-03
Either the port your SSH server uses is blocked or you just cant ping the ssh server

---

### Post by shanep-server on 2010-10-03
well isn't that funny... I'm a little confused... 

I was using a Belkin wireless router on the win7 machine... once I switched things over so both win7 and server were on cat5 cables... I can ping the server and ssh worked without a problem. It has to do with the wireless ssh connection I would guess... That doesn't explain how I could connect via laptop wirelessly on xubuntu but failed on vista... I tried to connect on vista with all firewalls avg spybot disabled... and its still failing. What settings in router/server could possibly be making wireless ssh connections fail in windows?

---

### Post by shanep-server on 2010-10-03
now i'm getting a different response when trying to connect to FTP "vsftpd" on server from FileZilla... 

Connecting to 192.168.2.2:20...
Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error: Could not connect to server

---

