---
title: "community broadband"
date: 2008-03-26
forum: Server Platforms
---

### Post by ully-mick on 2008-03-26
Hi, 
this is my first post here, so forgive me if I've posted in the wrong forum.
I live in a UK village with limited broadband, we're right on the limit. the max is 0.5 meg if you can get it at all, which over half the village can't, and for the rest it's somewhat flaky.
So a few of us got together and formed a company, a not for profit community broadband company. we've registered and applied to different bodies for funding for equipment.
we will be running a microwave link from the town 5 miles away from right next to the exchange. we have a clear line of sight from a friends company rooftop next door. we already have some equipment for testing, so we do know it will work.

my job is to set up a test server which i've done out of bits I have. I've installed ubuntu desktop which I would rather use because I'm used to a gui and also I need to show others how to access it.

simply put, there will be a microwave receiver coming down to a server on one lan card then out of the other lan card to a router and up to a transmitter/receiver that people will be able to see and connect to with their normal wireless dongle.
the bit I need help with is the server. I need software to setup usernames and passwords for each member so it can be made secure. also, would it be possible to access it remotely to add new members.
any help will be greatly appreciated by me, and probably by others in the same situation.

thanks in advance.
Mick

---

### Post by cdenley on 2008-03-26
I think you could either use a VPN server or a captive portal. It's been too long since I've set up a VPN server, and I don't know of an easy way to create a captive portal.

No matter what you do, it will always be possible to make changes remotely if you set up ssh (and vnc if you need gui).

---

### Post by bodycoach2 on 2008-03-26
I'm actually attempting to set up something like this, using WiFiDog as a portal:
[http://dev.wifidog.org/](http://dev.wifidog.org/)

The instructions for setting it up on Ubuntu Server:
[http://dev.wifidog.org/wiki/doc/install/ubuntu/auth-server](http://dev.wifidog.org/wiki/doc/install/ubuntu/auth-server)

I'm testing it out in VirtualBox first.

---

### Post by ully-mick on 2008-03-29
thanks for your help guys. I'll be having a go this weekend. :)

---

