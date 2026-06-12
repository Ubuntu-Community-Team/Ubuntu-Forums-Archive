---
title: "Cannot connect from Ubuntu system to other Ubuntu system in VM using a bridge."
date: 2014-04-22
forum: Virtualisation
---

### Post by Bobby_James on 2014-04-22
Hello,  

I am trying to transfer files from my Ubuntu system 12.04 to my other Ubuntu system 12.10 which is running in VirtualBox.  

I try: sftp linux@192.168.1.13 when linux is the name of my system in the VM and 192.168.1.13 is its IP.  

I have set up the VirtualBox Manager 'Network' setting to show: Bridged Adaptor on wlan0.  I have also tested this on eth0 but this does not connect to the router (no IP address). 

 When I sftp (on my system on 192.168.1.11) I get: sftp linux@192.168.1.13 ssh: connect to host 192.168.1.13 port 22: Connection refused Couldn't read packet: Connection reset by peer  

The brctl show command displays: bridge name    bridge id        STP enabled    interfaces  

In other words, there are apparently no bridges.   

Does anyone know how I can rectify this?  Thanks!

---

### Post by jdeca57 on 2014-04-23
First, a way around: Virtualbox has shared folders and that works perfectly. You just put the content in the shared folder and both machines can access it.
Then, the bridge problem. I assume both machines reach the Internet and that the connections are OK. Still, an easy way to check is ping.
If both machines can see each other with ping there are two questions remaining:
- did you use a firewall? (standard ufw closes ssh)
- more importantly, is the ssh deamon ruhning? Standard Ubuntu doesn't include an ssh server, see: [https://help.ubuntu.com/12.04/serverguide/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/openssh-server.html)

---

### Post by Bobby_James on 2014-04-23
Problem solved, thanks.  I had not installed the SSH deamon in the VM Linux.

---

