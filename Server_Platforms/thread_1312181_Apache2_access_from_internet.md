---
title: "Apache2 access from internet"
date: 2009-11-02
forum: Server Platforms
---

### Post by NeoShade on 2009-11-02
I have ubuntu Server x86 9.10 installed with LAMP/ftp/ssh.

I am able to connect to ftp and SSH from the outside world using my outside ip or dyndns domain name. Apache though, will not work.

I can connect to the server on my LAN (192.168.1.5) from any computer on my lan.

I have port 80 forwarded to 192.168.1.5 along with 20-22 ( and ssh and ftp work fine.)

The server is running (I can connect on LAN).

What should I do now? I have a mobile to check the site on, and vpn connections.

Do I need to add anything to hosts/host.allow/resolv or anything? I should have done everything that I need to do!

---

### Post by Barriehie on 2009-11-02
What are you finding in the apache log file???

Barrie

---

### Post by NeoShade on 2009-11-03
The logs do not show connections from the outside world, but do show the local lan connections in access.log

error.log just shows when the server rebooted, and thats about it.

I did a nmap just now and noticed something interesting.

nmap 127.0.0.1
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
111/tcp open  rpcbind
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

nmap 192.168.1.5
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
111/tcp open  rpcbind
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

nmap OUTSIDE IP
PORT      STATE    SERVICE
21/tcp    open     ftp
22/tcp    open     ssh
80/tcp    open     http
135/tcp   open     msrpc
139/tcp   open     netbios-ssn
445/tcp   open     microsoft-ds
1720/tcp  filtered H.323/Q.931
2869/tcp  open     unknown
5357/tcp  open     unknown
5801/tcp  open     vnc-http-1
5901/tcp  open     vnc-1
49152/tcp open     unknown
49153/tcp open     unknown
49154/tcp open     unknown
49155/tcp open     unknown
49156/tcp open     unknown

(the other ports are my other boxes and such doing stuff)

This looks like it sees the port 80 being open correct?

It gets better.

If my server is down and I do an online scan ([http://www.t1shopper.com/tools/scan.php4](http://www.t1shopper.com/tools/scan.php4))
I get xxxx.dyndns.org is not responding on port 80 (http).

I boot my server,

neoshade.dyndns.org is responding on port 80 (http).

---

### Post by NeoShade on 2009-11-03
Ok, I got it figured out. OpenDNS.

I set my router to use OpenDNS a while back. I told it to get DNS from my ISP, rebooted the router, and I can now access my http site!

i wonder why opendns wasn't letting this work?

---

### Post by Vegan on 2009-11-03
I have BIND9 on my machine to provide basic secondary DNS services.

---

### Post by cariboo on 2009-11-03
The problem with having bind set up on your server is that the rest of the world can also use your servers for dns. This can run into problems if you have a bandwidth cap, and you go over the limit.

How many times have we seem a web site that isn't accessable, because they've exceeded their bandwidth cap.

---

