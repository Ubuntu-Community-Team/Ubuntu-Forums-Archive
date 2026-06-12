---
title: "Firefox, Google's spyware machine. Ubuntu's Firefox flavor isn't clean."
date: 2009-01-16
forum: Security
---

### Post by Percolator on 2009-01-16
I just created a new Ubuntu partition for doing sensitive things (internet banking). Wanting to make the chances of compromising as little as possible I removed most of the non necessary applications of my Ubuntu, scanned my drive and some other stuff. I also had to do the usual new-firefox-needs-cleaning (wander how many times I've already done that :-S )

 - Deleted the "bookmarks" on the Bookmark Toolbar (they do a call home and no, BBC is stupid so why the f*** is it on it)

 - In the preferences I disabled Java (if some site is carrying Java applets everything goes way too slow)

 - I also disabled the cache, all forms of form collecting data and cookies will (off course) expire after Firefox exits
, DUH
 - And finally I also disabled all update checks



After going to the banking website everything seemed fine until.... about after 2 minutes. EtherApe was open and I saw some communication with the Google servers. First I thought the banking website was insecure by adding hidden third party links. After double checking that, I could exclude that option.

Then I used Wireshark to see what exactly was happening and saw calls like the following:

926	33.823524	74.125.100.26	************	HTTP	HTTP/1.1 200 OK  (application/vnd.google.safebrowsing-chunk)


Never having installed an application sounding like safebrowsing I double checked everything and couldn't possible find anything still linking my browser to Google. I rebooted to be sure, started Firefox and waited. After about 2 minutes it would reconnect to the Google servers again. I found something about Safe Browsing being part of Chrome and it being a data collecting tool for Google (what do you expect).
After hours of browsing I finally figured out what was happening. Because Firefox thinks I'm an infant who can't look out for himself and I was doing secure HTTP some secret invisible Google plug in you can't even uninstall was checking if my secure URL wasn't spoofed. So how are you supposed to turn it off? By unchecking "Tell me if the site I'm visiting is a suspected attack site" and "Tell me if the site I'm visiting is a suspected forgery".

Why isn't there any indication that those two check boxes are linked to Google instead of being a list-free algorithm or something part of Firefox :mad:

---

### Post by bodhi.zazen on 2009-01-16
Just blacklist the google empire with iptables or UFW or what have you :)

If you use iptables you can block in and out bound connections.

---

