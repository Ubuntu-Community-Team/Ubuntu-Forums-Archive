---
title: "How can I find out my IP address from the command line?"
date: 2010-08-09
forum: Server Platforms
---

### Post by evenstar7139 on 2010-08-09
I have Windows 7 but I'm running Ubuntu 10.04.1 LTS on virtual box. I have a program called SQLyog installed on Windows 7 and I want to connect to my MySQL database that's in Ubuntu. What would I put for the address? Localhost doesn't work (I figured it wouldn't).
 
Also: I don't have a GUI. Just command line.

---

### Post by CharlesA on 2010-08-09
**ifconfig ** would tell you what yer IP address is.

Make sure you are using bridge networking in VirtualBox as well.

---

### Post by Queue29 on 2010-08-09
If you are looking for your external I.P. 

```
wget www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null
```

---

### Post by evenstar7139 on 2010-08-10
> **Queue29 said:**
> If you are looking for your external I.P. 
 
```
wget www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null
```
 
How can I copy and paste that command into Ubuntu?
 
Sorry, I'm a Linux newb.

---

### Post by Xeora on 2010-08-10
on my headless I have it wired in (so for me it's eth0)

```
ifconfig eth0
```
results in
```

eth0      Link encap:Ethernet  HWaddr 00:19:21:8a:d8:e3  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe8a:d8e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41562970 (41.5 MB)  TX bytes:197617351 (197.6 MB)
          Interrupt:19 Base address:0xd400

```

inet addr: XXX.XXX.XXX.XXX is what your looking for, in my example is' the output of the second line

your connection may be different and ifconfig will show all the available connections (wlan0 for instance is one possible wireless connection interface)

Good luck.

---

### Post by evenstar7139 on 2010-08-10
Hmm...I did the "ifconfig" thing earlier (that's all I type) and it gave me something very similar to that.
 
I tried giving that IP address to SQLyog but it just said it couldn't find the MySQL server...
 
How can I be sure my virtual ubuntu server can be reached over the internet?
 
(btw MySQL is installed and I've used it)

---

### Post by nmaster on 2010-08-10
ifconfig will tell you the IP address within the LAN.  if you want your public IP address then you need to do what queue29 says. 

how do you copy and paste it?...since you only have a cli installation, you might just want to re-type it.  you could also add an alias, so you don't have to type it everytime.  check this out to learn about how to do that: [http://ubuntuforums.org/showthread.php?t=89732](http://ubuntuforums.org/showthread.php?t=89732)

---

### Post by spynappels on 2010-08-10
Are you accessing the MySQL DB from another machine? You need to make sure that the MySQL user has acess privileges from other hosts.

If a user only has access privileges from localhost, then attempts to access from another host will also fail.

---

### Post by CharlesA on 2010-08-10
What networking mode are you using in VirtualBox? The default is "NAT" which makes it hard for other machines to connect to any Guest OS.

---

### Post by richardjh on 2010-08-10
OK, just want to add one here that I use because it is very useful to get JUST THE IP without all the other HTML.

From the command line ( Applications > Accessories > Terminal )

```
curl icanhazip.com
```

It is a website set up by [Major Hayden]("http://rackerhacker.com/") which returns just the IP specifically so you can use it in scripts.

Or if you want a GUI way use Firefox ( Applications > Internet > Firefox ) and visit

```
http://icanhazip.com/
```

---

### Post by MasterGamerJK on 2010-08-10
you could always just ping something, or maby create a pcap of your traffic with "tcpdump"

---

### Post by fro1269 on 2010-08-14
> **evenstar7139 said:**
> How can I copy and paste that command into Ubuntu?
 
Sorry, I'm a Linux newb.

If I need to copy and paste into cli I just SSH in, otherwise you can just type it out manually :)

---

### Post by credomane on 2010-08-14
Ok from reading your post your VirtualBox setup is this:
HOST: Windows 7
GUEST: Ubuntu Lucid 10.4.1 (cli-only)


By default VirtualBox creates the network connection between the host and guest as a NAT. This allows the guest to talk to anyone that the host can but not the other way around. What you need to do is shutdown your guest then open up the VirtualBox "manager", the piece you can see all your VM's from and change their settings. From there right click your guest vm and click "settings". Once that window open click on "network" and change adapter one from NAT to Bridged Adapter. Under name make sure that adapter listed there is the one you want to "bind" your guest too. Might only be one listed there and that is fine. Now click ok and start the guest back up. Once the guest is up again, login, and type ```
ifconfig eth0
```

This will get you a different IP than what you got before. Put this ip into your SQLyog program. If it still fails it looks like you haven't setup MYSQL on the guest to accept connections on any interface but "lo". Which is the default in Ubuntu and probably the MySQL default period.

On the guest you have to edit /etc/mysql/my.cnf to bind to eth0 so that SQLyog can talk to the mysql server.
Still on the guest type ```
sudo nano +52 /etc/mysql/my.cnf
```
the +52 should put you on the starting with "bind-address". If not it should be close. the default line looks like this ```
bind-address = 127.0.0.1
``` to change the mysql to accept connection on all interfaces change it to ```
bind-address = 0.0.0.0
```
This will tell MySQL to bind to all interfaces. I'm pretty sure this will be lo (127.0.0.1) and eth0 which is what we want.
Save the file with ctrl+x
Once you are back at the console type ```
sudo service mysql restart
```
Now once the server finished restarting SQLyog on the host system should be able to connect to the MySQL server in the Ubuntu guest OS.

A word of **_warning:_** this setup change to the mysql server is technically a security risk. This is because ANYONE can now connect to your MySQL server and attempt to brute force the username/password on it.

---

### Post by AlphaLexman on 2010-08-14
My favorite (for an external IP) is ->
```
curl ifconfig.me
```You have to have 'curl' installed, it's not by default, but in the repo's.

---

### Post by bodhi.zazen on 2010-08-15
> **AlphaLexman said:**
> My favorite (for an external IP) is ->
```
curl ifconfig.me
```You have to have 'curl' installed, it's not by default, but in the repo's.

Nice one =)

---

### Post by prakshina on 2013-01-25
> **evenstar7139 said:**
> I have Windows 7 but I'm running Ubuntu 10.04.1 LTS on virtual box. I have a program called SQLyog installed on Windows 7 and I want to connect to my MySQL database that's in Ubuntu. What would I put for the address? Localhost doesn't work (I figured it wouldn't).
 
Also: I don't have a GUI. Just command line.

  To find your ip address , type the command " ipconfig" in windows command prompt or type the " ifconfig " / " sudo ip addr show" in Ubuntu terminal. Then it displays your internal ip address . The internal ip address is same in both the Ubuntu and windows . You can use the internal ip address to connect with Mysql database. If you want to know your external ip address visit the site [Ip-details.com]("http://www.ip-details.com/")   .  Command line is enough to know your ip address. :p

---

