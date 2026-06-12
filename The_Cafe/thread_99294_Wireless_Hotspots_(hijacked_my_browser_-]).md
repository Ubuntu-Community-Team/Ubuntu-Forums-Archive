---
title: "Wireless Hotspots (hijacked my browser :-])"
date: 2005-12-05
forum: The Cafe
---

### Post by Mr. Electric Wizard on 2005-12-05
I went to Starbucks the other day and I guessed that their WIFI access is free?  No, not free ($30 a month?).  WOW.
I always just assumed it was free.
Now I went to Panera Bread Co. and used theirs over the weekend, who is free by the way.
What I was intrigued by was how they could hijack my browser to open up to their customized Panera Home Page (only the first time I opened my browser).

Now I guess that it is some type of browser redirect at the time the DHCP lease is given out.

Anybody know how this works?  I would love to put one of these things up at home...

(Now I have a whole new outlook on the people that pay for this stuff at places like Starbucks - unbeleivable:???: )

---

### Post by Kvark on 2005-12-05
I've got a wild speculation guess about how that could be done, have no idea if it's correct or completely wrong and ridiculous...


I think the network traffic normally travels like this:

The page request is passed on from device to device until it reaches the server:
Browser -> Wireless Access Point -> Local Router -> ISP gateway -> Backbone Node -> Another Backbone Node -> Server

And then the page is passed on all the way back:
Browser <- Wireless Access Point <- Local Router <- ISP gateway <- Backbone Node <- Another Backbone Node <- Server


It should be pretty easy for the local router to stop passing on the request and instead send back a fake page (or maybe a real page from the server that has been cached earlier on the local router to save bandwidth) where the packets are made to look like they have been passed on all the way from the server's IP address.

Request gets stopped:
Browser -> Wireless Access Point -> Local Router

Fake or cached page that the router says is from the server:
Browser <- Wireless Access Point <- Local Router

---

### Post by ssam on 2005-12-05
if you make a http request through a router it can send back whatever it wants.

---

### Post by Mr. Electric Wizard on 2005-12-05
But this only happens once.  After the initial time, the browser maintains the previously recorded "home page".
For my router at home I use IPCop.  I wonder if there is a way using squid, to redirect to a nice "Welcome" page when a new lease is issued?

---

### Post by Mr. Electric Wizard on 2005-12-05
For anyone interested!
[http://publicip.net/]("http://publicip.net/")

Linux never ceases to amaze me!:p

---

