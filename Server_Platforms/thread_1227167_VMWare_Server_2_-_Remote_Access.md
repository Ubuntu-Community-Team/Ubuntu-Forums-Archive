---
title: "VMWare Server 2 - Remote Access"
date: 2009-07-30
forum: Server Platforms
---

### Post by lmlypfan on 2009-07-30
I have VMWare Server2 installed on my ubuntu machine at home. 
I've forwarded ports 8333 and 902 to my ubuntu server. 
These are the ports that VMWare server uses for the web interface. 

Is there a more secure way to launch and manage VM's remotely?

Thank you

---

### Post by Macchi on 2009-07-30
Nomachine NX provides a remote graphical desktop through an encrypted and compressed communication channel (ssh), thus safe and efficient. 
Their free version (as free beer) is limited to two users. Virtual machines can be accessed as if they were local through communication channels that are quite slow and have long latency.

---

### Post by samosamo on 2009-07-31
This is a very bad idea. I think you know this already since you posted here for help. If you want to access insecure services on a firewalled network you need to setup a VPN.  Most people here will tell you to use OpenVPN.  Now hurry and roll back the changes on your port forwarding config before someone scans your ISP and cracks you wide open.

---

### Post by lmlypfan on 2009-07-31
I figured it was a bad idea. The remote administration worked really well, but I knew it was a security risk. 

I have rolled back the configuration. I have remote access via SSH, i'm going to try this tutorial i found.

Tunneling VMWare Server over SSH with PuTTY

[http://www.brendonmatheson.com/2008/02/06/tunneling_vmware_server_over_ssh_with_putty.html]("http://www.brendonmatheson.com/2008/02/06/tunneling_vmware_server_over_ssh_with_putty.html")

---

### Post by Macchi on 2009-07-31
The tutorial that you have mentioned seems to be for Windows but you may apply the same method on Ubuntu. Search the wiki for ssh tunnelling.

I repeat that if you want to have a safe an efficient remote desktop access to your host server or to your virtual machines in a couple of minutes then you shoult look at freenx.

PS: Yes, it is very unsafe to open ports to the internet without suitable protection mechanisms.

---

