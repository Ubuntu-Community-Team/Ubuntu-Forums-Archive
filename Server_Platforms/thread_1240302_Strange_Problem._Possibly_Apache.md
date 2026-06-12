---
title: "Strange Problem. Possibly Apache"
date: 2009-08-14
forum: Server Platforms
---

### Post by borahshadow on 2009-08-14
Hi, I have a server that is used as a file server and a webserver mainly. Recently the webserver has not been used much. (I've been busy with other stuff and have not finished the site I am building) Today I needed to host a picture for some body and so I thought I'd just throw it on my server rather than use a service like photobucket or image shack. I put the file in place and tried to access it but it was not found. I then just tried to access my server through my dnydns subdomain and all I got was a stripped down version of my site. I tried again and I got
> Connection Interrupted
      
The connection to the server was reset while the page was loading

The network link was interrupted while negotiating a connection. Please try again.

Upon examination using firebug It was not loading some(most) of my pictures and style sheets. And sometimes it would not load anything hence the error above. 

       I've tried to restart apache, restart networking, and checked my port forwarding rules. Nothing has made any difference.
The only thing I have done lately that I would think could maybe be affecting this is to add another router (acting as a hub) to my network. However I don't know how that would interfere with the server as this is how my network is laid out

```

                                      --computer1
Internet--DSL Modem/router--New router-- computer2 etc
                          --server  
```  

Hopefully that makes sense Basically the old router modem combo serves the server and the new router and the new router serves everything else.

One outer quirk is that accessing it by using it's LAN IP address (eg. 192.168.1.2) it works fine. but if I try to access it from the internet (dnydns domain) then it acts weird.

The only other thing I could think it could be is my isp.

---

### Post by cdenley on 2009-08-14
It could be your ISP doing this intentionally. Do they allow web servers? Are you sure your two routers are configured properly? No conflicting DHCP servers or IP addresses? Did you try disconnecting the new router?

---

### Post by borahshadow on 2009-08-14
My ISP is Qwest and as far as I know they don't block ports and they allow servers. The server used to work just fine BTW. 
I configured the two routers correctly. The new one has dhcp turned off. There are no conflicting addresses that I know of. I have not tried disconnecting the new router but I don't think it is that as it is further down the line than the server.


EDIT
I just stumbled across this old thread of mine and I thought I would mark it as solved since I figured out the problem. I also wanted to post the solution in case somebody stumbled across it and I could be of help.

Solution:
My ISP with out my permission or notice upgraded my modem/router and the update appearantly made **loopback**not work properly. This is the function that allows me to access my network from inside using my public IP (or my dnydns domain name) So from the outside it still works just fine but from the inside I have to use the local IP (the one 192.168.X.X). To overcome this on my desktops I added my domain name to the hosts file and pointed that to the internal IP address.

Hopefully this can be of help to somebody.

---

