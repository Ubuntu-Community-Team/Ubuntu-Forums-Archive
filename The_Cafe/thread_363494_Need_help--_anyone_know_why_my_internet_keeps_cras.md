---
title: "Need help-- anyone know why my internet keeps crashing?"
date: 2007-02-17
forum: The Cafe
---

### Post by billdotson on 2007-02-17
I have this computer and two others in the house. The others run off of wireless and this one plugs directly into the router. The other computer's internet works when mine does not.

I am thinking since it messes up in both Windows and Ubuntu that there is something wrong with my Marvell Yukon Gigabit Ethernet controller (onboard on my Asus P5B Deluxe/Wi-fi AP motherboard) It has been working fine until recently and now I am having internet issues.

In Ubuntu I got the internet working (I think) by going to network manager and hitting configure on the eth0 ethernet device but a window popped up saying I do not have privileges to access the configuration. Then I went to the terminal and just blindly tried sudo network-manager, and then tried sudo net -w. After that I tried the internet and it was working.

I am in Windows now and I got it working in here (I think) by going to the device menu for the ethernet controller, going to the advanced tab, and in the internet connection sharing area I checked on 'Allow other network users to connect to the internet through this computer's connection. It worked after that, but then I turned it off and it is still working.
Funny thing is though Windows sees no problems with it and says it is connected.

I know it is not a driver issue because it was working fine earlier and it doesn't connect in Linux either.

Should I just get a new ethernet cable?

Please help....I hope I get a solution before it goes down again!! PLEASE..

---

### Post by corstar on 2007-02-17
I used to have a similar problem
It turns out I'd put the correct nameserver and dns into Networking, but only saved it if I edeited the text file (cant remember where nameserver was kept, maybe somewhere under /etc/)
This was in Dapper, though

---

