---
title: "help with setup for beginner please"
date: 2011-10-02
forum: Server Platforms
---

### Post by moletteuk on 2011-10-02
I've bought an hp proliant n36l microserver, I want to use it for storage & backup for the other (windows) PCs in the house and as a Squeezebox server.
I've bought 2 WD 2TB EARS hard drives to go along with the 250GB hard drive that came with it. I don't need RAID.
 
I've installed ubuntu server 11.04 and chosen samba file server at the end.
 
What do I do next?
 
I've been following some instruction on the squeezebox slimdevices forum, which say to add Webmin next, but am stuck at the point where I type in the web address for webmin on the source list, can't figure out how to save and exit.
 
Anyway, do I really want Webmin, or would something else be better?
 
How do I sort out the network?
 
Does anyone know of an idiot's guide for this type of setup?
 
Help please!

---

### Post by headvampyre@hotmail.co.uk on 2011-10-02
What text editor are you using?
For VI, just use CTRL+[ then type :wq and press enter.
And isn't webmin already in the repo's?

---

### Post by moletteuk on 2011-10-02
I used nano.
I've got webmin installed now.  I hit the problem of not being able to login but I did the following fix:
- sudo find / -name changepass.pl
(normal path /usr/share/webmin)
- cd /usr/share/webmin
- sudo find / -name miniserv.conf
(normal path /etc/webmin/)
- sudo ./changepass.pl /etc/webmin/ root typeyourpasswordhere

Is this OK, or have I compromised security? It seems to login in now without asking for login & password.

---

### Post by headvampyre@hotmail.co.uk on 2011-10-02
Your gonna want to set a password, but now you can login, change it via webmin, and if your really concerned about security, configure it to use HTTP+SSL.

---

### Post by moletteuk on 2011-10-02
Thanks, I'll come back to that, I've got a new problem now.
I'm trying to manually set the ip address.
I've followed a tutorial, put my best guess at the numbers I need (!), removed the dhcp3, restarted networking and end up with some dodgy messages.
 
Running /etc/init.d/networking restart is depracated because it may not enable again some interfaces
Reconfiguring network interfaces...
/etc/network/interfaces:11: interface eth0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
then last two lines repeated but with ifdown replaced with ifup
 
???

---

### Post by eric_1982 on 2011-10-02
Can you take a look at your settings for your network card.

This article has some really simple steps on setting a static IP address on Ubuntu: 

[http://mixeduperic.com/ubuntu/how-to-set-a-static-ip-address-on-a-ubuntu-server.html](http://mixeduperic.com/ubuntu/how-to-set-a-static-ip-address-on-a-ubuntu-server.html)

---

### Post by moletteuk on 2011-10-03
Thanks, OK, I've tried setting up the static IP address again, but I've got the same result.
This is exactly what I did:
sudo nano /etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.2.5
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
 
sudo nano /etc/resolv.conf 
name server 192.168.2.5 (I changed 1 to 5 for server address)
 
sudo apt-get remove dhcp3-client
package dhcp3-client is not installed so not removed
 
sudo apt-get remove dhcp-client
virtual packages like dhcp-client can't be removed
 
sudo /etc/init.d/networking restart
 
Still not working with same message as before.
This time when I went into the network config bit, there was nothing there, no iface eth0 inet dhcp or anything.
 
???

---

### Post by moletteuk on 2011-10-03
OK, I've gone back into sudo nano /etc/network/interfaces
It was showing iface eth0 inet dhcp as well as iface eth0 inet static, so I removed the static one.
 
Redone everything else and now am only getting part of the dodgy message:
 
Running /etc/init.d/networking restart is depracated because it may not enable again some interfaces
Reconfiguring network interfaces...
 
Still not working, I can't access webmin from my laptop over the network.
 
??

---

### Post by moletteuk on 2011-10-03
I've now tried the start/stop command:
 
sudo /etc/init.d/networking stop; sudo /etc/init.d/networking start
 
getting the following message:
*deconfiguring network interfaces...
Rather than invoking init scripts through /etc/init.d, use the service (8) utility, e.g. service networking start
 
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility e.g. start networking networking stop/waiting
 
???
Please help before I make this any worse!
 
....now I've tried sudo start networking and it says:
networking stop/waiting

---

### Post by viperce on 2011-10-03
nano /etc/resolv.conf
nameserver 192.168.2.1 if that is your routers IP 

ifconfig and post results please

---

