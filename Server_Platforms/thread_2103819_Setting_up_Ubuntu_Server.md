---
title: "Setting up Ubuntu Server"
date: 2013-01-11
forum: Server Platforms
---

### Post by chrisguk on 2013-01-11
Hi there,
I have just bought a second hand business PC that I want to use as an Ubuntu Server.  The specs of the PC are quite high so it can handle the installation no problem.

The advice I need is this:

How do I setup the server to be a file and web server?

I have a client PC using Ubuntu Desktop where I carryout all my development work in PHP.  On this client I have LAMP installed so I can test the pages or sites I have created locally.  I want to move all of my files to the PC I intend to use as a server and access the files read/write as normal.  Also to be a local web server.

I am very new to this so please excuse me if I am not using the correct terminology.  

Any help or thorough tutorials will be a great help ;)

I am using Ubuntu Server 12.10

---

### Post by lisati on 2013-01-11
There is a wealth of information here: [https://help.ubuntu.com/12.10/serverguide/index.html](https://help.ubuntu.com/12.10/serverguide/index.html)

Feel free to continue with the questions!

---

### Post by tgalati4 on 2013-01-11
```
sudo apt-get install tasksel
sudo tasksel

```

Pick some services to install--like the LAMP stack.

---

### Post by chrisguk on 2013-01-11
Hi again,

So I got the server package installed no problem.  I have the following packages installed:

LAMP - Stack
DNS
Mail Server

I have been doing some reading and from what I can gather I need to install "NFS" so I can access the files from my client ubuntu PC.  As I am a PHP developer this is necessary.

Also, presently I have a lamp stack installed on my client ubuntu PC which is what I used until I bought this server for checking the web page output of my code.

Im not sure where to start to kind of produce the same environment on the server.  So let me explain my setup a little more:

I have a desktop PC - Ubuntu desktop installed
I have a standalone server on the same network in a different room.

I want to store and edit website dev files (php, html, .js etc etc) as and when I want.

I want to be able to open my browser and point it to lets say:

[www.mysite.local](www.mysite.local)

Like I said I am really new to this so any help and advice would be great?

Also I think I need to install a Hosting type control panel so I can mimic a local network virtual hosting environment,  direction on that would be great too ! ;)

---

### Post by tgalati4 on 2013-01-11
You would need NFS if you are sharing your files with a Unix workstation, otherwise the default installations have SAMBA/CIFS for file sharing.  NFS is really optional.  You also don't need DNS, you can simply use external DNS servers to serve up names.

You will need to install ssh on both machines so you can remotely log in. 

```
sudo apt-get install ssh
```

Put your html in /var/www.

Log into your server via a browser.  Set up some local file shares between the machines so you can move files back and forth easily.  Install a web content management system (such as Drupal7) if you want to get up and running quickly.

