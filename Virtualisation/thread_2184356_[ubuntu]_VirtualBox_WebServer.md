---
title: "[ubuntu] VirtualBox WebServer"
date: 2013-10-28
forum: Virtualisation
---

### Post by daniel.fazio.92 on 2013-10-28
Hi everyone i'm new to this world!
I'm a Windows's User and i want/need to install my localserver into my UbuntuServer VirtualBox.
I'm trying to figuring out how to make my Host and my Guest to comunicate.
On the port forwarding's option of the VB i've setted up the Host port 8080 to the Guest 80 for the HTTP, and the 2222 to the 22 SSH (also tryed from the .xml file).
Like this I cant connect to SSH with putty and if i go to localhost:8080 nothing happens. 
I've tryed the NAT configuration and at least my Guest can connect to the Internet.
I've tryed with the Bridge or Host connection and i can connect to the Guest's IP to connect by SSH or or see the webserver's root (localhost), but my Guest cant connect to the internet so i cant install or update stuff.
Is there a solution to all this? 

Also i have a "strange" problem that i never seen before. when i 'sudo /etc/init.d/networkin restart(or other option)' It say "ERROR: calling a sysvinit script on a system upstart isnt supported. use the service command instead" i used that command without problems on a ubuntu machine just 5 mins before(which i deleted to create a new 64bit one). So i tryed to install again a new 32bit one and the error was there again. I installed a new 64 bit one and still the error

---

### Post by CharlesA on 2013-10-29
Why not just set up networking as bridged so the VM gets an ip from the host network?

As far as /etc/init.d/ goes, just use service serviename start|stop|restart|etc

If the guest isn't connecting to the internet, have you tried:

Ping localhost
ping hostname
ping router/gateway
ping another host on the same nework
ping [www.google.com](www.google.com)

---

### Post by TheFu on 2013-11-03
a) which Ubuntu are you running?  It matters.
b) which Windows are you runnnig? It matters.
c) I use bridged network connections. Then the host and client see each other as network peers. A server will need a static IP, so after installation, set that up - dont leave it with DHCP.  This removes all the fancy tunneling that isnt needed. Remove all VB forwards.
d) Did you allow the windows firewall access to the guest VM?

Virtualbox is fine for developers, but if you want to run a real server, look into server virtualization. It is faster, more stable and more like the real server you will use at deployment.
```
sudo /etc/init.d/networking restart
```
is the command that works on 12.04 LTS. Notice the exact spelling - if you use tab-completion, there shouldnt be any question, but it is impossible to tell in a forum post if you did or just mistyped it here.

If you are running a server, THAT is the version you should be on. Servers = LTS releases. See my signature for more about that.

Besides that Charles knows his stuff. A reply that you have tried these things would be appreciate.

---

