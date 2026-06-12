---
title: "Cannot connect to server outside home firewall"
date: 2010-02-10
forum: Server Platforms
---

### Post by TheProphet92 on 2010-02-10
I get a connection refused error whenever I try and connect to my home server from outside my network through SSH.

While connected to my home network (same network as server) I can SSH and connect via HTTP (PHP installed and working) with no problem, but when I'm on a different network it refuses the connection (SSH) or acts as a broken link (HTTP).

I've set up port forwarding on my router to forward ports 22 and 80 to the IP of my server, and set up one of those free DynDNS domain names which, again, works perfectly fine while at home. I can connect via SSH, typing in the server's IP (192.168.1.6) into a browser, typing in my IP into the browser (which is dynamic, hence the DynDNS), or by going to the free DynDNS domain name I set up. Outside of my home network, none of them work.

I'm guessing there's something really obvious I'm overlooking here, but I can't figure out what it is. :-|

---

### Post by gobbledigook on 2010-02-10
> **TheProphet92 said:**
> I'm guessing there's something really obvious I'm overlooking here, but I can't figure out what it is. :-|

as long as you have port 22 forwarded to port 22, you should be able to ssh in...!! however it would prob only work with the external ip of your connection. navigate to [**here**]("http://network-tools.com/") from inside your local network, it will show you your external ip - and pop that into your terminal/putty and ssh to that address from outside your network.

---

### Post by userkiller on 2010-02-10
> **gobbledigook said:**
> as long as you have port 22 forwarded to port 22, you should be able to ssh in...!! however it would prob only work with the external ip of your connection. navigate to [**here**]("http://network-tools.com/") from inside your local network, it will show you your external ip - and pop that into your terminal/putty and ssh to that address from outside your network.

Also make sure you have the ssh-server install.

---

### Post by TheProphet92 on 2010-02-11
I've got ssh-server installed and the ports should be forwarded fine.

If I'm on my home network and enter my external IP address into a browser, it connects without any problem. If I'm anywhere else and enter that same external IP address, it doesn't work :/

I'm using a Netgear WGR614 v9 router, if that helps.

---

### Post by joberly on 2010-02-11
If you are INSIDE your network, even if you use your external IP, it will still map to your INTERNAL ip address. You need to be physically outside of your network in order to resolve the external IP.

Seems as though this is a port forwarding issue, if it works inside the network. Are you running iptables, or just firewall software on the router? What's your setup like?

---

### Post by drave on 2010-02-12
you need to establish whether its the router or the pc thats rejecting the connection. is there anything in the sshd log showing a reject or any sort of logging in the router ?

---

### Post by Porter200el on 2010-02-12
Sounds like the port forwarding is not working, if ssh server is installed correctly, it is almost definitely on the router.  Do you have a static ip for your server locally?

---

### Post by TheProphet92 on 2010-02-18
Ok, I've sort of figured out what's going on now.

I can SSH into my home server if I'm using my laptop tethered to my friends 3G phone, but I get a connection refused error if I try to SSH from my laptop connected to my school's wifi. 

Another thing of interest is that http (port 80) still doesn't work, no matter where I connect from (as long as I'm outside my network). Works fine inside my network, port forwarding is set up exactly the same as it is for port 22.

Is it possible to use SSH through a port other than 22? How would I go about using this? Any theories about http not working?

---

### Post by KnottyMars on 2010-02-18
> **TheProphet92 said:**
> Ok, I've sort of figured out what's going on now.

I can SSH into my home server if I'm using my laptop tethered to my friends 3G phone, but I get a connection refused error if I try to SSH from my laptop connected to my school's wifi. 

Another thing of interest is that http (port 80) still doesn't work, no matter where I connect from (as long as I'm outside my network). Works fine inside my network, port forwarding is set up exactly the same as it is for port 22.

Is it possible to use SSH through a port other than 22? How would I go about using this? Any theories about http not working?

I use shorewall as my firewall on the server. You can specify the services in the rules. I think one of the other posters asked if you saw any connection attempts in the auth.log file. 

That is a good place to start. Cant really help with using non standard ports, sorry. But I agree that it sounds like a port issue. in most routers you should be able to turn off its firewall protection for a single IP (mine does at least). If you can do that, even just to test, that would tell you if your school network is blocking or your router is blocking. 

If you see attempts within your auth.log file, the reason should be listed there. 

I noticed sometimes that if I was attempting to connect via SFTP and there was no home directory specified, it wouldnt let me connect. Once I made a folder in /home/[username] it worked. 
Shell access should prompt a login so you would know immediately if you werent able to connect. Good luck

---

### Post by joberly on 2010-02-18
Port 80 is probably blocked by the ISP (whoever it is, the school, or some other ISP you may use). You can try running the webserver on another port to see if it connects. This is assuming your webserver is up and running.

/etc/init.d/apache2 status
 *if you're using apache.

As far as SSH on another port, it's in your /etc/ss/sshd_config file.

---

