---
title: "Apache2 on home ubuntu 8.10 problem"
date: 2009-01-16
forum: Server Platforms
---

### Post by hossiam on 2009-01-16
OK I have a no-ip (dynamic DNS) domain name for my website on my server.  I have got no errors when i restart apache, i have tested the connection and port and there fine.  my problem is i can type my domain name in the browser, let's say it example.com, and i can see it.  the problem is from another computer on my network i get "The server at example.org is taking too long to respond." When I add WWW i get "The browser could not find the host server for the provided address."  What files do I have to edit....hosts.config, httpd.config sites avalible.......can someone please help me.   My goal is just to use this to share photos and home videos among friends.

---

### Post by Thirtysixway on 2009-01-16
Did you forward ports on your router to your server?

---

### Post by Iowan on 2009-01-16
> **hossiam said:**
> ...  the problem is from another computer on my network i get... Is the problem getting to the server from the internet (outside your network) or accessing it from another machine *inside* your network? The inside machines will either need to have /etc/hosts file edited - or local DNS.

---

### Post by hossiam on 2009-01-16
I enabled appllicatins

Current Settings: Custom
Allowed Applications 	Port Number(s) 	Public IP
 	 VNC 	- 	TCP 	5500
	
			TCP 	5800
	
			TCP 	5900
	
	  Web Server 	- 	TCP 	80
	
	SSH Server 	- 	TCP 	22
	
	FTP Server 	FTP (file transfer protocol) server 	TCP 	21



There are some more options on my router.....

Public Proxied Subnet (NAT/Routed)
Enable
	This value will determine the public addresses available for using applications with your home network devices.

This information is provided by your ISP

	Internet Network: 	xx.xx.x.xx / xxx.xxx.xxx.xxx
	Subnet Mask: 	
Warning
	Auto Application Support Open
	Default DHCP Pool

---

### Post by hossiam on 2009-01-16
Iowan both...here is my hosts file

127.0.0.1	localhost
127.0.1.1	server
*:80   example.org(got this dns name from no-ip.com)


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


the * is actually * not trying to hide info.

---

### Post by hossiam on 2009-01-16
I do love Ubuntu....thats why im using it on two of my home computers....but as a newbie do you think it would be easier just to use windows?...WAMP...I don't want to sound like some college girl who bought a netbook from DELL...:P....but so that I don't keep asking such basic questions and troubling the pros.

---

### Post by mr.generic.user on 2009-01-17
review starting with the basics:

1) can you browse a page from the server itself (127.0.0.1)...  verifies that the server is running.

2) can you browse a page from another computer on your LAN using the server's LAN ip address (ie: 192.168.1.x)... verifies that the server's firewall is not blocking the port.

3) is your WAN (Internet) IP registered with no-ip.  i use dyndns.org and i have my router set up to update my dyndns.org address when my WAN IP changes.  that way DNS servers can reroute as needed.  you should be able to find out your wan ip address from your router's status page.

4) can you ping your WAN IP address?  if you can, try to ping your domain name.  in linux it will also show on the command line what WAN IP the DNS servers think it should be.

5) is WAN port 80 routed on your router routed to port 80 on your server.  your server should use a static LAN IP.  this will cut down on problems

6) is port 80 blocked by your ISP?  mine is.  i use port 8080 on the WAN side of the router, and route it back to port 80 on your server.  then all i have to do from a remote computer is type the address differently, ie:  

*my_dynamic_domain.org:8080*

now, though that is not my actual domain name, that is exactly how i use it.  for subfolders it would be *my_dynamic_domain.org:8080/subfolder*


let me know if any of this helps.  i will watch this thread for a while to see what happens.

---

### Post by hossiam on 2009-01-17
1. good
2. good
3. good
4. good
5. your server should use a static LAN......I followed a step by step for this and ended up having no connections at all.
6. on my router it says its open

Thank you for taking you time out of your day to help......this is for everyone.

---

### Post by mr.generic.user on 2009-01-18
if you are still having problems with step 5+....
example below assumes router LAN is 192.168.1.1/255.255.255.0

LAN static ip: (in case step by step was different from below)
1) *sudo -i*  (changes to root, better than sudo each command)
2) *ifconfig eth0 down*  (exchange eth0 to correct interface usually eth0 for fisrt NIC)
3) *ifconfig etho 192.168.1.2 netmask 255.255.255.0 up*  (sets machine's LAN ip to 192.168.1.2)
4) *route add default gw 192.168.1.1*  (tells the machine where to go to find networks outside your own, ie: internet)
5) edit /etc/resolv.conf , remove all lines and add these

