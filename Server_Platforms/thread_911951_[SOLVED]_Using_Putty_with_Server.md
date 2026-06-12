---
title: "[SOLVED] Using Putty with Server"
date: 2008-09-06
forum: Server Platforms
---

### Post by grs on 2008-09-06
I've beening having trouble getting Putty to connect to Ubuntu Server from my Windows XP PC. At first I thought it was the network, but that seems to be working fine.
Could not be connecting because for the sudo command that has to go before everything on Ubuntu Server?
Any ideas on how to connect putty to the server?

---

### Post by windependence on 2008-09-06
how are you connecting? You should be doing:

[email]user@xxx.xxx.xxx.xxx[/email]

You should not be trying to connect as root, that won't work. Use your user account and sudo after you get signed on.

-Tim

---

### Post by grs on 2008-09-06
Under host name/ip, I had been just typing in the IP of the ubuntu server on port 22, via SSH. When I tryied connecting it says connection refused. Should I have something setup on the server to recieve it?

---

### Post by windependence on 2008-09-06
Yes, you need to install OpenSSH server before you can do this.

```
sudo apt-get install openssh-server
```

Hope this helps.

-Tim

---

### Post by grs on 2008-09-06
The open ssh server guide from here

[https://help.ubuntu.com/8.04/serverguide/C/remote-administration.html](https://help.ubuntu.com/8.04/serverguide/C/remote-administration.html)

is all I need, right?
The little experience I've had with linux, this must have been setup automatically at install.

---

### Post by windependence on 2008-09-06
Once you install, you should be able to connect without tweaking anything.

-Tim

---

### Post by grs on 2008-09-06
When I tryied installing server I got the  following

```

Package not available, but is reffered to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.

```

Client it said was already newest version.
I found a file called /etc/ssh/ssh_config rather than sshd_config

I did have trouble connecting to my network, how can I tell from the server if it can connect to the internet?

---

### Post by windependence on 2008-09-06
See if you can do a ping yahoo.com from the server.

-Tim

---

### Post by grs on 2008-09-06
After typing in ping [www.yahoo.com](www.yahoo.com) it just comes back with unknown host

---

### Post by crachel on 2008-09-06
type in 'ifconfig'

you should see 'eth0', if not there is something wrong with your network connection

---

### Post by windependence on 2008-09-06
Can you post the contents of your /etc/resolv.conf?

-Tim

---

### Post by grs on 2008-09-06
That all seems ok. The problem must be with the SSH Server.

---

### Post by windependence on 2008-09-06
Could we see it? 

You either don't have dns configured correctly OR your gateway is missing/wrong. I can't tell if you won't post the files.

-Tim

---

### Post by grs on 2008-09-06
The contents are below

```

search irishbroadband.ie
nameserver 62.231.32.10
nameserver 62.231.32.11
nameserver 89.124.172.10

```

---

### Post by windependence on 2008-09-06
OK great! Now, what is in your /etc/network/interfaces?

I'm not being funny here, just trying to cover all the bases and find out why you can't get out of your network.

Can you ping 71.39.77.108 from your server?

-Tim

---

### Post by grs on 2008-09-06
/etc/network/interfaces has the following settings

```


#Loopback Interface
auto lo
iface lo inet loopback

#PCI network card, eth1, set to DHCP
auto eth1
iface eth1 inet dhcp


```

The titles are slightly different but I don't think it matter once there after a # symbol.

I've also realised the Ubuntu can see both the onboard NIC and the PCI NIC but it's only able to use the PCI NIC.

---

### Post by volkswagner on 2008-09-06
What is the output of 

```
ifconfig
```

Post results, and is the ip address the same you are using to login with?

Since you are using DHCP your ip could have changed.  Not sure if you are inside your LAN or outside WAN?

---

### Post by grs on 2008-09-06
ifconfig outputs

```


eth0 link encap: ethernet HWaddr 00:20:df:05:07:72
     inet address: 192.168.1.106 bcast: 192.168.1.255 Mask: 255.255.255.0
     inet6 address: fe80::220:dfff:fe05:772/64 scope: link
     up broadcast running multicast mtu:1500 metric:1
     rx packets:970 error:0 dropped:0 overruns:0 frame:0
     tx packets:548 error:0 dropped:0 overruns:0 carrier:0
     collision: 0 txqueulen: 1000
     rx bytes: 113913(111.2kb) tx bytes: 77322 (75.5kb)
     interupt: 20 base address: 0xbc00

lo   link encap: local loopback
     inet address: 172.0.0.1 mask: 255.0.0.0
     inet6 address: ::1/128 scope: host
     up loopback running mtu: 16436 metric: 1
     rx packets:44 error:0 dropped:0 overruns:0 frame:0
     tx packets:44 error:0 dropped:0 overruns:0 carrier:0
     collision: 0 txqueulen: 0
     rx bytes: 2200(2.1kb) tx bytes: 2200 (2.1kb)     



```

Are we getting any closer to why I can't install openssh-server

---

### Post by rhodest83 on 2008-09-06
A simple test to see if you can actually get to the internet is to do:

```
telnet www.google.com 80
```

Then press enter, you should see some raw HTML returned on the prompt.

if you don't get anything, try:

```
dig www.google.com
```

you should see a number of names and IP address printed out.

If you don't, your connection to the internet is still the problem.

---

### Post by grs on 2008-09-07
The tenet command produced:-

Trying 66.249.93.99
Conned to [www.l.google.com](www.l.google.com)
Escape character is '¬!'

After a few seconds follows:-

Connectio closed by foreign host

The dig command produce about 3/4 page of info, ip address for google.com etc..
Does this mean I'm getting an internet connection?

---

### Post by jerome1232 on 2008-09-07
Okay so that means DNS is resolving for you and it sounds like you were able to connect to google.com on port 80.

aka appears everything is working

Try installing the ssh server again. If you get any errors please post what the errors were and try to be as exact as you can.

```
sudo apt-get update
sudo apt-get install openssh-server
```

---

### Post by grs on 2008-09-07
That seems to have done it, thanks. apt-get install, does that do general upgrade of everything on the system or just from Ubuntu?

At least now I don't have to run from room to room to set up my server!!

Do you know much about WinSCP? Its handy for quick navagation around the file system, also for editing conf type files.
I have that connected to the server aswell, but when I try to add, edit or delete a file it won't allow me due the sudo prefix command been needed, do you know of a way around this, I think its possable but I don't really knwo the details fo the software too well.?

---

### Post by jerome1232 on 2008-09-07
Actually apt-get update just updates your database of what's available to download, apt-get upgrade will update your system.

apt-get install obviously installs packages

apt-cache search will search the database for keywords you specify

apt-cache show will give you details on a package

(try apt-cache search ssh, apt-cache show openssh-server and you should get an idea on how to use these, no need for sudo)

I use winscp just for transfering files (and I'll open a putty session from inside it).

To edit files in a command line, use nano or vim, nano is easier for the beginner but I like vim more.
You even have a web browerser called lynx (type lynx google.com) it's useful for some things, I'll use it to view documentation that's in html sometimes.

```
sudo nano /etc/foo/foos_config.conf
sudo vim /etc/foo/foos_config.conf
```

---

### Post by grs on 2008-09-08
I know about vim and nano. WinSCP makes it so much easier to just drag and drop files from a PC to the server, I had a webpage made up on my Windows PC I just dragged the files in the web folder on the server. If I edit a file I can very easily caopy and paste text from a webpage, notepad or other word processor program.

---

