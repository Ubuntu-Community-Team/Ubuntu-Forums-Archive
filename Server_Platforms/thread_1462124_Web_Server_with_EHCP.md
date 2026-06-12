---
title: "Web Server with EHCP"
date: 2010-04-25
forum: Server Platforms
---

### Post by ronhagley on 2010-04-25
Hi everyone,
I am trying to set up a webserver using Ubuntu server with the EHCP plugin. I have it working and can access the EHCP page by using the IP address on my local network (192.168.0.4)
So far so good. I then set uo a domain using the Domain add new(custom)from the sidebar. I provided the following info:
domainname - learner
Panel - me
Panel password - me2
Ftp user - DACL
ftp password cullompton

Great I have now got a folder structure including httpdocs for that domain, I can also use filezilla to upload webpages etc to that folder, and have uploaded a page called index.htm

One problem remains - what address do I type into the web browser to see the webpage. I've tried 192.168.0.4/learner which is what I expected to work.

Please note - this will only ever be used as a web server on a local network, never on the WAN
I'm sure I have done something stupid - but can't think what. I'm very new to LINUX so please be gentle with me. Can anyone help please.

---

### Post by dalitso on 2010-04-25
Please post your /etc/hosts
```
nano /etc/hosts
```

and output for hostname
```
hostname
```

---

### Post by dalitso on 2010-04-25
Since "learner" is your domain, try typing it in the browser. If that doesn't work try editing your domain name in EHCP to something like "learner.com" or "learner.local"
I hope the EHCP made the LAN to resolve to itself not over the internet. When you finish editing and save the changes, use the new domain name in your browser to access your website.

---

### Post by ronhagley on 2010-04-25
hi, and thanks for the reply.
when I type nano /etc/hosts this is what I see:

127.0.0.1 localhost
127.0.0.1 ubuntu

#the following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localhost
ff00::0 ip6-mcastprefix
ff02::1 ip6-allmodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.4 [www.domainname.com](www.domainname.com) [www.mydomain](www.mydomain) [www.learner](www.learner) [www.learner2](www.learner2) localhost


I hope this means something to you as it means relatively little to me!

thanks

Ron

---