Check out service "stacks" at [http://bitnami.org](http://bitnami.org) .  These are neatly-packaged services that can be installed with a few clicks.  Good for learning the different frameworks.  Many are programmed in php.

---

### Post by chrisguk on 2013-01-11
> **tgalati4 said:**
> You would need NFS if you are sharing your files with a Unix workstation, otherwise the default installations have SAMBA/CIFS for file sharing.  NFS is really optional.  You also don't need DNS, you can simply use external DNS servers to serve up names.

You will need to install ssh on both machines so you can remotely log in. 

```
sudo apt-get install ssh
```

Put your html in /var/www.

Log into your server via a browser.  Set up some local file shares between the machines so you can move files back and forth easily.  Install a web content management system (such as Drupal7) if you want to get up and running quickly.

Check out service "stacks" at [http://bitnami.org](http://bitnami.org) .  These are neatly-packaged services that can be installed with a few clicks.  Good for learning the different frameworks.  Many are programmed in php.


Im not sure you understand what I mean.  Im new so maybe I didnt word my question correctly.

I am a PHP developer already.  I develop my own frameworks for different projects that I work on.  

I installed openSSH on the server so I can configure that for access from my client pc.  I will give NFS a go as well to see if that works for me.

I believe the main issue is:

I will have all my project folders stored under:

 /var/www/project1
 /var/www/project2
 /var/www/project3

I want to open a browser on the client PC and navigate through [http://mysite.local](http://mysite.local)  (the local Directory is held on the server) in the folders named above.

I hope this makes sense ;)

---

### Post by spynappels on 2013-01-12
Do you want to access each site individually using [http://project1.local](http://project1.local), [http://project2.local](http://project2.local), etc. or just access mysite.local and have links to each project within that?

---

### Post by chrisguk on 2013-01-12
> **spynappels said:**
> Do you want to access each site individually using [http://project1.local](http://project1.local), [http://project2.local](http://project2.local), etc. or just access mysite.local and have links to each project within that?


Hi there,

Yes I want to access them individually.  I pondered on the thought do i need install a hosting control panel etc as well?

---

### Post by spynappels on 2013-01-12
Ok, what you need to do is have a separate virtualhost for each project. You set the name to be project1.local or whatever and if external access is also required you can set up an alias for that site as well. There are plenty of howtos and tutorials online for doing this. I don't think you should need a hosting panel for this, seems overkill.

As for accessing the sites from your laptop, there are 2 ways of doing that. The simplest way is to add entries to the /etc/hosts files of your laptop, putting your server IP address for project1.local, project2.local etc. This will only work from that laptop though. A more comprehensive, and less simple, solution is to set up a DNS server on your server and map each name to the server IP there. You set this up as the main DNS server for your network and you'll be able to access the test sites at your chosen names from any computer on your LAN. It is a little more complex to set up though.

---

### Post by chrisguk on 2013-01-12
> **spynappels said:**
> Ok, what you need to do is have a separate virtualhost for each project. You set the name to be project1.local or whatever and if external access is also required you can set up an alias for that site as well. There are plenty of howtos and tutorials online for doing this. I don't think you should need a hosting panel for this, seems overkill.

As for accessing the sites from your laptop, there are 2 ways of doing that. The simplest way is to add entries to the /etc/hosts files of your laptop, putting your server IP address for project1.local, project2.local etc. This will only work from that laptop though. A more comprehensive, and less simple, solution is to set up a DNS server on your server and map each name to the server IP there. You set this up as the main DNS server for your network and you'll be able to access the test sites at your chosen names from any computer on your LAN. It is a little more complex to set up though.

Than you so must for you advice.  

I have no issue with setting up virtual host blocks as I have this system setup on my desktop PC running Ubuntu LAMP already.

But because my projects are becoming bigger and more complex I decided I needed a server solution with RAID / Offsite back up and to act as the Main file and web server for all of the projects.

I have a very small team of guys that will need to access certain areas of the server from outside so i have just created users for them to use SSH / SCP using ssh keys only and disabled PasswordAuthentication so they have to have the right RSA key pair to gain access.  The server is behind a router and hardware firewall plus a cisco managed switch with added security protocols.

I think because I have a passion to know more I will go with the more difficult option and make it a domain server.

---

### Post by eenofonn on 2013-01-12
Have you had any luck configuring dns?  I followed a few tutorials on youtube 

[Part 1]("http://www.youtube.com/watch?v=OUv03JV5SLc")

[Part 2]("http://www.youtube.com/watch?v=2G8BhM6Ru1g")

[Part 3]("http://www.youtube.com/watch?v=ed4q5FWJfdc")

[Part 4]("http://www.youtube.com/watch?v=H8phIakC-Jk")

Although I did find some problems with the tutorial regarding reverse lookups, and he's pretty vague on a couple of the config options

I'm also running the LAMP stack and I'm hosting 3 virtualhosts on my server. NFS is great but Samba works too, it all just depends on what your looking for.

---

### Post by chrisguk on 2013-01-13
bump

Okay I need to bump this up for another question.

I followed the video guide as suggested and it all worked until I got to the client setup.

First of all I had to uninstall:

resolvconf
network-manager

on the client and server.

The reason I removed the above was due to the resolv.conf file being overwritten each time.

once all the settings in resolve.conf on the client had been completed for example:

search Servermain.com.
nameserver 192.168.178.150

I restarted everything on the client (reboot) Ubuntu client.

I checked the resolv.conf again and it was overwritten yet again.  I just cant figure out why.

When I ping the server it throws this back at me:

64 bytes from Server.fritz.box (192.168.178.150): etc etc

The IP is correct but the server name is not right.  I setup all the DNS to be Servermain.com.  It resolves correctly on server using nslookup etc basically using all the check supplied in the video.

Im at a dead end here.

Do I need to reinstall Ubuntu Server again and start fresh out of the box?  If so can you recommend a fresh basic install to get me started?

Anz help at all will be great

---

### Post by drdos2006 on 2013-01-13
To control your server have a look at Webmin. ([http://www.webmin.com/](http://www.webmin.com/)) 

Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. Based on Debian so just change the OS name to Ubuntu as you already have Ubuntu set up.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

Logon to your server and download from your server with :
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.610_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.610_all.deb)

Install with :
sudo dpkg -i webmin_1.610_all.deb

Add extra libraries with :
sudo apt-get -f install
[/code]


regards

---

### Post by eenofonn on 2013-01-13
I'd recommend you don't mess around with webmin because when I've used it in the past I've ran into issues but that's just my $.02

What's does your "/etc/network/interfaces" look like

you should have added 

dns-search Servermain.com.
dns-nameservers 192.168.178.150

for instance my server's interface:

```


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.11.254
        netmask 255.255.255.0
        network 192.168.11.0
        broadcast 192.168.11.255
        gateway 192.168.11.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search gotr.local.
        dns-nameservers 192.168.11.254

```

---

### Post by chrisguk on 2013-01-13
I think this is turning into a good thread as it could assist others in the future.

I am collect the info though to build my own setup file.

You may have a point about webmin.  I was talking to someone in the Ubuntu IRC channel and I said have you ever used "webmin".  He said , "don't try to make a difficult situation easy!, you need to understand the errors to fox them properly and a point and click environment is nothing more than like shopping on Ebay."

ok I added the lines to my /etc/interfaces files as suggested.  My file now looks like this:

```

auto eth0
iface eth0 inet static
  address 192.168.178.24
  netmask 255.255.255.0
  network 192.168.178.0
  gateway 192.168.178.1
  broadcast 192.168.178.255
  # dns-* options are implemented by the resolvconf package, if installed
  dns-search Servermain.com.
  dns-nameservers 192.168.178.150


```

I have this question because when I try to ping "server" it resolves to the following address:

```

:~$ping server
PING server.Servermain.com (107.20.206.69) 56(84) bytes of data.


```
Which is obviously not my server.  Can you think of a reason?

I wondered if the entries in my Servermain.com.db contain within the /etc/bind/zones is affecting the result.  They are as follows:

```

$TTL 3D
@ IN SOA server.Servermain.com. admin.Servermain.com. (
2013011301 ;
28800;
3600;
604800;
38400
);

Servermain.com. 	IN	NS	server.Servermain.com.
server			IN	A	192.168.178.150
nortest			IN	A	192.168.178.24
www			IN	CNAME	nortest

```

this is my reverse lookup file:
```
$TTL 3D
@ IN SOA server.Servermain.com.	admin.Servermain.com. (

2013011301;
28800;
6044800;
6044800;
86400
);

		IN	NS	server.Servermain.com.
150		IN	PTR	server.Servermain.com.
24		IN	PTR	nortest.Servermain.com.
1		IN	PTR	gw.Servermain.com.

```

this is my named.conf.options file:

```
forwarders {
	
	192.168.178.1;
	8.8.8.8;
	8.8.8.4;
	95.119.104.159;
 	
	 };

```

Does any of that shed any light.

By the way the client loads with the correct info in the resolv.conf now as expected but still no ping.

I also wondered about the naming conventions regarding my server:

Servermain.com
server.Servermain.com

Any advice will be great ;9 thanks

---

### Post by eenofonn on 2013-01-13
your config looks fine to me other than your reverse which should look like this:

```

$TTL 3D
$ORIGIN 178.168.192-IN-ADDR.ARPA.
@ IN SOA server.Servermain.com. admin.Servermain.com. (
2013011301 ;
28800;
3600;
604800;
38400
);

Servermain.com. 	IN	NS	server.Servermain.com.
server			IN	A	192.168.178.150
nortest			IN	A	192.168.178.24
www			IN	CNAME	nortest


```

Also did you make sure to set the server's ip to static and make the dns-* changes to it as well...

You should be able to run an nslookup on your dns server and have it return the correct information if it's all configured correctly e.g. 
```

root@mini:/# nslookup mini
Server:         192.168.11.254
Address:        192.168.11.254#53

Name:   mini.gotr.local
Address: 192.168.11.254

root@mini:/#

```

and to check reverse 
```

root@mini:/# nslookup 192.168.11.254
Server:         192.168.11.254
Address:        192.168.11.254#53

254.11.168.192.in-addr.arpa     name = mini.gotr.local.

root@mini:/#

```

---

### Post by chrisguk on 2013-01-13
ok im baffled so this is what I am going to do.

and btw, I did take a look at that webmin server setup and yes it looks great but I really want to keep it command line so I know exactly how things work inside the box and be confident and responsible for each file I create/rename/delete and edit.  I actually tested webmin on creating virtual hosts.  It doesnt produced the correct results so Ill stick to the manual command line way, which the way I know best.

Ok back to the drawing board.  Im gonna take into consideration the modifications in previous posts and start from scratch on the DNS setup.

Ill post here my results after that.):P:lolflag::guitar:

---

### Post by eenofonn on 2013-01-13
> **chrisguk said:**
> ok im baffled so this is what I am going to do.

and btw, I did take a look at that webmin server setup and yes it looks great but I really want to keep it command line so I know exactly how things work inside the box and be confident and responsible for each file I create/rename/delete and edit.  I actually tested webmin on creating virtual hosts.  It doesnt produced the correct results so Ill stick to the manual command line way, which the way I know best.

Ok back to the drawing board.  Im gonna take into consideration the modifications in previous posts and start from scratch on the DNS setup.

Ill post here my results after that.):P:lolflag::guitar:


You shouldn't have to start over from scratch... but if that
s what you want to do go right ahead :P

webmin does look like it makes things easier but from my history with it I'd never recommend it to someone

---

### Post by jdthood on 2013-01-14
> **chrisguk said:**
> ok I added the lines to my /etc/interfaces files as suggested.  My file now looks like this:

```

auto eth0
iface eth0 inet static
  address 192.168.178.24
  netmask 255.255.255.0
  network 192.168.178.0
  gateway 192.168.178.1
  broadcast 192.168.178.255
  # dns-* options are implemented by the resolvconf package, if installed
  dns-search Servermain.com.
  dns-nameservers 192.168.178.150


```


Note that the dns-* options will have no effect because you have uninstalled the resolvconf package.

---

### Post by jdthood on 2013-01-14
> **eenofonn said:**
> webmin does look like it makes things easier but from my history with it I'd never recommend it to someone

Distributions differ in how they should be configured and webmin wasn't developed for Debian-based distributions. So if you use webmin there is an excellent chance that it will configure the system in a nonstandard and suboptimal way.

---

### Post by chrisguk on 2013-01-14
> **eenofonn said:**
> your config looks fine to me other than your reverse which should look like this:

```

$TTL 3D
$ORIGIN 178.168.192-IN-ADDR.ARPA.
@ IN SOA server.Servermain.com. admin.Servermain.com. (
2013011301 ;
28800;
3600;
604800;
38400
);

Servermain.com. 	IN	NS	server.Servermain.com.
server			IN	A	192.168.178.150
nortest			IN	A	192.168.178.24
www			IN	CNAME	nortest


```

Also did you make sure to set the server's ip to static and make the dns-* changes to it as well...

You should be able to run an nslookup on your dns server and have it return the correct information if it's all configured correctly e.g. 
```

root@mini:/# nslookup mini
Server:         192.168.11.254
Address:        192.168.11.254#53

Name:   mini.gotr.local
Address: 192.168.11.254

root@mini:/#

```

and to check reverse 
```

root@mini:/# nslookup 192.168.11.254
Server:         192.168.11.254
Address:        192.168.11.254#53

254.11.168.192.in-addr.arpa     name = mini.gotr.local.

root@mini:/#

```

Are you sure about the Reverse lookup being as you described above.  It needs to contain PTR and not A name or CNAME records?

---

### Post by eenofonn on 2013-01-14
OOOPS you're right, I just did the top part manually then copied all of your stuff down.

---

### Post by eenofonn on 2013-01-14
> **jdthood said:**
> Distributions differ in how they should be configured and webmin wasn't developed for Debian-based distributions. So if you use webmin there is an excellent chance that it will configure the system in a nonstandard and suboptimal way.

Thank you for the explanation :) I have a friend that swears by webmin but I've always had issues with it and prefer to do everything cli.

---

### Post by eenofonn on 2013-01-17
Hey Chris you think you should mark this as resolved?

---

