---
title: "Cannot access website - except on server computer"
date: 2009-01-12
forum: Server Platforms
---

### Post by R.Bucky on 2009-01-12
Here is the deal - I have my Ubuntu Desktop server on the same router as my personal computer used for browsing the web and such. I have a static ip with my ISP. But, whenever I try and view my webpage with a computer on the network, it brings up the login screen for my router. 

I can view my pages just fine on my server box. But, any other computer on the network gives me the router config. 

What gives?

---

### Post by rickyjones on 2009-01-12
Have you forwarded port 80 from your router to your server?

Sincerely,
Richard

---

### Post by R.Bucky on 2009-01-12
Yup. see screenshot

---

### Post by rickyjones on 2009-01-12
Interesting. Well I know forwarding is working since I can access your site. It sounds like this router does not know how to send internal traffic to the internal server correctly. For the time being you could setup DNS services to service the internal clients. Otherwise use the internal IP?

Beyond that I might replace the router with a different one. I notice that that is the Comcast modem/router, correct? You might be able to configure it to pass the IP to another router and that might work.

Thanks,
Richard

---

### Post by R.Bucky on 2009-01-12
I switched over to the business account with Comcast around a month ago; I have to use this modem/router combo that they provided because it is configured for my static ip. I could always clone the MAC address with another router if I got desparate. 
The internal IP also shows the router config screen (quite annoying). I have also attempted to plug another router off of the comcast router with zero success. Ergggg!

---

### Post by Iowan on 2009-01-13
What is the IP of the router? The server?  You don't necessarily need to post them, but they should be different (I suspect the server is in a private IP range).  The local machines should be using the server's local address instead of the router address.

---

### Post by R.Bucky on 2009-01-13
My router ip follow the schema of 10.1.10.1, with every computer on the router assigned a different number after the 10.1.10."1". My server ip is 173.10.77.142. I was thinking that my server's /etc/hosts file might be causing the problem? the contents of the /etc/hosts below:

```
127.0.0.1 localhost buckyspalace.net
173.10.77.142 buckyspalace.net
```

I attempted to use the local machine (non web server box) to access my server with the 10.1.10.X address with zero success. However, when I use my server to access the localhost using the 10.1.10.X that I have on my regular box, it comes up just fine.

---

### Post by R.Bucky on 2009-01-14
Still a no go with serveral variants on my /etc/hosts file. I am open to any suggestions to resolve this problem...

---

