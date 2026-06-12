---
title: "Server 8.04 problems"
date: 2008-05-26
forum: Server Platforms
---

### Post by Wolf.Lexa on 2008-05-26
Ok to keep this short and sweet, I am new to linux and I just setup a server with 8.04 and all the base stuff installed fine but here are the problems I am running into:

1. when I run apt-get update or any program it fails to connect to the repositories

2. I tried to setup apache2 but it fails to work cuz it can't find the Fully Qualified Domain Name

now, I also have 8.04 installed as a second OS on my desktop and I can SSH into the server fine and I can ping websites with it so I know its connected to the internet. if there is anyone that can help, Please help, lol

---

### Post by rslrdx on 2008-05-26
you should be able to see apache even with the error about the FQDN.

what do you get when you try to access the server by ip address ?

try this too, directly at the server, or access it by ssh, and once logged in type, "w3m localhost" without the quotes. see what comes up, and if you do it using ssh, get a screenshot.  w3m is a text based browser, to quit simply press Q (means quit) and press Y to answer if you want to quit.

have you edited the repositories?

do the following from a prompt:

sudo nano /etc/apt/sources.list (hit enter)

use the arrow keys to navegate through the text.

the # (pound) sign means that the line is ignored. some lines are ignored by default, but at least you should have some enabled, meaning it doesnt have the # sign.

just check for now, make no changes yet.

once you done that, press Ctrl+X to quit, if it asks if you want to save the changes, hit N for "no"

post here what you see...


Have you checked the network settings?
maybe the system was setup using dhcp and was changed to static afterwards, and not hard at all to make a simple mistake there. That may cause the FQDN error and the updates.

---

### Post by Wolf.Lexa on 2008-05-27
ok, did all that and found out it was my router messing up. lol

---

