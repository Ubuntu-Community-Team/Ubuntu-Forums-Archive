---
title: "Remote access issues, connecting from windows and iphone"
date: 2011-05-18
forum: Server Platforms
---

### Post by koshiuk on 2011-05-18
I've installed teamviewer on my 11.04 ubuntu pc at home, which i can access fine using teamviewer on my iphone which is great but ideally i would like FTP access to see my photos / documents.

I've just started playing with this so please let me know if ive done anything wrong.

Registered with dyndns and linked the url to my external ip address, when i connect i just get the router login page.

Is this because i havent yet setup FTP server or is my port forwarding incorrect?  

And which FTP server should i use on ubuntu, must be able to connect via windows and iphone (3g)

Many thanks.

---

### Post by volkswagner on 2011-05-18
Your router must have a setting to enable/disable remote access.  Remote access enables configuring the router settings from outside your lan.  Once this is disabled, and you have port 80 forwarded to your server you will be able to view your webserver.  

If you want to use ftp from outside your LAN you will need to open port 22, or whichever port you configured for your ftpserver.

Check out an app for iPhone called EZ-Share.  It has a lot of great features including RDP/VNC, it can connect to SAMBA shares, has a Wakonlan utility, it can also make your iPhone act like a NAS on your network.

---

### Post by koshiuk on 2011-05-18
thanks for the info, will give that a go...  ive set my router (dlink) to port forward

192.168 <local ip>   protocol TCP, public start port 80, public end port 80.

i'l open up the FTP port 21 also later...

and enable remote access lol - missed that one.

many thanks

---

### Post by koshiuk on 2011-05-18
also do i have to have port forwarding and remote access enabled for team viewer to work?

---

### Post by spynappels on 2011-05-18
> **koshiuk said:**
> also do i have to have port forwarding and remote access enabled for team viewer to work?

Nope, it should just work.

I think Volkswagner was saying that you need to Disable remote access, as this is why you were getting the router config page when navigating to your DynDNS URL. Or were you doing that from inside the network?

---

### Post by koshiuk on 2011-05-18
got you ok thanks....... yeh router login page was coming up when on the internal LAN and typing in my dyndns address. 

cheers.

---

### Post by HermanAB on 2011-05-18
Please avoid FTP and rather use SSH.  It is easier to get to work and it is secure.  A good combination.

---

### Post by spynappels on 2011-05-18
> **koshiuk said:**
> got you ok thanks....... yeh router login page was coming up when on the internal LAN and typing in my dyndns address. 

cheers.

That suggests that your router does not support you accessing the Public IP (or DynDNS URL) from inside the LAN, that is very common. Check your DynDNS URL through a proxy service to see if it is accessible from outside your LAN, or use your iPhone on 3G rather than WIFI.

---

### Post by koshiuk on 2011-05-18
> **spynappels said:**
> That suggests that your router does not support you accessing the Public IP (or DynDNS URL) from inside the LAN, that is very common. Check your DynDNS URL through a proxy service to see if it is accessible from outside your LAN, or use your iPhone on 3G rather than WIFI.

thanks, ive accessed my dyndns.org URL fine from [www.proxy-service.de](www.proxy-service.de) so looking good? just need to know when the 
**Index of /**


is now on my hdd?    suppose thats where i put the index.html, and use Komposer?

---

### Post by spynappels on 2011-05-18
The webroot on the default Ubuntu webserver is in /var/www where the default index.html is located. Replace this with your own index.html to see if this is what you need.

---

### Post by koshiuk on 2011-05-19
> **spynappels said:**
> The webroot on the default Ubuntu webserver is in /var/www where the default index.html is located. Replace this with your own index.html to see if this is what you need.

many thanks....

---

### Post by koshiuk on 2011-05-19
> **koshiuk said:**
> many thanks....


Getting a http error 504 error now... think i need to get the book out.....

---

### Post by koshiuk on 2011-05-19
> **koshiuk said:**
> Getting a http error 504 error now... think i need to get the book out.....

ignore my last comment!  the ip address of the server changed, fixed ip and sorted.

---

