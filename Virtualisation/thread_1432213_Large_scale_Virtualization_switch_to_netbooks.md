---
title: "Large scale Virtualization: switch to netbooks"
date: 2010-03-17
forum: Virtualisation
---

### Post by UranUtan on 2010-03-17
Hi,

This is a crazy idea, I am not sure if this is the right place to ask. If you have any similar experience, I would appreciate any advices or comments.

The idea is to go light & green. Everybody at the office will use a light client like a small netbook. For people who still need a powerful computer, it will be virtualized in a centralized infrastructure and the VM will be accessed by remote control.

Do you think if this is a realistic scenario and if achieveable, what would be the most obvious shortcomings?

Thanks in advance.

---

### Post by nerdy_kid on 2010-03-17
all the workers would have to buy glasses after the first week
:lolflag:

netbook screens are too puny IMO

thats my 2 cents :D

---

### Post by UranUtan on 2010-03-17
I see what you meant. Me too I prefer bigger screen.
The scenario above, let's say "netbook" means a netbook or a not very expensive laptop, or people can still use an external monitor.

The main question I would like to have an answer is if it is viable to virtualize all workstations and what kind of changes that would imply. Of course, the goal is to provide an equal or better user experience at a, hopefully, greener or lower cost.

An analogy. Email & Cloud storage are convenient as data storage, this brings a change in habits. I use less often USB key and never need a floppy.

---

### Post by netztier on 2010-03-17
> **UranUtan said:**
> 
Do you think if this is a realistic scenario and if achieveable, what would be the most obvious shortcomings?


Not really new, there's already products on the market for that.

[http://en.wikipedia.org/wiki/Virtual_Desktop_Infrastructure](http://en.wikipedia.org/wiki/Virtual_Desktop_Infrastructure)

Thin client hardware on the desk, and some "rather big iron" down in the comms room offering one virtual PC per employee.

Thin client hardware in notebook or netbook form, ubiquituous WiFi and 3G, a bit of VPN for security - done. No PCs required. No local storage on the devices, no data loss when one gets lost or stolen.

best regards

Marc

---

### Post by PhilGil on 2010-03-17
We're already doing that in our office - our infrastructure is hosted in a server farm half a continent away.  We access our "office desktops" through remote desktop software.

There are many advantages to this strategy: IT support is easier to obtain and less expensive as there's no need to maintain a local server, small companies (such as ours) are able to take advantage of "economies of scale" by pooling IT resources, and local hardware has a longer lifespan as the system requirements are low (even while running the latest software in the remote environment).  In addition, staff can work from anywhere as long as they have an Internet connection and a remote desktop client 

There are also some disadvantages: you're unable to work without an Internet connection,  your hosting service (instead of local IT staff) is responsible for data security and backups, graphics-intensive operations (image editing, PDF file manipulation, web surfing, etc...) perform poorly due to bandwidth limitations, and support hours don't always coincide as our server is in a different time zone.

The biggest annoyance with working on a netbook is (as an earlier poster pointed out) limited screen real estate.  I have no problem running rdesktop on my 10" netbook, but the native resolution of our remote environment is 1024x768, so I have to do a lot of scrolling on my 1024x600 screen.

---

### Post by UranUtan on 2010-03-17
Hi,

Thanks very much for your inputs. So it sounds like the idea is worth a try. Now one step closer to practice for some proof of concept. What is the Virtual Desktop Infrastructure (VDI) would you recommend or that you have heard good about? (Free, Open, or even Commercial)

I've read an article (suggested by netztier above, thanks) for some complement of info: 
[http://en.wikipedia.org/wiki/Virtual_Desktop_Infrastructure](http://en.wikipedia.org/wiki/Virtual_Desktop_Infrastructure)

But I don't know any of the products cited in the "Providers" section. Hope I can get some help to reduce the evaluation time to pick a product.

Also how do you cope with multi-media applications such as Conference call, Video chat, etc?

---