### Post by stefangr1 on 2009-01-14
I have seen some routers with an option to allow access from the web to the configuration-ui. I think it is somewhat abnormal that you get to the configuration page when you browse to your ip-address (doesn't sound like default behaviour), so maybe your router is configured somehow to also listen at port 80 which might conflict with your NAPT rules!

---

### Post by R.Bucky on 2009-01-14
Thanks for the idea. I logged in to my router admin page (not too difficult to find - ehhhh) and deselected port forwarding on 80. No change what-so-ever. 

I called comcast and asked their business technical support if the router can handle internal traffic from an internal server - their response was "yes, absolutely." The only confusing thing that the rep. told me was that my static ip (173.10.77.142) was my outside ip, while 173.10.77.141 was my usable ip. What the heck does that mean? Netword Solutions has the .142 address, which works fine for seeing my pages, except on the network that is...

signed - still annoyed! Any other ideas?

---

### Post by stefangr1 on 2009-01-14
You should leave port 80 forwarding on, but in stead have a look into the "Admin" tab I see on the left side of the picture you posted. As you can access your admin page from the web, I figure that something must be enabled there to listen on port 80 (such that the NAPT configuration is ignored).

---

### Post by R.Bucky on 2009-01-14
The admin tab contains only the password change and a ping/tracerouter tool. Yes, went back and enabled port forwarding again.

---

### Post by Iowan on 2009-01-14
Try the following in your /etc/hosts file:```
127.0.0.1 localhost 
127.0.1.1  buckyspalace.net
#10.1.X.Xbuckyspalace.net
``` The port forwarding should get inbound traffic directed to the server.  If this doesn't work,

OOPS - dupe

---

### Post by Iowan on 2009-01-14
Try the following in your /etc/hosts file:```
127.0.0.1 localhost 
127.0.1.1  buckyspalace.net
#173.10.77.142 buckyspalace.net
``` The router should have the 173.10.77.142 address on it's "external" port.  The server should have an internal address - 10.1.10.X (but outside the DHCP range the router is using).  The port-forward in the router should redirect port 80 to the server's (internal) address.

---

### Post by R.Bucky on 2009-01-18
Modified my /etc/hosts file to the previous post. Restarted server box with no success. I have figured out that I can access Webmin and phpmyadmin from a browser by using my server hostname (e.g. [https://hostname.local:10000](https://hostname.local:10000) or [http://hostname.local/phpmyadmin](http://hostname.local/phpmyadmin)). It really seems like my router cannot handle an internal request to my webserver from a box on the network.

Any networking gurus out there right now listening? I am certainly not! :-)

---

### Post by cariboo on 2009-01-18
If you use the actual ip address of the server can you access it. The external ip address is for the router, and it forwards the packets to your server.

If your internal addresses are 10.1.10.1 and higher, the servers address on your internal network should be some variant of 10.1.10.5, you then forward that address to your router.

After changing the ip address you should be able to access the server from the internal network without having to loop around and back into your router.

Jim

---

### Post by R.Bucky on 2009-01-18
Thank you for responding. I attached a couple of screenshots to let you see what I am seeing. I am still unable to view my webpage. My static ip does not provide access to my page either. However, anything outside of port 80 is still viewable within the network. I am beginning to think that the networking gods have it in for me. 

Any other thoughts?

---

### Post by mr.generic.user on 2009-01-19
try removing all but the loopback (127.0.0.1) from hosts

check /etc/apache2/ports
make sure it is has:
```
NameVirtualHost *:80
Listen 80
```

mine look like this:
```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```


if NameVirtualHost is 127.0.0.1:80, it can only be accessed by the local machine because that is the loopback on all machines.

then check */etc/apache2/sites-enabled/000-default*  (or yours if different from default)

```
<VirtualHost *:80>
	...
</VirtualHost>
```

(... is not literal)

then run
```
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```

see if that makes the server visible from other pcs on the local network.

in client browser:
[http://(server](http://(server) lan ip)/


also if you can, try hooking up just the server and a test client to a router (with no wan hooked up) to see if the comcast equipment is blocking something...

---

### Post by R.Bucky on 2009-01-19
I double-checked my ../sites-enabled/default to ensure that the NameVirtualHost directive was was ported to 80. Also, the /ports file was just fine as well. Restarted the server. Nada.

The loopback and localhost used in my *server box* bring up my page, just not on any other PC or box on my network. I find this issue very strange because I can visit Webmin and VMWare Server using my domain name and port number; anything but port 80! Thought about changing the port...

Because I have a business account with Comcast, they gave me this crazy modem/router combo. I would need to clone the MAC address to hook up any other router setup.

---

### Post by R.Bucky on 2009-01-19
Another strange thing. I use FF3 on Ubuntu and IE7 on Vista for the other 2 boxes on my network. When I visit the addresses servername.local i can see on the lower bottom left of the browser that it is pulling "buckyspalace.net" and then a couple of my scripts. But, no page. Even more fascinating... It just times out

---

### Post by R.Bucky on 2009-01-21
I DARE YOU TO FIGURE THIS ONE OUT!!!

Ok, this is strange. The issue is still not resolved. However, I have made some progress. 

I can visit some of my pages using [http://hostname.local](http://hostname.local). I currently use Concrete5 CMS, Wordpress, and Jibberbook on my site. I can completely view hand-coded PHP pages and Jibberbook (AJAX driven) no problem using the hostname.local. My wordpress pages only seem to bring up the content (words) without an CSS styling or images. My Concrete5 does not show anything. They simply time-out. 

Ha!

---

### Post by volkswagner on 2009-01-21
Sounds like permission issues with the individual files.  Make sure your .css and other files/folders have correct permissions.

---

### Post by R.Bucky on 2009-01-21
That sounded logical to me as well. However, I previously, and most recently, set all files to 777 with no luck. I also thought it was a problem with UFW not allowing the database through, but my text in Wordpress is fine. It is the Concrete5 portion that is killing me. I left a post on their forums with no response as of yet.
[http://www.concrete5.org/index.php?cID=4263]("http://www.concrete5.org/index.php?cID=4263")

---