```
    nameserver 4.2.2.1
    nameserver 24.204.0.4

```

that sets static dns servers.  (if you still have gnome network manager, all this will be undone at next boot.  if this works you can uninstall the network manager and redo this to make it permanent.  if you get everything working this way i will find a step by step for removing network manager for you, i had to do that on my machine.)

if everything is good, you should be able to *ping google.com*



as for the port 80 issue, your router is likely not blocking it, but your router might not be able to detect if your ISP's routers are.  may still be worth a try if the above static ip stuff helps.

---

### Post by hossiam on 2009-01-18
Thanks again...I will try those steps but I just want someone to look at my error first to determine if its OK to go ahead.


I did some tinkering myself.....might have been a bad idea.....I dont know if i sould do a reinstall or if there is just on or two lines i need to fix.  OK the only files that I have been changing are hosts, httds, and sites enabled/available.  Now I getting this error.

* Starting web server apache2
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!

---

### Post by hossiam on 2009-01-18
OK uninstalled and reinstalled everything...here is what i did the only difference is that I am using ubuntu 8.10 not server edition....i need me some gui....
[http://nettuts.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/](http://nettuts.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/)
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)
registered a dyndns and downloaded inyadn [http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

My server times out when i put my wan in my browser and when i put my dns in.

checked  my port 80 [http://www.canyouseeme.org/](http://www.canyouseeme.org/) all is ok

tried this [http://www.dyndns.com/support/tools/dnsquery.html](http://www.dyndns.com/support/tools/dnsquery.html) but don't understand what im lookin for.

Also went through all this [http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html](http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html)

I didn't edit the hosts file or the httpd file this time.

site available file looks like this

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName [www.example.org(my](www.example.org(my) real site not example)
	DocumentRoot /var/www/Trial/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/Trial/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Any more help would be great.

---

### Post by mr.generic.user on 2009-01-18
ok, hmmm....  make sure that the WAN IP your router shows you on its status page is the same as the one you see here:
[http://www.whatismyip.com/]("http://www.whatismyip.com/")

if not, try using the address you see on whatismyip.com in your browser to see if that works.

also make sure your router has any 'remote configuration' or 'remote administration' turned off (just in case).

i know this may sound old, but have you tried routing port 8080 from your router to port 80 on your server just to see if it acts differently?  if not, when you do, make sure you have disabled the remote configuration on your router, it usually uses this port by default.

another thing you could try to see if there is a router setting that was somehow missed is to _temporarily set your SERVER LAN IP as the DMZ HOST in your router and remove any forwarding for port 80/8080_.  this exposes your server entirely to the internet, but that is why you only do it for testing.

what is the make and model of your router and cable / dsl modem?  what ISP?

---

### Post by hossiam on 2009-01-19
OK a friend outside of the network can access my web page by trying the ip address.  Which made me extremely happy.  The dns on the other hand will not display.   So what do you think?   Thanks for the help so far I ve learned plenty.   If i put my IP external ip from whatsmyip.com i cant see it.

OK I finally figured out the issue with the domain name and external IP in local browser.   For those who are having this same problem  in your etc/hosts file you must put 

127.0.0.1	localhost
127.0.1.1	ubuntu
*192.168.x.xx*      *yourdnsordomainname.org*
the ip address in front of yourdnsordomainname.org is your local ip for that computer/server.....you can fin this by opening your terminal and typing *ifconfig*  look for the number next to inet addr: thats your internal ip.  I know it's basic for most but it helped me with my internat problems now onto my external problems....

---

### Post by mr.generic.user on 2009-01-20
OK, if the WAN IP your router reports to you allows a remote friend to access your site, but the one you get from whatismyip.com does not, then the one on your router must be correct, and the one you get from the site is a gateway ip from your ISP.  make sure to completely remove your dns update software.

instead of using a software to update your dyndns.org account, look in your router configuration for a 'Dynamic DNS' configuration.  you should be able to set it up with your dyndns.org account and have it update your WAN IP correctly.  the software you installed to update your dyndns.org account is going to use an internet IP lookup page just like the site i gave you, whereas your router will use its own WAN IP address instead.

let me know if that helps.  if you have trouble finding / configuring your router's dynamic dns settings, post your router's make (encore/linksys/etc) and model number so i can look up the documentation and see if i can help there.

---

### Post by hossiam on 2009-01-20
You solved it.......it was the software I installed from the dns domain name hosting company. It did not update my IP.   It used the first on I put in manualy, has since changed.  All is good now.  Thanks for hanging in there mr.generic.user.  I am glad I stuck with Ubuntu.  All thanks to your help and the communities.

---

