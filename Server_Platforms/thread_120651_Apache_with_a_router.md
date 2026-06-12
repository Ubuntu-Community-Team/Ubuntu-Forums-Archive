---
title: "Apache with a router?"
date: 2006-01-23
forum: Server Platforms
---

### Post by `rAwr on 2006-01-23
I'm trying to set up a webserver on my Ubuntu machine.

I forwarded port 80 thru the router, but for some reason still cannot connect to my webserver via my IP address.
I can connect locally thru the network, using 192.168.2.12.

I figured it might be that port 80 is blocked.

So I configured Apache to Listen on port 8080 and forwarded that port to 192.168.2.12 aswell (the Ubuntu machine).

I can connect locally from any of the computers on my network thru 192.168.2.12:8080, but still cannot thru my WAN IP.
69.69.122.111:8080

If I configure Apache to Listen on port 80, it just connects directly to my DSL modem configuration page with 69.69.122.111
I assume I must do something with the remote management?
[IMG]http://img.photobucket.com/albums/v724/OMFGplz/modem.jpg[/IMG]

I don't know how to use/turn off the remote management :/

I NEED HELP!! !:(

---

### Post by Horndog on 2006-01-23
Seeing as how you have a router I presume you have other computer on your LAN. Check your IP using "ifconfig" and use *that* IP to forward port 80. Not having that kind of router I can only guess that you put the IP address on the bottom right under "web". and change "LAN only" to what ever it takes to let WAN requests in at that port. BTW Most router come, as default, DHCP enabled.
That means you have a dynamic IP "It will change at some point" so your setup might not be valid the next time you reboot your computer.

*EDIT* Internal IPs are not available through the Internet so you have to use you Internet IP  to access your server through port 80.

---

### Post by sent_by_LUG on 2006-01-23
It isn't remote management that you need, in order for the outsite world to see your server behind a firewall you need to set it up in a DMZ or set up your router to forward any request to port whatever to the internal IP address you want, it is sometimes a setting called public lan server or something to that effect. One peice of advice though, turn off remote administration unless you absolutely need it.

---

### Post by spectre_25gt on 2006-01-23
The biggest thing I'd be worried about at this point is that it looks as though you've got two NAT boxes on your network so you have two LAN's going: 192.168.2.0 and probably 192.168.1.0 (the screenshot didn't show your modem's internal address). Your computers seem to be on 192.168.2.0. Is your router doing wireless or is there some other reason that you need it? If not, your modem should be able to handle NAT and you should be able to remove the router. That will simplify things rather than forwarding twice.

Also, a good site to test whether a given port is open or not is: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2). They have a test that will check specific ports for you.

---

### Post by `rAwr on 2006-01-23
Well I turned off DHCP and set a static IP to the linux machine was 192.168.2.37.
I changed the port forwarding to forward port 80, and 8080 to the static IP (192.168.2.37)

[IMG]http://img.photobucket.com/albums/v724/OMFGplz/router.jpg[/IMG]
And I also did the same with my modem's port-forwarding.
[IMG]http://img.photobucket.com/albums/v724/OMFGplz/modem2.jpg[/IMG]

But it still does not work if I try to connect to 69.69.122.111:8080
Maybe it works for someone else?

---

### Post by Horndog on 2006-01-23
Aside from maybe your OS firewall (Firestarter) I would go to the ZyXEL site for more help.

---

### Post by herrpoon on 2006-01-23
Hi, I don't think it's actaully possible to connect to your webserver on a local mahcine via your external IP i.e. 69.69.122.111:8080, what ever port you forward!  However, other people (people not on your LAN) should be able to connect to your webserver with 69.69.122.111:8080.  

I remember having the exact same problem when I first set up my webserver!

---

### Post by Horndog on 2006-01-23
[QUOTE=herrpoon]Hi, I don't think it's actaully possible to connect to your webserver on a local mahcine via your external IP i.e. 69.69.122.111:8080, what ever port your forward!  However, other people (people not on your LAN) should be able to connect to your webserver with 69.69.122.111:8080.  

I remember having the exact same problem when first set up my webserver![/QUOTE]

Agreed. My router (Linksys) is able to do Internet loop back but some can't. Have some one try from outside your LAN.

---

### Post by `rAwr on 2006-01-23
Now everything has just gone more downhill than it was before..

Now I don't even get routed back to the modem configuration page when I type my WAN IP with the port extension.

Can anyone view my website?

[http://71.48.109.215:8080](http://71.48.109.215:8080)

Oh yes.. And I can't go to my router configuration page..

---

### Post by Horndog on 2006-01-23
No joy. I can't see your site.

---

### Post by GTvulse on 2006-01-23
`rAwr

You have set up your router with parameters that work with it. 

You see, home routers are Class C, that is, they only cover 256 addresses (and that the very expensive ones, most won't do more than 20 or so). Therefore, be consistent and set up all your LAN addresses within the range 192.168.1.xxx where xxx is some value between 0 and 20 (to be sure it will work). And remember, the authoritative source of information on your router specifications is the manual (if you don't have a copy the manufacturer should have PDFs in its web site.)

You'll have to do a hard reset in your router if you screwed up your LAN addresses as your last post suggests.

---

### Post by MJN on 2006-01-23
Incidentally, and quite unrelated to your current issue, you don't need to forward UDP traffic for HTTP and FTP - they're run over TCP.

Mathew

---

### Post by spectre_25gt on 2006-01-24
Something strange happened when I posted and it put my post towards the beginning of the thread... Anyway, I'll repost so it actually gets seen.

--

The biggest thing I'd be worried about at this point is that it looks as though you've got two NAT boxes on your network so you have two LAN's going: 192.168.2.0 and probably 192.168.1.0 (the screenshot didn't show your modem's internal address). Your computers seem to be on 192.168.2.0. Is your router doing wireless or is there some other reason that you need it? If not, your modem should be able to handle NAT and you should be able to remove the router. That will simplify things rather than forwarding twice.

Also, a good site to test whether a given port is open or not is: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2). They have a test that will check specific ports for you.

---

### Post by robinl on 2006-01-25
I experienced with this problem before and I tried to update the firmware things like that but with no use. I had to turn on DMZ and set the management page to other ports (and turn off ftp access). Hope it helps.

---

### Post by avintaquin on 2006-02-03
I have an older ZyXel modem and I have to forward some ports to my router first to get access from the web.
On my ZyXel adsl modem I forward specific port (my modem won't allow forward of a port range)to WAN address of Linksys router.
On my Linksys router I set up DMZ pointed at ubuntu server address.
Interesting thing is that if I set linux box to static ip everything breaks.  Being somewhat of a Newbie I haven't had time to figure out why yet.
But works great with ubuntu box set to DHCP.

---

