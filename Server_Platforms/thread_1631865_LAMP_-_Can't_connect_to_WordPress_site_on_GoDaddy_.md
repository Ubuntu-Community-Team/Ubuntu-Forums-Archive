---
title: "LAMP - Can't connect to WordPress site on GoDaddy domain behind router."
date: 2010-11-27
forum: Server Platforms
---

### Post by eeffoc on 2010-11-27
Hi folks, I've got Meerkat running as a VMware image; I've statically assigned the IP address of 192.168.1.106 to it, as well as went into resolv.conf and set my domain (itscol.es), the search (search.comcast.net || as comcast is my ISP) and have three nameservers: the first being 192.168.1.106 and the final two are the actual IP's (xxx.xxx.xxx.xxx) of GoDaddy's nameservers, which is where I am hosting the site. Now, I have forwarded port 80 for 192.168.1.106 through my routers admin page. I can access my site from anywhere outside my external network, but when trying to access the site behind my router (on my local home network,) I am greeted with GoDaddy's 'free parking' page...Any ideas on what I did wrong? Thanks in advance for any input whatsoever... if this is the wrong section, I am sorry! ;)

---

### Post by windependence on 2010-11-27
You cannot access your site from the internal network because your router does not support NAT reflection. 
 
An easy fix for this is to add an entry in your /etc/hosts file like this:
 
```
 
192.168.1.106 itscol.es

``` 
 
It should work fine then, you may need to clear your browser cache.
 
-Tim

---

### Post by eeffoc on 2010-11-27
Awesome; thanks for the reply. I've actually determined that my domain was 'parked' via GoDaddy by trying to connect to my site from work: I was WebSensed due to the fact that it was a parked domain. SO...after logging into GoDaddy and resetting my nameservers, with hopes of unparking my domain, maybe that will help. That's the only info I could find -- not sure if it's related to my initial problem, as I did what you instructed, which allowed me to see my site inside my LAN. >_< Thanks again for the info! :D

---

### Post by eeffoc on 2010-11-27
Just for anyone who needs to know -- after clearing my cache on the browsers I use, I was able to connect to my site at work without getting WebSensed; resetting the nameservers in order to deselect the 'park your domain' from GoDaddy worked. As previously mentioned, Tims fixed in the second post worked for my LAN. <solved>case|closed</solved>.

---

