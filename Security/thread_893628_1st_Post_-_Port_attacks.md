---
title: "1st Post - Port attacks?"
date: 2008-08-18
forum: Security
---

### Post by Nymrod on 2008-08-18
Thank you ahead of time if you are able to help me.  I tried searching but I'm not sure what I'm looking for.  On to my issue.

I started having issues with my connection locking, forcing me to hard reset my router.  I called the ISP and everything checks out ok. In the process they had me connect my modem directly to my PC, and Firestarter lit up like a Christmas tree.  There is a private IP going port to port (being rejected of course) showing up in the blocked connections tab.

My very newbie theory is that once they hit a port I am using, it is causing my connection to lock.  I went under outgoing and banned the IP from connections.  I guess I have two questions.

#1:  If I at some point opened a port via firestarter then removed the rule, did that port automatically close?

#2:  Is there anything I can do about this and is it a security threat?

Thank you again for any input.  I run 8.04 and all updates have been installed.

---

### Post by cdenley on 2008-08-18
Firewalls are kind of pointless for a typical desktop user. Even if you allow all traffic through the firewall, if you don't have any process listening on that port, the connection will get rejected anyway. It's not really a security risk unless you installed something like samba or openssh-server.

What do you mean "private" IP address? You shouldn't get any connections from unroutable IP's directly from your modem. It is typical to get random port scans, though.

---

### Post by Nymrod on 2008-08-18
Ok well the only thing I ever remember with the name "Samba" was something in the auto-updates, which I always install.  I ran a port scan under "Network tools" and it showed only port 80 open.  I also ran the netstat for system services and it came up with 3 ports (68, 54248, 5353) with the UDP protocol but does not list the service.

I know I don't need a firewall but I play games through wine so I still run a virus scanner from time to time.  I guess I just want to make sure that I'm not at risk and the fact that I have to reset my router constantly now after reinstalling all the firmware is kind of boggling.

Ty for the reassurance.

---

### Post by cariboo on 2008-08-19
Are you running a web server? Port 80 should only be open if you are running  some sort of web server. In a bone stock installation the only port that should show up in a port scan is 631, and that really isn't open as by default you can only access it from localhost.

I would also suggest not using the scan tool in Network Tools as it gives false positives see bug [#257042 @ launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042")

I use nmap to do port scans. There are graphical frontends for nmap available if don't like using the command line.

Nmap and zenmap are available in the repositories and you can use Add/Remove Programs, Synaptic Package Manger and of course the command line to install them.

Jim

---

### Post by Nymrod on 2008-08-20
I installed nmap and it still shows Port 80 open, service is http.  If I use ufw to close this, will it prevent internet access from my PC?  This is just a personal computer, basic install of 8.04.

---

### Post by cdenley on 2008-08-20
Filtering port 80 with UFW will prevent people from using the web server you are apparently running. Are you scanning your WAN IP or LAN IP? Are you using your router again? If you want to see exactly what's running on port 80 (probably apache, not installed by default)
```

sudo lsof -n -i :80

```

---

### Post by timcredible on 2008-08-20
> **cdenley said:**
> Firewalls are kind of pointless for a typical desktop user. Even if you allow all traffic through the firewall, if you don't have any process listening on that port, the connection will get rejected anyway. It's not really a security risk unless you installed something like samba or openssh-server.

ditto
> 
What do you mean "private" IP address? You shouldn't get any connections from unroutable IP's directly from your modem. It is typical to get random port scans, though.
well.... some programs do not put their real ip addresses in the source field, so that firewalls won't block them.  seems counter intuitive not to be able to get packets back, but the programs are guessing at what the target pc is going to do, and sends a string of packets in order to break in or get the target to open another port, etc.

---

### Post by Nymrod on 2008-08-20
I'm behind my router again.  I adjusted the MTU setting on the router and in my network interfaces config file to try to stop the dropping connection issue.  I don't run any kind of web server, I don't know why port 80 is open.  I tried using ufw to remove the allow 80/tcp but it is still there.  Is firestarter somehow keeping this port open?

I know this is overboard for a personal use only desktop, but I like my information to be protected.  Is there any way to close this, or is it even needed?

---

### Post by brian_p on 2008-08-20
> **Nymrod said:**
> I installed nmap and it still shows Port 80 open, service is http.

Please give the exact command you typed. What was the complete output?

Also the output of the command cdenley gave you would be useful.

---

### Post by cdenley on 2008-08-20
> **Nymrod said:**
> I'm behind my router again.  I adjusted the MTU setting on the router and in my network interfaces config file to try to stop the dropping connection issue.  I don't run any kind of web server, I don't know why port 80 is open.  I tried using ufw to remove the allow 80/tcp but it is still there.  Is firestarter somehow keeping this port open?

I know this is overboard for a personal use only desktop, but I like my information to be protected.  Is there any way to close this, or is it even needed?

If nmap says the port is open on your computer, then there is a process listening on that port. You could just use a firewall to block anyone from using it, but the best approach is to find out what is listening on that port and remove it. I already posted the command to identify what it is. Assuming it is apache, I believe this command will remove it.
```

sudo apt-get remove apache2.2-common

```

---

### Post by Nymrod on 2008-08-20
I downloaded knmap the gui for nmap because I am fairly new to Linux and I haven't used text based commands since DOS so I don't want to accidentally do something.  I ran the port scanner with the --allports and default options getting this output.

/usr/bin/nmap -T Normal --allports 192.168.1.1 

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-20 06:30 HST
Interesting ports on 192.168.1.1:
Not shown: 1713 closed ports
PORT   STATE SERVICE
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 2.344 seconds

I tried removing apache but it says it is not present, and I tried the sudo lsof -n -i :80 command but I didn't get any output.  I tried just doing sudo lsof but I didn't see anything that said 80.  I then tried that command without :80 and got these results.

COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
dhclient3 4066  dhcp    4u  IPv4   7272       UDP *:bootpc 
avahi-dae 5281 avahi   14u  IPv4  13117       UDP *:mdns 
avahi-dae 5281 avahi   15u  IPv4  13118       UDP *:50765 
cupsd     5418  root    2u  IPv4  13309       TCP 127.0.0.1:ipp (LISTEN)

I just want to figure out why this port is open, and close it.  Is there any other way to do this because using ufw to deny the port still left it open.

Appreciate all the help, I know me being a rookie doesn't make things easy.

Edit:  I got the sudo lsof -n -i :80 command to work and got this output (username changed obviously).  I was viewing this site when I entered the command.

COMMAND  PID     USER   FD   TYPE DEVICE SIZE NODE NAME

firefox 7105 Randomuser   43u  IPv4  26651       TCP 192.168.1.100:32968->66.11.119.69:www (ESTABLISHED)

firefox 7105 Randomuser   51u  IPv4  28561       TCP 192.168.1.100:49115->209.73.191.242:www (CLOSE_WAIT)

firefox 7105 Randomuser   53u  IPv4  26673       TCP 192.168.1.100:46110->72.246.102.10:www (ESTABLISHED)

---

### Post by cdenley on 2008-08-20
You scanned your router (192.168.1.1). It is probably running a web server for configuration. If you go to [http://192.168.1.1/](http://192.168.1.1/) you will probably get a login prompt. Your computer is not listening on that port, your router is.
```

nmap 192.168.1.100
nmap 192.168.1.1

```

The first output of the lsof command confirms you have no processes listening on port 80, which means it isn't open on your computer. The second output simply shows the http connections you have opened to websites since that command lists listening connections and established connections. As far as I can tell, you have nothing to worry about.

---

