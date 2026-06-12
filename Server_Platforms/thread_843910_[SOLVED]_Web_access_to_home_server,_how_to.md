---
title: "[SOLVED] Web access to home server, how to?"
date: 2008-06-28
forum: Server Platforms
---

### Post by cmittle on 2008-06-28
I've set up Apache2 for access via a browser at it's IP from within my LAN.  One thing that I can't find is how to determine the IP address that I need to type in at my work computer to access this server.  Please advise me as to how I can determine this IP address.

One more thing that I need to determine is if I download a spreadsheet from here and make some changes, how do I go about uploading this file back to my server?

Thanks,
Cory

---

### Post by dominiquec on 2008-06-28
On your server, open a terminal and type in:

sudo ifconfig

That should give you the IP address of your server.

---

### Post by cmittle on 2008-06-28
That gives me the IP address something like 192.168.1.xxx which is going to be the same on the inside of most Linksys routers.  I'm looking for the IP address that I can type in outside of my LAN to access this computer.

Cory

---

### Post by windependence on 2008-06-28
Log on to your linksys and check the outside (internet) facing address. That is the address yo should use. Please note that if you have not purchased a static IP from your ISP, it will change from time to time although not too often usually. There are band aid solutions out there for this but it's best to just get a static IP. I only pay $4.95 a month for mine.


-Tim

---

### Post by MJN on 2008-06-29
If you browse to a site like [whatismyip.com]("http://whatismyip.com/") this will give you your public/WAN address in most cases.

Or [whatsmyip.org/more]("http://www.whatsmyip.org/more/") is even fancier (using Javascript to give some other info).

Mathew

---

### Post by hyper_ch on 2008-06-29
you should give your server a static ip

---

### Post by cmittle on 2008-11-06
I determined the IP of my router by logging in, it's shown on the front page.  I then forwarded the appropriate ports to my server through my router (22 for ssh, 5900 for remote desktop, 21 for ftp, etc..)

Now I can log in via ssh and/or rdesktop when/if I feel like it.  My last obstacle is going to be wake on PME so I don't have to leave the server run all day if I think I might want to log in.

cory

---