### Post by dalitso on 2010-04-25
Try [www.learner](www.learner) or [http://learner](http://learner)

If its still not working try to do the changes I suggested in my previous post.

---

### Post by ronhagley on 2010-04-25
thanks, I tried that with no luck.
When I tried editing nano /etc/hosts to I was prevented from saving the file (error writing /etc/hosts: Permission denied)
As I say I am very much a beginner with this. When I used [www.learner](www.learner) I was taken to dyndns webpage when I tried [http://learner](http://learner) I was given the "server not found error"
I really appreciate your efforts to help - if you have any other advise I would be really grateful.

---

### Post by dalitso on 2010-04-25
Just hang in there. I am sure I will come up with a solution. I don't use EHCP so I will have to install it on one of my PCs then get back to you. I like trying out stuff. 

I usually use webmin/virtualmin to do my website hosting both on my LAN and WAN. There's also ISPConfig which is a very nice and easy hosting control panel. But for now, lets focus on EHCP.

Oh, and the reason you are getting "error writing /etc/hosts: Permission denied" is that you are editing as a normal user not root. Use "sudo" before the rest of the command. For now do not edit anything in /etc/hosts

The reason you are taken to the internet when you type [www.learner](www.learner) or "server not found", might be that your server is not resolving DNS on your LAN.

To make it resolve, add 192.168.0.4 and 127.0.0.1 in /etc/resolv.conf
```
sudo nano /etc/resolv.conf
```
```
nameserver 127.0.0.1
nameserver 192.168.0.4
```

then try again your website [www.leaner](www.leaner) or [http://learner](http://learner)

---

### Post by ronhagley on 2010-04-25
OK I looked a bit further in a forum a saw that you need to edit the file etc/apache2/sites-available to something like this
<VirtualHost 192.168.0.4>
ServerName learner
ServerAlias [www.learner](www.learner)
DocumentRoot /var/www/learner/httpdocs
</VirtualHost>

I still have a problem as I cannot find the key to make a < or a > (I've tried all the ones on the keyboard with and without the shift and can't locate them) Any help please?

---

### Post by dalitso on 2010-04-25
Am not sure if doing that is going to help unless u create a new virtual host in apache. 192.168.0.4 is already being used by EHCP, right? maybe am wrong but I believe these control panels like EHCP, ISPConfig, webmin/virtualmin usually takes care of the creation of virtual servers and even DNS settings automatically.

But like I said, I will let you know once I install EHCP and try it out to see what its all about.

---

### Post by dalitso on 2010-04-25
On a QWERTY keyboard, those keys are between "M" and "?", its the ","(comma) and "." (full stop) keys

---

### Post by ronhagley on 2010-04-25
Hi again,
tried that and managed to save the file this time - thanks for  making that clear SUDO presumably stands for superuser or similar?
However still no luck with making the browser work. I really appreciate all the effort you are making to help a newbie like me.

---

### Post by ronhagley on 2010-04-25
I tried those and got ; and : respectively when using shift and , or . without shift.
Seems odd!

---

### Post by ronhagley on 2010-04-25
Many, many thanks sorry to be such a pain in the *** but I really need to get this working and really appreciate the effort.

---

### Post by dalitso on 2010-04-25
I got it to work. Like I thought its a DNS thing. When accessing your domain [www.learner](www.learner) the client needs to resolve to your server's ip which is 192.168.0.4. But in your case it is resolving to another DNS hence going to the internet to look for the address.

Please explain how your network is; how many PCs, routers/network switches, modems, how many networks interface are you using on your server and how they are connected and also their ip addresses/gateways and stuff.

While you are getting the above info,please assign a static ip address on the client PC that you are using and on gateway put the router's ip address if you are using a router or 192.168.0.4 if you are using a switch. On dns servers use 192.168.0.4

Then type [www.learner](www.learner)
on your browser

The above can work if your network is as I have imagined it, otherwise then please post the info of your network. I also assume that DNS,postfix, pop3/imap are installed on your server. I believe so because the ehcp could not have installed successfully unless maybe they were warnings when installing it but you ignored them.

---

### Post by ronhagley on 2010-04-26
Hi Dalitso,

Many thanks for your advice and effort. I'm at work at present so can't do this at the moment but as soon as I get home I will do so.
Re your 3rd paragraph I have a couple of questions:
Will I have to have static IP addresses on all connectd PCs ( I can do this at home, but when I use this at work I cannot modify IP addresses on the client machines. 
Also I do not understand your reference to DNS servers. I know the function of a DNS server as far as the internet is concerned. But not where they are located on a LAN- is it on the server or the client machine, again the same problem exists - if it is on the clients then I cannot modify these.
Again many thanks for all your effort.

Ron

---

### Post by dalitso on 2010-04-26
You are welcome. I like Ubuntu so much and trying out stuff. It's best you do this setup(static ip changes) at home like you pointed out.

The DNS server should exist within your ubuntu server, it will mostly be like a LAN DNS server.

I believe you have Ubuntu server edition installed on your box and since it has no GUI, you are accessing it using one of your client PCs using an SSH client and also the EHCP. I am suggesting you modify the Ip address and other settings on that client PC only just to make it work. Is this client PC running windows or linux?
Please explain your network so that I can have an idea how the computers are connected.

I am having problems with my ADSL line so I am using a slow connection now. It might take me long to check for your reply.

---

### Post by windependence on 2010-04-26
Guys, just FYI, it looks like EHCP installs it's own DNS server. I don't think he wants to have another one on his server as they could conflict. Normally, you would not even need a DNS server, but for hosting you would have a local one or a caching server for the web clients. 

From the web server you should go to canyouseeme.org and check that port 80 is open. Can you ping google.com by name from the command line on the web server?

```
ping google.com
```

-Tim

---

### Post by ronhagley on 2010-04-26
Hi Dalitso,

I'm sorry to hear you are suffering from poor ADSL connection at present and hope it improves for you soon.
My network is based around a router with the IP address of 192.168.0.1 For the current problem there are 2 computers connected by ethernet cable:
the notebook running Ubuntu Server 9 and a PC running Windows XP
The Windows PC has the address 192.168.0.2 on a subnet mask of 255.255.255.0 default gateway of 192.168.0.1. Access from this PC to the internet and the router is fine, I can also PING the Ubuntu Server (192.168.0.4)

I have read the Ubuntu Server network details using the following command (nano /etc/network/interfaces) and get this report>
#this file describes the network interfaces available on your system
#and how to activate them. For mor information, see interfaces(5)
#The loopback network interface
auto lo
iface lo inet loopback
#the primary network interface
aout eth0
iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
network192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

I am typing any commands relevant to the Ubuntu server on its own command line notfrom the client PC.
The client PC is on Windows XP

Just to remind you I can access the server via FTP from the client using Filezilla but can't get antywhere using the browser. In fact things have deteriorated slightly over the past day (something I altered I guess) I was able to get the EHCP interface from the client via the browser by typing 192.168.0.4. Now not even that works. I am going to investigate further tomorrow as I have to work tonight.
For info I also checked whether I could ping Google from the Ubuntu server as suggested by windependence and can do so (about 30ms roundtrip)
Thanks again for all your help.
Ron

---

### Post by dalitso on 2010-04-26
windependence> Guys, just FYI, it looks like EHCP installs it's own DNS server. I don't think he wants to have another one on his server as they could conflict.


dalitso> I also assume that DNS,postfix, pop3/imap are installed on your server. I believe so because the ehcp could not have installed successfully unless maybe they were warnings when installing it but you ignored them. 

windependence
Thank you for pointing that out. I failed to explain myself there, I was not suggesting he install another DNS server. And it looks like even though ehcp can install its own DNS, it doesn't actually install it if one is already present. In my setup I had already Bind DNS installed then I installed ehcp and I don't have two DNS servers running. I think it must have detected it.

ronhagley
My ADSL is working normal now. Now I have a pretty good picture about your network. I am going to run the ehcp using a similar setup because the disadvantage of my setup that worked yesterday is that you might not have internet on your PC. Let us know when you get ehcp working again it could just be that ehcp is not running. Use 
```
/etc/init.d/ehcp start
```

Here's the setup that worked for me yesterday
I connected two PCs to a router. One ubuntu desktop with LAMP, DNS, postfix, imap/pop2 and ehcp installed, the other win xp. The Ubuntu desktop pc was designated server in the setup.

This router was not connected to the internet its not a modem/ router. Its ip is 192.168.0.254


Ubuntu
Ip 192.168.0.11
gateway 192.168.0.254
subnet 255.255.255.0


Xp
ip 192.168.0.10
gateway 192.168.0.254
subnet 255.255.255.0
Preferred DNS server 192.168.1.11 (the Ubuntu ip)


On such setup, when you type [www.leaner](www.leaner) on the xp browser, it works. (such a setup could make the xp PC not have internet if this router was a modem. If am right, that is.)

---

### Post by ronhagley on 2010-04-26
Hi again- I'm glad your ADSL is up again.
My router is an ADSL Modem /router
I'm a bit confused about your preferred DNS server which you say has the IP of 192.168.1.11 (the Ubuntu ip) however earlier you gave the Ubuntu IP as 192.168.0.11 - is one a typo or does the DNS server have a different IP than the server?
My DNS servers are set by the router as 216.146.35.35 or 216.146.35.36 which are the ones recommended by the ISP. Do I need to edit the list in the router settings to include the IP address of the server?
Are you running Ubuntu Server 9 or standard Ubuntu?

thanks for your efforts

Ron

---

### Post by dalitso on 2010-04-26
The ip address was a typo. It's 192.168.0.11
I was running this test on Ubuntu desktop 9.10 but method 3 below, runs on Ubuntu server 8.04. I have 4 machines in my room. 2 run Ubuntu server(one is a test server), the other one Ubuntu desktop and the last one xp.

You can try to add your server ip on the DNS settings of your router, maybe it will work. I tried it did not work for me maybe because my router only allows two dns server addresses.

I am not an expert. I have been using ubuntu server for a year and a half now. 
I have practically tested the methods below.

Method 1
Manually assigning network settings to your XP PC like I said in my previous 
post works not only to access your site [www.learner](www.learner) but also access internet.

IP address 192.168.0.5
subnet mask 255.255.255.0
default gateway 192.168.0.1
preferred DNS server address 192.168.0.4


This method requires that you to change network settings on the clients.


Method 2
Create a virtual IP address in /etc/network/interface
 ```
sudo nano /etc/network/interface
```
```

The loopback network interface
auto lo eth0 eth1 eth0:1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1


iface eth0:1 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0  

```

Then add eth0's IP to /var/www/vhosts/ehcp/apachehcp.conf


```
sudo nano /var/www/vhosts/ehcp/apachehcp.conf
```

Find your virtual host for [www.learner](www.learner) and will look like this

```

<VirtualHost 192.168.0.5>
ServerName site.local
        ServerAlias  www.site.local
	# buraya aliaslar yazilacak..

```



This method allows you to access your site by typing the virtual IP 192.168.0.5 in your browser.
No need to manually assign IP addresses on client PC, leave to obtain ip and dns automatically.
You cannot access your site by typing [www.learner](www.learner).




Method 3
Setup your Ubuntu server as a gateway/router. You will require two network interfaces(eth0 connects to your internet router and eth1 connects to your LAN) and a network switch/hub.You will also need to setup DHCP server on your Ubuntu server which will make the client to automatically obtain an IP address and even DNS settings.

There will be no need to use method two on this setup(creating virtual ip and editing
some virtual host)
No need to assign IP on client
you can access the site by typing [www.learner](www.learner)



This is as far as I can go, please guys provide other better ways to sort this one out.

---

### Post by ronhagley on 2010-04-26
Dear Dalitso,

you claim not to be an expert - I think you are too modest. your patience and help have been wonderful, I feel so privelidged to have been taught by you. Thank you so much for all your help. Tomorrow I will try to put in practice what you have explained so patiently. Thank you again - no-one could ask for more than you have been willing to give.

All the best in the future

Ron

---

### Post by dalitso on 2010-04-26
Thanks. Just a correction on method 2. Delete eth1 on the second line
```
The loopback network interface
auto lo eth0 [COLOR="Red"]eth1[/COLOR] eth0:1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1


iface eth0:1 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
```


It should be 
```
The loopback network interface
auto lo eth0 eth0:1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1


iface eth0:1 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
```

eth0:1 is a virtual interface


And another mistake> Then add eth0's IP to /var/www/vhosts/ehcp/apachehcp.conf


Code:

sudo nano /var/www/vhosts/ehcp/apachehcp.conf



I meant to say add eth0:1's IP

I hope they are no more mistakes

---

### Post by dalitso on 2010-04-26
By the way, you can have command line for your server on the xp pc by installing Putty, an ssh client. Download the putty.exe here [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
Just put your server IP where it says "hostname or IP address" and hit enter (click open"

You can also install webmin, a web interface for your Ubuntu server if you find command line difficult. You can do almost all the server setup with it. I combine webmin and command line. It makes things easier.

You can always PM me for webmin if you are interested, I have been using it for long so I know some good tricks.

---

### Post by ronhagley on 2010-04-27
Thankyou Dalitso,
just got home and am starting to work on it now. Going to try the various methods you have so kindly provided. You are a genuine star.
I will post when I have a result
Many thanks for all the effort.

Ron

---

### Post by ioasw on 2011-08-15
This is a fairly old thread, but any progress made on the subject.  I think dalitso's method 2 is the most promising, but I'm having the same problem as you're having.  I can't get a second added domain to point to the htdocs folder of the newly created domain in ehcp.

---

### Post by kapnnix on 2012-03-06
Old thread but thought I could contribute if anyone is still  having similar issues.

This explains ehcp for "LOCAL" networks only. I'm assuming you have ehcp running on a server of some sort and are wanting to view the sites from other computers within the local network. If you want WAN access to your sites you will have to buy a domain and configure additional things. 

1. Figure out the domain name your going to use for the site and create it with ehcp. Example: test.com 

2. Edit your hosts file.(local computers, not the ehcp server) This file will allow you to view your websites locally. Open the terminal on your local computer, Not the server. 

Type: sudo nano /etc/hosts


Mine looks like this:

-------------------------------------
127.0.0.1       localhost
127.0.1.1       mynix
192.168.0.3     hellserv
192.168.0.3     test.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
-------------------------------------

Notice where it says: 192.168.0.3     test.com
This is the ip of the ehcp server and the domain I created with ehcp.

Any time I type test.com into my browser MY page shows up because of the hosts file. If I was to remove the test.com hosts entry and then go to test.com it would bring me to the actual site test.com and not my local creation. 

Insert your domain in place of mine. First goes the IP of the ehcp server then the domain you've created. No need to use www.

For every domain created in ehcp you will need the corresponding entry in the hosts file. The hosts file will have to be updated on all local computers wanting access to your sites.

Once the hosts file is updated and saved you can open a browser and enter your newly created domain Example: [http://test.com](http://test.com)

You should now be able to view your sites.

---

