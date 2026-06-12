---
title: "Free Radius setup for my wireless"
date: 2009-05-28
forum: Security
---

### Post by StarThorn1 on 2009-05-28
I've been reading how to docs on Free Radius but none of them start at square one. 

I want this for my wireless. I wont to connect with TTLS and use my ldap/e directory to authenticate. I don't know what to put in the config files to make this happen. 

I'm looking at my wireless controller and its radius settings. it wants

Server IP address - Where do I type that in the config files?
Shared Secret format ACSSI or Hex -  I think I'll go with ACSSI
Shared Secret - Where do I tell in the config my shared secret?
Key Wrap check box - I don't think I will need this.
Port Number - has 1812 in this box by default
Server Status - I picked enable
RFC 3576 Support - I picked enable
IPSec - not sure what this is. It is not checked by default

I'll try and use this as my starting point....Plz help !

---

### Post by LEO_Servers on 2009-05-28
Are you willing to try some new software. Using monowall you gain the ability to set up a radius server and ipsec ect.. A Prety compleate free FireWall Program and their Documantion they have on there site is actualy preety nice and orginized they also give Examples on there site as to what you need for the information 
[http://m0n0.ch/wall/](http://m0n0.ch/wall/)
[]("http://openwrt.org/") 
This is just one great program Are you trying to set up a rtr or just a 2nd pc as a FW Authencation Server mix Just give me some more detail and i shuld be able to answer your quistions.
 
OpenWrt is anouther great choice that if you are using a linksys router gives you the ability do just about everthing a nice 500+ cisco router can do.
[http://openwrt.org/](http://openwrt.org/)
 
Good Luck in your Network setup.

---

### Post by StarThorn1 on 2009-05-28
I want to setup a server with Free Radius on it. I'm using 4404 cisco controller and all cisco AP's

when somone wants to connect to our open SSID, I want that trafic to be encrpyted with ttls. 

I don't know how to edit the config files in free radius to set this up.

---

### Post by LEO_Servers on 2009-05-31
ok i found a great start for you his website [http://rbirri.9online.fr/howto/Freeradius_+_TTLS.html](http://rbirri.9online.fr/howto/Freeradius_+_TTLS.html) hope that helps.

---

### Post by HermanAB on 2009-05-31
Maybe this will help:
[http://aeronetworks.ca/radius.html](http://aeronetworks.ca/radius.html)
[http://aeronetworks.ca/prepaid.html](http://aeronetworks.ca/prepaid.html)

---

